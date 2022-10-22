# SQL_SCRIPTS
CREATE:
      USED TO CREATE A NEW EMPTY TABLE
      SYNTAX:
      create table tablename(attr1 datatype1,attr2 datatype 2......);
      EXAMPLE:
      create table student(
      usn varchar2(20) not null primary key,
      name char(20),
      age number(10),
      gender char(3));

INSERT:
      USED TO INSERT NEW TUPLES OR VALUES INTO THE TABLE
      SYNTAX:
      insert into tablename values(value1,value2,......);
      EXAMPLE:
      REFERING TO INSERT THERE ARE TWO KINDS OF METHODS TO ENTER THE VALUES.

      TYPE1:
      insert into student values('1MS20IS090','KRISHNA',19,'M');

      TYPE2:
      insert into student values('&usn','&name',&age,&gender);
      enter the value for usn:1MS20IS090
      enter the value for name:KRISHNA
      enter the vakue for age:19
      enter the value for gender:M

DESCRIPTION:
      USED TO KNOW THE DESCRIPTION OF THE TABLE
      SYNTAX:
      desc table tablename;
      EXAMPLE:
      desc table student;

SELECT:
      USED TO RETRIEVE THE REQUIRED COLUMN VALUES FROM THE TABLE
      SYNTAX:
      select column names from tablename;
      EXAMPLE:
      HERE TOO WE HAVE TWO KINDS

      TYPE1:
      SELECT THE REQUIRED COLUMNS.
      select name,usn from student;

      TYPE2:
      SELECT EVERY COLUMN FROM THE TABLE.
      select * from student;

DELETE:
      USED TO DELETE AN EXISTING TUPLE FROM THE TABLE
      SYNTAX:
      delete from tablename where condition;
      EXAMPLE:
      delete from student 
      where usn='1MS20IS090';
      
      HERE WHERE CLAUSE IS USED TO DENOTE WHICH TUPLE WE ARE ACTUALLY ASKING THE COMPILER TO DELETE.
      
DROP:
      USED TO DROP AN ENTIRE TABLE FROM THE DATABASE
      SYNTAX:
      drop table tablename;
      EXAMPLE:
      drop table student;
      
ALTER:
      USED TO ALTER THE ATTRIBUTES OF THE TABLE.ALTER USES SOME KEYWORDS TO ALTER THE TABLE.
      i) ADD: to add a new attribute to the existing table
      ii) MODIFY: to modify the already existing attribute.
      
      SYNTAX:
      alter table tablename add/modify column_name datatype;
      EXAMPLE:
      1. alter table student
         add dept_id varchar2(20);
      2. alter table student
         modify usn number(10);

UPDATE:

      
      
