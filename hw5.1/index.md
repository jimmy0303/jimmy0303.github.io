---
layout: default
title: HW5.1
---

## Bigfoot Sightings Map
<div id="choropleth"></div>
<script>
  // Load and render the choropleth map
  fetch("{{ '/hw5.1/assets/choropleth.json' | relative_url }}")
    .then(response => response.json())
    .then(spec => vegaEmbed('#choropleth', spec))
    .catch(error => console.error("Error loading choropleth:", error));
</script>

## Interactive Line Chart
<div id="line-chart"></div>
<script>
  // Load and render the line chart
  fetch("{{ '/hw5.1/assets/line_chart.json' | relative_url }}")
    .then(response => response.json())
    .then(spec => vegaEmbed('#line-chart', spec))
    .catch(error => console.error("Error loading line chart:", error));
</script>