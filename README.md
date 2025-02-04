# SQL_Practice_tgb
tgb's SQL Practice
-- Show existing databases
SHOW DATABASES;

-- Create a new database named 'VIT'
CREATE DATABASE VIT;

-- Use the 'VIT' database
USE VIT;

-- Create a table 'CSE'
CREATE TABLE CSE (
    s_id INT,
    s_name VARCHAR(30),
    s_mark INT
);

-- Show all tables in the 'VIT' database
SHOW TABLES FROM VIT;

-- Select all records from the 'CSE' table
SELECT * FROM CSE;

-- Insert data into the 'CSE' table 
INSERT INTO CSE (s_id, s_name, s_mark) VALUES (70, 'jm', 78);

-- Describe the table structure 
DESC CSE;

-- Add a new column 'address' to the 'CSE' table
ALTER TABLE CSE ADD COLUMN address VARCHAR(200);

-- Drop the 'address' column from the 'CSE' table
ALTER TABLE CSE DROP COLUMN address;

-- Add a new column 's_country' to the 'CSE' table
ALTER TABLE CSE ADD COLUMN s_country VARCHAR(200);

-- Rename column 's_country' to 's_state' in the 'CSE' table
ALTER TABLE CSE RENAME COLUMN s_state TO s_country ;

UPDATE CSE 
SET s_country = 'India' 
WHERE s_id = 70;

--- With out "changing" 

SET SQL_SAFE_UPDATES = 0;

UPDATE CSE  
SET s_country = 'Belgium'  
WHERE s_id = 80;

SET SQL_SAFE_UPDATES = 1; -- (Re-enable safe mode after update)

update CSE 
set s_name ='Ashirwad'
where s_id=70;



create database practice1;
use practice1;
SELECT * FROM  practice1; -- i can not run this command 
create table Mech(s_id int,s_name varchar(25));
START TRANSACTION;
insert into Mech values (101,'jayanth');





create database practice1;
use practice1;
create table Mech(s_id int,s_name varchar(25));
START TRANSACTION;
insert into Mech values (101,'jayanth');
SAVEPOINT A;
update mech set s_id=102 where s_id=101;
SAVEPOINT B;
insert into Mech values (103,'Karthick');
select * from mech;
SAVEPOINT C;
select * from mech;
ROLLBACK TO B;
select * from mech;
commit;



CREATE DATABASE ORG123;
SHOW DATABASES;
USE ORG123;

CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);

SHOW TABLES FROM  ORG123 ;
desc worker;

SET SQL_SAFE_UPDATES = 0;


SET SQL_SAFE_UPDATES = 1; -- (Re-enable safe mode after update)

select * from org123;
INSERT INTO Worker 
	(WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
		(001, 'Monika', 'Arora', 100000, '14-02-20 09.00.00', 'HR'),
		(002, 'Niharika', 'Verma', 80000, '14-06-11 09.00.00', 'Admin'),
		(003, 'Vishal', 'Singhal', 300000, '14-02-20 09.00.00', 'HR'),
		(004, 'Amitabh', 'Singh', 500000, '14-02-20 09.00.00', 'Admin'),
		(005, 'Vivek', 'Bhati', 500000, '14-06-11 09.00.00', 'Admin'),
		(006, 'Vipul', 'Diwan', 200000, '14-06-11 09.00.00', 'Account'),
		(007, 'Satish', 'Kumar', 75000, '14-01-20 09.00.00', 'Account'),
		(008, 'Geetika', 'Chauhan', 90000, '14-04-11 09.00.00', 'Admin');



SELECT * FROM Worker 
WHERE SALARY > 200000 AND DEPARTMENT = 'HR';

SELECT * FROM Worker 
WHERE SALARY >= 200000;

SELECT * FROM Worker;



SELECT * FROM Worker;

select * from worker where salary >= 200000 and salary <= 500000;

select first_name from worker where salary between 200000 and 400000 and worker_id  in (1,2,3,4,5);

desc worker;

select * from worker  where salary between 200000 and 400000 and worker_id  in (1,2,3,4,5);



SELECT MIN(column_name)
FROM table_name
WHERE condition ;

SELECT MAX(column_name)
FROM table_name
WHERE condition;



SELECT * FROM Worker 
WHERE DEPARTMENT = 'HR' 
ORDER BY SALARY ASC 
LIMIT 1;

SELECT * FROM Worker W1
WHERE NOT EXISTS (
    SELECT 1 FROM Worker W2
    WHERE W2.DEPARTMENT = W1.DEPARTMENT AND W2.SALARY > W1.SALARY
);




SELECT W1.SALARY AS MAX_SALARY
FROM Worker W1, Worker W2
WHERE W1.DEPARTMENT = 'Account' 
AND W1.SALARY >= W2.SALARY
AND W2.DEPARTMENT = 'Account'
GROUP BY W1.SALARY
HAVING COUNT(W2.SALARY) = (SELECT COUNT(*) FROM Worker WHERE DEPARTMENT = 'Account');


SELECT W1.SALARY AS MIN_SALARY
FROM Worker W1, Worker W2
WHERE W1.DEPARTMENT = 'Account' 
AND W1.SALARY <= W2.SALARY
AND W2.DEPARTMENT = 'Account'
GROUP BY W1.SALARY
HAVING COUNT(W2.SALARY) = (SELECT COUNT(*) FROM Worker  WHERE DEPARTMENT = 'Account');

SELECT W1.SALARY AS MAX_SALARY
FROM Worker W1, Worker W2
WHERE W1.DEPARTMENT = 'Account' 
AND W1.SALARY >= W2.SALARY
AND W2.DEPARTMENT = 'Account'
GROUP BY W1.SALARY
HAVING COUNT(W2.SALARY) = (SELECT COUNT(*) FROM Worker WHERE DEPARTMENT = 'Account');


SELECT COUNT(column_name)
FROM table_name
WHERE condition;

-- AVG() Syntax

SELECT AVG(column_name)
FROM table_name
WHERE condition;

-- SUM() Syntax

SELECT SUM(column_name)
FROM table_name
WHERE condition;


SELECT MAX(SALARY) AS MAX_SALARY
FROM (
    SELECT MAX(SALARY) AS SALARY FROM Worker WHERE DEPARTMENT = 'Account'
    UNION
    SELECT MAX(SALARY) AS SALARY FROM Worker WHERE DEPARTMENT = 'HR'
) AS res_salary;


Limit to 1000 rows
FROM worker;
select * from worker where department='Admin' order by salary desc limit 3; 
select department, count(department) as total_employees from worker where department = 'HR' or department="account' group by department;


SELECT DEPARTMENT, COUNT(*) AS Count
FROM Worker
GROUP BY DEPARTMENT
ORDER BY Count DESC
LIMIT 2;


select department, count(department) as total_employees from worker
group by department
order by total_employees desc Limit 2;
