# IOC resolution notfications
## Deployment notification
### The IOC Resolution
IOC Resolution XX-6 ([IOC, 1999](https://www.ocean-ops.org/share/Argo/Doc/IOC_Resolution_XX-6.pdf)) requested Argo implementers to notify, reasonably in advance and through appropriate channels, any Argo float deployment in the high seas that might drift into Member States EEZ. Guidelines detailed in the  IOC Resolution EC-XLI.4 ([IOC, 2007](https://argo.ucsd.edu/wp-content/uploads/sites/361/2021/09/EC-XLI.4.pdf)).

Since 2018, the fifty-first session of the IOC Executive Council decided to allow the extention of Argo measurement capability to the 6 BGC variables. Official document is available here: [IOC resolution EC - LI](https://argo.ucsd.edu/wp-content/uploads/sites/361/2022/04/EC51-2A9-Argo-_e.pdf)

### Implementation at OceanOPS
To that end, Argo National Focal Points (NFPs) were designated by IOC Member States and WMO Members, following joint IOC-WMO circular letters, the latest is dated from 2016. The list and details of Argo NFPs is available at: http://www.ocean-ops.org/board?t=Argo&groupid=22 . Any update on Argo NFPs designation should be sent by IOC national delegations to the IOC secretariat: ioc-secretariat@unesco.org.
Sometimes, the change in Argo NFP are not notified to OceanOPS and the list can not be up to date. The reference document of GOOS national focal points is available here: https://goosocean.org/document-list/182 .

### Notification details
All Argo NFP receive a notification of any Argo deployment when float is notified at OceanOPS through the mailing list argo-notif@groups.wmo.int .
This notification, titled `[WMO - argo-notif] New Argo Deployment Notification` contain the information related to the deployment. 

### How to update the Argo National Focal Points

## EEZ notification
### The IOC Resolution
IOC Resolution EC-XLI.4 ([IOC, 2008](https://www.ocean-ops.org/share/Argo/Doc/XLI-4.pdf)) offered then the possibility to coastal states, through official request to IOC/UNESCO secretariat, to be formally and bilaterally notified of float drift into its EEZs by implementers. 
The following Member States have made such a request: Argentina, Brazil, Chile, China, Ecuador, Egypt, Greece, India, Peru, Russia, Tunisia, Turkey.

### Implementation at OceanOPS
OceanOPS has implemented a warning system which is routinely checking the floats drift in these EEZs and generate reports for implementers so they can - when appropriate - notify the coastal state. The OceanOPS Information System routinely checks if any float's latest location is closer than 100
nautical miles from the declared EEZs of these 12 coastal states (source: www.maritime boundaries.com). When the intersection matches (through a Geographical Information System analysis), the system logs the event for this float and the concerned coastal state.
Every week, a summary report is sent to all concerned implementers, including all floats approaching a given coastal state, and contact details for the Argo NFPs. Implementer has the action to acknowledge receipt of this on the OceanOPS website, float per float, and take any required step (e.g., a bilateral notification). As long as this acknowledgment is not made, floats will continue to appear in the reports. If acknowledgment is made, the next iteration of the warning system will omit that float for that coastal state. A float is flagged once and only once for a
given coastal state.
### Notification details.
The notification is send to the Program Manager of the program.
The Argo National Focal Point contact details of the 12 countries are registerd in the [Argo National Focal Point user group](http://www.ocean-ops.org/board?t=Argo&groupid=22).

## List of IOC resolutions
* IOC Resolution XX-6 ([IOC, 1999](https://www.ocean-ops.org/share/Argo/Doc/IOC_Resolution_XX-6.pdf))
* IOC Resolution EC-XLI.4 ([IOC, 2007](https://argo.ucsd.edu/wp-content/uploads/sites/361/2021/09/EC-XLI.4.pdf))
* IOC Resolution EC-LI ([IOC, 2018](https://argo.ucsd.edu/wp-content/uploads/sites/361/2022/04/EC51-2A9-Argo-_e.pdf))

# DMQC feedbacks
## argo greylist
Coriolis is running analysis and QC check routinely. On a monthly basis, Coriolis send us a file with new float to be added to the grey list. This file must be processed by us.
### procedure

## Min Max alerts
Coriolis is running on a hourly basis on every new profile reaching the GDAC a analysis called "min/max analysis" where every T and S measurement of the profile is compared to a min and max value for this lat, lon and depth.
On a monthly basis, Coriolis provide OceanOPS a list of the profile in alert. OceanOPS process this file to send warnings to DMO attached to the float or to the program if no DMO is attached to the float. 
In the near future, warrning will be send to DMCP.
DMO then have the capacity to report about the alert on the OceanOPS website.
### procedure

## Altimeters alerts
Every 6 months, CLS produced an analyses called "Altimeters analysis" where sea surface high is computed from T/S profiles and compared to altimetery. Profiles that doesn't pass the comparison are put it alert. The list of alert profile is send by CLS to OceanOPS and processed by OceanOPS similarly to the "Min/Max analysis" in order to warn DMO/DMCP of the concerned floats.
### procedures
In terms of procedure, files are deposit on ifremer ftp server (argo gdac) and OceanOPS use those files to produce the warnings.

# Other alerts, warnings and notifications
## Deployment plan reminder
## No data (to be implemented)
OceanOPS produce an alert for floats registered (i.e. notified at OceanOPS), with deployment date older than 2 months and not producing data. Floats with the "Ice_detection software" are excluded from the alerts.
## Metadata warnings

## Ice detection procedure

IN PROGRESS 


OceanOPS is running an ice detection alert when float is approaching an ice covered area.
We use this ice product https://noaadata.apps.nsidc.org/NOAA/G02135/

When a float is approaching 100nm of an ice region, the procedure call an event 'iced' for the float.

`This procedure has to be re-deployed since it is broken after migration in Feb 2024`

Ideally we should use this ice event to turn the activity criterion to 365 days instead of 30 days.