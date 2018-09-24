# Skilaverkefni 1

Entities and their Attributes:
Customer(CUS_CODE, CUS_LNAME, CUS_FNAME, CUS_INITIAL, CUS_AREACODE, CUS_PHONE, CUS_BALANCE)
Invoice(INV_NUMBER, CUS_CODE, INV_DATE)
Line(LIN_NUMBER, LINE_UNITS, LINE_PRICE)
Product(PROD_CODE, PROD_DESCRIPT, PROD_PRICE, PROD_ON_HAND)
Verdor(VEND_CODE, VEND_CONTACT, VEND_AREACODE, VEND_PHONE)

1-	Define the data type and size for each attribute: 
        
   #### Customer
   |   Attribute  | Data type | Size |
   | ------------ | --------- | ----:|
   | Cus_Code     | INT       | 10   |
   | Cus_Lname    | Varchar   | 30   |
   | Cus_Fname    | Varchar   | 30   |
   | Cus_Initial  | Char      |  1   |
   | Cus_Areacode | INT       | 10   |
   | Cus_Phone    | Varchar   | 15   |
   | Cus_Balance  | INT       | 20   |
    
   #### Invoice
   |   Attribute  | Data type | Size |
   | ------------ | --------- | ----:|
   | Inv_Number   | INT       | 10   |
   | Cus_Cod      | INT       | 10   |
   | Inv_Date     | Date      |      |
   
   ####  Line
   |   Attribute  | Data type | Size |
   | ------------ | --------- | ----:|
   | Line_Number  | INT       | 10   |
   | Line_Units   | Varchar   | 20   |
   | Line_Price   | INT       | 10   |
   | Inv_Number   | FK        |      |
   | Prod_Code    | FK        |      |
    
   #### Product 
   |   Attribute  | Data type | Size |
   | ------------ | --------- | ----:|
   | Prod_Code    | INT       | 10   |
   | Prod_Descript| Varchar   | 30   |
   | Prod_Price   | Varchar   | 30   |
   | Prod_On_Hand | Char      |  1   |
   | Vend_Code    | INT       | 10   |
   
   
   #### Verdor
   |   Attribute  | Data type | Size |
   | ------------ | --------- | ----:|
   | Vend_Code    | INT       | 10   |
   | Vend_Contact | Varchar   | 30   |
   | Vend_Areacode| INT       | 10   |
   | Vend_Phone   | Varchar   | 15   |
   
2- Creating database and tables:
3- primary and foreign keys constraints:
4- Adding the default values:

   I put the foregin and primary keys on wen i made the database and the default values, So this is the answer to question 2 and 3 and 4.
    
   ```sql
   create database 0907002780_SaleCO;
   use 0907002780_saleco;
   CREATE TABLE Customer(
       CUS_CODE int(10) not null primary key,
       CUS_LNAME varchar(30) not null,
       CUS_FNAME varchar(30) not null,
       CUS_INITIAL varchar(3) not null,
       CUS_AREACODE int(10) not null default 0181,
       CUS_PHONE varchar(15) not null,
       CUS_BALANCE float(8) default 0.00  
   );
    CREATE table Invoice(
       LIN_NUMBER int(10) not null primary key,
       Cus_Cod int(10) not null,
       INV_Date date not null,
       constraint petur foreign key(Cus_Cod) references Customer(CUS_CODE) on delete cascade
   );

   CREATE table Vendor(
       VEND_CODE int(10) not null primary key,
       VEND_CONTACT Varchar(30),
       VEND_AREACODE int(10),
       VEND_PHONE varchar(15)
   );

   CREATE table Product(
       PROD_CODE varchar(20) not null primary key,
       PROD_DESCRIPT varchar(50) not null,
       PROD_PRICE int(8) not null,
       PROD_ON_HAND int(10) not null,
       VEND_CODE int(10) not null,
       constraint fk_product_vencode foreign key(VEND_CODE) references Vendor(VEND_CODE) on delete cascade
   );

   CREATE TABLE Line(
       Line_Number int(10) not null primary key,
       LINE_UNITS int(5) not null default 0.00,
       LINE_PRICE int(10) not null default 0.00,
       INV_NUMBER int(10) not null,
       PROD_CODE varchar(20) not null,
       constraint fk_Line_Invoice foreign key(INV_NUMBER) references Invoice(LIN_NUMBER) on delete cascade,
       constraint fk_Line_Product foreign key(PROD_CODE) references Product(PROD_CODE) on delete cascade
   );
   
   ```
5- Inserting data in to tables

   ```sql
   INSERT INTO Customer (CUS_CODE, CUS_LNAME, CUS_FNAME, CUS_INITIAL, CUS_AREACODE, CUS_PHONE, CUS_BALANCE)
   VALUES (10010,'Ramas','Alfred','A','0181','844-2573',0),
   (10011,'Dunne','Leona','K','0161','894-1238',0),
   (10012,'Smith','Kathy','W','0181','894-2285',345.86);

   INSERT INTO Invoice (LIN_NUMBER, Cus_Cod, INV_Date)
   VALUES (1001,10010,'2008-01-16'),
   (1002,10011,'2008-01-16'),
   (1003,10012,'2008-01-16');
   
   INSERT INTO Vendor (VEND_CODE, VEND_CONTACT, VEND_AREACODE, VEND_PHONE)
   VALUES (21225,'Bryson, Inc.','0181','223-3234'),
   (21226,'SuperLoo, Inc.','0113','215-8995'),
   (21231,'D\&E Supply','0181','228-3245');
   
   INSERT INTO Product (PROD_CODE, PROD_DESCRIPT, PROD_PRICE, PROD_ON_HAND, VEND_CODE)
   VALUES ('11QER/31','Power painter, 15 psi., 3-nozzle',109.99,8,21225),
   ('13-Q2/P2','7.25-cm. pwr. saw blade',14.99,22,21226),
   ('14-Q1/L3','9.00-cm. pwr. saw blade',17.49,5,21231);
   
   INSERT INTO Line (Line_Number, LINE_UNITS, LINE_PRICE, INV_NUMBER, PROD_CODE)
   VALUES (1001,1,14.99,1001,'13-Q2/P2'),
   (1002,2,9.95,1002,'11QER/31'),
   (1003,1,4.99,1003,'14-Q1/L3');
    
   ```
    
6- find a solution to the Problem.

   ```sql
   CREATE TABLE Employee(
   	EMP_num int not null auto_increment primary key,
    	EMP_title char(10),
    	EMP_Lname varchar(15),
    	EMP_Fname varchar(15),
    	EMP_Inital char(1),
    	EMP_DOB date,
    	EMP_HIR_DATE date,
    	EMP_Areacode char(5),
    	EMP_Phone char(8)
   );

   insert into Employee(EMP_title,EMP_Lname,EMP_Fname,EMP_Inital,EMP_DOB,EMP_HIR_DATE,EMP_Areacode,EMP_Phone)
   Values ('HeadofSale','Halfdanarson','Robert','R','2000-07-09','2018-09-21',54826,'555-5555');
   
   alter table Customer add EMP_num int;
   alter table Customer add constraint emp_Line_customer foreign key(EMP_num) references Employee(EMP_num) on delete cascade;

   alter table Product add EMP_num int;
   alter table Product add constraint emp_Line_protuct foreign key(EMP_num) references Employee(EMP_num) on delete cascade;

   select * from Employee;
   ```
    
    
