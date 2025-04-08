---
title: HW5.1 - UFO Sightings Analysis
layout: post
---

## UFO Sighting Patterns Analysis

[The Data](https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/ufo-scrubbed-geocoded-time-standardized-00.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)

### Temporal Distribution
<div id="vis1"></div>

**Description**: Interactive line chart showing UFO sightings over time, filterable by country.

**Design Choices**:
- **Encodings**: Years (ordinal) on x-axis, Counts (quantitative) on y-axis
- **Color**: Single color scheme with country filtering
- **Interactivity**: Dropdown country selector

**Transformations**:
- Cleaned invalid dates (1950-2020 range)
- Extracted year from datetime
- Filtered missing geographic data

### Geographic Distribution
<div id="vis2"></div>

**Description**: Heatmap showing global UFO sighting density.

**Design Choices**:
- **Encodings**: Latitude/longitude positions with color intensity
- **Projection**: Equirectangular for global view
- **Color Scheme**: Viridis for better value differentiation

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

<script>
// Embed visualizations
vegaEmbed('#vis1', 'ufo_time.json');
vegaEmbed('#vis2', 'ufo_geo.json');
</script>