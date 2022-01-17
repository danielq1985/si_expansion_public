# SI Expansion 

Finding the right location to expand business.

### Background

The company I work with has been dominating the sprinkler service industry in Colorado Springs for the last 10 years. The 5-year plan is to expand to another location in a simalar market. With Colorado having 511 zip codes the question is, "Where do we go next?" 

### Analysis Overview
- Where are our current top performing locations?
- Who are our top performers?
- Finding our matching locations
- Presenting our findings

### Tech Used
- Programming: Python (libraries: )
- Data: Company CRM, Census API
- Visualization: Tableau

## Question: Where are our current top performing locations?
** Data: ** CRM Data (2018-06-01-2021-09-28)
Procedure:
- Group data by zip codes
- Agg groups by counting appointments per zip group
- Agg groups by dollar total per zip group
- Merge dataframes
- Rank each zip group based on frequency and monetary vales
  - This was achieved splitting each group into quartiles and assigning a score
  - Example: A zip group with the highest total dollar amount gets scored 1, being in the top quartile
- Assign label to each zip based on frequency and monetary values ('Top', 'Mid', 'Low')
  - Example: Zip code A has rankings 1 frequency and 1 monetarty giving it a score total of 2 is labeled 'Top'

Findings:
dist plots for total freq and mon, stats for total zips
Bar plot for group totals matplotlib
distplot stacked/colored for groups
stats for each group

## Who are our top performers?
This will be achieved by using the public Census API retriencing demogrpahics. 

Specific dataset used: American Community Survey 5-Year Data (2009-2019)

- The American Community Survey (ACS) is an ongoing survey that provides data every year -- giving communities the current information they need to plan investments and services. The ACS covers a broad range of topics about social, economic, demographic, and housing characteristics of the U.S. population.

- The 5-year estimates from the ACS are "period" estimates that represent data collected over a period of time. The primary advantage of using multiyear estimates is the increased statistical reliability of the data for less populated areas and small population subgroups.

The ACS 5-Year litterally has thousands of different variables, but we will using:
- Total population (B01001_001E) 
- Median age (B01002_001E)
- Home age median (B25035_001E) 
- Median home value (B25107_001E)
- Median household income the last 12 mo (B19013_001E)

Request Census data via API, convert JSON to pandas dataframe


The demographics of our top zips


## Finding our matching locations
This was achieved by creating a function that loops through all Colorado zip codes calculating the differences in demographics.


## Presenting our findings

https://public.tableau.com/views/si_expansion/LongDash?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link
