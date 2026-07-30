# Database Normalization - Complete Guide


# What is Normalization?

**Normalization** is the process of organizing data into multiple related tables to:

- Reduce data redundancy (duplicate data)
- Improve data consistency
- Prevent update anomalies
- Make the database easier to maintain

Instead of storing everything in one large table, we split it into logical tables connected by keys.

---

# Why Do We Need Normalization?

Imagine this table.

## Student Table

| StudentID | StudentName | Department | HOD | Course |
|------------|-------------|------------|-----|---------|
|1|Adil|CSE|Dr. Sharma|DBMS|
|2|Rahul|CSE|Dr. Sharma|OS|
|3|Aman|CSE|Dr. Sharma|CN|
|4|John|ECE|Dr. Patel|Signals|

Notice:

- "CSE" repeats many times.
- "Dr. Sharma" repeats many times.
- Department information is duplicated.

Problems:

- Wasted storage
- Difficult updates
- Risk of inconsistent data

---

# Why Normalize if We Can Use JOIN?

A common interview question is:

> **"If SQL has JOINs, why do we normalize?"**

### Answer

Normalization and JOINs solve **different problems**.

**Normalization**

- Reduces duplicate data.
- Improves consistency.
- Prevents anomalies.
- Makes updates safer.

**JOIN**

- Combines normalized tables when retrieving data.
- Does not reduce redundancy.
- Is used only during querying.

Think of it like this:

```
Normalization
      ↓
Store data efficiently

JOIN
      ↓
Read data efficiently
```

Without normalization, a single update (like changing a department head) may require updating hundreds of rows. With normalization, you update only one row in the `Departments` table.

---

# Problems Without Normalization

Suppose:

| Student | Department | HOD |
|----------|------------|-----|
|Adil|CSE|Dr. Sharma|
|Rahul|CSE|Dr. Sharma|
|Aman|CSE|Dr. Sharma|

Now the HOD changes.

Old

```
Dr. Sharma
```

New

```
Dr. Gupta
```

You must update every row.

If one row is missed:

|Student|Department|HOD|
|--------|----------|---|
|Adil|CSE|Dr. Gupta|
|Rahul|CSE|Dr. Sharma|

The database becomes inconsistent.

---

# Goals of Normalization

- Eliminate redundancy
- Improve consistency
- Reduce storage
- Prevent anomalies
- Improve maintainability
- Ensure data integrity

---

# Types of Anomalies

## 1. Insertion Anomaly

Cannot insert department information unless a student exists.

Example

Cannot add:

```
Department
AI
HOD
Dr. Kumar
```

because there is no student.

---

## 2. Update Anomaly

Need to update the same information in many rows.

Example

```
HOD changes.
```

Update hundreds of rows.

---

## 3. Deletion Anomaly

Deleting the last student also deletes department information.

Example

Delete

```
John
```

Now

```
ECE department
```

is completely lost.

---

# Functional Dependency

A functional dependency means one attribute determines another.

Notation

```
A → B
```

Meaning

```
A determines B
```

Example

```
StudentID → StudentName
```

One student ID always has one student name.

Another

```
DepartmentID → DepartmentName
```

---

# Normal Forms Overview

| Normal Form | Removes |
|--------------|---------|
|1NF|Repeating groups|
|2NF|Partial dependency|
|3NF|Transitive dependency|
|BCNF|Remaining dependency issues|
|4NF|Multi-valued dependency|
|5NF|Join dependency|

---

# First Normal Form (1NF)

## Rule

- Atomic values only
- No repeating groups
- No arrays or comma-separated values

Wrong

|Student|Courses|
|--------|-------|
|Adil|DBMS,OS,CN|

Correct

|Student|Course|
|--------|------|
|Adil|DBMS|
|Adil|OS|
|Adil|CN|

Every cell contains exactly one value.

---

# Second Normal Form (2NF)

## Rule

- Must satisfy 1NF.
- Remove partial dependency.

Partial dependency occurs when a non-key attribute depends on only part of a composite key.

Example

Table

|StudentID|CourseID|StudentName|CourseName|
|----------|--------|-----------|----------|

Composite Key

```
(StudentID, CourseID)
```

Problem

```
StudentName depends only on StudentID.
```

```
CourseName depends only on CourseID.
```

Solution

Create

### Students

|StudentID|StudentName|

### Courses

|CourseID|CourseName|

### Enrollments

|StudentID|CourseID|

Now every non-key column depends on the entire key.

---

# Third Normal Form (3NF)

## Rule

- Must satisfy 2NF.
- Remove transitive dependency.

Example

Wrong

|StudentID|DepartmentID|DepartmentName|

Dependency

```
StudentID
    ↓
DepartmentID
    ↓
DepartmentName
```

DepartmentName depends on DepartmentID, not directly on StudentID.

Solution

Students

|StudentID|DepartmentID|

Departments

|DepartmentID|DepartmentName|

Now each table stores facts about only one entity.

---

# Boyce-Codd Normal Form (BCNF)

BCNF is a stricter version of 3NF.

Rule

For every dependency

```
A → B
```

A must be a candidate key.

Example

```
Teacher
Course
Room
```

One teacher teaches one course.

One room is assigned to one course.

Certain dependencies may violate BCNF even if the table satisfies 3NF. Splitting the table based on candidate keys resolves the issue.

---

# Fourth Normal Form (4NF)

Removes multi-valued dependencies.

Example

Wrong

|Student|Language|Hobby|
|--------|--------|-----|
|Adil|English|Cricket|
|Adil|English|Chess|
|Adil|Hindi|Cricket|
|Adil|Hindi|Chess|

Here:

```
Languages
```

and

```
Hobbies
```

are independent.

Split into

StudentLanguages

|Student|Language|

StudentHobbies

|Student|Hobby|

---

# Fifth Normal Form (5NF)

Removes join dependency.

Rarely used in normal business applications.

Mostly appears in advanced database design.

---

# Denormalization

Denormalization is the opposite of normalization.

It intentionally introduces redundancy to improve read performance.

Example

Instead of joining

```
Orders
```

and

```
Customers
```

store

```
CustomerName
```

directly in Orders.

Advantage

- Faster reads

Disadvantage

- More duplicate data
- Harder updates

---

# Normalization vs Denormalization

| Feature | Normalization | Denormalization |
|----------|---------------|-----------------|
|Redundancy|Low|High|
|Storage|Less|More|
|Read Speed|May require joins|Usually Faster|
|Update Speed|Better consistency|More updates|
|Maintenance|Easy|Harder|
|Data Integrity|High|Lower if not managed|

---

# Real World Example

Without Normalization

```
Orders
----------------------------
OrderID
CustomerName
CustomerEmail
CustomerAddress
Product
Price
```

Customer details repeat for every order.

Normalized

Customers

|CustomerID|Name|Email|Address|

Orders

|OrderID|CustomerID|

Products

|ProductID|Price|

This reduces duplication and keeps customer information in one place.

---

# Advantages

- Reduces duplicate data
- Saves storage
- Easier maintenance
- Better consistency
- Prevents anomalies
- Improves data integrity

---

# Disadvantages

- More tables
- More JOIN operations
- Slightly more complex queries
- Can affect read performance in highly normalized schemas

---

# Interview Questions

### Q1

What is normalization?

**Answer**

The process of organizing data to reduce redundancy and improve consistency.

---

### Q2

Why is normalization needed?

To reduce duplicate data and prevent insertion, update, and deletion anomalies.

---

### Q3

Difference between 2NF and 3NF?

- **2NF** removes partial dependency.
- **3NF** removes transitive dependency.

---

### Q4

What is BCNF?

A stricter version of 3NF where every determinant must be a candidate key.

---

### Q5

Difference between normalization and denormalization?

Normalization reduces redundancy.

Denormalization improves read performance by allowing controlled redundancy.

---

### Q6

Why do we still use JOIN after normalization?

Because data is stored in separate related tables. JOIN combines them only when retrieving data.

---

### Q7

What anomalies does normalization remove?

- Insertion anomaly
- Update anomaly
- Deletion anomaly

---

# Practice Problems

1. Convert a student table with comma-separated subjects into 1NF.
2. Identify partial dependencies and convert a table to 2NF.
3. Remove transitive dependencies to achieve 3NF.
4. Determine whether a table satisfies BCNF.
5. Design a normalized database for:
   - Online Shopping
   - Library Management
   - Hospital Management
   - Banking System
   - University ERP

---

# Cheat Sheet

| Normal Form | Purpose |
|--------------|---------|
|1NF|Atomic values only|
|2NF|Remove partial dependency|
|3NF|Remove transitive dependency|
|BCNF|Every determinant is a candidate key|
|4NF|Remove multi-valued dependency|
|5NF|Remove join dependency|

---

# Memory Trick

```
1NF
=
One value per cell

2NF
=
Whole key

3NF
=
Nothing but the key

BCNF
=
Every determinant is a candidate key

4NF
=
One independent multi-valued fact

5NF
=
Perfect decomposition
```

---

# Summary

- Normalization organizes data into well-structured tables.
- It minimizes redundancy and improves consistency.
- 1NF removes repeating groups.
- 2NF removes partial dependencies.
- 3NF removes transitive dependencies.
- BCNF strengthens 3NF by requiring every determinant to be a candidate key.
- 4NF removes multi-valued dependencies.
- 5NF removes join dependencies.
- Denormalization is used selectively to improve read performance in specific scenarios.
