# Monthly maps
## Argo cycle times (declared in metadata file)
This map is based on the information declared in the float's meta.nc file when it is registered with OceanOPS.
Since IRIDIUM communication allows reconfiguration of the float during its mission, this map may mislead the reader. For example, many operators configure short initial cycles to verify the float's functionality and report this configuration in the meta file registered with OceanOPS. Changes in configuration during the mission are not reflected in this map.

## Argo density (Core, Deep, BGC)
Argo density represents the number of active floats for a particular mission (excluding floats on the grey list) within each cell of the mission's design grid:
* Argo BGC: Density is computed separately for each variable.
* Argo Core: Density includes all active Argo floats.
* Argo Deep: Density includes all active Deep Argo floats.

## Deep Argo projected density
This map calculates the density of active floats (excluding those on the grey list) in each cell of the mission's design grid while considering the age of the floats to highlight regions in need. 
Deployment plans are also consider, -4 months + 12 months of the calculation date of the map.

## Argo density / plan (Core, Deep, BGC)
This map include the age and the deployment plans in the density computation. 
Weight for plans are equal to 1.

## Deep Argo Coverage : 
Only Argo profile quality control flags for TEMP equal to A or B are counted to compute the deep coverage map.

## Argo BGC density/plan

This map calculates the density of active Argo BioGeoChemical floats (excluding those on the grey list) in each cell of the mission's design grid while considering the age of the floats. THis map aim at highlighting regions in need of deployments.
We use Argo BioGeoChemical as a reference to consider all BGC floats. This may have the consequence to underestimate the risk of surviving an extra year.
For Argo BioGeoChemical, the following weights are applied to each float based on its age, reflecting the probability of its survival in the following year:
* AGE < 1 year (365 days): weight = 1-0.14
* 1 year ≤ AGE < 2 years: Weight = 1-0.15
* 2 years ≤ AGE < 3 years: Weight = 1-0.23
* 3 years ≤ AGE < 4 years: Weight = 1-0.24
* 4 years ≤ AGE < 5 years: Weight = 1-0.17
* 5 years ≤ AGE < 6 years: Weight = 1-0.06
* 6 years ≤ AGE < 7 years: Weight = 1-0.10

ELSE 0

## [Argo National contribution](https://www.ocean-ops.org/share/Argo/Maps/ship_country_latest_loc_ope.png) 
Count all operational floats, no removal of grey listed float, no overlap with the design.
## [Argo National contribution small](https://www.ocean-ops.org/share/Argo/Maps/countries_s.png)
Count all operational floats, no removal of grey listed float, no overlap with the design.
## [Argo platform models](https://www.ocean-ops.org/share/Argo/Maps/models.png)
Count all operational floats, no removal of grey listed float, no overlap with the design.
## [Argo Simple](https://www.ocean-ops.org/share/Argo/Maps/simple.png)
Count all operational floats, no removal of grey listed float, no overlap with the design.
## [Argo Simple - Black & White](https://www.ocean-ops.org/share/Argo/Maps/simple_bw.png)
Count all operational floats, no removal of grey listed float, no overlap with the design.
## [Argo Network](https://www.ocean-ops.org/share/Argo/Maps/networks.png)
Count all operational floats, no removal of grey listed float, no overlap with the design.

