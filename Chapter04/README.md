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

### Start with Africa
- Open Power Query, select query `Africa`, right click and choose `Duplicate` because we don't want to lose data in it, right click `Africa(2)` and rename it as `All Countries`.
- We then start to append data from other tables. `Home` -> `AI Insights`, `Combine` -> `Append Queries` -> `Append Queries`. Let's try 
