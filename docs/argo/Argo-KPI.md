# Implementation
## Coverage

* **Coverage** and **Coverage Sum** and **Coverage potenatial** are three indicators used to assess the performance of Argo float observations.

## Monthly coverage and the annual coverage: 

* Annual coverage is the mean of each monthly coverage.
* Monthly coverage are computed every month. Monthly coverage are always computed in two steps:

Step 1: Compute the number of observations per design element (Procedure update_gis.argo_design33_obs_month() )

Step 2: Compute coverage metrics. 

We compute 3 different coverage metrics:
* **Coverage** (“Well-sampled” elements only):  
Only count elements where the number of observations per month/(3*target) >=1/total number of elements. Note that this coverage is the continuity of the "coverage" indicator before evolution of the coverage metrics in 2026.
* **Coverage, sum**:  
For each element, compute the number of observations per month/(3*target), capped at a maximum of 1. Then sum these values across all elements/total number of elements. Note that this coverage is the continuity of the "coverage, sum" indicator before the evolution of the coverage metrics in 2026.
* **Coverage potential**:  
For each element, compute the number of observations per month/(3*target), not capped at a maximum of 1. Then sum these values across all elements/total number of elements. This coverage provide a indication or the potential performance of Argo is the floats where perfectly distributed.

 
# Data flow
## Quality
Every month, the [index file](../Argo-Index-files#argo_synthetic-profile_detailled_indextxt) is checked and A quality profil are counted. The ratio between A quality profile and all profile is displayed in the quality KPI for all variables.

We need to check if the computation is re-done regularly (e.g. once a year) to take into account improvement in the overall data quality of the data base.

# Data uptake
This plot is produced by Megan Scanderberg (SIO). She follow this methodology.  
To find Argo papers, she search through :  
1. journal websites, 
2. papers citing by the Wong paper, 
3. google scholar for the word ‘argo’ anywhere in the text.  
4. I then go through each article and discover if Argo data was actually used or just mentioned.  
If it was used in a data collection including other data like EN4, WOA, etc, I include the paper.

After AST, it is recommended to ask her the update of the whole time serie (as some papers might pops up later and the procedure being revised).
Then the data are send to OceanOPS metadata Clerk and updated.