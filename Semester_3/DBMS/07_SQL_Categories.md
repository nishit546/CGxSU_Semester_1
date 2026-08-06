
## SQL Categories

SQL commands are divided into **five categories**:

1. **DDL (Data Definition Language)**
2. **DML (Data Manipulation Language)**
3. **DQL (Data Query Language)**
4. **DCL (Data Control Language)**
5. **TCL (Transaction Control Language)**

---

# 1. DDL (Data Definition Language)

DDL (**Data Definition Language**) is used to define and modify the structure of a database and its objects.

DDL commands **do not manipulate data**. Instead, they define how the data will be stored.

## DDL Commands

- `CREATE`
- `ALTER`
- `DROP`
- `TRUNCATE`
- `RENAME`

### Example

```sql
CREATE TABLE Student (
    StudentID INT,
    Name VARCHAR(50)
);
```

---

# CREATE DATABASE

Creates a new database.

## Syntax

```sql
CREATE DATABASE CollegeDB;
```

## Example

```sql
CREATE DATABASE CollegeDB;
```

---

# USE DATABASE

Selects the database to work with.

## Syntax

```sql
USE DatabaseName;
```

## Example

```sql
USE CollegeDB;
```

---

# CREATE TABLE

Creates a new table inside the selected database.

## Syntax

```sql
CREATE TABLE TableName (
    Column1 DataType,
    Column2 DataType,
    ...
);
```

## Example

```sql
CREATE TABLE Student (
    StudentID INT,
    Name VARCHAR(100),
    Age INT,
    City VARCHAR(50)
);
```

### Result

| StudentID | Name | Age | City |
|------------|------|-----|------|

> The table structure is created, but no data is stored yet.

---

# DESCRIBE TABLE

Displays the structure of a table.

## Syntax

```sql
DESC Student;
```

### Output

| Field | Type | Null | Key |
|--------|------|------|-----|
| StudentID | INT | YES | |
| Name | VARCHAR(100) | YES | |
| Age | INT | YES | |
| City | VARCHAR(50) | YES | |

---

# ALTER TABLE

Used to modify an existing table.

## Add a Column

```sql
ALTER TABLE Student
ADD Email VARCHAR(100);
```

### Before

| StudentID | Name | Age | City |
|------------|------|-----|------|

### After

| StudentID | Name | Age | City | Email |
|------------|------|-----|------|-------|

---

## Modify a Column

```sql
ALTER TABLE Student
MODIFY Name VARCHAR(150);
```

---

## Rename a Column

```sql
ALTER TABLE Student
RENAME COLUMN City TO Address;
```

---

## Drop a Column

```sql
ALTER TABLE Student
DROP COLUMN Email;
```

---

# RENAME TABLE

Renames an existing table.

```sql
RENAME TABLE Student TO Students;
```

---

# TRUNCATE TABLE

Removes all rows while keeping the table structure.

### Before

| ID | Name |
|----|------|
| 1 | Adil |
| 2 | Rahul |

### Command

```sql
TRUNCATE TABLE Student;
```

### After

| ID | Name |
|----|------|

> The table still exists and can accept new records.

---

# DROP TABLE

Deletes the table permanently along with all its data.

```sql
DROP TABLE Student;
```

---

# DROP DATABASE

Deletes the entire database.

```sql
DROP DATABASE CollegeDB;
```

> All tables and data inside the database are permanently removed.

---

# Difference Between DROP and TRUNCATE

| DROP | TRUNCATE |
|------|-----------|
| Deletes the table | Deletes all data only |
| Table structure is removed | Table structure remains |
| Cannot use the table afterwards | Can insert data again |
| Generally slower | Generally faster |

---

# Common SQL Data Types

| Category | Data Type | Description | Example |
|----------|-----------|-------------|---------|
| Numeric | `SMALLINT` | 2-byte integer | `age SMALLINT` |
| | `INT` / `INTEGER` | 4-byte integer | `quantity INT` |
| | `BIGINT` | 8-byte integer | `views BIGINT` |
| | `DECIMAL(p,s)` | Exact decimal value | `price DECIMAL(8,2)` |
| | `REAL` | Floating-point number | `rating REAL` |
| | `DOUBLE PRECISION` | Double precision floating-point | `accuracy DOUBLE PRECISION` |
| Character | `CHAR(n)` | Fixed-length string | `gender CHAR(1)` |
| | `VARCHAR(n)` | Variable-length string | `name VARCHAR(100)` |
| | `TEXT` | Long text | `bio TEXT` |
| Date & Time | `DATE` | Stores date | `joining_date DATE` |
| | `TIMESTAMP` | Stores date and time | `created_at TIMESTAMP` |
| | `INTERVAL` | Represents duration | `INTERVAL '5 days'` |
| Boolean | `BOOLEAN` | Stores `TRUE` or `FALSE` | `is_active BOOLEAN` |

---

# Data Types Example

```sql
CREATE TABLE strings (
    Id INT PRIMARY KEY,
    code CHAR(5) NOT NULL,
    email VARCHAR(100),
    bio TEXT,
    age INT CHECK (age >= 18)
);
```

### Insert Data

```sql
INSERT INTO strings (Id, code, email, bio, age)
VALUES
(1, 'AD001', 'adilahmadshah897@gmail.com', 'Hello this is the world.', 19);

INSERT INTO strings (Id, code, email, bio, age)
VALUES
(2, 'AD002', 'adil@example.com', 'Learning SQL data types.', 111);
```

### Display Data

```sql
SELECT * FROM strings;
```

---

# Project 1 – Amazon Product Inventory

## Task

Create a database named **Amazon_DB** and a table named **Products** with the following fields:

| Column | Requirement |
|---------|-------------|
| Product_ID | Auto Increment Primary Key |
| Product_Name | VARCHAR(100) |
| SKU_Code | CHAR(8) |
| Price | DECIMAL(8,2) |
| Stock_Quantity | Must be greater than or equal to 0 |
| Is_Available | BOOLEAN (Default TRUE) |
| Category | NOT NULL |
| Brand | VARCHAR |
| Added_On | DATE |
| Last_Updated | TIMESTAMP |

---

# Interview Questions

## 1. What is DDL?

**Answer:**

DDL (**Data Definition Language**) is used to define and modify the structure of database objects such as databases, tables, and indexes.

---

## 2. Which commands belong to DDL?

- CREATE
- ALTER
- DROP
- TRUNCATE
- RENAME

---

## 3. Difference Between DELETE, TRUNCATE, and DROP

| DELETE | TRUNCATE | DROP |
|---------|-----------|------|
| Deletes selected rows | Deletes all rows | Deletes the entire table |
| Supports `WHERE` clause | `WHERE` not allowed | Table is removed completely |
| Structure remains | Structure remains | Structure removed |
| Can be rolled back (in many DBMS) | Usually cannot be rolled back | Cannot be rolled back |

---

# Lab Exercise

## Task 1

Create a database named **SchoolDB**.

---

## Task 2

Create a table named **Student** with the following fields:

- StudentID
- Name
- Age
- Department

---

## Task 3

Remove the **Email** column.

---

## Task 4

Display the table structure.

---

## Task 5

Truncate the table.

---

## Task 6

Drop the table.

---

## Task 7

Drop the database.

---

# Summary

- DDL is used to define and modify database structures.
- `CREATE` creates databases and tables.
- `ALTER` modifies existing tables.
- `RENAME` changes object names.
- `TRUNCATE` removes all rows but keeps the table.
- `DROP` permanently removes database objects.
- Choosing the correct SQL data type improves storage efficiency and data integrity.
 
