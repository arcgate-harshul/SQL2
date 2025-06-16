ShopEase SQL Project - README.txt

------------------------------------------------------------
📌 PROJECT OVERVIEW
------------------------------------------------------------

This project simulates a simple e-commerce database system for a fictional online store called "ShopEase". It includes tables for customers, products, orders, shipping, and reviews. The data is created, inserted, and queried using SQL, and the project explores basic to advanced SQL concepts including joins, aggregations, and subqueries.

⚠️ Key Assumption:
- Each order contains only one product.
- If the order's TotalAmount matches a product's price multiplied by X, we assume it sold X units of that product.

------------------------------------------------------------
🗂️ TABLE STRUCTURE
------------------------------------------------------------

1. Customers
   - CustomerID (PK)
   - Name
   - Email
   - JoinDate
   - Country

2. Products
   - ProductID (PK)
   - Name
   - Category
   - Price
   - Stock

3. Orders
   - OrderID (PK)
   - CustomerID (FK)
   - OrderDate
   - TotalAmount

4. Shipping
   - ShippingID (PK)
   - OrderID (FK)
   - ShippingDate
   - DeliveryDate
   - Status

5. Reviews
   - ReviewID (PK)
   - ProductID (FK)
   - CustomerID (FK)
   - Rating (1 to 5)
   - ReviewText
   - ReviewDate

------------------------------------------------------------
📥 SAMPLE DATA
------------------------------------------------------------

Includes realistic mock data for:
- 3 customers
- 3 products (2 electronics, 1 stationery)
- 3 orders (with TotalAmount)
- 3 shipping records
- 3 reviews (each mapped to a product and customer)

------------------------------------------------------------
✅ SQL QUERIES INCLUDED
------------------------------------------------------------

🔹 BASIC QUERIES
1. Get names and emails of all customers.
2. List all products with category and price.
3. Count of electronics products.
4. Orders placed by customers from the US.

🔹 INTERMEDIATE QUERIES
5. Total revenue from all orders.
6. Customer with the highest order amount.
7. Products with stock < 50.
8. Reviews with rating 4+.

🔹 JOINS & RELATIONS
9. Display all orders with customer name and email.
10. Show reviews with product and customer names.

🔹 AGGREGATIONS
11. Average rating per product.
12. Revenue by product category (approximate).
13. Country with the most customers.

🔹 FILTERING
14. Orders placed after March 1, 2023.
15. Shipments that are still in transit.

🔹 ADVANCED QUERIES
16. Top-rated product by average rating.
17. Customers who have written at least one review.
18. Products purchased but not reviewed.
19. Product with highest total sales (based on estimation).
20. Products that have never been purchased or reviewed.

------------------------------------------------------------
💡 SPECIAL LOGIC USED
------------------------------------------------------------

✅ Revenue By Product (Estimated):
  Logic assumes: TotalAmount = Product Price × Quantity
  If product price divides the total amount exactly, we assume it was sold in that quantity.

✅ Purchased But Not Reviewed:
  Assumption: All reviewed products were purchased.
  So if a product is missing from the review table, it’s assumed purchased but not reviewed.

✅ Not Purchased Products:
  Products not appearing in the review table are considered never purchased.

------------------------------------------------------------
👨‍💻 CREATED BY
------------------------------------------------------------

Author: Harshul Nihalani  
SQL Project: ShopEase - E-commerce Schema & Analysis  
Date: 2025  
Scope: Intermediate SQL project for practice and interviews.

