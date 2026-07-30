# SQL (Structured Query Language)

# Introduction

SQL (Structured Query Language) is the standard language used to communicate with Relational Database Management Systems (RDBMS). It allows users to create databases, store data, retrieve data, update data, and delete data efficiently.

Almost every modern application stores its data in a database, and SQL is the language used to interact with those databases.

Some popular SQL databases are:

- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server
- SQLite



---


# Why Do We Need SQL?

Suppose a college has 20,000 students.

Without SQL:

- Searching a student is difficult.
- Updating marks is difficult.
- Deleting records is time-consuming.
- Maintaining relationships is almost impossible.

SQL solves all these problems.

---

# Features of SQL

- Easy to learn
- Standard language
- High performance
- Supports large databases
- Supports relationships
- Secure
- Portable
- Supports transactions
- Data integrity
- Multi-user support

---

# Advantages of SQL

- Fast data retrieval
- Easy data management
- Less redundancy
- Data consistency
- Backup and recovery
- Supports multiple users
- Secure access
- Powerful querying capabilities

---

# Disadvantages of SQL

- Fixed schema
- Complex joins for beginners
- Scaling large systems can be challenging
- Commercial databases can be expensive
- Less flexible than NoSQL for unstructured data

---

# SQL vs NoSQL

| SQL | NoSQL |
|------|--------|
| Relational Database | Non-Relational Database |
| Stores data in tables | Stores data as documents, key-value pairs, graphs, etc. |
| Fixed schema | Flexible schema |
| Supports joins | Joins are generally avoided |
| ACID transactions | Depends on the database |
| Best for structured data | Best for unstructured or semi-structured data |
| Examples: MySQL, PostgreSQL | Examples: MongoDB, Cassandra |

---

# Why Learn SQL?

SQL is one of the most important skills for:

- Software Developers
- Backend Developers
- Data Analysts
- Data Scientists
- Database Administrators
- Full Stack Developers

Almost every company uses SQL somewhere in its technology stack.

---


# SQL Categories

SQL commands are divided into five categories.

## 1. DDL (Data Definition Language)

Used to define the database structure.

Commands:

- CREATE
- ALTER
- DROP
- TRUNCATE
- RENAME

Example:

```sql
CREATE TABLE Student (
    StudentID INT,
    Name VARCHAR(50)
);


---

# 1. DDL (Data Definition Language)

DDL commands are used to define and modify the structure of a database and its objects.

They do **not** manipulate the data; instead, they define how the data will be stored.

DDL Commands:

- CREATE
- ALTER
- DROP
- TRUNCATE
- RENAME

---

# CREATE DATABASE

Used to create a new database.

### Syntax

```sql
CREATE DATABASE CollegeDB;
```

### Example

```sql
CREATE DATABASE CollegeDB;
```

---

# USE DATABASE

Selects a database to work with.

### Syntax

```sql
USE DatabaseName;
```

### Example

```sql
USE CollegeDB;
```

---

# CREATE TABLE

Creates a new table inside the database.

### Syntax

```sql
CREATE TABLE TableName
(
    Column1 DataType,
    Column2 DataType,
    ...
);
```

### Example

```sql
CREATE TABLE Student
(
    StudentID INT,
    Name VARCHAR(100),
    Age INT,
    City VARCHAR(50)
);
```

Result

| StudentID | Name | Age | City |
|------------|------|-----|------|

The table structure is created, but no data is stored yet.

---

# DESCRIBE TABLE

Displays the structure of a table.

### Syntax

```sql
DESC Student;
```

Output

| Field | Type | Null | Key |
|--------|------|------|-----|
| StudentID | INT | YES | |
| Name | VARCHAR(100) | YES | |
| Age | INT | YES | |
| City | VARCHAR(50) | YES | |

---

# ALTER TABLE

Used to modify an existing table.

---

## Add a Column

```sql
ALTER TABLE Student
ADD Email VARCHAR(100);
```

Before

| StudentID | Name | Age | City |

After

| StudentID | Name | Age | City | Email |

---

## Modify Column

```sql
ALTER TABLE Student
MODIFY Name VARCHAR(150);
```

---

## Rename Column

```sql
ALTER TABLE Student
RENAME COLUMN City TO Address;
```

---

## Drop Column

```sql
ALTER TABLE Student
DROP COLUMN Email;
```

---

# RENAME TABLE

Changes the table name.

```sql
RENAME TABLE Student TO Students;
```

---

# TRUNCATE TABLE

Deletes all records but keeps the table structure.

Before

|ID|Name|
|--|----|
|1|Adil|
|2|Rahul|

Command

```sql
TRUNCATE TABLE Student;
```

After

|ID|Name|
|--|----|

Table still exists.

---

# DROP TABLE

Deletes the table completely.

```sql
DROP TABLE Student;
```

The table structure and all records are permanently removed.

---

# DROP DATABASE

Deletes the complete database.

```sql
DROP DATABASE CollegeDB;
```

Everything inside the database is deleted.

---

# Difference Between DROP and TRUNCATE

| DROP | TRUNCATE |
|-------|-----------|
| Deletes table | Deletes data only |
| Structure removed | Structure remains |
| Cannot use table afterwards | Can insert data again |
| Slower | Faster |

---



## Common SQL Data Types

    | **Category**         | **Data Type**                   | **Description**                                                        | **Example**                 |
    | -------------------- | ------------------------------- | ---------------------------------------------------------------------- | --------------------------- |
    | **Numeric**          | `SMALLINT`                      | 2-byte integer (-32,768 to 32,767)                                     | `age SMALLINT`              |
    |                      | `INT` / `INTEGER`               | 4-byte integer                                                         | `quantity INT`              |
    |                      | `BIGINT`                        | 8-byte integer                                                         | `views BIGINT`              |
    |                      | `DECIMAL(p,s)` / `NUMERIC(p,s)` | Exact decimal numbers (`p` = total digits, `s` = digits after decimal) | `price DECIMAL(8,2)`        |
    |                      | `REAL`                          | 4-byte floating-point number                                           | `rating REAL`               |
    |                      | `DOUBLE PRECISION`              | 8-byte floating-point number                                           | `accuracy DOUBLE PRECISION` |
    | **Character/String** | `CHAR(n)`                       | Fixed-length string (pads with spaces)                                 | `gender CHAR(1)`            |
    |                      | `VARCHAR(n)`                    | Variable-length string (up to *n* characters)                          | `name VARCHAR(100)`         |
    |                      | `TEXT`                          | Long text/string                                                       | `bio TEXT`                  |
    | **Date & Time**      | `DATE`                          | Stores only the date (`YYYY-MM-DD`)                                    | `joining_date DATE`         |
    |                      | `TIMESTAMP`                     | Stores date and time                                                   | `created_at TIMESTAMP`      |
    |                      | `INTERVAL`*                     | Represents a duration or time interval                                 | `INTERVAL '5 days'`  
    |    BOOLEAN                                                True or False




### Example

    CREATE TABLE strings (
    Id INT PRIMARY KEY,
    code CHAR(5) not null,
    email VARCHAR(100),
    bio TEXT,
    age int check (age>=18)
    );
    
    INSERT INTO strings (Id, code, email, bio,age)
    VALUES
    (1, 'AD001', 'adilahmadshah897@gmail.com', 'Hello this is the world.',19);
    
    INSERT INTO strings (Id, code, email, bio,age)
    VALUES
    (2, 'AD002', 'adil@example.com', 'Learning SQL data types.',111);
    
    SELECT * FROM strings;








### Project 1 – Amazon Product Inventory
    Task
    
    Create a database named Amazon_DB and create a table Products with the following requirements:
    
    Product_ID – Auto Increment Primary Key
    Product_Name – String (maximum 100 characters)
    SKU_Code – String (exactly 8 characters)
    Price – Decimal number (maximum 999999.99)
    Stock_Quantity – Must be greater than or equal to 0
    Is_Available – Boolean (default TRUE)
    Category – String (cannot be NULL)
    Brand – String
    Added_On – Date
    Last_Updated – Timestamp



# Interview Questions

### What is DDL?

DDL (Data Definition Language) is used to define and modify the structure of database objects such as databases and tables.

---

### Which commands belong to DDL?

- CREATE
- ALTER
- DROP
- TRUNCATE
- RENAME

---

### What is the difference between DELETE, TRUNCATE, and DROP?

| DELETE | TRUNCATE | DROP |
|----------|------------|--------|
| Deletes selected rows | Deletes all rows | Deletes the table |
| WHERE allowed | WHERE not allowed | Removes table completely |
| Structure remains | Structure remains | Structure removed |

---

# Lab Exercise

1. Create a database named SchoolDB.

2. Create a table Student.

Fields

- StudentID
- Name
- Age
- Department



3. Remove Email.

4. Display the table structure.

5. Truncate the table.

6. Drop the table.

7. Drop the database.

---

## What is a Clause?

A clause is a part of an SQL statement that performs a specific task, such as selecting data, filtering records, grouping rows, or sorting results.

### 1. SELECT Clause
Purpose: Used to choose which column(s) to display.

Syntax

    SELECT column_name
    FROM table_name;
Example

    SELECT Product_Name, Price
    FROM Products;

### 2. FROM Clause
Purpose: Specifies the table from which data will be retrieved.
    
 Syntax

     SELECT *
    FROM table_name;
Example

    SELECT *
    FROM Products;

### 3. WHERE Clause
Purpose: Filters rows based on a condition.

Syntax

        SELECT column_name
        FROM table_name
        WHERE condition;
Example

        SELECT *
        FROM Products
        WHERE Category = 'Electronics';

### 4. GROUP BY Clause
Purpose: Groups rows that have the same values in a specified column.
It is commonly used with aggregate functions such as:

COUNT()
SUM()
AVG()
MIN()
MAX()

Syntax:

    SELECT column_name, COUNT(*)
    FROM table_name
    GROUP BY column_name;

Example:

    SELECT Category, COUNT(*)
    FROM Products
    GROUP BY Category;

### 5. HAVING Clause
Purpose: Filters grouped data after the GROUP BY clause.

Syntax:

        SELECT column_name, COUNT(*)
        FROM table_name
        GROUP BY column_name
        HAVING COUNT(*) > 1;
Example:

        SELECT Category, COUNT(*)
        FROM Products
        GROUP BY Category
        HAVING COUNT(*) > 1;

### 6. ORDER BY Clause
Purpose: Sorts the result in ascending or descending order.

Syntax
Ascending Order (Default)

        SELECT *
        FROM table_name
        ORDER BY column_name;
Descending Order

        SELECT *
        FROM table_name
        ORDER BY column_name DESC;

Example:

        SELECT *
        FROM Products
        ORDER BY Price ASC;

### 7. LIMIT Clause
Purpose: Limits the number of rows returned.

Syntax

        SELECT *
        FROM table_name
        LIMIT number;

Example

         SELECT *
         FROM Products
         LIMIT 3;

### 8. AS Clause (Alias)
Purpose: Gives a temporary name to a column or table.

Syntax

    SELECT column_name AS alias_name
    FROM table_name;
Example

     SELECT Product_Name AS Item_Name,
    Price AS Item_Price
    FROM Products;

### 9. DISTINCT Clause
Purpose: Returns only unique values from a column.

Syntax    

        SELECT DISTINCT column_name
        FROM table_name;

Example

        SELECT DISTINCT Category
        FROM Products;


### 10.  SQL `LIKE` Operator

The `LIKE` operator is used in SQL to search for a specified pattern in a column. It is commonly used with the `WHERE` clause to filter records based on text patterns.

## Syntax

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern;
```

## Wildcards

| Wildcard | Description |
|----------|-------------|
| `%` | Matches **zero or more characters** |
| `_` | Matches **exactly one character** |

---

## Examples

### 1. Starts With

```sql
SELECT * FROM Products
WHERE Name LIKE 'A%';
```

**Result:** Returns all products whose name starts with **A**.

Examples:
- Apple
- Acer Laptop
- AirPods

---

### 2. Ends With

```sql
SELECT * FROM Products
WHERE Name LIKE '%w';
```

**Result:** Returns all products whose name ends with **w**.

Examples:
- Saw
- Screw
- Window

---

### 3. Contains

```sql
SELECT * FROM Products
WHERE Name LIKE '%phone%';
```

**Result:** Returns all products whose name contains **phone**.

Examples:
- Smartphone
- Headphone
- iPhone

---

### 4. Exactly One Character (`_`)

```sql
SELECT * FROM Products
WHERE Name LIKE '_at';
```

**Result:** Returns names with exactly three letters ending in **at**.

Examples:
- Cat
- Bat
- Hat

---

### 5. Second Character is 'a'

```sql
SELECT * FROM Products
WHERE Name LIKE '_a%';
```

Examples:
- Samsung
- Camera
- Table

---

### 6. Exactly Five Characters

```sql
SELECT * FROM Products
WHERE Name LIKE '_____';
```

**Result:** Returns names containing exactly **5 characters**.

Examples:
- Apple
- Mouse

---

## Wildcard Summary

| Pattern | Meaning |
|---------|---------|
| `'A%'` | Starts with **A** |
| `'%A'` | Ends with **A** |
| `'%A%'` | Contains **A** anywhere |
| `'A_B%'` | Starts with **A**, third character is **B** |
| `'_____'` | Exactly **5 characters** |
| `'_a%'` | Second character is **a** |

---

## Key Points

- `LIKE` is used for **pattern matching**.
- `%` matches **zero or more characters**.
- `_` matches **exactly one character**.
- `LIKE` is commonly used with the `WHERE` clause.
- It is mainly used with text-based columns (`CHAR`, `VARCHAR`, `TEXT`, etc.).

## Example

```sql
SELECT Product_Name
FROM Products
WHERE Product_Name LIKE '%Book%';
```

This query returns all products whose name contains the word **"Book"**.


### SQL Clauses Practice Questions

    Assume the table name is Products.
    | Column Name    | Data Type    | Constraints                         |
    | -------------- | ------------ | ----------------------------------- |
    | Student_ID     | INT          | Primary Key, Auto Increment         |
    | Student_Name   | VARCHAR(100) | NOT NULL                            |
    | Roll_No        | CHAR(8)      | UNIQUE                              |
    | Age            | INT          | Must be greater than or equal to 18 |
    | Gender         | VARCHAR(10)  | NOT NULL                            |
    | Course         | VARCHAR(50)  | NOT NULL                            |
    | Department     | VARCHAR(50)  | NOT NULL                            |
    | CGPA           | DECIMAL(3,2) | Default 0.00                        |
    | Admission_Date | DATE         | NOT NULL                            |


Q1.

Show the Product_Name and Price of all products.

Q2.

Show all products where the Category is 'Electronics'.

Q3.

Group products by Category and display the total number of products in each category.

Q4.

Show only those categories that have more than one product.

(Hint: Use GROUP BY with HAVING.)

Q5.

Display all products sorted by Price in ascending order.

Q6.

Display only the first three products from the table.

Q7.

Display Product_Name as Item_Name and Price as Item_Price.

Q8.

Display all unique categories from the Products table.


##  SQL String Functions

String functions are built-in SQL functions used to manipulate and analyze text data.

---

## 1. `UPPER()`

Converts all characters in a string to **uppercase**.

### Syntax

```sql
UPPER(column_name)
```

### Example

```sql
SELECT UPPER(Product_Name)
FROM Products;
```

**Output**

| Product_Name |
|--------------|
| LAPTOP |
| MOUSE |
| KEYBOARD |

---

## 2. `LOWER()`

Converts all characters in a string to **lowercase**.

### Syntax

```sql
LOWER(column_name)
```

### Example

```sql
SELECT LOWER(Product_Name)
FROM Products;
```

**Output**

| Product_Name |
|--------------|
| laptop |
| mouse |
| keyboard |

---

## 3. `LENGTH()`

Returns the **number of characters** in a string.

### Syntax

```sql
LENGTH(column_name)
```

### Example

```sql
SELECT Product_Name, LENGTH(Product_Name) AS Length
FROM Products;
```

**Output**

| Product_Name | Length |
|--------------|--------|
| Laptop | 6 |
| Mouse | 5 |
| Keyboard | 8 |

---




## 4. `SUBSTRING()`

Extracts a specified part of a string.

### Syntax

```sql
SUBSTRING(column_name, start_position, length)
```

- `start_position` → Starting position (starts from **1**).
- `length` → Number of characters to extract.

### Example

```sql
SELECT SUBSTRING(Product_Name, 1, 4)
FROM Products;
```

**Output**

    | Product_Name |
    |--------------|
    | Lapt |
    | Mous |
    | Keyb |


## Summary

| Function | Description | Example |
|----------|-------------|---------|
| `UPPER()` | Converts text to uppercase | `UPPER('sql')` → `SQL` |
| `LOWER()` | Converts text to lowercase | `LOWER('SQL')` → `sql` |
| `LENGTH()` | Returns the number of characters | `LENGTH('Laptop')` → `6` |


## SQL `CASE` Statement

The `CASE` statement is used to apply **conditional logic** in SQL. It works like an **IF...ELSE** statement and returns a value based on the first condition that is true.

---

## Syntax

```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    ...
    ELSE result
END
```

---

## Example 1: Product Availability

```sql
SELECT Product_Name,
       Stock_Quantity,
       CASE
           WHEN Stock_Quantity = 0 THEN 'Out of Stock'
           WHEN Stock_Quantity <= 10 THEN 'Low Stock'
           ELSE 'In Stock'
       END AS Stock_Status
FROM Products;
```

**Output**

| Product_Name | Stock_Quantity | Stock_Status |
|--------------|---------------:|--------------|
| Laptop | 25 | In Stock |
| Mouse | 8 | Low Stock |
| Keyboard | 0 | Out of Stock |

---

## Example 2: Grade Classification

```sql
SELECT Student_Name,
       Marks,
       CASE
           WHEN Marks >= 90 THEN 'A'
           WHEN Marks >= 75 THEN 'B'
           WHEN Marks >= 60 THEN 'C'
           ELSE 'Fail'
       END AS Grade
FROM Students;
```

---

## Example 3: Price Category

```sql
SELECT Product_Name,
       Price,
       CASE
           WHEN Price >= 50000 THEN 'Expensive'
           WHEN Price >= 10000 THEN 'Moderate'
           ELSE 'Budget'
       END AS Price_Category
FROM Products;
```

---

## Key Points

- `CASE` is used to implement **conditional logic** in SQL.
- Conditions are checked **from top to bottom**.
- The **first matching condition** is returned.
- `ELSE` is optional. If omitted and no condition matches, `NULL` is returned.
- `CASE` can be used with `SELECT`, `WHERE`, `ORDER BY`, `GROUP BY`, and `HAVING`.

---

## Summary

| Keyword | Description |
|---------|-------------|
| `CASE` | Starts the conditional expression |
| `WHEN` | Specifies a condition |
| `THEN` | Value returned if the condition is true |
| `ELSE` | Default value if no conditions match |
| `END` | Ends the `CASE` expression |







# SQL Joins - Complete Guide 🚀


---

## What is a JOIN?

A **JOIN** is used to combine rows from **two or more tables** based on a related column.

Think of it like connecting two Excel sheets using a common column.

Example:

Students Table

    | student_id | name |
    |------------|------|
    | 1 | ankit |
    | 2 | Rahul |
    | 3 | Priya |

Marks Table
    
    | student_id | marks |
    |------------|-------|
    | 1 | 90 |
    | 3 | 85 |

Using JOIN we can get

    | name | marks |
    |------|------|
    | ankit | 90 |
    | Priya | 85 |

---

# Why Do We Need JOIN?

Imagine an E-commerce database.

Customers

    | customer_id | name |
    |-------------|------|
    |1|ankit|
    |2|Rahul|

Orders

    | order_id | customer_id | amount |
    |-----------|-------------|--------|
    |101|1|500|
    |102|2|800|

Instead of storing customer name repeatedly, we store customer_id.

JOIN combines them whenever required.

---

# Types of SQL JOIN

```
                 JOINS
                    |
   --------------------------------
   |        |        |            |
 INNER    LEFT     RIGHT       FULL
                    |
              SELF JOIN
                    |
             CROSS JOIN
```

---

# Sample Database

We'll use these tables throughout.

## Students

    | student_id | name | city_id |
    |------------|------|---------|
    |1           |ankit  |1|
    |2           |Rahul  |2|
    |3           |Aman   |3|
    |4           |Priya  |2|
    |5           |Riya   |NULL|

---

## Cities

        | city_id | city |
        |---------|------|
        |1        |Ahmedabad|
        |2        |Delhi|
        |3        |Mumbai|
        |4        |Pune|

---

# 1. INNER JOIN

## Definition

Returns only matching records from both tables.

        Students
             |
        INNER JOIN
             |
        Cities
        
        Only Matching Rows
        ```


### Syntax
        
        ```sql
        SELECT *
        FROM Students
        INNER JOIN Cities
        ON Students.city_id = Cities.city_id;
        ```

---

### Result

    | student_id | name | city |
    |------------|------|------|
    |1           |ankit |Ahmedabad|
    |2           |Rahul |Delhi|
    |3           |Aman  |Mumbai|
    |4           |Priya |Delhi|

Notice:

Riya is not returned because city_id is NULL.

---


> INNER JOIN returns only those rows that have matching values in both tables.

---



# 2. LEFT JOIN

## Definition

    Returns
    
    - All rows from LEFT table
    - Matching rows from RIGHT table
    
    If no match exists
    
    → NULL is returned.
    
    ---

### Syntax

    ```sql
    SELECT *
    FROM Students
    LEFT JOIN Cities
    ON Students.city_id = Cities.city_id;
    ```

---

### Output

    | name | city |
    |------|------|
    |Adil  |Ahmedabad|
    |Rahul |Delhi|
    |Aman  |Mumbai|
    |Priya |Delhi|
    |Riya  |NULL|

Even though Riya has no city,
she is still shown.

---



# 3. RIGHT JOIN

##Definition

    Opposite of LEFT JOIN.
    Returns
    - All rows from RIGHT table
    - Matching rows from LEFT table



### Syntax
    
    sql
    SELECT *
    FROM Students
    RIGHT JOIN Cities
    ON Students.city_id = Cities.city_id;


---

### Output

| city     | student |
|------    |----------|
|Ahmedabad |Adil|
|Delhi     |Rahul|
|Delhi     |Priya|
|Mumbai    |Aman|
|Pune      |NULL|

Notice

Pune has no students.

Still appears.

---



# 4. FULL OUTER JOIN

Definiton

    Returns
    - All rows from LEFT
    - All rows from RIGHT
    Matched where possible.
    Otherwise NULL.

### Syntax

        sql
        SELECT *
        FROM Students
        FULL OUTER JOIN Cities
        ON Students.city_id = Cities.city_id;


---

### Output

    | student | city    |    
    |---------|---------|
    |Adil     |Ahmedabad|
    |Rahul    |Delhi|
    |Priya    |Delhi|
    |Aman     |Mumbai|
    |Riya     |NULL|
    |NULL     |Pune|
    
    ---




# 5. CROSS JOIN

### Definition

    Every row joins with every row.
Formula
    
    ```
    Rows = Table1 × Table2
    ```

Example

Students = 5

Cities = 4

Output

```
5 × 4 = 20 rows
```

---

### Syntax

    ```sql
    SELECT *
    FROM Students
    CROSS JOIN Cities;
    ```

---

### Output

```
Adil Ahmedabad
Adil Delhi
Adil Mumbai
Adil Pune

Rahul Ahmedabad
Rahul Delhi

...
```

# 6. SELF JOIN

## Definition 

    A table joins with itself.
    Useful when employees have managers.

---

Employee Table

    |id|name|manager_id|
    |--|----|----------|
    |1 |CEO        |NULL|
    |2 |Manager    |1|
    |3|Developer   |2|

---

### Query
    
    sql
    SELECT
    E.name AS Employee,
    M.name AS Manager
    FROM Employee E
    JOIN Employee M
    ON E.manager_id = M.id;
    

---

Output

    |Employee|Manager|
    |----------|--------|
    |Manager|CEO|
    |Developer|Manager|

---

# JOIN vs UNION

    |    JOIN        |    UNION    |
    |----------------|-------------|
    |Combines columns|Combines rows|
    |Uses ON         |No ON|
    |Horizontal Merge|Vertical Merge|

---

# ON vs WHERE


Wrong understanding

```
ON = WHERE
```

❌ False

---

ON

Used for matching tables.
    
    sql
    JOIN Orders
    ON customer.id = orders.customer_id
    

WHERE

    Filters result.
    
    sql
    WHERE amount > 500
    

---

# Execution Order

```
FROM

↓

JOIN

↓

ON

↓

WHERE

↓

GROUP BY

↓

HAVING

↓

SELECT

↓

ORDER BY

↓

LIMIT
```

---


# Practice Questions

## Easy

1. Display student name and city.
2. Show all students even if city is missing.
3. Show all cities even if no students.
4. Count students in every city.
5. Show students without city.

---

## Medium

6. List all orders with customer names.
7. Show customers who never placed orders.
8. Find products never ordered.
9. Find highest order per customer.
10. Display employee-manager relationship.

---

## Hard

11. Second highest salary department-wise.
12. Customers who ordered every product.
13. Employees earning more than manager.
14. Consecutive login analysis.
15. Find duplicate customers using SELF JOIN.

---

# JOIN Summary Table

| JOIN         |         Returns |
|--------------|-----------------|
| INNER JOIN | Matching rows only|
| LEFT JOIN | All left + matching right |
| RIGHT JOIN | All right + matching left |
| FULL OUTER JOIN | All rows from both tables |
| CROSS JOIN | Cartesian Product |
| SELF JOIN | Table joined with itself |

---

# Memory Trick

```
INNER
Intersection

LEFT
Everything Left

RIGHT
Everything Right

FULL
Everything

CROSS
Everything × Everything

SELF
Same Table
```

---


# SQL Set Operations - Complete Guide

> A complete guide to SQL Set Operations with syntax, examples, interview questions, and LeetCode practice.

---

# Table of Contents

1. Introduction
2. Types of Set Operations
3. UNION
4. UNION ALL
5. INTERSECT
6. EXCEPT / MINUS
7. Comparison Table
8. Rules
9. Examples
10. Interview Questions
11. Common Mistakes
12. LeetCode Problems

---

# What are Set Operations?

Set operations are used to combine the result of **two or more SELECT statements**.

Think of them like mathematical sets.

Example:

Set A
```
1
2
3
```

Set B
```
3
4
5
```

Different operations produce different results.

---

# SQL Set Operations

| Operation | Removes Duplicates | Purpose |
|------------|-------------------|----------|
| UNION | ✅ Yes | Combine unique rows |
| UNION ALL | ❌ No | Combine all rows |
| INTERSECT | ✅ Yes | Common rows |
| EXCEPT (MINUS) | ✅ Yes | Rows in first query but not second |

---

# Sample Tables

## Employees_India

| id | name |
|----|------|
|1|Adil|
|2|Rahul|
|3|Aman|

---

## Employees_USA

| id | name |
|----|------|
|3|Aman|
|4|John|
|5|Alex|

---

# 1. UNION

Returns all unique rows from both queries.

Syntax

```sql
SELECT column_list
FROM table1

UNION

SELECT column_list
FROM table2;
```

Example

```sql
SELECT name
FROM Employees_India

UNION

SELECT name
FROM Employees_USA;
```

Output

| name |
|------|
|Adil|
|Rahul|
|Aman|
|John|
|Alex|

Notice

Aman appears only once.

Because UNION removes duplicates.

---

# Visualization

Table A

```
Adil
Rahul
Aman
```

Table B

```
Aman
John
Alex
```

UNION

```
Adil
Rahul
Aman
John
Alex
```

---

# 2. UNION ALL

Returns every row.

Duplicates are NOT removed.

Syntax

```sql
SELECT column_list
FROM table1

UNION ALL

SELECT column_list
FROM table2;
```

Example

```sql
SELECT name
FROM Employees_India

UNION ALL

SELECT name
FROM Employees_USA;
```

Output

| name |
|------|
|Adil|
|Rahul|
|Aman|
|Aman|
|John|
|Alex|

Notice

Aman appears twice.

---

# Visualization

```
Adil
Rahul
Aman
Aman
John
Alex
```

---

# UNION vs UNION ALL

| Feature | UNION | UNION ALL |
|----------|--------|-----------|
|Duplicates Removed|✅|❌|
|Sorting Required|Yes|No|
|Performance|Slower|Faster|
|Interview Favorite|Yes|Yes|

---

# Why UNION ALL is Faster?

UNION

Step 1

```
Combine rows
```

↓

Step 2

```
Find duplicates
```

↓

Step 3

```
Remove duplicates
```

Extra work.

---

UNION ALL

Step 1

```
Combine rows
```

Done.

No duplicate checking.

---

# 3. INTERSECT

Returns only common rows.

Syntax

```sql
SELECT column_list
FROM table1

INTERSECT

SELECT column_list
FROM table2;
```

Example

```sql
SELECT name
FROM Employees_India

INTERSECT

SELECT name
FROM Employees_USA;
```

Output

| name |
|------|
|Aman|

Because Aman exists in both tables.

---

Visualization

Table A

```
Adil
Rahul
Aman
```

Table B

```
Aman
John
Alex
```

Result

```
Aman
```

---

# 4. EXCEPT

Returns rows that exist in first query but NOT in second.

Syntax

```sql
SELECT column_list
FROM table1

EXCEPT

SELECT column_list
FROM table2;
```

Example

```sql
SELECT name
FROM Employees_India

EXCEPT

SELECT name
FROM Employees_USA;
```

Output

| name |
|------|
|Adil|
|Rahul|

Because Aman exists in both.

Only remaining rows stay.

---

Visualization

Table A

```
Adil
Rahul
Aman
```

Table B

```
Aman
John
Alex
```

Result

```
Adil
Rahul
```

---

# MINUS

Oracle uses

```sql
MINUS
```

instead of

```sql
EXCEPT
```

Same behavior.

---

# Rules of Set Operations

## Rule 1

Both SELECT statements must return the same number of columns.

Correct

```sql
SELECT id,name
FROM student

UNION

SELECT id,name
FROM teacher;
```

Wrong

```sql
SELECT id,name
FROM student

UNION

SELECT id
FROM teacher;
```

---

## Rule 2

Corresponding columns must have compatible data types.

Correct

```sql
INT
INT
```

Correct

```sql
VARCHAR
VARCHAR
```

Wrong

```sql
INT
DATE
```

---

## Rule 3

Column names come from the first SELECT.

Example

```sql
SELECT name
FROM student

UNION

SELECT employee_name
FROM employee;
```

Output column

```
name
```

---

## Rule 4

ORDER BY comes only once.

Correct

```sql
SELECT name
FROM student

UNION

SELECT name
FROM employee

ORDER BY name;
```

Wrong

```sql
SELECT name
FROM student
ORDER BY name

UNION

SELECT name
FROM employee;
```

---

# Multiple UNION

```sql
SELECT city
FROM student

UNION

SELECT city
FROM teacher

UNION

SELECT city
FROM employee;
```

Works perfectly.

---

# Practical Example

Students

|name|
|----|
|Adil|
|Rahul|

Teachers

|name|
|----|
|Aman|
|Rahul|

Guests

|name|
|----|
|John|

Get everyone

```sql
SELECT name FROM Students

UNION

SELECT name FROM Teachers

UNION

SELECT name FROM Guests;
```

Output

```
Adil
Rahul
Aman
John
```

---

# When to Use Each

## UNION

Need unique values

Example

Unique cities

---

## UNION ALL

Need all records

Example

Sales history

Log tables

Transactions

---

## INTERSECT

Need common customers

Common students

Common employees

---

## EXCEPT

Need missing records

Customers who never ordered

Students not enrolled

---

# Interview Questions

## Q1

Difference between UNION and UNION ALL?

Answer

UNION removes duplicates.

UNION ALL keeps duplicates.

---

## Q2

Which is faster?

Answer

UNION ALL.

---

## Q3

Can UNION combine different number of columns?

Answer

No.

---

## Q4

Can UNION combine INT and VARCHAR?

Answer

Generally no, unless the database can implicitly convert them to a compatible type. It's best to use matching data types.

---

## Q5

Which operation finds common records?

Answer

INTERSECT.

---

## Q6

Which operation finds missing records?

Answer

EXCEPT.

---

# Common Mistakes

## Mistake 1

Different column count

Wrong

```sql
SELECT id,name
FROM A

UNION

SELECT id
FROM B;
```

---

## Mistake 2

ORDER BY in both queries

Wrong

```sql
SELECT name
FROM A
ORDER BY name

UNION

SELECT name
FROM B;
```

---

## Mistake 3

Expecting UNION ALL to remove duplicates

It never removes duplicates.

---

# Real Interview Scenario

Table A

```
Apple
Banana
Orange
```

Table B

```
Banana
Mango
Orange
```

UNION

```
Apple
Banana
Orange
Mango
```

UNION ALL

```
Apple
Banana
Orange
Banana
Mango
Orange
```

INTERSECT

```
Banana
Orange
```

EXCEPT

```
Apple
```

---

# SQL Server vs PostgreSQL vs MySQL

| Database | UNION | UNION ALL | INTERSECT | EXCEPT |
|------------|--------|-----------|-----------|---------|
| MySQL 8.x | ✅ | ✅ | ❌ Not Supported | ❌ Not Supported |
| PostgreSQL | ✅ | ✅ | ✅ | ✅ |
| SQL Server | ✅ | ✅ | ✅ | ✅ |
| Oracle | ✅ | ✅ | ✅ | MINUS |

> **Note:** MySQL 8.x supports `UNION` and `UNION ALL` but does not support `INTERSECT` or `EXCEPT`. Similar results can be achieved using `JOIN`, `IN`, `EXISTS`, or `NOT EXISTS`.

---

# LeetCode SQL Practice

Easy

- 175 - Combine Two Tables
- 176 - Second Highest Salary
- 181 - Employees Earning More Than Their Managers
- 183 - Customers Who Never Order
- 196 - Delete Duplicate Emails

Medium

- 177 - Nth Highest Salary
- 184 - Department Highest Salary
- 185 - Department Top Three Salaries
- 570 - Managers with at Least 5 Direct Reports
- 1045 - Customers Who Bought All Products

---

# Cheat Sheet

| Operation | Duplicate Removed | Returns |
|------------|------------------|----------|
| UNION | ✅ | All unique rows |
| UNION ALL | ❌ | All rows |
| INTERSECT | ✅ | Common rows |
| EXCEPT | ✅ | First query minus second |

---

# Memory Trick

```
UNION
=
Combine Everything
(Removes duplicates)

UNION ALL
=
Everything
(Keep duplicates)

INTERSECT
=
Common

EXCEPT
=
Difference
```

---

# SQL Subqueries - Complete Guide

> A complete guide to SQL Subqueries with syntax, types, examples, interview questions, optimization tips, and LeetCode practice.

---

# Table of Contents

1. What is a Subquery?
2. Types of Subqueries
3. Single Row Subquery
4. Multiple Row Subquery
5. Multiple Column Subquery
6. Correlated Subquery
7. Nested Subquery
8. EXISTS
9. NOT EXISTS
10. ANY
11. ALL
12. IN vs EXISTS
13. Correlated vs Non-Correlated
14. Common Mistakes
15. Optimization Tips
16. Interview Questions
17. LeetCode Problems
18. Cheat Sheet

---

# What is a Subquery?

A **subquery** is a query written **inside another SQL query**.

The inner query executes first, and its result is used by the outer query.

Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator
(
    SELECT column_name
    FROM another_table
);
```

---

# Sample Tables

## Employees

| id | name | salary | dept_id |
|----|------|--------|---------|
|1|Adil|60000|1|
|2|Rahul|50000|2|
|3|Aman|70000|1|
|4|John|40000|3|
|5|Alex|80000|2|

---

## Departments

| dept_id | department |
|----------|------------|
|1|IT|
|2|HR|
|3|Sales|

---

# Types of Subqueries

| Type | Returns |
|------|----------|
| Single Row | One value |
| Multiple Row | Multiple values |
| Multiple Column | Multiple columns |
| Correlated | Executes once per outer row |
| Nested | Subquery inside another subquery |

---

# 1. Single Row Subquery

Returns exactly one row.

Example

Find employees earning more than the average salary.

```sql
SELECT *
FROM Employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
);
```

Average salary

```
60000
```

Output

|name|salary|
|----|------|
|Aman|70000|
|Alex|80000|

---

Another Example

Employee with highest salary

```sql
SELECT *
FROM Employees
WHERE salary =
(
    SELECT MAX(salary)
    FROM Employees
);
```

Output

```
Alex
```

---

# 2. Multiple Row Subquery

Returns multiple rows.

Use

- IN
- ANY
- ALL

Example

Employees in IT or HR.

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
    WHERE department IN ('IT','HR')
);
```

Output

```
Adil
Rahul
Aman
Alex
```

---

# Why "=" Doesn't Work

Wrong

```sql
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
)
```

Error

```
Subquery returns more than one row
```

Correct

```sql
WHERE dept_id IN (...)
```

---

# 3. Multiple Column Subquery

Returns multiple columns.

Example

```sql
SELECT *
FROM Employees
WHERE (dept_id, salary) IN
(
    SELECT dept_id,
           MAX(salary)
    FROM Employees
    GROUP BY dept_id
);
```

Returns the highest-paid employee in each department.

---

# 4. Correlated Subquery

A correlated subquery depends on the outer query.

It executes once for **every row** of the outer query.

Example

Employees earning more than their department average.

```sql
SELECT *
FROM Employees e
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
    WHERE dept_id = e.dept_id
);
```

Execution

Outer Row

```
Adil
```

↓

Inner Query

```
Average IT Salary
```

↓

Check condition

↓

Next Employee

Repeat.

---

# Correlated Query Visualization

```
Outer Query
     |
     v
Employee Row
     |
     v
Run Inner Query
     |
     v
Compare
     |
     v
Return/Skip
```

---

# 5. Nested Subquery

Subquery inside another subquery.

Example

```sql
SELECT *
FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE department =
    (
        SELECT 'IT'
    )
);
```

---

# Subquery in SELECT

Example

```sql
SELECT
name,
salary,
(
    SELECT AVG(salary)
    FROM Employees
) AS average_salary
FROM Employees;
```

Output

|Employee|Salary|Average|
|---------|------|-------|
|Adil|60000|60000|
|Rahul|50000|60000|

---

# Subquery in FROM

Example

```sql
SELECT *
FROM
(
    SELECT dept_id,
           AVG(salary) avg_salary
    FROM Employees
    GROUP BY dept_id
) AS dept_avg;
```

---

# EXISTS

Returns TRUE if at least one row exists.

Example

Departments having employees.

```sql
SELECT *
FROM Departments d
WHERE EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# NOT EXISTS

Returns rows with no matching records.

Example

Departments without employees.

```sql
SELECT *
FROM Departments d
WHERE NOT EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# EXISTS vs IN

Example

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
);
```

Same using EXISTS

```sql
SELECT *
FROM Employees e
WHERE EXISTS
(
    SELECT 1
    FROM Departments d
    WHERE d.dept_id = e.dept_id
);
```

---

# ANY

Condition is TRUE if **at least one** value satisfies it.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ANY
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than at least one salary.
```

---

# ALL

Condition is TRUE if it satisfies **every** value.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ALL
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than every salary.
```

---

# ANY vs ALL

Suppose subquery returns

```
30000
50000
70000
```

Condition

```sql
salary > ANY (...)
```

Means

```
salary > 30000
OR
salary > 50000
OR
salary > 70000
```

Condition

```sql
salary > ALL (...)
```

Means

```
salary > 30000
AND
salary > 50000
AND
salary > 70000
```

---

# IN vs EXISTS

| Feature | IN | EXISTS |
|----------|----|---------|
|Compares values|✅|❌|
|Checks existence|❌|✅|
|Large tables|Slower|Usually Faster|
|Stops early|❌|✅|

---

# Correlated vs Non-Correlated

| Feature | Correlated | Non-Correlated |
|----------|------------|----------------|
|Depends on outer query|✅|❌|
|Runs once|❌|✅|
|Runs per row|✅|❌|
|Performance|Usually Slower|Usually Faster|

---

# Common Mistakes

## Using = instead of IN

Wrong

```sql
WHERE dept_id =
(
SELECT dept_id
FROM Departments
)
```

Correct

```sql
WHERE dept_id IN (...)
```

---

## Forgetting Alias in Correlated Query

Wrong

```sql
WHERE dept_id = dept_id
```

Correct

```sql
WHERE e.dept_id = d.dept_id
```

---

## Returning Multiple Columns

Wrong

```sql
SELECT salary,name
```

when a single value is expected.

---

# Optimization Tips

✅ Prefer `EXISTS` for checking matching rows in large tables.

✅ Use `JOIN` instead of a subquery when possible for better readability and performance.

✅ Index columns used in subquery conditions.

✅ Avoid correlated subqueries on large datasets if an equivalent `JOIN` or window function is available.

---

# Interview Questions

### Q1

What is a subquery?

**Answer**

A query inside another query.

---

### Q2

What is a correlated subquery?

A subquery that references columns from the outer query.

---

### Q3

Which runs faster?

Usually

```
JOIN
```

or

```
EXISTS
```

depending on the database and execution plan.

---

### Q4

Difference between EXISTS and IN?

`EXISTS` checks whether matching rows exist.

`IN` compares values against a list.

---

### Q5

Can a subquery be inside SELECT?

Yes.

---

### Q6

Can a subquery be inside FROM?

Yes.

---

### Q7

Can a subquery return multiple rows?

Yes, when used with operators like `IN`, `ANY`, or `ALL`.

---

# LeetCode SQL Problems

## Easy

- 175 - Combine Two Tables
- 176 - Second Highest Salary
- 177 - Nth Highest Salary
- 181 - Employees Earning More Than Their Managers
- 183 - Customers Who Never Order

## Medium

- 184 - Department Highest Salary
- 185 - Department Top Three Salaries
- 570 - Managers with at Least 5 Direct Reports
- 1045 - Customers Who Bought All Products
- 1978 - Employees Whose Manager Left the Company

---

# Cheat Sheet

| Operator | Purpose |
|-----------|---------|
| = | One value |
| IN | Multiple values |
| EXISTS | Matching rows exist |
| NOT EXISTS | No matching rows |
| ANY | At least one value |
| ALL | Every value |

---

# Memory Trick

```
Subquery
=
Query inside Query

IN
=
Many values

EXISTS
=
Does it exist?

ANY
=
One match

ALL
=
Every match

Correlated
=
Runs for every row
```

---
# SQL Subqueries - Complete Guide

> A complete guide to SQL Subqueries with syntax, types, examples, interview questions, optimization tips, and LeetCode practice.

---

# Table of Contents

1. What is a Subquery?
2. Types of Subqueries
3. Single Row Subquery
4. Multiple Row Subquery
5. Multiple Column Subquery
6. Correlated Subquery
7. Nested Subquery
8. EXISTS
9. NOT EXISTS
10. ANY
11. ALL
12. IN vs EXISTS
13. Correlated vs Non-Correlated
14. Common Mistakes
15. Optimization Tips
16. Interview Questions
17. LeetCode Problems
18. Cheat Sheet

---

# What is a Subquery?

A **subquery** is a query written **inside another SQL query**.

The inner query executes first, and its result is used by the outer query.

Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator
(
    SELECT column_name
    FROM another_table
);
```

---

# Sample Tables

## Employees

| id | name | salary | dept_id |
|----|------|--------|---------|
|1|Adil|60000|1|
|2|Rahul|50000|2|
|3|Aman|70000|1|
|4|John|40000|3|
|5|Alex|80000|2|

---

## Departments

| dept_id | department |
|----------|------------|
|1|IT|
|2|HR|
|3|Sales|

---

# Types of Subqueries

| Type | Returns |
|------|----------|
| Single Row | One value |
| Multiple Row | Multiple values |
| Multiple Column | Multiple columns |
| Correlated | Executes once per outer row |
| Nested | Subquery inside another subquery |

---

# 1. Single Row Subquery

Returns exactly one row.

Example

Find employees earning more than the average salary.

```sql
SELECT *
FROM Employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
);
```

Average salary

```
60000
```

Output

|name|salary|
|----|------|
|Aman|70000|
|Alex|80000|

---

Another Example

Employee with highest salary

```sql
SELECT *
FROM Employees
WHERE salary =
(
    SELECT MAX(salary)
    FROM Employees
);
```

Output

```
Alex
```

---

# 2. Multiple Row Subquery

Returns multiple rows.

Use

- IN
- ANY
- ALL

Example

Employees in IT or HR.

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
    WHERE department IN ('IT','HR')
);
```

Output

```
Adil
Rahul
Aman
Alex
```

---

# Why "=" Doesn't Work

Wrong

```sql
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
)
```

Error

```
Subquery returns more than one row
```

Correct

```sql
WHERE dept_id IN (...)
```

---

# 3. Multiple Column Subquery

Returns multiple columns.

Example

```sql
SELECT *
FROM Employees
WHERE (dept_id, salary) IN
(
    SELECT dept_id,
           MAX(salary)
    FROM Employees
    GROUP BY dept_id
);
```

Returns the highest-paid employee in each department.

---

# 4. Correlated Subquery

A correlated subquery depends on the outer query.

It executes once for **every row** of the outer query.

Example

Employees earning more than their department average.

```sql
SELECT *
FROM Employees e
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
    WHERE dept_id = e.dept_id
);
```

Execution

Outer Row

```
Adil
```

↓

Inner Query

```
Average IT Salary
```

↓

Check condition

↓

Next Employee

Repeat.

---

# Correlated Query Visualization

```
Outer Query
     |
     v
Employee Row
     |
     v
Run Inner Query
     |
     v
Compare
     |
     v
Return/Skip
```

---

# 5. Nested Subquery

Subquery inside another subquery.

Example

```sql
SELECT *
FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE department =
    (
        SELECT 'IT'
    )
);
```

---

# Subquery in SELECT

Example

```sql
SELECT
name,
salary,
(
    SELECT AVG(salary)
    FROM Employees
) AS average_salary
FROM Employees;
```

Output

|Employee|Salary|Average|
|---------|------|-------|
|Adil|60000|60000|
|Rahul|50000|60000|

---

# Subquery in FROM

Example

```sql
SELECT *
FROM
(
    SELECT dept_id,
           AVG(salary) avg_salary
    FROM Employees
    GROUP BY dept_id
) AS dept_avg;
```

---

# EXISTS

Returns TRUE if at least one row exists.

Example

Departments having employees.

```sql
SELECT *
FROM Departments d
WHERE EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# NOT EXISTS

Returns rows with no matching records.

Example

Departments without employees.

```sql
SELECT *
FROM Departments d
WHERE NOT EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# EXISTS vs IN

Example

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
);
```

Same using EXISTS

```sql
SELECT *
FROM Employees e
WHERE EXISTS
(
    SELECT 1
    FROM Departments d
    WHERE d.dept_id = e.dept_id
);
```

---

# ANY

Condition is TRUE if **at least one** value satisfies it.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ANY
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than at least one salary.
```

---

# ALL

Condition is TRUE if it satisfies **every** value.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ALL
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than every salary.
```

---

# ANY vs ALL

Suppose subquery returns

```
30000
50000
70000
```

Condition

```sql
salary > ANY (...)
```

Means

```
salary > 30000
OR
salary > 50000
OR
salary > 70000
```

Condition

```sql
salary > ALL (...)
```

Means

```
salary > 30000
AND
salary > 50000
AND
salary > 70000
```

---

# IN vs EXISTS

| Feature | IN | EXISTS |
|----------|----|---------|
|Compares values|✅|❌|
|Checks existence|❌|✅|
|Large tables|Slower|Usually Faster|
|Stops early|❌|✅|

---

# Correlated vs Non-Correlated

| Feature | Correlated | Non-Correlated |
|----------|------------|----------------|
|Depends on outer query|✅|❌|
|Runs once|❌|✅|
|Runs per row|✅|❌|
|Performance|Usually Slower|Usually Faster|

---

# Common Mistakes

## Using = instead of IN

Wrong

```sql
WHERE dept_id =
(
SELECT dept_id
FROM Departments
)
```

Correct

```sql
WHERE dept_id IN (...)
```

---

## Forgetting Alias in Correlated Query

Wrong

```sql
WHERE dept_id = dept_id
```

Correct

```sql
WHERE e.dept_id = d.dept_id
```

---

## Returning Multiple Columns

Wrong

```sql
SELECT salary,name
```

when a single value is expected.

---

# Optimization Tips

✅ Prefer `EXISTS` for checking matching rows in large tables.

✅ Use `JOIN` instead of a subquery when possible for better readability and performance.

✅ Index columns used in subquery conditions.

✅ Avoid correlated subqueries on large datasets if an equivalent `JOIN` or window function is available.

---

# Interview Questions

### Q1

What is a subquery?

**Answer**

A query inside another query.

---

### Q2

What is a correlated subquery?

A subquery that references columns from the outer query.

---

### Q3

Which runs faster?

Usually

```
JOIN
```

or

```
EXISTS
```

depending on the database and execution plan.

---

### Q4

Difference between EXISTS and IN?

`EXISTS` checks whether matching rows exist.

`IN` compares values against a list.

---

### Q5

Can a subquery be inside SELECT?

Yes.

---

### Q6

Can a subquery be inside FROM?

Yes.

---

### Q7

Can a subquery return multiple rows?

Yes, when used with operators like `IN`, `ANY`, or `ALL`.

---

# LeetCode SQL Problems

## Easy

- 175 - Combine Two Tables
- 176 - Second Highest Salary
- 177 - Nth Highest Salary
- 181 - Employees Earning More Than Their Managers
- 183 - Customers Who Never Order

## Medium

- 184 - Department Highest Salary
- 185 - Department Top Three Salaries
- 570 - Managers with at Least 5 Direct Reports
- 1045 - Customers Who Bought All Products
- 1978 - Employees Whose Manager Left the Company

---

# Cheat Sheet

| Operator | Purpose |
|-----------|---------|
| = | One value |
| IN | Multiple values |
| EXISTS | Matching rows exist |
| NOT EXISTS | No matching rows |
| ANY | At least one value |
| ALL | Every value |

---

# Memory Trick

```
Subquery
=
Query inside Query

IN
=
Many values

EXISTS
=
Does it exist?

ANY
=
One match

ALL
=
Every match

Correlated
=
Runs for every row
```

---

# SQL Subqueries - Complete Guide

> A complete guide to SQL Subqueries with syntax, types, examples, interview questions, optimization tips, and LeetCode practice.

---

# Table of Contents

1. What is a Subquery?
2. Types of Subqueries
3. Single Row Subquery
4. Multiple Row Subquery
5. Multiple Column Subquery
6. Correlated Subquery
7. Nested Subquery
8. EXISTS
9. NOT EXISTS
10. ANY
11. ALL
12. IN vs EXISTS
13. Correlated vs Non-Correlated
14. Common Mistakes
15. Optimization Tips
16. Interview Questions
17. LeetCode Problems
18. Cheat Sheet

---

# What is a Subquery?

A **subquery** is a query written **inside another SQL query**.

The inner query executes first, and its result is used by the outer query.

Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator
(
    SELECT column_name
    FROM another_table
);
```

---

# Sample Tables

## Employees

| id | name | salary | dept_id |
|----|------|--------|---------|
|1|Adil|60000|1|
|2|Rahul|50000|2|
|3|Aman|70000|1|
|4|John|40000|3|
|5|Alex|80000|2|

---

## Departments

| dept_id | department |
|----------|------------|
|1|IT|
|2|HR|
|3|Sales|

---

# Types of Subqueries

| Type | Returns |
|------|----------|
| Single Row | One value |
| Multiple Row | Multiple values |
| Multiple Column | Multiple columns |
| Correlated | Executes once per outer row |
| Nested | Subquery inside another subquery |

---

# 1. Single Row Subquery

Returns exactly one row.

Example

Find employees earning more than the average salary.

```sql
SELECT *
FROM Employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
);
```

Average salary

```
60000
```

Output

|name|salary|
|----|------|
|Aman|70000|
|Alex|80000|

---

Another Example

Employee with highest salary

```sql
SELECT *
FROM Employees
WHERE salary =
(
    SELECT MAX(salary)
    FROM Employees
);
```

Output

```
Alex
```

---

# 2. Multiple Row Subquery

Returns multiple rows.

Use

- IN
- ANY
- ALL

Example

Employees in IT or HR.

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
    WHERE department IN ('IT','HR')
);
```

Output

```
Adil
Rahul
Aman
Alex
```

---

# Why "=" Doesn't Work

Wrong

```sql
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
)
```

Error

```
Subquery returns more than one row
```

Correct

```sql
WHERE dept_id IN (...)
```

---

# 3. Multiple Column Subquery

Returns multiple columns.

Example

```sql
SELECT *
FROM Employees
WHERE (dept_id, salary) IN
(
    SELECT dept_id,
           MAX(salary)
    FROM Employees
    GROUP BY dept_id
);
```

Returns the highest-paid employee in each department.

---

# 4. Correlated Subquery

A correlated subquery depends on the outer query.

It executes once for **every row** of the outer query.

Example

Employees earning more than their department average.

```sql
SELECT *
FROM Employees e
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
    WHERE dept_id = e.dept_id
);
```

Execution

Outer Row

```
Adil
```

↓

Inner Query

```
Average IT Salary
```

↓

Check condition

↓

Next Employee

Repeat.

---

# Correlated Query Visualization

```
Outer Query
     |
     v
Employee Row
     |
     v
Run Inner Query
     |
     v
Compare
     |
     v
Return/Skip
```

---

# 5. Nested Subquery

Subquery inside another subquery.

Example

```sql
SELECT *
FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE department =
    (
        SELECT 'IT'
    )
);
```

---

# Subquery in SELECT

Example

```sql
SELECT
name,
salary,
(
    SELECT AVG(salary)
    FROM Employees
) AS average_salary
FROM Employees;
```

Output

|Employee|Salary|Average|
|---------|------|-------|
|Adil|60000|60000|
|Rahul|50000|60000|

---

# Subquery in FROM

Example

```sql
SELECT *
FROM
(
    SELECT dept_id,
           AVG(salary) avg_salary
    FROM Employees
    GROUP BY dept_id
) AS dept_avg;
```

---

# EXISTS

Returns TRUE if at least one row exists.

Example

Departments having employees.

```sql
SELECT *
FROM Departments d
WHERE EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# NOT EXISTS

Returns rows with no matching records.

Example

Departments without employees.

```sql
SELECT *
FROM Departments d
WHERE NOT EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# EXISTS vs IN

Example

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
);
```

Same using EXISTS

```sql
SELECT *
FROM Employees e
WHERE EXISTS
(
    SELECT 1
    FROM Departments d
    WHERE d.dept_id = e.dept_id
);
```

---

# ANY

Condition is TRUE if **at least one** value satisfies it.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ANY
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than at least one salary.
```

---

# ALL

Condition is TRUE if it satisfies **every** value.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ALL
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than every salary.
```

---

# ANY vs ALL

Suppose subquery returns

```
30000
50000
70000
```

Condition

```sql
salary > ANY (...)
```

Means

```
salary > 30000
OR
salary > 50000
OR
salary > 70000
```

Condition

```sql
salary > ALL (...)
```

Means

```
salary > 30000
AND
salary > 50000
AND
salary > 70000
```

---

# IN vs EXISTS

| Feature | IN | EXISTS |
|----------|----|---------|
|Compares values|✅|❌|
|Checks existence|❌|✅|
|Large tables|Slower|Usually Faster|
|Stops early|❌|✅|

---

# Correlated vs Non-Correlated

| Feature | Correlated | Non-Correlated |
|----------|------------|----------------|
|Depends on outer query|✅|❌|
|Runs once|❌|✅|
|Runs per row|✅|❌|
|Performance|Usually Slower|Usually Faster|

---

# Common Mistakes

## Using = instead of IN

Wrong

```sql
WHERE dept_id =
(
SELECT dept_id
FROM Departments
)
```

Correct

```sql
WHERE dept_id IN (...)
```

---

## Forgetting Alias in Correlated Query

Wrong

```sql
WHERE dept_id = dept_id
```

Correct

```sql
WHERE e.dept_id = d.dept_id
```

---

## Returning Multiple Columns

Wrong

```sql
SELECT salary,name
```

when a single value is expected.

---

# Optimization Tips

✅ Prefer `EXISTS` for checking matching rows in large tables.

✅ Use `JOIN` instead of a subquery when possible for better readability and performance.

✅ Index columns used in subquery conditions.

✅ Avoid correlated subqueries on large datasets if an equivalent `JOIN` or window function is available.

---

# Interview Questions

### Q1

What is a subquery?

**Answer**

A query inside another query.

---

### Q2

What is a correlated subquery?

A subquery that references columns from the outer query.

---

### Q3

Which runs faster?

Usually

```
JOIN
```

or

```
EXISTS
```

depending on the database and execution plan.

---

### Q4

Difference between EXISTS and IN?

`EXISTS` checks whether matching rows exist.

`IN` compares values against a list.

---

### Q5

Can a subquery be inside SELECT?

Yes.

---

### Q6

Can a subquery be inside FROM?

Yes.

---

### Q7

Can a subquery return multiple rows?

Yes, when used with operators like `IN`, `ANY`, or `ALL`.

---

# LeetCode SQL Problems

## Easy

- 175 - Combine Two Tables
- 176 - Second Highest Salary
- 177 - Nth Highest Salary
- 181 - Employees Earning More Than Their Managers
- 183 - Customers Who Never Order

## Medium

- 184 - Department Highest Salary
- 185 - Department Top Three Salaries
- 570 - Managers with at Least 5 Direct Reports
- 1045 - Customers Who Bought All Products
- 1978 - Employees Whose Manager Left the Company

---

# Cheat Sheet

| Operator | Purpose |
|-----------|---------|
| = | One value |
| IN | Multiple values |
| EXISTS | Matching rows exist |
| NOT EXISTS | No matching rows |
| ANY | At least one value |
| ALL | Every value |

---

# Memory Trick

```
Subquery
=
Query inside Query

IN
=
Many values

EXISTS
=
Does it exist?

ANY
=
One match

ALL
=
Every match

Correlated
=
Runs for every row
```

---



# SQL Subqueries - Complete Guide

> A complete guide to SQL Subqueries with syntax, types, examples, interview questions, optimization tips, and LeetCode practice.

---

# Table of Contents

1. What is a Subquery?
2. Types of Subqueries
3. Single Row Subquery
4. Multiple Row Subquery
5. Multiple Column Subquery
6. Correlated Subquery
7. Nested Subquery
8. EXISTS
9. NOT EXISTS
10. ANY
11. ALL
12. IN vs EXISTS
13. Correlated vs Non-Correlated
14. Common Mistakes
15. Optimization Tips
16. Interview Questions
17. LeetCode Problems
18. Cheat Sheet

---

# What is a Subquery?

A **subquery** is a query written **inside another SQL query**.

The inner query executes first, and its result is used by the outer query.

Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name operator
(
    SELECT column_name
    FROM another_table
);
```

---

# Sample Tables

## Employees

| id | name | salary | dept_id |
|----|------|--------|---------|
|1|Adil|60000|1|
|2|Rahul|50000|2|
|3|Aman|70000|1|
|4|John|40000|3|
|5|Alex|80000|2|

---

## Departments

| dept_id | department |
|----------|------------|
|1|IT|
|2|HR|
|3|Sales|

---

# Types of Subqueries

| Type | Returns |
|------|----------|
| Single Row | One value |
| Multiple Row | Multiple values |
| Multiple Column | Multiple columns |
| Correlated | Executes once per outer row |
| Nested | Subquery inside another subquery |

---

# 1. Single Row Subquery

Returns exactly one row.

Example

Find employees earning more than the average salary.

```sql
SELECT *
FROM Employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
);
```

Average salary

```
60000
```

Output

|name|salary|
|----|------|
|Aman|70000|
|Alex|80000|

---

Another Example

Employee with highest salary

```sql
SELECT *
FROM Employees
WHERE salary =
(
    SELECT MAX(salary)
    FROM Employees
);
```

Output

```
Alex
```

---

# 2. Multiple Row Subquery

Returns multiple rows.

Use

- IN
- ANY
- ALL

Example

Employees in IT or HR.

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
    WHERE department IN ('IT','HR')
);
```

Output

```
Adil
Rahul
Aman
Alex
```

---

# Why "=" Doesn't Work

Wrong

```sql
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
)
```

Error

```
Subquery returns more than one row
```

Correct

```sql
WHERE dept_id IN (...)
```

---

# 3. Multiple Column Subquery

Returns multiple columns.

Example

```sql
SELECT *
FROM Employees
WHERE (dept_id, salary) IN
(
    SELECT dept_id,
           MAX(salary)
    FROM Employees
    GROUP BY dept_id
);
```

Returns the highest-paid employee in each department.

---

# 4. Correlated Subquery

A correlated subquery depends on the outer query.

It executes once for **every row** of the outer query.

Example

Employees earning more than their department average.

```sql
SELECT *
FROM Employees e
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
    WHERE dept_id = e.dept_id
);
```

Execution

Outer Row

```
Adil
```

↓

Inner Query

```
Average IT Salary
```

↓

Check condition

↓

Next Employee

Repeat.

---

# Correlated Query Visualization

```
Outer Query
     |
     v
Employee Row
     |
     v
Run Inner Query
     |
     v
Compare
     |
     v
Return/Skip
```

---

# 5. Nested Subquery

Subquery inside another subquery.

Example

```sql
SELECT *
FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE department =
    (
        SELECT 'IT'
    )
);
```

---

# Subquery in SELECT

Example

```sql
SELECT
name,
salary,
(
    SELECT AVG(salary)
    FROM Employees
) AS average_salary
FROM Employees;
```

Output

|Employee|Salary|Average|
|---------|------|-------|
|Adil|60000|60000|
|Rahul|50000|60000|

---

# Subquery in FROM

Example

```sql
SELECT *
FROM
(
    SELECT dept_id,
           AVG(salary) avg_salary
    FROM Employees
    GROUP BY dept_id
) AS dept_avg;
```

---

# EXISTS

Returns TRUE if at least one row exists.

Example

Departments having employees.

```sql
SELECT *
FROM Departments d
WHERE EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# NOT EXISTS

Returns rows with no matching records.

Example

Departments without employees.

```sql
SELECT *
FROM Departments d
WHERE NOT EXISTS
(
    SELECT 1
    FROM Employees e
    WHERE e.dept_id = d.dept_id
);
```

---

# EXISTS vs IN

Example

```sql
SELECT *
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
);
```

Same using EXISTS

```sql
SELECT *
FROM Employees e
WHERE EXISTS
(
    SELECT 1
    FROM Departments d
    WHERE d.dept_id = e.dept_id
);
```

---

# ANY

Condition is TRUE if **at least one** value satisfies it.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ANY
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than at least one salary.
```

---

# ALL

Condition is TRUE if it satisfies **every** value.

Example

```sql
SELECT *
FROM Employees
WHERE salary >
ALL
(
    SELECT salary
    FROM Employees
    WHERE dept_id = 1
);
```

Equivalent to

```
Greater than every salary.
```

---

# ANY vs ALL

Suppose subquery returns

```
30000
50000
70000
```

Condition

```sql
salary > ANY (...)
```

Means

```
salary > 30000
OR
salary > 50000
OR
salary > 70000
```

Condition

```sql
salary > ALL (...)
```

Means

```
salary > 30000
AND
salary > 50000
AND
salary > 70000
```

---

# IN vs EXISTS

| Feature | IN | EXISTS |
|----------|----|---------|
|Compares values|✅|❌|
|Checks existence|❌|✅|
|Large tables|Slower|Usually Faster|
|Stops early|❌|✅|

---

# Correlated vs Non-Correlated

| Feature | Correlated | Non-Correlated |
|----------|------------|----------------|
|Depends on outer query|✅|❌|
|Runs once|❌|✅|
|Runs per row|✅|❌|
|Performance|Usually Slower|Usually Faster|

---

# Common Mistakes

## Using = instead of IN

Wrong

```sql
WHERE dept_id =
(
SELECT dept_id
FROM Departments
)
```

Correct

```sql
WHERE dept_id IN (...)
```

---

## Forgetting Alias in Correlated Query

Wrong

```sql
WHERE dept_id = dept_id
```

Correct

```sql
WHERE e.dept_id = d.dept_id
```

---

## Returning Multiple Columns

Wrong

```sql
SELECT salary,name
```

when a single value is expected.

---

# Optimization Tips

✅ Prefer `EXISTS` for checking matching rows in large tables.

✅ Use `JOIN` instead of a subquery when possible for better readability and performance.

✅ Index columns used in subquery conditions.

✅ Avoid correlated subqueries on large datasets if an equivalent `JOIN` or window function is available.

---

# Interview Questions

### Q1

What is a subquery?

**Answer**

A query inside another query.

---

### Q2

What is a correlated subquery?

A subquery that references columns from the outer query.

---

### Q3

Which runs faster?

Usually

```
JOIN
```

or

```
EXISTS
```

depending on the database and execution plan.

---

### Q4

Difference between EXISTS and IN?

`EXISTS` checks whether matching rows exist.

`IN` compares values against a list.

---

### Q5

Can a subquery be inside SELECT?

Yes.

---

### Q6

Can a subquery be inside FROM?

Yes.

---

### Q7

Can a subquery return multiple rows?

Yes, when used with operators like `IN`, `ANY`, or `ALL`.

---

# LeetCode SQL Problems

## Easy

- 175 - Combine Two Tables
- 176 - Second Highest Salary
- 177 - Nth Highest Salary
- 181 - Employees Earning More Than Their Managers
- 183 - Customers Who Never Order

## Medium

- 184 - Department Highest Salary
- 185 - Department Top Three Salaries
- 570 - Managers with at Least 5 Direct Reports
- 1045 - Customers Who Bought All Products
- 1978 - Employees Whose Manager Left the Company

---

# Cheat Sheet

| Operator | Purpose |
|-----------|---------|
| = | One value |
| IN | Multiple values |
| EXISTS | Matching rows exist |
| NOT EXISTS | No matching rows |
| ANY | At least one value |
| ALL | Every value |

---

# Memory Trick

```
Subquery
=
Query inside Query

IN
=
Many values

EXISTS
=
Does it exist?

ANY
=
One match

ALL
=
Every match

Correlated
=
Runs for every row
```

---

# Summary
