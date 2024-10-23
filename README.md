# Reorganisation_Sales_And_Location-_Anakysis
Project entails the analysis of sales, revenue for consolidation and optimization., Client is an wholesale importer and distributor of novelty goods

# OUTLINE
 [Project Overview](#project-overview)
 
[Data Source](#data-source)

[Tools](#tools)

[High level requirements](#high-level-requirements)

[Data modeling](#data-modeling)

[Data Analysis](#data-analysis)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Forecasting](#forecasting)

[Business Process Flow](#business-process-flow)

[Reporting](#reporting)

 
## Project Overview
Client is a wholesale importer and distributor of novelty goods operating from the United States of America. Buys novelty goods from Suppliers, Manufacturer and Wholesalers, they also engage in buying packaging materials in large quantities and warehouse. They sell to their customers via network of agents, wholesale Customers in turn resell to retail outlets across the network. Growing competition , increasing sales dynamics and rising Customer expectation  makes it imperative for the Management to embark on the project to reorganize and consolidate operations for business optimization and reduced cost of doing business
---
## Data Source
The data used in this project is sourced from customer database and is stored in a CSV format, named `customer_data.csv`.
---
## Tools
### Agile Methodologies was used in this Project
- Confluence -Project planning, collaboration within team, documentation 
- Jira-project management, reporting and tracking
- SQL-Data analysis and Investigate relationship between data
- Power BI-Data analysis, modeling, visualization and reporting
- Draw.io- Business process flow chart.
---
## High level requirements
### Data modeling
- Data extraction - from SQL-Structured Querry Language [DOWNLOAD HERE](https://1drv.ms/w/s!ApWnci176Rvogx7ot_oLHxoFDL0c?e=vUtqeh)
- Data importation- to Power BI 
- Data validation and  transformation- Fit and ready for analysis
---
### Data Analysis
- Define KPI”s
- Sales analysis -(sub task *- By Province, *by product category)
- Revenue analysis- (sub task- *by Province, *by product categories) 
- Customer analysis-(sub tasks -by product categories, by province)
- Visualization/Dashboard
---
### Exploratory Data Analysis
#### EDA involved exploring the Data to answer the following questions
  1.  What is the sales trend in all the Provinces
  2.  What is the Revenue trend in all the Provinces
  3.  Which are the Top 5 Provinces by Sales/Revenue
  4.  What are the Customer Categories
  5.  Which are the top 2 Customer Categories in each of the 5 Provinces
  6   What is Population by Province
---
### Forecasting
- 3 year revenue forecast -for entire 49 districts 
- Top Selling  Provinces (3 year forecast)
- Market trend analysis- Periodic trend analysis
---  
### Business Process Flow
- Current state of business Process flow 
- Define Process steps
- Analyze process performance
- Map out process steps-Flow Diagram
- Review and validate 
---
### Reporting
- SWOT analysis
- Risk analysis
- Rationale for sales restriction
--- 
###Data Analysi-Here we have some basic codes used
- To identify top 5 Provinces by revenue 

- Top 2 Customers from each of the 5 Provinces Identified by Customer categories. 

 We needed the sales table and the Customer /Location table; 

 Sales Table—Sales table was created by joining the Invoice Table and the Invoice line Table using an INNER JOIN on INVOICE ID; 

 

```SQL
SELECT * FROM [Sales].[Invoices]----70,510 rows
 ```

```SQL
SELECT * FROM [Sales].[InvoiceLines]---228,265rows
```

 

```SQL
SELECT 

SI.[InvoiceID] 

,[OrderID]  

,[CustomerID] 

,[InvoiceDate] 

,[Quantity] 

,[StockItemID] 

,[UnitPrice] 

,[TaxAmount] 

,[LineProfit] AS PROFIT 

,[ExtendedPrice] AS SALES 

,[Quantity]*[UnitPrice] AS REVENUE 

  

 

FROM [Sales].[Invoices]  SI 

INNER JOIN[Sales].[InvoiceLines] SIL 

ON SI.[InvoiceID]=SIL.[InvoiceID]
```

 

 

 

2.  The Customer Table –This was created by Left join of tables below; 

```SQL
SELECT* FROM [Sales].[Customers]-----633 ROWS 

SELECT*FROM[Sales].[CustomerCategories]----8ROWS  

SELECT * FROM[Sales].[CustomerTransactions]--97,147ROWS 

  

SELECT*FROM[Application].[Countries]---190ROWS 

SELECT* FROM[Application].[Cities]----37,040ROWS 

SELECT *FROM[Application].[StateProvinces]---53ROWS 

SELECT*FROM[Sales].[Invoices]---70,510ROWS
```

------------------------------------------------------------------------------------- 
```SQL
SELECT 

[CustomerID] 

,[CustomerName] 

,[CityID] 

,[CityName] 

,AP.[StateProvinceID] 

,[StateProvinceName] AS PROVINCE 

,AP.[LatestRecordedPopulation] 

,[SalesTerritory] 

,SCC.[CustomerCategoryID] 

,[CustomerCategoryName] 

  

FROM[Sales].[Customers] SC 

LEFT JOIN [Application].[Cities] AC 

ON SC.[DeliveryCityID]=AC.[CityID] 

LEFT JOIN[Sales].[CustomerCategories] SCC 

ON SC.[CustomerCategoryID]=SCC.[CustomerCategoryID] 

LEFT JOIN[Application].[StateProvinces] AP 

ON AC.[StateProvinceID]=AP.[StateProvinceID] 

```
 

The two tables joined by the CustomerID 
 


 



 



 
