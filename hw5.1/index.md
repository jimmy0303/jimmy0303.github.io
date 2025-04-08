---
layout: default
title: HW5.1
---

## Bigfoot Sightings Map
<div id="choropleth"></div>
<script>
  fetch("{{ '/hw5.1/assets/choropleth.json' | relative_url }}")
    .then(response => {
      console.log("Choropleth response status:", response.status); // Debug line
      return response.json();
    })
    .then(spec => {
      console.log("Choropleth spec loaded:", spec); // Debug line
      return vegaEmbed('#choropleth', spec);
    })
    .catch(error => console.error("Error:", error));
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


---

### 3. `hw5.1_analysis.ipynb`
```python
import pandas as pd
import altair as alt

# =====================
# Bigfoot Data Processing
# =====================
bfro_url = "https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/bfro_reports_fall2022.csv"
bfro_df = pd.read_csv(bfro_url)

# State to FIPS mapping
state_to_fips = {
    "Washington": 53, "California": 6, "Florida": 12, # ... (full mapping from previous example)
}

# Process data
state_counts = (
    bfro_df.groupby('state', as_index=False)
    .size()
    .rename(columns={'size': 'count'})
)
state_counts['state_id'] = state_counts['state'].map(state_to_fips)

# Save processed CSV
state_counts.to_csv("hw5.1/assets/bfro_reports_processed.csv", index=False)

# Create choropleth
states = alt.topo_feature('https://cdn.jsdelivr.net/npm/vega-datasets@v1.29.0/data/us-10m.json', 'states')
choropleth = alt.Chart(states).mark_geoshape().encode(
    color='count:Q',
    tooltip=['state:N', 'count:Q']
).transform_lookup(
    lookup='id',
    from_=alt.LookupData(state_counts, 'state_id', ['count', 'state'])
).project('albersUsa')
choropleth.save('hw5.1/assets/choropleth.json')

# =====================
# UFO Data Processing
# =====================
ufo_url = "https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/ufo-scrubbed-geocoded-time-standardized-00.csv"
ufo_df = pd.read_csv(ufo_url, usecols=['sighted_at', 'shape', 'latitude', 'longitude'])

# Clean data
ufo_df = ufo_df.dropna(subset=['latitude', 'longitude'])
ufo_df['year'] = pd.to_datetime(ufo_df['sighted_at']).dt.year

# Create UFO map
states = alt.topo_feature('https://cdn.jsdelivr.net/npm/vega-datasets@v1.29.0/data/us-10m.json', 'states')
background = alt.Chart(states).mark_geoshape(fill='lightgray', stroke='white').project('albersUsa')

shape_selection = alt.selection_point(
    fields=['shape'],
    bind=alt.binding_select(options=ufo_df['shape'].unique().tolist(), name='Shape:'),
    value={'shape': 'circle'}
)

points = alt.Chart(ufo_df).mark_circle(size=10).encode(
    longitude='longitude:Q',
    latitude='latitude:Q',
    color=alt.Color('shape:N', legend=None),
    tooltip=['shape:N', 'year:O']
).add_params(shape_selection).transform_filter(shape_selection)

ufo_map = (background + points).properties(title="UFO Sightings by Shape")
ufo_map.save('hw5.1/assets/ufo_map.json')