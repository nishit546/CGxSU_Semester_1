# SQL Joins 

## Introduction

SQL **JOIN** is used to combine rows from **two or more tables** based on a related column.

In relational databases, data is usually stored across multiple tables to reduce redundancy and improve consistency. JOIN allows us to retrieve related information from these tables in a single query.

---

# What is a JOIN?

A **JOIN** combines records from two or more tables using a common column.

Think of it like connecting two Excel sheets using a common field.

### Example

### Students Table

| student_id | name |
|------------|------|
| 1 | Ankit |
| 2 | Rahul |
| 3 | Priya |

### Marks Table

| student_id | marks |
|------------|------:|
| 1 | 90 |
| 3 | 85 |

### SQL Query

```sql
SELECT Students.name,
       Marks.marks
FROM Students
INNER JOIN Marks
ON Students.student_id = Marks.student_id;
```

### Output

| name | marks |
|------|------:|
| Ankit | 90 |
| Priya | 85 |

---

# Why Do We Need JOIN?

Consider an e-commerce application.

Instead of storing customer details repeatedly in every order, only the **customer_id** is stored.

### Customers

| customer_id | name |
|-------------|------|
| 1 | Ankit |
| 2 | Rahul |

### Orders

| order_id | customer_id | amount |
|----------|-------------|-------:|
| 101 | 1 | 500 |
| 102 | 2 | 800 |

Using a JOIN, we can retrieve the customer's name along with the order details.

---

# Types of SQL JOIN

```
                  SQL JOINS
                      │
    ┌─────────────────┼─────────────────┐
    │                 │                 │
INNER JOIN       LEFT JOIN        RIGHT JOIN
                      │
              FULL OUTER JOIN
                      │
                CROSS JOIN
                      │
                 SELF JOIN
```

---

# Sample Database

We'll use the following tables for all examples.

## Students

| student_id | name | city_id |
|------------|------|--------:|
| 1 | Ankit | 1 |
| 2 | Rahul | 2 |
| 3 | Aman | 3 |
| 4 | Priya | 2 |
| 5 | Riya | NULL |

---

## Cities

| city_id | city |
|--------:|------|
| 1 | Ahmedabad |
| 2 | Delhi |
| 3 | Mumbai |
| 4 | Pune |

---

# 1. INNER JOIN

## Definition

Returns **only matching records** from both tables.

### Diagram

```
Students
     │
INNER JOIN
     │
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

### Output

| student_id | name | city |
|------------|------|------|
| 1 | Ankit | Ahmedabad |
| 2 | Rahul | Delhi |
| 3 | Aman | Mumbai |
| 4 | Priya | Delhi |

### Explanation

- Only matching rows are returned.
- Riya is not included because her `city_id` is `NULL`.

> **INNER JOIN returns only those rows that have matching values in both tables.**

---

# 2. LEFT JOIN

## Definition

Returns:

- All rows from the **left table**
- Matching rows from the **right table**

If no match exists, **NULL** is returned.

### Syntax

```sql
SELECT *
FROM Students
LEFT JOIN Cities
ON Students.city_id = Cities.city_id;
```

### Output

| name | city |
|------|------|
| Ankit | Ahmedabad |
| Rahul | Delhi |
| Aman | Mumbai |
| Priya | Delhi |
| Riya | NULL |

### Explanation

Even though Riya has no city assigned, she still appears in the result.

---

# 3. RIGHT JOIN

## Definition

Returns:

- All rows from the **right table**
- Matching rows from the **left table**

### Syntax

```sql
SELECT *
FROM Students
RIGHT JOIN Cities
ON Students.city_id = Cities.city_id;
```

### Output

| city | student |
|------|----------|
| Ahmedabad | Ankit |
| Delhi | Rahul |
| Delhi | Priya |
| Mumbai | Aman |
| Pune | NULL |

### Explanation

Pune has no students, but it is still displayed because all rows from the right table are returned.

---

# 4. FULL OUTER JOIN

## Definition

Returns:

- All rows from the left table
- All rows from the right table

Matching rows are combined, and non-matching rows contain `NULL`.

### Syntax

```sql
SELECT *
FROM Students
FULL OUTER JOIN Cities
ON Students.city_id = Cities.city_id;
```

> **Note:** MySQL does not support `FULL OUTER JOIN` directly. It can be simulated using `LEFT JOIN UNION RIGHT JOIN`.

### Output

| student | city |
|----------|------|
| Ankit | Ahmedabad |
| Rahul | Delhi |
| Priya | Delhi |
| Aman | Mumbai |
| Riya | NULL |
| NULL | Pune |

---

# 5. CROSS JOIN

## Definition

A **CROSS JOIN** returns the Cartesian Product of two tables.

Every row from the first table is combined with every row from the second table.

### Formula

```
Rows Returned = Rows in Table A × Rows in Table B
```

### Example

Students = **5**

Cities = **4**

```
5 × 4 = 20 rows
```

### Syntax

```sql
SELECT *
FROM Students
CROSS JOIN Cities;
```

### Sample Output

```
Ankit  Ahmedabad
Ankit  Delhi
Ankit  Mumbai
Ankit  Pune

Rahul  Ahmedabad
Rahul  Delhi
Rahul  Mumbai
Rahul  Pune

...
```

---

# 6. SELF JOIN

## Definition

A **SELF JOIN** joins a table with itself.

It is commonly used to represent hierarchical relationships such as:

- Employee → Manager
- Parent → Child
- Category → Parent Category

---

## Employee Table

| id | name | manager_id |
|---:|------|-----------:|
| 1 | CEO | NULL |
| 2 | Manager | 1 |
| 3 | Developer | 2 |

---

### Query

```sql
SELECT
    E.name AS Employee,
    M.name AS Manager
FROM Employee E
JOIN Employee M
ON E.manager_id = M.id;
```

### Output

| Employee | Manager |
|-----------|----------|
| Manager | CEO |
| Developer | Manager |

---

# JOIN vs UNION

| JOIN | UNION |
|------|-------|
| Combines columns | Combines rows |
| Uses `ON` clause | Does not use `ON` |
| Horizontal merge | Vertical merge |
| Requires related tables | Requires same number of columns |

---

# ON vs WHERE

Many beginners think `ON` and `WHERE` are the same.

❌ **Incorrect**

## `ON`

Used to specify the matching condition between tables.

```sql
SELECT *
FROM Customers
JOIN Orders
ON Customers.customer_id = Orders.customer_id;
```

## `WHERE`

Used to filter the final result.

```sql
SELECT *
FROM Orders
WHERE amount > 500;
```

---

# SQL Query Execution Order

SQL executes queries in the following logical order:

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

1. Display student names along with their city names.
2. Show all students even if they do not belong to any city.
3. Show all cities even if no students belong to them.
4. Count the number of students in each city.
5. Display students who do not have a city assigned.

---

## Medium

6. List all orders with customer names.
7. Display customers who have never placed an order.
8. Find products that have never been ordered.
9. Find the highest order amount for each customer.
10. Display employee-manager relationships using a SELF JOIN.

---

## Hard

11. Find the second-highest salary department-wise.
12. Find customers who ordered every product.
13. Find employees earning more than their managers.
14. Analyze consecutive login days for users.
15. Find duplicate customers using a SELF JOIN.

---

# JOIN Summary

| JOIN Type | Returns |
|------------|---------|
| `INNER JOIN` | Matching rows only |
| `LEFT JOIN` | All rows from the left table + matching rows from the right table |
| `RIGHT JOIN` | All rows from the right table + matching rows from the left table |
| `FULL OUTER JOIN` | All rows from both tables |
| `CROSS JOIN` | Cartesian Product |
| `SELF JOIN` | A table joined with itself |

---

# Memory Tricks

| JOIN | Easy Way to Remember |
|------|----------------------|
| INNER | Intersection |
| LEFT | Everything from Left |
| RIGHT | Everything from Right |
| FULL OUTER | Everything from Both Tables |
| CROSS | Everything × Everything |
| SELF | Same Table |

---

# Interview Questions

### 1. What is a JOIN in SQL?

A JOIN combines rows from two or more tables based on a related column.

---

### 2. What is the difference between INNER JOIN and LEFT JOIN?

- **INNER JOIN** returns only matching rows.
- **LEFT JOIN** returns all rows from the left table, even if there is no matching row in the right table.

---

### 3. Which JOIN returns all records from both tables?

**FULL OUTER JOIN**

---

### 4. What is a CROSS JOIN?

A CROSS JOIN returns the Cartesian Product of two tables.

---

### 5. What is a SELF JOIN?

A SELF JOIN joins a table with itself, usually to represent hierarchical relationships.

---

### 6. What is the difference between `ON` and `WHERE`?

- `ON` specifies the join condition.
- `WHERE` filters the final result.

---

### 7. Does MySQL support FULL OUTER JOIN?

No. MySQL does not support `FULL OUTER JOIN` directly. It can be achieved using a combination of `LEFT JOIN` and `RIGHT JOIN` with `UNION`.

---

# Lab Exercise

Create the following tables:

- **Students**
- **Cities**
- **Orders**
- **Customers**

Insert at least **5 records** into each table and write SQL queries to:

1. Perform an INNER JOIN between Students and Cities.
2. Perform a LEFT JOIN.
3. Perform a RIGHT JOIN.
4. Simulate a FULL OUTER JOIN.
5. Perform a CROSS JOIN.
6. Create an Employee table and perform a SELF JOIN.
7. Count students in each city.
8. Display customers who have never placed an order.

---
