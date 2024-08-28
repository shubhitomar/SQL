# SQL
This repository contains various SQL practice queries.

# Basic SQL Syntax
# SQL Keywords

## **Select** - The SELECT statement in SQL is majorly used for fetching data from the database.

``` select * from customers; ```

``` select county, orderstatus from customers;```

## The SELECT DISTINCT statement is used to return only distinct (different) values. 

``` select distinct age from customers;```

## SELECT WHERE
SELECT statement combined with WHERE gives us the ability to filter records based on a condition.

```
select customer_id from customers where first_name like '%ohn%';
```

```
select customer_id from customers where first_name = "John";
```
```
select first_name from customers where customer_id = 2;
```
