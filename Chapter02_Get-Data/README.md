# GET DATA

## Power BI data sources: The basics

`Ribbon` -> `Home` -> `Get data` -> `More...`

Power BI Service has access to a limited number of types of data connections. But Power BI Desktop is toally different. We have six primary data sources. You can always search a particular type of data you want to retrieve in the seraching box.

### :arrow_forward: File
Excel, Text/CSV, XML, SharePoint folder...

### :arrow_forward: Database
SQL Server, Access, Jethro (Beta), IBM Informix database (Beta)..., and some of theses are in beta

### :arrow_forward: Power Platform
Power BI is part of the Microsoft's Power Platform, such as Power BI datasets, Power BI dataflows. 

Dataverse: the updated version of the Common Data Service (Legacy). It is used by all the tools in the Power Platform and other applications like Microsoft Teams.

### :arrow_forward: Azure
Cloud services: Azure SQL Database

### :arrow_forward: Online Services
Microsoft SharePoint Online, Microsoft Exchange Online, Dynamics. Also including other SaaS connections, such as LinkedIn Sales Navigator, Marketo, Smartsheet, Intune Data Warehouse, Webtrends Analytics...

### :arrow_forward: Other
If the data source you are looking for is not in the list, choose Other. We have Web, SharePoint list, Microsoft Exchange. But, we also have the ability to retrieve data using OData feed, ODBC or OLE DB, which means we can connect to almost any data source even if there isn't a pre-built connection for it.

***:sparkle: Whenever we choose a data source and click connect, whatever happens next is based on the data source type we chose to connect to.***

## Connect to a file: Excel
`Home` -> `Excel` -> `MedianAge.xlsx`

1. Under `Suggested Tables`, choose `Countries`, (Optional: then click on `Transform Data`), then click on `Load`.
2. In `Data View`, you can see the data there; In `Report View`, it is empty, but you can see the data in `Fields`.
3. Save this for further work. `File` -> `Save as` -> `MedianAge.pbix`.
4. Close Power BI Desktop.

## Connect to a file: CSV
`Home` -> `Get data` -> `More...` -> `Text/CSV` -> `Connect` -> `GDP.csv`

1. CSV files are flat files that do not content multiple sheets. You get options in choosing 
   - `File Origin` (Windows)
   - `Delimiter`(most common delimiter are comma and colon, some old files are using `--Fixed Width--` with allocated character spaces to specify a field)
   - `Data Type Detection` (if data type are self identified, you can choose `Based on first 200 rows`, otherwise you can decide the datatype by yourself later using `Do not detect data types`)
2. Click on `Load`.
3. Similarly, examine the data in `Data View` and `Report View`.
4. For practice use, you don't need to save the file. You can just close Power BI Desktop and choose `Don't Save`.
