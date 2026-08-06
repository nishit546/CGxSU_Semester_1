# SQL String Functions & CASE Statement

## Introduction

SQL provides several built-in **String Functions** that allow you to manipulate and analyze text data stored in database tables.

These functions are commonly used for:

- Converting text to uppercase or lowercase
- Finding the length of a string
- Extracting part of a string
- Formatting output
- Cleaning text data

---

# SQL String Functions

## 1. `UPPER()`

The `UPPER()` function converts all characters in a string to **uppercase**.

### Syntax

```sql
UPPER(column_name)
```

### Example

```sql
SELECT UPPER(Product_Name)
FROM Products;
```

### Output

| Product_Name |
|--------------|
| LAPTOP |
| MOUSE |
| KEYBOARD |

---

## 2. `LOWER()`

The `LOWER()` function converts all characters in a string to **lowercase**.

### Syntax

```sql
LOWER(column_name)
```

### Example

```sql
SELECT LOWER(Product_Name)
FROM Products;
```

### Output

| Product_Name |
|--------------|
| laptop |
| mouse |
| keyboard |

---

## 3. `LENGTH()`

The `LENGTH()` function returns the **number of characters** in a string.

### Syntax

```sql
LENGTH(column_name)
```

### Example

```sql
SELECT Product_Name,
       LENGTH(Product_Name) AS Length
FROM Products;
```

### Output

| Product_Name | Length |
|--------------|-------:|
| Laptop | 6 |
| Mouse | 5 |
| Keyboard | 8 |

---

## 4. `SUBSTRING()`

The `SUBSTRING()` function extracts a specified portion of a string.

### Syntax

```sql
SUBSTRING(column_name, start_position, length)
```

### Parameters

- **start_position** → Starting position (starts from **1**)
- **length** → Number of characters to extract

### Example

```sql
SELECT SUBSTRING(Product_Name, 1, 4)
FROM Products;
```

### Output

| Product_Name |
|--------------|
| Lapt |
| Mous |
| Keyb |

---

# Summary of String Functions

| Function | Description | Example |
|----------|-------------|---------|
| `UPPER()` | Converts text to uppercase | `UPPER('sql')` → `SQL` |
| `LOWER()` | Converts text to lowercase | `LOWER('SQL')` → `sql` |
| `LENGTH()` | Returns the number of characters | `LENGTH('Laptop')` → `6` |
| `SUBSTRING()` | Extracts part of a string | `SUBSTRING('Laptop',1,4)` → `Lapt` |

---

# SQL `CASE` Statement

The `CASE` statement is used to implement **conditional logic** in SQL.

It works similarly to an **IF...ELSE** statement found in programming languages.

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

# Example 1: Product Availability

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

### Output

| Product_Name | Stock_Quantity | Stock_Status |
|--------------|---------------:|--------------|
| Laptop | 25 | In Stock |
| Mouse | 8 | Low Stock |
| Keyboard | 0 | Out of Stock |

---

# Example 2: Grade Classification

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

### Sample Output

| Student_Name | Marks | Grade |
|---------------|------:|-------|
| Adil | 92 | A |
| Rahul | 81 | B |
| Priya | 67 | C |
| Aman | 45 | Fail |

---

# Example 3: Price Category

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

### Sample Output

| Product_Name | Price | Price_Category |
|--------------|------:|----------------|
| Laptop | 65000 | Expensive |
| Mobile | 25000 | Moderate |
| Mouse | 900 | Budget |

---

# Key Points

- `CASE` is used to implement conditional logic in SQL.
- Conditions are evaluated from **top to bottom**.
- The **first matching condition** is returned.
- `ELSE` is optional.
- If no condition matches and `ELSE` is omitted, SQL returns **NULL**.
- `CASE` can be used with:
  - `SELECT`
  - `WHERE`
  - `ORDER BY`
  - `GROUP BY`
  - `HAVING`

---

# CASE Statement Summary

| Keyword | Description |
|---------|-------------|
| `CASE` | Starts the conditional expression |
| `WHEN` | Specifies a condition |
| `THEN` | Value returned if the condition is true |
| `ELSE` | Default value if no condition matches |
| `END` | Ends the `CASE` expression |

---

# Practice Questions

Assume the table name is **Products**.

## Q1

Display all product names in uppercase.

---

## Q2

Display all product names in lowercase.

---

## Q3

Display each product name along with its length.

---

## Q4

Display the first 5 characters of every product name.

---

## Q5

Display the stock status using the following conditions:

- Stock = 0 → **Out of Stock**
- Stock ≤ 10 → **Low Stock**
- Otherwise → **In Stock**

---

## Q6

Display the price category using the following conditions:

- Price ≥ 50000 → **Expensive**
- Price ≥ 10000 → **Moderate**
- Otherwise → **Budget**

---

## Q7

Display the first 3 letters of every product name.

---

## Q8

Display all product names along with their character count.

---

# Interview Questions

### 1. What is the purpose of the `UPPER()` function?

It converts all characters in a string to uppercase.

---

### 2. What does the `LOWER()` function do?

It converts all characters in a string to lowercase.

---

### 3. What is the difference between `LENGTH()` and `SUBSTRING()`?

- `LENGTH()` returns the number of characters in a string.
- `SUBSTRING()` extracts a specific portion of a string.

---

### 4. What is the purpose of the `CASE` statement?

The `CASE` statement is used to apply conditional logic in SQL. It works similarly to an `IF...ELSE` statement.

---

### 5. Is the `ELSE` clause mandatory in a `CASE` statement?

No. If omitted and no condition matches, SQL returns `NULL`.

---

### 6. Where can the `CASE` statement be used?

The `CASE` statement can be used with:

- `SELECT`
- `WHERE`
- `ORDER BY`
- `GROUP BY`
- `HAVING`

---

# Lab Exercise

Create a table named **Products** with the following fields:

- Product_ID
- Product_Name
- Price
- Stock_Quantity

Insert at least **5 records** and write SQL queries to:

1. Convert product names to uppercase.
2. Convert product names to lowercase.
3. Find the length of each product name.
4. Extract the first four characters of each product name.
5. Display stock status using a `CASE` statement.
6. Display price category using a `CASE` statement.
7. Display product names along with their character count.
8. Display the first three characters of each product name.

---
