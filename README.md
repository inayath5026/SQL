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
  (val1, val2, val3);  --for multiple rows

# SQL CONSTRAINTS
 
- NOT NULL - columns cannot have null a value
- UNIQUE - all values in column should be unique
- PRIMARY KEY - makes column unique and not null, only used for one column in a table

# PRIMARY KEY SYNTAX

- columnName datatype PRIMARY KEY
- PRIMARY KEY(columnName)
- PRIMARY KEY(columnName1,columnName2) --for combination of columns

# FOREIGN KEY SYNTAX

- FOREIGN KEY (column_name) references referencing_table_name(column_name)
