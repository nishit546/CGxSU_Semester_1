### 1. Introduction to DBMS

  1.Database: An organized collection of related data that can be easily accessed, managed, and updated.
  
  2.DBMS (Database Management System): Software used to create, store, retrieve, update, and manage databases efficiently.
  
  3.Data: Raw facts and figures without any context.
  
  4.Information: Processed and meaningful data.
  
  5.File System: A traditional method of storing data in separate files without proper relationships.
  
  6.Database Users: People who interact with the database, such as administrators, developers, and end users.
  
  7.Data Independence: The ability to change the database structure without affecting application programs.

### 2. Database Models

  1.Hierarchical Model: Organizes data in a tree-like structure where each child has only one parent.
  
  2.Network Model: Allows a child record to have multiple parent records.
  
  3.Relational Model: Stores data in tables consisting of rows and columns.
  
  4.ER Model: Represents entities and their relationships graphically.
  
  5.Object-Oriented Model: Stores data as objects similar to object-oriented programming.

### 3. ER Model

  1.Entity: A real-world object or thing about which data is stored.
  
  2.Attribute: A property or characteristic of an entity.
  
  3.Relationship: An association between two or more entities.
  
  4.Cardinality: Specifies the number of entities that can participate in a relationship.
  
  5.Weak Entity: An entity that cannot exist without another entity.
  
  6.ER Diagram: A graphical representation of entities, attributes, and relationships.

### 4. Relational Model

  1.Relation: A table in a relational database.
  
  2.Tuple: A single row in a table.
  
  3.Attribute: A column in a table.
  
  4.Domain: The set of valid values for an attribute.

### Keys

  1.Super Key: Any attribute or combination of attributes that uniquely identifies a record.
  
  2.Candidate Key: The smallest possible super key.
  
  3.Primary Key: The candidate key selected to uniquely identify records.
  
  4.Alternate Key: Candidate keys that are not selected as the primary key.
  
  5.Composite Key: A key made up of two or more attributes.
  
  6.Foreign Key: An attribute that links one table to another.

### 5. SQL

  1.SQL (Structured Query Language): A language used to create, retrieve, update, and delete data from databases.
  
  2.DDL (Data Definition Language): Commands used to define database structures.
  
  3.DML (Data Manipulation Language): Commands used to insert, update, and delete data.
  
  4.DQL (Data Query Language): Used to retrieve data using the SELECT command.
  
  5.DCL (Data Control Language): Used to control user permissions.
  
  6.TCL (Transaction Control Language): Used to manage transactions.

### 6. Normalization

  1.Normalization: The process of organizing data to reduce redundancy and improve consistency.
  
  2.Functional Dependency: A relationship where one attribute determines another.
  
  3.1NF: Eliminates repeating groups.
  
  4.2NF: Removes partial dependency.
  
  5.3NF: Removes transitive dependency.
  
  6.BCNF: A stronger form of 3NF that removes remaining anomalies.

### 7. Transaction Management

   1.Transaction: A transaction is a sequence of one or more database operations performed as a 
   single logical unit of work.

  2.Atomicity: Either all operations of a transaction are completed successfully, or none of them 
  are performed.

  3.Consistency: A transaction ensures that the database moves from one valid state to another without 
    violating any rules or constraints.

  4.Isolation: Multiple transactions can run simultaneously without affecting each other's intermediate 
  results.
  
  5.Isolation: Transactions do not interfere with each other.
  
  6.Durability: Committed changes are permanently saved.
  
  7.Deadlock: A situation where two or more transactions wait indefinitely for each other.

### 8. Concurrency Control

  1.Concurrency Control: Ensures that multiple users can access the database simultaneously without conflicts.
  
  2.Locking: Prevents multiple users from modifying the same data at the same time.
  
  3.Two-Phase Locking (2PL): A protocol that guarantees serializable transactions.
  
  4.Timestamp Protocol: Uses timestamps to determine the execution order of transactions.

### 9. Storage & Indexing

  1.File Organization: The method of storing records on disk.
  
  2.Index: A data structure that speeds up data retrieval.
  
  3.B-Tree: A balanced tree used for efficient searching and insertion.
  
  4.B+ Tree: An improved version of the B-Tree where all records are stored at the leaf level.
  
  5.Hashing: A technique that uses a hash function for fast data retrieval.

### 10. Database Security
  
  1.Database Security: Protecting a database from unauthorized access and threats.
  
  2.Authentication: Verifying the identity of a user.
  
  3.Authorization: Granting users permission to perform specific actions.
  
  4. Backup: Creating a copy of the database to prevent data loss.
  
  5. Recovery: Restoring the database after a failure.
