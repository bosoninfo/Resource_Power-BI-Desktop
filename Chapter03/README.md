# TRANSFORM DATA WITH THE POWER QUERY EDITOR

## :potted_plant:Overview:potted_plant:

In this chapter, we will explore the Power Query Editor, a powerful tool in Power BI for cleaning and transforming data to suit our needs. We will cover how to use the Power Query Editor, reduce rows, filter, set data types, replace values, unpivot columns, and transform columns. By the end of this chapter, you will have a solid understanding of the Power Query Editor's capabilities and how to use it to streamline your data preparation process.

Section 1: Use the Power Query Editor
We'll begin by learning how to access the Power Query Editor and navigate its various features. We will also discuss the importance of setting properties and the applied steps pane.

Section 2: Reduce Rows
In this section, we will explore techniques for reducing the number of rows in our dataset, such as sorting, filtering, and removing errors.

Section 3: Filter, Set Data Type, Replace Values
Here, we will dive into the process of filtering data, setting data types, and replacing values in our dataset. We will work with an example using historical census data.

Section 4: Unpivot Columns
Occasionally, we might need to unpivot data from a pivot table format to a more suitable format for visualization. We will learn how to do this using the Power Query Editor.

Section 5: Transform Columns
Finally, we will explore the various transformation options available for text, number, and date & time columns in the Power Query Editor. This will help you make the most of your data and prepare it for insightful visualizations.

By the end of this chapter, you will have a strong foundation in using the Power Query Editor to clean and transform data, making it easier to create powerful visualizations and gain valuable insights from your data.

---
|Table of Sections|
|---|
|<ul><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter03/README.md#use-the-power-query-editor">Use the Power Query Editor</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter03/README.md#reduce-rows">Reduce rows</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter03/README.md#filter-set-data-type-replace-values">Filter, set data type, replace values</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter03/README.md#unpivot-columns">Unpivot columns</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter03/README.md#transform-columns">Transform columns</a></li></ul>|



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

| ![image](https://user-images.githubusercontent.com/19381768/224904286-ace9ee24-7456-4cd4-8cd4-ea068ecd87d2.png) |
| :--: |
| error message |
- Set data type to `Whole Number` for "World Bank Estimate". It will pitch a few errors as well.
- Go to "CIA Estimate" and change data type to `Whole Number`. You can notice the data type are show at the top of each column.
- To apply the changes, go to `Home` -> `Close`, `Close & Apply` -> `Apply`. It says we have 33 errors, but we know where they are. Go to `Home` -> `Close`, `Close & Apply` -> `Close & Apply`. 
- Notice that the field names are changed under `Report View` -> `Fields`.

## Reduce rows
If you are not in the Power Query view, use `Home` -> `Transfer data` -> `Transfer data` to go back.

We would like to reduce this data set so that we have the top 25 countries in terms of their GDP per capita. We'll handle those errors along the way.

- The dataset we want to use is the "World Bank" data set since it's a newer data set and it tends to exclude territories and include countries. Other data set like CIA, for example, does includes other territorial units. And also some of the data here is older, in 2014 or 2015, whereas the "World Bank" tends to be 2019 or 2020.
- Having decided that we don't care about the "IMF" data, hold "Ctrl", select "IMF Estimate", "IMF Year", "CIA Estimate" and "CIA Year", go to `Home` -> `Manage Columns`, `Remove Columns` -> `Remove Columns`. We have five columns left.
- Select "World Bank Estimate", right click, choose `Remove Errors`. Now we have 201 rows rather than 227.
- Select :arrow_down_small: in "World Bank Estimate" column, choose `Sort Descending`.
- Go to `Home` -> `Reduce Rows`, `Keep Rows` -> `Keep Top Rows`, enter 25. Now we have our query result.
- One more thing to notice is that we have "(more)" under "Country (or territory)" column since this "(more)" was actually a hyperlink to more information. We need to perform some text transformation here.
- Go to `Transform` -> `Text Column`, `Extract` -> `Text Before Delimiter`, enter "(" under `Delimiter`, the word "(more)" disappears.
- There are other transformations for number and date & time columns, you can have a try and play around.
- Remember to `Close & Apply`, the data will be reloaded to Power BI Desktop. There are now 5 columns and 25 rows in the data model.
- You may save it but you do not necessarily need to. We won't be using this later in the course.

## Filter, set data type, replace values
In this section, we're going to create a new data model so that we can do some filtering, setting data types and replacing values.

Open `Transform Census.xlsx`. 
- It is this historical census data from 1790 to 1860. 
- Choose `US Pop Table 1790-1860` -> `Load`, you can see it is populated into the field list, and the column names are default.

Go to Power Query
- `Home` -> `Transfer data` -> `Transfer data`
- From right side bar, three things were done: `Source`, `Navigation`, and `Changed Type`.
- `Home` -> `Transform`, `Use First Row as Headers`
- You can see the green bar across most of the columns. Eg, in "1790" column, it says that 19 (37%) of the entries are valid, no error, 33 (63%) are empty.

| ![image](https://user-images.githubusercontent.com/19381768/224904124-f2564767-6b74-4266-bf44-260a2129bb84.png) |
| :--: |
| the validity of the data |
- When we examine the data, we found out the missing data in "Admitted" are accepted, locate to that column, choose `Remove Empty` to remove 2 rows. An action named `Filtered Rows` is added to the `Applied Steps` as well. The green bar goes 100% in "Admitted" column since there is no null value now.
- Choose `Hawaii` and click `11` from the first column, it will display a transpose view of this record at the bottom of the window. We notice that it has no value by 1860 so we want to eliminate it. So, hover over column "1860", click on `Remove Empty` to remove 8 rows.

Replace value
- Click on column "1790", go to `Home` -> `Transform`, `Replace Values`, replace all "null" with "0".
- But now we actually want to undo that because 0 means there were no people there while, in fact, it's "null" because there was no census taken in that state or territory in that particular year. Before you hit :x: to the step, you can click on :gear: to see what has been done in that step.
- You can also sorting the data by ascending or descending order in any column.
- Now `Close & Apply` the data, save it as `Census History.pbix`.

## Unpivot columns
Open `Census History.pbix`.

- If you look at the `Data View`, you would notice that it is actually a pivot table. For example, originally we should have 8 records in Connecticut and 1 record in Colorado.
- Occasionally, we need to have that original data back, so we can create the visualization. Go to Power Query mode by `Home` -> `Transfer data` -> `Transfer data`.
- We want to unpivot this data, so every single row then would have the same information about the state, the year it was admitted, but it would have then the year of the census and the data value for that year of the census.
- Choose column "Name" and hold "Ctrl" button and select "Admitted", go to `Transform` -> `Any Column`, `Unpivot Columns` -> `Unpivot Other Columns`. But we notice there is a key column.
- Move back by undoing the step, select "key" column and right click, choose `Move` -> `To Beginning`.
- Then you choose "key", "Name" and "Admitted", repeat the unpivot other columns step, you will get the data set you want.
- Rename "Attribute" as "Census Year", rename "Value" as "Population", change "Census Year" to "Whole Number" by clicking the small "ABC" icon in the column name.

## Transform columns
Below are ribbons under `Transform` tab

:arrow_forward:`Table`
- `Transpose`: transpose table so rows become columns, columns become rows
- `Reverse Rows`: last rows are displayed first
- `Count Rows`: know how many rows the table has

:arrow_forward:`Any Column`
- `Data Type`: change data type
- `Detect Data Type`: assume you have a column with lots of null values but all the others are numbers. That might be assigned originally as text. But if we choose the column and use detect data type, the data type is clearly numeric without the presence of nulls.
- `Replace Values`: replace values
- `Fill`: fill up and down as in Excel.
- `Move`: move column

:arrow_forward:`Text Column`
- `Split Column`: by delimiter, by number of charaters, etc.
- `Format`: modify the format of the column, lowercase or uppercase, trim any trailing or leading spaces, clean any non-printable characters, add prefix etc.
- `Extract`: first character, last character, range etc.

:arrow_forward:`Number Column`
- `Statistics`: aggregate functions
- `Standard`: basic math
- `Information`: is Even, is Odd, etc.

:arrow_forward:`Date & Time Column`
- format date value
- format time value

Head back to `Census History.pbix`.
After manipulating in Power Query, you can just `Close` it. Then a notification will show up at the top with the options of `Apple changes` or `Discard changes`. It's a good way to practice and change the data in Power Query.
