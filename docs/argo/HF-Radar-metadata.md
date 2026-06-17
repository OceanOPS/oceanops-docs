# Registration of HF Radar stations from the EU HFR node
## Metadata access
[ERDDAP](https://erddap.hfrnode.eu/erddap/index.html)

[API](https://api.hfrnode.eu/)

## Update of the OceanOPS database
Before the update of the HF Radar network, some records were already existing in the OceanOPS database. 

* Step 1: export the station metadata from the EU HFR node API
* Step 2: step up the environment. Mainly, creation of new programs. Program name = HF _country _- _lead agency_
* Step 3: identify the API records matching with historical records => update of the metadata record
* Step 4: registration of new records 

## How to select HF Radar records
* Network = "Global High Frequency Radar"=> records from the API 
* Network = "HF Radars"=> Historical records + "Global High Frequency Radar" records
* Network = "HF Radars" + exclude network = "Global High Frequency Radar" => only historical records

