# Argo ENDING CAUSE
The information about the end-of-life of a float is stored here: 
1. Ending  cause ([Reference table](https://www.ocean-ops.org/api/help/?param=endingcause))
2. Retrieval comments (free text)

## In case of a single ending cause 
1. Ending cause = single ending cause of the float
2. Retrieval comments = comments

Example: <br>
Information sent to OceanOPS: <br>
ending_cause = "sensor_ctd"<br>
ending_cause_comment = "CTD issues"<br>

How the information is stored in OceanOPS: 
1. Ending cause = Defect of the primary CTD sensor (argo_ref = sensor_ctd)
2. Retrieval comments = "CTD issues"

## In case of multiple ending causes 
1. Ending cause = primary ending cause of the float
2. Retrieval comments = "Multiple_ending_cause: ending_cause1, ending_cause2, ending_cause3, ..., comments"

Example: <br>
Information sent to OceanOPS: <br>
ending_cause = "ballast, telemetry" <br> 
ending_cause_comment = "APEX air bladder issue: loss of air inside the float's hull. The loss of air would impact the ability for the float to fill the air bladder when at the surface and possibly reduce the efficiency of the file telemetry" <br>

How the information is stored in OceanOPS: 
1. Ending cause = Ballast issues (argo_ref = ballast)
2. Retrieval comments = "Multiple_ending_cause: ballast, telemetry, APEX air bladder issue: loss of air inside the float's hull. The loss of air would impact the ability for the float to fill the air bladder when at the surface and possibly reduce the efficiency of the file telemetry"


## When a retrieval comment is already existing in the OceanOPS database
When a retrieval comment is already existing in the OceanOPS database, we concatenate all the available information. 

Example: <br> 
Before the update, the retrieval comment was ""A sailing boat has found an Argo buoy drifting in the sea and have left in the nautical club of Ciudadela in Menorca, Balearic islands". <br><br>
After the update: 
1. Ending cause = Battery exhausted (argo_ref = battery_end_of)
2. Retrieval comments = "A sailing boat has found an Argo buoy drifting in the sea and have left in the nautical club of Ciudadela in Menorca, Balearic islands
Multiple_ending_cause: battery_end_of,stuck_on_surface,recovered_unintentionnally"
