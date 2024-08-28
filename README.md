# SQL
This repository contains various SQL practice queries.

# Basic SQL Syntax
# 1) SQL Keywords

## *Select* - The SELECT statement in SQL is majorly used for fetching data from the database.

``` select * from customers; ```

``` select county, orderstatus from customers;```

## The SELECT DISTINCT statement is used to return only distinct (different) values. 

``` select distinct age from customers;```

## SELECT WHERE
### SELECT statement combined with WHERE gives us the ability to filter records based on a condition.

```
select customer_id from customers where first_name like '%ohn%';
```

```
select customer_id from customers where first_name = "John";
```
```
select first_name from customers where customer_id = 2;
```

## SELECT ORDER BY
### Using SELECT statement in conjunction with ORDER BY, we can sort the result-set in ascending or descending order.

```
select first_name , customer_id from customers
order by
customer_id;
```
### The default sort order is ascending if the ASC|DESC parameter is not defined.

```
select first_name , customer_id from customers
order by
customer_id desc;
```

## *From* - to specify the table from which to fetch data.
### FROM can be used to join tables as well.


```
select * FROM customers;
```
