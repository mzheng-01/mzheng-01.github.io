---
name: "Pedaling the Windy City: Visualizing Divvy Ridership in July 2025"
tools: [Python, HTML, vega-lite]
image: assets/pngs/chicago_geo.png
description: An interactive data visualization article exploring Divvy bike share ridership patterns in Chicago, July 2025.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

# Pedaling the Windy City: Visualizing Divvy Ridership from July 2025

### By Matthew Zheng

---

Divvy is Chicago's public bike share system, operated by Lyft, with hundreds of docking stations spread across the city. Riders can pick up a bike at any station and return it to any other station, making it a flexible option for short trips around the city. This analysis looks at over 500,000 Divvy rides taken in July 2025, one of the busiest months of the year for cycling in Chicago. The dataset includes information about where each ride started, when it started, how long it lasted, and whether the rider was a casual user or an annual member.

---

## Where Are People Riding?

Nearly all of the busiest stations are concentrated along the lakefront and in the downtown Loop area, with Millennium Park and DuSable Lake Shore Drive among the most popular starting points. The dominance of lakefront stations suggests that a significant portion of July ridership is driven by recreational use along the scenic lakefront trail.

> Hover over any circle to see the station name and total number of rides.

<vegachart schema-url="{{ site.baseurl }}/assets/json/divvy_map.json" style="width: 100%"></vegachart>

---

## When and How Long Are People Riding?

Selecting a station in the dashboard reveals two patterns about when and how people ride. The hour of day chart shows that most stations see peak ridership in the late afternoon between 4pm and 6pm, consistent with an evening commute or post-work recreational ride. The heatmap of ride duration by hour tells a more nuanced story: shorter rides of under 20 minutes tend to cluster during commute hours, while longer rides of 30 minutes or more are more common in the middle of the day, suggesting a mix of practical commuting and leisurely exploration.

> Click any station in the bar chart to filter the other two charts. Click again to deselect.

<vegachart schema-url="{{ site.baseurl }}/assets/json/divvy_dashboard.json" style="width: 100%"></vegachart>

---

## Who Is Riding?

In July 2025, rides were split between annual members and casual riders. Members are riders with an annual Divvy subscription, while casual riders purchased a single ride or day pass. The breakdown reveals how much of the system's usage comes from tourists and occasional riders versus committed regular users.

> Hover over each slice to see the exact count and percentage.

<vegachart schema-url="{{ site.baseurl }}/assets/json/divvy_donut.json" style="width: 100%"></vegachart>

  

## Citations

- Data source: [Divvy System Data](https://divvy-tripdata.s3.amazonaws.com/202507-divvy-tripdata.zip)
- Chicago Neighborhoods GeoJSON: [Chicago Data Portal](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Neighborhoods/bbvz-uum9)
- All visualizations and contextual visualizations created by Matthew Zheng. Analysis notebook linked in button below.


<div class="left">
{% include elements/button.html link="https://divvy-tripdata.s3.amazonaws.com/202507-divvy-tripdata.zip" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/mzheng-01/mzheng-01.github.io/blob/main/python_notebooks/final_project_plots.ipynb" text="The Analysis" %}
</div>


<style>
  /* 1. Make the entire tooltip box dark */
  #vg-tooltip-element {
    background-color: #333333 !important;
    border: 1px solid #555555 !important;
  }

  /* 2. Make text inside (top and bottom) white */
  #vg-tooltip-element table tr td {
    color: white !important;
    background-color: transparent !important;
  }

  /* 3 Make labels bold so they pop */
  #vg-tooltip-element td.key {
    font-weight: bold !important;
  }
</style>

