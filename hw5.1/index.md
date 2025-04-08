---
title: HW5.1 - Business Licenses
layout: post
---

## Business License Analysis

[The Data](https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/licenses_fall2022.csv) | 
[The Analysis](https://github.com/yourusername/your-repo/blob/main/hw5.1_analysis.ipynb)

### License Type Distribution
<div id="vis1"></div>

### Secondary Visualization
<div id="vis2"></div>

<!-- Required Vega dependencies -->
<script src="https://cdn.jsdelivr.net/npm/vega@5.22.1"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5.6.1"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6.21.0"></script>

<script>
// Embed visualizations with error handling
async function embedVisualizations() {
  try {
    // Embed first visualization
    await vegaEmbed('#vis1', 'license_types.json', {
      actions: false,
      renderer: 'canvas'
    });
    
    // Embed second visualization
    await vegaEmbed('#vis2', 'license_secondary.json', {
      actions: false,
      renderer: 'canvas'
    });
    
  } catch (error) {
    console.error('Error embedding visualizations:', error);
    document.getElementById('vis1').innerHTML = 
      '<p>Error loading visualization. Check console for details.</p>';
    document.getElementById('vis2').innerHTML = 
      '<p>Error loading visualization. Check console for details.</p>';
  }
}

// Run embedding when page loads
if (document.readyState !== 'loading') {
  embedVisualizations();
} else {
  document.addEventListener('DOMContentLoaded', embedVisualizations);
}
</script>