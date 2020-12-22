---
published: true
date: 2020-12-21T00:00:00.000Z
tags:
  - dataviz
  - hvplot
  - holoviews
altair-loader:
  altair-chart-1: charts/measlesAltair.json
hv-loader:
  hv-chart-1:
    - charts/temp.html
    - '400'
  hv-chart-2:
    - charts/sunHour.html
    - '400'
  hv-chart-3:
    - charts/visibility.html
    - '400'
  hv-chart-4:
    - charts/windspeed.html
    - '400'
  hv-chart-5:
    - charts/precip.html
    - '400'
  hv-chart-6:
    - charts/humidity.html
    - '400'
  hv-chart-7:
    - charts/crime.html
    - '400'
toc: true
toc_sticky: true
read_time: true
folium-loader:
  folium-chart-1:
    - charts/distribution.html
    - '400'
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

We visualized the spatial distribution for the crime incidents in Philadelphia. At first sight， most of the Airbnb are located in Manhattan and brooklyn.

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

- See the [raw source code](https://raw.githubusercontent.com/MUSA-550-Fall-2020/github-pages-starter/master/_posts/2019-04-13-measles-charts.md) of this post for details on how these charts were embedded.
- See the [lecture 13A slides](https://github.com/MUSA-550-Fall-2020/week-13/blob/master/lecture-13A.ipynb) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**

Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.



## A New Post

This post will show examples of embedding interactive charts produced using [Altair](https://altair-viz.github.io) and [Hvplot](https://hvplot.pyviz.org/).

## Altair Example

Below is a chart of the incidence of measles since 1928 for the 50 US states.

<div id="altair-chart-1"></div>

This was produced using Altair and embedded in this static web page. Note that you can also display Python code on this page:

```python
import altair as alt
alt.renderers.enable('notebook')
```
