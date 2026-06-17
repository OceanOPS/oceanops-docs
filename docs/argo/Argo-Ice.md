# Argo ICE
## Allocate the "ice detection software" metadata to a float.
When a float is equipped with the "Ice Sensing software", the boolean is filed as "On".
To allocate the "ice detection software" to a float, we look in the "SPECIAL_FEATURES" variable and if the value is "ice detection software" then the bollean is true. Otherwise it is false.

## Suggested change in the allocation scheme
We should look in the "TECHNICAL_param_name" and look for values with prefix "CONFIG_IceDetection". If it is there, then the "ice detection software" metadata should be turned on.

## Impact on Operational floats
A float equipped with the "Ice detection software" and operating North of 60N and South of 65°S will have a activity criterion of 365 days.

## Iced event
see: https://github.com/OceanOPS/helpdesk/wiki/Argo-alert,-warning-and-notification-system#ice-detection-procedure