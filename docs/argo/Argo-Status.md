# Argo Satus timeline
## Probable
When a plan only have a deployment date and location (warning: Location can be set to Lat = 0, Lon = 0 by default).  No ship is needed.

## Confirmed
When a plan have a ship a deployment date and a location.

## Registered
When a float is notified.

## Operational
When registered and data younger than the activity criteria available at GDAC.
By default activity criteria is 30 days for all floats.
When float latitude <=-65S and >=60N and the Ice Detection software is "activated" onboard the activity criteria is switch to 365 days.

## Inactive
When data younger than the activity criteria not available at GDAC.
By default closure criteria is 5 years for all floats.

## Closed
If Inactive for the duration of the closure criteria.