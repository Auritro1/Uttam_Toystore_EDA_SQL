# Uttam_Toystore_EDA_SQL

## Description
A brief description of your project, what it does, and its purpose.

## Tables

### `inventory`
- **Store_ID**: ID of the store.
- **Product_ID**: ID of the product.
- **Stock_On_Hand**: The current stock of each product.

### `products`
- **Product_ID**: Unique identifier for each product.
- **Product_Name**: Name of the product.
- **Product_Category**: Category of the product.
- **Product_Cost**: Cost price of the product.
- **Product_Price**: Selling price of the product.

### `sales`
- **Sale_ID**: Unique identifier for each sale.
- **Sale_Date**: Date of the sale.
- **Store_ID**: ID of the store where the sale took place.
- **Product_ID**: ID of the product sold.
- **Units**: Number of units sold.

### `stores`
- **Store_ID**: Unique identifier for each store.
- **Store_Name**: Name of the store.
- **Store_City**: City where the store is located.
- **Store_Location**: Address or area of the store.
- **Store_Open_Date**: Date the store was opened.

## SQL Queries

### 1. Total Sales Revenue by Store
```sql
SELECT 
  s2.Store_ID, 
  s2.Store_Name,
  ROUND(SUM(p.Product_Price * s1.Units)::NUMERIC, 2) AS Total_Revenue
FROM stores s2
JOIN sales s1 ON s2.Store_ID = s1.Store_ID
JOIN products p ON s1.Product_ID = p.Product_ID
GROUP BY s2.Store_ID, s2.Store_Name;
