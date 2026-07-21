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


### SQL Clauses Practice Questions

Assume the table name is Products.

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
