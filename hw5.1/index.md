---
layout: default
title: HW5.1
---

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>

## Visualization 1: Bigfoot Sightings Choropleth Map

**Description**  
This choropleth map shows the number of Bigfoot sightings reported per U.S. state from 2000-2022. Darker blue shades indicate higher reported sightings.

**Design Choices**  
- **Encodings**:  
  - *Geographic Regions*: `geoshape` mark with Albers USA projection  
  - *Color Encoding*: Sequential blue scale for sighting counts  
- **Color Scheme**:  
  - `"blues"` scheme chosen for intuitive intensity representation  

**Data Transformations**  
- Grouped raw data by `state` to count reports  
- Mapped state names to FIPS codes using manual lookup  
- Filtered out null/undefined states  

```vega-lite
{% include_relative assets/choropleth.json %}