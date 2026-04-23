---
layout: default
title: "Assignment 5: Illinois License Data Visualizations"
---

# Assignment 5: Illinois License Data Visualizations

## Project Links

<div style="margin: 1rem 0;">
  <a href="https://github.com/UIUC-iSchool-DataViz/is445_data/raw/main/licenses_fall2022.csv" target="_blank" style="display:inline-block; padding:10px 16px; margin-right:10px; background:#2d6cdf; color:white; text-decoration:none; border-radius:8px;">The Data</a>
  <a href="PASTE_YOUR_NOTEBOOK_GITHUB_LINK_HERE" target="_blank" style="display:inline-block; padding:10px 16px; background:#28a745; color:white; text-decoration:none; border-radius:8px;">The Analysis</a>
</div>

---

## Dataset Overview

For this project, I used the `licenses_fall2022.csv` dataset, which contains information about professional and occupational licenses. The dataset includes columns such as license type, description, license status, city, county, and expiration date. I chose this dataset because it has clear categories that are easy to compare and works well for making both summary and interactive visualizations. My two visualizations explore which license descriptions appear most often and how license records are distributed across counties by status.

---

## Visualization 1

<div id="vis1"></div>

<script src="https://cdn.jsdelivr.net/npm/vega@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6"></script>
<script>
  vegaEmbed('#vis1', '{{ site.baseurl }}/assets/vis1.json');
</script>

### Write-up for Visualization 1

**What is being visualized:**  
This visualization shows the top 10 license descriptions by number of records in the dataset. The goal of this plot is to compare which kinds of licenses appear most often and make the overall distribution easier to understand. By looking at this chart, the viewer can quickly see which license descriptions are the most common and how much they differ from one another.

**Design choices / encodings:**  
I used a bar chart because bar charts work well for comparing counts across categories. The x-axis represents the number of records, and the y-axis represents the license description. I also included tooltips so the viewer can hover over each bar and see the exact count. I chose this chart type because it makes category comparisons very clear and helps the largest groups stand out immediately.

**Color choices:**  
I used a single consistent color for the bars instead of assigning a different color to every category. I made this choice because the main purpose of the chart is to compare bar lengths, not to emphasize separate groups with color. Using one color keeps the chart clean and prevents it from looking too busy.

**Transformations:**  
To create this visualization, I grouped the data by `Description` and counted the number of rows in each category. After that, I sorted the counts from highest to lowest and kept only the top 10 descriptions so the chart would stay readable. This transformation was important because the raw dataset contains many categories, and showing all of them at once would make the visualization harder to interpret.

---

## Visualization 2

<div id="vis2"></div>

<script>
  vegaEmbed('#vis2', '{{ site.baseurl }}/assets/vis2.json');
</script>

### Write-up for Visualization 2

**What is being visualized:**  
This visualization shows the number of license records by county, and it is interactive so the viewer can filter the chart by license status. The main purpose of this plot is to show how the distribution of licenses changes across counties depending on whether the licenses are active, not renewed, cancelled, inactive, or in another status category. This helps the viewer move beyond just overall totals and explore how records are spread across different areas.

**Design choices / encodings:**  
I used a bar chart for this visualization because it is an effective way to compare counts across counties. The x-axis represents the number of license records, and the y-axis represents county. I used color to represent license status and tooltips to show the county name, status, and exact count when the viewer hovers over a bar. I chose this design because county comparisons are easiest to read when values are aligned on a common axis.

**Color choices:**  
I used color to represent license status so that the viewer can distinguish between different status categories more easily. This makes sense because license status is a categorical variable, so different colors help separate the groups clearly. A categorical color palette works well here because the goal is to compare distinct labels rather than a continuous numeric range.

**Transformations:**  
To prepare this visualization, I grouped the data by `County` and `License Status` and counted how many records fell into each combination. I also removed missing county values and limited the chart to the counties with the largest totals so that the visualization would remain readable. These transformations made the chart more focused and helped highlight the most meaningful comparisons instead of overwhelming the viewer with too many categories at once.

---

## Interactivity Discussion

I added interactivity by making the second visualization filterable by license status with a dropdown menu. This allows the viewer to focus on one status at a time, such as active, not renewed, or cancelled, instead of trying to read all categories at once. This makes the chart clearer and more useful because it helps the viewer compare counties within a specific status group. This is more meaningful than basic pan and zoom because it directly supports exploration of the data.

---

## Reflection

Overall, these two visualizations helped me understand the dataset from two different angles. The first chart gives a broad overview of which license descriptions are most common, while the second chart gives a more detailed look at how license records are distributed geographically by status. Together, the two plots provide a clearer picture of the dataset than the raw table alone.
