---
title: HW5.1 - Business Licenses Analysis
layout: post
---

## Business License Visualizations

[The Data](https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/licenses_fall2022.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)

### License Type Distribution
<div id="types"></div>

**Description**: Bar chart showing frequency of different license types.

**Design Choices**:
- **Encodings**: License types on x-axis, counts on y-axis
- **Color**: Uniform steelblue for clarity
- **Interactivity**: Built-in pan/zoom

**Transformations**:
- Aggregated counts per license type
- Sorted by frequency

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script>
vegaEmbed('#types', 'license_types.json')
  .catch(error => console.error(error));
</script>