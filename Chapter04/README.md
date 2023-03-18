# COMBINE, APPEND, AND MERGE DATA

## :potted_plant:Overview:potted_plant:
In this chapter, we'll dive into the powerful data shaping tools offered by Power BI Desktop, focusing on combining, appending, and merging data from multiple sources. We'll be working with a dataset containing information about countries and their populations, stored in the 'CountryPops.xlsx' Excel file. Our goal is to visualize our data on a continent-by-continent basis, but first, we need to prepare and combine the data in Power BI Desktop.

The sections of this chapter will guide you through the process of preparing and combining multiple tables, appending data to queries, adding index columns, cleaning up data, relating tables in your model, hiding or displaying queries, and merging data in Power BI Desktop. Along the way, you'll learn about the M Language, which is the language behind the custom query formulas in Power BI.

By the end of this chapter, you'll be well-equipped to handle complex data manipulation tasks and create sophisticated data models in Power BI Desktop. So let's dive in and start combining, appending, and merging data!

---
|Table of Sections|
|---|
|<ul><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#prep-to-combine-multiple-tables">Prep to combine multiple tables</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#append-data-to-a-query">Append data to a query</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#add-an-index-column">Add an index column</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#clean-up-data">Clean up data</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#relate-tables-in-your-model">Relate tables in your model</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#hide-or-display-queries">Hide or display Queries</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter04/README.md#merge-data">Merge data</a></li></ul>|

***:koala: Fun fact: The lanuage behind the custom query formulas is called M Language***

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
Continue with `Relate.pbix`. If you directly open `Relate.pbix` without go throught the previous section, remember to [link it to the data source](https://github.com/HuaijiGao/Resourse_Power-BI-Desktop/tree/main/Chapter04#append-data-to-a-query). In the fields under `Report View`, we will see three primary tables: `All Countries`, `Population by Country`, and `Population Growth Rate`. We would llike to relate those three tables to each other.

Go to `Model View`

### Delete unwanted relationship
- You can collapse the `Properties` pane. If you use zooming (bottom-right corner) to zoom out the window, you can see all the tables, some are related and some ain't.
- If you zoom in, you can see `All Countries` is related to `Antarctica` and others by the "Key" field. But they are not the relationships we want, right click the relationship -> `Delete`.
- Zoom out, you can drag around all tables. Drag the three tables of insteret to make them close to each other. Delete the relationship between `Population by Country` and `Population Growth Rate` as well.

### Create new relationships
- To relate "Name" in `All Countries` to "Country" in `Population by Country`, simply just drag one towards the other one and that would create a relationship between the two.
- Right click on this relationship and select `Properties`, you can examine the relationship by looking at what tables are related, how is the `Cardinality` and the `Cross filter direction`.
- Similarly, relate "Name" in `All Countries` to "Country" in `Population Growth Rate`
- We could have removed the other tables, and asked Power BI to attempt to determine what the relationships are in the model that works. But if you know what the columns are then it's equally easy to open the `Model View`, and relate them by yourself.
- Finally, by relating these tables, we can ask valid questions such as the `Population Growth Rate` in a country versus the current population because they are both related through `All Countries`.

## Hide or display Queries

If you have too many queries, you can have the choices to hide or display them.

- In `Model View` under `Fields`, right click the `...` near query name, choose `Hide in report view`. Hide all the tables except `All Countries`, `Population Growth Rate`, and `Population by Country`.
- You can still see all the tables in `Model View`, but when you navigate to `Report View`, you won't see the hidden tables.
- Now if you share this Power BI data model with others, it's much more compact and much clearer now.
- Save it as `Merge.pbix`

## Merge data
Continue working on `Merge.pbix`. If you directly open `Merge.pbix` without go throught the previous section, remember to [relate it to the data source](https://github.com/HuaijiGao/Resourse_Power-BI-Desktop/tree/main/Chapter04#append-data-to-a-query). We are going to merge a couple of these data sources together so that we get a single larger query.

***Why?***
1. Speed, because it's easier and faster to pull data from a single cached query than from several queries.
2. Simplicity, because you have a lot of small queries and you'd like to merge them together.
3. You might want to standardize your data, which is the reason we're going to do it.

### New merge
- Go to Power Query Editor, select `All Countries`, go to `Home` -> `AI Insights`, `Combine` -> `Merge Queries` -> `Merge Queries as New`. In the merge window, select `Population by Country` to be merged with `All Countries`, highlight "Name" and "Country" columns to establish the relationship.
- At the bottom it says "The selection matches 236 of 269 rows from the first table", so we have 33 that come back with no values. The reason is that in  `Population by Country` list, many of these are territories.
- There is a `Use fuzzy matching to perform the merge` function, which is designed for poor data set because it tries to match more based on the information being similar and perhaps, a typo. But we don't get any extra out of these data set because there aren't typos.
- Navigate to `Join Kind`, and be aware to choose the correct join type. Here we use `Left Outer (all from first, matching from second)`, click on `OK`.

### Wrangling
- In `Merge1` query, you will see a column named "Population by Country" with the value "table", click on the expend button to choose what columns we want.
| ![image](https://user-images.githubusercontent.com/19381768/225175332-b252d7d3-9f00-4b5b-8175-410dc3d21779.png) |
| :--: |
| expend button |
- Deactivate "(Select All Columns)", and tick "Population", "Date", and "% of world population". You would notice the less full green bar in terms of validity. If we scroll down, we can find those territories that are reported here.

### Merge another data source
- Repeat the steps to merge `Merge1` with `Population Growth Rate`. But this time, it's not "Merge Queries as New", it's just `Merge Queries`.
- Select `Population Growth Rate`, based on "Name" and "Country", "Left Outer", and we get 221 of 269 rows from the first table.
- From the "Population Growth Rate" table, simply choose "Population growth rate (%)" and deactivate other columns. Untick `Use original column name as prefix` to kick out redundant information.
- In `Query Settings` under `Properties`, `Name`, rename the query as "All Countires and Population Data". If you wish, you could click in `All Properties` and document the types of joins that you used, and it's normally you would do that.

### Useful take-away
***:question: Q: What step should you perfrom before adding data from more tables, if you need to eventually aggregate the data by which table it originally came from?***

***:exclamation: A: Add a custom column to each table, set to the table name. Because a custom column with a fixed and unique value can later be used to associate a row to its original table.***
