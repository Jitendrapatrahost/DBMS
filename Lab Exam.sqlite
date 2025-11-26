Q1.
  -- Create Student table (DDL)
CREATE TABLE Student (
    roll_no INT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    branch VARCHAR(20),
    age INT CHECK(age > 16),
    email VARCHAR(40) UNIQUE
);

---------------------------------------------------------------------------------------
-- Insert / Update / Delete using DML
INSERT INTO Student VALUES (101, 'Rohan', 'CSE', 19, 'rohan@gmail.com');
INSERT INTO Student VALUES (102, 'Priya', 'ECE', 18, 'priya@gmail.com');
INSERT INTO Student VALUES (103, 'Amit', 'ME', 20, 'amit@gmail.com');

UPDATE Student SET branch = 'IT' WHERE roll_no = 102;

DELETE FROM Student WHERE roll_no = 103;

---------------------------------------------------------------------------------------
-- TCL Commands

START TRANSACTION;

UPDATE Student SET age = 21 WHERE roll_no = 101;

SAVEPOINT S1;

INSERT INTO Student VALUES (104, 'Sneha', 'Civil', 19, 'sneha@gmail.com');

ROLLBACK TO S1;

COMMIT;


---------------------------------------------------------------------------------------
-- DCL Commands

GRANT SELECT, UPDATE ON Student TO userA;

REVOKE UPDATE ON Student FROM userA;


---------------------------------------------------------------------------------------
-- Employee Table + View + Partition + Lock

CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    salary INT CHECK(salary > 10000),
    email VARCHAR(40) UNIQUE
);


---------------------------------------------------------------------------------------


CREATE VIEW EmpView AS
SELECT emp_id, name, salary FROM Employee;


---------------------------------------------------------------------------------------
-- Partitioning (Range based on Salary)

ALTER TABLE Employee
PARTITION BY RANGE (salary) (
    PARTITION p1 VALUES LESS THAN (25000),
    PARTITION p2 VALUES LESS THAN (50000),
    PARTITION p3 VALUES LESS THAN (100000)
);


---------------------------------------------------------------------------------------
-- Locking Update

LOCK TABLE Employee WRITE;

UPDATE Employee SET salary = salary + 2000 WHERE emp_id = 1;

UNLOCK TABLES;

---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

Q2.
--Create Employee Table
CREATE TABLE Employee (
    emp_id INT PRIMARY KEY,
    name VARCHAR(30) NOT NULL,
    dept VARCHAR(20),
    salary INT CHECK(salary > 15000),
    email VARCHAR(40) UNIQUE
);


---------------------------------------------------------------------------------------
-- Insert / Update / Delete

INSERT INTO Employee VALUES (201, 'Aman', 'HR', 30000, 'aman@cmp.com');
INSERT INTO Employee VALUES (202, 'Divya', 'IT', 45000, 'divya@cmp.com');
INSERT INTO Employee VALUES (203, 'Karan', 'Finance', 35000, 'karan@cmp.com');
INSERT INTO Employee VALUES (204, 'Sara', 'IT', 25000, 'sara@cmp.com');

UPDATE Employee SET salary = 50000 WHERE emp_id = 202;

DELETE FROM Employee WHERE emp_id = 204;

---------------------------------------------------------------------------------------
-- TCL

START TRANSACTION;

SAVEPOINT P1;

UPDATE Employee SET dept = 'Admin' WHERE emp_id = 201;

ROLLBACK TO P1;

COMMIT;

---------------------------------------------------------------------------------------
-- DCL

GRANT INSERT, SELECT ON Employee TO empUser;

REVOKE INSERT ON Employee FROM empUser;


---------------------------------------------------------------------------------------
-- View + Partition + Lock

CREATE VIEW EmpView AS
SELECT emp_id, name, salary FROM Employee;


---------------------------------------------------------------------------------------


ALTER TABLE Employee
PARTITION BY RANGE (salary) (
    PARTITION e1 VALUES LESS THAN (30000),
    PARTITION e2 VALUES LESS THAN (60000)
);

---------------------------------------------------------------------------------------


LOCK TABLE Employee READ;

SELECT * FROM Employee;

UNLOCK TABLES;

---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

Q3.
-- Create Courses table
CREATE TABLE Courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(40) NOT NULL,
    credit INT CHECK(credit BETWEEN 2 AND 5),
    instructor VARCHAR(30) DEFAULT 'TBD'
);


---------------------------------------------------------------------------------------
-- Insert / Update / Delete

INSERT INTO Courses VALUES (1, 'DBMS', 4, 'Dr. Sharma');
INSERT INTO Courses VALUES (2, 'OOP', 3, 'TBD');
INSERT INTO Courses VALUES (3, 'CN', 5, 'Dr. Verma');

UPDATE Courses SET instructor = 'Dr. Sen' WHERE course_id = 2;

DELETE FROM Courses WHERE course_id = 3;

---------------------------------------------------------------------------------------
-- TCL

BEGIN;

SAVEPOINT C1;

UPDATE Courses SET credit = 5 WHERE course_id = 1;

ROLLBACK TO C1;

COMMIT;

---------------------------------------------------------------------------------------
-- DCL

GRANT SELECT ON Courses TO admin1;

GRANT ALL PRIVILEGES ON Courses TO faculty1;

REVOKE ALL PRIVILEGES ON Courses FROM faculty1;


---------------------------------------------------------------------------------------
-- View + Locking + Partition

CREATE VIEW CourseView AS
SELECT course_id, course_name, credit FROM Courses;


---------------------------------------------------------------------------------------
-- Lock during update

LOCK TABLE Courses WRITE;

UPDATE Courses SET credit = 4 WHERE course_id = 1;

UNLOCK TABLES;

---------------------------------------------------------------------------------------
-- Simple partition on credit

ALTER TABLE Courses
PARTITION BY RANGE (credit) (
    PARTITION c1 VALUES LESS THAN (4),
    PARTITION c2 VALUES LESS THAN (6)
);
