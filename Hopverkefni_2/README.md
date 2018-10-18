# Hópverkefni 2
### Nemendur: Helgi & Róbert


#### 1. Write the SQL code that will create the table structure for a table named EMP_1. This table is a subset of the EMPLOYEE table. The basic EMP_1 table structure is summarized in the table below. (Note that the JOB_CODE is the FK to JOB.)

```sql

create database 0907002780_Hopverkefni2;
use 0907002780_Hopverkefni2;

create table JOB(
    JOB_CODE int PRIMARY KEY NOT NULL auto_increment,
    JOB_DESCRIPTION varchar(40),
    JOB_CHG_HOUR NUMERIC(9, 2),
    JOB_LAST_UPDATE date
)AUTO_INCREMENT=500;

create table EMPLOYEE(
    EMP_NUM int PRIMARY KEY NOT NULL auto_increment,
    EMP_LNAME varchar(15),
    EMP_FNAME varchar(15),
    EMP_INITIAL char(3),
    EMP_HIREDATE date not null,
    JOB_CODE_FK int not null,
    EMP_YEARS char(3), 
    FOREIGN KEY(JOB_CODE_FK) references JOB (JOB_CODE)
)AUTO_INCREMENT=100;

create table ASSIGNMENT(
    ASSIGN_NUM INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    ASSIGN_DATE date NOT NULL,
    PROJ_NUM_FK char(4) not null,
    EMP_NUM_FK int not null,
    JOB_CODE_FK int not null,
    ASSIGN_CHG_HR NUMERIC(9,2),
    ASSIGN_HOURS NUMERIC(9,2),
    ASSIGN_CHARGE NUMERIC(9,2),
    FOREIGN KEY (PROJ_NUM_FK) references PROJECT(PROJ_NUM),
    FOREIGN KEY (EMP_NUM_FK) references EMPLOYEE(EMP_NUM),
    FOREIGN KEY (JOB_CODE_FK) references JOB(JOB_CODE)
)AUTO_INCREMENT=1000;

create table PROJECT(
    PROJ_NUM char(4) not null PRIMARY KEY,
    PROJ_NAME varchar(30),
    PROJ_VALUE NUMERIC(25, 2),
    PROJ_BALANCE NUMERIC(25, 2),
    EMP_NUM_FK int not null,
    FOREIGN KEY(EMP_NUM_FK) references EMPLOYEE (EMP_NUM)
);

```
___
#### 2. Having created the table structure in Question 1, write the SQL code to enter the first two rows for the table shown in Figure Q1.2.

```sql

INSERT INTO ASSIGNMENT(ASSIGN_DATE,PROJ_NUM_FK,EMP_NUM_FK,JOB_CODE_FK,ASSIGN_CHG_HR,ASSIGN_HOURS) values
('2016-05-22',18,103,503,84.50,3.5),
('2013-04-01',22,117,509,34.55,4.2),
('2014-03-05',18,117,509,34.55,2.0),
('2012-11-07',18,103,503,84.50,5.9),
('2011-12-23',18,103,503,96.75,2.2),
('2015-12-27',22,117,509,96.75,4.2),
('2017-12-29',18,117,509,50.75,3.8),
('2018-01-15',18,103,503,84.50,0.9),
('2011-08-18',18,103,503,96.75,5.6),
('2015-08-16',22,117,509,34.55,2.4),
('2013-06-22',18,117,509,105.00,4.3),
('2017-01-12',18,103,503,96.75,3.4),
('2018-05-13',18,103,503,96.75,2.0),
('2012-02-08',22,117,509,96.75,2.8),
('2013-07-09',18,117,509,84.50,6.1),
('2017-09-15',18,103,503,105.00,4.7),
('2015-12-03',18,103,503,34.55,3.8),
('2013-12-02',22,117,509,34.55,2.2),
('2015-02-26',18,117,509,110.50,4.9),
('2018-07-30',18,103,503,125.00,3.1),
('2017-06-22',18,103,503,110.50,2.7),
('2017-08-21',22,117,509,110.50,4.9),
('2016-11-05',18,117,509,125.00,3.5),
('2017-03-15',18,103,503,84.50,3.3),
('2016-12-04',18,103,503,34.55,4.2);


INSERT INTO EMPLOYEE(EMP_LNAME, EMP_FNAME, EMP_INITIAL,EMP_HIREDATE,JOB_CODE_FK, EMP_YEARS) values
('News','John','G','2013-09-25',502,4),
('Senior','Dabid','H','2004-07-11',502,15),
('Arbough','June','E','2010-03-4',502,8),
('Ramoras','Anne','K','2001-02-26',502,17),
('Johnson','Alice','K','2006-04-12',502,12),
('Smithfield','William',null,'2018-01-22',502,0),
('Alonzo','Maria','D','2006-12-06',502,11),
('Washington','Ralph','B','2004-11-02',502,13),
('Smith','Larry','W','2011-12-22',502,7),
('Olenko','Gerald','A','2009-03-22',502,9),
('Wabash','Geoff','B','2004-05-26',502,14),
('Smithson','Derlene','M','2008-12-22',502,10),
('Joenbrood','Delbert','K','2010-03-18',502,8),
('Jones','Annelise',null,'2007-07-17',502,11),
('Bawangi','Travis','B','2005-06-03',502,13),
('Pratt','Gerald','L','2010-04-06',502,8),
('Williamson','Angie','H','2010-01-05',502,8),
('Frommer','James','J','2018-07-03',502,0);

INSERT INTO JOB(JOB_DESCRIPTION, JOB_CHG_HOUR, JOB_LAST_UPDATE) values
('Programmer',37.75, '2018-07-26'),
('System Analyst',96.75, '2018-07-26'),
('Database Designer',125.00, '2018-07-26'),
('Electrical Designer',84.50, '2018-06-26'),
('Machanical Engineer',67.90, '2018-07-26'),
('Civil Engineer',55.78, '2018-06-26'),
('Clerical Support',26.87, '2018-07-26'),
('DSS Analyst',45.95, '2018-06-26'),
('Application Designer',48.10, '2018-07-26'),
('Bio Technician',34.55, '2018-06-26'),
('General Support',18.36, '2018-06-26');

INSERT INTO PROJECT values
('15','Evergreen',1453500.00,1002350.00,103),
('18','Amber Wave',3500500.00,2110346.00,108),
('22','Rolling Tide',805000.00,500345.20,102),
('25','Starflight',2650500.00,2309880.00,107);

```

___
#### 3. Assuming the data shown in the EMP_1 table have been entered, write the SQL code that will list all attributes for a job code of 502.

```sql

SELECT * FROM EMPLOYEE WHERE JOB_CODE_FK = 502;

```
___
#### 4. Write the SQL code that will save the changes made to the EMP_1 table.
```sql

commit;

```
___
#### 5. Write the SQL code to change the job code to 501 for the person whose employee number (EMP_NUM) is 107. After you have completed the task, examine the results, and then reset the job code to its original value.
#### 6. Write the SQL code to delete the row for the person named William Smithfield, who was hired on June 22, 2004, and whose job code classification is 500. (Hint: Use logical operators to include all of the information given in this problem.)
#### 7. Write the SQL code that will restore the data to its original status; that is, the table should contain the data that existed before you made the changes in Questions 5 and 6.

```sql

set autocommit= 0;
Set sql_safe_updates = 0;
start transaction;
update EMPLOYEE SET JOB_CODE_FK = 501 WHERE EMP_NUM = 107;

DELETE FROM EMPLOYEE
WHERE  EMP_FNAME = 'William' AND EMP_LNAME = 'Smithfield' AND EMP_HIREDATE = '2018-01-22';
SELECT * FROM employee;
Rollback;

```
___
#### 8. Write the SQL code to create a copy of EMP_1, naming the copy EMP_2. Then write the SQL code that will add the attributes EMP_PCT and PROJ_NUM to its structure. The EMP_PCT is the bonus percentage to be paid to each employee. The new attribute characteristics:
#### are: EMP_PCTNUMBER(4,2) and PROJ_NUMCHAR(3)
#### (Note: If your SQL implementation allows it, you may use DECIMAL(4,2) rather than NUMBER(4,2).)
 
```sql

alter table EMPLOYEE add EMP_PCT decimal(4,2);
alter table EMPLOYEE add PROJ_NUM_FK char(4);
alter table EMPLOYEE add FOREIGN KEY(PROJ_NUM_FK) references PROJECT(PROJ_NUM);

```
___
#### 9. Write the SQL code to change the EMP_PCT value to 3.85 for the person whose employee number (EMP_NUM) is 103. Next, write the SQL command sequences to change the EMP_PCT values as shown in Figure Q1.3.

```sql

update EMPLOYEE SET EMP_PCT = 5 WHERE EMP_NUM = 101;
update EMPLOYEE SET EMP_PCT = 8 WHERE EMP_NUM = 102;
update EMPLOYEE SET EMP_PCT = 3.85 WHERE EMP_NUM = 103;
update EMPLOYEE SET EMP_PCT = 10 WHERE EMP_NUM = 104;
update EMPLOYEE SET EMP_PCT = 5 WHERE EMP_NUM = 105;
update EMPLOYEE SET EMP_PCT = 6.2 WHERE EMP_NUM = 106;
update EMPLOYEE SET EMP_PCT = 5.15 WHERE EMP_NUM = 107;
update EMPLOYEE SET EMP_PCT = 10 WHERE EMP_NUM = 108;
update EMPLOYEE SET EMP_PCT = 2 WHERE EMP_NUM = 109;

```
___
#### 10. Using a single command sequence, write the SQL code that will change the project number (PROJ_NUM) to 18 for all employees whose job classification (JOB_CODE) is 500.
```sql

update EMPLOYEE set PROJ_NUM_FK = 18 where JOB_CODE_FK = 500;

```
___
#### 11. Using a single command sequence, write the SQL code that will change the project number (PROJ_NUM) to 25 for all employees whose job classification (JOB_CODE) is 502 or higher. When you finish Questions 10 and 11, the EMP_2 table will contain the data shown in Figure Q7.11. (You may assume that the table has been saved again at this point.)

```sql

update EMPLOYEE set PROJ_NUM_FK = 25 where JOB_CODE_FK >= 502;

```
___
#### 12. Write the SQL code that will change the PROJ_NUM to 15 for those employees who were hired before January 1, 1994 and whose job code is at least 501. (You may assume that the table will be restored to its condition preceding this question.)

```sql

update EMPLOYEE set PROJ_NUM_FK = 15 where EMP_HIREDATE < '2011-01-01' and JOB_CODE_FK >= 501;

```
___
#### 13. Write the two SQL command sequences required to: 
#### a. Create a temporary table named TEMP_1 whose structure is composed of the EMP_2 attributes EMP_NUM and EMP_PCT.
#### b. Copy the matching EMP_2 values into the TEMP_1 table.
#### 14. Write the SQL command that will delete the newly created TEMP_1 table from the database.
```sql

CREATE TABLE TEMP_1 AS SELECT EMP_NUM, EMP_PCT FROM EMPLOYEE;
select * from TEMP_1;

drop table TEMP_1;

```
___
#### 15. Write the SQL code required to list all employees whose last names start with Smith. In other words, the rows for both Smith and Smithfield should be included in the listing. Assume case sensitivity.
```sql

select * from EMPLOYEE where EMP_LNAME like 'Smith%';

```
___
#### 16. Using the EMPLOYEE, JOB, and PROJECT tables in the Review database (see Figure Q7.1), write the SQL code that will produce the results shown in Figure Q1.4.
```sql

SELECT P.PROJ_NAME, P.PROJ_VALUE, P.PROJ_BALANCE, E.EMP_LNAME, E.EMP_FNAME, E.EMP_INITIAL, J.JOB_CODE, J.JOB_DESCRIPTION, J.JOB_CHG_HOUR
FROM Project AS P
INNER JOIN Employee AS E ON P.EMP_NUM_FK = E.EMP_NUM
INNER JOIN JOB AS J ON E.JOB_CODE_FK = J.JOB_CODE;

```
___
#### 17. Write the SQL code that will produce a virtual table named REP_1. The virtual table should contain the same information that was shown in Question 16.
```sql

create view REP_1 as

SELECT P.PROJ_NAME, P.PROJ_VALUE, P.PROJ_BALANCE, E.EMP_LNAME, E.EMP_FNAME, E.EMP_INITIAL, J.JOB_CODE, J.JOB_DESCRIPTION, J.JOB_CHG_HOUR
FROM Project AS P
INNER JOIN Employee AS E ON P.EMP_NUM_FK = E.EMP_NUM
INNER JOIN JOB AS J ON E.JOB_CODE_FK = J.JOB_CODE;

```
___
#### 18. Write the SQL code to find the average bonus percentage in the EMP_2 table you created in Question 8.
```sql

SELECT AVG(EMP_PCT) FROM EMPLOYEE;

```
___

#### 19. Write the SQL code that will produce a listing for the data in the EMP_2 table in ascending order by the bonus percentage.
```sql

SELECT * FROM EMPLOYEE order by EMP_PCT;

```
___   
#### 20. Write the SQL code that will list only the distinct project numbers found in the EMP_2 table.
```sql

SELECT distinct PROJ_NUM_FK FROM employee;

```
___
#### 21. Write the SQL code to calculate the ASSIGN_CHARGE values in the ASSIGNMENT table in the Review database. (See Figure Q1.7.) Note that ASSIGN_CHARGE is a derived attribute that is calculated by multiplying ASSIGN_CHG_HR by ASSIGN_HOURS.
```sql

select PROJ_NUM_FK, sum(ASSIGN_CHG_HR), sum(ASSIGN_HOURS), sum(ASSIGN_CHG_HR*ASSIGN_HOURS) AS sum_of_CHG from ASSIGNMENT group by PROJ_NUM_FK;

```

___
#### 22. Using the data in the ASSIGNMENT table, write the SQL code that will yield the total number of hours worked for each employee and the total charges stemming from those hours worked. The results of running that query are shown in Figure Q1.5.
```sql

select E.EMP_NUM, E.EMP_LNAME, SUM(A.ASSIGN_HOURS), SUM(A.ASSIGN_CHG_HR*A.ASSIGN_HOURS) from EMPLOYEE as E
INNER JOIN ASSIGNMENT AS A ON A.EMP_NUM_FK = E.EMP_NUM group by E.EMP_NUM;

```

___
#### 23. Write a query to produce the total number of hours and charges for each of the projects represented in the ASSIGNMENT table. The output is shown in Figure Q1.6.
```sql

select PROJ_NUM_FK, sum(ASSIGN_CHG_HR), sum(ASSIGN_HOURS), sum(ASSIGN_CHG_HR*ASSIGN_HOURS) AS sum_of_CHG from ASSIGNMENT group by PROJ_NUM_FK;

```

___
#### 24. Write the SQL code to generate the total hours worked and the total charges made by all employees. The results are shown in Figure Q1.8. (Hint: This is a nested query. If you use Microsoft Access, you can generate the result by using the query output shown in Figure Q1.6 as the basis for the query that will produce the output shown in Figure Q1.8.)
```sql

select SUM(A.ASSIGN_HOURS), SUM(A.ASSIGN_CHG_HR*A.ASSIGN_HOURS) from EMPLOYEE as E
INNER JOIN ASSIGNMENT AS A ON A.EMP_NUM_FK = E.EMP_NUM;

```
___
#### 25. Write the SQL code to generate the total hours worked and the total charges made to all projects. The results should be the same as those shown in Figure Q1.8. (Hint: This is a nested query. If you use Microsoft Access, you can generate the result by using the query output shown in Figure Q1.7 as the basis for this query.)

```sql

select SUM(A.ASSIGN_HOURS), SUM(A.ASSIGN_CHG_HR*A.ASSIGN_HOURS) from Project as P
INNER JOIN ASSIGNMENT AS A ON A.PROJ_NUM_FK = P.PROJ_NUM;

```

