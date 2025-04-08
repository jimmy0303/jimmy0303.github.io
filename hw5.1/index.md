---
title: HW5.1 - UFO Sightings Visualization
layout: post
---

## UFO Sightings Analysis

[The Data](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)

### Line Chart: UFO Sightings Over Time by State
<div id="linechart"></div>

### Choropleth Map: Total Sightings by State
<div id="choropleth"></div>

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script>
// Embed visualizations
vegaEmbed('#linechart', 'line_chart.json')
  .catch(error => console.error(error));
  
vegaEmbed('#choropleth', 'choropleth.json')
  .catch(error => console.error(error));
</script>