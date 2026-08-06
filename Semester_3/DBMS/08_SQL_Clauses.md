# SQL Clauses

## What is a Clause?

A **clause** is a part of an SQL statement that performs a specific task, such as selecting data, filtering records, grouping rows, or sorting results.

---

# 1. SELECT Clause

### Purpose

The **SELECT** clause is used to choose which column(s) to display from a table.

## Syntax

```sql
SELECT column_name
FROM table_name;
```

## Example

```sql
SELECT Product_Name, Price
FROM Products;
```

---

# 2. FROM Clause

### Purpose

The **FROM** clause specifies the table from which data will be retrieved.

## Syntax

```sql
SELECT *
FROM table_name;
```

## Example

```sql
SELECT *
FROM Products;
```

---

# 3. WHERE Clause

### Purpose

The **WHERE** clause filters rows based on a specified condition.

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE condition;
```

## Example

```sql
SELECT *
FROM Products
WHERE Category = 'Electronics';
```

---

# 4. GROUP BY Clause

### Purpose

The **GROUP BY** clause groups rows that have the same values in one or more columns.

It is commonly used with aggregate functions such as:

- `COUNT()`
- `SUM()`
- `AVG()`
- `MIN()`
- `MAX()`

## Syntax

```sql
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name;
```

## Example

```sql
SELECT Category, COUNT(*)
FROM Products
GROUP BY Category;
```

---

# 5. HAVING Clause

### Purpose

The **HAVING** clause filters grouped data after the `GROUP BY` clause.

## Syntax

```sql
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING COUNT(*) > 1;
```

## Example

```sql
SELECT Category, COUNT(*)
FROM Products
GROUP BY Category
HAVING COUNT(*) > 1;
```

---

# 6. ORDER BY Clause

### Purpose

The **ORDER BY** clause sorts query results in ascending or descending order.

## Ascending Order (Default)

```sql
SELECT *
FROM table_name
ORDER BY column_name;
```

## Descending Order

```sql
SELECT *
FROM table_name
ORDER BY column_name DESC;
```

## Example

```sql
SELECT *
FROM Products
ORDER BY Price ASC;
```

---

# 7. LIMIT Clause

### Purpose

The **LIMIT** clause restricts the number of rows returned.

## Syntax

```sql
SELECT *
FROM table_name
LIMIT number;
```

## Example

```sql
SELECT *
FROM Products
LIMIT 3;
```

---

# 8. AS Clause (Alias)

### Purpose

The **AS** clause gives a temporary name (alias) to a column or table.

## Syntax

```sql
SELECT column_name AS alias_name
FROM table_name;
```

## Example

```sql
SELECT Product_Name AS Item_Name,
       Price AS Item_Price
FROM Products;
```

---

# 9. DISTINCT Clause

### Purpose

The **DISTINCT** clause returns only unique values.

## Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

## Example

```sql
SELECT DISTINCT Category
FROM Products;
```

---

# 10. SQL LIKE Operator

The **LIKE** operator is used for **pattern matching** in SQL.

It is commonly used with the **WHERE** clause to search text data.

## Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name LIKE pattern;
```

---

# Wildcards

| Wildcard | Description |
|----------|-------------|
| `%` | Matches zero or more characters |
| `_` | Matches exactly one character |

---

# LIKE Examples

## 1. Starts With

```sql
SELECT *
FROM Products
WHERE Name LIKE 'A%';
```

Returns all names starting with **A**.

Example Output

- Apple
- Acer Laptop
- AirPods

---

## 2. Ends With

```sql
SELECT *
FROM Products
WHERE Name LIKE '%w';
```

Returns all names ending with **w**.

Example Output

- Saw
- Screw
- Window

---

## 3. Contains

```sql
SELECT *
FROM Products
WHERE Name LIKE '%phone%';
```

Returns all names containing **phone**.

Example Output

- Smartphone
- Headphone
- iPhone

---

## 4. Exactly One Character (`_`)

```sql
SELECT *
FROM Products
WHERE Name LIKE '_at';
```

Returns names with exactly three letters ending in **at**.

Example Output

- Cat
- Bat
- Hat

---

## 5. Second Character is 'a'

```sql
SELECT *
FROM Products
WHERE Name LIKE '_a%';
```

Example Output

- Samsung
- Camera
- Table

---

## 6. Exactly Five Characters

```sql
SELECT *
FROM Products
WHERE Name LIKE '_____';
```

Example Output

- Apple
- Mouse

---

# Wildcard Summary

| Pattern | Meaning |
|----------|---------|
| `'A%'` | Starts with **A** |
| `'%A'` | Ends with **A** |
| `'%A%'` | Contains **A** anywhere |
| `'A_B%'` | Starts with **A**, third character is **B** |
| `'_____'` | Exactly five characters |
| `'_a%'` | Second character is **a** |

---

# Key Points

- `LIKE` is used for pattern matching.
- `%` matches **zero or more characters**.
- `_` matches **exactly one character**.
- `LIKE` is generally used with the `WHERE` clause.
- It works with text-based columns such as `CHAR`, `VARCHAR`, and `TEXT`.

---

# Example

```sql
SELECT Product_Name
FROM Products
WHERE Product_Name LIKE '%Book%';
```

Returns all products whose name contains **Book**.

---

# SQL Clauses Practice Questions

Assume the table name is **Products**.

## Table Structure

| Column Name | Data Type | Constraints |
|-------------|-----------|-------------|
| Student_ID | INT | Primary Key, Auto Increment |
| Student_Name | VARCHAR(100) | NOT NULL |
| Roll_No | CHAR(8) | UNIQUE |
| Age | INT | CHECK (Age >= 18) |
| Gender | VARCHAR(10) | NOT NULL |
| Course | VARCHAR(50) | NOT NULL |
| Department | VARCHAR(50) | NOT NULL |
| CGPA | DECIMAL(3,2) | DEFAULT 0.00 |
| Admission_Date | DATE | NOT NULL |

---

## Practice Questions

### Q1

Display the **Product_Name** and **Price** of all products.

---

### Q2

Display all products where the **Category** is **'Electronics'**.

---

### Q3

Group products by **Category** and display the total number of products in each category.

---

### Q4

Display only those categories that have more than one product.

> **Hint:** Use `GROUP BY` with `HAVING`.

---

### Q5

Display all products sorted by **Price** in ascending order.

---

### Q6

Display only the first **three** products from the table.

---

### Q7

Display **Product_Name** as **Item_Name** and **Price** as **Item_Price**.

---

### Q8

Display all unique categories from the **Products** table.

---

# Summary

| Clause | Purpose |
|---------|---------|
| `SELECT` | Select columns |
| `FROM` | Specify table |
| `WHERE` | Filter rows |
| `GROUP BY` | Group similar rows |
| `HAVING` | Filter grouped rows |
| `ORDER BY` | Sort data |
| `LIMIT` | Limit number of rows |
| `AS` | Create aliases |
| `DISTINCT` | Remove duplicate values |
| `LIKE` | Pattern matching |
