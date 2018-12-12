
## Table - People

### Instructions
1. Create a table called Person that records a person's ID, Name, Age, Height ( in cm ), City, FavoriteColor. 
    * ID should be an auto-incrementing id/primary key - Use type: INTEGER PRIMARY KEY AUTOINCREMENT

	CREATE TABLE Person 
	(ID INTEGER PRIMARY KEY AUTOINCREMENT,
	Name varchar(255),
	Age Integer,
	Height Integer,
	City varchar(255),
	FavoriteColor varchar(255)
	);

2. Add 5 different people into the Person database. 
    * Remember to not include the ID because it should auto-increment.

	INSERT INTO Person(Name,Age,Height,City,FavoriteColor)
	VALUES
	('Braden',27,188,'Denton','Red'),
	('David',24,176,'Dallas','Orange'),
	('Tim',26,177,'Ft Worth','Yellow'),
	('Garrett',18,190,'Dallas','Green'),
	('Logan',88,108,'Dallas','Blue');

3. List all the people in the Person table by Height from tallest to shortest.

	SELECT * FROM Person ORDER BY Height DESC;

4. List all the people in the Person table by Height from shortest to tallest.

	SELECT * FROM Person ORDER BY Height ASC;

5. List all the people in the Person table by Age from oldest to youngest.

	SELECT * FROM Person ORDER BY Age DESC;

6. List all the people in the Person table older than age 20.

	SELECT * FROM Person WHERE Age > 20;

7. List all the people in the Person table that are exactly 18.

	SELECT * FROM Person WHERE Age = 18;

8. List all the people in the Person table that are less than 20 and older than 30.

	SELECT * FROM Person WHERE Age<20 OR Age>30;

9. List all the people in the Person table that are not 27 (Use not equals).

	SELECT * FROM Person WHERE Age !=27;

10. List all the people in the Person table where their favorite color is not red.

	SELECT * FROM Person WHERE FavoriteColor != 'Red';

11. List all the people in the Person table where their favorite color is not red and is not blue.

	SELECT * FROM Person WHERE FavoriteColor != 'Red' AND FavoriteColor != 'Blue';
	
12. List all the people in the Person table where their favorite color is orange or green.

	SELECT * FROM Person WHERE FavoriteColor = 'Orange' OR FavoriteColor = 'Green';
	
13. List all the people in the Person table where their favorite color is orange, green or blue (use IN).

	SELECT * FROM Person WHERE FavoriteColor IN ('Orange','Green','Blue');
	
14. List all the people in the Person table where their favorite color is yellow or purple (use IN).

	SELECT * FROM Person WHERE FavoriteColor IN ('Yellow','Purple');

## Table - Orders

### Instructions

1. Create a table called Orders that records: PersonID, ProductName, ProductPrice, Quantity.

	CREATE TABLE Orders (
		PersonID integer,
		ProductName varchar(255),
		ProductPrice numeric(4,2),
		Quantity integer
	);

2. Add 5 Orders to the Orders table.
    * Make orders for at least two different people.
    * PersonID should be different for different people.

	INSERT INTO Orders (PersonID, ProductName, ProductPrice, Quantity)
	VALUES
	(1,'Apple',01.99,4),
	(1,'Cookie',02.50,10),
	(2,'Pizza',10.00,1),
	(3,'LaCroix',02.00,10),
	(4,'M&Ms', 03.75,1);

3. Select all the records from the Orders table.

	SELECT * FROM Orders;

4. Calculate the total number of products ordered.

	SELECT Sum(Quantity) FROM Orders;

5. Calculate the total order price.

	SELECT Sum(Quantity*ProductPrice) FROM Orders;

6. Calculate the total order price by a single PersonID.

	SELECT Sum(Quantity*ProductPrice) FROM Orders WHERE PersonID=1;
	

## Table - Artist

### Instructions

1. Add 3 new Artists to the Artist table. ( It's already created )

	INSERT INTO Artist (Name)
	VALUES 
	('Run The Jewels'),
	('Beastie Boys'),
	('Sia');

2. Select 10 artists in reverse alphabetical order.

	SELECT * FROM Artist ORDER BY Name DESC LIMIT 10;

3. Select 5 artists in alphabetical order.

	SELECT * FROM Artist ORDER BY Name ASC LIMIT 5;

4. Select all artists that start with the word "Black".

	SELECT * FROM Artist WHERE Name LIKE 'Black%';

5. Select all artists that contain the word "Black".

	SELECT * FROM Artist WHERE Name LIKE '%Black%';
	

## Table - Employee

### Instructions

1. List all Employee first and last names only that live in Calgary.

	SELECT FirstName, LastName FROM Employee WHERE City = 'Calgary'

2. Find the first and last name and birthdate for the youngest employee.

	SELECT FirstName, LastName, BirthDate FROM Employee ORDER BY BirthDate DESC LIMIT 1;

3. Find the first and last name and birthdate for the oldest employee.

	SELECT FirstName, LastName, BirthDate FROM Employee ORDER BY BirthDate ASC LIMIT 1;

4. Find everyone that reports to Nancy Edwards (Use the ReportsTo column).
   * You will need to query the employee table to find the Id for Nancy Edwards

	SELECT * FROM Employee WHERE ReportsTo = '2';

5. Count how many people live in Lethbridge.

	SELECT Count(*) FROM Employee WHERE City = 'Lethbridge';

## Table - Invoice 

### Instructions

1. Count how many orders were made from the USA.

	SELECT Count(*) FROM Invoice WHERE BillingCountry = 'USA';

2. Find the largest order total amount.

	SELECT Total FROM Invoice ORDER BY Total DESC LIMIT 1;

3. Find the smallest order total amount.

	SELECT Total FROM Invoice ORDER BY Total ASC LIMIT 1;

4. Find all orders bigger than $5.

	SELECT * FROM Invoice WHERE Total > 5;

5. Count how many orders were smaller than $5.

	SELECT Count(*) FROM Invoice WHERE Total < 5;

6. Count how many orders were in CA, TX, or AZ (use IN).

	SELECT Count(*) FROM Invoice WHERE BillingState IN ('CA','TX','AZ');

7. Get the average total of the orders.

	SELECT Avg(Total) FROM Invoice;

8. Get the total sum of the orders.

	SELECT Sum(TOTAL) FROM Invoice;