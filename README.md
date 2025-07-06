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

#### Case Scenario I

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
 
3. What were the total sales of appliances in Ontario?

   My query returned NULL which implies that there was no sales of Appliances in Ontario.
   
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers

  Recommendations to Increase Revenue:Based on the query results, here are actionable recommendations to increase revenue from the bottom 10 customers:

 a) Targeted Marketing Campaigns: Analyze the customer segment and product category preferences of these customers.Offerng personalized promotions or discounts on high-margin products they are likely to purchase.
	
 b) Customer Engagement: Reach out to these customers with loyalty programs or incentives (e.g., discounts for bulk purchases or referrals) to encourage repeat  purchases.

 c) Cross-Selling Opportunities: Identify products frequently purchased by similar customers in the same segment and recommend these to the bottom 10 customers.
	
 d) Improve Customer Experience: Analyze their order patterns to ensure timely delivery and high-quality service, which may increase their spending.
	
 e) Upselling High-Value Products: Promote higher-priced or complementary products (e.g., furniture or technology items) to these customers based on their segment  and past purchases.

5. KMS incurred the most shipping cost using which shipping method?

   Delivery Truck with total shipping cost of 5,1971.9399

#### Case Scenario II

6. Who are the most valuable customers, and what products or services do they typically purchase?

 a) Emily Phan --------- Office Suplies,Furniture and Technology

 b) Deborah Brumfield  --------- Office Suplies,Furniture and Technology

 c) Roy Skaria  ----------Office Suplies,Furniture and Technology
 
 d) Sylvia Foulston ------Office Suplies,Furniture and Technology
 
 e) Grant Carrol -----Office Suplies,Furniture and Technology

7. Which small business customer had the highest sales?
    Dennis Kane with total sales of 74298.54049

8. Which Corporate Customer placed the most number of orders in 2009 – 2012?
    My query returned NULL impliying no corporate customer placed order in 2009 - 2012.
   
9. Which consumer customer was the most profitable one?

    Emily Phan with a total profit of 34005.44

10. Which customer returned items, and what segment do they belong to?

    About 945 customers returned items

11. If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer

    After running my query,I will say that the company did not choose ship mode based on Order Priority.From the query I ran the result showed that for '3 Critical orders' the company used 3 different ship mode,DElivery Truck,Express Air and Regular Air.

    Below is the query i used to run this analysis;

    
select*
from `kms data (1)`

1)
select `Product Category`,sum(Sales) as
total_sales
from`kms data (1)`
group by `Product Category`
order by total_sales desc
limit 1;

2)
select Region, Sum(Sales) as total_sales
from `kms data (1)`
group by Region
order by total_sales Desc
Limit 3;

select Region, Sum(Sales) as total_sales
from `kms data (1)`
group by Region
order by total_sales Asc
Limit 3;


3)
select sum(Sales) as total_appliance_sales
from`kms data (1)`
where `Product Sub-Category`='Appliances' and
Province ='Ontorio';

4)
select `Customer Name`,sum(Sales) as total_sales
from `kms data (1)`
group by `Customer Name`
order by total_sales ASc
Limit 10;

5) Shipping method with the most shipping cost;
select `Ship Mode`,sum(`Shipping Cost`) as
total_shipping_cost
from `kms data (1)`
group by `Ship Mode`
order by total_shipping_cost DEsc
Limit 1;

6) Most Valuable Customers
select `Customer Name`,sum(Sales) as total_sales
from `kms data (1)`
group by `Customer Name`
order by total_sales DEsc
LImit 5;

Products typically purchased by top customers
SELECT t1.`Customer Name`, t1.`Product Category`, t1.`Product Sub-Category`, 
SUM(t1.Sales) AS total_sales
FROM `kms data (1)` t1
JOIN (
  SELECT `Customer Name`
  FROM `kms data (1)`
  GROUP BY `Customer Name`
  ORDER BY SUM(Sales) DESC
  LIMIT 5
) t2 ON t1.`Customer Name` = t2.`Customer Name`
GROUP BY t1.`Customer Name`, t1.`Product Category`, t1.`Product Sub-Category`
ORDER BY t1.`Customer Name`, total_sales DESC;

7) Small buisness owner with the highest sales
select `Customer Name`,sum(Sales) as total_sales 
from `kms data (1)`
where `Customer Segment`= 'small business'
group by `Customer Name`
order by total_sales desc
limit 1;

8)
select `Customer Name`,count(Distinct `Order ID`)
as order_count
from `kms data (1)`
where `Customer Segment`='Corporate'
and year(`Order Date`) between 2009 and 2012
group by `Customer Name`
order by order_count desc
limit 1;

9)Most profitable customer
select `Customer Name`,sum(Profit) as
total_profit
from `kms data (1)`
where `Customer Segment`='Consumer'
group by `Customer Name`
order by total_profit Desc
Limit 1;

10)
select distinct `Customer Name`,`Customer Segment`
from`kms data (1)`
where Profit <0;

11)
select `Order Priority`,`Ship Mode`,
sum(`Shipping Cost`) as total_shipping_cost,
count(*) as order_count
from `kms data (1)`
group by `Order Priority`,`Ship Mode`
order by `Order Priority`
total_shipping_cost desc;

    
