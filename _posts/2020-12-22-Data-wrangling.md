---
published: true
date: 2020-12-21T00:00:00.000Z
tags:
  - Data wrangling
  - Feature engineering
excerpt: false
altair-loader:
  altair-chart-1: charts/measlesAltair.json
hv-loader:
  hv-chart-1:
    - charts/measlesHvplot.html
    - '500'
toc: trueF
toc_sticky: true
read_time: true
---
## **Datasets Used in This Project**

- **Philadelphia Crime Data (by OpenDataPhilly)**
- **Weather data (by WorldWeatherOnline)**
- **Census tracts data (by the U.S. Census Bureau)**

We accessed the API documentation from **OpenDataPhilly** to load the **Crime Incidents data** and then we removed data that do not contain location information.    
   
```python
API_endpoint = "https://phl.carto.com/api/v2/sql"
# the query
query = "SELECT * FROM incidents_part1_part2 WHERE dispatch_date_time >= '2015-01-01' AND dispatch_date_time < '2020-12-01'" 
output_format = 'geojson'
params = dict(q=query, format=output_format)
r = requests.get(API_endpoint, params=params)
features = r.json()
crime = gpd.GeoDataFrame.from_features(features)
```

Also, we loaded **Weather data** (from 2015 to present) by using the [wwo-hist package](https://github.com/ekapope/WorldWeatherOnline), a WorldWeatherOnline historical weather data API wrapper. We added a new field Diff_temp (Diff_temp= maxtempC-mintempC) into our weather dataset.    
```python
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

We also query **Census data** from **the U.S. Census Bureau** for demographic data, we got total population, white residents population, median household income and median contract rent data. We then added a new field Pct_White (Pct_White=white residents population/total population) into our demographic dataset. 

```python
acs = cenpy.remote.APIConnection("ACSDT5Y2018")
variables = [
    "NAME",
    "B02001_001E", # Total population
    "B02001_002E", #White residents population
    "B19001_001E", #Median household income
    "B25058_001E", #Median contract rent ]
    
philly_demo_data = acs.query(
    cols=variables,
    geo_unit="block group:*",
    geo_filter={"state": "42", 
                "county": "101", 
                "tract": "*"},)
                
# Use SQL to return geometries only for Philadelphia County in PA
where_clause = f"STATE = {42} AND COUNTY = {101}"

# Query for block groups
philly_block_groups = acs.mapservice.layers[10].query(where=where_clause)
philly_demo_final = philly_block_groups.merge(
    philly_demo_data,
    left_on=["STATE", "COUNTY", "TRACT", "BLKGRP"],
    right_on=["state", "county", "tract", "block group"],)
```

**We removed data that did not contain location information, and adjusted the projection of them. We spatially joined the crime incidents data with demographic data by census tracts’ location, and then joined weather data by date time to get our final dataframe.**

## **Feature engineering**

For our final datasets, the following 20 featured attributes are included:   

- **DC_Dist**	: A two character field that names the District boundary.	   
- **DC_Key**	: The unique identifier of the crime that consists of Year + District + Unique ID.   
- **Dispatch_Date_Time**	: The date and time that the officer was dispatched to the scene.   	
- **Hour**	: The generalized hour of the dispatched time.	   
- **Location_Block**	: The location of crime generalized by street block.   
- **Tract** : Census tracts.   
- **PSA**	: A single character field that names the Police Service Area boundary.	   
- **Text_General_Code**	: General Crime Category	The generalized text for the crime code.   
- **Text_general**	: General Crime Category	The generalized text for the crime code.   
- **Total population**  Total population.   
- **White residents population** : White residents population.   
- **Pct_White** : Pct_White = white residents population/total population.   
- **Median household income** : Median household income.   
- **Median contract rent** : Median contract rent.   
- **Geometry** : Geometry.   
- **tempC** : Day temperature.   
- **maxtempC** :Max temperature.   
- **mintempC**: : Min temperature.   
- **FeelsLikeC** : Feels like temperature.   
- **Diff_temp** : Diff_temp = maxtempC - mintempC.
 
