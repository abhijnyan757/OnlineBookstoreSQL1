# OnlineBookstoreSQL1
SQL project for an Online Bookstore: tables, queries, and data analysis
# Online Bookstore SQL Database

## Project Overview
This project demonstrates a fully functional **Online Bookstore database** built using **PostgreSQL**.  
It simulates a real-world e-commerce bookstore, allowing users to store, manage, and analyze data about books, customers, and orders.  

The project includes **table creation**, **data import**, and **advanced SQL queries** to gain business insights.

---

## Tables

### 1. Books
Stores information about all books in the bookstore.

| Column          | Data Type      | Description                        |
|-----------------|----------------|------------------------------------|
| Book_ID         | SERIAL         | Primary key                        |
| Title           | VARCHAR(90)    | Name of the book                   |
| Author          | VARCHAR(90)    | Author of the book                 |
| Genre           | VARCHAR(60)    | Genre of the book                  |
| Published_Year  | INT            | Year the book was published        |
| Price           | NUMERIC(10, 2) | Price of the book                  |
| Stock           | INT            | Available quantity in stock        |

---

### 2. Customers
Stores customer information.

| Column       | Data Type   | Description                |
|--------------|------------|----------------------------|
| Customer_ID  | SERIAL      | Primary key               |
| Name         | VARCHAR(100)| Customer name             |
| Email        | VARCHAR(100)| Customer email            |
| Phone        | VARCHAR(15) | Customer phone number     |
| City         | VARCHAR(50) | Customer city             |
| Country      | VARCHAR(150)| Customer country          |

---

### 3. Orders
Tracks customer orders for books.

| Column       | Data Type      | Description                           |
|--------------|----------------|---------------------------------------|
| Order_ID     | SERIAL          | Primary key                          |
| Customer_ID  | INT             | References Customers(Customer_ID)    |
| Book_ID      | INT             | References Books(Book_ID)            |
| Order_Date   | DATE            | Date of order                         |
| Quantity     | INT             | Number of books ordered               |
| Total_Amount | NUMERIC(10, 2)  | Total price for the order             |


---

## Features

- ✅ Create and manage **Books, Customers, Orders** tables  
- ✅ Import CSV data into tables using `COPY`  
- ✅ Perform queries to retrieve, filter, and analyze data  
- ✅ Calculate **total revenue**, **top-selling books**, **remaining stock**, and more  
- ✅ Advanced SQL techniques: `JOINs`, `GROUP BY`, `ORDER BY`, `SUM()`, `AVG()`, `COALESCE`, `DISTINCT`  

---

## Sample Queries

```sql
-- Retrieve all Fiction books
SELECT *
FROM Books
WHERE Genre = 'Fiction';

-- Calculate total revenue
SELECT SUM(Total_Amount) AS Revenue
FROM Orders;

-- Find the top 3 most expensive Fantasy books
SELECT *
FROM Books
WHERE Genre = 'Fantasy'
ORDER BY Price DESC
LIMIT 3;

-- Find the most frequently ordered book
SELECT o.Book_ID, b.Title, COUNT(o.Order_ID) AS Order_Count
FROM Orders o
JOIN Books b ON o.Book_ID = b.Book_ID
GROUP BY o.Book_ID, b.Title
ORDER BY Order_Count DESC
LIMIT 1;
