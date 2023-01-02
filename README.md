# US-Superstore
Hello! This is a Data Analysis and Visualization project using the US Superstore Dataset which was provided on Kaggle.
Link to Kaggle Dataset Page: https://www.kaggle.com/datasets/juhi1994/superstore
This project was done using SQL (Big Query) and Tableau (Tableau Public).
Link to Tableau Public Dashboards: https://public.tableau.com/app/profile/gabriel.garza7892
The "Vizzes" for this project will be named "US Superstore Dashboards".

## Methodolgy
Data Analysis and Visualization

## Data Analysis
## US Superstore Data Exploration and Visualization
## Checking to see if our data loads
SELECT 
  *
FROM
  `US_Superstore.Superstore`;

## Which Product Category sold the most and is profitable?
SELECT 
  Category,
  ROUND(SUM(Sales),2) AS Total_Sales,
  ROUND(SUM(Profit),2) AS Profit,
  SUM(Quantity) AS Quantity_Sold
FROM
  `US_Superstore.Superstore`
GROUP BY
  Category;


## Which Product Sub Categories sold the most and is profitable? 
SELECT 
  Sub_Category,
  ROUND(SUM(Sales),2) AS Total_Sales,
  ROUND(SUM(Profit),2) AS Profit,
  SUM(Quantity) AS Quantity_Sold
FROM
  `US_Superstore.Superstore`
GROUP BY
  Sub_Category
ORDER BY
  Total_Sales DESC;

## Which Customer Segment provides the most profit?
SELECT
  Segment,
  ROUND(SUM(Profit),2) AS Profit
FROM
  `US_Superstore.Superstore`
GROUP BY
  Segment;

## Which customer segment has made the most shipments?
SELECT
  Segment,
  COUNT(Ship_Mode) AS Total_Shipped
FROM
  `US_Superstore.Superstore`
GROUP BY 
  Segment;

## Which of the cities have made the most amount of sales?
SELECT
  City,
  ROUND(SUM(Sales),2) AS Total_Sales,
  SUM(Quantity) AS Quantity_Sold
FROM
  `US_Superstore.Superstore`
GROUP BY
  City
ORDER BY
  Total_Sales DESC;

## Bottom 10 Cities with the least amount of sales.
SELECT
  City,
  ROUND(SUM(Sales),2) AS Total_Sales,
  SUM(Quantity) AS Quantity_Sold
FROM
  `US_Superstore.Superstore`
GROUP BY
  City
ORDER BY
  Total_Sales
Limit 10;

## Top 10 Customers that have made the most sales in 2017.
SELECT
  Customer_ID,
  Customer_Name,
  ROUND(SUM(Sales),2) AS Total_Sales,
  SUM(Quantity) AS Quantity_Sold
FROM
  `US_Superstore.Superstore`
WHERE
  Order_Date BETWEEN '2017-1-1' AND '2017-12-30'
GROUP BY
  Customer_ID,
  Customer_Name
ORDER BY
  Total_Sales DESC
LIMIT
  10;

## Which Product Sub-Category tend to have a higher discount rate?
SELECT
  Sub_Category,
  ROUND(SUM(Discount),2) AS Discount_Rate
FROM
  `US_Superstore.Superstore`
GROUP BY
  Sub_Category
ORDER BY
  Discount_Rate DESC;

## Which Region had the highest profits?
SELECT
  Region,
  ROUND(SUM(Profit),2) AS Profits
FROM
  `US_Superstore.Superstore`
GROUP BY
  Region
ORDER BY
  Profits DESC;

## Which 10 States had less than 100 quantity sold in 2017?
SELECT
  State,
  SUM(Quantity) AS Quantity_Sold
FROM
  `US_Superstore.Superstore`
WHERE
  Order_Date BETWEEN '2017-1-1' AND '2017-12-30'
GROUP BY
  State
HAVING
  Quantity_Sold < 100
ORDER BY
  Quantity_Sold DESC
LIMIT
  10;

## Data Visualization
This was done using Tableau
![Dashboard 1](https://user-images.githubusercontent.com/120590361/210282631-12b37d49-84d5-488e-abf8-1fb30bc89aed.png)
![Dashboard 2](https://user-images.githubusercontent.com/120590361/210282632-b99f0344-aa76-452a-a8ef-7ca12207c9db.png)
