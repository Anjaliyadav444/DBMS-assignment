# DBMS-assignment

Assignment-1

Business Requirement:

1. Create a customer table which comprises of these columns – ‘customer_id’, ‘first_name’, ‘last_name’, ‘email’, ‘address’, ‘city’,’state’,’zip’

2. Insert 5 new records into the table

3. Select only the ‘first_name’ & ‘last_name’ columns from the customer table

4. Select those records where ‘first_name’ starts with “G” and city is ‘San Jose’

Solution:

1. Create a customer table which comprises of these columns – ‘customer_id’, ‘first_name’, ‘last_name’, ‘email’, ‘address’, ‘city’,’state’,’zip’

CREATE TABLE: We know that a table comprises of rows and columns. So while creating tables we have to provide all the information to SQL about the names of the columns, type of data to be stored in columns, size of the data.

CREATE TABLE Customer (customer_id INT,first_name VARCHAR (20),last_name VARCHAR(20),
email VARCHAR (30),address VARCHAR (80),City VARCHAR (20),State VARCHAR (20),Zip INT)

2. Insert 5 new records into the table.

insert a single record or multiple records into a table. While inserting a row, if the columns are not specified, it means that vales are added for all of the columns of the table resulting addition of a single row. 

INSERT INTO Customer
VALUES (1209276,'Joel','Varghese','JoelVarghese01@gmail.com','23 nd Floor, Bhagwati Krupa Bldg,  Police Court Lane, Fort',
 ' Mumbai',' Maharashtra',400001),
 (101,'Viay','Venkat','VijayVenkat@gmail.com','4262  Gambler Lane','San Jose','California',95106),
 (102,'Greyson','Gavin','GreysonGavini@gmail.com','2266  Lee Avenue','Camden','New Jersey',08102),
 (103,'Nagesh','Siva','NageshSiva@gmail.com','1533  Thomas Street','Schaumburg','Illinois',60173),
 (104,'Graham','Griffin','GrahamGriffin@gmail.com','4678  Oakmound Road','San Jose','California',95101)

3. Select only the ‘first_name’ & ‘last_name’ columns from the customer table

4. Select those records where ‘first_name’ starts with “G” and city is ‘San Jose’

SELECT Statement:  A SELECT statement retrieves zero or more rows from one or more database tables or database views. In most applications, SELECT is the most commonly used data manipulation language (DML) command.

WHERE: A WHERE clause in SQL specifies that a SQL Data Manipulation Language (DML) statement should only affect rows that meet specified criteria. ... In brief SQL WHERE clause is used to extract only those results from a SQL statement, such as: SELECT, INSERT, UPDATE, or DELETE statement.   

SELECT first_name,last_name
 FROM Customer
 WHERE first_name LIKE 'G%' AND City ='San Jose'


* * *
Assignment-2

Business Requirement:

1. Create an ‘Orders’ table which comprises of these columns – ‘order_id’, ‘order_date’, ‘amount’, ‘customer_id’

2. Make an inner join on ‘Customer’ & ‘Order’ tables on the ‘customer_id’ column

3. Make left and right joins on ‘Customer’ & ‘Order’ tables on the ‘customer_id’ column

4. Update the ‘Orders’ table, set the amount to be 100 where ‘customer_id’ is 3.

Solution:

1. Create an ‘Orders’ table which comprises of these columns – ‘order_id’, ‘order_date’, ‘amount’, ‘customer_id’

CREATE TABLE Orders (Order_id INT,Order_date DATE,Amount INT, customer_id INT)

INSERT INTO Orders
VALUES (256,'2015-11-05',350, 101),(257,'2015-11-07',156,105),(258,'2015-11-08',100,007),
(260,'2015-11-11',500, 104),(261,'2015-11-12',700,003),(262,'2015-11-13',900,102)

2. Make an inner join on ‘Customer’ & ‘Order’ tables on the ‘customer_id’ column

INNER JOIN: Inner Join clause in SQL Server creates a new table (not physical) by combining rows that have matching values in two or more tables. This join is based on a logical relationship (or a common field) between the tables and is used to retrieve data that appears in both tables.

SELECT CUST.customer_id, CUST.first_name, CUST.City, ORD.Amount, ORD.Order_id
FROM Customer AS CUST
INNER JOIN Orders AS ORD
ON CUST.customer_id = ORD.Customer_id

3. Make left and right joins on ‘Customer’ & ‘Order’ tables on the ‘customer_id’ column

LEFT JOIN:  The LEFT JOIN keyword returns all records from the left table (table1), and the matching records from the right table (table2). The result is 0 records from the right side, if there is no match.

SELECT CUST.customer_id, CUST.first_name, CUST.City, ORD.Amount, ORD.Order_id
FROM Customer AS CUST
LEFT JOIN Orders AS ORD
ON CUST.customer_id = ORD.customer_id

RIGHT JOIN:  The RIGHT JOIN keyword returns all records from the right table (table2), and the matching records from the left table (table1). The result is 0 records from the left side, if there is no match. 

SELECT CUST.customer_id, CUST.first_name, CUST.City, ORD.Amount, ORD.Order_id, ORD.Order_date
FROM Customer AS CUST
RIGHT JOIN Orders AS ORD
ON CUST.customer_id = ORD.customer_id

4. Update the ‘Orders’ table, set the amount to be 100 where ‘customer_id’ is 3.

UPDATE Orders
SET Amount = 100 WHERE customer_id = 003

SELECT * FROM Orders

* * *
Assignment-3

Business Requirement:

1. Use the inbuilt functions and find the minimum, maximum and average amount from the orders table

2. Create a user-defined function, which will multiply the given number with 10

3. Use the case statement to check if 100 is less than 200, greater than 200 or equal to 2oo and print the corresponding value.

Solution:

1. Use the inbuilt functions and find the minimum, maximum and average amount from the orders table.

SELECT MIN(Amount) AS MINIMUM, MAX (Amount) AS MAXIMUM,Avg(Amount) AS AVERAGE
FROM Orders

2. Create a user-defined function, which will multiply the given number with 10.

In SQL Server they are 3 types of User Define Function.

1. Scalar Functions

2. Inline table Valued Functions.

3.Multi Statement table Valued functions.

Scalar Functions:

It May or may not have parameters, But always return a single (Scalar) value. The returned value can be of any date type, Except text, ntext, image, cursor and timeStamp.

CREATE FUNCTION MULTI(@Number INT)
RETURNS INT
AS
BEGIN
RETURN @Number*10
END
Once the query is executed successfully. We can check in Database-> Programmability->Functions-> Scalar Valued Functions


Whenever we calling out the function name we have mentioned Database Owner dot Name of the function. if we not mention the DBO function Name we will get an error  'Multi  is not a recognized built-in function name'.



3. Use the case statement to check if 100 is less than 200, greater than 200 or equal to 2oo and print the corresponding value.

CASE STATEMENT: The CASE statement goes through conditions and returns a value when the first condition is met (like an if-then-else statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.

SELECT
CASE
WHEN 100 < 200 THEN '100 is less than 200'
WHEN 100 >= 200 THEN 'Greater than 200'
END AS RESULT

* * *
Assignment-4

Business Requirement:

1. Arrange the ‘Orders’ dataset in decreasing order of amount

2. Create a table with name ‘Employee_details1’ and comprising of these columns – ‘Emp_id’, ‘Emp_name’, ‘Emp_salary’. Create another table with name ‘Employee_details2’, which comprises of same columns as first table.

3. Apply the union operator on these two tables

4. Apply the intersect operator on these two tables

5. Apply the except operator on these two tables

Solution:

1. Arrange the ‘Orders’ dataset in decreasing order of amount

SELECT * FROM Orders

ORDER BY Amount DESC

2. Create a table with name ‘Employee_details1’ and comprising of these columns – ‘Emp_id’, ‘Emp_name’, ‘Emp_salary’. Create another table with name ‘Employee_details2’, which comprises of same columns as first table.

CREATE TABLE Employee_details1 (Emp_id INT, Emp_name VARCHAR (25),Emp_salary INT)

INSERT INTO Employee_details1

VALUES (201,'Cycle',2000),(202,'Bike',4000),(203,'Car',6000),(204,'AeroPlane',8000)

SELECT * FROM Employee_details1

CREATE TABLE Employee_details2 (Emp_id INT, Emp_name VARCHAR (25),Emp_salary INT)

INSERT INTO Employee_details2

VALUES (208,'Helicopter',1200),(210,'Truck',1500),(201,'Cycle',2000),(202,'Bike',4000)

SELECT * FROM Employee_details2

Employee_details1

Employee_details2
Apply the union operator on these two tables

The UNION operator is used to combine the result sets of 2 or more SELECT statements. It removes duplicate rows between the various SELECT statements. Each SELECT statement within the UNION operator must have the same number of columns in the result sets with similar data types.

SELECT * FROM Employee_details1

UNION

SELECT * FROM Employee_details2

The UNION ALL operator is used to combine the result sets of 2 or more SELECT statements. It does not remove duplicate rows between the various SELECT statements (all rows are returned). Each SELECT statement within the UNION ALL must have the same number of fields in the result sets with similar data types.

SELECT * FROM Employee_details1

UNION ALL

SELECT * FROM Employee_details2

4. Apply the intersect operator on these two tables.

INTERSECT operator is used to return the records that are in common between two SELECT statements or data sets. If a record exists in one query and not in the other, it will be omitted from the INTERSECT results. It is the intersection of the two SELECT statements.

SELECT * FROM Employee_details1

INTERSECT

SELECT * FROM Employee_details2

5. Apply the except operator on these two tables. 

The SQL EXCEPT clause/operator is used to combine two SELECT statements and returns rows from the first SELECT statement that are not returned by the second SELECT statement. This means EXCEPT returns only rows, which are not available in the second SELECT statement.

SELECT * FROM Employee_details1

EXCEPT

SELECT * FROM Employee_details2

* * *
Assignment-5

Business Requirement:

1. Create a view named ‘customer_san_jose’ which comprises of only those customers who are from san jose

2. Inside a transaction, update the first name of the customer to Francis, where the last name is Jordan a. Rollback the transaction

b. Set the first name of customer to Alex, where the last name is Jordan

3. Inside a try catch block, divide 100 with 0, print the default error message

Solution:

1. Create a view named ‘customer_san_jose’ which comprises of only those customers who are from san jose.

What is a View?

A View is nothing more than a saved SQL Query. A View can also be considered as a virtual table.

CREATE VIEW customer_san_jose AS
SELECT * FROM Customer
WHERE City = 'San Jose'

SELECT * FROM customer_san_jose

We can also see the created view in Database-> View-> View Name.

2. Inside a transaction, update the first name of the customer to Francis, where the last name is Jordan a. Rollback the transaction.

What is Transaction?

A Transaction is a group of commands that change the data stored in a database. A transaction is treated as a single unit. A transaction ensure that either all of the commands succeed, or none of them. if one of the commands in the transaction fails. All of the commands fail, and any data that was modified in the database is rolled back. In this way transactions maintain the integrity of data in a database.

INSERT INTO customer
VALUES (110,'Tom','Jordan','TomJordan@gmail.com','2283  Felosa Drive','San Angelo','Texas',76903),
(111,'Rajesh','Kumar','RajeshKumar@gmail.com','372  Palmer Road','Westerville','Ohio',43081)

SELECT * FROM Customer

BEGIN TRANSACTION
UPDATE Customer
SET first_name = 'Francis'
WHERE last_name ='Jordan'
ROLLBACK TRANSACTION

SELECT * FROM Customer

b. Set the first name of customer to Alex, where the last name is Jordan.

BEGIN TRANSACTION
UPDATE Customer
SET first_name = 'Alex'
WHERE last_name ='Jordan'
COMMIT TRANSACTION

SELECT * FROM Customer

3. Inside a try catch block, divide 100 with 0, print the default error message

BEGIN TRY    
    SELECT 100/0 AS Division;  
END TRY  
BEGIN CATCH  
    SELECT  
        ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
END CATCH
