# Hópverkefni 1

#### Client
    A Country Bus Company owns a number of busses. Each bus is allocated to a
    particular route, although some routes may have several busses. Each route passes
    through a number of towns. One or more drivers are allocated to each stage of a
    route, which corresponds to a journey through some or all the towns on a route.
    Some of the towns have a garage where busses are kept and each of the busses are
    identified by the registration number and can carry different numbers of passengers,
    since the vehicles vary in size and can be single or double-decked. Each route is
    identified by a route number and information is available on the average number of
    passengers carried per day for each route. Drivers have an employee number, name,
    address, and sometimes a telephone number.
   
   ___


1. Read the test carefully, list all possible entities.
    
    ```
    Route -(1-M)- stage -(1-M)- Driver
    Route -(1-M)- Busses 
    Route -(1-M)- Town -(1 - (0-1))- Garage
    ````
    
    ___
2. Write down the relationships between entities with their cardinalities.

3. Draw an ER (Entity Relationship) diagram with all possible entities, their relationships, and cardinalities?
4. List all possible attributes of the entities and define primary and foreign keys.
![alt text](https://github.com/Robertingi00/GAGN2HS05BU/blob/master/H%C3%B3pverkefni_1/img/Entity_Relationships.PNG "Entity_Relationships")
___
5. Draw an ERD Mapping that depicts all the entities, their attributes and link the foreign keys to their appropriate primary keys.
6. Define the data types of all attributes.
7. Create Database Called <Your kennitala_bus_db> and the create database tables using phpMyAdmin or Workbench.
