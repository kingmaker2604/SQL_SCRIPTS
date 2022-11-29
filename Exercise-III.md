# *Exercise-III*

## Question

Consider the relations BOAT, SAILOR and RESERVES. The relation BOAT identifies the features<br>
of a boat such as unique identifier, color and a name. The list of sailors with attributes such as<br>
SailorID, name, age etc., are stored in the relation SAILOR. The sailors are allowed to reserve any<br>
number of boats on any day of the week and the records are to be updated in the RESERVES table.<br>
&ensp;a) Mention the constraints neatly.<br>
&ensp;b) Design the ER diagram for the problem statement<br>
&ensp;c) State the schema diagram for the ER diagram.<br>
&ensp;d) Create the tables, insert suitable tuples and perform the following operations in SQL:<br>
&emsp;1. Obtain the details of the boats reserved by ‘#Sailor_Name’.<br>
&emsp;2. Retrieve the BID of the boats reserved necessarily by all the sailors.<br>
&emsp;3. Find the number of boats reserved by each sailor. Display the Sailor_Name along<br>
&emsp;with the number of boats reserved.<br>
&emsp;4. Identify which boats have the same name as their sailor.<br>
&ensp;e) Create the table, insert suitable tuples and perform the following operations using<br>
&emsp;MongoDB.<br>
&emsp;1. Obtain the number of boats obtained by sailor :#Sailor_Name<br>
&emsp;2. Retrieve boats of color :”#color”<br>
&ensp;f) Write a PL/SQL program to check whether a given number is prime or not.<br>


## d)Create the tables, insert suitable tuples and perform the following operations in SQL:
### Creating entities boat,sailor,reserves
```SQL
CREATE TABLE BOAT(
BOAT_ID VARCHAR2(20),
BOAT_NAME CHAR(20),
BOT_COLOR CHAR(10),
PRIMARY KEY(BOAT_ID));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q21.png?raw=True"></P>

```SQL
CREATE TABLE SAILOR(
SAILOR_ID VARCHAR2(20),
SAILORNAME CHAR(20),
AGE NUMBER(3),
RATING VARCHAR(9),
PRIMARY KEY(SAILOR_ID));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q22.png?raw=True"></P>

```SQL
CREATE TABLE RESERVES(
BOAT_ID VARCHAR2(20) REFERENCES BOAT(BOAT_ID),
SAILOR_ID VARCHAR2(20) REFERENCES SAILOR(SAILOR_ID),
DAY CHAR(10),
PRIMARY KEY(BOAT_ID,SAILOR_ID));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q23.png?raw=True"></P>

### Inserting values into the tables
```SQL
INSERT INTO BOAT
VALUES('&BOAT_ID','&BOAT_NAME','&BOAT_COLOR');
```
```SQL
INSERT INTO SAILOR
VALUES('&SAILOR_ID','&SAILORNAME',&AGE,'&RATING');
```
```SQL
INSERT INTO RESERVES
VALUES('&BOAT_ID','&SAILOR_ID','&DAY');
```
<FIGURE>
<FIGCAPTION>BOAT</FIGCAPTION>
<IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q24.png?raw=True">
<FIGCAPTION>SAILOR</FIGCAPTION>
<IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q25.png?raw=True">
<FIGCAPTION>RESERVES</FIGCAPTION>
<IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q26.png?raw=True">
</FIGURE>


### 1) Obtain the details of the boats reserved by ‘#Sailor_Name’.
```SQL
SELECT *
FROM BOAT
WHERE BOAT_ID IN(SELECT BOAT_ID
                 FROM RESERVES
                 WHERE SAILOR_ID IN (SELECT SAILOR_ID
                                     FROM SAILOR
                                     WHERE SAILORNAME='MANAV'));
```
<P ALIGN="CENTER"><IMG SRC="https://github.com/MXNXV-ERR/SQL_SCRIPTS/blob/main/IMGS/Q1D1.png?raw=True"></P>

### 2) Retrieve the BID of the boats reserved necessarily by all the sailors
```SQL

```