# Argo Deployement plan procedures
## Request ID.
1) request an id: Only the program and the approximated deployment date is mandatory.
2) register the plan with csv upload (save). csv file should be:
COUNTRY,PROGRAM,DEPLOYMENT DATE,DEPLOYMENT LAT,DEPLOYMENT LON,MODEL,DEPLOYMENT SHIP
3) Notify float deployement by ipload meta.nc file shortly before of after deployment (Save and notify)

It is important to have in mind that notification and plan can be decorrelated. For instance, float XXX is planned to be deployed in the Indian Ocean and float YYY planned to be deploy in the Atlantic Ocean. If for any reason float XXX is deploy in the Atlantic and float YYY in the Pacific, the notification through meta.nc will correct this automatically.

Note that the initial deployment date needed to request a WMOID is used to remove unused WMOIDs after 2 years without notification

## csv upload
* It is also possible to register plan without requesting WMO IDs before. 
* In this case, upload the csv file similar to the above (without the WMO ID column). The ipload of the csv will deliver a reference starting with TMP (instead of the WMO ID). 
* To update and create new plans, it is requested to deleat all previous plans and upload the new csv. OceanOPS shall assist on this.
* As for every float, to notify a deployment, a WMO ID is requested. Meaning that before the creation of the meta.nc operator must request an id through the request id.
* This procedure make sens for program or aggregation of program managing many floats and re-planning deployment very frequently (e.g. GO-BGC).
* This is not the standard procedure. This procedure request the support of OceanOPS.


