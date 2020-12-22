---
published: true
date: 2020-12-22T00:00:00.000Z
tags:
  - dataviz
  - hvplot
  - holoviews
altair-loader:
  altair-chart-1: charts/measlesAltair.json
hv-loader:
  hv-chart-1:
    - charts/temp.html
    - '1000'
  hv-chart-2:
    - charts/sunHour.html
    - '1000'
  hv-chart-3:
    - charts/visibility.html
    - '1000'
  hv-chart-4:
    - charts/windspeed.html
    - '1000'
  hv-chart-5:
    - charts/precip.html
    - '1000'
  hv-chart-6:
    - charts/humidity.html
    - '1000'
  hv-chart-7:
    - charts/crime.html
    - '1000'
toc: true
toc_sticky: true
read_time: true
---


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

<div id="hv-chart-2"></div>
<div id="hv-chart-3"></div>
<div id="hv-chart-4"></div>
<div id="hv-chart-5"></div>
<div id="hv-chart-6"></div>

<div id="hv-chart-7"></div>

## Notes

- See the [raw source code](https://raw.githubusercontent.com/MUSA-550-Fall-2020/github-pages-starter/master/_posts/2019-04-13-measles-charts.md) of this post for details on how these charts were embedded.
- See the [lecture 13A slides](https://github.com/MUSA-550-Fall-2020/week-13/blob/master/lecture-13A.ipynb) for the code that produced these plots.

**Important: When embedding charts, you will likely need to adjust the width/height of the charts before embedding them in the page so they fit nicely when embedded.**

Enter text in [Markdown](http://daringfireball.net/projects/markdown/). Use the toolbar above, or click the **?** button for formatting help.
