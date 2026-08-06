# SQL Subqueries

A **Subquery** is a query written inside another SQL query. It is enclosed in parentheses `()` and its result is used by the outer query.

```sql
SELECT column_name
FROM table_name
WHERE column_name operator (
    SELECT column_name
    FROM another_table
);
```

---

# Why Use Subqueries?

- Retrieve data based on another query
- Compare values dynamically
- Filter records
- Use with `SELECT`, `INSERT`, `UPDATE`, and `DELETE`

---

# Types of Subqueries

- Single-row Subquery
- Multiple-row Subquery
- Correlated Subquery
- Nested Subquery

---

# Sample Tables

## Employees

| emp_id | name | salary | dept_id |
|--------|------|--------|---------|
|1|Adil|50000|1|
|2|Rahul|60000|2|
|3|Aman|45000|1|
|4|Priya|70000|2|

## Departments

| dept_id | dept_name |
|---------|-----------|
|1|IT|
|2|HR|

---

# 1. Single-row Subquery

Returns only one value.

```sql
SELECT name
FROM Employees
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees
);
```

---

# 2. Multiple-row Subquery

Returns multiple rows.

```sql
SELECT name
FROM Employees
WHERE dept_id IN
(
    SELECT dept_id
    FROM Departments
    WHERE dept_name IN ('IT', 'HR')
);
```

---

# 3. Correlated Subquery

Depends on the outer query.

```sql
SELECT e1.name
FROM Employees e1
WHERE salary >
(
    SELECT AVG(salary)
    FROM Employees e2
    WHERE e1.dept_id = e2.dept_id
);
```

---

# 4. Nested Subquery

A subquery inside another subquery.

```sql
SELECT name
FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE dept_name = 'IT'
);
```

---

# Subquery with SELECT

```sql
SELECT name,
(
    SELECT dept_name
    FROM Departments
    WHERE Departments.dept_id = Employees.dept_id
) AS Department
FROM Employees;
```

---

# Subquery with INSERT

```sql
INSERT INTO IT_Employees
SELECT *
FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE dept_name = 'IT'
);
```

---

# Subquery with UPDATE

```sql
UPDATE Employees
SET salary = salary + 5000
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE dept_name = 'IT'
);
```

---

# Subquery with DELETE

```sql
DELETE FROM Employees
WHERE dept_id =
(
    SELECT dept_id
    FROM Departments
    WHERE dept_name = 'HR'
);
```

---

# EXISTS

Returns `TRUE` if the subquery returns at least one row.

```sql
SELECT name
FROM Employees e
WHERE EXISTS
(
    SELECT 1
    FROM Departments d
    WHERE e.dept_id = d.dept_id
);
```

---

# IN vs EXISTS

| IN | EXISTS |
|----|---------|
| Compares values | Checks row existence |
| Good for small datasets | Better for large datasets |

---

# Common Interview Questions

### 1. What is a subquery?
A query inside another SQL query.

### 2. Types of subqueries?
- Single-row
- Multiple-row
- Correlated
- Nested

### 3. Difference between JOIN and Subquery?

| JOIN | Subquery |
|------|----------|
| Combines tables | Query inside another query |
| Often faster | Easier for nested conditions |

### 4. Difference between IN and EXISTS?

- `IN` compares values.
- `EXISTS` checks whether rows exist.

---

# Practice Questions

1. Find employees earning more than the average salary.
2. Find employees in the IT department.
3. Find departments with more than one employee.
4. Find employees earning the highest salary in their department.
5. Delete employees belonging to the HR department.

---

# Cheat Sheet

| Type | Returns |
|------|---------|
| Single-row | One value |
| Multiple-row | Multiple values |
| Correlated | Depends on outer query |
| Nested | Subquery inside another subquery |

---

# Memory Trick

```text
Subquery = Query inside Query

IN      → Compare values
EXISTS  → Check existence
```
