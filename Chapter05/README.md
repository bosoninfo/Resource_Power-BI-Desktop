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

Recently Microsoft has redesigned the formatting panes and you can apply this new changes by going to `File` -> `Options and settings` -> `Options` -> `Preview features` -> tick `New format pane`. Reopen Power BI Desktop, reopen `CP Report.pbix`, and continue on.

### Thmems
- If we want to make sweeping changes in the color design, simply go to `View` -> `Theme`, play around with different themes and see how the color design is applied to all elements.
- If we just one to change the theme in one visualization, we can choose the visualization, go to `Visualization pane` -> `Format your visual`. There are two tabs, `General` tab are the same for all types of visualizations while `Visual` is specific for each type of the visualization. 
- We can easily make changes to each elements, and the nice thing about it is we can always `Revert to default` if we don't like the changes. Another option is under the `...` button beside `General`, we can `Revert all settings to default`.
- If we have no selected any visualization, the format setting will be `Format page`, where you can format the whole page.

## Create text visuals: Cards, table and matrix

### Matrix
- In `Visualizations` pane choose `Matrix`, expand `All Countries and Population Data`, choose `Name`, `Population by Country.Population`, and `Population by Country.% of world population`.
- The column names are too long, and we understand that if we change data source than the visualization would apply the changes. However, actually we are able to change the column name without affecting the original data source. Click the small dropdown button under `Visualizations` pane -> `Build visual` -> `Values` section. Choose the column name -> `Rename for this visual`. 
- Rename `Population by Country.% of world population` as `% of World Population`, and rename `Population by Country.Population` as `Population`.
- In the `Fields`, right click on `Name` and rename it as `Country Name`, then it will apply changes to all.

|![image](https://user-images.githubusercontent.com/19381768/225188517-6e5e1801-6609-4be0-bfa6-f0e562706a49.png)|
|:--:|
|change column name without affecting data source|


### Card (also called a big number card)
- Click on `Card` in `Visualizations` pane, choose `Population by Country.Population` as the field. It will add up all the numbers an show us 4 billions.
- We can click on the filter button, and notice that it is only showing the data from Asian. If we click on the bubble of Asia in map visualization, it will lead us to all data again, and all the visualizations will change accordingly. This is called cross filtering.
- In a standdard card visualization, a field added to the Card is added at the right.
- We can rename the label in Card as well, follow the same method in matrix, rename it as `Total Population`. If we just want it gone, go to `Visualizations` pane -> `Format visual` -> `Visual` -> turn `Category label` off.

|![image](https://user-images.githubusercontent.com/19381768/225190125-9e117648-aa9f-4f3f-bf17-8066bef9ed31.png)|
|:--:|
|use filtering to check what data is showing|

### Interim result
|![image](https://user-images.githubusercontent.com/19381768/225190909-88a3451f-37c7-482a-ae43-7229677b340e.png)|
|:--:|
|an interim view of the report|

## Apply preset styles and conditional formatting
The reason we like tables and matrices is that we can style them and format them as we would in Excel. We will do two different ways to format a matrix.

### Method 1
- Select the matrix, go to `Visualizations` pane -> `Format visual` -> `Visual` -> `Sytle presets` -> change `Default` to other styles matching with your chosen theme.
- If we don't like the presets, we can alter the matrix by using the categories below `Style presets`.

### Method 2 (Conditional Formatting)
- Select the matrix, go to `Visualizations` pane -> `Build visual` -> `Visual`, click on the small button near `% of World Population` -> `Conditional formatting`. We have many options here, just choose on to start with.
- Select `Data bars`, a dialogue open for this perticular data. Change the `Positive bar` with a light blue color and click `OK`.
- Click on `% of World Population` column to sort the data, make large values show at the top.
- Many of the choices that you are familiar with from Microsoft Excel are available here for conditional formatting.

|![image](https://user-images.githubusercontent.com/19381768/225192651-2b0fa792-ec8e-40bf-a076-9919ab4422ad.png)|
|:--:|
|conditional formatting|

## Apply formatting to titles
- Choose the map visual, go to `Format visual` -> `Visual` -> `Map settings` -> `Style`, we can change what type of map we want, and `Controls` with the setting as `Auto zoom` or `Zoom buttons` etc.
- If we go to `General` -> `Title`, we can change the text color, font, etc. Change the title to dark blue.
- Change the title of Treemap to 18 pt and dark blue.
- Go to the matrix visual, the `Title` is turned off, change it to `on`, type `Country Population` in `Text` field to make a title. Change title to 18 pt and dark blue. Go to `Visual` and turn `Row subtotals` off to prevent distraction.
- Come back to Treemap, this time, we can type `title` in search box to quick locate the function we want. Change the long title into `Population by Country`.
