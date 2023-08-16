# An Analysis of Dollar Stores in Tennessee

## Table of Contents


1. [Overview](#overview)
2. [Data Question](#dataquestion)
3. [Methodology](#methodology)
4. [Technologies](#technologies)
5. [Data Sources](#datasources)
6. [Conclusion](#conclusion)




<a name="overview"></a>
## Overview
Dollar store locations have exploded over the past two decades, especially in rural areas that typically do not see much retail/grocery sector growth.   This project looks at the relationship between county-level metrics and the number of dollar store locations in a given Tennessee County. The goal of this analysis was to examine the correlation of dollar store locations and the physical and financial health a given county in the State of Tennesee, potentially providing insight into the strategies of the three largest companies: Dollar General, Dollar Tree, and Family Dollar. 

<a name="dataquestion"></a>
## Data Question
  Is there a relationship between the number of dollar store locations and the metrics of a given Tennessee County? Which counties have the most dollar stores and how does this correlate to poverty, obesity, food security and median income?

<a name="methodology"></a>
  ## Methodologies
  #### Gathering the Data
  Utilizing the United States Census Bureau's 2020 Decennial Census API, I imported the population for each county in Tennessee. (P1_001N) https://api.census.gov/data/2020/dec/dhc/variables.html

  Utilizing the United States Census Bureau's 2020 Small Area Income and Poverty Estimates (SAIPE) API, I imported 2020 estimates on household median income and poverty rates(all ages) for each county in Tennessee. (SAEMHI_PT, SAEPOVRTALL_PT) https://api.census.gov/data/timeseries/poverty/saipe/variables.html
  
  This project utilitzes census data and estimates from 2020.

  Utilizing the Centers for Disease Control and Prevention's Diabetes Surveillance System, I exported the table for 2020 estimated obesity percentage for adults aged 20+ for each county in Tennessee. 
  https://gis.cdc.gov/grasp/diabetes/diabetesatlas-surveillance.html#
  
  While searching for data to use with the Census metrics I came across http://www.poi-factory.com where I was able to locate location listings for each major dollar store brand.

  Located https://www.countyhealthrankings.org/ which used the U.S. Department of Agriculture's Food Environment Atlas (https://www.ers.usda.gov/data-products/food-environment-atlas/) to pull the percentage of residents who are food insecure in each Tennessee County in 2020.
  
  #### Cleaning the Data

  Initially formatted columns for Dollar General, Dollar Tree, and Family Dollar locations in excel, then imported to Python for further cleaning. I then utilized merges while dropping redundant columns to combine all dollar store locations in Tennessee for the three major brands. 

  Imported metrics for the population, household median income, and poverty rate for each county in Tennessee via US Census API. Cleaned tables by dropping unncessary columns and renaming variables appropriately. Merged these metrics into one data frame to then merge onto the concatenated dollar store locations data frame.

  Imported obesity metrics and merged metric onto fully concatenated dollar store locations with metrics data frame. 



  #### Analysis
  Imported Tennessee zip codes by county and merged to Dollar Store data frame to reach a count of dollar stores by county. 

  Concatenated metrics of population, household median income, and poverty rate with count of dollar stores by county. 

  While analyzing the concatenated dollar store location data frame, I decided on the creation of two additional metrics, dollar stores per capita and dollar stores per 10,000 people. This assisted in analyzing the prevelance of dollar stores in a given Tennessee County. This normalized metric allowed for a more accurate comparison of counties regardless of population. 

  Brought in food insecurity percentage by Tennessee County and merged onto concatenated dollar store location data frame and dollar stores by county data frame.

  Ran .corr() function on variables in count of dollar stores by county dataframe to obtain correlation coefficients on multiple variables.

  Ran scatterplots using seaborn in Python to visualize correlation between stores per 10,000 people and median household income, obesity percentage, and food insecurity percentage.

  Upon importing data to Tableau and plotting locations withing Tennessee Counties, I noticed multiple discrepencies with the number of plots in a given county and the count of dollar stores in that county.

  Following further investigation, multiple zip codes in Tennessee straddle multiple counties, therefore the count of dollar stores by county was slightly skewed.

  Utilized geojson file (https://hub.arcgis.com/datasets/b3b22bda38d54d0686efb4a9d60c8d1b/explore?showTable=true) for Tennessee County areas and performed geospatial join on Dollar Store locations.

  Repeated analysis and respective cleaning on corrected county dollar store locations then imported to Tableau. 

  #### Visualizations
  Imported dollar store locations with metrics data frame to Tableau to visualize locations and metrics on a map of Tennessee.

  Plotted each dollar store location with county borders then created separate maps for each variable.

  Used variables to display as appropriate gradient on county borders to visualize any correlation. 

  Created story from maps and charts to present findings and observations.


<a name="technologies"></a>
## Technologies
  Excel: Preliminary column cleaning and data organization

  Python: pandas, geopandas, numpy, seaborn, matplotlib, requests, folium

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

   TN Counties geojson: https://hub.arcgis.com/datasets/b3b22bda38d54d0686efb4a9d60c8d1b/explore?showTable=true

   Special thanks to user Mahoney and Jonathan Melby at POI-factory.com for their volunteer work. Their updated location data sets were a key part of this analysis.


<a name="conclusion"></a>
## Conclusion

Although the number of dollar stores is very high among counties with high obesity and poverty rates, it is misleading due to the population metric. Any business will target high population areas with more stores in an attempt to capture the highest portion of market share, therefore it is expected that heavily populated counties will have more dollar stores. This is why the creation of the dollar stores per 10,000 people metric was so imperative, as it normalized the population metric when analyzing the data.


  #### Notable Observations:
   1.) There is a weak negative correlation between stores per 10,000 people and household median income.

   2.) There is a weak positive correlation between stores per 10,000 people and food insecurity percentage. 

   3.) There is a weak positive correlation between stores per 10,000 people and poverty rate.

   4.) Clay County had the highest number of stores per 10,000 people, with 5.28. Clay County has three Dollar Generals and one Family Dollar with a population of 7581.

   5.) This is in contrast to a county such as Williamson, which ranks last out of 95 counties with a stores per capita metric of .363. Williamson County has a population just under 250,000, but is only home to five Dollar Generals and four Dollar Trees. 

   6.) Rural counties in general have more dollar stores per 10,000 people than urban counties. For example, Davidson County (Nashville) has 76 total stores, with stores per 10,000 people at 1.06. Where as a county such as Pickett only has 2 stores with a population just over 5000 equating to four stores per 10,000 people.

   7.) Trousdale, Moore, and Van Buren counties are the only three counties with one store and they are all Dollar Generals.
       

The relative most notable and highest correlation coefficient is between the variables of stores per 10,000 people and household median income with a correlation coefficient of -0.553. That is, as the number of stores per 10,000 people increases, median household income decreases. 

Not to say the number of dollar stores in a given county causes a decrease in household median income, but it does provide some insight on the growth strategies of dollar store companies. Rural counties typically have worse metrics and fewer resources in general when compared to urban counties, usually due to the lack of funding and resources from a smaller tax base. Dollar store companies most likely choose these locations due to a lack of competition and because they see a gap they can fill in regard to resources for local residents. Not every county has an easily accessible large scale grocer, and dollar stores seem to have jumped on the opportunity to fill the gap in recent years. 