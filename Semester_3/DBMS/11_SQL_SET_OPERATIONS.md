# SQL Set Operations - Complete Guide

> A complete guide to SQL Set Operations with syntax, examples, interview questions, common mistakes, and LeetCode practice.

---

# 📚 Table of Contents

1. Introduction
2. What are Set Operations?
3. Types of Set Operations
4. UNION
5. UNION ALL
6. INTERSECT
7. EXCEPT / MINUS
8. Rules of Set Operations
9. Multiple UNION
10. Practical Example
11. When to Use Each Operation
12. Interview Questions
13. Common Mistakes
14. Database Support
15. LeetCode Practice
16. Cheat Sheet
17. Memory Trick

---

# Introduction

SQL **Set Operations** combine the results of two or more `SELECT` statements into a single result set.

They work similarly to mathematical set operations and are useful when data is spread across multiple tables with the same structure.

---

# What are Set Operations?

Set operations combine the results of multiple `SELECT` queries.

### Example

### Set A

```
1
2
3
```

### Set B

```
3
4
5
```

Different SQL set operations return different combinations of these values.

---

# SQL Set Operations

| Operation | Removes Duplicates | Purpose |
|------------|-------------------|----------|
| `UNION` | ✅ Yes | Combine unique rows |
| `UNION ALL` | ❌ No | Combine all rows |
| `INTERSECT` | ✅ Yes | Return common rows |
| `EXCEPT` / `MINUS` | ✅ Yes | Return rows in first query but not second |

---

# Sample Tables

## Employees_India

| id | name |
|----|------|
| 1 | Adil |
| 2 | Rahul |
| 3 | Aman |

---

## Employees_USA

| id | name |
|----|------|
| 3 | Aman |
| 4 | John |
| 5 | Alex |

---

# 1. UNION

Returns all **unique rows** from both queries.

## Syntax

```sql
SELECT column_list
FROM table1

UNION

SELECT column_list
FROM table2;
```

## Example

```sql
SELECT name
FROM Employees_India

UNION

SELECT name
FROM Employees_USA;
```

## Output

| name |
|------|
| Adil |
| Rahul |
| Aman |
| John |
| Alex |

### Explanation

- `Aman` appears in both tables.
- `UNION` removes duplicate rows automatically.

---

## Visualization

### Table A

```
Adil
Rahul
Aman
```

### Table B

```
Aman
John
Alex
```

### Result

```
Adil
Rahul
Aman
John
Alex
```

---

# 2. UNION ALL

Returns **all rows**, including duplicates.

## Syntax

```sql
SELECT column_list
FROM table1

UNION ALL

SELECT column_list
FROM table2;
```

## Example

```sql
SELECT name
FROM Employees_India

UNION ALL

SELECT name
FROM Employees_USA;
```

## Output

| name |
|------|
| Adil |
| Rahul |
| Aman |
| Aman |
| John |
| Alex |

### Explanation

`Aman` appears twice because `UNION ALL` does **not** remove duplicates.

---

## Visualization

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
| Removes Duplicates | ✅ | ❌ |
| Sorting Required | Yes | No |
| Performance | Slower | Faster |
| Interview Favorite | ✅ | ✅ |

---

# Why is UNION ALL Faster?

### UNION

```
Combine rows
      ↓
Find duplicates
      ↓
Remove duplicates
```

Extra processing is required.

---

### UNION ALL

```
Combine rows
      ↓
Done
```

No duplicate checking is performed, making it faster.

---

# 3. INTERSECT

Returns only rows that exist in **both** queries.

> **Note:** Supported in PostgreSQL, SQL Server, and Oracle, but **not in MySQL**.

## Syntax

```sql
SELECT column_list
FROM table1

INTERSECT

SELECT column_list
FROM table2;
```

## Example

```sql
SELECT name
FROM Employees_India

INTERSECT

SELECT name
FROM Employees_USA;
```

## Output

| name |
|------|
| Aman |

### Visualization

### Table A

```
Adil
Rahul
Aman
```

### Table B

```
Aman
John
Alex
```

### Result

```
Aman
```

---

# 4. EXCEPT

Returns rows that exist in the **first query but not in the second**.

> **Note:** Supported in PostgreSQL and SQL Server. Oracle uses `MINUS`.

## Syntax

```sql
SELECT column_list
FROM table1

EXCEPT

SELECT column_list
FROM table2;
```

## Example

```sql
SELECT name
FROM Employees_India

EXCEPT

SELECT name
FROM Employees_USA;
```

## Output

| name |
|------|
| Adil |
| Rahul |

### Visualization

### Table A

```
Adil
Rahul
Aman
```

### Table B

```
Aman
John
Alex
```

### Result

```
Adil
Rahul
```

---

# MINUS (Oracle)

Oracle uses:

```sql
MINUS
```

instead of:

```sql
EXCEPT
```

Both produce the same result.

---

# Rules of Set Operations

## Rule 1

Both queries must return the **same number of columns**.

### Correct

```sql
SELECT id, name
FROM Student

UNION

SELECT id, name
FROM Teacher;
```

### Wrong

```sql
SELECT id, name
FROM Student

UNION

SELECT id
FROM Teacher;
```

---

## Rule 2

Corresponding columns must have **compatible data types**.

### Correct

```text
INT       ↔ INT
VARCHAR   ↔ VARCHAR
```

### Wrong

```text
INT ↔ DATE
```

---

## Rule 3

Column names come from the **first SELECT statement**.

### Example

```sql
SELECT name
FROM Student

UNION

SELECT employee_name
FROM Employee;
```

Output column name:

```
name
```

---

## Rule 4

`ORDER BY` is written **only once**, at the end.

### Correct

```sql
SELECT name
FROM Student

UNION

SELECT name
FROM Employee

ORDER BY name;
```

### Wrong

```sql
SELECT name
FROM Student
ORDER BY name

UNION

SELECT name
FROM Employee;
```

---

# Multiple UNION

You can combine multiple queries.

```sql
SELECT city
FROM Student

UNION

SELECT city
FROM Teacher

UNION

SELECT city
FROM Employee;
```

---

# Practical Example

## Students

| name |
|------|
| Adil |
| Rahul |

---

## Teachers

| name |
|------|
| Aman |
| Rahul |

---

## Guests

| name |
|------|
| John |

---

### Query

```sql
SELECT name FROM Students

UNION

SELECT name FROM Teachers

UNION

SELECT name FROM Guests;
```

### Output

```
Adil
Rahul
Aman
John
```

---

# When to Use Each Operation

## UNION

Use when you need **unique records**.

Examples:

- Unique cities
- Unique customer names
- Unique departments

---

## UNION ALL

Use when duplicates are important.

Examples:

- Sales history
- Transaction logs
- Audit records
- Event logs

---

## INTERSECT

Use when you need common records.

Examples:

- Common customers
- Common employees
- Students enrolled in multiple courses

---

## EXCEPT

Use when you need missing records.

Examples:

- Customers who never ordered
- Students not enrolled
- Products never purchased

---

# Interview Questions

## Q1. What is the difference between UNION and UNION ALL?

**Answer:**

- `UNION` removes duplicates.
- `UNION ALL` keeps duplicates.

---

## Q2. Which is faster?

**Answer:**

`UNION ALL`, because it does not check for duplicates.

---

## Q3. Can UNION combine queries with different numbers of columns?

**Answer:**

No. Both queries must return the same number of columns.

---

## Q4. Can UNION combine INT and VARCHAR columns?

**Answer:**

Generally, no. Corresponding columns should have compatible data types. Some databases perform implicit conversion, but matching data types is recommended.

---

## Q5. Which operation finds common records?

**Answer:**

`INTERSECT`

---

## Q6. Which operation finds missing records?

**Answer:**

`EXCEPT` (or `MINUS` in Oracle)

---

# Common Mistakes

## Mistake 1

Different number of columns.

### Wrong

```sql
SELECT id, name
FROM A

UNION

SELECT id
FROM B;
```

---

## Mistake 2

Using `ORDER BY` in both queries.

### Wrong

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

Expecting `UNION ALL` to remove duplicates.

It never removes duplicate rows.

---

# Real Interview Scenario

### Table A

```
Apple
Banana
Orange
```

### Table B

```
Banana
Mango
Orange
```

### UNION

```
Apple
Banana
Orange
Mango
```

### UNION ALL

```
Apple
Banana
Orange
Banana
Mango
Orange
```

### INTERSECT

```
Banana
Orange
```

### EXCEPT

```
Apple
```

---

# Database Support

| Database | UNION | UNION ALL | INTERSECT | EXCEPT |
|----------|:-----:|:---------:|:---------:|:-------:|
| MySQL 8.x | ✅ | ✅ | ❌ | ❌ |
| PostgreSQL | ✅ | ✅ | ✅ | ✅ |
| SQL Server | ✅ | ✅ | ✅ | ✅ |
| Oracle | ✅ | ✅ | ✅ | `MINUS` |

> **Note:** MySQL does not support `INTERSECT` or `EXCEPT`. Similar results can be achieved using `JOIN`, `IN`, `EXISTS`, or `NOT EXISTS`.

---

# LeetCode SQL Practice

## Easy

- 175 — Combine Two Tables
- 176 — Second Highest Salary
- 181 — Employees Earning More Than Their Managers
- 183 — Customers Who Never Order
- 196 — Delete Duplicate Emails

---

## Medium

- 177 — Nth Highest Salary
- 184 — Department Highest Salary
- 185 — Department Top Three Salaries
- 570 — Managers with at Least 5 Direct Reports
- 1045 — Customers Who Bought All Products

---

# Cheat Sheet

| Operation | Removes Duplicates | Returns |
|------------|-------------------|----------|
| `UNION` | ✅ | All unique rows |
| `UNION ALL` | ❌ | All rows |
| `INTERSECT` | ✅ | Common rows |
| `EXCEPT` | ✅ | Rows in first query but not second |

---

# Memory Trick

```text
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

# Key Takeaways

- Set operations combine the results of multiple `SELECT` statements.
- `UNION` removes duplicate rows.
- `UNION ALL` keeps duplicate rows and is faster.
- `INTERSECT` returns common rows.
- `EXCEPT` (or `MINUS` in Oracle) returns rows present in the first query but not the second.
- Both queries must return the same number of columns with compatible data types.
- `ORDER BY` should be used only once, at the end of the combined query.
