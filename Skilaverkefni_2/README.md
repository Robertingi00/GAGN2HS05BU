# Skilaverkefni 2:       
                                                                         
## Use Northwind database to answer the following questions: 
## BASIC QUERIES:
### 1.	Write a query to get Product name and quantity/unit.
```sql
SELECT ProductName, UnitsInStock FROM Products;
```

___
### 2.	 Write a query to get current Product list (Product ID and name).
```sql
SELECT ProductID, ProductName FROM Products ORDER BY ProductID;
```

___
### 3.	Write a query to get discontinued Product list (Product ID and name).
```sql
SELECT ProductID, ProductName FROM Products WHERE Discontinued = 1 ORDER BY ProductID;
```

___
### 4.	Write a query to get most expense and least expensive Product list (name and unit price).
```sql
SELECT ProductID, ProductName, UnitPrice FROM Products ORDER BY UnitPrice DESC;
```

___
### 5.	Write a query to get Product list (id, name, unit price) where current products cost less than $20.
```sql
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE UnitPrice < 20 ORDER BY UnitPrice DESC;
```

___
### 6.	 Write a query to get Product list (id, name, unit price) where products cost between $15 and $25.
```sql
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE UnitPrice BETWEEN 15 AND 25 ORDER BY UnitPrice DESC;
```

___
### 7.	Write a query to get Product list (name, unit price) of above average price
```sql
SELECT ProductName, UnitPrice FROM Products WHERE UnitPrice > (SELECT AVG(UnitPrice) FROM Products) ORDER BY UnitPrice DESC;
```

___
### 8.	Write a query to get Product list (name, unit price) of ten most expensive products.
```sql
SELECT DISTINCT ProductName, UnitPrice FROM Products AS a WHERE 10 >= (select count(DISTINCT  UnitPrice) FROM Products AS b WHERE b.UnitPrice >= a.UnitPrice) ORDER BY UnitPrice DESC;
```

___
### 9.	Write a query to count current and discontinued products.
```sql
SELECT COUNT(ProductID) FROM Products WHERE Discontinued = 1 ORDER BY ProductID;
```

___
### 10.	 Write a query to get Product list (name, units on order , units in stock) of stock is less than the quantity on order.
```sql
SELECT ProductName, UnitsOnOrder, UnitsInStock FROM Products WHERE UnitsOnOrder > UnitsInStock;
```

___
## Use HumanResources database to answer the following questions:
## SUB-QUERIES:
### 1.	Write a query to find the name (first_name, last_name) and the salary of the employees who have a higher salary than the employee whose last_name='Bull'.
```sql
SELECT FIRST_NAME, LAST_NAME FROM employees WHERE SALARY >(SELECT SALARY FROM employees WHERE LAST_NAME = 'Bull');
```

___
### 2.	Write a query to find the name (first_name, last_name) of all employees who works in the IT department.
```sql
SELECT FIRST_NAME, LAST_NAME FROM employees WHERE DEPARTMENT_ID = (SELECT DEPARTMENT_ID FROM departments WHERE DEPARTMENT_NAME = 'IT');
```

___
### 3.	Write a query to find the name (first_name, last_name) of the employees who have a manager and worked in a USA based department.
```sql
SELECT FIRST_NAME, LAST_NAME FROM employees WHERE MANAGER_ID IN (SELECT DEPARTMENT_ID FROM departments WHERE LOCATION_ID IN (SELECT LOCATION_ID FROM locations WHERE COUNTRY_ID = 'US'));
```

___
### 4.	Write a query to find the name (first_name, last_name) of the employees who are managers.
```sql
SELECT FIRST_NAME, LAST_NAME FROM employees WHERE EMPLOYEE_ID IN (SELECT MANAGER_ID FROM departments);
```

___
### 5.	Write a query to find the name (first_name, last_name), and salary of the employees whose salary is greater than the average salary.
```sql
SELECT FIRST_NAME, LAST_NAME, SALARY FROM employees WHERE SALARY > (SELECT AVG(SALARY) FROM employees) ORDER BY SALARY DESC;
```

___
## JOIN
### 1.	Write a query to find the addresses (location_id, street_address, city, state_province, country_name) of all the departments. Hint : Use NATURAL JOIN
```sql
SELECT d.DEPARTMENT_ID, l.LOCATION_ID, l.STREET_ADDRESS, l.CITY, c.COUNTRY_NAME FROM departments AS d NATURAL JOIN locations AS l NATURAL JOIN countries AS c;
```

___
### 2.	Write a query to find the name (first_name, last name), department ID and name of all the employees
```sql
SELECT e.FIRST_NAME, e.LAST_NAME, d.DEPARTMENT_ID FROM employees AS e JOIN departments AS d ON d.DEPARTMENT_ID = E.DEPARTMENT_ID;
```

___
### 3.	 Write a query to find the name (first_name, last_name), job, department ID and name of the employees who works in London. 
```sql
SELECT e.FIRST_NAME, e.LAST_NAME, e.DEPARTMENT_ID, l.City FROM employees AS e JOIN departments AS d ON d.DEPARTMENT_ID = E.DEPARTMENT_ID JOIN jobs AS j ON e.JOB_ID=J.JOB_ID JOIN locations AS L ON D.LOCATION_ID = l.LOCATION_ID WHERE l.CITY = 'London';
```

___
### 4.	Write a query to find the employee id, name (last_name) along with their manager_id and name (last_name).
```sql
SELECT e.EMPLOYEE_ID, e.LAST_NAME, d.MANAGER_ID, M.LAST_NAME AS Manager FROM employees AS e JOIN departments AS d ON e.DEPARTMENT_ID = d.DEPARTMENT_ID JOIN employees AS m ON d.MANAGER_ID = m.EMPLOYEE_ID WHERE(e.EMPLOYEE_ID != m.EMPLOYEE_ID);
```

___
### 5.	Write a query to find the name (first_name, last_name) and hire date of the employees who was hired after 'Jones'.
```sql
SELECT FIRST_NAME, LAST_NAME, HIRE_DATE FROM employees WHERE HIRE_DATE > (select HIRE_DATE FROM employees WHERE LAST_NAME = 'Jones');
```

___
### 6.	Write a query to get the department name and number of employees in the department.
```sql
SELECT d.DEPARTMENT_NAME, COUNT(e.EMPLOYEE_ID) AS EMPLOYEES FROM employees AS e JOIN departments AS d ON d.DEPARTMENT_ID = E.DEPARTMENT_ID group by d.department_name;
```

___
