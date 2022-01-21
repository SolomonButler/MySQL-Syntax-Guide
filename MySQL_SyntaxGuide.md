MySQL Syntax Guide - Sol Butler

1. How to login into mysql from terminal.

- First SSH to the preferred server.

- Then run the command:
  mysql -u root -p.

- You will then be prompted to enter your password, and you're in.

2. How to SHOW USERS.

- To see all users run this command:
  SELECT user FROM mysql.user;

- Remember to end all SQL command lines with an semicolon;.

3. How to CREATE USERS.

- To add a new user, run this command:
  CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';

- Alternatively you can use this command:
  CREATE USER 'username'@'ip_address' IDENTIFIED BY 'password';

- Replacing 'username and 'password' with their respective values.

4. How to GRANT PRIVILEGES, SHOW granted privileges and REVOKE.

- To grant ALL privileges to a user, run this command:
  GRANT ALL PRIVILEGES ON _._ TO 'username'@'localhost';

- To grant limited permission to a user run this command:
  GRANT ALL PRIVILEGES ON 'database_name.table_name' TO 'username'@'localhost'

- To show granted privileges run this commend:
  SHOW GRANTS FOR 'username'@'localhost';

- To revoke to a user run this command:
  REVOKE privilege_type ON database.table FROM 'user_name'@'localhost';

- Privilege types can be, SELECT, INSERT, UPDATE, DELETE, INDEX, CREATE, ALTER, DROP, GRANT OPTION, or ALL.

5. How to SHOW, DELETE & CREATE DATABASES & SELECT DATABASES.

- To see all databases run this command:
  show databases;

- To delete a database run this command:
  DORP DATABASE database_name;

- To create a database run this command:
  CREATE DATABASE database_name;

- To select a database run this command:
  USE database_name;

6. How to CREATE a TABLE with Columns and their data types.

- Tables are used to store and organize data, tables are made up of Columns and Rows. where the Column specifies the type of data and the Rows contain the data its self.

- Creating a table in MySQL looks like this:
  CREATE TABLE table_name(
  column1_name data_type constraint(s),
  column2_name data_type constraint(s),
  column3_name data_type constraint(s)
  );
  This will create a table with 3 columns and 0 rows, rows will be created when data is entered.

- Data types that used in the table are listed below:
  INT - Used to whole numeric values.
  DECIMAL - Used to store numeric values with exact decimal values.
  CHAR(255) - Used to store character strings with a fixed_length up to 255 characters.
  VARCHAR(255) - Used to store character strings up to 65,535 characters.
  TEXT - Used to store character strings up to 65.535 without having to specify a character count.
  DATE - Used to store date values formatted by YYY-MM-DD.
  DATETIME - Used to store date and time values formatted by YYY-MM-DD HH:MM:SS.
  TIMESTAMP - Used to store a timestamp value in the number of seconds since the Unix epoch, and automatically update.

- Constraints in MySQL are restrictions placed on the entire table or table columns to limit the type of data that the table or columns can store, they are declared when creating a table, and help to maintain accuracy, cardinality and integrity of data.

- Here are some of the most commonly used constraints and what they do:
  NOT NULL - Limits that column to not accepting NULL values, when entering data into a row there must be a value entered into this column.

  PRIMARY KEY - Assigns the column to have unique values that can be used to identify a row in a table by not allowing two rows on the table to have the same primary key as well as no NULL values.

  UNIQUE - Restricts the column to contain unique values, or non-repeating values, similar to PRIMARY KEY except multiple columns can have the constraint UNIQUE. Both UNIQUE and PRIMARY key help with Cardinality.

  DEFAULT - Used to assign a column to have a default value if the column is left empty when inserting values.

  FOREIGN KEY - A constraint used to establish and enforce the relationship between the data in two or more tables. Also known as the referencing key it matches the data from one tables to that of the primary key in another table.

  CHECK - Restricts the values being inserted into the row by the pre-determined condition.

  AUTO_INCREMENT - Usually places along side the PRIMARY KEY, this constraint automatically increments up by 1 every time a new row in created. This is very useful for maintaining uniqueness of data values.

7. How to SHOW, DELETE & DROP Tables.

- To drop a table run this command:
  DROP table_name;

- To show all tables run this command:
  SHOW tables;

- To delete a table run this command:
  DROP TABLE table_name;

8. How to Insert ROWS & RECORDS (single and multiple)
The INSERT does exactly what it says, it inserts one or more rows into the table as well as values.

- Single Insertion:
Step ONE start the query with:
  INSERT INTO.

Step TWO specify the table which you want to insert a row into:
  table_name

Step THREE a comma-separated, bracket enclosed list of column names of which you want to inset a value into their row: - Note. You do not need to specify columns with the constraint AUTO_INCREMENT when doing this.
  (column1, column2, column3)

Step FOUR use the VALUE clause to specify that the latter is going to be the value for the specified columns:
  VALUE

Step FIVE, a comma-separated list of values enclosed in brackets, matching the number of columns specified in step THREE:
  ("value1", "value2", "value3");

All of this together makes an insertion query that looks like this:
  INSERT INTO table_name(column1, column2, column3) VALUES ("value1", "value2", "value3");

- Multiple insertion:
Very similar to single insertion, follow all the steps listed above. Once you're listing the values, you can create another comma-separated list of values enclosed in brackets. Each list of values is separated by a comma, this should look like this:
  INSERT INTO table_name(column1, column2, column3) VALUES 
  ("value1", "value2", "value3"), 
  ("value1", "value2", "value3"), 
  ("value1", "value2", "value3");

Note. When creating an insert query, the columns and values must be listed in the same order of which they appear in the table.

9. How to SELECT with the WHERE Clause.

- WHERE clause is used to filter and extract records or values that fulfill a specified condition. 

Take for example there was a table of the words Countries and Cities, and you want to retrieve all the Cities that reside in Canada, a query using the SELECT and WHERE clauses would look like this:
  SELECT * FROM Countries WHERE Country = "Canada";

In the example above im SELECTING all Cities from the table Countries where the Country equals Canada.

10. How to SELECT with the WHERE Clause using a range.
- Very similar to the example above, you can also include the AND, IN and, BETWEEN clauses to refine the query even further, the addition of these would look like this:
  SELECT * FROM Countries WHERE Population BETWEEN 600,000 AND 1,000,000;
  SELECT * FROM Countries WHERE City IN ("Canada", "USA");

The first query will select all Countries where the population is between the pre-determined conditions.

The second query will select all Cities that reside within Canada AND USA.

11. How to DELETE an individual ROW.
- To delete an individual row in a table run this command:
  DELETE FROM table_name WHERE (condition);

Be careful when running this query, if you do not specify the condition with the WHERE clause all data in the table will be deleted.

12. How to UPDATE a ROW.
- To update a row in MySQL run this command:
  UPDATE table_name SET column_name1 = "New Value", column_name2 = "New Value" WHERE condition;

In the above example you will be updating the values of the columns where the condition is met.

13. How to add a new column and modify it
- To add a column run this command:
  ALTER TABLE table_name ADD column_name constraint(s);

This will add a column with the name specified and constraints specified when creating query.

- To delete a column run this command:
  ALTER TABLE table_name DROP COLUMN column_name:

This will delete the column specified.

14. How to Order by and use Distinct.
- ORDER BY is used to sort the results of a query by ascending (ASC) or descending (DESC) values. ORDER BY clause looks like this:
  SELECT column1, column2, ... FROM table_name ORDER BY column_name1, column_name2 ASC;

- SELECT DISTINCT statement is used to return only distinct (unique) values, this is especially useful when finding the COUNT (sum) of unique values in a column. SELECT DISTINCT clause looks like this:
  SELECT DISTINCT column_name FROM table_name;

15. How to Concatenate Columns.
- CONCAT() function in MySQL allows the user to concatenate (add, or merge) values from two or more columns into one. Concatenating in MySQL looks like this:
  SELECT column_name CONCAT(column1, column2, ...) AS existing_column FROM table_name;

- CONCAT_WS() function is used when concatenating strings, it automatically adds a separator between values but is written the same as CONCAT() function.

16. How to Select Distinct Rows.
- To select a distinct row run this command:
  SELECT DISTINCT column1, column2, ... FROM table_name;

17. How to use LIKE to Search.
- The LIKE operator is used in conjunction with the WHERE clause to define and return a value that meets a specific pattern or not.

- There are two symbols often used when using the LIKE clause:
  % represents zero, one, or multiple characters.
  _ represents a single character.

- Syntax when using the LIKE clause looks like this:
  WHERE Name LIKE 'a%' Finds any values that start with "a".
  WHERE Name LIKE '%a' Finds any values that end with "a".
  WHERE Name LIKE '%or%' Finds any values that have "or" in any position.
  WHERE Name LIKE '_r%' Finds any values that have "r" in the second position.
  WHERE Name LIKE 'a_%' Finds any values that start with "a" and are at least 2 characters in length.
  WHERE Name LIKE 'a__%' Finds any values that start with "a" and are at least. 3 characters in length.
  WHERE Name LIKE 'a%o'	Finds any values that start with "a" and ends with "o".


- To run a query using the LIKE operator should look like this:
  SELECT column1, column2 FROM table_name WHERE column_name LIKE patters:

18. How to select using IN.
- The IN operator allows the user to specify multiple values in a WHERE clause, rather than using multiple OR conditions.

- The syntax for using the IN operator in a query looks like this:
  SELECT column_name(s) FROM table_name WHERE column_name IN (value1, value2, ...);

- Selecting all skis from their brand name would look like this:
  SELECT * FROM Inventory WHERE Skis IN ('Line', 'Armada');

This will select all skis with the brand Line and Armada in the Skis column in the Inventory table.

19. How to Create & Remove Index.
- The CREATE INDEX, and CREATE UNIQUE INDEX statements are used to speed up the retrieving of data from a table by assigning an index value to rows in the specified column(s).

- CREATE INDEX syntax looks like this:
  CREATE INDEX index_name ON table_name (column1, column2, ...);

This will allow duplicate index values.

- CREATE UNIQUE INDEX syntax looks like this:
  CREATE UNIQUE INDEX index_name ON table_name (column1, column2, ...);

This will enforce unique values for all index values.

- To remove an index from a column looks like this:
  DROP INDEX index_name ON table_name;
Or like this:
  ALTER TABLE table_name DROP INDEX index_name;

20. Create Two Tables demonstrating a one to many relationship that shows a PK & FK.

CREATE TABLE Orders(
  orderID INT AUTO_INCREMENT,
  productID INT NOT NULL,
  order_date DATE NOT NULL,
  PRIMARY KEY (orderID),
  FOREIGN KEY (productID) REFERENCES Products(productID)
); 

CREATE TABLE Products(
  productID INT AUTO_INCREMENT,
  product_category VARCHAR(255),
  product_name VARCHAR(255),
  PRIMARY KEY (productID)
);

- This enforces the relationship between the primary key (productID) in the table(Products), with the column (productID) in table (Orders).

21. How to use Inner Join.
- The inner join keyword is used to select and return records from two or three tables that have matching values, this will select any matching values from all rows in the specified columns of the specified tables, and hide all other values.

- The syntax for INNER JOIN looks like this:
  SELECT column_name(s) 
  FROM table1 
  INNER JOIN table2 
  ON table1.column_name = table2.column_name;

This will return all values that match in table1 and the specified column, with table2 in the specified column.

- This can also be done on 3 or more tables, the syntax looks like this:
  SELECT table1.column_name, table2.column_name, table3.column_name 
  FROM ((table1 
  INNER JOIN table2 ON table1.column_name = table2.column_name)
  INNER JOIN table3 ON table1.column_name = table3.column_name);

This will return all matching values from table1.specified-column, with table2.specified-column, with table3.specified-column.

22. How to JOIN Multiple Tables.
- We have covered INNER JOIN above, but there are more ways of combining tables, these are the JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN.

- The JOIN clause is used to combine rows from two or more tables based on a related column and its data type.
The syntax looks like this:
  SELECT t1.col, t3.col
  FROM ((table1
  JOIN table2 ON table1.primary key = table2.foreign key)
  JOIN table3 ON table2.primary key = table3.foreign key);

This will create a temporary table with the combined data from table1 and table2, which is joined to table3.

- The LEFT JOIN, or sometimes call LEFT OUTER JOIN keyword returns all data from table1 and only values from table2 that match those in table1. 
The syntax looks like this:
  SELECT column_name(s)
  FROM table1
  LEFT JOIN table2
  ON table1.column_name = table2.column_name;

This will returns all values of table1 regardless, and only values from table2 specified column that match values in the column specified in table1.

- The RIGHT JOIN, or sometimes call RIGHT OUTER JOIN keyword works the exact same as LEFT JOIN, except it will return all values from the specified column in table2 regardless, and only values from the specified column from table1 that match values the values in the specified column in table2.

See above for syntax:

- The FULL JOIN, FULL OUTER JOIN keyword returns all values from both tables, incorporating a WHERE clause to refine the search.
The syntax for FULL JOIN looks like this:
  SELECT column_name(s)
  FROM table1
  FULL OUTER JOIN table2
  ON table1.column_name = table2.column_name
  WHERE condition;

This will return all values from both tables that meet the specified condition.