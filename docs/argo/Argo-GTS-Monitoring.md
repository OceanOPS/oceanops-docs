# How do we monitor Argo on the GTS ?

Historically, we upload files delivered by météo france (daily and monthly), supposed to capture Argo on the GTS. This procedure is still operational, but we have loose contact with Météo France on this regard (at the time of writting - 20241017) and we are not sure the Météo-France extraction of the GTS cover all the following headers and bulletin.

Argo use the BUFR sequence 3.15.003 to publish on the GTS.

Origine of the bulletin for Argo floats are:
* AMMC – Australia
* BABJ – China
* CWOW - Canada
* DEMS - India
* EGRR - UK
* KWBC – USA
* LFVW – France CLS*
* LFVX - Coriolis
* RJTD - Japan
* RKSL - Korea

Bulletin Header are : 
* IOPB01
* IOPB02
* IOPB03
* IOPB04
* IOPB05
* IOPC01
* IOPC02
* IOPC03
* IOPC04
* IOPC05
* IOPD01
* IOPI01
* IOPJ01
* IOPJ02
* IOPJ03
* IOPJ04
* IOPJ05
* IOPX01
* IOPX02
* IOPX03
* IOPX11
* IOPK01
* IOPK02
* IOPK03
* IOPL01
* IOPL02
* IOPL03
* IOPX92

For Argo floats submitted with BUFR format "TTAAii" is "IOPXii". 
* IO = Data type: oceanographic information
* PX = Argo BUFR
* ii = bulletin sequence number (00-99) used to differentiate multiple bulletin of the same type.



