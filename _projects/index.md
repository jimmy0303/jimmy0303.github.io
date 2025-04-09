--- 
name: Bigfoot Sightings Visualization
tools: [HTML, Vega, Vega-Lite]
image: assets/pngs/bigfoot.png
description: This project visualizes Bigfoot sightings data across the United States using interactive Vega-Lite charts.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

<!-- Load Vega libraries required for vegachart rendering -->
<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>


<!-- Custom script to embed the charts -->
<script>
document.addEventListener('DOMContentLoaded', function() {
  var charts = document.getElementsByTagName('vegachart');
  Array.from(charts).forEach(function(chartElem) {
    var schemaURL = chartElem.getAttribute('schema-url');
    vegaEmbed(chartElem, schemaURL, {actions: false}).catch(console.error);
  });
});
</script>


## Visualizing Bigfoot Sightings Across the United States


This project explores Bigfoot sightings data from the BFRO reports dataset, showing both geographic distribution and temporal trends.


### The Visualizations


<div class="grid">
    <div class="cell">
        <vegachart schema-url="/assets/json/choropleth.json"></vegachart>
    </div>
    <div class="cell">
        <vegachart schema-url="/assets/json/line_chart.json"></vegachart>
    </div>
</div>


---


### Visualization 1: Choropleth Map


**What's visualized:**  
This map displays the total number of Bigfoot reports per state from 2000–2022.


**Design choices – Encodings:**  
- **Geographic encoding:** State boundaries represent spatial locations.
- **Quantitative encoding:** Report counts are represented using a blue sequential color scale.
- **Tooltip:** Hover interactions reveal the state name and the exact number of reports.


**Design choices – Colormaps:**  
A blue sequential colormap was chosen because its darker shades intuitively indicate higher counts, making patterns of intensity easy to spot.


**Data Transformations:**  
- The raw data is grouped by state to compute total report counts.
- State names are mapped to FIPS codes for accurate geographic joining.
- The data is filtered to include only records from 2000 until 2022.


---


### Visualization 2: Temporal Line Chart


**What's visualized:**  
This interactive line chart shows the annual count of Bigfoot sightings for a selected state. Users can choose a state from a dropdown, which dynamically updates the chart.


**Design choices – Encodings:**  
- **Temporal encoding:** The x-axis (years) is treated as an ordinal sequence.
- **Quantitative encoding:** The y-axis shows the number of reports.
- **Interactive filtering:** A dropdown menu lets users select the state of interest.


**Design choices – Colormaps:**  
A single color (steel blue) is used for the line to maintain visual clarity and focus, avoiding distraction with multiple colors.


**Data Transformations:**  
- The date strings are converted into year values.
- Data is aggregated by state and year to compute annual counts.
- Invalid date entries are filtered out to ensure a clean time series.


**Interactivity:**  
The chart employs a parameter-driven dropdown that updates the displayed state. This interactivity allows for easy comparisons of temporal patterns and helps highlight outlier years.


---


### Data Sources and Analysis


<a class="button" href="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv" target="_blank">The Data</a>
<a class="button" href="https://github.com/jimmy0303/jimmy0303.github.io/blob/main/hw5.1/hw5.1_analysis.ipynb" target="_blank">The Analysis</a>

