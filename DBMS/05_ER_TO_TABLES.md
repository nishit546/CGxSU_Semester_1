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
