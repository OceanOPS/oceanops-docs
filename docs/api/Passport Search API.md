# Passport Search API

## Endpoint

```http
POST https://www.ocean-ops.org/api/data/passports/search
Content-Type: application/json
```

Returns pre-generated OceanOPS passport JSON documents from the PostgreSQL passport cache.

Unlike traditional passport generation, this endpoint **does not rebuild JSON on demand**. Instead, it serves cached passport documents generated asynchronously by the database refresh pipeline, allowing fast queries and efficient bulk export.

---

# Features

The endpoint supports:

- Retrieve one passport
- Retrieve multiple passports
- Bulk download all passports (~80,000)
- Filter using the existing OceanOPS platform filtering engine
- Filter by platform IDs
- Filter by OceanOPS internal IDs
- Incremental synchronization using cache update timestamps
- Pagination
- Streaming large responses

---

# Authentication

This endpoint is public so does not require authentication.

---

# Request Body

All request fields are optional.

```json
{
  "filters": {},
  "ptfIds": [],
  "internalIds": [],
  "cachedSince": "2026-07-14T18:00:00",
  "paginationEnabled": true,
  "limit": 100,
  "offset": 0
}
```

## Request Fields

| Field | Type | Description |
|--------|------|-------------|
| `filters` | object | Existing OceanOPS platform filters. |
| `ptfIds` | integer[] | Restrict to specific OceanOPS platform IDs. |
| `internalIds` | string[] | Restrict to OceanOPS internal platform identifiers. |
| `cachedSince` | ISO datetime | Only return passports regenerated after this UTC timestamp. |
| `paginationEnabled` | boolean | Enable or disable pagination. |
| `limit` | integer | Maximum number of passports returned when pagination is enabled. |
| `offset` | integer | Number of matching passports to skip. |

All supplied criteria are combined using **AND** logic.

---

# Response

## Paginated response

```json
{
  "items": [
    {
      "ptfId": 420,
      "version": 3,
      "cacheUpdatedAt": "2026-07-14T19:02:17.324271Z",
      "schemaVersion": "1.0",
      "passport": {
        ...
      }
    }
  ],
  "total": 1,
  "paginationEnabled": true,
  "limit": 100,
  "offset": 0
}
```

## Bulk response

When `paginationEnabled` is `false`, the response is streamed.

```json
{
  "items": [
        ...
  ],
  "total": 80452,
  "paginationEnabled": false
}
```

---

# Response Fields

## Top-level response

| Field | Description |
|--------|-------------|
| `items` | Matching passport documents. |
| `total` | Total number of matching passports. |
| `paginationEnabled` | Indicates whether pagination was used. |
| `limit` | Page size (paginated mode only). |
| `offset` | Current page offset (paginated mode only). |

## Passport metadata

Each returned item contains:

| Field | Description |
|--------|-------------|
| `ptfId` | OceanOPS platform database ID. |
| `version` | Passport cache version. Incremented whenever the cached passport changes. |
| `cacheUpdatedAt` | UTC timestamp when the cached passport was last regenerated. |
| `schemaVersion` | Passport JSON schema version. |
| `passport` | Complete cached passport JSON document. |

Each passport section contains this structure:
```json
{
            "ptfId": 22,
            "version": 1,
            "cacheUpdatedAt": "2026-07-15T11:17:04.227482Z",
            "schemaVersion": "1.0",
            "passport": {
                "status": {
                    "reportingStatus": {
                        "id": 5,
                        "code": "closed",
                        "name": "CLOSED"
                    },
                    "latestObservation": {
                        "latitude": 33.815,
                        "longitude": 149.765,
                        "timestamp": "2002-06-08T23:54:33Z"
                    }
                },
                "hardware": {
                    "telecom": {
                        "type": {
                            "id": 2,
                            "name": "ARGOS"
                        },
                        "number": "23815",
                        "endTimestamp": "2002-06-08T23:54:33Z",
                        "startTimestamp": "2001-07-20T00:00:00Z"
                    },
                    "platform": {
                        "asset": {
                            "wmo": "2900314",
                            "model": {
                                "id": 1182,
                                "code": "provor-mt",
                                "name": "PROVOR_MT",
                                "type": {
                                    "id": 26,
                                    "name": "Float",
                                    "wigosUri": "https://codes.wmo.int/wmdr/FacilityType/_underwaterMobile"
                                }
                            },
                            "endTimestamp": "2002-06-08T23:54:33Z"
                        }
                    },
                    "sensorSetups": [
                        {
                            "id": 23763,
                            "variable": {
                                "id": 31,
                                "code": "ocean-temperature",
                                "name": "Ocean temperature"
                            }
                        },
                        {
                            "id": 23764,
                            "variable": {
                                "id": 1,
                                "code": "ocean-salinity",
                                "name": "Ocean salinity"
                            }
                        },
                        {
                            "id": 55942,
                            "variable": {
                                "id": 3,
                                "code": "pressure",
                                "name": "Pressure"
                            }
                        },
                        {
                            "id": 635349,
                            "variable": {
                                "id": 3,
                                "code": "pressure",
                                "name": "Pressure"
                            }
                        },
                        {
                            "id": 635350,
                            "variable": {
                                "id": 1,
                                "code": "ocean-salinity",
                                "name": "Ocean salinity"
                            }
                        },
                        {
                            "id": 635351,
                            "variable": {
                                "id": 31,
                                "code": "ocean-temperature",
                                "name": "Ocean temperature"
                            }
                        },
                        {
                            "id": 641049,
                            "variable": {
                                "id": 3,
                                "code": "pressure",
                                "name": "Pressure"
                            }
                        }
                    ]
                },
                "operations": {
                    "deployment": {
                        "ship": {
                            "hull": {
                                "imoNumber": "8920012"
                            },
                            "registration": {
                                "name": "KAIYO MARU"
                            }
                        },
                        "latitude": 33.999,
                        "longitude": 143.993,
                        "timestamp": "2001-10-12T00:00:00Z"
                    },
                    "endTimestamp": "2002-06-08T23:54:33Z"
                },
                "affiliation": {
                    "networkTags": [
                        {
                            "id": 1000420,
                            "name": "Argo Core"
                        },
                        {
                            "id": 1000180,
                            "name": "Argo Global"
                        },
                        {
                            "id": 1001976,
                            "name": "Global Core mission"
                        }
                    ],
                    "supervisingProgram": {
                        "id": 52,
                        "code": "argo-jamstec",
                        "name": "Argo JAMSTEC",
                        "country": {
                            "id": 190,
                            "name": "Japan"
                        }
                    },
                    "goosObservingNetworks": [
                        {
                            "id": 1000620,
                            "name": "Argo",
                            "wigosCode": "argo"
                        }
                    ]
                },
                "dataChannels": {},
                "identification": {
                    "reference": "2900314",
                    "passportId": "0-22000-0-2900314"
                }
            }
        }
```

---

# Usage Examples

## Retrieve one passport

```json
{
    "ptfIds": [420]
}
```

---

## Retrieve several passports

```json
{
    "ptfIds": [
        420,
        511430,
        511431
    ]
}
```

---

## Retrieve by OceanOPS internal identifiers

```json
{
    "internalIds": [
        "5212",
        "8245"
    ]
}
```

---

## Retrieve all closed platforms

```json
{
    "filters": {
        "status": "5"
    }
}
```

---

## Retrieve all Argo platforms

```json
{
    "filters": {
        "masterNetworks": "1000620"
    }
}
```

---

## Filter by program

```json
{
    "filters": {
        "programs": "59"
    }
}
```

---

## Filter by country

```json
{
    "filters": {
        "countries": "66"
    }
}
```

---

## Filter by WIGOS identifier

```json
{
    "filters": {
        "wigosId": "0-22000-0-5904525"
    }
}
```

---

## Incremental synchronization

Returns only passports regenerated after the supplied UTC timestamp.

```json
{
    "cachedSince": "2026-07-01T00:00:00"
}
```

This is the recommended mechanism for synchronizing Gateway or mobile app.

---

## Paginated download

```json
{
    "filters": {
        "masterNetworks": "1000620"
    },
    "paginationEnabled": true,
    "limit": 500,
    "offset": 1000
}
```

---

## Bulk download

Downloads every matching passport.

```json
{
    "paginationEnabled": false
}
```

Filtering can still be applied.

Example:

```json
{
    "filters": {
        "masterNetworks": "1000620"
    },
    "paginationEnabled": false
}
```
---

# Performance

The endpoint is designed for high-volume metadata distribution.

Characteristics:

- Reads only from `passport_json_cache`
- No JSON generation during requests
- Supports streaming responses
- Supports PostgreSQL cursor fetching
- Suitable for complete exports (>80,000 passports)
- Supports efficient incremental synchronization using `cachedSince`

---

# Typical Usage

## Gateway

Nightly synchronization:

```json
{
    "paginationEnabled": false
}
```

Incremental synchronization every few minutes:

```json
{
    "cachedSince": "2026-07-14T18:00:00"
}
```

---

## Mobile applications

Initial installation:

```json
{
    "paginationEnabled": false
}
```

Subsequent synchronizations:

```json
{
    "cachedSince": "2026-07-14T18:00:00"
}
```

---

# Notes

- All timestamps are returned in UTC using ISO 8601 format with a trailing `Z`.
- Passport JSON is generated asynchronously by the database refresh pipeline.
- The endpoint never regenerates passports during request processing.
- `version` changes whenever the cached passport changes.
- `schemaVersion` identifies the version of the passport JSON contract.

---

# Supported Platform Filters

The `filters` object supports the filtering capabilities provided by the OceanOPS platform search engine through `PlatformFilterSubQueryBuilder`.

Filter names are **case-sensitive** and must be supplied exactly as documented below.

## Filter format

Filters are passed as properties of the request's `filters` object:

```json
{
  "filters": {
    "status": "1,2",
    "programs": "12,45",
    "masterNetworks": "1000620",
    "deplDateFrom": "2025-01-01",
    "deplDateTo": "2025-12-31",
    "hasWigosId": "on"
  }
}
```

Most filters accepting multiple identifiers use a comma-separated string:

```json
{
  "filters": {
    "programs": "12,45,81",
    "variables": "1,2,7"
  }
}
```

Dates use the `YYYY-MM-DD` format unless otherwise stated.

Boolean-style filters generally use `"on"` or `"1"`. Some legacy filters also accept `"Yes"`.

> [!IMPORTANT]
> These are legacy search-engine parameters. Although values are supplied as strings, their meaning varies by filter and may represent identifiers, text, dates, numbers, or boolean flags.

## Common filters

Frequently used filters include:

* `status`
* `programs`
* `masterNetworks`
* `networks`
* `country`
* `model`
* `modelType`
* `family`
* `ptfCategories`
* `variables`
* `deplDateFrom`
* `deplDateTo`
* `obsDateFrom`
* `obsDateTo`
* `wmoId`
* `wigosId`
* `internalId`

## Complete filter reference

Many filters use oceanops database ids as values in filters. 
Whilst these ids are not always easily publicly accessible, some are accessible via the vocabulary tables here: [OceanOPS Code Tables](https://www.ocean-ops.org/passports/#/code-tables).

### Platform identity

* `ref`  : performs a prefix search , case-insensitive, so "390" matches: 390, 390A, 3907800) Supports multiple values: "filters": {"ref": "390,391"}
* `exactRef` : performs exact match, "3902800" only matches 3902800. Supports multiple values: "filters": {"exactRef": "3902800,5906601"}
* `name` : platform name prefix search. Example: `"RAMA"`
* `internalId` : internal platform IDs. Example: `"12345,67890"`
* `serialId` : platform serial number. Example: `"8472"`
* `maxSerial` : maximum platform serial. Example: `"5000"`
* `osPlatformName` : OceanSITES platform name. Example: `"PAPA"`
* `ageMin` : minimum platform age (years). Example: `"2"`
* `ageMax` : maximum platform age (years). Example: `"10"`
* `theme` : theme ID. Example: `"3"`

### Platform classification and ownership

* `model` : platform model IDs. Example: `"15,32"`
* `modelType` : model type IDs. Example: `"4,6"`
* `family` : platform family IDs. Example: `"2,5"`
* `ptfCategories` : platform category IDs. Example: `"7,9"`
* `classCategory` : class category IDs. Example: `"1000621"`
* `status` : platform status IDs. Example: `"1,2"`
* `owner` : owner agency ID. Example: `"105"`
* `country` : programme country IDs. Example: `"250,840"`
* `programs` : programme IDs. Example: `"12,45"`
* `programsAgency` : programme agency IDs. Example: `"10,15"`
* `masterNetworks` : master network IDs. Example: `"1000620"`
* `networks` : network IDs. Example: `"1000620,1000622"`
* `excludeNetworks` : excluded network IDs. Example: `"1000621"`
* `sensorProviderPrograms` : sensor provider programme IDs. Example: `"12,18"`
* `isAdopted` : adopted platforms only. Example: `"on"`
* `isPogoMember` : POGO member programmes only. Example: `"on"`

### Platform identifiers

* `wmoId` : WMO identifiers. Example: `"5906601"`
* `wmoStart` : WMO assignment start date. Example: `"2025-01-01"`
* `wmoEnd` : WMO assignment end date. Example: `"2025-12-31"`
* `wmoActive` : active WMO IDs only. Example: `"on"`
* `wigosId` : WIGOS identifiers. Example: `"0-22000-0-12345"`
* `hasWigosId` : platforms with a WIGOS ID. Example: `"on"`

### Deployment

* `deplDateFrom` : deployment date from. Example: `"2025-01-01"`
* `deplDateTo` : deployment date to. Example: `"2025-12-31"`
* `deplLatFrom` : minimum deployment latitude. Example: `"-60"`
* `deplLatTo` : maximum deployment latitude. Example: `"60"`
* `deplLonFrom` : minimum deployment longitude. Example: `"-180"`
* `deplLonTo` : maximum deployment longitude. Example: `"180"`
* `deplCountries` : deployment country IDs. Example: `"250,554"`
* `deplTypes` : deployment type IDs. Example: `"1,2"`
* `deplMethods` : deployment method IDs. Example: `"3"`
* `deplShip` : ship IDs or names. Example: `"1234,Pourquoi Pas?"`
* `excludeDeplShip` : exclude deployment ships. Example: `"on"`
* `deplCruise` : deployment cruise name. Example: `"PS145"`
* `minimumMaxMooringDepth` : minimum mooring depth (m). Example: `"1000"`
* `maximumMaxMooringDepth` : maximum mooring depth (m). Example: `"6000"`
* `drogue` : drogue status. Example: `"1"`
* `iced` : ice-capable platforms only. Example: `"on"`
* `beached` : beached platforms only. Example: `"on"`

### Deployment ship

* `ptfShip` : platform ship IDs or names. Example: `"1234,Polarstern"`
* `excludePtfShip` : exclude platform ships. Example: `"on"`
* `shipTypes` : ship type IDs. Example: `"2,5"`
* `shipCountries` : ship country IDs. Example: `"250"`
* `shipIces` : ship ICES codes. Example: `"74AB"`
* `shipImo` : ship IMO number. Example: `"9272222"`
* `shipCallsign` : ship call sign. Example: `"FNCM"`
* `shipMmsi` : ship MMSI. Example: `"228123456"`

### Cruise and route

* `cruiseName` : cruise name. Example: `"PS145"`
* `cruiseExclude` : exclude cruise. Example: `"on"`
* `cruiseLine` : cruise line IDs. Example: `"23"`
* `lineType` : line type IDs. Example: `"2"`
* `lineFamily` : line family IDs. Example: `"5"`
* `lineStatus` : line status IDs. Example: `"1"`
* `area` : monitoring area IDs. Example: `"12"`

### Retrieval

* `retrievalExclude` : platforms not retrieved. Example: `"on"`
* `retrievalCountry` : retrieval country ID. Example: `"250"`
* `retrievalStatus` : retrieval status IDs. Example: `"1,2"`
* `postRetrievalStatus` : post-retrieval status IDs. Example: `"3"`
* `retrievalStartDateFrom` : retrieval start date from. Example: `"2025-01-01"`
* `retrievalStartDateTo` : retrieval start date to. Example: `"2025-12-31"`
* `retrievalEndDateFrom` : retrieval end date from. Example: `"2025-01-01"`
* `retrievalEndDateTo` : retrieval end date to. Example: `"2025-12-31"`
* `retrievalLatFrom` : minimum retrieval latitude. Example: `"-45"`
* `retrievalLatTo` : maximum retrieval latitude. Example: `"45"`
* `retrievalLonFrom` : minimum retrieval longitude. Example: `"-180"`
* `retrievalLonTo` : maximum retrieval longitude. Example: `"180"`
* `endingCause` : ending cause IDs. Example: `"2,5"`

### Latest location

* `locDateFrom` : latest location date from. Example: `"2026-01-01"`
* `locDateTo` : latest location date to. Example: `"2026-12-31"`
* `locLatFrom` : minimum latitude. Example: `"-45"`
* `locLatTo` : maximum latitude. Example: `"45"`
* `locLonFrom` : minimum longitude. Example: `"-180"`
* `locLonTo` : maximum longitude. Example: `"180"`
* `locStatus` : location status IDs. Example: `"1"`
* `lastLocOnly` : latest location only. Example: `"on"`

### Observations

* `obsDataStatus` : observation status IDs. Example: `"1,2"`
* `obsDateFrom` : observation date from. Example: `"2026-01-01"`
* `obsDateTo` : observation date to. Example: `"2026-12-31"`
* `obsLatFrom` : minimum latitude. Example: `"-45"`
* `obsLatTo` : maximum latitude. Example: `"45"`
* `obsLonFrom` : minimum longitude. Example: `"-180"`
* `obsLonTo` : maximum longitude. Example: `"180"`
* `lastObsOnly` : latest observation only. Example: `"on"`
* `dmMin` : minimum delayed-mode percentage. Example: `"80"`
* `dmMax` : maximum delayed-mode percentage. Example: `"100"`

### Observation statistics

* `obsAdMeanPsalMin` : minimum mean PSAL adjustment. Example: `"0.1"`
* `obsAdMeanPsalMax` : maximum mean PSAL adjustment. Example: `"1.0"`
* `obsAdMeanPsalAbs` : absolute mean PSAL adjustment. Example: `"0.5"`
* `obsAdDevPsalMin` : minimum PSAL deviation. Example: `"0.01"`
* `obsAdDevPsalMax` : maximum PSAL deviation. Example: `"0.50"`
* `obsAdDevPsalAbs` : absolute PSAL deviation. Example: `"0.25"`

### Standby observations

* `yearsInStandby` : years in standby. Example: `"2"`
* `obsStandbyVariables` : variable IDs. Example: `"1,7"`
* `standbyObsExcludeAdjusted` : exclude adjusted observations. Example: `"on"`

### Platform operating configuration

* `totalCycleTime` : cycle time (hours). Example: `"240"`
* `minTotalCycleTime` : minimum cycle time. Example: `"120"`
* `maxTotalCycleTime` : maximum cycle time. Example: `"360"`
* `driftDepth` : drift depth (m). Example: `"1000"`
* `minDriftDepth` : minimum drift depth. Example: `"800"`
* `maxDriftDepth` : maximum drift depth. Example: `"2000"`
* `profileDepth` : profile depth (m). Example: `"2000"`
* `minProfileDepth` : minimum profile depth. Example: `"1000"`
* `maxProfileDepth` : maximum profile depth. Example: `"6000"`
* `surfaceTime` : surface time (minutes). Example: `"20"`
* `minSurfaceTime` : minimum surface time. Example: `"10"`
* `maxSurfaceTime` : maximum surface time. Example: `"30"`
* `sampleLevels` : number of sample levels. Example: `"50"`
* `minSampleLevels` : minimum sample levels. Example: `"30"`
* `maxSampleLevels` : maximum sample levels. Example: `"100"`
* `battery` : battery percentage. Example: `"80"`
* `trackingSystem` : tracking system ID. Example: `"2"`

### Variables and sensors

* `variables` : variable IDs. Example: `"1,2,7"`
* `variableExclude` : excluded variable IDs. Example: `"10"`
* `variableFamily` : variable family IDs. Example: `"3"`
* `variableMustMeasureAll` : require all variables. Example: `"on"`
* `subvariables` : subvariable IDs. Example: `"15,16"`
* `sensormodels` : sensor model IDs. Example: `"101,102"`
* `sensortypes` : sensor type IDs. Example: `"5,8"`
* `sensorfamilies` : sensor family IDs. Example: `"2"`
* `sensorSerialId` : sensor serial number. Example: `"A12345"`
* `maxSensorSerial` : maximum sensor serial. Example: `"99999"`
* `minimumSensorDepth` : minimum sensor depth (m). Example: `"100"`
* `maximumSensorDepth` : maximum sensor depth (m). Example: `"5000"`
* `noSensors` : platforms without sensors. Example: `"on"`

### Telecommunications

* `telType` : telemetry type IDs. Example: `"2"`
* `telServices` : telemetry service IDs. Example: `"4"`
* `telFormats` : telemetry format IDs. Example: `"1"`
* `telNum` : telemetry number prefix search. Example: `"3002"`
* `imei` : IMEI prefix search. Example: `"30023401"`
* `backupTelType` : backup telemetry type IDs. Example: `"2"`
* `backupTelServices` : backup telemetry service IDs. Example: `"3"`
* `backupTelFormats` : backup telemetry format IDs. Example: `"1"`
* `backupTelNum` : backup telemetry number. Example: `"8816"`
* `backupTelImei` : backup IMEI. Example: `"30023456"`

### Data assembly centres

* `dacs` : DAC IDs. Example: `"1,3"`
* `gdacs` : GDAC IDs. Example: `"1,2"`
* `notGdacs` : excluded GDAC IDs. Example: `"3"`
* `allDacs` : require all DACs. Example: `"1"`
* `allGdacs` : require all GDACs. Example: `"1"`
* `allNotGdacs` : exclude all GDACs. Example: `"1"`
* `noDmManager` : no delayed-mode manager. Example: `"on"`

### Sites

* `siteNames` : site IDs or names. Example: `"PAPA,BERMUDA"`
* `sitesLatest` : latest site only. Example: `"on"`

### Contacts

* `contacts` : contact IDs. Example: `"1000360"`
* `contactRoles` : contact role IDs. Example: `"243"`

### Geographic areas at deployment

* `seaRegions` : sea region IDs. Example: `"2"`
* `seaSubRegions` : sea subregion IDs. Example: `"15"`
* `sovereignties` : sovereignty IDs. Example: `"250"`
* `claims` : maritime claim IDs. Example: `"3"`
* `deplArgoDesignOceans` : Argo design ocean IDs. Example: `"1"`

### Geographic areas at latest location

* `latestLocSeaRegions` : sea region IDs. Example: `"2"`
* `latestLocSeaSubRegions` : sea subregion IDs. Example: `"15"`
* `latestLocSovereignties` : sovereignty IDs. Example: `"250"`
* `latestLocClaims` : maritime claim IDs. Example: `"3"`
* `latestLocArgoDesignOceans` : Argo design ocean IDs. Example: `"1"`

### Quality control

* `blacklist` : blacklist status. Example: `"1"`
* `pendingFeedback` : pending QC only. Example: `"on"`
* `qcErrorType` : QC error type IDs. Example: `"4"`
* `qcAction` : QC action IDs. Example: `"2"`
* `qcVariable` : variable IDs. Example: `"7"`
* `qcFeedbackType` : feedback type IDs. Example: `"5"`
* `warningsChecked` : warning review status. Example: `"1"`
* `warningCoastalState` : coastal state IDs. Example: `"250"`
* `warningDateFrom` : warning date from. Example: `"2026-01-01"`
* `warningDateTo` : warning date to. Example: `"2026-12-31"`
* `warningLastReportDateFrom` : last report date from. Example: `"2026-01-01"`
* `warningLastReportDateTo` : last report date to. Example: `"2026-12-31"`

### Notifications and batch processing

* `notifDateFrom` : notification date from. Example: `"2026-01-01"`
* `notifDateTo` : notification date to. Example: `"2026-12-31"`
* `batchRef` : batch reference prefix search. Example: `"REQ2026"`
* `batchStatus` : batch status IDs. Example: `"2"`

### Ice detection

* `iceDetect` : ice detection enabled. Example: `"on"`
* `noIceDetect` : no ice detection. Example: `"on"`

### Firmware and control hardware

* `softName` : firmware name. Example: `"OpenCPN"`
* `softVersion` : firmware version. Example: `"2.1.4"`
* `softFormat` : firmware format IDs. Example: `"1"`
* `ctrlBoard` : controller board name. Example: `"OpenLog"`
* `crtlBrdSerial` : controller board serial number. Example: `"CB-12345"`

> [!NOTE]
> `crtlBrdSerial` contains the spelling used by the current implementation and must be sent exactly as shown.

## Value conventions

### Identifier-list filters

The following kinds of filters generally expect one or more numeric identifiers as a comma-separated string:

```json
{
  "filters": {
    "programs": "12,45",
    "status": "1,2",
    "variables": "5,8,11"
  }
}
```

### Date-range filters

Date ranges are represented by separate `From` and `To` filters:

```json
{
  "filters": {
    "deplDateFrom": "2026-01-01",
    "deplDateTo": "2026-12-31"
  }
}
```

The same convention is used for observation, location, retrieval, warning, and notification dates.

### Geographic bounds

Bounding boxes use separate latitude and longitude limits:

```json
{
  "filters": {
    "deplLatFrom": "-60",
    "deplLatTo": "60",
    "deplLonFrom": "120",
    "deplLonTo": "-120"
  }
}
```

When the minimum longitude is greater than the maximum longitude, the search may be interpreted as crossing the antimeridian.

### Boolean-style filters

Boolean-style filters are normally enabled using `"on"`:

```json
{
  "filters": {
    "hasWigosId": "on",
    "wmoActive": "on",
    "lastObsOnly": "on"
  }
}
```

Some legacy filters use `"1"` instead:

```json
{
  "filters": {
    "allGdacs": "1"
  }
}
```

## Compatibility

This endpoint delegates filter processing to `PlatformFilterSubQueryBuilder`. New filters added to that builder may therefore become usable by the endpoint before they are added to this document.

The list above should nevertheless be treated as the documented public contract. New filter keys should be explicitly added here when introduced so that clients do not need to inspect the Java implementation.
