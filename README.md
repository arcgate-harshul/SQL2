### ShopEase eCommerce SQL Project

### Overview

This project simulates an online marketplace **ShopEase**, designed to track customers, products, orders, shipping, and reviews using a relational SQL database. It involves table creation, data insertion, and writing queries to analyze sales, customer behavior, and operations.

---

### Highlight: Estimating Quantity Sold Without OrderDetails

The `Orders` table includes only the `TotalAmount`, without specifying which products were bought or how many.  
To estimate sales per product, we apply the logic:

sql
Estimated Quantity = TotalAmount / Product Price


### Schema Structure
1. Customers
Stores customer information.

Column	Type
CustomerID	INT (PK)
Name	VARCHAR(100)
Email	VARCHAR(100)
JoinDate	DATE
Country	VARCHAR(50)

2. Products
Stores details about products.

Column	Type
ProductID	INT (PK)
Name	VARCHAR(100)
Category	VARCHAR(50)
Price	DECIMAL(10,2)
Stock	INT

3. Orders
Stores order records.

Column	Type
OrderID	INT (PK)
CustomerID	INT (FK)
OrderDate	DATE
TotalAmount	DECIMAL(10,2)

4. Shipping
Tracks shipping status.

Column	Type
ShippingID	INT (PK)
OrderID	INT (FK)
ShippingDate	DATE
DeliveryDate	DATE
Status	VARCHAR(50)

5. Reviews
Stores customer feedback.

Column	Type
ReviewID	INT (PK)
ProductID	INT (FK)
CustomerID	INT (FK)
Rating	INT (1–5)
ReviewText	TEXT
ReviewDate	DATE

###  Sample Data Used
sql
Copy
Edit
-- Insert data into Customers
INSERT INTO Customers (CustomerID, Name, Email, JoinDate, Country) VALUES
(1, 'Alice Johnson', 'alice@example.com', '2023-01-15', 'United States'),
(2, 'Bob Smith', 'bob@example.com', '2023-02-20', 'Canada'),
(3, 'Charlie Brown', 'charlie@example.com', '2023-03-05', 'United Kingdom');

-- Insert data into Products
INSERT INTO Products (ProductID, Name, Category, Price, Stock) VALUES
(1, 'Wireless Mouse', 'Electronics', 25.99, 150),
(2, 'Bluetooth Headphones', 'Electronics', 79.99, 100),
(3, 'Notebook', 'Stationery', 5.49, 300);

-- Insert data into Orders
INSERT INTO Orders (OrderID, CustomerID, OrderDate, TotalAmount) VALUES
(1, 1, '2023-03-10', 51.98),
(2, 2, '2023-03-15', 79.99),
(3, 3, '2023-03-20', 16.47);

-- Insert data into Shipping
INSERT INTO Shipping (ShippingID, OrderID, ShippingDate, DeliveryDate, Status) VALUES
(1, 1, '2023-03-11', '2023-03-14', 'Delivered'),
(2, 2, '2023-03-16', '2023-03-20', 'Delivered'),
(3, 3, '2023-03-21', NULL, 'In Transit');

-- Insert data into Reviews
INSERT INTO Reviews (ReviewID, ProductID, CustomerID, Rating, ReviewText, ReviewDate) VALUES
(1, 1, 1, 5, 'Great product! Works perfectly.', '2023-03-12'),
(2, 2, 2, 4, 'Good sound quality, but a bit pricey.', '2023-03-18'),
(3, 3, 3, 3, 'Decent notebook, but paper quality could be better.', '2023-03-22');
✅ Key Queries Solved
🔹 Basic
Retrieve customer names and emails

List products by category and price

Count electronics items

Intermediate
Total revenue from all orders

Customer with highest spending

Low stock products

High-rated reviews (4+)

joins
Orders with customer details

Reviews with product and customer names

Aggregations
Average rating per product

Revenue per product category

Country with most customers

Advanced & Subqueries
Top-rated product

Customers who reviewed

Products purchased but not reviewed

Products not purchased at all

Sample Logic: Product with Highest Sales
sql
Copy
Edit
SELECT 
    P.ProductID,
    P.Name,
    SUM(O.TotalAmount) AS EstimatedTotalSales
FROM 
    Orders O
JOIN 
    Products P ON ROUND(O.TotalAmount / P.Price) = O.TotalAmount / P.Price
GROUP BY 
    P.ProductID, P.Name
ORDER BY 
    EstimatedTotalSales DESC
LIMIT 1;
This query estimates the sales based on price match and sums total revenue per product.

📌 Notes
Designed under the assumption that each order involves only one product.

Real-world systems use an OrderDetails table to manage product quantities.

Ideal for learning JOIN, AGGREGATE, and SUBQUERY techniques in SQL.

🙌 Author
Harshul Nihalani
Project: eCommerce SQL Mock Test (Intermediate Level)
