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
  Is there a relationship between the number of dollar store locations and the health metrics of a given Tennessee County? Which counties have the most dollar stores and does this correlate to high poverty, high obesity, and low median income?

<a name="methodology"></a>
  ## Methodologies
  #### Gathering the Data
  While searching for data to use with the Census metrics I came across http://www.poi-factory.com where I was able to locate location listings for each major dollar store brand. Utilizing the United States Census Bureau's API, I imported metrics to Python for the median income and poverty rate for each county in Tennessee. This project utilitzes census data from 2020 as it contains the most accurate hard numbers rather than an estimate from a non census year. 

  #### Cleaning the Data

  Cleaned and formatted columns for Dollar General, Dollar Tree, and Family Dollar locations in excel, then imported to Python for further cleaning. I then utilized merges while dropping redundant columns to combine all dollar store locations in Tennessee for the three major brands. 

  Imported metrics for the population, household median income, and poverty rate for each county in Tennessee from the US Census API. Merged these metrics into one data frame to then merge onto the concatenated dollar store locations data frame.

  Imported obesity metrics from the Center for Disease Control and merged metric onto fully concatenated dollar store locations with financial metrics data frame. 
  The obsesity rate metric is for the year 2020, and only includes adults aged 20+.

    
  #### Analyzing the Data
  Imported Tennessee zip codes by county and merged to Dollar Store DataFrame to reach a count of dollar stores by county. 

  Concatenated metrics of population, household median income, and poverty rate with count of dollar stores by county. 

  While analyzing the concatenated dollar store location data frame, I decided on the creation of two additional metrics, dollar stores per capita and dollar stores per 10,000 people. This assisted in analyzing the prevelance of dollar store prevelance in a given Tennessee County. This normalized metric allowed for a more accurate comparison of counties regardless of population. 

  Once the prevelance of stores was evident in the counties, I was able to start formulating hypotheses on the market strategy in regard to locations of these companies.


  #### Visualizing the Data 

<a name="technologies"></a>
## Technologies

Excel: Preliminary Column cleaning and organization
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


<a name="conclusion"></a>
## Conclusion

Although the number of dollar stores is very high among counties with high obesity and poverty rates, it is misleading due to the population metric. Any business will target high population areas with more stores in an attempt to capture the highest portion of market share, therefore it is expected that heavily populated counties will have more dollar stores.