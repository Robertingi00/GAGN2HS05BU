## 1-	Create database called your_kenetala_company, use company.SQL file locate in inna. Suppose we want to keep track of the total salaries of employees working for each department
```sql

create database 0907002780_Company;

use 0907002780_Company;

```

## 2-	Create new table call deptsal as shown in the bellow.

```sql

create table deptsal
(
	dept_no int not null,
    totalsalary int,
    constraint FOREIGN KEY deptsal(dept_no) REFERENCES dept(dept_no)
    
);

insert into deptsal values
(1,0),
(2,0),
(3,0),
(4,0);

```


 

## 3-	Follow the steps to update the total salaries of employees for each department.
### Step 1: 
Change the delimiter (i.e., terminating character) of SQL statement from semicolon (;) to something else (e.g., //) So that you can distinguish between the semicolon of the SQL statements in the procedure and the terminating character of the procedure definition
### Step 2: 
1.	Define a procedure called updateSalary which takes as input a department number. 
2.	The body of the procedure is an SQL command to update the totalsalary column of the deptsal table. 
3.	Terminate the procedure definition using the delimiter you had defined in step 1 (//)
### Step 3: 
Change the delimiter back to semicolon (;)
### Step 4: 
Call the procedure to update the totalsalary for each department
### Step 5: 
Show the updated total salary in the deptsal table
```sql
delimiter //
SET SQL_SAFE_UPDATES = 0;
drop procedure IF EXISTS updateDalary;

CREATE PROCEDURE updateDalary (dep_num INT) 
BEGIN 
	update deptsal 
    set totalsalary = (select sum(salary) from employee where dept_no = dep_num)
    where dept_no = dep_num;

END; // 

delimiter ;

call updateDalary(2);

```

## 4-	Write an SQL statement to display the list of stored procedures
```sql
select * from deptsal;
```
## 5-	Write an SQL to remove the stored procedure
```sql
DROP PROCEDURE updateDalary;
```
## 6-	Write an SQL statement that resets the totasalary to zero?
```sql
update deptsal 
set totalsalary = 0;
```

## 7-	Suppose we want to update all the rows in deptsal simultaneously, using while loop write an SQL procedure that updates all the rows?

```sql

delimiter //
SET SQL_SAFE_UPDATES = 0 //
drop procedure IF EXISTS updateDalary_loop //

CREATE PROCEDURE updateDalary_loop () 
BEGIN
	DECLARE i INT;
    DECLARE counter INT;
	SET i = 1;
    set counter = (select count(dept_no) from dept);
	while (i <= counter)DO
		update deptsal 
		set totalsalary = (select sum(salary) from employee where dept_no = i)
		where dept_no = i;
        set i = i + 1;
	End WHILE;

END; // 

delimiter ;

call updateDalary_loop();


```


## 8-	Create a stored procedure that updates all the rows simultaneously, using cursors?
```sql
delimiter //
drop procedure IF EXISTS up_salary_cursor //
SET SQL_SAFE_UPDATES = 0 //
CREATE PROCEDURE up_salary_cursor ()
BEGIN

	DECLARE Done bool default false;
    DECLARE current_dept_no int default 0;
    
	DECLARE dept_PK CURSOR FOR select dept_no from dept;
    DECLARE CONTINUE HANDLER FOR NOT FOUND SET Done = true;
	
    
	OPEN dept_PK;
      repeat
    
	      FETCH dept_PK INTO current_dept_no;
          call updateDalary(current_dept_no);
      until Done
	  end repeat;
    CLOSE dept_PK;
    
END; // 

delimiter ;
```
## 9-	Create a procedure that will raise the salary of all employees by 10% .

```sql
delimiter //
drop procedure IF EXISTS raise //
SET SQL_SAFE_UPDATES = 0 //
CREATE PROCEDURE raise () 
BEGIN

	update employee
    set salary = salary * 1.10;
	
END; // 

delimiter ;

call raise();
```
## 10-	Create a trigger that will update the total salary of all employee as follows:
### a-	If employee is hired, test by inserting new employee record.
```sql
delimiter //
create trigger update_salary
after insert on employee
for each row 
begin      
         if new.dept_no is not null then		  
                call updateDalary_loop();  
         end if;      
end ; //
delimiter ;

insert into employee values 
(9, 'Clark Mgr', null, 4, 450000);
```
### b-	If employee is fired, test by deleting an employee record.

```sql
delimiter //
create trigger update_salary_after_fierd
after DELETE on employee
for each row 
begin      
         if old.dept_no is not null then		  
                call updateDalary_loop();  
         end if;      
end ; //
delimiter ;

delete from employee where emp_id = 9;
select *from employee;
select * from deptsal;
```
