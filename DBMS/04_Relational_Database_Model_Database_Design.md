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
    Simple Definition

The Relational Model is a way of storing and organizing data in the form of tables that are connected through relationships.

### Formal Definition

    A Relational Model is a collection of relations (tables) where each relation contains tuples (rows) and
    attributes (columns), and relationships among tables are established using keys.

->After designing the conceptual model of Database using ER diagram , we need to convert the conceptual model int the relational model 
which can be implemented using any RDBMS language 
RDBMS Language - oracle , SQL , MySql.

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

## 5. Components of the Relational Model

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

## 7. Real-Life Example

  #### Find students with marks greater than 90.

      | RollNo | Name  | Semester | Branch | Marks |
      | ------ | ----- | -------- | ------ | ----- |
      | 101    | Rahul | 3        | CSE    | 90    |
      | 102    | Amit  | 3        | IT     | 82    |
      | 103    | Neha  | 3        | CSE    | 95    |


Only one SQL query is needed.

## 8. Real-Life Applications

The Relational Model is used in almost every industry.

### Banking

    Stores:
    
        Customers
        Accounts
        Transactions
        Loans

### Hospital

     Stores:
      
        Patients
        Doctors
        Medicines
        Appointments

### College ERP

     Stores:
      
        Students
        Faculty
        Attendance
        Fees
        Results

### Railway Reservation

    Stores:
      
        Passengers
        Trains
        Tickets
        Stations


### E-Commerce

    Stores:

        Products
        Customers
        Orders
        Payments

### Social Media
    Stores:
    
        Users
        Posts
        Comments
        Followers
