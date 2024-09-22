# SQL
This repository contains various SQL practice queries.

- [Select](#select)
- [From](#from)
- [Where](#where)
- [Group By](#group-by)
- [Order By](#order-by)
- [Having](#having)
- [Insert](#insert)
- [Update](#update)
- [Delete](#delete)
- [Aggregate functions](#aggregate_functions)
- [Sum](#sum)
- [Count](#count)

# Basic SQL Syntax
# 1) SQL Keywords

## *Select* 
### The SELECT statement in SQL is majorly used for fetching data from the database.

```
SELECT * from customers;
```

```
SELECT county, orderstatus from customers;
```

## The SELECT DISTINCT 
### this statement is used to return only distinct (different) values. 

``` 
SELECT DISTINCT age from customers;
```

## SELECT WHERE
### SELECT statement combined with WHERE gives us the ability to filter records based on a condition.

```
SELECT customer_id from customers WHERE first_name like '%ohn%';
```

```
SELECT customer_id from customers WHERE first_name = "John";
```

```
SELECT first_name from customers WHERE customer_id = 2;
```

## SELECT ORDER BY
### Using SELECT statement in conjunction with ORDER BY, we can sort the result-set in ascending or descending order.

```
SELECT first_name , customer_id from customers
ORDER BY
customer_id;
```

### The default sort order is ascending if the ASC|DESC parameter is not defined.

```
SELECT first_name , customer_id from customers
ORDER BY
customer_id DESC;
```

## *From* 
### to specify the table from which to fetch data. FROM can be used to join tables as well.

```
select * FROM customers;
```

## *Where* 
### Used to filter records. Incorporating a WHERE clause, you might specify conditions that must be met.

```
select * from Customers WHERE Country='Germany';
```
### WHERE clause can be combined with AND, OR, and NOT operators:

```
select * from customers
WHERE country = 'USA'
AND
customer_id = 2;
```

```
select * from customers
WHERE country = 'UK'
OR
customer_id = 4
Or
first_name = 'John';
```

```
select * from customers
WHERE
country = 'USA'
OR
country = 'UK'
```

```select * from customers
WHERE
country in ('USA', 'UK');
```

```
select first_name
from customers
WHERE NOT country = 'USA';
```

```
select * from customers
WHERE first_name LIKE '%Betty%';
```


```
select * from customers
WHERE month(date_ordered) between 3 and 4 ;
```

```
select * from customers
WHERE cost > 10 AND country = 'USA';
```

## *Group By* 
### Used to filter records. Incorporating a WHERE clause, you might specify conditions that must be met.

```
select country,avg(age)
from customers
GROUP BY country;
```

```
select ProductCategory, SUM(SalesAmount) AS TotalSales
from Sales
GROUP BY ProductCategory;
```

### This query groups the data by both CustomerID and the year extracted from OrderDate. It then calculates the total order amount for each customer for each year.
```
SELECT CustomerID, YEAR(OrderDate) AS OrderYear, SUM(OrderAmount) AS TotalOrderAmount
FROM Orders
GROUP BY CustomerID, YEAR(OrderDate);
```

## *ORDER BY*
## The ORDER BY clause in SQL is used to sort the result-set from a SELECT statement in ascending or descending order. 

```
select age
from customers
order by age ;
```

```
select age
from customers
order by age desc;
```

### Multiple Columns in ORDER BY
#### Priority in Sorting:
#### First Priority - first column
#### Second Priority - second column
#### After sorting by the first column, this part specifies that if there are any ties (i.e., if multiple rows have the same age), then the sorting will be done by the second column in the specified order.

```
select *
from customers
order by age desc, customer_id asc;
```

## *HAVING*
### The HAVING clause is used to filter groups after aggregation has taken place.
### It is typically used with GROUP BY to apply conditions on aggregate functions (like SUM(), COUNT(), AVG(), etc.) and filtered results of grouped data.

```
select department, AVG(salary)
from Employees
GROUP BY department
HAVING avg(salary) > 50000;
```

### When used without a GROUP BY clause, the HAVING clause acts similarly to a WHERE clause but is applied after aggregation.

```
select sum(salary) AS total_salary
from employees
HAVING total_salary > 50000;
```

### WHERE: Filters rows before aggregation. It works on individual rows of data. You cannot use aggregate functions directly in a WHERE clause.
### HAVING: Filters groups after aggregation. It works on grouped data and can use aggregate functions to filter those groups.

## Combining WHERE, GROUP BY, and HAVING

```
SELECT salesperson, SUM(amount) AS total_sales
FROM sales
WHERE region = 'North'
GROUP BY salesperson
HAVING total_sales > 5000;
```

## Why We Cannot Use Aggregate Functions in WHERE:
### Order of Execution: SQL processes the WHERE clause before it processes the aggregate functions. 

```
SELECT salesperson, SUM(amount) AS total_sales
FROM sales
WHERE SUM(amount) > 10000
GROUP BY salesperson;
```
### Why This Fails: The above query will produce an error because the WHERE clause tries to use SUM(amount), which is an aggregate function. Since WHERE is evaluated before grouping and aggregation, it cannot reference SUM(amount).

## Correct Approach Using HAVING:
### It is used after the aggregation is performed. HAVING can reference aggregate results because it is evaluated after the GROUP BY operation has taken place.

```
SELECT salesperson, SUM(amount) AS total_sales
FROM sales
GROUP BY salesperson
HAVING SUM(amount) > 10000;
```

## *INSERT*
### There are two main forms of the INSERT command: 

### INSERT INTO table_name (column1, column2, ...): where only named columns will be filled with data.

```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
### INSERT INTO: if we add values for all the columns of the table, then the column names in the SQL query need not be specified. However, the values' order should be the same as the columns in the table.

```
INSERT INTO table_name
VALUES (value1, value2, value, ...);
```

## *UPDATE*
### The UPDATE statement is used to modify the existing records in a table.

```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

## *DELETE*
### The DELETE statement is used to delete existing records in a table.

```
DELETE FROM table_name WHERE condition;
```

# Aggregate Functions

## *SUM*
### The SUM() function returns the total sum of a numeric column.

```
SELECT SUM(column)
FROM table_name;
```

## *COUNT*
### The COUNT() function returns the number of rows that match a specified criterion.

```
SELECT COUNT(*)
FROM column;
```


