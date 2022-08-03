# MYSQL-CHEAT-SHEET
### MySQL command-line client Commands
> Connect to MySQL server using mysql  command-line client with a username and password (MySQL will prompt for a password):
```bash
mysql -u [username] -p;
```
#
> Connect to MySQL Server with a specified database using a username and password:
```bash
mysql -u [username] -p [database];
```
#
>Exit mysql command-line client:
```bash
exit;
```
#
> Export data using mysqldump tool
```bash
mysqldump -u [username] -p [database] > data_backup.sql;
```
#
> To clear MySQL screen console window on Linux, you use the following command:
```bash
mysql> system clear;
```
> Currently, there is no command available on Windows OS for clearing MySQL screen console window.
#
#

####__Working with databases__
> Create a database with a specified name if it does not exist in the database server
```bash
CREATE DATABASE [IF NOT EXISTS] database_name;
```
#
> Use a database or change the current database to another database that you are working with:
```bash
USE database_name;
```
#
> Drop a database with a specified name permanently. All physical files associated with the database will be deleted.
```bash
DROP DATABASE [IF EXISTS] database_name;
```
#
> Show all available databases in the current MySQL database server
```bash 
SHOW DATABASE;
```
#
#
#### __Working with tables__
> Show all tables in a current database.
```bash
SHOW TABLES;
```
#
> Create a new table
```bash
CREATE TABLE [IF NOT EXISTS] table_name(
  column_list
);
```
#
> Add a new column into a table:
```bash
ALTER TABLE table 
ADD [COLUMN] column_name;
```
#
> Drop a column from a table:
```bash
ALTER TABLE table_name
DROP [COLUMN] column_name;
```
#
> Add index with a specific name to a table on a column:
```bash
ALTER TABLE table 
ADD INDEX [name](column, ...);
```
#
> Add primary key into a table:
```bash
ALTER TABLE table_name 
ADD PRIMARY KEY (column_name,...);
```
#
> Remove the primary key of a table:
```bash
ALTER TABLE table_name
DROP PRIMARY KEY;
```
#
> Drop a table:
```bash
DROP TABLE [IF EXISTS] table_name;
```
#
> Show the columns of a table:
```bash
DESCRIBE table_name;
```
#
> Show the information of a column in a table:
```bash
DESCRIBE table_name column_name;
```
#
#
#### __Working with indexes__
> Creating an index with the specified name on a table:
```bash
CREATE INDEX index_name
ON table_name (column,...);
```
#
> Drop an index:
```bash
DROP INDEX index_name;
```
#
> Create a unique index:
```bash
CREATE UNIQUE INDEX index_name 
ON table_name (column,...);
```
#
#
#### __Working with views__
> Create a new view:
```bash
CREATE VIEW [IF NOT EXISTS] view_name 
AS 
  select_statement;
```
#
> Create a new view with the WITH CHECK OPTION:
```bash
CREATE VIEW [IF NOT EXISTS] view_name 
AS select_statement
WITH CHECK OPTION;
```
#
> Create or replace a view:
```bash
CREATE OR REPLACE view_name 
AS 
select_statement;
```
#
> Drop a view:
```bash
DROP VIEW [IF EXISTS] view_name;
```
#
> Drop multiple views:
```bash
DROP VIEW [IF EXISTS] view1, view2, ...;
```
#
> Rename a view:
```bash
RENAME TABLE view_name
TO new_view_name;
```
#
> Show views from a database:
```bash
SHOW FULL TABLES
[{FROM | IN } database_name]
WHERE table_type = 'VIEW';
```
#
#
#### __Working with triggers__
> Create a new trigger:
```bash
CREATE TRIGGER trigger_name
{BEFORE | AFTER} {INSERT | UPDATE| DELETE }
ON table_name FOR EACH ROW
trigger_body;
```
#
> Drop a trigger:
```bash
DROP TRIGGER [IF EXISTS] trigger_name;
```
#
> Show triggers in a database:
```bash
SHOW TRIGGERS
[{FROM | IN} database_name]
[LIKE 'pattern' | WHERE search_condition];
```
#
#
#### __Working with stored procedures__
> Create a stored procedure:
```bash
DELIMITER $$

CREATE PROCEDURE procedure_name(parameter_list)
BEGIN
   body;
END $$

DELIMITER ;
```
#
> Drop a stored procedure:
```bash
DROP PROCEDURE [IF EXISTS] procedure_name;
```
#
> Show stored procedures:
```bash
SHOW PROCEDURE STATUS 
[LIKE 'pattern' | WHERE search_condition];
```
#
#
#### __Working with stored functions__
> Create a new stored function:
```bash
DELIMITER $$
 
CREATE FUNCTION function_name(parameter_list)
RETURNS datatype
[NOT] DETERMINISTIC
BEGIN
 -- statements
END $$
 
DELIMITER ;
```
#
> Drop a stored function:
```bash
DROP FUNCTION [IF EXISTS] function_name;
```
#
> Show stored functions:
```bash
SHOW FUNCTION STATUS 
[LIKE 'pattern' | WHERE search_condition];
```
#
#
#### __Querying data from tables__
> Query all data from a table:
```bash
SELECT * FROM table_name;
```
#
> Query data from one or more column of a table:
```bash
SELECT 
    column1, column2, ...
FROM 
    table_name;
```
#
> Remove duplicate rows from the result of a query:
```bash
SELECT 
    DISTINCT (column)
FROM 
   table_name;
```
#
> Query data with a filter using a WHERE clause:
```bash
SELECT select_list
FROM table_name
WHERE condition;
```
#
> Change the output of the column name using column alias:
```bash
SELECT 
    column1 AS alias_name,
    expression AS alias,
    ...
FROM 
    table_name;
```
#
> Query data from multiple tables using inner join:
```bash
SELECT select_list
FROM table1
INNER JOIN table2 ON condition;
```
#
> Query data from multiple tables using left join:
```bash
SELECT select_list
FROM table1 
LEFT JOIN table2 ON condition;
```
#
> Query data from multiple tables using right join:
```bash
SELECT select_list 
FROM table1 
RIGHT JOIN table2 ON condition;
```
#
> Make a Cartesian product of rows:
```bash
SELECT select_list
FROM table1
CROSS JOIN table2;
```
#
> Counting rows in a table.
```bash
SELECT COUNT(*)
FROM table_name;
```
#
> Sorting a result set:
```bash
SELECT 
    select_list
FROM 
    table_name
ORDER BY 
    column1 ASC [DESC], 
    column2 ASC [DESC];
```
#
> Group rows using the GROUP BY clause.
```bash
SELECT select_list
FROM table_name
GROUP BY column_1, column_2, ...;
```
#
> Filter group using the HAVING clause:
```bash
SELECT select_list
FROM table_name
GROUP BY column1
HAVING condition;
```
#
#
#### __Modifying data in tables__
> Insert a new row into a table:
```bash
INSERT INTO table_name(column_list)
VALUES(value_list);
```
#
> Insert multiple rows into a table:
```bash
INSERT INTO table_name(column_list)
VALUES(value_list1),
      (value_list2),
      (value_list3),
      ...;
```
#
> Update all rows in a table:
```bash
UPDATE table_name
SET column1 = value1,
    ...;
```
#
> Update data for a set of rows specified by a condition in WHERE clause.
```bash
UPDATE table_name
SET column_1 = value_1,
    ...
WHERE condition
```
#
> Update with join
```bash
UPDATE 
    table1, 
    table2
INNER JOIN table1 ON table1.column1 = table2.column2
SET column1 = value1,
WHERE condition;
```
#
> Delete all rows in a table
```bash
DELETE FROM table_name;
```
#
> Delete rows specified by a condition:
```bash
DELETE FROM table_name
WHERE condition;
```
#
> Delete with join
```bash
DELETE table1, table2
FROM table1
INNER JOIN table2
    ON table1.column1 = table2.column2
WHERE condition;
```
#
#
#### __Searching__
> Search for data using the LIKE operator:
```bash
SELECT select_list
FROM table_name
WHERE column LIKE '%pattern%';
```
#
> Text search using a regular expression with RLIKE operator.
```bash
SELECT select_list
FROM table_name
WHERE column RLIKE 'regular_expression';
```
