# jared-capstone

## Table of Contents


1. [Overview](#overview)
2. [Data Question](#dataquestion)
3. [Methodology](#methodology)
4. [Technologies](#technologies)
5. [Data Sources](#datasources)
6. [Conclusion](#conclusion)




<a name="overview"></a>
## Overview
Dollar store locations have exploded over the past two decades, especially in rural areas that typically do not see much retail/grocery sector growth.   This project looks at the relationship between county-level metrics and the number of dollar store locations in a given Tennessee County. The goal of this analysis would be to examine the impact of dollar store locations on the physical and financial health a given county in the State of Tennesee, potentially providing insight into the strategies of the three largest companies: Dollar General, Dollar Tree, and Family Dollar. 

<a name="dataquestion"></a>
## Data Question
  Is there a relationship between the number of dollar store locations and the health metrics of a given Tennessee County? Which counties have the most dollar stores and how does this correlate to 
  poverty, obesity, food security and median income?

<a name="methodology"></a>
  ## Methodologies
  #### Gathering the Data
  Utilizing the United States Census Bureau's 2020 Decennial Census API, I imported the population for each county in Tennessee. (P1_001N) https://api.census.gov/data/2020/dec/dhc/variables.html

  Utilizing the United States Census Bureau's 2020 Small Area Income and Poverty Estimates (SAIPE) API, I imported 2020 estimates on household median income and poverty rates(all ages) for each county in Tennessee. (SAEMHI_PT, SAEPOVRTALL_PT) https://api.census.gov/data/timeseries/poverty/saipe/variables.html
  
  This project utilitzes census data and estimates from 2020.

  Utilizing the Centers for Disease Control and Prevention's Diabetes Surveillance System, I exported the table for 2020 estimated obesity percentage for adults aged 20+ for each county in Tennessee. 
  https://gis.cdc.gov/grasp/diabetes/diabetesatlas-surveillance.html#
  
  While searching for data to use with the Census metrics I came across http://www.poi-factory.com where I was able to locate location listings for each major dollar store brand.

  Located https://www.countyhealthrankings.org/ which used the U.S. Department of Agriculture's Food Environment Atlas (https://www.ers.usda.gov/data-products/food-environment-atlas/) to pull the percentage of residents who are food insecure for each Tennessee Counties in 2020.
  
  #### Cleaning the Data

  Initially formatted columns for Dollar General, Dollar Tree, and Family Dollar locations in excel, then imported to Python for further cleaning. I then utilized merges while dropping redundant columns to combine all dollar store locations in Tennessee for the three major brands. 

  Imported metrics for the population, household median income, and poverty rate for each county in Tennessee via US Census API. Cleaned tables by dropping unncessary columns and renaming variables appropriately. Merged these metrics into one data frame to then merge onto the concatenated dollar store locations data frame.

  Imported obesity metrics and merged metric onto fully concatenated dollar store locations with metrics data frame. 



  #### Analyzing the Data
  Imported Tennessee zip codes by county and merged to Dollar Store data frame to reach a count of dollar stores by county. 

  Concatenated metrics of population, household median income, and poverty rate with count of dollar stores by county. 

  While analyzing the concatenated dollar store location data frame, I decided on the creation of two additional metrics, dollar stores per capita and dollar stores per 10,000 people. This assisted in analyzing the prevelance of dollar stores in a given Tennessee County. This normalized metric allowed for a more accurate comparison of counties regardless of population. 

  Brought in food insecurity percentage by Tennessee County and merged onto concatenated dollar store location data frame and dollar stores by county data frame.

  Ran .corr() function on variables in count of dollar stores by county dataframe to obtain correlation coefficients on multiple variables.

  Ran scatterplots using seaborn in Python to visualize correlation between stores per 10,000 people and median household income, obesity percentage, and food insecurity percentage.



  #### Visualizing the Data 
  Imported dollar store locations with metrics data frame to Tableau to visualize locations and metrics on a map of Tennessee.

  Plotted each dollar store location with county borders then created separate maps for each variable.

  Used variables to display as appropriate gradient on county borders to visualize any correlation. 

  Created story from maps and charts to present findings and observations.


<a name="technologies"></a>
## Technologies

Excel: Preliminary Column cleaning and data organization
Python: pandas, numpy, seaborn, matplotlib
Tableau: Visualization



<a name="datasources"></a>
## Data Sources

   #### Imported
   Dollar General US Store Locations:  http://www.poi-factory.com/node/30072
   
   Dollar Tree US Store Locations:  http://www.poi-factory.com/node/23597
   
   Family Dollar US Store Locations:  http://www.poi-factory.com/node/16577 
   
   TN County Zip Codes: https://www.whereig.com/usa/zipcodes/tennessee.html#
   
   US Census Bureau API : https://www.census.gov/data/developers.html

   US Obesity Rates by County: https://gis.cdc.gov/grasp/diabetes/diabetesatlas-surveillance.html#

   Food Security in Tennessee: https://www.countyhealthrankings.org/explore-health-rankings/tennessee?year=2023&tab=1&measure=Food+Environment+Index


<a name="conclusion"></a>
## Conclusion

Although the number of dollar stores is very high among counties with high obesity and poverty rates, it is misleading due to the population metric. Any business will target high population areas with more stores in an attempt to capture the highest portion of market share, therefore it is expected that heavily populated counties will have more dollar stores. This is why the creation of the dollar stores per 10,000 people metric was so imperative, as it normalized the population metric when analyzing the data.

Notable Observations:
  1.) There is a weak negative correlation between stores per 10,000 people and median income.
  2.) There is a weak positive correlation between stores per 10,000 people and food insecurity percentage. 
  3.) Meigs County had the highest count of stores per 10,000 people at 5.48. Household median income was 49242, poverty rate was 16 percent, food insecurity was 15% and obesity rate was 21.5 percent. With a population just under 13,000,  it is home to six Dollar Generals and one Dollar Tree. 
  4.) Williamson County had the lowest count of stores per 10,000 people at .32. Household median income was 118257, poverty rate was 4 percent, food insecurity was 6% and obesity rate was 25.9 percent. With a population just under 250,000, it is home to five Dollar Generals and three Dollar Trees. 