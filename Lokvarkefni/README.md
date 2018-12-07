# Lokaverkefni GAGN2HS05BU
## 1. Write the SQL code to create the table structures for the entities shown in Figure P7.44. The structures should contain the attributes specified in the ERD. Use data types that are appropriate for the data that will need to be stored in each attribute. Enforce primary key and foreign key constraints as indicated by the ERD.

```sql


```
## 2. The following tables provide a very small portion of the data that will be kept in the database. This data needs to be inserted into thedatabase for testing purposes. Write the INSERT commands necessary to place the following data in the tables that were created in Problem 1.
```sql


```
## 3. Write a query to display the movie title, movie year, and movie cost for all movies that contain the word “hope” anywhere in the title. Sort the results in ascending order by title. (The results are shown in figure P7.55.)
```sql



```
## 4. Write a query to display the movie title, movie year, and movie genre for all action movies. (The results are shown in Figure P7.56.)
```sql

```
## 5. Write a query to display the movie number, movie title, and movie cost for all movies with a cost greater than $40. (The results are shown in Figure P7.57.)
```sql

```
## 6. Write a query to display the movie number, movie title, movie cost, and movie genre for all movies that are either action or comedy movies and that have a cost that is less than $50. Sort the results in ascending order by genre. (The results are shown in Figure P7.58.)
```sql

```
## 7. Write a query to display the movie number, and movie description for all movies where the movie description is a combination of the movie title, movie year, and movie genre with the movie year enclosed in parentheses. (The results are shown in Figure P7.59.)
```sql

```
## 8. Write a query to display the movie genre and the number of movies in each genre. (The results are shown in Figure P7.60.)
```sql

```
## 9. Write a query to display the average cost of all of the movies. (The results are shown in Figure P7.61.)
```sql

```
## 10. Write a query to display the movie genre and average cost of movies in each genre. (The results are shown in Figure P7.62.)
```sql

```
## 11. Write a query to display the movie title, movie genre, price description, and price rental fee for all movies with a price code. (The results are shown in Figure P7.63.)
```sql

```
## 12. Write a query to display the movie genre and average price rental fee for movies in each genre that have a price. (The results are shown in Figure P7.64.)
```sql

```
## 13. Write a query to display the movie title, movie year, and the movie cost divided by the price rental fee for each movie that has a price to determine the number of rentals it will take to break even on the purchase of the movie. (The results are shown in Figure P7.65.)
```sql

```
## 14. Write a query to display the movie title and movie year for all movies that have a price code. (The results are shown in Figure P7.66.)
```sql

```
## 15. Write a query to display the movie title, movie year, and movie cost for all movies that have a cost between $44.99 and $49.99. (The results are shown in Figure P7.67.)
```sql

```
## 16. Write a query to display the movie title, movie year, price description, and price rental fee for all movies that are in the genres family, comedy, or drama. (The results are shown in Figure P7.68.)
```sql

```
## 17. Write a query to display the minimum balance, maximum balance, and average balance for memberships that have a rental. (The results are shown in Figure P7.71.)
```sql

```
## 18. Write a query to display the membership name (concatenate the first name and last name with a space between them into a single column), membership address (concatenate the street, city, state, and zip codes into a single column with spaces. (The results are shown in Figure P7.72.)
```sql

```
## 19. Write a query to display the rental number, rental date, video number, movie title, due date, and return date for all videos that were returned after the due date. Sort the results by rental number and movie title. (The results are shown in Figure P7.73.)
```sql

```
## 20. Write a query to display the rental number, rental date, video number, movie title, due date, return date, detail fee, and number of days past the due date that the video was returned for each video that was returned after the due date. Sort the results by rental number and movie title. (The results are shown in Figure P7.74.)
```sql

```
## 21. Write a query to display the rental number, rental date, movie title, and detail fee for each movie that was returned on or before the due date. (The results are shown in Figure P7.75.)
```sql

```
## 22. Write a query to display the membership number, last name, first name, and total rental fees earned from that membership. (The results are shown in Figure P7.76.) The total rental fee is the sum of all of the detail fees (without the late fees) from all movies that the membership has rented.
```sql

```
## 23. Write a query to display the movie number, movie genre, average movie cost of movies in that genre, movie cost of that individual movie, and the percentage difference between the average movie cost and the individual movie cost. (The results are shown in Figure P7.77.) (Note: The percentage difference is calculated as the cost of the individual movie minus the average cost of movies in that genre, divided by the average cost of movies in that genre multiplied by 100. For example, if the average cost of movies in the “family” genre is $25, if a given family movie cost $26, then the calculation would be ((26 – 25) / 25 * 100), which would work out to be 4.00%. This indicates that this movie costs 4% more than the average family movie.)
```sql

```
## 24. Alter the DETAILRENTAL table to include a derived attribute named DETAIL_DAYSLATE to store integers up to 3 digits. The attribute should accept null values.
```sql

```
## 25. Alter the VIDEO table to include an attribute named VID_STATUS to store character data up to 4 characters long. The attribute should not accept null values. The attribute should have a constraint to enforce the domain (“IN”, “OUT”, and “LOST”) and have a default value of “IN”.
```sql

```
## 26. Update the VID_STATUS attribute of the VIDEO table using a subquery to set the VID_STATUS to “OUT” for all videos that have a null value in the DETAIL_RETURNDATE attribute of the DETAILRENTAL table.
```sql

```
## 27. Alter the PRICE table to include an attribute named PRICE_RENTDAYS to store integers up to 2 digits. The attribute should not accept null values, and should have a default value of 3.
```sql

```
## 28. Update the PRICE table to place the values shown in the following table in the PRICE_RENTDAYS attribute.
```sql

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

```