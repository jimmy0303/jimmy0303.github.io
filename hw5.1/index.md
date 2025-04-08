---
title: HW5.1 - Bigfoot Reports Analysis
layout: post
---

## Verified Bigfoot Sighting Dashboard

[The Data](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)

<div id="dashboard"></div>
<div id="error" style="color:red; margin:20px 0"></div>

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script>
vegaEmbed('#dashboard', 'bfro_dashboard.json')
  .catch(error => {
    document.getElementById('error').innerHTML = `
      <h3>Error Loading Visualization</h3>
      <p>${error.message}</p>
      <p>Verify:</p>
      <ul>
        <li>JSON file exists at: bfro_dashboard.json</li>
        <li>Data range: 1960-2022</li>
        <li>State names match US map data</li>
      </ul>
    `;
  });
</script>