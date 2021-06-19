---
layout: post
title: SQL Note
---

Below is my SQL note for preparing my interview.
- SQL stands for Structured QUERY LANGUAGE, used for communicate with database
- MYSQL is relational database management system
<br><br>

#### CRUD
> - INSERT INTO table (column) VALUES (value)
> - SELECT * FROM table
> - UPDATE table SET tableName = ""
> - DELETE FROM table WHERE condition

### SELECT
#### DISTINCT and LIMIT
- DISTINCT: select not repeat
> SELECT DISTINCT column FROM table;
- LIMIT: select only how many row
> SELECT column list
FROM table_name
LIMIT [number of records];

### WHERE
- WHERE condition
- Condition can be 
#### BETWEEN
```sql
SELECT * FROM customer
WHERE id BETWEEN 10 AND 99
```
#### AND/OR
```sql
SELECT * FROM customer
WHERE (id = 1 OR id = 2)
AND city = 'Boston'
```
#### IN/ NOT IN
```sql
SELECT name, state FROM customers 
WHERE state IN ('MY','SG','TW');
```
```sql
SELECT name, state FROM customers 
WHERE state NOT IN ('MY','SG','TW');
```
### SUBQUERY
### JOIN
#### UNION
> The UNION operator is used to combine the result-sets of two or more SELECT statements.
```sql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```
#### UNION ALL
> SELECT ALL ROW INCLUDING REPEAT ROW

![image](https://user-images.githubusercontent.com/74011230/122631179-4e5d3780-d0fc-11eb-92fd-4cbb38a178a6.png)

### OTHER
#### CONCAT/AS
- CONCAT
> is used to concatenate two or more text values and returns the concatenating string.
```sql
SELECT CONCAT (name, ',', state) AS new_column_name
FROM customers
```
#### UPPER/LOWER
```sql
SELECT UPPER(name), LOWER(nickname) FROM customer 
```
#### SQRT/AVG/SUN
- The SQRT function returns the square root of given value in the argument.
```sql
SELECT SQRT(salary) FROM employee;
```
- the AVG function returns the average value of a numeric column:
```sql
SELECT AVG(money) FROM customer;
```
- SUM function is used to calculate the sum for a column's values.
```sql
SELECT SUM(money) FROM customer;
```
#### LIKE
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE 'A%';
```
- 'A%'
- '%A'

### SQL Example
```sql
SELECT * FROM Apartments 
WHERE price > (SELECT AVG(price) FROM Apartments) 
AND status = 'Not rented' 
ORDER BY price
```
