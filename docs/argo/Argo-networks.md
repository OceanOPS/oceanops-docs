In this section we detail the definitions of the different Argo networks

# Global Argo
All floats are part the Argo Global Networks (including Argo Equivalent) appart from the Non Argo floats.
# Argo Core
The network Argo Core exclude floats tagged under Argo BGC, Argo Deep, Argo coastal, Argo Equivalent and Non Argo.
# Argo Deep
Argo floats sampling below 2000m are part of the Argo Deep network. It is computed looking at the platform type = deep float

# Argo BGC
Argo BGC can measures the following parameters : chla, suspended particules, nitrate, oxygen, pH and downwelling irradiance in addition to temperature and salinity. To better assess the implementation of the Argo BGC network, we split it into sub-networks described below.

Computation is based on declared variable (not observed variables).
## Argo BioGeoChemical (Argo BGC)
Any Argo float measuring at least one BGC parameter  is considered as part of the "Argo BGC" network.

Computation is based on declared variable (not observed variables).
## T/S/O2 only (Argo O2 Only)
Any Argo float measuring only oxygen as extra parameter is considered as part of the "Argo O2 only" network. 

Computation is based on declared variable (not observed variables).
## Argo BGC - multiparam
Any Argo float measuring at least one BGC parameter and not included in the "Argo O2 only" network, is considered as part of the "Argo BGC - multiparam" network. In rare cases, "Argo BGC - multiparam" floats may only measure one BGC parameter (e.g., only a nitrate, pH, or irradiance sensor on board, in addition to the CTD).

Computation is based on declared variable (not observed variables).
## Argo BGC - full
Any Argo float measuring at least 5 BGC parameters is considered as part of the "Argo BGC - full" network. 

Computation is based on declared variable (not observed variables).
## Argo GO-BGC
Any float deployed by one of the US GO-BGC programs is part of the network "Argo GO-BGC".

## Argo BGC - `VARIABLE`
Any Argo float measuring the BGC variable is considered as part of the "Argo BGC - `VARIABLE`" network.

Computation is based on observed variable (not declared variables).
# Argo equivalent
A profiling float funded and operated through ad hoc or research projects, not necessarily complying with Argo best practices for sampling, but sharing data according to Argo standard and complying with Argo notification regimes. Extra sensors can be piloted, but all data must be made available without any restriction.
# Argo coastal
The Argo Coastal Network group together the floats design for coastal (shallow water) operation. Any Float model finishing with "_C" is part of the Argo coastal network.
# Euro Argo
The Euro Argo network include all floats operated by the members of the EuroArgo ERIC.
# TPOS (Tropical Pacific Observing System)

# Non-Argo
Profiling floats operated at regional (e.g. micro floats for hurricane tracking), national or international level (e.g. Earthscope oceans11) not complying with any best practices for sampling, having other sensors (e.g. passive acoustic) not complying with the Argo framework. These floats are not part of Argo and therefore not allowed to put the Argo sticker. Some of these floats share data (e.g. on the Global Telecommunication System of WMO), which can be very important for some operational users, and consequently needs to be monitored by OceanOPS.
