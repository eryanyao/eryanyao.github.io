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

### ALTER TABLE/DROP/RENAME
Allow CRUD the table column

### VIEW
```sql
CREATE VIEW view_name AS
SELECT column_name(s)
FROM table_name
WHERE condition;
```
```sql
CREATE OR REPLACE VIEW ​view_name A
SELECT column_name(s)
FROM table_name
WHERE condition
```
```sql
DROP VIEW ​List
```

### Data type
Data types specify the type of data for a particular column.

If a column called "LastName" is going to hold names, then that particular column should have a "varchar" (variable-length character) data type.
The most common data types:
Numeric
INT -A normal-sized integer that can be signed or unsigned.
FLOAT(M,D) - A floating-point number that cannot be unsigned. You can optionally define the display length (M) and the number of decimals (D).
DOUBLE(M,D) - A double precision floating-point number that cannot be unsigned. You can optionally define the display length (M) and the number of decimals (D).

Date and Time
DATE - A date in YYYY-MM-DD format.
DATETIME - A date and time combination in YYYY-MM-DD HH:MM:SS format.
TIMESTAMP - A timestamp, calculated from midnight, January 1, 1970
TIME - Stores the time in HH:MM:SS format.

String Type
CHAR(M) - Fixed-length character string. Size is specified in parenthesis. Max 255 bytes.
VARCHAR(M) - Variable-length character string. Max size is specified in parenthesis.
BLOB - "Binary Large Objects" and are used to store large amounts of binary data, such as images or other types of files.
TEXT - Large amount of text data.
