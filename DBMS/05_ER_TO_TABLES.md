## These are the standard ER Diagram → Relational Model Mapping Rules.

## Rule 1: Strong Entity Set with Only Simple Attributes
    A strong entity set having only simple attributes is mapped to one relation (table).
    The primary key of the entity becomes the primary key of the table.

<img width="324" height="401" alt="Screenshot 2026-07-14 105336" src="https://github.com/user-attachments/assets/983e103d-da3c-4408-9549-ac94e29cb20c" />

1.Attributes of the Table will be the attribute of entity set.

2.The Primary key of the table will the key attribute of entity set.


## Rule 2: Strong Entity Set with  Composite Attributes
    A strong entity set with  having any number of  composite attributes will require only one table in relational model.
    The primary key of the entity becomes the primary key of the table.

<img width="470" height="422" alt="Screenshot 2026-07-14 105637" src="https://github.com/user-attachments/assets/4382fad3-4157-420f-aea9-1301bb689b09" />

1.A strong entity set with any number of composite attributes will require only one table in Relational model

2.While conversion , simple attributes of the composite attributes are taken 
into account and not the composite attribute itself.


## Rule 3: Strong Entity Set with  Multi Valued Attributes
    A strong entity set with  having any number of  Multi valued attributes will require two  table in relational model.

<img width="380" height="456" alt="Screenshot 2026-07-14 105957" src="https://github.com/user-attachments/assets/44fec972-37be-414c-8c6d-687c90fdb47d" />

1.one table will contain all the simple attributes with the primary key. 

2.Other table will contain the primary key and all the multivalued attributes.


## Rule 4: Translating Relationship into a table 
    A relationship set will require one table in the relational model.
    
<img width="518" height="367" alt="Screenshot 2026-07-14 110246" src="https://github.com/user-attachments/assets/d5c48b01-b817-4ae0-beb1-1a34492af28f" />


Attributes of the table are 
Primary key attributes of the participating entity sets.
Its own descriptive attributes (if any).

The set of non-descriptive attributes (i.e., the primary key attributes of the participating entity sets) will form the primary key of the relationship table.


For the given ER diagram, three tables will be required in the relational model:

One table for the entity set Employee
One table for the entity set Department
One table for the relationship set Works In
