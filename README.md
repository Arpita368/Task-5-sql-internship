# Task 5: SQL Joins (Inner, Left, Right, Full) with Price

## Objective
Learn how to combine data from multiple tables using different SQL join types: INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN.

## Tools Required
- MySQL Workbench (recommended for all joins)
- DB Browser for SQLite (SQLite does not support FULL or RIGHT joins directly)

## Steps to Execute

1. Create the Customers table
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    name VARCHAR(30),
    phone VARCHAR(10),
    city VARCHAR(20)
);
--------------------------------

2. Create the Orders table
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    product VARCHAR(20),
    price FLOAT,
    FOREIGN KEY(customer_id) REFERENCES Customers(customer_id)
);
--------------------------------

3. Insert data into Customers
INSERT INTO Customers VALUES (1, 'Ravi Sharma','9745834678', 'Mumbai');
INSERT INTO Customers VALUES (2, 'Priya Verma','8345587878', 'Delhi');
INSERT INTO Customers VALUES (3, 'Amit Kumar','9793258778', 'Pune');
INSERT INTO Customers VALUES (4, 'Neha Singh','9432885346', 'Chennai');
--------------------------------

4. Insert data into Orders
INSERT INTO Orders VALUES (101, 1, 'Laptop', 55000.00);
INSERT INTO Orders VALUES (102, 1, 'Keyboard', 1500.00);
INSERT INTO Orders VALUES (103, 2, 'Smartphone', 18000.00);
INSERT INTO Orders VALUES (104, 3, 'Tablet', 12000.00);
--------------------------------

5. View data in Customers
SELECT customer_id, name, phone, city FROM Customers;
--------------------------------

6. View data in Orders
SELECT order_id, customer_id, product, price FROM Orders;
--------------------------------

## SQL Joins Examples

1. INNER JOIN – Returns only matching records from both tables
SELECT C.name, C.city, O.product, O.price
FROM Customers C
INNER JOIN Orders O
ON C.customer_id = O.customer_id;
--------------------------------

2. LEFT JOIN – Returns all records from the left table and matching from right
SELECT C.name, O.product, O.price
FROM Customers C
LEFT JOIN Orders O
ON C.customer_id = O.customer_id;
--------------------------------

3. RIGHT JOIN – Returns all records from the right table and matching from left
SELECT C.name, O.product, O.price
FROM Customers C
RIGHT JOIN Orders O
ON C.customer_id = O.customer_id;
--------------------------------

4. FULL JOIN – Returns all records when there’s a match in either table (MySQL via UNION)
SELECT C.name, C.city, C.phone, O.product, O.price
FROM Customers C
LEFT JOIN Orders O
ON C.customer_id = O.customer_id
UNION
SELECT C.name, C.city, C.phone, O.product, O.price
FROM Customers C
RIGHT JOIN Orders O
ON C.customer_id = O.customer_id;
--------------------------------

## Expected Output Samples

Customers Table:
--------------------------------
customer_id | name         | phone       | city
1           | Ravi Sharma  | 9745834678  | Mumbai
2           | Priya Verma  | 8345587878  | Delhi
3           | Amit Kumar   | 9793258778  | Pune
4           | Neha Singh   | 9432885346  | Chennai

Orders Table:
--------------------------------
order_id | customer_id | product     | price
101      | 1           | Laptop      | 55000.00
102      | 1           | Keyboard    | 1500.00
103      | 2           | Smartphone  | 18000.00
104      | 3           | Tablet      | 12000.00

## Outcome
By running these queries, you will:
- Understand how different joins work
- Learn how to merge customer and order data
- Gain practical skills for database query writing

## Author
Created by Arpita Jitendra Sonparote
