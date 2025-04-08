---
layout: default
title: HW5.1
---

## Bigfoot Sightings Map
<div id="choropleth"></div>
<script>
  fetch("{{ '/hw5.1/assets/choropleth.json' | relative_url }}")
    .then(response => {
      console.log("Choropleth response status:", response.status); 
      return response.json();
    })
    .then(spec => {
      console.log("Choropleth spec loaded:", spec); 
      return vegaEmbed('#choropleth', spec);
    })
    .catch(error => console.error("Error:", error));
</script>


## Interactive Line Chart
<div id="line-chart"></div>
<script>
  fetch("{{ '/hw5.1/assets/line_chart.json' | relative_url }}")
    .then(response => response.json())
    .then(spec => vegaEmbed('#line-chart', spec))
    .catch(error => console.error("Error loading line chart:", error));
</script>