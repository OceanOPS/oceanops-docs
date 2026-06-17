# Argo Script
## Argo missing
On a daily basis: 
* We scan the index_profile (**add the link here**) and load new observations available at GDAC (**identify the script here**).
* We compare WMO IDs in the index_profile file with existing WMO IDs in our data base, if not matching or if matching with a planned status (probable, confirmed) then an message is send to support@ocean-ops.org to notify Argo TC that a float has been deployed and not being notify at OceanOPS. This allow to follow closely with IOC resolution XX-6.
* Argo TC is in charge of notifying the float in a short period of time (less than a month) through the upload of the corresponding meta.nc file.

