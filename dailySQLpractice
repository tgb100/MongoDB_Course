# SQL_Practice_tgb
tgb's SQL Practice
-- Database Operations for VIT
-- Show existing databases
SHOW DATABASES;

-- Create and use VIT database
CREATE DATABASE IF NOT EXISTS VIT;
USE VIT;

-- Create CSE table with improved structure
CREATE TABLE IF NOT EXISTS CSE (
    s_id INT PRIMARY KEY,
    s_name VARCHAR(30) NOT NULL,
    s_mark INT CHECK (s_mark BETWEEN 0 AND 100),
    s_country VARCHAR(50) DEFAULT 'India'
);

-- Verify table creation
SHOW TABLES;

-- Insert initial data
INSERT INTO CSE (s_id, s_name, s_mark) 
VALUES (70, 'jm', 78);

-- Table structure inspection
DESC CSE;

-- Column modifications
ALTER TABLE CSE 
ADD COLUMN address VARCHAR(200);

ALTER TABLE CSE 
DROP COLUMN address;

ALTER TABLE CSE 
RENAME COLUMN s_country TO s_state;

-- Safe update demonstration
SET SQL_SAFE_UPDATES = 0;
UPDATE CSE 
SET s_state = 'Belgium' 
WHERE s_id = 70;
SET SQL_SAFE_UPDATES = 1;

-- Transaction Practice Database
CREATE DATABASE IF NOT EXISTS practice1;
USE practice1;

CREATE TABLE IF NOT EXISTS Mech (
    s_id INT PRIMARY KEY,
    s_name VARCHAR(25)
);

-- Transaction with savepoints
START TRANSACTION;
INSERT INTO Mech VALUES (101, 'jayanth');
SAVEPOINT A;
UPDATE Mech SET s_id = 102 WHERE s_id = 101;
SAVEPOINT B;
INSERT INTO Mech VALUES (103, 'Karthick');
SAVEPOINT C;
ROLLBACK TO B;
COMMIT;

-- Organization Database Setup
CREATE DATABASE IF NOT EXISTS ORG;
USE ORG;

CREATE TABLE IF NOT EXISTS Worker (
    WORKER_ID INT PRIMARY KEY AUTO_INCREMENT,
    FIRST_NAME VARCHAR(25),
    LAST_NAME VARCHAR(25),
    SALARY INT,
    JOINING_DATE DATETIME,
    DEPARTMENT VARCHAR(25)
);

-- Insert data with corrected date format
INSERT INTO Worker (FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT) VALUES
('Monika', 'Arora', 100000, '2014-02-20 09:00:00', 'HR'),
('Niharika', 'Verma', 80000, '2014-06-11 09:00:00', 'Admin'),
('Vishal', 'Singhal', 300000, '2014-02-20 09:00:00', 'HR'),
('Amitabh', 'Singh', 500000, '2014-02-20 09:00:00', 'Admin'),
('Vivek', 'Bhati', 500000, '2014-06-11 09:00:00', 'Admin'),
('Vipul', 'Diwan', 200000, '2014-06-11 09:00:00', 'Account'),
('Satish', 'Kumar', 75000, '2014-01-20 09:00:00', 'Account'),
('Geetika', 'Chauhan', 90000, '2014-04-11 09:00:00', 'Admin');

-- Enhanced Queries
-- 1. Employees with salary > 200,000 in HR
SELECT * FROM Worker 
WHERE DEPARTMENT = 'HR' AND SALARY > 200000;

-- 2. Salary range query
SELECT * FROM Worker 
WHERE SALARY BETWEEN 200000 AND 500000;

-- 3. Department statistics
SELECT 
    DEPARTMENT,
    COUNT(*) AS employee_count,
    AVG(SALARY) AS avg_salary,
    MAX(SALARY) AS max_salary,
    MIN(SALARY) AS min_salary
FROM Worker
GROUP BY DEPARTMENT
ORDER BY employee_count DESC;

-- 4. Top 2 departments by employee count
SELECT DEPARTMENT, COUNT(*) AS employee_count
FROM Worker
GROUP BY DEPARTMENT
ORDER BY employee_count DESC
LIMIT 2;

-- 5. Department-wise maximum salaries using window functions
SELECT DISTINCT DEPARTMENT,
MAX(SALARY) OVER (PARTITION BY DEPARTMENT) AS max_salary
FROM Worker;

-- 6. Top 3 salaries in Admin department
SELECT * FROM Worker
WHERE DEPARTMENT = 'Admin'
ORDER BY SALARY DESC
LIMIT 3;

CREATE TABLE person1 (
    id INT PRIMARY KEY, 
    lastname VARCHAR(255) NOT NULL UNIQUE, 
    firstname VARCHAR(255) NOT NULL UNIQUE, 
    age INT
);

DESC person1;

INSERT INTO person1 (id, lastname, firstname, age) 
VALUES (1, 'Doe', 'John', 30);


SELECT * FROM person1;

create table category(
c_id int primary key,
c_name varchar(25) not null unique,
c_decrp varchar(250) not null
);

insert into category values (102, 'furnitures', 'it stores all set of wooden items');
select * from category;
desc category;

use org123;
CREATE TABLE Products (
    P_ID int primary key,
    p_Name varchar(250) NOT NULL,
    c_id int ,
    CONSTRAINT c_id FOREIGN KEY (c_id)
    REFERENCES category(c_id)
);
show tables from org123;
desc products;

drop table products;

insert into products values (904, 'Wooden table', null);
select * from products;


select * from category;

delete from category where c_id=101;

drop table category;

USE org123;


CREATE TABLE Student (
    sno INT PRIMARY KEY,
    sname VARCHAR(20),
    age INT

);


INSERT INTO Student(sno, sname,age) 
 VALUES(5,'skit',17),
       (7,'samya',18),
       (6,'samm',16);

SELECT *
FROM Student;

CREATE TABLE Course (
    cno INT PRIMARY KEY,
    cname VARCHAR(20)
);

SELECT *
FROM Course;

INSERT INTO Course(cno, cname) 
 VALUES(101,'c'),
       (102,'c++'),
       (103,'DBMS');

INSERT INTO Course(cno, cname) 
 VALUES(104,'c#'),
       (105,'java'),
       (106,'OS');

CREATE TABLE Enroll (
    sno INT,
    cno INT,
    jdate DATE,
    PRIMARY KEY(sno, cno),
    FOREIGN KEY(sno) REFERENCES Student(sno) ON DELETE CASCADE,
    FOREIGN KEY(cno) REFERENCES Course(cno) ON DELETE CASCADE
);

INSERT INTO Enroll(sno, cno, jdate) 
VALUES (1, 101, '2021-06-05'),
       (1, 102, '2021-06-05'),
       (2, 103, '2021-06-06');

SELECT * FROM Enroll;

DELETE FROM Student WHERE sname = 'Ramya';

SELECT * FROM Student;

SELECT * FROM Enroll;

INSERT INTO Enroll(sno, cno, jdate) 
VALUES(2, 105, "2021/05/05");
select * from enroll;
desc Enroll;

create database saturday;
use saturday;

create table category(
c_id int primary key,
c_name varchar(25) not null unique,
c_decrp varchar(250) not null
);

insert into category values (101, 'electronics', 'it stores all set of electronics items');
select * from category;
desc category;

CREATE TABLE Products (
    P_ID int primary key,
    p_Name varchar(250) NOT NULL,
    c_id int ,
    CONSTRAINT c_id FOREIGN KEY (c_id)
    REFERENCES category(c_id) on delete cascade
);

insert into products values (904, 'INTEL I5 Processor', 101);
select * from products;
delete from category where c_id=101;
select * from category;

CREATE TABLE Colleges (
    college_id INT PRIMARY KEY,
    college_name VARCHAR(50) NOT NULL
);

CREATE TABLE Subjects (
    subject_id INT PRIMARY KEY,
    subject_name VARCHAR(50) NOT NULL,
    college_id INT,
    FOREIGN KEY (college_id) REFERENCES Colleges(college_id) ON DELETE CASCADE
);

CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(50) NOT NULL,
    college_id INT,
    subject_id INT,
    FOREIGN KEY (college_id) REFERENCES Colleges(college_id) ON DELETE CASCADE,
    FOREIGN KEY (subject_id) REFERENCES Subjects(subject_id) ON DELETE CASCADE
);

INSERT INTO Colleges (college_id, college_name) VALUES
    (1, 'VIT Bhopal'),
    (2, 'IIT Indore'),
    (3, 'NIT Warangal');

INSERT INTO Subjects (subject_id, subject_name, college_id) VALUES
    (1, 'Computer Science', 1),
    (2, 'Mathematics', 1),
    (3, 'Physics', 2),
    (4, 'Electrical Engineering', 3);

INSERT INTO Students (student_id, student_name, college_id, subject_id) VALUES
    (1, 'Rahul Sharma', 1, 1),
    (2, 'Priya Jain', 1, 2),
    (3, 'Amit Verma', 2, 3),
    (4, 'Sneha Rao', 3, 4);

SELECT * FROM Colleges;
SELECT * FROM Subjects;
SELECT * FROM Students;

SELECT * FROM Worker 
WHERE SALARY > 200000 AND DEPARTMENT = 'HR';

SELECT * FROM Worker 
WHERE SALARY >= 200000;

SELECT * FROM Worker;

select * from worker where salary >= 200000 and salary <= 500000;

SELECT * FROM Worker
WHERE department = 'Admin' AND salary > 100000
ORDER by salary DESC;

SELECT * FROM Students WHERE s_name LIKE 'A%';
SELECT * FROM Students WHERE s_name LIKE 'd%';

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

CREATE TABLE Bonus (
	WORKER_REF_ID INT,
	BONUS_AMOUNT INT(10),
	BONUS_DATE DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);

INSERT INTO Bonus 
	(WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
		(001, 5000, '16-02-20'),
		(002, 3000, '16-06-11'),
		(003, 4000, '16-02-20'),
		(001, 4500, '16-02-20'),
        
		(002, 3500, '16-06-11');

SELECT * FROM Worker 
WHERE FIRST_NAME NOT IN ('Vipul', 'Satish');

SELECT * FROM Worker 
WHERE FIRST_NAME LIKE '%a';

SELECT * FROM Worker 
WHERE FIRST_NAME LIKE '_____h';

create table vitBhopal (id int primary key, name varchar(20) not null,
department varchar(25) not null);
insert into vitbhopal values (104,'Karthik','cs'),(103,'Arun','cs');

create table vit (id int primary key, name varchar(20) not null,
college varchar(25) not null);
insert into vit values (104,'Karthik','chennai'),(103,'Arun','bhopal');
select * from vit;

select * from vitbhopal;

select name as WinnerOfTheYear from vitbhopal
where id = (select id from vit where college='bhopal');

CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);

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

CREATE TABLE Bonus (
	WORKER_REF_ID INT,
	BONUS_AMOUNT INT(10),
	BONUS_DATE DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);

INSERT INTO Bonus 
	(WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
		(001, 5000, '16-02-20'),
		(002, 3000, '16-06-11'),
		(003, 4000, '16-02-20'),
		(001, 4500, '16-02-20'),
		(002, 3500, '16-06-11');
CREATE TABLE Title (
	WORKER_REF_ID INT,
	WORKER_TITLE CHAR(25),
	AFFECTED_FROM DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);

INSERT INTO Title 
	(WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM) VALUES
 (001, 'Manager', '2016-02-20 00:00:00'),
 (002, 'Executive', '2016-06-11 00:00:00'),
 (008, 'Executive', '2016-06-11 00:00:00'),
 (005, 'Manager', '2016-06-11 00:00:00'),
 (004, 'Asst. Manager', '2016-06-11 00:00:00'),
 (007, 'Executive', '2016-06-11 00:00:00'),
 (006, 'Lead', '2016-06-11 00:00:00'),
 (003, 'Lead', '2016-06-11 00:00:00');
 
 CREATE TABLE vitbhopal (
  id INT PRIMARY KEY,
  name VARCHAR(20) NOT NULL,
  department VARCHAR(25) NOT NULL
);

INSERT INTO vitbhopal (id, name, department) 
VALUES (222, 'Karthik', 'cs'), (312, 'Arun', 'cs');

SELECT * FROM vitbhopal;

CREATE TABLE viteee (
  id INT PRIMARY KEY, 
  name VARCHAR(20) NOT NULL,
  college VARCHAR(25) NOT NULL
);

INSERT INTO viteee (id, name, college) 
VALUES (104, 'Karthik', 'chennai'), (103, 'Arun', 'bhopal');

SELECT * FROM viteee;

SELECT DEPARTMENT, COUNT(*) AS DEPARTMENT_COUNT 
FROM Worker
GROUP BY DEPARTMENT
HAVING COUNT(*) < 5;


SELECT *
FROM (
  SELECT *
  FROM Worker
  ORDER BY WORKER_ID DESC
  LIMIT 5
) AS subquery
ORDER BY WORKERID;

CREATE TABLE student12 (
    s_id INT PRIMARY KEY,
    s_name VARCHAR(25) NOT NULL,
    s_department VARCHAR(25) NOT NULL
);


INSERT INTO student12 VALUES 
(1001, 'Jayanth', 'ECE'),
(1002, 'Praveen', 'CSE'),
(1003, 'Logesh', 'Mech'),
(1006, 'Karthick', 'Aero'),
(1007, 'Mahesh', 'Civil');


SELECT * FROM student12;

DROP TABLE IF EXISTS vit;


CREATE TABLE VIT (
    s_id INT PRIMARY KEY,
    s_cgpa VARCHAR(5) NOT NULL
);


INSERT INTO VIT VALUES 
(1001, '7.2'),
(1002, '8.6'),
(1007, '9.25');

SELECT * FROM VIT;

SELECT * FROM  STUDENT CROSS JOIN VIT ;

SELECT * 
FROM Worker 
WHERE WORKER_ID IN (SELECT DISTINCT Manager_ID FROM Worker WHERE Manager_ID IS NOT NULL);


SELECT W.* 
FROM Worker W
INNER JOIN Manager M ON W.WORKER_ID = M.Manager_ID;

CREATE DATABASE ORG;
USE ORG;
CREATE TABLE Worker (
	WORKER_ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
	FIRST_NAME CHAR(25),
	LAST_NAME CHAR(25),
	SALARY INT(15),
	JOINING_DATE DATETIME,
	DEPARTMENT CHAR(25)
);

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

CREATE TABLE Bonus (
	WORKER_REF_ID INT,
	BONUS_AMOUNT INT(10),
	BONUS_DATE DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);

INSERT INTO Bonus 
	(WORKER_REF_ID, BONUS_AMOUNT, BONUS_DATE) VALUES
		(001, 5000, '16-02-20'),
		(002, 3000, '16-06-11'),
		(003, 4000, '16-02-20'),
		(001, 4500, '16-02-20'),
		(002, 3500, '16-06-11');
CREATE TABLE Title (
	WORKER_REF_ID INT,
	WORKER_TITLE CHAR(25),
	AFFECTED_FROM DATETIME,
	FOREIGN KEY (WORKER_REF_ID)
		REFERENCES Worker(WORKER_ID)
        ON DELETE CASCADE
);

INSERT INTO Title 
    (WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM) VALUES
    (001, 'Manager', '2016-02-20 00:00:00'),
    (002, 'Executive', '2016-06-11 00:00:00'),
    (008, 'Executive', '2016-06-11 00:00:00'),
    (005, 'Manager', '2016-06-11 00:00:00'),
    (004, 'Asst. Manager', '2016-06-11 00:00:00'),
    (007, 'Executive', '2016-06-11 00:00:00'),
    (006, 'Lead', '2016-06-11 00:00:00'),
    (003, 'Lead', '2016-06-11 00:00:00');
 
-- 1. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending.
-- 2. Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.
-- 3. Write an SQL query to print details of workers excluding first names, “Vipul” and “Satish” from Worker table.
-- 4. Write an SQL query to print details of the Workers whose FIRST_NAME ends with ‘h’ and contains six alphabets.
-- 5. Write an SQL query to fetch the count of employees working in the department ‘Admin’.
-- 6. Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.
-- 7. Write an SQL query to fetch the no. of workers for each department in the descending order.
-- 8. Write an SQL query to determine the 5th highest salary without using TOP or limit method.
-- 9  Write an SQL query to fetch the list of employees with the same salary.

SELECT * FROM Worker  
ORDER BY FIRST_NAME ASC;

SELECT * FROM Worker  
ORDER BY FIRST_NAME ASC, DEPARTMENT DESC;

SELECT * FROM Worker  
WHERE FIRST_NAME NOT IN ('Vipul', 'Satish');

SELECT * FROM Worker  
WHERE FIRST_NAME LIKE '_____h';

SELECT COUNT(*) AS Admin_Count  
FROM Worker  
WHERE DEPARTMENT = 'Admin';

SELECT FIRST_NAME, LAST_NAME  
FROM Worker  
WHERE SALARY BETWEEN 50000 AND 100000;

SELECT DEPARTMENT, COUNT(*) AS Worker_Count  
FROM Worker  
GROUP BY DEPARTMENT  
ORDER BY Worker_Count DESC;

SELECT DISTINCT Salary
FROM Worker w1
WHERE 4 = (
    SELECT COUNT(*)
    FROM Worker w2
    WHERE w2.Salary > w1.Salary
);

SELECT w1.WORKER_ID, w1.FIRST_NAME, w1.LAST_NAME, w1.SALARY
FROM Worker w1
JOIN Worker w2
ON w1.SALARY = w2.SALARY AND w1.WORKER_ID <> w2.WORKER_ID
ORDER BY w1.SALARY, w1.WORKER_ID;

SELECT DEPARTMENT
FROM Worker
GROUP BY DEPARTMENT
HAVING COUNT(WORKER_ID) < 3;

Connection JAVA SQL.





