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
