---
name: "Pedaling the Windy City: Visualizing Divvy Ridership from July 2025"
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
## Introduction

Chicago's Divvy bike share network is one of the largest in the United States, with hundreds of docking stations spread across the city. Every time someone unlocks a bike, a record is created: where they started, when they left, and whether they are a paying annual member or a casual day-pass rider. Understanding who is riding, from where, and at what times of day is not just interesting trivia. It reveals whether the system is primarily serving Chicago residents as a daily transportation tool or tourists as a summertime attraction. This analysis looks at Divvy rides taken in July 2025, one of the busiest months of the year for cycling in Chicago, to answer a simple but important question: is Divvy a commuter tool, a leisure service, or something in between?

---

## Where Are People Riding?

The map below shows the 20 busiest starting stations in July 2025, with circle size representing total rides. The geographic pattern is immediately striking. Nearly every high-traffic station clusters along the lakefront or near major downtown attractions, with the biggest circles concentrated around well-known destinations like Streeter Drive, Millennium Park, and DuSable Lake Shore Drive. Stations in residential neighborhoods on the North, West, and South Sides are almost entirely absent from the top 20. This geographic concentration raises a question worth holding in mind as you look at the next chart: if the busiest stations are clustered around leisure and tourist destinations, what does that tell us about when and how people are actually riding?

> Hover over any circle to see the station name and total number of rides.

<vegachart schema-url="{{ site.baseurl }}/assets/json/divvy_map.json" style="width: 100%"></vegachart>
*Created by Matthew Zheng. [View the analysis notebook](https://github.com/mzheng-01/mzheng-01.github.io/blob/main/python_notebooks/final_project_plots.ipynb)*


---

## When and How Long Are People Riding?

The interactive dashboard below lets you click on any station in the bar chart to filter the other two charts to that station's specific patterns. This interactivity matters because different stations tell very different stories that the overall citywide picture can obscure.
Across nearly every station, the hour-of-day chart shows rides building steadily through the day and peaking in the late afternoon and evening hours. This consistent pattern suggests that regardless of whether a station serves commuters or recreational riders, the end of the working day is when Chicagoans are most likely to get on a bike. What changes from station to station is the shape of the morning. Stations like Kingsbury and Kinzie and Clinton and Washington show a much more pronounced morning spike alongside the evening one, the classic double-hump signature of a commuter station. At stations like Theater on the Lake or Dusable Harbor that morning spike is far flatter, suggesting fewer people are starting rides there on their way to work.
The most striking exception is Streeter Dr and Grand Ave, the single busiest station in the entire system. Unlike every other station in the top 20, its hour-of-day chart peaks in the mid-afternoon rather than the evening, and rides are spread broadly across the whole day from mid-morning onward. This is the clearest visual signal in the dashboard that the top of the rankings is being driven by a fundamentally different kind of use, recreational and tourist riders filling their afternoons, rather than the commuter-driven evening surge seen everywhere else.
The duration heatmap tells a consistent story across all stations: the darkest concentration of rides sits in the short duration range, confirming that quick trips dominate the system regardless of where you start. However, stations with a stronger recreational character tend to show a slightly wider spread of ride durations, with more activity in the longer ranges compared to the tighter, short-duration clusters visible at busier commuter-adjacent stations.


> Click any station in the bar chart to filter the other two charts. Click again to deselect.

<vegachart schema-url="{{ site.baseurl }}/assets/json/divvy_dashboard.json" style="width: 100%"></vegachart>

---

## Who Is Riding?

The donut chart below shows the overall split between annual members and casual riders for July 2025. Members hold a majority of rides, but the casual share is substantial enough that it cannot be dismissed as occasional or incidental use. This near-even split is notable for a transit system, where you might expect committed regular users to dominate. When you consider that the busiest stations show a broader, less commute-driven hourly pattern, the overall casual share starts to make more sense. July ridership is not simply a commuter story with some tourists on the side. It is genuinely split between two different kinds of use, and the geographic and timing patterns explored above reveal where each type of rider is showing up.

> Hover over each slice to see the exact count and percentage.

<vegachart schema-url="{{ site.baseurl }}/assets/json/divvy_donut.json" style="width: 100%"></vegachart>
*Created by Matthew Zheng. [View the analysis notebook](https://github.com/mzheng-01/mzheng-01.github.io/blob/main/python_notebooks/final_project_plots.ipynb)*

---

## Conclusion

Three trends emerge from this data that together tell a coherent story. First, Divvy's busiest stations are heavily concentrated on the lakefront and at tourist destinations, suggesting that geography and tourism are major drivers of summer volume. Second, while a consistent evening peak exists across the system, the character of individual stations varies meaningfully: commuter stations show a strong morning spike alongside the evening peak, while recreational stations like Streeter Drive show a broad mid-afternoon pattern with almost no morning activity at all. Third, the near-even split between members and casual riders confirms that July ridership is genuinely serving two audiences at once rather than one dominant use case. Rather than pointing to a single conclusion, the data raises a broader question worth exploring further: as Divvy continues to grow, how should the system balance serving the recreational riders who dominate its busiest stations with expanding access for the everyday commuters who are largely absent from the top 20?
  

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

