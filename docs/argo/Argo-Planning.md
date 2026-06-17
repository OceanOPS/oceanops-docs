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

## float editor/wizzard

## gis editor
When ploting a map with plans.
We consider as "stock"/"float waiting for deployment opportunities", floats that are registered with the following locations. Those corresponding to laboratories (Lat Lon) in decimal degree.

* Japan (JMA): 35.661 139.698
* Korea: 35.075 129.079
* Canadian east coast (Victoria University) : 48.468 -123.296
* US (PMEL) : 47.651 -122.312
* US (SIO) : 32.865 -117.253
* Australia (CSIRO, Hobart) : -42.886 147.338
* US (UW): 47.686 -122.25
* France (IFREMER) : 48.360 -4.560
* Poland (IOPAN) : 54.450 18.563
* South Africa (Univ. of Cape Town): -33.956 18.461 
* UK (NOC) : 50.893 -1.395 
* Germany (BSH) : 53.546 9.967 

Any addition of stock location should be reported in the following maps: 
* plan by country
* plan by network
* plan by status
* bgc plan flowers (float type)

# Deployment plan management 

## Platform Reference management
There are several ways to upload deployment plan in the OceanOPS system that impact the reference management of the pklatform differently.

* When deployment plans are created through the request id, they are created with a WMO ID.
* When deployment plans are uploaded through csv file, without WMO ID, the ref is TMP*
* When deployment plans are uploaded through csv file, with WMO ID, the plan is uploaded.
* When deployment plans are uploaded through the float editor/wizzard: TO BE COMPLETED
* When deployment plans are uploaded through the gis editor: TO BE COMPLETED

## When do we delete a plan?
* 2 month after the planned deployment date for a plan with a TMP* reference. This routine run every 27th of each month).

## How do we notify the program? (**to be implemented**)
* Deployment plan notifications are send the 1st of each month to program manager and data manager. 
* Deployment plan notification concern only the deployment plans older than 2 month.

The message send contains: 
* a request to update or deleate the plan, 
* a reminder about the deployment plan removal date, including the different treatment between ref type TMP* and WMOID
* a link to the float editor of each platform.


