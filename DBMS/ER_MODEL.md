## 1. What is Database Design?

Before creating a database, we must first plan how the data will be stored. This planning process is called Database Design.

Database design is the process of identifying:

    What data should be stored?
    How is the data related?
    What are the rules for storing the data?
    How can data be organized efficiently?

### A good database design ensures that the database is:

    Efficient
    Organized
    Easy to maintain
    Free from unnecessary duplication (redundancy)
    Consistent and accurate


## 2. What is the ER Model?

The Entity Relationship (ER) Model is a conceptual data model used to design databases before implementation.
It provides a graphical representation of:

    Entities (Objects)
    Attributes (Properties)
    Relationships (Connections)
    Constraints (Rules)

---->>> using symbols such as rectangles, ovals, diamonds, and lines.


### Standard Definition

The Entity Relationship (ER) Model is a high-level conceptual data model
that represents the structure of a database using entities, attributes,
relationships, and constraints.

### Why is it called the Entity Relationship Model?

The name comes from two main concepts:

    Entity → Real-world object (Student, Teacher, Product)
    Relationship → Association between entities (Student enrolls in Course)

## 3. Need for the ER Model

Without an ER Model, developers often create tables directly, which can lead to poor design.

### Problems without ER Modeling
            Duplicate data
            Missing relationships
            Difficult maintenance
            Data inconsistency
            Complex SQL queries
            Difficult expansion

### Example (Without ER Model)
Suppose a college stores all information in one table:
    
    | RollNo | StudentName | Course | Faculty    | Department | Fees  | Hostel | Library |
    | ------ | ----------- | ------ | ---------- | ---------- | ----- | ------ | ------- |
    | 101    | Rahul       | DBMS   | Dr. Sharma | CSE        | 50000 | H101   | B001    |


### Problems:

    Faculty information repeats.
    Department information repeats.
    Course details repeat.
    Updating faculty requires multiple changes.
    Data redundancy increases.


### Example (With ER Model)

We first identify the entities:

    Student
    
    Faculty
    
    Course
    
    Department
    
    Library

Then identify relationships:

      Student -------- Enrolls -------- Course
                    |
                    |
                 Taught By
                    |
                 Faculty

Finally, convert the ER model into relational tables.

Result:

    Better organization
    Less redundancy
    Easier maintenance


  ## 4. Components of the ER Model
  An ER Model consists of four main components.

### 1. Entity

 An Entity is a real-world object or thing that can be identified independently.

   Examples:
    
    Student
    Faculty
    Course
    Customer
    Product

 ###  2. Attribute

  An Attribute describes an entity.

  Example:
    
  ## Student
      Roll Number
      Name
      Age
      City
      

  ### 3. Relationship

  A Relationship shows how two or more entities are connected.

  Example:

    Student -------- Enrolls -------- Course

  ### 4. Constraints

  Constraints define the rules governing the relationships.

  Example:

    One student can enroll in many courses.
    One faculty teaches many students.
    Every course belongs to one department.

  ## 5. ER Model Symbols
            | Symbol               | Meaning                  |
            | -------------------- | ------------------------ |
            | Rectangle            | Entity                   |
            | Double Rectangle     | Weak Entity              |
            | Oval                 | Attribute                |
            | Double Oval          | Multivalued Attribute    |
            | Dashed Oval          | Derived Attribute        |
            | Diamond              | Relationship             |
            | Double Diamond       | Identifying Relationship |
            | Underlined Attribute | Primary Key              |

  ## 6.ER Model Development Process

             Client Requirements
                    │
                    ▼
            Requirement Analysis
                    │
                    ▼
            Identify Entities
                    │
                    ▼
            Identify Attributes
                    │
                    ▼
            Identify Relationships
                    │
                    ▼
            Draw ER Diagram
                    │
                    ▼
            Validate Design
                    │
                    ▼
            Convert to Relational Schema
                    │
                    ▼
            Create SQL Tables

## 9. Real-World Example: College Management System

 ##  Step 1: Requirements
          A college wants to store:
              Students
              Faculty
              Courses
              Departments

    
 ##  Step 2: Identify Entities
              Student
              Faculty
              Course
              Department
        

  ## Step 3: Identify Relationships
            Department
                 │
                 │ Has
                 ▼
            Course
                 ▲
                 │ Taught By
            Faculty
                 ▲
                 │ Enrolls
            Student

            
### Step 4: Convert into Tables
        Student
        Faculty
        Course
        Department
        Enrollment


 ##  10. Real-World Applications of the ER Model
     | Domain        | Example Entities               |
    | ------------- | ------------------------------ |
    | College       | Student, Faculty, Course       |
    | Hospital      | Patient, Doctor, Appointment   |
    | Banking       | Customer, Account, Transaction |
    | E-Commerce    | Customer, Product, Order       |
    | Railway       | Passenger, Train, Ticket       |
    | Hotel         | Guest, Room, Booking           |
    | Social Media  | User, Post, Comment            |
    | Food Delivery | Restaurant, Menu, Order        |
    | Library       | Book, Author, Member           |
    | Government    | Citizen, Passport, License     |


## 11. Practical Classroom Activity
    Problem Statement
    
    Design a database for a university.
    
    Requirements:
    
    A student enrolls in courses.
    Each course is taught by one faculty member.
    Each faculty belongs to one department.
    Task
    Identify the entities.
    List attributes for each entity.
    Identify relationships.
    Draw a simple ER diagram.
    Suggest primary keys.


   ## 12 Uses of ER Diagrams in DBMS

    ER diagrams represent the E-R model in a database, making them easy to convert into relations (tables).
    These diagrams serve the purpose of real-world modeling of objects which makes them intently useful.
    Unlike technical schemas, ER diagrams require no technical knowledge of the underlying DBMS used.
    They visually model data and its relationships, making complex systems easier to understand.

## Types of Attributes
### 1. Key Attribute

The attribute which uniquely identifies each entity in the entity set is called the key attribute.
For example, Roll_No will be unique for each student. In ER diagram,
the key attribute is represented by an oval with an underline. 

<img width="268" height="151" alt="frame_3253" src="https://github.com/user-attachments/assets/926002a7-3ef1-4a60-910a-fd88deccd04f" />


### 2. Composite Attribute

An attribute composed of many other attributes is called a composite attribute. 
For example, the Address attribute of the student Entity type consists of Street, City, State, and Country. 
In ER diagram, the composite attribute is represented by an oval comprising of ovals. 

<img width="800" height="250" alt="frame_3257" src="https://github.com/user-attachments/assets/31261377-15f2-492f-96c9-d8ea0fae4563" />


###  3. Multivalued Attribute 

An attribute consisting of more than one value for a given entity. 
For example, Phone_No (can be more than one for a given student). 
In ER diagram, a multivalued attribute is represented by a double oval. 

<img width="268" height="151" alt="frame_3254" src="https://github.com/user-attachments/assets/9f4c8c77-3e05-4624-a33b-f7c7c5c1e0c4" />


 ### 4. Derived Attribute

An attribute that can be derived from other attributes of the entity type is known as a derived attribute.
e.g.; Age (can be derived from DOB). In ER diagram, the derived attribute is represented by a dashed oval. 

<img width="268" height="151" alt="frame_3255" src="https://github.com/user-attachments/assets/ea418941-a86b-4b9d-8ee3-2a5fced096f5" />

 The Complete Entity Type Student with its Attributes can be represented as: 

 <img width="800" height="400" alt="frame_3256" src="https://github.com/user-attachments/assets/4b2e9039-5abd-46c7-84e7-1c0ad593237d" />



## Relationship Type and Relationship Set 

A Relationship Type represents the association between entity types. For example, 
‘Enrolled in’ is a relationship type that exists between entity type Student and Course.
In ER diagram, the relationship type is represented by a diamond and connecting the entities with lines. 

<img width="800" height="245" alt="frame_3239" src="https://github.com/user-attachments/assets/dccc0f2d-5604-447d-a5c9-b98bd3033821" />

A set of relationships of the same type is known as a relationship set. 
The following relationship set depicts S1 as enrolled in C2, S2 as enrolled in C1,
and S3 as registered in C3. 

<img width="629" height="308" alt="frame_3245" src="https://github.com/user-attachments/assets/dabd2881-74fc-4b98-92e9-21ead78698ba" />



## Degree of a Relationship Set 

The number of different entity sets participating in a relationship set is called the degree of a relationship set.

### 1. Unary/Recursive Relationship: When there is only ONE entity set participating in a relation.
For example, one person is married to only one person. 

<img width="539" height="188" alt="frame_3251" src="https://github.com/user-attachments/assets/5346e43e-7ed8-4e5f-98b0-38c0e2f85866" />

### 2. Binary Relationship: When there are TWO entities set participating in a relationship. For example, a Student is enrolled in a Course. 

<img width="800" height="245" alt="frame_3239" src="https://github.com/user-attachments/assets/e42d206e-99f3-426a-9634-d212a3f19d68" />

### 3. Ternary Relationship: When there are three entity sets participating in a relationship.

 <img width="800" height="323" alt="ternary_relationship" src="https://github.com/user-attachments/assets/e17f4012-37c7-45ed-8336-72a8f537ee2b" />

### 4. N-ary Relationship: When there are n entities set participating in a relationship, the relationship is called an n-ary relationship. 

<img width="800" height="380" alt="n_ary_relationship" src="https://github.com/user-attachments/assets/513f02ca-af11-491d-9fb1-95d73b6bf3c1" />

