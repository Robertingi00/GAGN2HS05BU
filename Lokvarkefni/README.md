# Lokaverkefni GAGN2HS05BU
## 1. Write the SQL code to create the table structures for the entities shown in Figure P7.44. The structures should contain the attributes specified in the ERD. Use data types that are appropriate for the data that will need to be stored in each attribute. Enforce primary key and foreign key constraints as indicated by the ERD.

```sql

CREATE TABLE MEMBERSHIP (
MEM_NUM     INT PRIMARY KEY NOT NULL AUTO_INCREMENT,
MEM_FNAME   VARCHAR(30),
MEM_LNAME   VARCHAR(30),
MEM_STREET  VARCHAR(39),
MEM_CITY	VARCHAR(30), 
MEM_STATE   VARCHAR(3),
MEM_ZIP		INT NOT NULL,
MEM_BALANCE	INT )AUTO_INCREMENT = 102;

CREATE TABLE RENTAL (
RENT_NUM INT PRIMARY KEY AUTO_INCREMENT,
RENT_DATE DATE,
MEM_NUM INT NOT NULL,
constraint THISMEMBERSHIP foreign key(MEM_NUM) references MEMBERSHIP(MEM_NUM))AUTO_INCREMENT = 1001;

CREATE TABLE PRICE (
PRICE_CODE	INT PRIMARY KEY NOT NULL,
PRICE_DESCRIPTION VARCHAR(20),
PRICE_RENTFEE INT,
PRICE_DAILYLATEFEE INT);

CREATE TABLE MOVIE (
MOVIE_NUM INT PRIMARY KEY NOT NULL,
MOVIE_TITLE VARCHAR(40),
MOVIE_YEAR INT,
MOVIE_COST float,
MOVIE_GENRE VARCHAR(15),
PRICE_CODE INT,
CONSTRAINT THISPRICE FOREIGN KEY(PRICE_CODE) REFERENCES PRICE(PRICE_CODE));

CREATE TABLE VIDEO (
VID_NUM INT PRIMARY KEY NOT NULL,
VID_INDATE DATE,
MOVIE_NUM INT,
CONSTRAINT THISMOVIE FOREIGN KEY(MOVIE_NUM) REFERENCES MOVIE(MOVIE_NUM));


CREATE TABLE DETAILRENTAL (
RENT_NUM INT,
VID_NUM INT,
DETAIL_FEE 	FLOAT,
DETAIL_DUEDATE	DATE,
DETAIL_RETURNDATE DATE,
DETAIL_DAILYLATEFEE INT,
CONSTRAINT THISRENTAL FOREIGN KEY(RENT_NUM) REFERENCES RENTAL(RENT_NUM),
CONSTRAINT THISVIDEO FOREIGN KEY(VID_NUM) REFERENCES VIDEO(VID_NUM));

```
## 2. The following tables provide a very small portion of the data that will be kept in the database. This data needs to be inserted into thedatabase for testing purposes. Write the INSERT commands necessary to place the following data in the tables that were created in Problem 1.
```sql

INSERT INTO MEMBERSHIP(MEM_FNAME, MEM_LNAME, MEM_STREET, MEM_CITY, MEM_STATE,MEM_ZIP, MEM_BALANCE) values
("Tami","Dawson","2632 Takli Circle","Norene","TN",37136,11),
("Curt","Knight","4025 Cornell Court","Flatgap","KY",41219,6),
("Jamal","Melendez","788 East 145th Avenue","Quebeck","TN",38579,0),
("Iva","Mcclain","6045 Musket Ball Circle","Summit","TN",42783,15),
("Maranda","Parks","4469 Maxwell Place","Germantown","TN",38183,0),
("Rosario","Elliott","7578 Danner Avenue","Columbia","TN",38402,5),
("Mattie","Guy","4390 Evergreen Avenue","Lily","KY",40740,0),
("Clint","Ochoa","1711 Elm Street","Greeneville","TN",37745,10),
("Lewis","Rosales","4524 Southwind Circle","Counce","TN",38326,0),
("Stacy","Mann","2789 Est Cook Avenue","Murfreesboro","TN",37132,8),
("Luis","Trujillo","7267 Malvin Avenue","Heiskell","TN",37754,3),
("Minnie","Gonzales","6430 Vasili Drive","Willston","TN",38076,0);

INSERT INTO RENTAL(RENT_DATE, MEM_NUM) VALUES
("2009-03-01",103),
("2009-03-01",105),
("2009-03-02",102),
("2009-03-02",110),
("2009-03-02",111),
("2009-03-02",107),
("2009-03-02",104),
("2009-03-03",105),
("2009-03-03",111);

INSERT INTO PRICE VALUES
(1,"Standard",2,1),
(2,"New Release",3.5,3),
(3,"Discount",1.5,1),
(4,"Weekly Special",1,0.5);

INSERT INTO MOVIE VALUES
(1234,"The Cesar Family Christmas",2007,39.95,"FAMILY",2),
(1235,"Smokey Mountain Wildlife",2004,59.95,"ACTION",1),
(1236,"Richard Goodhope",2008,59.95,"DRAMA",2),
(1237,"Beatnik Fever",2007,29.95,"COMEDY",2),
(1238,"Constant Companion",2008,89.95,"DRAMA",2),
(1239,"Where Hope Dies",1998,25.49,"DRAMA",3),
(1245,"Time to Burn",2005,45.49,"ACTION",1),
(1246,"What He Doesn't Know",2006,58.25,"COMEDY",1);

INSERT INTO VIDEO VALUES
(54321,"2008-06-18",1234),
(54324,"2008-06-18",1234),
(54325,"2008-06-18",1234),
(34341,"2007-01-22",1235),
(34342,"2007-01-22",1235),
(34366,"2009-03-02",1236),
(34367,"2009-03-02",1236),
(34368,"2009-03-02",1236),
(34369,"2009-03-02",1236),
(44392,"2008-10-21",1237),
(44397,"2008-10-21",1237),
(59237,"2009-02-14",1237),
(61388,"2007-01-25",1239),
(61353,"2006-01-28",1245),
(61354,"2006-01-28",1245),
(61367,"2008-07-30",1246),
(61369,"2008-07-30",1246);

INSERT INTO DETAILRENTAL VALUES
(1001,34342,2,"2009-03-04","2009-03-02",3),
(1001,61353,2,"2009-03-04","2009-03-03",3),
(1002,59237,3.5,"2009-03-04","2009-03-04",3),
(1003,54325,3.5,"2009-03-04","2009-03-09",3),
(1003,61369,2,"2009-03-06","2009-03-09",1),
(1003,61388,0,"2009-03-06","2009-03-09",1),
(1004,44392,3.5,"2009-03-05","2009-03-07",3),
(1004,34367,3.5,"2009-03-05","2009-03-07",3),
(1004,34341,2,"2009-03-07","2009-03-07",1),
(1005,34342,2,"2009-03-07","2009-03-05",1),
(1005,44397,3.5,"2009-03-05","2009-03-05",3),
(1006,34366,3.5,"2009-03-05","2009-03-04",3),
(1006,61367,2,"2009-03-07",NULL,1),
(1007,34368,3.5,"2009-03-05",NULL,3),
(1008,34369,3.5,"2009-03-05","2009-03-05",3),
(1009,54324,3.5,"2009-03-05",NULL,3),
(1001,34366,3.5,"2009-03-04","2009-03-02",3);



```
## 3. Write a query to display the movie title, movie year, and movie cost for all movies that contain the word “hope” anywhere in the title. Sort the results in ascending order by title. (The results are shown in figure P7.55.)
```sql

SELECT MOVIE_TITLE, MOVIE_YEAR, MOVIE_COST 
FROM MOVIE 
WHERE MOVIE_TITLE 
LIKE "%hope%" 
ORDER BY(MOVIE_TITLE);

```
## 4. Write a query to display the movie title, movie year, and movie genre for all action movies. (The results are shown in Figure P7.56.)
```sql

SELECT MOVIE_TITLE, MOVIE_YEAR, MOVIE_GENRE 
FROM MOVIE 
WHERE MOVIE_GENRE = "ACTION" 
ORDER BY(MOVIE_TITLE);

```
## 5. Write a query to display the movie number, movie title, and movie cost for all movies with a cost greater than $40. (The results are shown in Figure P7.57.)
```sql

SELECT MOVIE_NUM , MOVIE_TITLE, MOVIE_COST 
FROM MOVIE 
WHERE MOVIE_COST > 40 
ORDER BY(MOVIE_NUM);

```
## 6. Write a query to display the movie number, movie title, movie cost, and movie genre for all movies that are either action or comedy movies and that have a cost that is less than $50. Sort the results in ascending order by genre. (The results are shown in Figure P7.58.)
```sql

SELECT MOVIE_NUM , MOVIE_TITLE, MOVIE_COST , MOVIE_GENRE 
FROM MOVIE 
WHERE (MOVIE_GENRE = "ACTION" 
       OR MOVIE_GENRE = "COMEDY") 
       AND MOVIE_COST < 50; 

```
## 7. Write a query to display the movie number, and movie description for all movies where the movie description is a combination of the movie title, movie year, and movie genre with the movie year enclosed in parentheses. (The results are shown in Figure P7.59.)
```sql

SELECT MOVIE_NUM , concat(MOVIE_TITLE, '(' ,MOVIE_YEAR,')' , MOVIE_GENRE) AS "MOVIE DESCRIPTION" 
FROM MOVIE;

```
## 8. Write a query to display the movie genre and the number of movies in each genre. (The results are shown in Figure P7.60.)
```sql

SELECT MOVIE_GENRE , COUNT(MOVIE_GENRE) AS "NUMBERS OF MOVIES" 
FROM MOVIE 
GROUP BY(MOVIE_GENRE);

```
## 9. Write a query to display the average cost of all of the movies. (The results are shown in Figure P7.61.)
```sql

SELECT ROUND(avg(MOVIE_COST), 2) 
FROM MOVIE;

```
## 10. Write a query to display the movie genre and average cost of movies in each genre. (The results are shown in Figure P7.62.)
```sql

SELECT MOVIE_GENRE , ROUND(AVG(MOVIE_COST), 2) 
FROM MOVIE 
GROUP BY MOVIE_GENRE;

```
## 11. Write a query to display the movie title, movie genre, price description, and price rental fee for all movies with a price code. (The results are shown in Figure P7.63.)
```sql

SELECT M.MOVIE_TITLE , M.MOVIE_GENRE , PRICE_DESCRIPTION , PRICE_RENTFEE 
FROM PRICE AS P INNER 
JOIN MOVIE AS M 
ON P.PRICE_CODE  = M.PRICE_CODE;

```
## 12. Write a query to display the movie genre and average price rental fee for movies in each genre that have a price. (The results are shown in Figure P7.64.)
```sql

SELECT M.MOVIE_GENRE , AVG(PRICE_RENTFEE) AS "AVARAGE RENTAL FEE" 
FROM PRICE AS P INNER 
JOIN MOVIE AS M 
ON P.PRICE_CODE  = M.PRICE_CODE 
GROUP BY(MOVIE_GENRE);

```
## 13. Write a query to display the movie title, movie year, and the movie cost divided by the price rental fee for each movie that has a price to determine the number of rentals it will take to break even on the purchase of the movie. (The results are shown in Figure P7.65.)
```sql

SELECT M.MOVIE_TITLE , M.MOVIE_YEAR , M.MOVIE_COST/PRICE_RENTFEE AS "BREAKEVEN RENTALS" 
FROM PRICE AS P INNER 
JOIN MOVIE AS M 
ON P.PRICE_CODE  = M.PRICE_CODE 
GROUP BY(MOVIE_TITLE);

```
## 14. Write a query to display the movie title and movie year for all movies that have a price code. (The results are shown in Figure P7.66.)
```sql

SELECT M.MOVIE_TITLE , M.MOVIE_YEAR  
FROM MOVIE AS M INNER 
JOIN PRICE AS P 
ON M.PRICE_CODE = P.PRICE_CODE 
WHERE P.PRICE_CODE IS NOT NULL;

```
## 15. Write a query to display the movie title, movie year, and movie cost for all movies that have a cost between $44.99 and $49.99. (The results are shown in Figure P7.67.)
```sql

SELECT MOVIE_TITLE , MOVIE_YEAR , MOVIE_COST 
FROM MOVIE 
WHERE MOVIE_COST > 44.99 
AND MOVIE_COST < 49.99;

```
## 16. Write a query to display the movie title, movie year, price description, and price rental fee for all movies that are in the genres family, comedy, or drama. (The results are shown in Figure P7.68.)
```sql

SELECT M.MOVIE_TITLE , M.MOVIE_YEAR , PRICE_DESCRIPTION , PRICE_RENTFEE , M.MOVIE_GENRE
FROM PRICE AS P INNER JOIN MOVIE AS M ON P.PRICE_CODE  = M.PRICE_CODE 
WHERE M.MOVIE_GENRE = "FAMILY" 
OR M.MOVIE_GENRE = "COMEDY" 
OR M.MOVIE_GENRE = "DRAMA" 
GROUP BY(MOVIE_TITLE);

```
## 17. Write a query to display the minimum balance, maximum balance, and average balance for memberships that have a rental. (The results are shown in Figure P7.71.)
```sql

SELECT MIN(MEM_BALANCE) , MAX(MEM_BALANCE) , AVG(MEM_BALANCE) 
FROM MEMBERSHIP;

```
## 18. Write a query to display the membership name (concatenate the first name and last name with a space between them into a single column), membership address (concatenate the street, city, state, and zip codes into a single column with spaces. (The results are shown in Figure P7.72.)
```sql

SELECT concat(MEM_FNAME, " ", MEM_LNAME) AS "MEMBERSHIP NAME" 
, concat(MEM_STREET, " ,",
         MEM_CITY, " ,",MEM_STATE, " ,",MEM_ZIP ) AS "MEMEBERSHIP ADDRESS" 
FROM MEMBERSHIP;

```
## 19. Write a query to display the rental number, rental date, video number, movie title, due date, and return date for all videos that were returned after the due date. Sort the results by rental number and movie title. (The results are shown in Figure P7.73.)
```sql

SELECT R.RENT_NUM , R.RENT_DATE , V.VID_NUM , M.MOVIE_TITLE , DR.DETAIL_DUEDATE , DR.DETAIL_RETURNDATE 
FROM RENTAL AS R INNER JOIN DETAILRENTAL AS DR 
ON DR.RENT_NUM = R.RENT_NUM
INNER JOIN VIDEO AS V 
ON DR.VID_NUM = V.VID_NUM
INNER JOIN MOVIE AS M 
ON M.MOVIE_NUM = V.MOVIE_NUM 
GROUP BY RENT_NUM;

```
## 20. Write a query to display the rental number, rental date, video number, movie title, due date, return date, detail fee, and number of days past the due date that the video was returned for each video that was returned after the due date. Sort the results by rental number and movie title. (The results are shown in Figure P7.74.)
```sql

SELECT R.RENT_NUM , R.RENT_DATE , V.VID_NUM , M.MOVIE_TITLE , DR.DETAIL_DUEDATE , DR.DETAIL_RETURNDATE , DR.DETAIL_FEE , DATEDIFF(DR.DETAIL_RETURNDATE, DR.DETAIL_DUEDATE) as Days_Past_Due
FROM RENTAL AS R INNER JOIN DETAILRENTAL AS DR 
ON DR.RENT_NUM = R.RENT_NUM
INNER JOIN VIDEO AS V 
ON DR.VID_NUM = V.VID_NUM
INNER JOIN MOVIE AS M 
ON M.MOVIE_NUM = V.MOVIE_NUM 
WHERE DATEDIFF(DR.DETAIL_RETURNDATE, DR.DETAIL_DUEDATE) > 0 
GROUP BY RENT_NUM;

```
## 21. Write a query to display the rental number, rental date, movie title, and detail fee for each movie that was returned on or before the due date. (The results are shown in Figure P7.75.)
```sql

SELECT R.RENT_NUM , R.RENT_DATE, M.MOVIE_TITLE, DR.DETAIL_FEE
FROM RENTAL AS R INNER JOIN DETAILRENTAL AS DR 
ON DR.RENT_NUM = R.RENT_NUM
INNER JOIN VIDEO AS V 
ON DR.VID_NUM = V.VID_NUM
INNER JOIN MOVIE AS M 
ON M.MOVIE_NUM = V.MOVIE_NUM 
WHERE DATEDIFF(DR.DETAIL_RETURNDATE, DR.DETAIL_DUEDATE) <= 0 
GROUP BY RENT_NUM;

```
## 22. Write a query to display the membership number, last name, first name, and total rental fees earned from that membership. (The results are shown in Figure P7.76.) The total rental fee is the sum of all of the detail fees (without the late fees) from all movies that the membership has rented.
```sql

SELECT M.MEM_NUM, M.MEM_LNAME, M.MEM_FNAME, SUM(DR.DETAIL_FEE) FROM MEMBERSHIP AS M
INNER JOIN RENTAL AS R 
ON M.MEM_NUM = R.MEM_NUM
INNER JOIN DETAILRENTAL AS DR 
ON R.RENT_NUM = DR.RENT_NUM 
GROUP BY MEM_LNAME;


```
## 23. Write a query to display the movie number, movie genre, average movie cost of movies in that genre, movie cost of that individual movie, and the percentage difference between the average movie cost and the individual movie cost. (The results are shown in Figure P7.77.) (Note: The percentage difference is calculated as the cost of the individual movie minus the average cost of movies in that genre, divided by the average cost of movies in that genre multiplied by 100. For example, if the average cost of movies in the “family” genre is $25, if a given family movie cost $26, then the calculation would be ((26 – 25) / 25 * 100), which would work out to be 4.00%. This indicates that this movie costs 4% more than the average family movie.)
```sql
ALVEG EIN OG 17 :) 

```
## 24. Alter the DETAILRENTAL table to include a derived attribute named DETAIL_DAYSLATE to store integers up to 3 digits. The attribute should accept null values.
```sql

ALTER TABLE DETAILRENTAL ADD DETAIL_DAYSLATE DECIMAL(3,0) NOT NULL;

```
## 25. Alter the VIDEO table to include an attribute named VID_STATUS to store character data up to 4 characters long. The attribute should not accept null values. The attribute should have a constraint to enforce the domain (“IN”, “OUT”, and “LOST”) and have a default value of “IN”.
```sql

ALTER TABLE VIDEO ADD VID_STATUS VARCHAR(4) DEFAULT "IN" NOT NULL;

```
## 26. Update the VID_STATUS attribute of the VIDEO table using a subquery to set the VID_STATUS to “OUT” for all videos that have a null value in the DETAIL_RETURNDATE attribute of the DETAILRENTAL table.
```sql

SET SQL_SAFE_UPDATES = 0;
UPDATE VIDEO
SET VID_STATUS ='OUT'
WHERE VID_NUM IN (SELECT VID_NUM FROM DETAILRENTAL 
                  WHERE DETAIL_RETURNDATE IS NULL);

```
## 27. Alter the PRICE table to include an attribute named PRICE_RENTDAYS to store integers up to 2 digits. The attribute should not accept null values, and should have a default value of 3.
```sql

ALTER TABLE PRICE ADD PRICE_RENTDAYS INT(2) DEFAULT 3 NOT NULL;

```
## 28. Update the PRICE table to place the values shown in the following table in the PRICE_RENTDAYS attribute.
```sql

UPDATE PRICE SET PRICE_RENTDAYS = 5 
WHERE PRICE_CODE IN (1, 3);

UPDATE PRICE SET PRICE_RENTDAYS = 7 
WHERE PRICE_CODE = 4;

```
## 29. Create a stored procedure named prc_new_rental to insert new rows in the RENTAL table. The procedure should satisfy the following conditions.
a. The membership number will be provided as a parameter.
b. Use a Count () function to verify that the membership number exists in the MEMBERSHIP table. If it does not exist, then a message
should be displayed stating that the membership does not exist and no data should be written to the database.
c. If the membership does exist, then retrieve the membership balance and display a message stating the balance amount as the
previous balance. (For example, if the membership has a balance of $5.00, then display “Previous balance: $5.00”.
d. Insert a new row in the rental table using the sequence created in #42 above to generate the value for RENT_NUM, the current
system date for the value for RENT_DATE, and the membership number provided as the value for MEM_NUM.
AGH TÆKNISKOLINN, 26-11-2018

```sql

DELIMITER //
DROP PROCEDURE IF EXISTS `prc_new_rental`//
CREATE PROCEDURE `prc_new_rental` (
`Param_MEM_NUM` int 
)
BEGIN
	IF (SELECT COUNT(*) 
        FROM MEMBERSHIP 
        WHERE MEM_NUM = Param_MEM_NUM) = 0 THEN
		SELECT "ÞETTA ER EKKI TIL";
    ELSE
		SELECT CONCAT("$", MEM_BALANCE) AS "PERVIOUS BALANCE:" 
        FROM MEMBERSHIP 
        WHERE MEM_NUM = Param_MEM_NUM;
    END IF;


END//
DELIMITER ;

SELECT * FROM Membership;
CALL prc_new_rental(102);


```