## Types of DBMS Architecture

A DBMS architecture defines how users interact with the database to read, write, or update information.
A well-designed architecture and schema (a blueprint detailing tables, fields, and relationships) ensures
data consistency, improves performance, and keeps data secure.

### 1-Tier Architecture

1-Tier Architecture: the user works directly with the database on the same system. 
  This means the client, server, and database are all in one application.
  The user can open the application, interact with the data, and perform tasks without 
  needing a separate server or network connection.

  <img width="689" height="269" alt="single_tier_architecture" src="https://github.com/user-attachments/assets/950283a2-c2ad-412b-a9ef-8f892d1a6fc4" />
    
    Imagine a railway booking computer.
    
    Inside that one computer:
    
    🖥️ Booking software is installed.
    💾 Railway database is stored locally (for example, as an SQLite or Microsoft Access database file).
    👨‍💼 The booking clerk uses the same computer to book tickets.
    
    When the clerk clicks "Book Ticket":
    
    The software reads the local database.
    It checks seat availability.
    It updates the database.
    It prints the ticket.


  ###  Advantages

    Simple Architecture: Only a single machine is required to maintain it.
    Cost-Effective: No additional hardware is required for implementing 1-Tier Architecture.
    Easy to Implement: It is mostly used in small projects. 

  ### Disadvantages

    Limited to Single User: It’s not designed for multiple users or teamwork.
    Poor Security: Everything is on the same machine, if someone gets access to the system, they can access both the data and the application easily.
    No Centralized Control: Data is stored locally, so there's no central database. This makes it hard to manage or back up data across multiple devices.
    Hard to Share Data: Everything is stored on one computer.

  ### 2-Tier Architecture

  The 2-tier architecture is similar to a basic client-server model. The application at the client end 
  directly communicates with the database on the server side. APIs like ODBC and JDBC are used for 
  this interaction. The server side is responsible for providing query processing and transaction 
  management functionalities. 

  <img width="800" height="400" alt="2_tier" src="https://github.com/user-attachments/assets/282888cf-ccec-4508-a8d8-89f0f427b40c" />

## Example
  🚆 Railway Reservation – 2-Tier Architecture
Situation

There are two computers:

🖥️ Booking Computer (used by the railway clerk)
🗄️ Database Server (stores all passenger and seat information)

The booking computer does not store the database. Instead, it directly connects to the database server through a network.

                  Railway Booking Counter
                  +------------------------+
                  |  Booking Application   |
                  |       (Client)         |
                  +-----------+------------+
                              |
                         Network (LAN/Internet)
                              |
                  +-----------v------------+
                  |    Database Server     |
                  | (Passengers, Seats,    |
                  |  Train Information)    |
                  +------------------------+

            Example

        Suppose Train 12345 has 100 seats.
        
        Indore counter books 1 seat.
        The booking application sends a request to the database server.
        The server updates the seats from 100 → 99.
        
        Now, Bhopal counter checks the same train.
        
        Since both counters are connected to the same database server, Bhopal also sees 99 seats.
        
        ✅ Data is always consistent.



  ### Why is it called 2-Tier?

      There are only two layers:
      
      Client Layer → Booking application
      Database Layer → Database server
      
      The client talks directly to the database.

 ###  Advantages

    Easy to Access: Makes fast retrieval.
    Low Cost: 2-Tier Architecture is cheaper than 3-Tier Architecture and Multi-Tier Architecture.
    Easy Deployment: Easier to deploy than 3-Tier Architecture.
    Simple: It consists only two components. 

 ### Disadvantages

    Limited Scalability: As the number of users increases, the system performance can slow down because the server gets overloaded with too many requests.
    Security Issues: Clients connect directly to the database, which can make the system more vulnerable to attacks or data leaks.
    Tight Coupling: If the database changes, the client application often needs to be updated too.
    Difficult Maintenance: Managing updates, fixing bugs, or adding features becomes harder

## 3-Tier Architecture 

  In 3-Tier Architecture, there is another layer between the client and the server. 
  The client does not directly communicate with the server. Instead, it interacts with 
  an application server which further communicates with the database system and then the
  query processing and transaction management takes place. This intermediate layer acts as a 
  medium for the exchange of partially processed data between the server and the client. This
  type of architecture is used in the case of large web applications.


  <img width="800" height="400" alt="3_tier" src="https://github.com/user-attachments/assets/84edebc3-e81f-4afb-bd01-0cd698d70b69" />

 Example: E-commerce Store

    User: You visit an online store, search for a product and add it to your cart.
    Processing: The system checks if the product is in stock, calculates the total price and applies any discounts.
    Database: The product details, your cart and order history are stored in the database for future reference.

Advantages

    Enhanced scalability: Due to the distributed deployment of application servers. Now, individual connections need not be made between the client and server.
    Data Integrity: There is a middle layer between the client and the server, data corruption can be avoided/removed.
    Security: This type of model prevents direct interaction of the client with the server thereby reducing access to unauthorized data. 

Disadvantages

    More Complex: From 2-tier to 3-tier adds one extra communication point.
    Difficult to Interact: This sort of interaction to take place due to the presence of middle layers.
    Slower Response Time: Since the request passes through an extra layer (application server), it may take more time to get a response compared to 2-Tier systems.
    Higher Cost: Setting up and maintaining three separate layers (client, server and database) requires more hardware, software and skilled people. This makes it more expensive.


  ## Difference Between 2-Tier and 3-Tier Architecture


    | Feature           | 2-Tier Architecture                           | 3-Tier Architecture                                                       |
    | ----------------- | --------------------------------------------- | ------------------------------------------------------------------------- |
    | Number of Layers  | 2 Layers                                      | 3 Layers                                                                  |
    | Layers            | Client + Database Server                      | Client + Application Server + Database Server                             |
    | Client Connection | Client directly connects to the database      | Client connects to the application server, which connects to the database |
    | Business Logic    | Stored in the client application              | Stored in the application server                                          |
    | Security          | Less secure (database exposed to clients)     | More secure (database hidden from clients)                                |
    | Performance       | Good for small applications                   | Better for large applications                                             |
    | Scalability       | Limited                                       | Highly scalable                                                           |
    | Maintenance       | Difficult                                     | Easier because logic is centralized                                       |
    | Example           | College library software, small office system | Banking apps, Amazon, Flipkart, Facebook                                  |
