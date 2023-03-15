# USE FILTERS AND Q&A IN A REPORT

## Use slicers to filter visuals
Open `Simple CP Report.pbix`. 

- Slicer is actually a filter for an entire page. Go to `Visualizations` -> `Build visual` -> `Slicer`.
- Select `Continent` under query `All Countries and Population Data`.
- Go to `Format visual` -> `Slicer header`, change the title as 18 pt and deep blue. Go to `Format visual` -> `Values` -> `Values`, change the text as 12 pt 
- We can test the result by choose `Asia` in the slicer. You can notice that it is not cross filtering but pure filtering, all the data in the page are only for Asia region. So it is totally different how slicer works compared to cross filtering.

To make the slicer looks nicer.
- Go to `Format visual` -> `General` -> `Effects` -> `Background`, choose lighter gold.
- We can modify the slicer setting by going to `Format visual` -> `Visual` -> `Slicer settings`. In `Options`, we can change `Orientation` from `Vertical` to `Horizontal`. In `Selection`, we can choose `Single select` or `Multi-select with CTRL`.

|![image](https://user-images.githubusercontent.com/19381768/225203589-9ec129b0-2790-4f7c-bbfa-3f786c1b95ed.png)|
|:--:|
|adding slicer|

## Filter reports and pages
Continue on from the previous section. Sometimes we want a filter that is just baked right into the report, for example, to show visualizations for a particular geography.

- Right click on `Visuals` page, duplicate, and we have a `Duplicate of Visuals`. Right click again and rename `Visual` as `All Continents`. Rename `Duplicate of Visuals` as `South America`.
- On the `South America` page, collapse the `Visualization` pane and open the `Filters` pane, there are two text wells here, this is the place where you can filter the whole page.
- Drag `Continent` from Fields to the first well, `Filters on this page`. Tick `South America` only. Click on the slicer and simply remove it, because there is only one continent in this page.
- The second well is `Filters on all pages`, drag `Continent` to this well, set the continent to `Asia`. Now every page become the data in Asia. To delete it, simply clear the filter.
- Remember to click the `South America` back on the page filter, since it is overwritten in the previous step.
- We can show or hide the filter pane from report readers.

|![image](https://user-images.githubusercontent.com/19381768/225204970-4dd059e7-c8ef-4f57-8170-6bf852eb3657.png)|
|:--:|
|hide the filter pane from report readers|

##
