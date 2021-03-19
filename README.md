# SQL Mini Project
A mini-project SQL project completed during training at Sparta Global.

## About this Project
An introduction to SQL basics and intermediate queries. Mainly focusing on DDL and DML commands, this project had been completed within a working week and had consisted of numeral topics. Data had been exported and visually represented in the [PDF](https://github.com/alexsikorski/sql-mini-project/blob/main/SQL_Report_AlexSikorski.pdf) file (you can also view the respective [Excel files](https://github.com/alexsikorski/sql-mini-project/blob/main/docs)). This repository contains a SQL file that was used in Microsoft Azure and the documentation. The Northwind database was used for this project.

[View the SQL file](https://github.com/alexsikorski/sql-mini-project/blob/main/SQL_Practical_Exercise.sql) or [view the PDF file](https://github.com/alexsikorski/sql-mini-project/blob/main/SQL_Report_AlexSikorski.pdf).

## Topics
- Basic Syntax
- Concatenation
- Ordering
- Conditions
- Joins
- Grouping
- Aggregate Functions

## Example Queries
#### Concatenation and LEFT JOIN
```sql
SELECT CONCAT(e.FirstName,' ',e.LastName) AS "Employee Name", CONCAT(emp.FirstName,' ',emp.LastName) AS "Reports To"
FROM Employees e 
LEFT JOIN Employees emp ON e.ReportsTo = emp.EmployeeID
```
#### Wildcard
```sql
SELECT ProductName
FROM Products
WHERE QuantityPerUnit LIKE'%bottle%'
```
#### Aggregate Functions, Sub Queries and INNER JOINs
```sql
SELECT TOP 10 c.CompanyName, SUM((1-od.Discount)*od.Quantity*od.UnitPrice) AS "Value of Orders Shipped" FROM Customers c
INNER JOIN Orders o ON c.CustomerID = o.CustomerID
INNER JOIN [Order Details] od  ON o.OrderID = od.OrderID
WHERE YEAR(o.OrderDate) = YEAR((SELECT TOP 1 OrderDate FROM Orders ORDER BY OrderDate DESC))
AND o.ShippedDate IS NOT NULL 
GROUP BY c.CompanyName
ORDER BY 2 DESC
```
