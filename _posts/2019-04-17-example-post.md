---
title: 'Example: Embedding Matplotlib Images'
date: 2020-12-21T00:00:00.000Z
published: true
tags:
  - Dataviz
  - Hvplot
  - Folium
  - Holoviews
excerpt: >-
  We produced some simple exploratory analysis of weather data, crime data, and
  census data using `HvPlot` ,`Folium, and `Wordcloud` packages...
toc: true
toc_sticky: true
read_time: true
altair-loader:
  altair-chart-1: charts/measlesAltair.json
hv-loader:
  hv-chart-1:
    - charts/temp.html
    - '300'
  hv-chart-2:
    - charts/sunHour.html
    - '300'
  hv-chart-3:
    - charts/visibility.html
    - '300'
  hv-chart-4:
    - charts/windspeed.html
    - '300'
  hv-chart-5:
    - charts/precip.html
    - '300'
  hv-chart-6:
    - charts/humidity.html
    - '300'
  hv-chart-7:
    - charts/crime.html
    - '500'
  hv-chart-8:
    - charts/Total_population.html
    - '400'
  hv-chart-9:
    - charts/White_population.html
    - '400'
  hv-chart-10:
    - charts/Median_household_income.html
    - '400'
  hv-chart-11:
    - charts/Median_contract_rent.html
    - '400'
folium-loader:
  folium-chart-1:
    - charts/distribution.html
    - '700'
---
## **Weather**

We produced some simple exploratory analysis of weather data using the `HvPlot` package:     
   
The following chart shows the changes in weather data during the six years (2015-2020), including temperature, body temperature, temperature difference, sunshine duration, visibility, wind speed, precipitation and humidity.  
      
<div id="hv-chart-1"></div>
<div id="hv-chart-2"></div>
<div id="hv-chart-3"></div>
<div id="hv-chart-4"></div>
<div id="hv-chart-5"></div>
<div id="hv-chart-6"></div>
   
It can be seen from the figure that part of the precipitation data is missing, so we excluded the precipitation data in the final modeling.   
   
## **Crime**

We then performed some simple exploratory analysis of our crime incidents data using the `HvPlot` package and `Folium` package:  

### Spatial Distribution of Crime in Philadelphia (Folium)

We visualized the spatial distribution for the crime incidents in Philadelphia. Most cases occurred in West Philadelphia, Southwest Philadelphia, Central Philadelphia and East Philadelphia.

<div id="folium-chart-1"></div>   
   
### Crime in Philadelphia (Hvplot & Wordcloud)
   
<div id="hv-chart-7"></div>   
   
A wordcloud with the top 40 keywords for crime types in Philadelphia has also been created. As can be seen from the following picture, violent crime and property crimes are the major contributors to the general rate of crime in Philadelphia, which is consistent with the information we got from NeighborhoodScout's analysis: the violent crime rate is one of the highest in the nation, across communities of all sizes (both large and small). Violent offenses tracked included rape, murder and non-negligent manslaughter, armed robbery, and aggravated assault, including assault with a deadly weapon.    
   
![wordcloud.png]({{site.baseurl}}/assets/image/wordcloud.png)


We have selected ten types of crimes that occur most frequently. They are:

**Count by type of crime**
- All Other Offenses	         (170487)
- Other Assaults	            (137504)
- Thefts	                 (130602)
- Vandalism/Criminal Mischief	    (87772)
- Theft from Vehicle	         (76206)
- Fraud	                    (64698)
- Narcotic / Drug Law Violations	 (50660)
- Aggravated Assault No Firearm	    (31576)
- Burglary Residential	         (30486)
- Robbery No Firearm	         (19530)


## **Census**

We also performed some simple exploratory analysis of our census data using the `HvPlot` package:     
  
Total population distribution:    
   
<div id="hv-chart-8"></div>   
   
White population distribution:    
   
<div id="hv-chart-9"></div>   
   
Median household income distribution:    
   
<div id="hv-chart-10"></div>   
   
Median contract rent distribution:     
   
<div id="hv-chart-11"></div>
