# Argo targets
## Background
The evolution of the argo program toward OneArgo has modified and complexify the design and target used by OceanOPS to monitor the program. At the time of writing (2024) we are in a transition phase toward OneArgo monitoring.

## Definitions
A **design** is the traduction of the scientific objectives into an operational implementation of the program (e.g. "*to acheive the scientific objective of the Argo program we need to implement such design*").

A **target** is the numerical objective toward the completness of the design. A target always refers to a design, a region and a network. Here we are differentiating the communication with the implementation target. While communication target are used to impact the audience with roung numbers, the implementation target are computed from the design. Below "target" refers to implementation target unless we explicitly refer to "communication target".

In this page, a **network** refers to the regroupement by float capacity (BGC, Core, Deep).

Along the life of the Argo program the scientific objectives of Argo have evolved, and so the designs, targets and networks.

This page aim to define the different elements participating to the monitoring of the Argo program.

## Former design and targets
### The initial Argo design
Design: Temperature and salinity profiles over the 2km of the ice free global ocean spacing of 300km on a 10 days interval.

This result in a target of **3085 operational core floats** drifting permanently over the ocean. Note that the target of 3000 floats was an communication objectives (not the real implementation objectif).
* Atlantic: 793 floats
* Indian: 697 floats
* Pacific Ocean: 1595 floats

This target is not visible anymore in the list ok KPI.

### The 2de Argo design.
The program extended to the polar oceans with the same time and space constrains and the marginal seas with a double float density, plus the consideration of minimum ice extension and usage (i.e. regular deployment in specific area like polynies).
This extension added:
* Southern Ocean: 376 floats
* Arctic Ocean: 69 floats
* Marginal Seas: 226 floats

Leading to a target of **3756 core floats**.
In the KPI section (ToW 2024), the 2de Argo design is the default desing (when not refering to **`2020`** or specific mission).

### The Argo 2020 design
The program extended it implementation objectif toward a double float density in the Western Boundary Currents (WBC) and in the tropical regions.
This extention added:
* WBC: 461 floats
* Tropical regions: 318 floats

Leading to a target of **922 core floats in the WBC** and **636 core floats in the tropical regions**.
This is currently identify by **`(2020)`** in the implementation section of the KPI.

### Note on the Argo Global Network
Argo Global is a network that include all floats (Core, BGC, Deep, Argo Eq.).
Note that Argo Core is a network that consider only core floats.

## OneArgo design and targets
OneArgo design is the combination of the (2de) `Argo design` and the `Argo 2020 design` (see above) overlaped by the design of the new missions of Argo (Deep and BGC).

### OneArgo BGC design and target.
Design: A full (i.e. T/S/Chla/Optical-Backscatter/PH/N/Irradiance/O2) BGC floats every 6°X6°.

This result in a target of **912 BGC floats**. This is slightly different from the 1000 floats often used as communication target.
In 2025, the BGC design has been reviewed and the target become 1000 floats

### OneArgo Deep design and target
Design: In the region below 2000m, every 5°X5°, a deep float should operate.

This result in a target of **1069 Deep floats**. This target is slightly different from the 1200 deep floats often used as communication target.
In 2025, the Deep design has been reviewed to be closer the the "communication target". New target is 1254 deep floats.

### OneArgo Core design and target
OneArgo Core design is the combination of the (2de ) **`Argo desing`** and the **`Argo 2020 design`**.

This result in a target of **`3756 floats (Argo) + (922+636)/2 (Argo 2020) = 4535 floats`** measuring T and S.

Note that this number is slightly different from the communication target of 4700 floats.

Since 2025 and the new design for BGC and Deep, the target for the Argo Core network in the OneArgo design is **4535 - 1000 - 1254 = 2281 floats** (without the BGC and Deep floats).

Currently (ToW 2024) there is no reference of OneArgo Core target in the OceanOPS KPI system. 

## Evolution in the KPI system
For each implementation KPI, the design should be identify into brackets, like `Activity (2020)`. We should be able to select the design (Argo, Argo 2020, OneArgo Deep, OneArgo BGC, OneArgo Core, OneArgo).

* The targets related to the implementation of OneArgo Core, OneArgo Deep and OneArgo BGC should be created.
* The target of OneArgo should be created.
* The Argo Deep design should become OneArgo Deep, no impact on the activity target.
* The Argo BGC design should become OneArgo BGC, no impact on the activity target.
* The activity target for OneArgo core should be set to 2554 floats.
* The activity target for OneArgo should be set to 4535 floats.
