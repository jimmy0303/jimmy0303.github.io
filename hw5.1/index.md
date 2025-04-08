---
layout: default
title: HW5.1
---

## Visualization 1: Bigfoot Sightings Choropleth Map

**Description**:  
This choropleth map visualizes the number of Bigfoot sightings reported per U.S. state from 2000 to 2022. Darker shades indicate higher reported sightings.

**Design Choices**:  
- **Encodings**:  
  - Geographic regions encoded using `geoshape`.  
  - Sighting counts encoded via a sequential blue color scheme (`"blues"`).  
- **Color Scheme**:  
  - A sequential blue color scale (`"blues"`) was chosen to intuitively represent higher counts with darker colors.  
  - The `count` field (quantitative) drives the color encoding.  

**Data Transformations**:  
- Grouped raw data by `state` to compute sighting counts.  
- Mapped state names to FIPS codes for geographic joining.  
- Filtered out null states.  

---

## Visualization 2: UFO Sightings Interactive Map

**Description**:  
This interactive map shows UFO sighting locations across the U.S., colored by UFO shape. Users can filter by shape and time period.

**Design Choices**:  
- **Encodings**:  
  - Latitude/longitude encoded as `longitude`/`latitude` (quantitative).  
  - UFO shapes encoded categorically via color.  
- **Color Scheme**:  
  - Categorical colors assigned to UFO shapes (e.g., "circle", "triangle").  

**Data Transformations**:  
- Extracted `year` from datetime.  
- Filtered out rows with missing coordinates.  
- Aggregated yearly counts for the line chart.  

---

## Interactivity Discussion

1. **Choropleth Map**:  
   - **Tooltips**: Show state names and exact sighting counts on hover.  
   - **Purpose**: Allows users to explore state-level details without cluttering the map.  

2. **UFO Map**:  
   - **Dropdown**: Filters sightings by UFO shape (e.g., "circle", "triangle").  
   - **Time Slider**: Filters sightings by year range.  
   - **Purpose**: Enables focused exploration of patterns by shape and time.  

---

## Links

[The Data](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv)  
[The Analysis Notebook](https://github.com/jimmy0303/jimmy0303.github.io/blob/main/hw5.1/hw5.1_analysis.ipynb)