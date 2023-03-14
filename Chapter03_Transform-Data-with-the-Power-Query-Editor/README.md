# TRANSFORM DATA WITH THE POWER QUERY EDITOR

## Use the Power Query Editor

Open `myGDPs.pbix`

Access to Power Query
- In `Report View` -> `Fields` -> find the table click `...`
- You can `Refresh data`, `Edit query`, `Rename`, etc.
- Actually `Edit query` is a way to open Power Query
- Alternatively, you can use `Home` -> `Transform data` -> `Transform data` to open Power Query

Power Query Window
- Left side bar: `Queries`, you can have multiple queries a model
- Right side bar: `Query settings` for the selected queries.
  - Properties: under `Name`, choose `All Properties`, you can add `Description` to it.
  - Applied steps: the running history of steps that have been taken. The following are auto taken by Power BI Desktop.
    - `Source`: we have lots of HTML here, that's step one and here is a link back to our webpage.
    - `Extracted Table from HTML`: Power BI extracted table data from HTML.
    - `Change Type`: Power BI auto changed some data type of columns.

Issue
- The column names are Column1, Column2, Column3...
- The actual column names in the webpage were actually across row1 and row2.

Fix
- `Home` -> `Transform`, `Use First Row as Headers`
- Rename some of the column, right click the column and choose `Rename`, eg. rename "IMF[5]" as "IMF Estimate", change all the column names with issues.
- Select row1, `Home` -> `Reduce Rows`, `Remove Rows` -> `Remove Top Rows`, input "1" under `Number of rows` to remove row1.
- Note that each of the steps above is recorded in the right side bar. You can undo a step by click :x: next to it.
- Lastly, fix the data type. Eg, for "IMF Estimate" column, it is predominantly numbers, but it also has some text and blanks. Highlight this column, go to `Transform` -> `Any Column`, change `Data Type: Text` to `Data Type: Whole Number`.
- Some errors are thrown because we have some text value ("N/A") here. Hover over the column you see message showing "31% of the changes that were made here resulted in errors". If you wish, you can choose `Remove Errors`, you will remove all the rows with errors in it. But it is not recommended here because for those rows with errors we still have values we want to keep in other columns. Leave it as what it is first.
- Set data type to `Whole Number` for "World Bank Estimate". It will pitch a few errors as well.
- Go to "CIA Estimate" and change data type to `Whole Number`. You can notice the data type are show at the top of each column.
- To apply the changes, go to `Home` -> `Close`, `Close & Apply` -> `Apply'. It says we have 33 errors, but we know where they are. Go to `Home` -> `Close`, `Close & Apply` -> 'Close & Apply'. 
- Notice that the field names are changed under `Report View` -> `Fields`.

