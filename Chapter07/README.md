# SHARE YOUR WORK

|Table of Sections|
|---|
|<ul><li><a href="https://github.com/HuaijiGao/Resourse_Power-BI-Desktop/tree/main/Chapter07#"></a></li></ul>|

## Sharing: The basics

### Sharing
- Share a report in Microsoft Teams
  - best option if your organization uses Microsoft Teams.
- Distribute a PBIX file
  - share reports and the datasets underneath them.
  - if local data sources are included, the receiver need to change the data source location or the PBIX file will generate an error.
  - if the data sources are from non-local location, such as in a SharePoint library or OneDrive, there will be no issue.
- Upload PBIX file from the Power BI service
  - your report and your data set will be added to the Power BI service
  - another option is to publish your report to send ti to a Power BI service directly from Power BI Desktop.
  - these two options both upload the PBIX to Microsoft's PBI storage in the cloud.

### Live Connections
- Share your dataset
  - Publish dataset in an appropriate workspace
  - set up build permission for others to connect
- Create and share a dashboard
  - pin visuals from your report on a shareable dashboard
  
## Publish from Power BI Desktop
Open `Countries Populations Final.pbix`. If you get an error, remember to link the data sources correctly. [Don't know how to link?](https://github.com/HuaijiGao/Resourse_Power-BI-Desktop/tree/main/Chapter04#append-data-to-a-query)

- `Home` -> `Share`, `Publish`, save the changes if you haven't.
- Select a destination from the list. If you intend to publish and create a live connection later, you want to make sure that you're using what's called a "new experience workspace". `My workspace`, by definition, is a new experience workspace. Locate `My workspace` -> `Select`.
- After loading, click the link `Open 'Countries Populations Final.pbix' in Power BI`.
- Power BI service would ask you to log in, and here is the published report.
- On the lefthand side, you can see `Countries Populations Final` is both a report and a data source, and both of them are in `My workspace`.

## Get a PBIX file from the Power BI Service
- In the Power BI Service page, choose `Get data` in the bottom-left corner -> `Create new content` -> `Files` -> `Get`.
- Choose `Local File` -> `Countries Population Final.pbix` -> `Open`.
- The result will be exactly the same as if I had published it from Power BI Desktop.

## Display Power BI content in Microsoft Teams
The only two sources to display Power BI in Teams are an app that was created using Power BI, or content from the Power BI Service. (Not directly from Power BI Desktop)

- First, choose the channel, or possibly the chat where you want to place the report.
- We choose a channel here, in the top memu, `Add a tab` -> `Power BI` -> select the report from `My workspace`. Make sure this team has been given access to this report in Power BI. Choose whehter you want a post by ticking `Post to the channel about this tab`.
- Before save, you can add "PBI - " to the `tab name` to remind that this is a Power BI file. You can change it later as well.

Remember that tip that we had to make sure that the content published in Teams is actually available to the people that we're sharing it with. Go to Power BI Service and open the report now.
- At the top menu, click `Share`, change permission from `People in your organization`, `People with existing access`, and `Specific people`, also the options of `Allow recipients to share this report` and `Allow recipients to build content with the data associated with this report`.
- After you apply the setting, you can `Copy link` to share it. Or, you can click `Teams`, enter the channel, attach a message to it, and `Share`.
- You will find your link is being shared in Teams now.

## Republish a dataset to the Power BI Service.
If you want to do some changes in Power BI Desktop, you may wish to republish the updated version.

- Open `Countries Populations Final.pbix`, make a duplicate of `South America` page and rename it as `North America`. Drag and put it in front of `South America` to make them in alphabetically order, and amend the `Filters` setting accordingly.
- Simply go to `Home` -> `Share`, `Publish`, save the changes if you haven't. Choose exactly the same destination, `My workspace`.
- Power BI prompts a dialogue and saying `Replace this dataset?`, "You already have a dataset named 'Countries Populations Final' in Power BI". Click on `Replace`, open the link to Power BI Service again.
- Notice that the new version has been published.
- In Microsoft Teams, simply switch to a different channel and come back, you can get the updated report because you republished to the Power BI Service.

In summary, we create data models and reports here in Power BI desktop. But when we want to share them broadly, the best way to do it is to publish them to the Power BI service. And then if we want to use them in Teams or if we want to share them, we can share them directly from the Power BI service. And each time we republish, we are effectively republishing to all of those locations.
