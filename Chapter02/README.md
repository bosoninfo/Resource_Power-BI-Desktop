# GET DATA

## :potted_plant:Overview:potted_plant:
In this chapter, we'll delve into the process of getting data into Power BI Desktop from various sources. Data is the lifeblood of any business intelligence application, and Power BI Desktop offers a wide range of data connection options to meet your needs. Whether you're connecting to files, databases, web sources, SharePoint lists, or Microsoft Dataverse, this chapter will guide you through each step.

We'll start by discussing the basics of Power BI data sources and how to navigate the available options. You'll learn how to connect to different types of files, such as Excel and CSV, and explore ways to connect to databases like SQL Server and Amazon Redshift. We'll also show you how to connect to web data sources and SharePoint lists, making sure you have all the information you need to access your organization's data.

Next, we'll introduce you to Microsoft Dataverse, a powerful cloud-based data storage and management platform that integrates seamlessly with Power BI. You'll learn how to connect Power BI Desktop to Dataverse and understand the advantages of using it in your data management workflow.

Furthermore, we'll discuss advanced data connection types like DirectQuery and live connections, and explain when and why you should use them. These connection types allow you to keep your data up-to-date and minimize the need for manual refreshes, ensuring that your reports and visualizations are always accurate and current.

Lastly, we'll cover the process of opening and modifying existing Power BI files (PBIX) or Excel data models, as well as changing the data source for a PBIX file. This is particularly useful when you need to update the data source or path, or when transferring files between different users or systems.

By the end of this chapter, you'll be confident in connecting to a wide range of data sources and managing your data effectively within Power BI Desktop. So let's dive in and start unlocking the power of your data!

---
|Table of Sections|
|---|
|<ul><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#power-bi-data-sources-the-basics">Power BI data sources: The basics</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#connect-to-a-file-excel">Connect to a file: Excel</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#connect-to-a-file-csv">Connect to a file: CSV</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#connect-to-database">Connect to database</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#connect-to-web-data-source">Connect to web data source</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#connect-to-a-sharepoint-list">Connect to a SharePoint list</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#connect-to-microsoft-dataverse">Connect to Microsoft Dataverse</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#power-bi-data-connections">Power BI Data Connections</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#open-a-pbix-file-or-excel-data-model">Open a PBIX file or Excel data model</a></li><li><a href="https://github.com/JefoGao/Resourse_Power-BI-Desktop/blob/main/Chapter02/README.md#change-the-data-source-for-a-pbix-file">Change the data source for a PBIX file</a></li></ul>|

## Power BI data sources: The basics

`Ribbon` -> `Home` -> `Get data` -> `More...`

Power BI Service offers access to a limited number of data connections. However, Power BI Desktop provides a wider range of options with six primary data sources. You can easily search for a specific data type to retrieve using the search box.

**:arrow_forward: File**

- Examples: Excel, Text/CSV, XML, SharePoint folder, etc.

**:arrow_forward: Database**

- Examples: SQL Server, Access, Jethro (Beta), IBM Informix database (Beta), etc. Note that some of these are in beta.

**:arrow_forward: Power Platform**

- Power BI is part of Microsoft's Power Platform, which includes Power BI datasets and Power BI dataflows.

- **Dataverse**: This is the updated version of the Common Data Service (Legacy). It is used by all tools within the Power Platform and other applications like Microsoft Teams.

**:arrow_forward: Azure**

- Examples: Cloud services like Azure SQL Database.

**:arrow_forward: Online Services**

- Examples: Microsoft SharePoint Online, Microsoft Exchange Online, Dynamics, LinkedIn Sales Navigator, Marketo, Smartsheet, Intune Data Warehouse, Webtrends Analytics, and other SaaS connections.

**:arrow_forward: Other**

If the data source you're looking for isn't listed, choose 'Other'. Examples include Web, SharePoint list, Microsoft Exchange, OData feed, ODBC, and OLE DB. This means you can connect to almost any data source, even if there isn't a pre-built connection for it.

***When you choose a data source and click 'Connect', the next steps depend on the type of data source you chose to connect to.***

## Connect to a file: Excel

1. `Home` -> `Excel` -> `MedianAge.xlsx`
2. Under `Suggested Tables`, choose `Countries`, (Optional: then click on `Transform Data`)
3. Click on `Load`.
4. In `Data View`, you can see the data; In `Report View`, it is empty, but you can see the data in `Fields`.
5. Save this for further work. `File` -> `Save as` -> `MedianAge.pbix`.
6. Close Power BI Desktop.

## Connect to a file: CSV

1. `Home` -> `Get data` -> `More...` -> `Text/CSV` -> `Connect` -> `GDP.csv`
2. CSV files are flat files that do not content multiple sheets. You get options in choosing 
   - `File Origin` (Windows)
   - `Delimiter` (most common delimiter are comma and colon, some old files are using `--Fixed Width--` with allocated character spaces to specify a field)
   - `Data Type Detection` (if data type are self identified, you can choose `Based on first 200 rows`, otherwise you can decide the datatype by yourself later using `Do not detect data types`)
3. Click on `Load`.
4. Similarly, examine the data in `Data View` and `Report View`.
5. For practice use, you don't need to save the file. Close Power BI Desktop and choose `Don't Save`.

## Connect to database
Most enterprise data is stored in databases. Here's an example:

- `Home` -> `Get data` -> `More...` -> `Database` -> `SQL Sever database` -> `Connect`
- Fill out `Server`, `Database (optional)` and Advanced options. You can ask for those information from the database administrator (DBA). 
- You can filter out data beform populating them into Power BI Desktop by writing `SQL statement`.
- You also have choices to `Import` or `DirectQuery`, we will talk about these later in the course. Of note is that there is limited set of data sources that support direct query. `Import` means that the data is going to be coming directly into Power BI and cached for Power BI to use; Direct query actually  creates a direct connection to the database.

Another example,
- `Home` -> `Get data` -> `More...` -> `Database` -> `Amazon Redshift` -> `Connect`
- The view looks similar, but the `Database` is not optional.
- Under Advanced Options, you have `Role` and `Batch Size`.

***So, the general process for connecting to a database in Power BI Desktop will be:***
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

## Connect to Microsoft Dataverse
:link: http://powerapps.microsoft.com

Microsoft Dataverse, formerly known as Common Data Service (CDS), is a cloud-based data storage and management platform that allows users to store and manage data for their business applications. It provides a unified and secure data storage solution that can be used across different Microsoft applications such as Dynamics 365, Power Apps, and Power BI.

Dataverse enables businesses to create custom data models, define business rules and workflows, and manage data entities and relationships. It also provides data validation and data integration capabilities, allowing data to be easily imported or exported from other sources.

With Dataverse, users can easily build and deploy custom business applications using low-code or no-code development tools such as Power Apps, Microsoft Flow, and Power BI. These applications can be used to automate business processes, manage data, and gain insights into business performance.

1. Locate yourself to Microsoft Power Apps, ensure the environment is correct (located in the top-right corner, eg. KinetEco)
2. Go to `Settings` -> `Session details`, look at `Instance url`, but you only need the middle part between "https://" and "/" the trails the string, which is the "{organization_code}.crm.dynamics.com", copy it.
3. Return to Power BI Desktop, go to `Home` -> `Dataverse`, paste the url in `Environment domain`.
4. If we choose `import`, the data will be cached in Power BI Desktop in our model. Save here so that we can work with it very robustly. We only choose `DirectQuery` if we have to have current data minute by minute. Because if we use direct query, every time we refresh, anything we build just go back out and go to get data. Leave it as "import" here, and click `OK`.
5. You may be prompted to log in again to your account.
6. You will see a list of all the tables that are available, you can use search box to find the one you want. The tables have the appropriate structure with empty data. You can bring multiple tables at the same time.

## Power BI Data Connections
*Advanced connection types: DirectQuery and live connections*

### Connection Modes
- Import
- Live connection
- DirectQuery

### :sparkle: Import (fastest) - Use most of the time
- Loaded data is imported into Power BI cache
- Visualizations are created using data in the cache
- Report data must be refreshed to view changes in visualizations
- Default connection method in Power BI

### :sparkle: DirectQuery (slower than import) - Use for some organizations
- Loaded data is not imported into Power BI cache (every time it retrieves data from data source)
- Visualizations are created using the data source
- Report data must still be refreshed to view changes in visualizations
- Each time you open or create a report, the data source is querried
- Not available for all data connections

#### *Why Use DirectQuery?* 
- Data must be up-to-the-minute
- Data source too large to import

### :sparkle: Live Connections (faster than DirectQuery) - Use sometimes
- Data sources
   - SQL Server Analysis Services
   - Dataverse
   - Common Data Service (legacy)
   - Power BI datasets published to powerbi.com
- Support dataset sharing in Power BI
- Data souce is queried directly, but the data source itself is living in the Power BI Service

## Open a PBIX file or Excel data model
There's another way that we can bring data directly into Power BI Desktop, and that is to open a data model that was created either using Power BI Desktop or perhaps a data model that was created using Excel and the tools like Power Pivot and Power Query that work with Microsoft Excel. 

- `File` -> `Browse reports` -> `MedianAge.pbix`
- `File` -> `Import` -> `Power Query, Power Pivot, Power View` -> look for Excel file

## Change the data source for a PBIX file
When we create a data model and save it as a PBIX file, we begin by getting data from a source. And when we saved this PBIX file, that data source connection was saved as part of the file.

- `Home` -> `Transform data` -> `Data source settings` -> you can find the location of the data source. But your PBIX file may be stored in a different path to the data source.
- When you transfer the PBIX file to others, the data source path will not be the same as it is in your computer. If you use SharePoint or OneDrive to locate the data source, it could be fine. But if you use an Excel workbook, there will be a problem even you send the Excel workbook.
- So you need to be able to change the path. Highlight the path, click on `Change Source...` -> `Browse` -> find the file you are looking for to create a connection to your version of the Excel workbook.
- Except for that, other use case may be you want to use an entirely different set of data. If both data sources have the same columns, you can simply change the data source and use the same report that you have built in Power BI. You can have a read on `Changing the data source for a PBIX file.pdf` file and use it to explain to someone else as well.
