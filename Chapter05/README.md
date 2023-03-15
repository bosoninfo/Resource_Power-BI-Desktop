# CREATE REPORTS AND VISUALIZATIONS

## Use the Power BI Desktop report view
In Chapter04, our data model is done. If you are a data modeler, data designers, at this point it would be done since we've done is created a data model. But we are not finished yet, it's good to practice few visualizations. Let's begin by switching to 'Report View'.

There are two ways we can add a visualization to the report canvas:
1. Start with `Fields`.
2. Start with `Visualizations`.

### Start with `Fields`
- Expand `All Countries and Population Data`, click on `Continent`, we will get a map because we chose geospatial data. Likewise if we choose zip codes, the name of states or privinces, countries, continents, and so on, we get a map as a default.
- Add `Population by Countinent.% of world population`, we will get some bubbles showing the proportions of population in each continent.

|![image](https://user-images.githubusercontent.com/19381768/225183413-b5de1a5e-767e-45d6-b2d2-8d0310c7abcc.png)|
|:--:|
|Map|

### Start with `Visualizations`
- Choose `Stacked bar chart`, add `Name` and `Population by Countinent.% of world population`, we will get a bar chart with very large countries at the top.
- If you click `Pie chart`, it will switch to a pie chart. But the presentation is not good since there are too many categories and most of them are very small.
- In this case, it's better to go with `Treemap` where the size of shape indicating the proportion with a clearer way. We now have more larger rectangles that are easier for us to compare.
- If we want to change the data selected, just untick `Population by Countinent.% of world population` and tick `Population by Country.Population`. That's how easy we can change the data that we're looing at in a visualization.

Save it as `CP Report.pbix`.

|![image](https://user-images.githubusercontent.com/19381768/225184429-a8d0d06f-ab6e-40d7-94d8-b227203c0eaa.png)|
|:--:|
|Treemap|

## Format visualizations and apply themems

Recently Microsoft has redesigned the formatting panes and you can apply this new changes by going to `File` -> `Options and settings` -> `Options` -> `Preview features`
