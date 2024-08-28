# SQL
This repository contains various SQL practice queries.

# Basic SQL Syntax
# 1) SQL Keywords

## *Select* - The SELECT statement in SQL is majorly used for fetching data from the database.

```
SELECT * from customers;
```

```
SELECT county, orderstatus from customers;
```

## The SELECT DISTINCT statement is used to return only distinct (different) values. 

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

## *From* - to specify the table from which to fetch data.
### FROM can be used to join tables as well.


```
select * FROM customers;
```

## *Where* - Used to filter records. Incorporating a WHERE clause, you might specify conditions that must be met.

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
