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

# Practical Example

Step 1

```sql
CREATE DATABASE CollegeDB;
```

Step 2

```sql
USE CollegeDB;
```

Step 3

```sql
CREATE TABLE Student
(
    StudentID INT,
    Name VARCHAR(50),
    Age INT,
    City VARCHAR(30)
);
```

Step 4

```sql
DESC Student;
```

Step 5

```sql
ALTER TABLE Student
ADD Email VARCHAR(100);
```

Step 6

```sql
ALTER TABLE Student
DROP COLUMN Email;
```

Step 7

```sql
TRUNCATE TABLE Student;
```

Step 8

```sql
DROP TABLE Student;
```

---

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

3. Add a column Email.

4. Rename Department to Branch.

5. Remove Email.

6. Display the table structure.

7. Truncate the table.

8. Drop the table.

9. Drop the database.

---

