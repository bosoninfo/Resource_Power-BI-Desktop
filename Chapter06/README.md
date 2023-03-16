# USE FILTERS AND Q&A IN A REPORT

|Table of Sections|
|---|
|<ul><li><a href="https://github.com/HuaijiGao/Resourse_Power-BI-Desktop/tree/main/Chapter06#"></a></li></ul>|

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

## Add search capabilities with a Q&A visualization
Continue on the previous section, we will now add a natural language capability to a report.

- Insert a new page, go to `Visualization` pane -> `Build visual` -> `Q&A`. This visualization allows us to use text to create a new visualization.
- Try "show all countries", the term "all countries" is underlined in blue. It shows us a matrix with the name, key, captical, and continent of all countries.
- Try "show all countries as map", the terms "all countries" and "map" are underlined in blue.
- Try "show all countries with populations".
- When a term is underlined in blue, it means that there are other options. Simply hover over the term and click the option you want.

***Issue case***
- If you see some text underlined in orange, that means it's a little bit ambiguous.
- Try "show growth rate for all counties", Power BI will prompt to ask if "counties" is actually "countries"
- Try "show sales", get "Hmm, we didn't understand your question..."
- Try "list all countries with growth rate below 0". The orange says where do you want to get this information from?

|![image](https://user-images.githubusercontent.com/19381768/225207254-4d06910c-5982-472b-b921-ef461a6086c6.png)|
|:--:|
|underlined in orange means ambiguity|

If at some point, if it is just the visualization we want, click on the button to the left of the settings gear, it will turn this result into a standard visual. Click on the page background, then it is clocked in, the Q&A visual goew away and is replaced.

## Add suggestions to a Q&A visualizaiton
Continue on from the previous section. 

- Delete the visualization created by the Q&A visual. Change `Page 1` to `QA`. Drag `Q&A` tile to the page.
- Click on the :gear: setting button in Q&A tile to enter the `Q&A setup` dialogue.
- We have options of "Field synonyms", "Review questions", "Teach Q&A", and "Suggest quetions".

### Field synonyms
- Here shows the tables we are using. If we wanted to have a hidden table to be useful in Q&A, we can turn them back on.
- Expand `All Countries`, notice that there are suggested terms that have been supplied.
- We notice that `Capital` is matched with wrong synonyms, just `Add +` a term `capital city` to it, Power BI will automatically change those matched words. We can amend the suggested term by click :x: next to it, for example, clear municipality. 
- Add `GUID` to `Key`, and delete other synonyms.

### Review questions
- We can sign in and see any questions that people have asked that were not answered.

### Teach Q&A
- We can ask questions in the same way we did in the Q&A tool and then clean them up, because we'll get the same feedback with the orange underline, the double red underline, the blue underline, and so on.

### Manage terms
- Manage the terms we have defined or throw they away.

### Suggested questions
- The list of questions that we start people off with should be something that they might be interested in.
- Try  "countries with the highest growth rates", "countries with the 10 highest growth rates", "ten countries with the lowest growth rates". Add the last two.
- We can click the questions that we have added and amend it again. Click "countries with the 10 highest growth rates" and change it to "ten countries with the highest growth rate".
- The more description you add, the less ambiguity the question will be.
- Try "five countries with the largest populations as a matrix"
- "five countries with the largest populations in order"
- "five countries with the largest populations from largest to smallest", add this one.
- Click save. Come back and you will see the suggested questions are now changed.
