# Argo Synchronisation with GDAC

In order to limit the drift between the GDAC and the OceanOPS data base, a procedure to synchronise OceanOPS with the GDAC has been set in place.
This procedure runs on a monthly basis and concern the following fields:

## Synchronised fields
**Configurations**: 
* Parking depth
* Max profile pressure
* cycle duration
* Ice detection

**Hardware**:
* Sensor model
* sensor serial number
* platform model

**Contributors**:
* PI
* Float owner
* Operating institution
* project

**Others**
* Special feature
* Customization

## Procedures and rules
On a monthly basis, floats that transmit data over the last 10 days are checked and metadata files are read.
A csv file with all the metadata listed above for each identified float is listed above and transmitted to metadata manager at OceanOPS.
This file is processed to update the OceanOPS system when needed with the extracted information, following the rules:

**Rules**: 
* If no value in the csv file but exist in the OceanOPS data base, no update, we keep the OceanOPS value, considering the level of information is higher.
* If the csv value is different from the OceanOPS data base, we update the OOps data base with the .csv value.
* If there is no value in the OOps data base, the OOps data base is updated with the csv value.
* If no value in OOps and csv, the default value is used to update OOps data base.
* For deep floats, the max profile pressure is updated only if the csv value exist, otherwise we leave it as it is. We do not use default value for max profile pressure for deep floats.  
* for ice detection, we look for the "CONFIG_IceDetection_degC", that seems to be common to all float type. If this parameter is not empty, we consider this float has an ice avoidance algorithm active on board and the OOps data base is updated consequently.
* Custimoization and special feature are updated in the OOps data base when value in the csv file exist.

`Hardware and contributors fields are not treated yet by metadata manager.`

**Default values**
* CONFIG_ParkPressure_dbar, default : 1000 (CONFIG.drift_press) 
* CONFIG_CycleTime_hours, default: 240 (CONFIG.cycle_time)  
* CONFIG_ProfilePressure_dbar, default: 2000 (CONFIG.profile_press) (with an exeption for deep floats) 

## Automatisation
This process is not automatise yet. Metadata extraction runs on the Argo TC computer and is launched manually. Metadata update runs on Metadata manager computer and is lauched when csv file ready.

A report is produce every month to identify the number of update and the concerned floats. 