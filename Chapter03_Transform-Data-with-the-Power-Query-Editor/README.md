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
    
