# dsa-capstone-KMS-sql-project
### Goals And Objectives
We had a 3month virtual training session with Incubator Hub as our trainer.This repository is a project given to the student to test our knowledge of what we have learnt in the past months.
### Company Overview
Kultra Mega Stores (KMS), headquartered in Lagos, specialises in office supplies and furniture. Its customer base includes individual consumers, small businesses (retail), and large corporate clients (wholesale) across Lagos, Nigeria.I have been engaged as a Business Intelligence Analyst to support the Abuja division of
KMS. The Business Manager has shared an Excel file containing order data from 2009 to 2012 and has requested that I analyze the data and present my key insights and
findings.My goal is;
- To understand customer behavior through their purchases
- Track product sales
- Identify key trends in purchases and deliveries

### Methodology and Tools Needed
- Microsoft Excel for Data cleaning.
- MYSQL for analysing data.
- Github for submission.

### Methodology and Tools Needed
- Microsoft Excel for Data cleaning,calculations and Visualization.
- Pivot table for summarizing and analysing data.
- Github for submission.

### Data Source and Description

The primary source of data used here is Kultra Mega Stores Inventory.csv and this is an open source data provided by our instructors.Contained in the dataset is ;

- Product details: Row ID,Order Id, Order Date,Order Priority,Order quantity,Product category,Product name,Product sub-category,Product base,Sales,Unit price,discount,Ship mode,Profit,Ship date and Shipping cost.

- Customer details: Customer name,Province,Region and Customer segment.

### Analysis and Results
I started my analysis by;

Browsing through the data to understand what I have and identify what is needed.

I put my dataset in a table format to help excel recognise my dataset as a structured table.

Icleaned the data by checking for blanks and duplicates, which was not found.

I ensured my file was in a csv format and uploaded it into MYSQL workbench for analysis using queries.

Case Scenario I

1. Which product category had the highest sales?

-Technology had the highest sales of 59,669,69.82199

2. What are the Top 3 and Bottom 3 regions in terms of sales?

 -The top 3 regions in terms of sales are;
 a) West with toal sales of 3569219.45549
 b) Ontoria with total sales of 3024107.119499
 c) Prarie with total sales of 2807846.231499

 -The bottom 3 regions in terms of sales are;
 a) Yukon with total sales of 974102.350
 b) Northwest Territories with total sales of 793919.4995
 c) Nunavut with total sales of 115487.693500
 

2. What were the total sales of appliances in Ontario?
3. Advise the management of KMS on what to do to increase the revenue from the bottom
10 customers
4. KMS incurred the most shipping cost using which shipping method?
