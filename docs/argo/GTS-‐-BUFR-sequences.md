# BUFR format 
To push data on the GTS or WIS2.0 networks data assembly center and/or meteorolgical agencies should follow WMO recommendation on format.
The definition of the BUFR format are available in the [wmo manual of code](https://library.wmo.int/records/item/35625-manual-on-codes-volume-i-2-international-codes#.X18yfpMza3I).

## Sequence for profiling instruments
The sequences for profiling instrument are in table D of the wmo manual of code:
* Argo BUFR sequence: 3.15.003
* OceanGliders BUFR sequence: 3.15.012
* AniBOS BUFR sequence: 3.15.023
* FVON BUFR sequence: **to be completed**
* Surface vehicles BUFR sequence: 3.15.011

TESAC format is the "level 1" format to be able to push data on GTS. TESAC is reducing the number of metadata going along with the data set. 
BUFR is the "level 2" format to be able to submit data on GTS and WIS2.0. There is one BUFR format by platform type. BUFR format will be the only format allowed on WIS2.0.

## Network details.
### Argo
See [here](https://github.com/OceanOPS/helpdesk/wiki/Argo-GTS-Monitoring#how-do-we-monitor-argo-on-the-gts) to know how OceanOPS monitor the Argo on the GTS.

#### Core
#### BGC
BGC BUFR sequences that have now been approved for operational use include the following parameters:
* dissolved oxygen
* chlorophyll-A
* nitrate
* sea water pH
* BBP700 (particle backscattering at 700 nm)

![image](https://github.com/user-attachments/assets/90e9dd3c-6453-4738-a6d7-a07dd02e44a6)
(See p78 of the WMO Manual on codes)

Due to the large uncertainties in unadjusted BGC parameter data, we have agreed that only adjusted BGC parameter data ('A' mode) should be sent to the GTS (no 'R' mode BGC data should be sent to the GTS). 

### OceanGliders
### AniBOS
> NOAA/NWS/NDBC is using the new BUFR template for GTS data.   UK Met is still using TESAC format, as of June 2024.
### FVON