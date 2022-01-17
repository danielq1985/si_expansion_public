# SI Expansion 

Finding the right location to expand business.

### Background

The company I work with has been dominating the sprinkler service industry in Colorado Springs for the last 10 years. The 5-year plan is to expand to another location in a simalar market. With Colorado having 511 zip codes the question is, "Where do we go next?" 

### Analysis Overview
- How is performance distributed accross zip codes?
  - Where are our top performers?
- Who are our top performers?
- Finding our matching locations
- Presenting our findings

### Tech Used
- Programming: Python (libraries: )
- Data: Company CRM, Census API
- Visualization: Tableau

## How is performance distributed accross zip codes?
#### **Data:** CRM Data (2018-06-01-2021-09-28)
#### **Procedure:**
- Group data by zip codes, frequency, and monetary
  - Frequency: Total service visits
  - Monetary: Total dollar amount spent
- Rank each zip group based on frequency and monetary vales
  - This was achieved splitting each group into quartiles and assigning a score
  - Example: A zip group with the highest total dollar amount gets scored 1, being in the top quartile
- Assign label to each zip based on frequency and monetary values - Top, Mid, Low
  - Example: Zip code X has a frequency score of 1 and a monetary score of 1 a total of 2 - then labeled 'Top'
  - Example: Zip code Y has a frequency score of 2 and a monetary score of 1 a total of 3 - then labeled 'Mid'
  - Example: Zip code Z has a frequency score of 2 and a monetary score of 3 a total of 5 - then labeled 'Low'
- Where are our top performers?
  - Filter data by 'Top' performers label
  - Sort data by frequency count and monetary sum, keeping our top 5
    - Our top performing zips: 80919, 80920, 80906, 80921, 80132

#### **Findings:**
![alt text](/images/bar_groups.jpg)
![alt text](/images/hist_freq.jpg)
![alt text](/images/hist_mon.jpg)
![alt text](/images/group_stats.jpg)

Out of 54 zip codes in service only 13 are high performing, generating the majority of company revenue. 
For frequency count and monetary sum our top performing zips have the greatest degree of variance. 
Our low performing zips have the smallest degree of variance - we can see the min frequency is 1 and the max is 36. This may be caused by out-of-state customers with rental properties. 

## Who are our top performers?
This question will be answered by using demograhic data
#### **Data:** Census - American Community Survey 5-Year Data (2009-2019)
- The American Community Survey (ACS) is an ongoing survey that provides data every year -- giving communities the current information they need to plan investments and services. The ACS covers a broad range of topics about social, economic, demographic, and housing characteristics of the U.S. population.
- The 5-year estimates from the ACS are "period" estimates that represent data collected over a period of time. The primary advantage of using multiyear estimates is the increased statistical reliability of the data for less populated areas and small population subgroups.

#### **Procedure:**
- Retrieve data (API) for the following demographics:
  - Total population (B01001_001E) 
  - Median age (B01002_001E)
  - Home age median (B25035_001E) 
  - Median home value (B25107_001E)
  - Median household income the last 12 mo (B19013_001E)
  - Owner Occupided (B07013_002E)
- Use our top 5 performing zip codes to filter through all 511 zip codes 

![alt text](/images/top_zip_demo_chart.jpg)

## Finding our matching locations
This was achieved by creating a function that loops through all Colorado zip codes calculating the differences in demographics.


## Presenting our findings

https://public.tableau.com/views/si_expansion/LongDash?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link
