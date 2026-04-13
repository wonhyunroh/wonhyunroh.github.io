---
title: "HW5: UFO Sightings Visualizations"
---

<a href="https://github.com/wonhyunroh/wonhyunroh.github.io/blob/main/HW5-1.ipynb">The Analysis</a> | <a href="https://github.com/UIUC-iSchool-DataViz/is445_data/blob/main/ufo-scrubbed-geocoded-time-standardized-00.csv">The Data</a>

## Plot 1: UFO Sightings by Shape

<div id="vis1"></div>
This bar chart shows UFO sightings by shape from 1950. The x-axis is count (quantitative), and the y-axis is shape (nominal), sorted in descending order by count. Color is encoded by count using the viridis sequential scheme, chosen because count is an ordered variable and viridis is perceptually uniform and colorblind friendly, which reinforces the ranking. For data transformation, I parsed datetime with 'pd.to_datetime', dropped missing values, filtered to years >= 1950, and preaggregated with groupby('shape').size()
to keep the exported JSON small. 

## Plot 2: UFO Sightings Over Time by Shape

<div id="vis2"></div>

This line chart shows sightings per shape over time, limited to the top 8 shapes for readbility. Encodings are year on the x-axis (ordinal), count on the y-axis (quantitative), and shape as color (nominal). Since shape has no natural ordering, I used the default categorical palette
instead of a sequential scheme. For transformations, I selected the top 8 shapes with value_counts().head(8) and aggregated with groupby(['year', 'shape']).size().

## Interactivity

I added a selection_point bound to the legend. Clicking a shape highlights that line while fading the others, making it easy to isolate a single shape's trend even when the 8 lines overlap.

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script type="text/javascript">
  vegaEmbed('#vis1', 'https://raw.githubusercontent.com/wonhyunroh/wonhyunroh.github.io/main/chart1.json');
  vegaEmbed('#vis2', 'https://raw.githubusercontent.com/wonhyunroh/wonhyunroh.github.io/main/chart2.json');
</script>
