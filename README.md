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

## Where are our current top performing locations?
The CRM data used is from 2018-06-01-2021-09-28 dividing service calls by zip code

The metrics we will use to find our top performing zips:
- Frequency: How many times were we out to service?
- Monetary : What was the total amount of money spent?

How many zip codes are being serviced?


Total frequencies for each zip code. Plot distribution.


Total dollars spent for each zip code. Plot distribution


Both dataframes were then mereged into 'df_f_m'

Rank each zip based on Frequency and Monetary values. Assign score total.


Label each zip based on rank.


Assigning rank and labels to each zip code is useful in plotting findings.


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
