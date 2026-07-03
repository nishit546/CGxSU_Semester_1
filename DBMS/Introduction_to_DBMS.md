# Introduction to Data

## 1. What is Data?

Data is a collection of raw facts, figures, symbols, observations, or values that have not yet been processed or organized into meaningful information.

Data by itself does not provide any useful meaning until it is processed.

Examples
95
Adil
CSE
50000
12/07/2026

Example in Real Life
Student Name	Marks
Rahul	85
Priya	91
Aman	78

These values are data because they are raw facts.

## Types of Data
### 1. Numeric Data

    Contains numbers.

        Example:

          50
          95
          45000
      
### 2. Text Data

    Contains alphabets or words.

        Example:

          Adil
          Delhi
          Computer Science
          
### 3. Date and Time Data

        Example:

          12-07-2026
          10:30 AM
          
### 4. Boolean Data
    Contains only two values.
      True
      False

### 5. Multimedia Data

    Includes

      Images
      Videos
      Audio
      Documents


## 2. What is Information?
Information is processed, organized, and meaningful data that helps in decision making.
Information is obtained after processing raw data.

Formula
Data + Processing = Information

            Example
            Student	Marks
            Rahul	85
            Priya	91
            Aman	78
#### After Processing

            Highest Marks = 91
            Average Marks = 84.67
            Student Passed = 3

Now the data becomes information.

## Difference Between Data and Information
        Data	    Information
        Raw facts	Processed data
        No meaning	Meaningful

### 3. Database
A Database is an organized collection of related data that is stored electronically and can be easily accessed, managed, and updated.

Example
## Student Database
    Roll No	Name	Branch	Marks
    101	   Rahul	 CSE	  90
    102	   Amit	      IT	  87
    103	   Neha	      ECE     95

## Characteristics of Database
        Organized
        Easy to access
        Secure
        Consistent
        Supports multiple users
        Reduces redundancy
## Real-Life Examples
        Banking System
        Railway Reservation
        Hospital Management
        Facebook
        Instagram
        Amazon
        Flipkart
        College ERP


## 4. Database Management System (DBMS)
A Database Management System (DBMS) is software that allows users to create, store, retrieve, update, and manage data efficiently.
It acts as an interface between users/applications and the database.

### Examples of DBMS
        MySQL
        Oracle Database
        Microsoft SQL Server
        PostgreSQL
        SQLite
        IBM Db2

### Working of DBMS
        User
           │
           ▼
        Application
           │
           ▼
        DBMS
           │
           ▼
        Database

The DBMS processes user requests and interacts with the database to retrieve or modify data.

### Functions of DBMS
        Data Storage
        Data Retrieval
        Data Update
        Data Security
        Backup and Recovery
        Transaction Management
        Concurrency Control
        Data Integrity
        Access Control


## Why Do We Need DBMS?

Before DBMS, organizations stored data in separate files.

### Example
    
    Student.txt
    
    Teacher.txt
    
    Marks.txt

### Problems with file systems:
        
        Duplicate data
        Difficult searching
        Poor security
        Data inconsistency
        No backup
        Difficult updates

## 6. Characteristics of DBMS
### 1. Data Sharing

Multiple users can access the same database simultaneously.

### 2. Data Security

Only authorized users can access sensitive data.

Example:

Student → Can view marks
Teacher → Can update marks
Admin → Full access

### 3. Data Integrity

Ensures stored data is accurate and consistent.

Example:

Marks cannot be negative.

### 4. Data Independence

Changes in the physical storage do not affect application programs.

### 5. Concurrency Control

Allows multiple users to work on the database at the same time without conflicts.

Example:

Two bank employees accessing the same account simultaneously.

### 6. Backup and Recovery

Automatically creates backups and restores data after failures.

### 7. Reduced Redundancy

Avoids storing duplicate copies of the same data.

### 8. Multiple User Support

Many users can access the database simultaneously.

### 9. Efficient Query Processing

Retrieves data quickly using SQL queries and indexes.


## 7. Advantages of DBMS
    Reduces Data Redundancy
    Improves Data Consistency
    Better Security
    Data Sharing
    Backup and Recovery
    Faster Searching
    Multiple User Access
    Better Data Integrity
    Easy Data Management
    Supports Transactions


## 8. Disadvantages of DBMS
    High Cost
    Complex Software
    Requires Skilled Professionals
    Higher Hardware Requirements
    Failure Can Affect All Users
    Regular Maintenance Needed


## 9. File System vs DBMS
    File System	                                    DBMS
    Data stored in files	                Data stored in databases
    High redundancy	                            Low redundancy
    Less security	                            High security
    No concurrency control	               Concurrency control available
    No backup	                            Backup & recovery supported
    Slow searching	                            Fast searching
    No integrity	                           Maintains integrity
    No transactions	                           Supports transactions

## 10. Applications of DBMS
        Banking
        Railway Reservation
        Airlines
        Hospital Management
        College ERP
        Library Management
        E-commerce
        Online Shopping
        Social Media
        Inventory Management
        Hotel Management
        Payroll Systems


## 11. Popular DBMS Software
        DBMS	                    Developed By	        Type
        MySQL	                        Oracle	        Open Source
        Oracle Database	                Oracle	         Commercial
        Microsoft SQL Server	        Microsoft	     Commercial
        PostgreSQL	                PostgreSQL Global 
                                    Development Group	 Open Source
        SQLite	                    SQLite Consortium	    Embedded
        IBM Db2	                          IBM	           Commercial
