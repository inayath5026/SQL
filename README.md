# CREATE DB

- CREATE DATABASE db_name;
- CREATE DATABASE IF NOT EXIST db_name; --if not exist

# DELETE DB

- DROP DATABASE db_name;
- DROP DATABASE IF EXIST db_name; --if exist

# USING DB

- USE db_name;

# SHOW DB & TABLES

- SHOW DATABASES;
- SHOW TABLES;

# CREATE TABLE

- CREATE TABLE table_name(
  column_name1 datatype constraint,
  column_name2 datatype constraint,
  column_name3 datatype constraint
  );

# INSERT VALUES

- INSERT INTO table_name VALUES(val1, val2, val3);

- INSERT INTO table_name
  (column1,column2)
  VALUES
  (val1, val2, val3),
  (val1, val2, val3),
  (val1, val2, val3); --for multiple rows

# SQL CONSTRAINTS

- NOT NULL - columns cannot have null a value
- UNIQUE - all values in column should be unique
- PRIMARY KEY - makes column unique and not null, only used for one column in a table
- DEFAULT - sets the column with default value
- CHECK - it can limit the values allowed in column

# PRIMARY KEY SYNTAX

- columnName datatype PRIMARY KEY
- PRIMARY KEY(columnName)
- PRIMARY KEY(columnName1,columnName2) --for combination of columns

# FOREIGN KEY SYNTAX

- FOREIGN KEY (column_name) references referencing_table_name(column_name)
  ON DELETE CASCADE
  ON UPDATE CASCADE

# DEFAULT

- sets the column with default value
- salary INT DEFAULT 200000

# CHECK

- CONSTRAINT constraint_name CHECK (cond AND age>=18)
- age INT CHECK (age>=18) --another way

# SELECT

- SELECT column1,column2,... FROM table_name; --from specific columns
- SELECT * FROM table_name; --from all columns
- SELECT DISTINCT column_names FROM table_name; --returns only different values of columns

# WHERE clause

- to define some conditions
- SELECT col1,col2 FROM table_name
  WHERE conditions;

# OPERATORS

- Arithmetic : +, -, *, /, %
- Comparison : =, !=, >, >=, <, <=
- Logical : AND, OR, NOT, IN, BETWEEN, LIKE, ANY, ALL
- Bitwise : &, |

# LIMIT

- limit the number of rows to be returned
- SELECT * FROM table_name LIMIT 4;
- SELECT * FROM table_name
  WHERE city = "Hyderabad"
  LIMIT 6;

# ORDER BY clause

- To sort in ASC or DESC order
- SELECT * FROM table_name
  ORDER BY column_name ASC/DESC;

- SELECT * FROM student
  ORDER BY marks DESC;

# AGGREGATE FUNCTIONS

- Aggregate functions perform calculations on set of values and returns single value.

- COUNT()
- MAX()
- MIN()
- SUM()
- AVG()

# GROUP BY clause

- Groups rows that have the same values into summary rows.
- It collects data from multiple records and groups the result by one or more columns.
- Generally we use GROUP BY with some AGGREGATE functions.

- SELECT city, COUNT(roll_no)
  FROM student
  GROUP BY city; --It Groups into cities and then returns COUNT of students present in each city

# HAVING clause

- Similar to WHERE clause i.e. applies some condition on rows.
- Used when we want apply any condition after GROUPING.

- SELECT city, COUNT(roll_no)
  FROM student
  GROUP BY city
  HAVING COUNT(roll_no) >= 2; --Condition on city GROUPS

# TURNING OFF SAFE MODE in SQL

- SET SQL_SAFE_UPDATES=0;

# UPDATE

- UPDATE table_name
  SET column_name = val
  WHERE column_name = val;

- UPDATE student
  SET grade = 'O'
  WHERE grade = 'A';

# DELETE

- DELETE FROM table_name
  WHERE condition;

- DELETE FROM student
  WHERE marks <= 40;

# TABLE RELATED QUERIES

- ALTER column

> ALTER TABLE table_name
> ADD COLUMN column_name datatype constraint;

- DROP column

> ALTER TABLE table_name
> DROP COLUMN column_name;

- RENAME table

> ALTER TABLE table_name
> RENAME TO new_table_name;

- RENAME column_name

> ALTER TABLE table_name
> CHANGE COLUMN old_column_name new_column_name new_datatype new_constraint;

- MODIFY column (datatype/constraint)

> ALTER TABLE table_name
> MODIFY column_name new_datatype new_constraint;

# TRUNCATE

- Deletes all the table data, where as DROP TABLE Deletes the whole table

- TRUNCATE TABLE table_name;

# JOINS

- Join is used to combine rows from two or more tables, based on a related column between them.

# INNER JOIN

- Returns records that have matching values in both tables.

- SELECT column(s)
  FROM table_A
  INNER JOIN table_B
  ON table_A.column = table_B.column;

- SELECT *
  FROM student as s
  INNER JOIN course as c
  ON s.id = c.id;

# LEFT JOIN

- Returns all the records from the left table, and the matched records from the right table.

- SELECT column(s)
  FROM table_A
  LEFT JOIN table_B
  ON table_A.column_name = table_B.column_name;

- SELECT student.id,name,course
  FROM student
  LEFT JOIN course
  ON student.id = course.id;

# RIGHT JOIN

- Returns all the records from the right table, and the matched records from the left table.

- SELECT column(s)
  FROM table_A
  RIGHT JOIN table_B
  ON table_A.column_name = table_B.column_name;

- SELECT student.id,name,course
  FROM student
  RIGHT JOIN course
  ON student.id = course.id;

# FULL JOIN

- Combining both tables completely and also returns matching records from both tables.

- LEFT JOIN
  UNION
  RIGHT JOIN;

- SELECT *
  FROM student
  LEFT JOIN course
  ON student.stu_id = course.stu_id

  UNION

  SELECT *
  FROM student
  RIGHT JOIN course
  ON student.stu_id = course.stu_id;

# LEFT EXCLUSIVE JOIN

- SELECT *
  FROM student
  LEFT JOIN course
  ON student.stu_id = course.stu_id
  WHERE course.stu_id IS NULL

# RIGHT EXCLUSIVE JOIN

- SELECT *
  FROM student
  RIGHT JOIN course
  ON student.stu_id = course.stu_id
  WHERE student.stu_id IS

# SELF JOIN

- The table is joined with itself.

- SELECT column(s)
  FROM table_A as a
  JOIN table_A as b
  ON a.column_name = b.column_name;

# UNION

- It is used to combine the result-set of two or more SELECT statements.
- Gives UNIQUE records.

- SELECT column(s) from table_A
  UNION 
  SELECT column(s) from table_B;

- SELECT column(s) from table_A
  UNION ALL 
  SELECT column(s) from table_B ; --Returns duplicate values also.

# VIEWS

- A view is virtual table based on the result-set of SQL statement.

- CREATE VIEW view_name AS
  SELECT column(s) FROM table_name;

- CREATE VIEW view1 AS
  SELECT roll_no, name FROM student;

- SELECT * FROM view1;
- DROP VIEW view1;