# DBMS Views

A complete guide to SQL **Views** with syntax, examples, advantages, disadvantages, interview questions, and practice exercises.

---

# Table of Contents

1. What is a View?
2. Why Use Views?
3. Syntax
4. Create a View
5. Display a View
6. Update a View
7. Delete a View
8. Types of Views
9. Advantages
10. Disadvantages
11. Table vs View
12. Real-World Example
13. Interview Questions
14. Practice Questions
15. Cheat Sheet

---

# What is a View?

A **View** is a **virtual table** created using a `SELECT` statement. It does not store data itself; instead, it stores the query and displays the latest data from the underlying table(s).

> **Definition:** A View is a virtual table that displays data from one or more tables.

---

# Why Use Views?

- Hide sensitive information
- Simplify complex queries
- Reuse frequently used queries
- Provide data abstraction
- Restrict user access to specific columns

---

# Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table_name
WHERE condition;
```

---

# Create a View

### Student Table

| student_id | name | marks |
|------------|------|------:|
| 1 | Adil | 85 |
| 2 | Ali | 72 |
| 3 | Sara | 91 |

### Query

```sql
CREATE VIEW TopStudents AS
SELECT student_id, name, marks
FROM Student
WHERE marks >= 80;
```

### Output

| student_id | name | marks |
|------------|------|------:|
| 1 | Adil | 85 |
| 3 | Sara | 91 |

---

# Display a View

```sql
SELECT * FROM TopStudents;
```

---

# Update a View

```sql
CREATE OR REPLACE VIEW TopStudents AS
SELECT student_id, name, marks
FROM Student
WHERE marks >= 75;
```

---

# Delete a View

```sql
DROP VIEW TopStudents;
```

---

# Types of Views

## 1. Simple View

- Based on a single table
- No aggregate functions
- Usually updatable

```sql
CREATE VIEW StudentInfo AS
SELECT student_id, name
FROM Student;
```

---

## 2. Complex View

- Based on multiple tables
- Uses JOIN, GROUP BY, Aggregate Functions, etc.
- Usually not updatable

```sql
CREATE VIEW DepartmentReport AS
SELECT d.department_name,
       COUNT(s.student_id) AS TotalStudents
FROM Department d
JOIN Student s
ON d.department_id = s.department_id
GROUP BY d.department_name;
```

---

# Advantages of Views

- Improves security
- Simplifies complex queries
- Reusable SQL
- Provides data abstraction
- Shows customized data to users

---

# Disadvantages of Views

- Can be slower for complex queries
- Some views cannot be updated
- Depends on underlying tables
- Table changes may affect the view

---

# Table vs View

| Feature | Table | View |
|---------|-------|------|
| Stores Data | ✅ Yes | ❌ No |
| Storage Required | High | Very Little |
| Based On | Actual Data | SQL Query |
| Can Be Updated | ✅ Yes | Sometimes |
| Index Support | ✅ Yes | Generally No |

---

# Real-World Example

Suppose the **Employee** table contains salary information.

| employee_id | name | salary | department |
|-------------|------|--------|------------|
| 1 | Adil | 70000 | IT |
| 2 | Sara | 90000 | HR |

Employees should not see salaries.

```sql
CREATE VIEW EmployeeDetails AS
SELECT employee_id, name, department
FROM Employee;
```

Now users can access:

```sql
SELECT * FROM EmployeeDetails;
```

without viewing salary details.

---

# Interview Questions

### 1. What is a View?

A virtual table created using a `SELECT` statement.

### 2. Does a View store data?

No. It stores only the SQL query.

### 3. Can a View be updated?

Yes, but only some simple views are updatable.

### 4. Difference between Table and View?

| Table | View |
|-------|------|
| Stores data | Stores query |
| Occupies storage | Minimal storage |
| Physical object | Virtual object |

### 5. Why are Views used?

- Security
- Simplicity
- Data abstraction
- Reusability

---

# Practice Questions

1. Create a view showing students with marks above 80.
2. Display all records from a view.
3. Update a view using `CREATE OR REPLACE VIEW`.
4. Delete a view.
5. Create a view that hides employee salaries.
6. Create a complex view using `JOIN` and `GROUP BY`.

---

# Cheat Sheet

| Command | Syntax |
|---------|--------|
| Create View | `CREATE VIEW view_name AS SELECT ...;` |
| Display View | `SELECT * FROM view_name;` |
| Update View | `CREATE OR REPLACE VIEW view_name AS ...;` |
| Delete View | `DROP VIEW view_name;` |

---

# Memory Trick

```text
VIEW

V → Virtual Table
I → Improves Security
E → Easy Query Reuse
W → Works Like a Table
```
