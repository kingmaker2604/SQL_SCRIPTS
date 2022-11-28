# *Exercise-I*

## Question
Consider an Employee with a social security number (SSN) working on multiple projects with<br>
definite hours for each. Each Employee belongs to a Department. Each project is associated with<br>
some domain areas such as Database, Cloud and so on. Each Employee will be assigned to some<br>
project. Assume the attributes for Employee and Project relations.<br>
 &ensp;a) Mention the constraints neatly.<br>
 &ensp;b) Design the ER diagram for the problem statement<br>
 &ensp;c) State the schema diagram for the ER diagram.<br>
 &ensp;d) Create the tables, insert suitable tuples (min 6 each) and perform the following operations<br>
 &ensp;in SQL<br>
 &emsp;1. Obtain the details of employees assigned to “Database” project.<br>
 &emsp;2. Find the number of employees working in each department with department<br>
 &emsp;details.<br>
 &emsp;3. Update the Project details of Employee bearing SSN = #SSN to ProjectNo =<br>
 &emsp;#Project_No and display the same.<br>
 &emsp;4. Retrieve the employee who has not been assigned more than two projects.<br>
 &ensp;e) Create the table, insert suitable tuples and perform the following operations using<br>
 &ensp;MongoDB<br>
 &emsp;1. List all the employees of Department named #Dept_name.<br>
 &emsp;2. Name the employees working on Project Number :#Project_No<br>
 &ensp;f) Write a program that gives all employees in Department #number a 15% pay increase.<br>
 &ensp;Display a message displaying how many employees were awarded the increase.<br>


 ## d)
 ### Creating table employee,project,assign 
```SQL
CREATE TABLE EMPLOYEE(
SSN VARCHAR2(10) NOT NULL PRIMARY KEY,
NAME CHAR(10),
DEPT_NO VARCHAR2(10));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/DESCEMPLOYEE.png?raw=True"></P>

```SQL
CREATE TABLE PROJECT(
PROJ_NO VARCHAR2(10) NOT NULL PRIMARY KEY,
PROJ_AREA VARCHAR2(10));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/DESCPROJECT.png?raw=True"></P>

<BR>

```SQL
CREATE TABLE ASSIGN(
SSN VARCHAR2(10) REFERENCES EMPLOYEE(SSN),
PROJ_NO VARCHAR2(10) REFERENCES PROJECT(PROJ_NO));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/DESCASSIGN.png?raw=True"></P>
<BR>

### Inserting values into the tables
```SQL
INSERT INTO EMPLOYEE
VALUES('&SSN','&NAME','&DEPT_NO');
```
```SQL
INSERT INTO PROJECT
VALUES('&PROJ_NO','&PROJ_AREA');
```
```SQL
INSERT INTO ASSIGN
VALUES('&SSN','&PROJ_AREA');
```

<FIGURE>
<FIGCAPTION>EMPLOYEE</FIGCAPTION>
<IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/SELECTALLFROMEMPLOYEE.png?raw=True">
<FIGCAPTION>PROJECT</FIGCAPTION>
<IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/SELECTALLFROMPROJECT.png?raw=True">
<FIGCAPTION>ASSIGN</FIGCAPTION>
<IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/SELECTALLFROMASSIGN.png?raw=True">
</FIGURE>


### 1)Obtain the details of employees assigned to “Database” project.
```SQL
SELECT * 
FROM EMPLOYEE
WHERE SSN IN (SELECT SSN
              FROM ASSIGN
              WHERE PROJ_NO IN(SELECT PROJ_NO
                               FROM PROJECT
                               WHERE PROJ_AREA='DATABASE'));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q1D1.png?raw=True"></P>

### 2)Find the number of employees working in each department with department <BR>details
```SQL
SELECT DEPT_NO,COUNT(SSN)
FROM EMPLOYEE
GROUP BY DEPT_NO;
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q1D2.png?raw=True"></P>

### 3) Update the Project details of Employee bearing SSN = #SSN to ProjectNo =#Project_No and display the same.<br>
```SQL
UPDATE ASSIGN
SET PROJ_NO='P5'
WHERE SSN = 'S001';
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q1D3.png?raw=True"></P>

### 4) Retrieve the employee who has not been assigned more than two projects.
```SQL
SELECT SSN,COUNT(PROJ_NO)
FROM ASSIGN
GROUP BY SSN
HAVING COUNT(PROJ_NO)<=1;
```
*FOR THIS EXAMPLE I TOOK LESS THAN ONE SO WE GET TO KNOW THE DIFFRENCE*
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q1D4.png?raw=True"></P>


## e) Create the table, insert suitable tuples and perform the following operations using MongoDB
Creating table in mongo
```javascript
db.createCollection("Employee")
```
Inserting tuples in mongo
```javascript
db.Employee.insertOne({"SSN":1234,"Name":"Sita","Dept_no":2,"DeptName":'ISE',"Proj_no":"1"})
```
```javascript
 db.Employee.insertOne({"SSN":1235,"Name":"John","Dept_no":1,"DeptName":'MECH',"Proj_no": 2})
```
To view contents
```javascript
db.Employee.find().pretty()
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q1EO.png?raw=True"></P>
