---
title: HW5.1 - UFO Sightings Visualization
layout: post
---

## UFO Sightings Analysis

### Line Chart: UFO Sightings Over Time by State
<div id="linechart"></div>

**Description**: This interactive line chart shows the number of UFO sightings per year, filterable by US state using the dropdown menu.

**Design Choices**:
- **Encodings**: Temporal (year) on x-axis, Quantitative (count) on y-axis
- **Color**: Single color (steelblue) for consistency
- **Interactivity**: State selection dropdown helps compare temporal patterns across states

**Transformations**:
- Filtered out entries with missing year values
- Grouped data by state and year
- Converted year to ordinal scale for better temporal representation

### Choropleth Map: Total Sightings by State
<div id="choropleth"></div>

**Description**: This choropleth map shows the total number of UFO sightings per state using color intensity.

**Design Choices**:
- **Encodings**: Geographic position with color intensity representing total sightings
- **Color Scheme**: Viridis color scale (blue-green-yellow) for clear value differentiation
- **Tooltips**: Show state name and exact count on hover

**Transformations**:
- Aggregated total sightings per state
- Merged with US geographic data
- Used Albers USA projection for accurate state representation

### Interactivity Discussion
The state selection dropdown in the line chart allows users to isolate specific state trends while maintaining context of national patterns through the choropleth map. This dual-view interaction enables comparative analysis between regional and temporal patterns in UFO sightings.

<script>
// Embed Vega visualizations
vegaEmbed('#linechart', 'line_chart.json');
vegaEmbed('#choropleth', 'choropleth.json');
</script>

[The Data](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)