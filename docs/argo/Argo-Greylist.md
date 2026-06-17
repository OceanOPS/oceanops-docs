Argo maintained a greylist file (https://data-argo.ifremer.fr/ar_greylist.txt) listing the floats that should be taken off the fleet due to bad data. 
This greylist file is currently the concatenation of the greylist files from all the DAC.

On a daily basis, OceanOPS load this grey list to flag the floats consequently and not count them in the statistics (data flow, density, coverage, etc.).

The grey list is organised as follow:
PLATFORM_CODE,PARAMETER_NAME,START_DATE,END_DATE,QUALITY_CODE,COMMENT,DAC
5905254,TEMP,20201218,,4,presumed sensor problem,AO
5905255,PRES,20180204,,4,sensor problem,AO
5905255,PSAL,20180204,,4,sensor problem,AO
5905255,TEMP,20180204,,4,sensor problem,AO
5905258,PSAL,20220901,,4,sensor problem,AO
5905260,PSAL,20211125,,4,sensor failure,AO

Note that the greylist do not include the floats in Alerts due to "min/max" test (Run by Coriolis) and "Altimetry" test (run by cls) until the DAC investigates on each float and decide to put or not the float in its greylists.

Note also that we need to figure out if OceanOPS is considering the end_date or not. A doute still exist at the time we are writting down those line.






 