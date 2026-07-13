## 1.Introduction to the Relational Model

Before learning SQL or designing databases, it is important to understand how data is organized.

There are many ways to organize data, such as:

    Hierarchical Model
    Network Model
    Object-Oriented Model
    Relational Model

Among all these models, the Relational Model is the most widely used because it is simple, efficient, and easy to understand.
Almost every modern database system, including MySQL, PostgreSQL, Oracle, SQL Server, and SQLite, is based on the Relational Model.


## 2. What is the Relational Model?
The Relational Model is a database model that organizes data into tables, called relations. Each table consists of rows (tuples) and columns (attributes).
The relational model is the theoretical basis of relational databases 
A 'relation' is a mathematical conceept based on the ideas of sets.

In the Relational Model:

    Data is stored in tables.
    Tables are related using keys.
    SQL is used to retrieve and manipulate data.

The Relational Model is a way of storing and organizing data in the form of tables that are connected through relationships.

### Formal Definition

    A Relational Model is a collection of relations (tables) where each relation contains tuples (rows) and
    attributes (columns), and relationships among tables are established using keys.

->After designing the conceptual model of Database using ER diagram , we need to convert the conceptual model into the relational model 
which can be implemented using any RDBMS language 

## 3. Why Do We Need the Relational Model?

Imagine a college stores student information in notebooks.

      Student 1
      Rahul
      CSE
      85

      Student 2
      Amit
      IT
      78

Finding all CSE students would require checking every page manually.

Now imagine the same information stored in a table.

    RollNo	Name	Branch	Marks
      101  	Rahul	  CSE    	85
      102  	Amit  	IT    	78
      103  	Priya  	CSE    	92

Finding all CSE students becomes simple.This is why databases use the Relational Model.


## 4. Features of the Relational Model

### 1. Data is Stored in Tables

Every table represents one type of entity.

      Example:

        Student Table

            RollNo	Name	Branch
            101	    Rahul	  CSE
            102	    Priya  	IT

 ### 2. Rows Represent Records

Each row contains information about one object.

    Example:
        101 Rahul CSE

represents one student.


### 3. Columns Represent Attributes

  Columns describe the properties of an entity.

    Example:
    
    Student Table
    
    | RollNo | Name | Branch | Semester |

Here,

RollNo
Name
Branch
Semester

are attributes.


### 4. Relationships Between Tables

Tables are connected using Foreign Keys.

    Example:
    
        Student Table
        
        RollNo	Name	CourseID
        101	    Rahul	CS101

        
        Course Table
        
        CourseID	    CourseName
        CS101	    Database Management System

The CourseID connects both tables.


### 5. SQL Support

The Relational Model uses SQL for:

      Retrieving data
      Updating records
      Deleting records
      Inserting records

      Example:
      
      SELECT Name
      FROM Student
      WHERE Branch='CSE';


### 6. Data Integrity

Rules ensure only valid data is stored.

      Example:
      Marks cannot be greater than 100.

### 7. Data Independence

Changing the storage structure does not require changes in application programs.

## 8. Components of the Relational Model

The Relational Model consists of the following components:

    Relation
    Tuple
    Attribute
    Domain
    Keys
    Constraints
    Degree- The total number of columns or attributes in the relation
    Cardinality - Total number of rows present in the table
Each of these concepts will be studied in detail in the following chapters.



## 9. properties of relational model
### 1. Relation (Table)
    Data is organized into tables called relations.
    Each table has a unique name.

### 2. Tuples (Rows)
    Each row represents a single record in the table.
    No two tuples are identical.

### 3. Attributes (Columns)
    Each column represents a property or characteristic of the data.
    Each attribute has a unique name within a relation.

### 4. Atomic Values
    Each cell contains only one value (indivisible).
    No multiple values are allowed in a single cell
    
### 5.Unique Rows
    Duplicate rows are not permitted in a relation.

### 6. Order of Rows and Columns
    The order of rows and columns has no significance.
    Data remains the same regardless of their arrangement.
    
### 7. Domain Constraint
    Each attribute contains values from a predefined set called a domain.
    All values in a column must belong to the same data type.

### 8. Primary Key
    Every relation should have a primary key to uniquely identify each tuple.
    
### 9. Null Values
    Null values are allowed to represent missing or unknown information (except in primary key attributes).

### 10. Integrity Constraints
    Ensures data accuracy and consistency through:
    a. Entity Integrity: Primary key cannot be NULL.
    b. Referential Integrity: Foreign key values must match a primary key in the referenced table or be NULL.
    c.Domain Integrity: defines the domain or the valid set of values for an attribute

    EMP(Table 1) : Related / Refrencing Table
    | Emp_ID | Name  | Age | Dep_No |     
    | -----: | ----- | --: | :----: |
    |    101 | Rahul |  24 |  D101  |
    |    102 | Amit  |  26 |  D102  |
    |    103 | Priya |  23 |  D103  |
    |    104 | Neha  |  25 |  D104  |

    DEP(Table 2) : Primary / Refrenced Table

    | Dep_No | Department | Location  |
    | :----: | ---------- | --------- |
    |  D101  | HR         | Delhi     |
    |  D102  | IT         | Mumbai    |
    |  D104  | Finance    | Bengaluru |

    Which department does Priya (Emp_ID = 103) belong to?
    So the database cannot determine:

    Department Name ❌
    Department Location ❌

This creates an invalid reference.



## 10.  Rules for Refrential Integrity 

### Rule 1: Foreign Key must match an existing Primary Key
    Every Foreign Key value must exist in the referenced parent table.
    
        Department
        
        Dep_No (PK)	Department
        D101	    HR
        D102	    IT
        
        Employee
        
        Emp_ID	Name	Dep_No (FK)
        101    	Rahul	D101
        102	    Amit	D102
        
✅ Valid because D101 and D102 exist in the Department table.


### Rule 2: Foreign Key can be NULL (if allowed)
    If the relationship is optional, the Foreign Key may be NULL.

        Example
        
        Emp_ID	Name	Dep_No (FK)
        103    	Priya	NULL

✅ Valid if an employee is not yet assigned to any department.


### Rule 3: Cannot insert an invalid Foreign Key
    You cannot insert a Foreign Key value that does not exist in the parent table.

        Example
        
        Department
        
        Dep_No
        D101
        D102
        
        Trying to insert:
        
        Emp_ID	Name	Dep_No
        104	        Neha	D105

❌ Invalid because D105 does not exist in the Department table.

### Rule 4: Cannot delete a parent row if child rows exist (by default)
    If employees are using a department, you cannot delete that department unless the child records are handled.

    Example
    
    Department:
    
    Dep_No
    D101
    
    Employee:
    
    Emp_ID	Dep_No
    101    	D101
    
    Trying to delete D101:

❌ Not allowed because Employee 101 still references it.

        
## 11. Relational Query Language

A Relational Query Language is a language used to retrieve and manipulate data stored in a relational database. It allows users to specify what data they want without describing how the database should retrieve it.

The relational model provides two main types of query languages:

    Relational Algebra (Procedural Query Language)
    Relational Calculus (Non-Procedural Query Language)
    
## 12 Why Do We Need a Relational Query Language?

Data in a relational database is stored in the form of tables (relations). To interact with this data—such as retrieving, inserting, updating, or deleting records—we need a query language.

### A relational query language helps users to:
    
    Retrieve specific data from one or more tables.
    Insert new records.
    Update existing records.
    Delete records.
    Perform operations on relations.

    
## 13. Types of Relational Query Languages

## 1. Relational Algebra (Procedural)

Relational Algebra is a procedural query language. In this language, the user specifies what data is required and how to obtain it.

It consists of operations such as:

Selection (σ)
Projection (π)
Union (∪)
Set Difference (−)
Cartesian Product (×)
Rename (ρ)
Join (⨝)

Example

Find students whose marks are greater than 80:

σ Marks > 80 (Student)

## 2. Relational Calculus (Non-Procedural)

Relational Calculus is a non-procedural (declarative) query language. The user specifies what data is required, while the database system decides how to retrieve it.


Although SQL is the standard language used in relational databases, it is based on the concepts of Relational Algebra and Relational Calculus.

For example:

SELECT Name
FROM Student
WHERE Marks > 80;

Internally, the database converts this SQL query into Relational Algebra operations before executing it.

## 14. Difference Between Relational Algebra and Relational Calculus
            | Relational Algebra                      | Relational Calculus                     |
            | --------------------------------------- | --------------------------------------- |
            | Procedural query language               | Non-procedural query language           |
            | Specifies **what** and **how**          | Specifies only **what**                 |
            | Uses algebraic operations               | Uses logical expressions                |
            | Forms the basis of SQL query processing | Forms the theoretical foundation of SQL |



## 15. Procedural and Non-Procedural Query Language

### 1. Procedural Query Language

    A Procedural Query Language requires the user to specify:
    
    What data is needed
    How to retrieve the data
    
    User tells what data to be retrieved from the database and how to retrieve it
        | RollNo | Name  | Branch | Marks |
        | ------ | ----- | ------ | ----: |
        | 101    | Rahul | CSE    |    90 |
        | 102    | Amit  | IT     |    75 |
        | 103    | Priya | CSE    |    95 |

### 2. Non-Procedural Query Language
    A Non-Procedural Query Language requires the user to specify only:
        
        What data is needed
        
        The database management system decides how to retrieve the data.

    User tells what data to be retrieved from the database but doesnt tell how to retrieve it
        Example

        Using SQL:
        
        SELECT Name
        FROM Student
        WHERE Marks > 80;
        
        The user only specifies the required result. The DBMS determines the execution plan.


## 16. Relational Algebra Operations
Relational Algebra is a procedural query language used to perform operations on relations (tables). It forms the theoretical foundation of SQL.

In Relational Algebra, the user specifies:

What data is required.
How to retrieve the data.

It consists of a set of operations that take one or more relations as input and produce another relation as output.

### Types of Relational Algebra Operations

Relational Algebra operations are classified into two categories:

### 1. Unary Operations

Unary operations work on only one relation (table).

They are:
    
    Selection (σ)
    Projection (π)
    Rename (ρ)

### 2. Binary Operations

Binary operations work on two relations (tables).

They are:

    Union (∪)
    Set Difference (−)
    Intersection (∩)
    Cartesian Product (×)
    Join (⨝)
    Division (÷)



## Selection (σ)
Selection is used to select rows from a relation based on a specified condition.
            
            σ Branch = 'CSE' (Student)

Select all students whose branch is CSE.

 Multiple Conditions
AND (∧)
            
            σ Branch='CSE' ∧ Marks>90 (Student)

OR (∨)

            σ Branch='IT' ∨ Marks>90 (Student)

NOT (¬)

            σ ¬(Branch='CSE') (Student)

## Projection (π)
Projection is a relational algebra operation used to retrieve specific columns (attributes) from a relation.

        π Name, Branch (Student)

    
