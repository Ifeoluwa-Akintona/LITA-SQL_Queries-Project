# LITA_SQL Queries Documentation (Retail Project)

## Description.
This repository contains a detailed documentation of various SQL queries used in different scenarios. It includes queries for Aggregations.

## Analysis And Results.
Aggregates functions; 'SUM' and 'COUNT', were used mostly for the data analysis. The following queries used for this data analysis can be found below;
  1) Retrieve the total sales for each product category.
     `Select Product, sum(Quantity) as Total_Sales
      From [Retail csv copy]
      Group by Product;`
     
     <img width="414" alt="TS Per Product" src="https://github.com/user-attachments/assets/a8dcec26-274d-4b4e-8fa6-9b85522a2f52">

  2) Find the number of sales transactions in each region.
      `Select Region, count(*) as Total_Sales_Transactions
       From [Retail csv copy]
       Group by Region;`
     
     <img width="407" alt="Sales Per Region" src="https://github.com/user-attachments/assets/5a751214-2167-4253-84f7-fa8dc514fff8">

  3) Find the highest-selling product by total sales value.
     `Select Top 1 Product, sum(TotalSales) as Total_Sales
      From [Retail csv copy]
      Group by Product
      Order by Total_Sales desc;`

     <img width="417" alt="Highest selling" src="https://github.com/user-attachments/assets/a402d697-f08c-420f-b481-a80ab2d31386">

  4) Calculate total revenue per product.
     `Select Product, sum(TotalSales) as Total_Revenue
      From [Retail csv copy]
      Group by Product;`

     <img width="350" alt="Total revenue" src="https://github.com/user-attachments/assets/ab3df54b-66e5-480e-b215-0ae37e1d2ad7">

  5a) Calculate monthly sales totals for the current year.
     `Select Month_Name, sum(Quantity) as Total_Sales
      From [Retail csv copy]
      Where Year = '2024'
      Group by Month_Name;`

     <img width="410" alt="MS for CY" src="https://github.com/user-attachments/assets/79452cd1-1cbe-4bae-8b24-530a695525b9">
  
  5b) Calculate monthly total reveue for the current year.
      `Select Month_Name, sum(TotalSales) as Total_Revenue
       From [Retail csv copy]
       Where Year = '2024'
       Group by Month_Name;`

      <img width="413" alt="image" src="https://github.com/user-attachments/assets/e5b27cad-b4eb-4e40-ab8d-5c74ea621beb">

  6) Find the top 5 customers by total purchase amount.
     `Select Top 5 Customer_Id, sum(TotalSales) as Total_Purchase_Amount
      From [Retail csv copy]
      Group by Customer_Id
      Order by sum(TotalSales) desc;`

      <img width="452" alt="image" src="https://github.com/user-attachments/assets/a587ea76-6d7a-46b6-8201-22d9d95ee4a8">

  7) Calculate the percentage of total sales contributed by each region.
     `Select Region, sum(TotalSales) as Total_Sales,
      (sum(TotalSales)/ (select sum(TotalSales) from [Retail csv copy]) *100) as Sales_Percentage
      From [Retail csv copy]
      Group by Region`

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

     <img width="455" alt="image" src="https://github.com/user-attachments/assets/739f345d-57a1-4d58-96de-9720f39e50a0">




     







