# Argo Synch - 3 steps

1. Extraction of metadata from GDAC
2. Reporting of additions
3. upload in the data base

# 1. Extraction of metadata from GDAC - Operational Argo Float Metadata Extraction – User Documentation

## Overview

This notebook extracts metadata and configuration information for recently active Argo floats using the `argopy` library and exports the results into a CSV file.

The workflow:

1. Loads the global Argo profile index
2. Identifies floats that produced profiles during the last *N* days
3. Retrieves:

   * General metadata (`meta.nc`)
   * Latest profile information (`prof.nc`)
4. Extracts selected configuration parameters from the latest mission
5. Generates a clean CSV file for further manual updates and operational use

---

# File Location

Notebook directory:

```text
C:\Users\vturpin\Documents\Mes Notebooks
```

Notebook file:

```text
GetOperationalFloatMetadata_V6-1.ipynb
```

(previously `GetOperationalFloatMetadata_V6.ipynb`)

---

# Environment Setup

## Launch Anaconda Navigator

Select the environment:

```text
ArgoPY-env
```

---

# Launch JupyterLab

From Anaconda Navigator:

* Open **JupyterLab**
* Create or open a **Python 3 Notebook**

⚠️ Important:
Verify that the notebook is running on the correct kernel:

```text
Python 3 ipykernel
```

---

# Running the Notebook

## Open the Notebook

Navigate to:

```text
Mes Notebooks
```

Open:

```text
GetOperationalFloatMetadata_V6-1.ipynb
```

---

## Update the Output Filename

Before execution, update the CSV filename with the current month if necessary.

Example:

```python
df.to_csv("argo_metadata_last_config_clean_202604.csv", index=False)
```

---

## Execute the Notebook

Run all notebook cells sequentially.

The script will:

* Load the Argo GDAC index
* Identify recently active floats
* Retrieve metadata and latest configuration parameters
* Export the results into a CSV file

---

# Post-processing Workflow

Once the V6 CSV file has been generated:

1. Transfer the CSV file to **Magali**
2. Manual updates are then performed for:

   * Configuration parameters
   * PI information
   * Sensor model
   * Sensor serial number
   * Platform model
   * Special features
   * Customization fields

⚠️ The detailed update procedure still needs to be formally established with Magali.

---

# Troubleshooting

If the notebook fails because of `argopy` dependency issues:

## Open Anaconda Prompt

Run:

```bash
conda activate argopy_env
pip install --upgrade argopy
```

Then:

* Restart JupyterLab
* Restart the notebook kernel
* Rerun the notebook

---

# Script Description

# Imported Libraries

The script uses:

* `numpy`
* `pandas`
* `datetime`
* `xarray`
* `netCDF4`
* `argopy`

Warnings related to large integer conversion are ignored to avoid unnecessary console messages.

---

# Utility Function

## `clean_argo_value(val)`

Cleans metadata values extracted from Argo `meta.nc` files.

### Purpose

* Removes padding spaces
* Converts arrays/lists into compact strings
* Handles missing values safely

### Returns

A cleaned string suitable for CSV export.

---

# User Parameters

## Float Activity Selection

```python
days_back = 14
```

Only floats that produced profiles within the last 14 days are processed.

---

# Loading and Filtering the Argo Index

The script loads the global Argo profile index:

```python
idx = ArgoIndex(index_file="ar_index_global_prof.txt")
```

Then:

* Converts dates to pandas datetime objects
* Filters profiles more recent than `days_back`
* Extracts unique WMO float identifiers

---

# Metadata Fields Extracted

The following metadata fields are retrieved from `meta.nc`:

```python
PI_NAME
FLOAT_OWNER
OPERATING_INSTITUTION
PROJECT_NAME
PLATFORM_NUMBER
PLATFORM_TYPE
SENSOR_MODEL
SENSOR_SERIAL_NO
SPECIAL_FEATURES
CUSTOMISATION
```

---

# Configuration Parameters Extracted

The script extracts selected mission configuration parameters:

```python
CONFIG_ParkPressure_dbar
CONFIG_IceDetection_degC
CONFIG_CycleTime_hours
CONFIG_ProfilePressure_dbar
```

These values are taken from the latest mission configuration associated with the latest profile.

---

# Main Processing Workflow

For each float WMO:

## 1. Load Float Data

```python
af = ArgoFloat(wmo, aux=True)
```

---

## 2. Retrieve Latest Profile

The script opens:

```text
prof.nc
```

and identifies the latest profile using:

* `JULD`
  or
* `CYCLE_NUMBER`

---

## 3. Determine Latest Mission Number

The latest mission configuration number is extracted from:

```text
CONFIG_MISSION_NUMBER
```

---

## 4. Open Metadata File

The script opens:

```text
meta.nc
```

and extracts:

* Metadata fields
* Configuration parameters

---

## 5. Match Configuration Parameters

The script:

* Searches the latest mission configuration
* Identifies target parameters
* Stores their values individually

---

## 6. Error Handling

If a float cannot be processed:

```python
except Exception as e:
```

the script logs the error and continues processing the remaining floats.

---

# CSV Export

All extracted records are stored in a pandas DataFrame and exported as:

```text
argo_metadata_last_config_clean_YYYYMM.csv
```

Example:

```text
argo_metadata_last_config_clean_202604.csv
```

---

# Output

The generated CSV contains:

* One row per operational float
* General metadata
* Latest mission configuration parameters

This file is intended for:

* Operational monitoring
* Metadata harmonization
* Manual completion/update workflows

---

# Notes

* The script depends on online access to Argo GDAC resources through `argopy`.
* Processing time depends on the number of active floats.
* Some metadata fields may be empty if unavailable in `meta.nc`.

# 2. Reporting of additions
# 3. upload in the data base
## Rules for uploading
### General rules
### Fields specific rules