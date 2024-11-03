# LITA_SQL Queries Documentation (Retail Project)

## Description.
This repository contains a detailed documentation of various SQL queries used in different scenarios to analysis a retail store data. It includes queries for Aggregations.

## Analysis And Results.
Aggregates functions; 'SUM' and 'COUNT', were used mostly for the data analysis. The following queries used for this data analysis can be found below;
  1) Retrieve the total sales for each product category.
     
     `Select Product, sum(Quantity) as Total_Sales
      From [Retail csv copy]
      Group by Product;`
     
     This data shows that the product 'Hat' had the highest quanity sold with a total of 15,929 (which is a total percentage of 23.3%) while Jacket had the lowest quantity sold with a total of 5452 (which is a total percentage of 21%).
     
      <img width="414" alt="TS Per Product" src="https://github.com/user-attachments/assets/a52b9362-4908-4d78-8345-981101c4b0f1">


  2) Find the number of sales transactions in each region.
     
      `Select Region, count(*) as Total_Sales_Transactions
       From [Retail csv copy]
       Group by Region;`

     As shown, the 'East Region' has the highest sale transaction of 2483 which is 25.02% while the 'West Region' has the lowest sale transaction of 2477 which is 25%
     
     <img width="407" alt="Sales Per Region" src="https://github.com/user-attachments/assets/5a751214-2167-4253-84f7-fa8dc514fff8">

  3) Find the highest-selling product by total sales value.
     
     `Select Top 1 Product, sum(TotalSales) as Total_Sales
      From [Retail csv copy]
      Group by Product
      Order by Total_Sales desc;`

     The product 'Shoes' is the highest selling product by sales value with the value 613,380 which is a total percentage of 29.2%

     <img width="417" alt="Highest selling" src="https://github.com/user-attachments/assets/a402d697-f08c-420f-b481-a80ab2d31386">

  4) Calculate total revenue per product.
     
     `Select Product, sum(TotalSales) as Total_Revenue
      From [Retail csv copy]
      Group by Product;`

     According to this data analysis, it can be seen that the product 'Shoes' has the highest total revenue generated of 29.2% and the product 'Socks' has the lowest total revenue generated of 8.6%.

     <img width="350" alt="Total revenue" src="https://github.com/user-attachments/assets/ab3df54b-66e5-480e-b215-0ae37e1d2ad7">

  5) Calculate monthly sales totals for the current year.
      
     `Select Month_Name, sum(Quantity) as Total_Sales
      From [Retail csv copy]
      Where Year = '2024'
      Group by Month_Name;`

     The month of 'June' made the highest revenue with the total value of 5928 (20%) while the month of 'May' has the lowest revenue with the total value of 1488 (5%).

     <img width="410" alt="MS for CY" src="https://github.com/user-attachments/assets/79452cd1-1cbe-4bae-8b24-530a695525b9">

  6) Find the top 5 customers by total purchase amount.
      
     `Select Top 5 Customer_Id, sum(TotalSales) as Total_Purchase_Amount
      From [Retail csv copy]
      Group by Customer_Id
      Order by sum(TotalSales) desc;`

     This shows the top 5 customers with the highest purchasing power

      <img width="452" alt="image" src="https://github.com/user-attachments/assets/a587ea76-6d7a-46b6-8201-22d9d95ee4a8">

  7) Calculate the percentage of total sales contributed by each region.
      
     `Select Region, sum(TotalSales) as Total_Sales,
      (sum(TotalSales)/ (select sum(TotalSales) from [Retail csv copy]) *100) as Sales_Percentage
      From [Retail csv copy]
      Group by Region`

     This analysis shows the percentage total of each products. 

     <img width="574" alt="image" src="https://github.com/user-attachments/assets/809cbd23-5668-4a45-8208-e400a2d7de58">

  8) Identify products with no sales in the last quarter.
      
     `Select Product
      From [Retail csv copy]
      Where Product Not In (
      Select Distinct Product
      From [Retail csv copy]
      Where  year = 2024
	    AND Quarter = 3)
      Group by Product;`

     This shows the list of products that didn't make any sale in the last quarter. 

     <img width="455" alt="image" src="https://github.com/user-attachments/assets/739f345d-57a1-4d58-96de-9720f39e50a0">




     







