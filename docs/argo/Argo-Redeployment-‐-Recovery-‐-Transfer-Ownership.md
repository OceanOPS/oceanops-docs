This section describe the procedure for float redeployment, float Recovery, float Transfer Ownership.

# Recovery
# Redeployment
# Transfer Ownership
## DAC and GDAC management
At DAC and GDAC level the full data set is transfered to the new DAC. This is impacting the index file.
## Close the ptf
* The float to be transfered is closed with a closing date compatible with the transfer date
* The ending cause should be set as transfer ownership
* The recovery comment should be completed
* update link to data url (not tested yet)
## open new ptf
* The meta file are reloaded
* ref is modified with WMO_001
* Parent ref is filled with previous ref
* program is modified
* Deployment date is set to transfer ownership date
* Deployment location is set to first surfacing after transfer ownership


