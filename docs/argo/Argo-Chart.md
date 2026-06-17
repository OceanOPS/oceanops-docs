This page describes the statistics display in the section Argo > Chart > Data Flow

# Data flow
## [Delay Grids](../Delay-Grids)

# Performance
## [survival rate](../survival_rate)
## [survival rate 2](../survival_rate_2)

## Sensor Activity
### Methodology:
For every cycle we compute the ratio of sensor delivering data (any quality) and sensor delivering bad data.
We use the profil "parameter_quality = F" to assess bad data
We compute 70 cycles only

### Note: 
The expected behaviour of the curve would be to decline. However, there are several reason to see the curve improving.
1) **Missing cycles**: If one or more cycles are missing this affect the total number of floats, which can cause the ratio to increase when back.
2) **Sensors returning to good quality**: A sensor may produce bad data for one profile and good data for the next. When data quality improves, the ratio increases.
3) **Floats with failed sensors reaching end of life**: When a float equipped with a sensor that was delivering bad data dies, the total number of floats decreases while the number of operational sensors stays the same. This also leads to an increase in the ratio.


**SQL procedure** <br><br>
The OBS_INFO.update_sensor_cycle_activity procedure runs daily to insert new rows to the oceanops.SENSOR_CYCLE table.
1. Selection of the records from the OBS_ARGO_GDAC and OBS_ARGO_GDAC_VARIABLE tables: 
* where cycle <= 150 (OBS_ARGO_GDAC.cycle_nb) 
* and obs_data_status_id is not null (OBS_ARGO_GDAC_VARIABLE.obs_data_status_id)
* and obs update_date is recent (in the last 5 days) (OBS_ARGO_GDAC.update_date)

Fields resulting from this selection: 
* OBS_ARGO_GDAC_VARIABLE.QC
* OBS_ARGO_GDAC_VARIABLE.OBS_DATA_STATUS_ID
* OBS_ARGO_GDAC_VARIABLE.VARIABLE_ID
* OBS_ARGO_GDAC.CYCLE_NB
* OBS_ARGO_GDAC.PTF_ID

2. Based on the content of this selection, only records for which a unique link can be established between the measured variable (OBS_ARGO_GDAC_VARIABLE.VARIABLE_ID) and the declared variable (PTF_VARIABLE.variable_id) are selected. 
The goal is to link the measured variable to a declared sensor model. e.g., if the measured variable is 'Ocean Temperature' and the corresponding float is registered in OceanOPS with 2 'Ocean Temperature' sensors, we are not able to link the measured variable to the right sensor model: these raws are ignored. 
 
4. Insertion in the oceanops.SENSOR_CYCLE table
The values inserted in the oceanops.SENSOR_CYCLE table are based on the check detailled above. Fields of the table: 
* PTF_VARIABLE_ID
* CYCLE 
* IS_ACTIVE (0/1, if QC = 'F' then 0 else 1)
* DATA_STATUS_ID