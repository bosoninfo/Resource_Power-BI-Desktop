# COMBINE, APPEND, AND MERGE DATA

## Prep to combine multiple tables

In this next series of sections, we're going to use the data shaping tools of Power BI Desktop to create a model that includes multiple tables using file `CountryPops.xlsx`. The Excel contains several worksheets: the first one shows the countries and their populations, the other worksheets contains countries from each continents. We want to visualise our data on a continent by continent basis.

***Why can't we apply the changes to the Excel table directly?***

1. We can make mistakes even with copy and paste
2. There may be a valid reason that someone else is using this Excel data just as it is
3. Perhaps it's not our data set.

The best way is we can manipulate and disaggregate the data as we want in Power BI Desktop.

### Uploading
- `Home` -> `Data`, `Excel` -> `CountryPops.xlsx`
- Select the continental data for `Africa`, `Antarctica`, `Asia`, `Europe`, `North America`, `Oceania` and `South America`. Each of them has the same columns: "Flag", "Name", "Capital" and "Stutas".
- After loading, Power BI creates 7 queries with 7 sets of data.

### Begin with Africa
- Go to Power Query view by `Home` -> `Transform data` -> `Transform data`.
- Right click columns "Flag" and "Status", remove
- Right click "Key", send to the beginning, `Move` -> `To Beginning`.
- Add a new column, select "Captical", go to `Add Column` -> `Custom Column`, name the column as "Continent", fill custom column formula with = "Africa" (including the quotes)

### Repeat the same steps to the rest of queries.
- Remove columns
- Add columns
- Assgin column value as the Continent.
- Save the file as `Countries.pbix`.

## Append data to a query

If you just open the `Countries.pbix` from download, you need to go to `Home` -> `Transform data` -> `Data source settings` to link to the Excel workbook. We want to combine these 7 queries into one containing all seven continents.

### Start combine
- Open Power Query, select query `Africa`, right click and choose `Duplicate` because we don't want to lose data in it, right click `Africa(2)` and rename it as `All Countries`.
- We then start to append data from other tables. `Home` -> `AI Insights`, `Combine` -> `Append Queries` -> `Append Queries`. Let's try to append one data set Antarctica, choose `Two tables` and in the dropdown list, select `Antarctica, click on `OK`. Now if you scroll down, there are four entries from `Antarctica`.
- Practice again, this time, choose `Three or more tables`, select `Asia`, `Europe`, `North America`, `Oceania`, and `South America`. Wait a moment, and you now have 269 rows.
- `Close & Apply`, save as `All Countries.pbix`

## Add an index column
Continue with `All Countries.pbix`

- First you notice we have duplicated values in "Key" column, let's go to Power Query to fix it.
- Right click "Key" -> `Remove`
- `Add Column` -> `General`, `Index Column` -> `From 1` (BTW, if you choose `Custom`, you can set both `Starting Index` and `Increment`), move the new index column to the beginning, rename it as "ID".
- `Close & Apply`

## Clean up data
We will add two more small data sources to our model that will provide some real value, but also have some issues. Continue to working on `All Countries.pbix`.

### Fix Population Growth Rate

- `Home` -> `Excel` -> `GrowthRates.xlsx`, select `Population by Country` and `Population Growth Rate`, go to Power Query Editor.
- Select `Population by Country`, the "Date" column is with type "text", fix it by applying `Home` -> `Transform`, `Data Type: Text` -> `Date`. Since originally there is a `Changed Type` step, the software will ask you would you replace or add new step to it, choose `Add new step`.
- The green bars located under column insight are all cross over, so we know that we are not throwing erros anywhere, all we had was a data type mismatch.

### Fix Population by Country

- "Population growth rate (%)" is assigned as "text", but if we change it to .. -> `Decimal number` -> `Add new step`, notice that we have errors (15%). So we remove the step and examine why errors occur.
- You notice the error occurs when there is a negative number, but Power BI definately can handle nagetive numbers. If you take very, very close attention, you might notice the minus sign is actually a hyphen (it's bigger).
- Apply your skills you have learned by replacing hyphen (also called "M dash" or "Y dash") with minus sign (also called "N dash" or "narrow dash"). Tips: `Transform` -> `Replace Values`.
- Now you can change the data type into `Decimal` and get a full green bar. Use `Close & Apply` -> `Apply` to apply the changes.
- Save the file as `Relate.pbix`.

### :dizzy: Wrapped up :dizzy:
Common practice for data clean
1. check data type
2. replace unusual data: nulls, empty, N/A
3. pay close attention to the indicator bar that shows the validity of a column

## Relate tables in your model
Continue with `Relate.pbix`. If you directly open `Relate.pbix` without go throught the previous section, remember to [relate it to the data source](https://github.com/HuaijiGao/Resourse_Power-BI-Desktop/tree/main/Chapter04#append-data-to-a-query). In the fields under `Report View`, we will see three primary tables: `All Countries`, `Population by Country`, and `Population Growth Rate`. We would llike to relate those three tables to each other.

Go to `Model View`

### Delete unwanted relationship
- You can collapse the `Properties` pane. If you use zooming (bottom-right corner) to zoom out the window, you can see all the tables, some are related and some ain't.
- If you zoom in, you can see `All Countries` is related to `Antarctica` and others by the "Key" field. But they are not the relationships we want, right click the relationship -> `Delete`.
- Zoom out, you can drag around all tables. Drag the three tables of insteret to make them close to each other. Delete the relationship between `Population by Country` and `Population Growth Rate` as well.

### Create new relationships
-
