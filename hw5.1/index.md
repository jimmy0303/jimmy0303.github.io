---
title: HW5.1 - Bigfoot Reports Dashboard
layout: post
---

## Interactive Bigfoot Sighting Analysis

[The Data](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)

<div id="dashboard"></div>

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script>
vegaEmbed('#dashboard', 'bfro_dashboard.json')
  .then(res => {
    // Add year reset functionality
    const container = document.querySelector('#dashboard');
    const resetBtn = document.createElement('button');
    resetBtn.textContent = 'Reset Year Selection';
    resetBtn.style.margin = '10px 0';
    resetBtn.onclick = () => {
      res.view.signal('Select Years', {}).run();
    };
    container.prepend(resetBtn);
  })
  .catch(console.error);
</script>