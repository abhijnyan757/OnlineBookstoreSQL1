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


