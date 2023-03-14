# GET DATA

## Power BI data sources: The basics

`Ribbon` -> `Home` -> `Get data` -> `More...`

Power BI Service has access to a limited number of types of data connections. But Power BI Desktop is toally different. We have six primary data sources. You can always search a particular type of data you want to retrieve in the seraching box.

**:arrow_forward: File**

Excel, Text/CSV, XML, SharePoint folder...

**:arrow_forward: Database**

SQL Server, Access, Jethro (Beta), IBM Informix database (Beta)..., and some of theses are in beta

**:arrow_forward: Power Platform**

Power BI is part of the Microsoft's Power Platform, such as Power BI datasets, Power BI dataflows. 

Dataverse: the updated version of the Common Data Service (Legacy). It is used by all the tools in the Power Platform and other applications like Microsoft Teams.

**:arrow_forward: Azure**

Cloud services: Azure SQL Database

**:arrow_forward: Online Services**

Microsoft SharePoint Online, Microsoft Exchange Online, Dynamics. Also including other SaaS connections, such as LinkedIn Sales Navigator, Marketo, Smartsheet, Intune Data Warehouse, Webtrends Analytics...

**:arrow_forward: Other**

If the data source you are looking for is not in the list, choose Other. We have Web, SharePoint list, Microsoft Exchange. But, we also have the ability to retrieve data using OData feed, ODBC or OLE DB, which means we can connect to almost any data source even if there isn't a pre-built connection for it.

***When we choose a data source and click connect, what happens next is based on the data source type we chose to connect to.***

## Connect to a file: Excel

1. `Home` -> `Excel` -> `MedianAge.xlsx`
2. Under `Suggested Tables`, choose `Countries`, (Optional: then click on `Transform Data`), then click on `Load`.
3. In `Data View`, you can see the data there; In `Report View`, it is empty, but you can see the data in `Fields`.
4. Save this for further work. `File` -> `Save as` -> `MedianAge.pbix`.
5. Close Power BI Desktop.

## Connect to a file: CSV

1. `Home` -> `Get data` -> `More...` -> `Text/CSV` -> `Connect` -> `GDP.csv`
2. CSV files are flat files that do not content multiple sheets. You get options in choosing 
   - `File Origin` (Windows)
   - `Delimiter` (most common delimiter are comma and colon, some old files are using `--Fixed Width--` with allocated character spaces to specify a field)
   - `Data Type Detection` (if data type are self identified, you can choose `Based on first 200 rows`, otherwise you can decide the datatype by yourself later using `Do not detect data types`)
3. Click on `Load`.
4. Similarly, examine the data in `Data View` and `Report View`.
5. For practice use, you don't need to save the file. You can just close Power BI Desktop and choose `Don't Save`.

## Connect to database
Most exterprise data is kept in a database. Here is an example.

- `Home` -> `Get data` -> `More...` -> `Database` -> `SQL Sever database` -> `Connect`
- Fill out `Server`, `Database (optional)` and Advanced options. You can ask for those information from the database administrator (DBA). 
- You can filter out data beform populating them into Power BI Desktop by writing `SQL statement`.
- You also have choices to `Import` or `DirectQuery`, we will talk about these later in the course. Of note is that there is limited set of data sources that support direct query. `Import` means that the data is going to be coming directly into Power BI and cached for Power BI to use; Direct query actually  creates a direct connection to the database.

Another example,
- `Home` -> `Get data` -> `More...` -> `Database` -> `Amazon Redshift` -> `Connect`
- The view looks similar, but the `Database` is not optional.
- Under Advanced Options, you have `Role` and `Batch Size`.

So, the general process will be:
1. Go to `Get data`
2. Select the type of database
3. Determine what information you need from your DBA
4. Return with that information
5. Connect to your database in Power BI Desktop.

## Connect to web data source
1. `Home` -> `Get data` -> `Web`
2. Paste the link into `URL`: https://en.wikipedia.org/wiki/List_of_countries_by_GDP_(PPP)_per_capita
3. The link shows the List of Countries by GDP with Purchasing Power Parity per capita, we have a large table containing colunmns of data from three different sources.
4. After connected to the web source, you can select a list of tables from the web page. You can select a table, and go to `Web View` to check.
5. Power BI will create queries and import the data. After that, you can examine the data in `Report View` and `Data View`.
6. Save the file as `MyGDOs.pbix` for later use.

## Connect to a SharePoint list
If your organization uses SharePoint either online or on premises, there are some customized lists that were created for your organization.

1. `Home` -> `Get data` -> `More...` -> search `sharepoint`
2. You get result of `SharePoint folder`, `SharePoint Online List`, and `SharePoint list`. Click on `SharePoint Online List`.
3. There are two connectors available under `Implementation`.
   - The version `1.0` connector allows you to retrieve all the columns from the list.
   - The version `2.0` connector allows not only retrieve all colunmns, but also retrieve the columns set in the "Default View"
4. Also, you need to provide `Site URL`, where you should enter the root URL for the SharePoint site not including subfolders. (eg. the URL before "../List.." not including "/List..")
5. You will get everything that is available in that site. Choose the table, click on `Load`, wait for a moment.
6. Examine `Data View` and the field in `Report View`.
7. Since we don't need to use the data later, simply close Power BI.
