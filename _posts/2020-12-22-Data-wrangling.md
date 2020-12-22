---
published: true
date: 2020-12-22T00:00:00.000Z
tags:
  - dataviz
  - hvplot
  - holoviews
excerpt: false
altair-loader:
  altair-chart-1: charts/measlesAltair.json
hv-loader:
  hv-chart-1:
    - charts/measlesHvplot.html
    - '500'
toc: true
toc_sticky: true
---
## **Datasets Used in This Project**

- Philadelphia Crime Data (by OpenDataPhilly)
- Weather data (by WorldWeatherOnline)
- Census tracts data (by the U.S. Census Bureau)

We accessed the API documentation from OpenDataPhilly to load the Crime Incidents data and then we removed data that do not contain location information.    
   
```Python
API_endpoint = "https://phl.carto.com/api/v2/sql"
# the query
query = "SELECT * FROM incidents_part1_part2 WHERE dispatch_date_time >= '2015-01-01' AND dispatch_date_time < '2020-12-01'" 
output_format = 'geojson'
params = dict(q=query, format=output_format)
r = requests.get(API_endpoint, params=params)
features = r.json()
crime = gpd.GeoDataFrame.from_features(features)
```

Also, we loaded Weather data (from 2015 to present) by using the [wwo-hist package](https://github.com/ekapope/WorldWeatherOnline), a WorldWeatherOnline historical weather data API wrapper. We added a new field Diff_temp (Diff_temp= maxtempC-mintempC) into our weather dataset.    
```Python
from wwo_hist import retrieve_hist_data
import os
os.chdir("your own path")
frequency = 12
start_date = '1-1-2015'
end_date = '12-1-2020'
api_key = 'your own api key'
location_list = ['philadelphia']
hist_weather_data = retrieve_hist_data(api_key,
                          location_list,
                          start_date,
                          end_date,
                          frequency,
                          location_label = False,
                          export_csv = True,
                          store_df = True)
```

We also query census data from the U.S. Census Bureau for demographic data, we got total population, white residents population, median household income and median contract rent data. We then added a new field Pct_White (Pct_White=white residents population/total population) into our demographic dataset. 

```Python
acs = cenpy.remote.APIConnection("ACSDT5Y2018")
variables = [
    "NAME",
    "B02001_001E", # Total population
    "B02001_002E", #White residents population
    "B19001_001E", #Median household income
    "B25058_001E", #Median contract rent    
]
philly_demo_data = acs.query(
    cols=variables,
    geo_unit="block group:*",
    geo_filter={"state": "42", 
                "county": "101", 
                "tract": "*"},
)
# Use SQL to return geometries only for Philadelphia County in PA
where_clause = f"STATE = {42} AND COUNTY = {101}"

# Query for block groups
philly_block_groups = acs.mapservice.layers[10].query(where=where_clause)
philly_demo_final = philly_block_groups.merge(
    philly_demo_data,
    left_on=["STATE", "COUNTY", "TRACT", "BLKGRP"],
    right_on=["state", "county", "tract", "block group"],
)
```

We removed data that did not contain location information, and adjusted the projection of them. We spatially joined the crime incidents data with demographic data by census tracts’ location, and then joined weather data by date time.




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

## HvPlot Example

Lastly, the measles incidence produced using the HvPlot package:

<div id="hv-chart-1"></div>

## Notes

- See the [raw source code](https://raw.githubusercontent.com/MUSA-550-Fall-2020/github-pages-starter/master/_posts/2019-04-13-measles-charts.md) of this post for details on how these charts were embedded.
- See the [lecture 13A slides](https://github.com/MUSA-550-Fall-2020/week-13/blob/master/lecture-13A.ipynb) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**

Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.
