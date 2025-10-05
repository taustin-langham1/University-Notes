That is there will be questions that require you to write MongoDB and MySQL scripts in the form of DML and DDL.


db.users.find()
db.users.find({"name":1})

1. DDL (Data Definition Language) - Structure Operations
	1. CREATE
	2. ALTER
	3. DROP
	4. TRUNCATE

2. DML (Data Manipulation Language)
	1. INSERT
	2. UPDATE
	3. DELETE
	4. SELECT/QUERY


##### **DDL QUESTIONS (DDL IS ABOUT DEFINIGN THE DATABSE)**

NOTES:

			MY SQL:                             MongoDB

Create DB          CREATE DATABASE dbname;                           use dbname 

Insert                  INSERT INTO table VALUES (...);                     db.collection.insertOne({...})      

Query                  SELECT * FROM table WHERE conditions;     db.collection.find({conditions})   

Update                UPDATE table SET... WHERE...;               db.collection.updateOne({filter}, {$set:{....}})                
Delete                  TELETE FROM table WHERE.....;                    db.collection.deleteOne({conditions})

Join                      JOIN clauses                                                  $lookup





CREATE DATABASE school;

CREATE TABLE students(
	
id INT AUTO_INCREMENT PRIMARY KEY
name VARCHAR(100) NOT NULL,
age INT,
enrollment date DATE
);

ALTER TABLE students
ADD COLUMN email VARCHAR(255) UNIQUE;



##### **DML (DML IS ABOUT MANIPULATING DATABASE)**

NOTES:

INSERT INTO Students(sid, name, login, age, gpa)
VALUES (53688, 'thomas', austinla@lancaster.ac.uk, 21, idk)
![[Pasted image 20250517151413.png]]
DELETE
FROM Students S
WHERE S.name = 'Jones'


![[Pasted image 20250517151413.png]]


Query: Find names of sailors who Reserved boat number 103

**SELECT** sname **FROM** Sailors, Reserves **WHERE** Sailors.sid=Reserves.sid AND Reserves.bid=103


TASK 4:
write the SQL queries for the given Relational Schema

**EMPLOYEE(NAME, SSN, BDATE, ADDRESS, SALARY, SUPERSSN, DNO)**

**DEPARTMENT(DNAME, DNUMBER, MGRSSN, MGRSTARTDATE)**

**DEPT_LOCATIONS(DNUMBER, DLOCATION)**

**PROJECT(PNAME, PNUMBER, PLOCATION, DNUM)**

**WORKSON(SSN, PNUMBER, HOURS)**

**DEPENDENT(SSN, DEPENDENT_NAME, SEX, BDATE, RELATIONSHIP)**




**Q1) Retrieve the rows from the employee**


SELECT * FROM employee;


**Q2) Retrieve salaries of employees who are living in the**
**address "Lancaster."**


SELECT salary FROM employee WHERE address="Lancaster";

**Q3) Retrieve the employees' names in a department located in**
**"London."**

SELECT name FROM employee, DEPT_LOCATIONS WHERE
employee.DNO= DEPT_LOCATIONS.DNUMBER AND
DEPT_LOCATIONS.DLOCATION="London"; 


here it seems to use DNO as the referenced key when inside DEP_LOCATIONS, and uses the probably key DNUMBER to then  query DEPT_LOCATIONS.DLOCATION="London";

**Q4) Retrieve the names of employees who work on all projects.**


SELECT name FROM employee, PROJECT WHERE
employee.DNO= PROJECT.PNUMBER AND
PROJECT.PNAME=*;



TASK 2

- Create the ER Diagram, write the Relational Schema with ICs, and create the British Airways (BA) database using MySQL. BA has several planes. Each plane has a unique chassis number, capacity, a Boolean value indicating the plane has Business-Class Option (1 foryes, 0 for no), and range (in km's). BA has captains. Each Captain has a unique licence code, age, and phone number. BA has several routes; each has a unique route_id, distance (in km), and Source andbDestination as text values.
- A captain may SERVE on many routes and can caption many planes. Likewise, a plane may be SERVED by Many captains.




JUST SQL HERE:


CREATE TABLE BA_Captain(LisenceCode INTEGER, PRIMARY KEY(Lisence Code));

CREATE TABLE Routes (route_id INTEGER, Distance INTEGER, )