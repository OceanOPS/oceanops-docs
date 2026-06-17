# Argo files
## Index files
Argo data management produces several index files easy to read by users. In this section we are reviewing the uses of the several indexes files by OceanOPS.

### Ar_index_global_prof.txt
File can be found here: https://data-argo.ifremer.fr/ar_index_global_prof.txt

### Argo_synthetic-profile_detailled_index.txt
File can be found here: https://data-argo.ifremer.fr/etc/argo_synthetic-profile_detailled_index.txt
OceanOPS extract from the synthetic profile the "parameter_data_mode" and the "parameter_quality" to plot data quality charts.

### Argo_profile_detailed_index.txt 
The file is available here: https://data-argo.ifremer.fr/etc/argo_profile_detailled_index.txt
This file is used to compute timeliness by comparing "observation date" to "GDAC date creation".
This file is also used to compute data quality charts by loading "ad_psal_adjustment_mean", "ad_psal_adjustment_deviation".

### Other index files
All index files files are available at: https://data-argo.ifremer.fr/etc/argo-index

## Profile file
Profile files produce by each DAC can be found here: https://data-argo.ifremer.fr/dac/
* R* files are Core Real Time files
* D* files are Core delayed time files
* BR* files are Bio profile files real time. Including all intermediate parameters. Note the in B* files, there is one pressure by BGC variable.
* BD* files are Bio profile files in delayed time. Including all intermediate parameters. Note the in B* files, there is one pressure by BGC variable.
* SR* files are Argo Synthetic profile files in Real Time. Synthetic profiles only have one pressure vector for all Core and BGC parameters. The parameters are copied or interpolated at the right pressure.
* SD* files are Argo Synthetic profile files in Real Time. Synthetic profiles only have one pressure vector for all Core and BGC parameters. The parameters are copied or interpolated at the right pressure.

OceanOPS does not use the data file. OceanOPS only use the index file pointing to the data files.