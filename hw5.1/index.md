---
title: Bigfoot Sightings Visualization
---

## Visualizing Bigfoot Sightings Across the United States

This project explores Bigfoot sightings data from the BFRO reports dataset, showing both geographic distribution and temporal trends.

### The Visualizations

<div class="grid">
    <div class="cell">
        <vegachart schema-url="/hw5.1/choropleth.json"></vegachart>
    </div>
    <div class="cell">
        <vegachart schema-url="/hw5.1/line_chart.json"></vegachart>
    </div>
</div>

### Visualization 1: Choropleth Map

**What's visualized**: This map shows the total number of Bigfoot reports per state from 2000-2022. 

**Design choices**: 
- Geographic encoding using state boundaries
- Quantitative color encoding (blue scale) for report counts
- Tooltip interaction showing state names and exact counts

**Data transformations**:
- Grouped raw data by state
- Mapped state names to FIPS codes for geographic joining
- Filtered to include only 2000-2022 data

**Color scheme**: Blue sequential scale was chosen to represent increasing report counts intuitively.

### Visualization 2: Temporal Line Chart

**What's visualized**: This interactive chart shows yearly report counts for selected states.

**Design choices**: 
- Line encoding for temporal trends
- Ordinal x-axis for years
- Quantitative y-axis for counts
- State selection dropdown

**Data transformations**:
- Extracted year from date strings
- Grouped counts by state and year
- Filtered out invalid dates

**Interactivity**: 
- Dropdown selector allows users to choose different states
- Enables comparison of temporal patterns between regions
- Helps identify outlier years for specific states

### Data Sources and Analysis

<a class="button" href="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv" target="_blank">The Data</a>
<a class="button" href="https://github.com/yourusername/yourrepo/blob/main/hw5.1_analysis.ipynb" target="_blank">The Analysis</a>