
2026-02-05  03:36 pm

Tags: [[School]] [[Coding]] [[SQL]] [[Database]]

---
# Advanced Database Management System  |  2025-26

---

# 1st Semester

## Prelim


### 02/09/26 - SQL

#### DDL - Data Definition Language

- CREATE - creates a database/table
- DROP - deletes the whole database
- ALTER - 
- TRUNCATE - 


#### DML - Data Manipulation Language

- INSERT
- UPDATE
- DELETE


#### TCL - Transaction Control Language

- COMMIT
- SAVEPOINT
- ROLLBACK


#### DQL -Data Query Language

- SELECT


#### DCL - Data Control Language

- GRANT - grants user access to a table/database
- REVOKE - revokes access of user to a table/database


---

### 02/23/26  - Lab Activity 1

```sql
CREATE DATABASE TindahanDB;
USE TindahanDB;


CREATE TABLE Products (
  ProductID INT PRIMARY KEY,
  ProductName VARCHAR(30) NOT NULL,
  Category VARCHAR(50) NOT NULL
);

CREATE TABLE  Inventory (
  InventoryID INT PRIMARY KEY,
  ProductID INT NOT NULL,
  QuantityOnHand INT NOT NULL,
  UnitCost INT NOT NULL,
  RetailPrice INT NOT NULL,
  CONSTRAINT FK_Inventory_Products
  FOREIGN KEY (ProductID)
  REFERENCES Products(ProductID)
);

INSERT INTO Products (ProductID, ProductName, Category)
	VALUES 
	  (1, 'Magic Sarap', 'Cooking'),
	  (2, 'Marlboro Light', 'Cigarette'),
	  (3, 'Chippy', 'Snacks & Candies'),
	  (4, 'Sprite', 'Drinks'),
	  (5, 'Pochi', 'Snacks & Candies');
	  
INSERT INTO Inventory (InventoryID, ProductID, QuantityOnHand, UnitCost, RetailPrice)
  VALUES
    (1, 5, 325, 3, 4),
    (2, 2, 14, 15, 20),
    (3, 4, 51, 20, 30),
    (4, 3, 107, 10, 13),
    (5, 1, 46, 20, 25);


-- DELETE FROM Products
--   WHERE ProductID = 2;

-- DELETE FROM Inventory
--   WHERE ProductID = 1;

SELECT * FROM Products;
SELECT * FROM Inventory;


-- SELECT Products.ProductName, Inventory.QuantityOnHand
-- FROM Products
--   INNER JOIN Inventory
--   ON Products.ProductID = Inventory.ProductID;


-- UPDATE Products
--   SET Category = 'Tabacco'
--   WHERE ProductID = 2;

-- UPDATE Inventory
--   SET RetailPrice = 50
--   WHERE ProductID = 2;
```


### 2/24/26

#### Lab Activity 2

```sql
--- Step 1 Create Table
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  LastName VARCHAR(100) NOT NULL,
  FirstName VARCHAR(100) NOT NULL,
  Age INT CHECK (Age>=18)
);

--- Step 2 Populate Table
INSERT INTO Students (StudentID, LastName, FirstName, Age)
	VALUES
    	(1, 'Smith', 'John', 21),
        (2, 'Johnson', 'Emma', 19),
        (3, 'Williams', 'Liam', 22),
        (4, 'Maluenda', 'John Steven', 20), --- Step 3 Populate table with 3 more rows
        (5, 'Talisaysay', 'Kirk', 22),
        (6, 'De Leon', 'Jacob', 9999999);

SELECT * FROM Students;
        
--- Step 4 Add Email Column
ALTER TABLE Students
	ADD Email VARCHAR(255);
        
SELECT COLUMN_NAME
FROM INFORMATION_SCHEMA.COLUMNS
	WHERE TABLE_NAME='Students';

--- Step 5
SELECT * FROM Students;
    
--- Step 6
UPDATE Students
SET EMAIL = 'johnsmith@gmail.com'
	WHERE StudentID = 1;
    
UPDATE Students
SET EMAIL = 'emmajohnson@gmail.com'
	WHERE StudentID = 2;
    
UPDATE Students
SET EMAIL = 'liamwilliams@gmail.com'
	WHERE StudentID = 3;
    
UPDATE Students
SET EMAIL = 'johnstevenmaluenda@gmail.com'
	WHERE StudentID = 4;
    
UPDATE Students
SET EMAIL = 'kirktalisaysay@gmail.com'
	WHERE StudentID = 5;
    
UPDATE Students
SET EMAIL = 'certifiedprogrammer@gmail.com'
	WHERE StudentID = 6;
    
--- Step 7
SELECT * FROM Students;
    
--- Step 8
SELECT Email, COUNT(*)
FROM Students
	GROUP BY Email
    HAVING COUNT(*)>1;
    
--- Step 9
ALTER TABLE Students
	ADD CONSTRAINT UQ_Students_Email UNIQUE(Email);
    
--- Step 10
EXEC sp_help Students;
    
SELECT * FROM Students;
```


#### Data Insertion Lab Activity

```sql

-------- TABLE CREATION --------

-- REGIONS
CREATE TABLE REGIONS (
    REGION_ID NUMERIC(4) NOT NULL,
    REGION_NAME VARCHAR(25)
);

ALTER TABLE REGIONS
ADD CONSTRAINT PK_REGIONS PRIMARY KEY (REGION_ID);


-- COUNTRIES
CREATE TABLE COUNTRIES (
    COUNTRY_ID CHAR(2) NOT NULL,
    COUNTRY_NAME VARCHAR(40),
    REGION_ID NUMERIC(4)
);

ALTER TABLE COUNTRIES
ADD CONSTRAINT PK_COUNTRIES PRIMARY KEY (COUNTRY_ID);

ALTER TABLE COUNTRIES
ADD CONSTRAINT FK_COUNTRIES_REGION
FOREIGN KEY (REGION_ID)
REFERENCES REGIONS(REGION_ID);


-- LOCATIONS
CREATE TABLE LOCATIONS (
    LOCATION_ID NUMERIC(4) NOT NULL,
    STREET_ADDRESS VARCHAR(40),
    POSTAL_CODE VARCHAR(12),
    CITY VARCHAR(30) NOT NULL,
    STATE_PROVINCE VARCHAR(25),
    COUNTRY_ID CHAR(2)
);

ALTER TABLE LOCATIONS
ADD CONSTRAINT PK_LOCATIONS PRIMARY KEY (LOCATION_ID);

ALTER TABLE LOCATIONS
ADD CONSTRAINT FK_LOCATIONS_COUNTRY
FOREIGN KEY (COUNTRY_ID)
REFERENCES COUNTRIES(COUNTRY_ID);


-- JOBS
CREATE TABLE JOBS (
    JOB_ID VARCHAR(10) PRIMARY KEY,
    JOB_TITLE VARCHAR(35) NOT NULL,
    MIN_SALARY NUMERIC(6),
    MAX_SALARY NUMERIC(6)
);


-- EMPLOYEES
CREATE TABLE EMPLOYEES (
    EMPLOYEE_ID NUMERIC(6) PRIMARY KEY,
    FIRST_NAME VARCHAR(20),
    LAST_NAME VARCHAR(25) NOT NULL,
    EMAIL VARCHAR(25) NOT NULL UNIQUE,
    PHONE_NUMBER VARCHAR(20),
    HIRE_DATE DATE NOT NULL,
    JOB_ID VARCHAR(10) NOT NULL,
    SALARY NUMERIC(8,2) CHECK (SALARY > 0),
    COMMISSION_PCT NUMERIC(4,2),
    MANAGER_ID NUMERIC(6),
    DEPARTMENT_ID NUMERIC(4)
);

ALTER TABLE EMPLOYEES
ADD CONSTRAINT FK_EMP_JOB
FOREIGN KEY (JOB_ID) REFERENCES JOBS(JOB_ID);

ALTER TABLE EMPLOYEES
ADD CONSTRAINT FK_EMP_MANAGER
FOREIGN KEY (MANAGER_ID) REFERENCES EMPLOYEES(EMPLOYEE_ID);


-- DEPARTMENTS
CREATE TABLE DEPARTMENTS (
    DEPARTMENT_ID NUMERIC(4) NOT NULL,
    DEPARTMENT_NAME VARCHAR(30) NOT NULL,
    MANAGER_ID NUMERIC(6),
    LOCATION_ID NUMERIC(4)
);

ALTER TABLE DEPARTMENTS
ADD CONSTRAINT PK_DEPARTMENTS PRIMARY KEY (DEPARTMENT_ID);

ALTER TABLE DEPARTMENTS
ADD CONSTRAINT FK_DEPT_LOCATION
FOREIGN KEY (LOCATION_ID) REFERENCES LOCATIONS(LOCATION_ID);

ALTER TABLE DEPARTMENTS
ADD CONSTRAINT FK_DEPT_MANAGER
FOREIGN KEY (MANAGER_ID) REFERENCES EMPLOYEES(EMPLOYEE_ID);

ALTER TABLE EMPLOYEES
ADD CONSTRAINT FK_EMP_DEPARTMENT
FOREIGN KEY (DEPARTMENT_ID) REFERENCES DEPARTMENTS(DEPARTMENT_ID);


-- JOB_HISTORY
CREATE TABLE JOB_HISTORY (
    EMPLOYEE_ID NUMERIC(6) NOT NULL,
    START_DATE DATE NOT NULL,
    END_DATE DATE NOT NULL,
    JOB_ID VARCHAR(10) NOT NULL,
    DEPARTMENT_ID NUMERIC(4),
    CONSTRAINT PK_JOB_HISTORY PRIMARY KEY (EMPLOYEE_ID, START_DATE),
    CONSTRAINT CHK_JOB_HISTORY CHECK (END_DATE > START_DATE)
);

ALTER TABLE JOB_HISTORY
ADD CONSTRAINT FK_JH_EMP FOREIGN KEY (EMPLOYEE_ID)
REFERENCES EMPLOYEES(EMPLOYEE_ID);

ALTER TABLE JOB_HISTORY
ADD CONSTRAINT FK_JH_JOB FOREIGN KEY (JOB_ID)
REFERENCES JOBS(JOB_ID);

ALTER TABLE JOB_HISTORY
ADD CONSTRAINT FK_JH_DEPT FOREIGN KEY (DEPARTMENT_ID)
REFERENCES DEPARTMENTS(DEPARTMENT_ID);


-------- DATA INSERTION --------

-- REGIONS
INSERT INTO REGIONS (REGION_ID, REGION_NAME)
	VALUES
	  (1, 'North America'),
	  (2, 'Russia'),
	  (3, 'Asia'),
	  (4, 'Australia');


-- COUNTRIES
INSERT INTO COUNTRIES (COUNTRY_ID, COUNTRY_NAME, REGION_ID)
	VALUES
	  ('US', 'United States', 1),
	  ('CA', 'Canada', 1),
	  ('MX', 'Mexico', 1),
	  ('CU', 'Cuba', 1),
	  ('GT', 'Guatemala', 1),

	  ('RU', 'Russia', 2),

	  ('CN', 'China', 3),
	  ('JP', 'Japan', 3),
	  ('KR', 'South Korea', 3),
	  ('PH', 'Philippines', 3),
	  ('SG', 'Singapore', 3),
	  ('TH', 'Thailand', 3),
	  ('MY', 'Malaysia', 3),
	  ('VN', 'Vietnam', 3),
	  ('ID', 'Indonesia', 3),
	  ('IN', 'India', 3),
	  ('PK', 'Pakistan', 3),
	  ('BD', 'Bangladesh', 3),
	  ('SA', 'Saudi Arabia', 3),
	  ('AE', 'United Arab Emirates', 3),

	  ('AU', 'Australia', 4),
	  ('NZ', 'New Zealand', 4),
	  ('PG', 'Papua New Guinea', 4),
	  ('FJ', 'Fiji', 4),
	  ('SB', 'Solomon Islands', 4);


-- LOCATIONS
INSERT INTO LOCATIONS (LOCATION_ID, STREET_ADDRESS, POSTAL_CODE, CITY, STATE_PROVINCE, COUNTRY_ID)
	VALUES
	  (1000, '5th Avenue', '10001', 'New York', 'NY', 'US'),
	  (1100, 'Market Street', '94103', 'San Francisco', 'CA', 'US'),
	  (1200, 'Bay Street', 'M5J2N8', 'Toronto', 'Ontario', 'CA'),
	  (1300, 'Avenida Reforma', '06600', 'Mexico City', NULL, 'MX'),
	  (1400, 'Nevsky Prospekt', '191025', 'Saint Petersburg', NULL, 'RU'),

	  (1500, 'Shibuya Crossing', '1500002', 'Tokyo', NULL, 'JP'),
	  (1600, 'Gangnam-daero', '06129', 'Seoul', NULL, 'KR'),
	  (1700, 'Ayala Avenue', '1226', 'Makati City', 'Metro Manila', 'PH'),
	  (1800, 'Orchard Road', '238823', 'Singapore', NULL, 'SG'),
	  (1900, 'Sukhumvit Road', '10110', 'Bangkok', NULL, 'TH'),

	  (2000, 'Jalan Ampang', '50450', 'Kuala Lumpur', NULL, 'MY'),
	  (2100, 'Pham Ngu Lao', '700000', 'Ho Chi Minh City', NULL, 'VN'),
	  (2200, 'MG Road', '560001', 'Bangalore', NULL, 'IN'),
	  (2300, 'King Fahd Road', '12271', 'Riyadh', NULL, 'SA'),
	  (2400, 'Sheikh Zayed Road', '00000', 'Dubai', NULL, 'AE'),

	  (2500, 'George Street', '2000', 'Sydney', 'NSW', 'AU'),
	  (2600, 'Queen Street', '1010', 'Auckland', NULL, 'NZ'),
	  (2700, 'Waigani Drive', '111', 'Port Moresby', NULL, 'PG'),
	  (2800, 'Victoria Parade', '0000', 'Suva', NULL, 'FJ'),
	  (2900, 'Mendana Avenue', '0000', 'Honiara', NULL, 'SB');


-- JOBS
INSERT INTO JOBS (JOB_ID, JOB_TITLE, MIN_SALARY, MAX_SALARY)
	VALUES
	  ('CEO', 'Chief Executive Officer', 90000, 200000),
	  ('CFO', 'Chief Financial Officer', 80000, 180000),
	  ('CTO', 'Chief Technology Officer', 80000, 180000),
	  ('HR_MGR', 'HR Manager', 40000, 90000),
	  ('IT_MGR', 'IT Manager', 50000, 120000),
	  ('DEV', 'Software Developer', 30000, 100000),
	  ('QA', 'QA Engineer', 30000, 80000),
	  ('ACC', 'Accountant', 35000, 85000),
	  ('SALES_MGR', 'Sales Manager', 50000, 110000),
	  ('SALES_REP', 'Sales Representative', 25000, 70000),
	  ('MK_MGR', 'Marketing Manager', 45000, 100000),
	  ('MK_OFF', 'Marketing Officer', 30000, 70000),
	  ('DATA_ENG', 'Data Engineer', 40000, 120000),
	  ('SUPPORT', 'Technical Support', 25000, 60000),
	  ('ADMIN', 'Administrative Officer', 25000, 60000);


-- EMPLOYEES
INSERT INTO EMPLOYEES
	(EMPLOYEE_ID, FIRST_NAME, LAST_NAME, EMAIL, PHONE_NUMBER, HIRE_DATE, JOB_ID, SALARY, COMMISSION_PCT, MANAGER_ID, DEPARTMENT_ID)
	VALUES
	  (1,'John','Anderson','JANDERSON','1111111111','2010-01-01','CEO',150000,NULL,NULL,NULL),
	  (2,'Emily','Clark','ECLARK','1111111112','2011-02-01','CFO',140000,NULL,1,NULL),
	  (3,'Michael','Brown','MBROWN','1111111113','2012-03-01','CTO',135000,NULL,1,NULL),
	  (4,'Robert','Garcia','RGARCIA','1111111114','2013-04-01','IT_MGR',95000,NULL,3,NULL),
	  (5,'David','Smith','DSMITH','1111111115','2014-05-01','DEV',80000,NULL,4,NULL),
	  (6,'Carlos','Mendoza','CMENDOZA','1111111116','2015-06-01','SALES_MGR',90000,NULL,1,NULL),
	  (7,'Anna','Ivanova','AIVANOVA','2222222221','2013-02-10','HR_MGR',85000,NULL,1,NULL),
	  (8,'Sergey','Petrov','SPETROV','2222222222','2014-03-11','DEV',75000,NULL,4,NULL),
	  (9,'Dmitry','Volkov','DVOLKOV','2222222223','2015-04-12','DATA_ENG',90000,NULL,3,NULL),
	  (10,'Olga','Smirnova','OSMIRNOVA','2222222224','2016-05-13','ACC',70000,NULL,2,NULL),

	  (11,'Hiroshi','Tanaka','HTANAKA','3333333331','2016-06-01','DEV',85000,NULL,4,NULL),
	  (12,'Yuna','Kim','YKIM','3333333332','2017-07-01','QA',65000,NULL,4,NULL),
	  (13,'Wei','Zhang','WZHANG','3333333333','2018-08-01','DATA_ENG',95000,NULL,3,NULL),
	  (14,'Arjun','Sharma','ASHARMA','3333333334','2019-09-01','SUPPORT',60000,NULL,4,NULL),
	  (15,'Maria','Santos','MSANTOS','3333333335','2020-01-01','ADMIN',50000,NULL,7,NULL),
	  (16,'Nguyen','Tran','NTRAN','3333333336','2020-02-01','DEV',70000,NULL,4,NULL),
	  (17,'Ahmad','Khan','AKHAN','3333333337','2021-03-01','QA',62000,NULL,4,NULL),
	  (18,'Siti','Rahman','SRAHMAN','3333333338','2021-04-01','MK_OFF',55000,NULL,6,NULL),
	  (19,'Juan','Dela Cruz','JDELACRUZ','3333333339','2022-05-01','SALES_REP',60000,0.10,6,NULL),
	  (20,'Min','Lee','MLEE','3333333340','2022-06-01','DEV',78000,NULL,4,NULL),

	  (21,'Liam','Wilson','LWILSON','4444444441','2017-01-01','DEV',82000,NULL,4,NULL),
	  (22,'Noah','Taylor','NTAYLOR','4444444442','2018-02-01','QA',67000,NULL,4,NULL),
	  (23,'Olivia','White','OWHITE','4444444443','2019-03-01','MK_MGR',88000,NULL,6,NULL),
	  (24,'Ava','Martin','AMARTIN','4444444444','2020-04-01','ACC',72000,NULL,2,NULL),
	  (25,'Lucas','Thompson','LTHOMPSON','4444444445','2021-05-01','SUPPORT',58000,NULL,4,NULL),
	  (26,'Ethan','Hall','EHALL','4444444446','2022-06-01','DEV',77000,NULL,4,NULL),
	  (27,'Mason','Allen','MALLEN','4444444447','2023-07-01','SALES_REP',55000,0.15,6,NULL),
	  (28,'Chloe','Young','CYOUNG','4444444448','2023-08-01','ADMIN',52000,NULL,7,NULL),
	  (29,'James','King','JKING','4444444449','2023-09-01','QA',64000,NULL,4,NULL),
	  (30,'Sophia','Scott','SSCOTT','4444444450','2023-10-01','DEV',79000,NULL,4,NULL);


-- DEPARTMENTS
INSERT INTO DEPARTMENTS
	(DEPARTMENT_ID, DEPARTMENT_NAME, MANAGER_ID, LOCATION_ID)
	VALUES
	  (10,'Executive',1,1000),
	  (20,'Finance',2,1000),
	  (30,'Technology',3,1100),
	  (40,'Engineering',4,1100),
	  (50,'Sales',6,1200),
	  (60,'Human Resources',7,1000),
	  (70,'Data Science',9,1500),
	  (80,'Marketing',23,1700),
	  (90,'Accounting',10,1400),
	  (100,'Support',14,2200),
	  (110,'Operations',5,1000),
	  (120,'International Sales',6,1500),
	  (130,'Product Development',4,1600),
	  (140,'Asia Pacific',11,1700),
	  (150,'Australia Region',21,2500);
	  
UPDATE EMPLOYEES SET DEPARTMENT_ID = 10 WHERE EMPLOYEE_ID = 1;
UPDATE EMPLOYEES SET DEPARTMENT_ID = 20 WHERE EMPLOYEE_ID IN (2,24);
UPDATE EMPLOYEES SET DEPARTMENT_ID = 30 WHERE EMPLOYEE_ID = 3;
UPDATE EMPLOYEES SET DEPARTMENT_ID = 40 WHERE EMPLOYEE_ID IN (4,5,11,12,16,17,20,21,22,26,29,30);
UPDATE EMPLOYEES SET DEPARTMENT_ID = 50 WHERE EMPLOYEE_ID IN (6,19,27);
UPDATE EMPLOYEES SET DEPARTMENT_ID = 60 WHERE EMPLOYEE_ID IN (7,15,28);
UPDATE EMPLOYEES SET DEPARTMENT_ID = 70 WHERE EMPLOYEE_ID = 9;
UPDATE EMPLOYEES SET DEPARTMENT_ID = 80 WHERE EMPLOYEE_ID = 23;
UPDATE EMPLOYEES SET DEPARTMENT_ID = 90 WHERE EMPLOYEE_ID = 10;
UPDATE EMPLOYEES SET DEPARTMENT_ID = 100 WHERE EMPLOYEE_ID = 14;


-- JOB HISTORY
INSERT INTO JOB_HISTORY
	(EMPLOYEE_ID, START_DATE, END_DATE, JOB_ID, DEPARTMENT_ID)
	VALUES
	  (5,'2013-01-01','2014-04-30','SUPPORT',100),
	  (8,'2014-01-01','2015-04-30','QA',40),
	  (9,'2014-01-01','2015-04-30','DEV',30),
	  (12,'2016-01-01','2017-06-30','SUPPORT',100),
	  (14,'2018-01-01','2019-08-31','QA',40),
	  (16,'2019-01-01','2020-01-31','QA',40),
	  (18,'2020-01-01','2021-03-31','SALES_REP',50),
	  (21,'2016-01-01','2016-12-31','QA',40),
	  (23,'2018-01-01','2019-02-28','MK_OFF',80),
	  (27,'2022-01-01','2023-06-30','SUPPORT',100);


-- QUERY OF ALL TABLES
SELECT * FROM REGIONS;
SELECT * FROM COUNTRIES;
SELECT * FROM LOCATIONS;
SELECT * FROM JOBS;
SELECT * FROM EMPLOYEES;
SELECT * FROM DEPARTMENTS;
SELECT * FROM JOB_HISTORY;

```


**Clarifications**

- Same amount po ba of data yung iinsert sa data insertion activity? same amount
- Deadline of data insertion activity? wednesday 11:59pm
- Date, time, and room number of the prelim exam? to be announced


---

## Midterm


### 03/10/26 - Module 4 Lab Activity

```sql
CREATE TABLE Fruits (
FruitID INT PRIMARY KEY,
FruitName VARCHAR(50),
Category VARCHAR(50),
Price DECIMAL(10,2),
Qty INT,
PurchaseDate DATE
);

  
INSERT INTO Fruits (FruitID, FruitName, Category, Price, Qty, PurchaseDate)
VALUES
(1, 'Apple', 'Imported', 80, 10, '2024-01-10'),
(2, 'Banana', 'Local', 40, 15, '2024-01-11'),
(3, 'Orange', 'Imported', 75, 8, '2024-01-12'),
(4, 'Mango', 'Local', 90, 12, '2024-01-15'),
(5, 'Grapes', 'Imported', 120, 6, '2024-01-16'),
(6, 'Pineapple', 'Local', 60, 9, '2024-01-18'),
(7, 'Watermelon', 'Local', 110, 5, '2024-01-19'),
(8, 'Strawberry', 'Imported', 150, 4, '2024-01-20'),
(9, 'Papaya', 'Local', 50, 11, '2024-01-21'),
(10, 'Avocado', 'Local', 70, 7, '2024-01-22');


-- 1
SELECT * FROM Fruits

-- 2
SELECT AVG(Price) AS AveragePrice FROM Fruits

-- 3
SELECT MAX(Price) AS HighestPrice FROM Fruits

-- 4
SELECT Category, SUM(Qty) AS TotalQty FROM Fruits
GROUP BY Category;

-- 5
SELECT Category, AVG(Qty) AS AveragePrice FROM Fruits
GROUP BY Category;

-- 6
SELECT Category, SUM(Qty) AS TotalQty FROM Fruits
GROUP BY Category
HAVING SUM(Qty) > 20;

-- 7
SELECT FruitName, SUM(Qty * Price) AS TotalSales FROM Fruits
GROUP BY FruitName;

-- 8
SELECT Category, AVG(Price) AS AveragePrice FROM Fruits
GROUP BY Category
HAVING AVG(Price) > 80;

-- 9
SELECT SUM(Qty) AS TotalQuantity
FROM Fruits
WHERE PurchaseDate > '2024-01-15';

-- 10
SELECT Category, AVG(Price) AS AvgPrice
FROM Fruits
GROUP BY Category
ORDER BY AvgPrice DESC;
 

SELECT Category, SUM(Qty) AS TotalQuantity
FROM Fruits
GROUP BY Category
ORDER BY TotalQuantity DESC;

```


### 03/31/26 - Subquery Activity

```sql
-- Drop tables if they exist (for clean start)
IF OBJECT_ID('Employees', 'U') IS NOT NULL DROP TABLE Employees;
IF OBJECT_ID('Departments', 'U') IS NOT NULL DROP TABLE Departments;
GO

-- Create Departments table
CREATE TABLE Departments (
    Department_ID INT PRIMARY KEY,
    Department_Name VARCHAR(50) NOT NULL,
    Location_ID INT,
    Manager_ID INT
);
GO

-- Create Employees table
CREATE TABLE Employees (
    Employee_ID INT PRIMARY KEY,
    First_Name VARCHAR(50),
    Last_Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100),
    Phone_Number VARCHAR(20),
    Hire_Date DATE NOT NULL,
    Job_ID VARCHAR(20) NOT NULL,
    Salary DECIMAL(10, 2) NOT NULL,
    Commission_PCT DECIMAL(3, 2),
    Manager_ID INT,
    Department_ID INT,
    FOREIGN KEY (Department_ID) REFERENCES Departments(Department_ID)
);
GO

CREATE TABLE Locations (
    Location_ID INT PRIMARY KEY,
    Location_Name VARCHAR(100) NOT NULL
);
GO

-- Insert Departments data
INSERT INTO Departments (Department_ID, Department_Name, Location_ID, Manager_ID)
VALUES 
    (10, 'Administration', 1700, 200),
    (20, 'Marketing', 1800, 201),
    (50, 'Shipping', 1500, 124),
    (60, 'IT', 1400, 103),
    (80, 'Sales', 2500, 145),
    (90, 'Executive', 1700, 100),
    (110, 'Accounting', 1700, 205),
    (190, 'Contracting', 1700, NULL);
GO

-- Insert Employees data (comprehensive dataset)
INSERT INTO Employees (Employee_ID, First_Name, Last_Name, Email, Phone_Number, Hire_Date, Job_ID, Salary, Commission_PCT, Manager_ID, Department_ID)
VALUES 
    -- Executive (Department 90)
    (100, 'Steven', 'King', 'SKING', '515.123.4567', '1987-06-17', 'AD_PRES', 24000, NULL, NULL, 90),
    (101, 'Neena', 'Kochhar', 'NKOCHHAR', '515.123.4568', '1989-09-21', 'AD_VP', 17000, NULL, 100, 90),
    (102, 'Lex', 'De Haan', 'LDEHAAN', '515.123.4569', '1993-01-13', 'AD_VP', 17000, NULL, 100, 90),
    
    -- IT (Department 60)
    (103, 'Alexander', 'Hunold', 'AHUNOLD', '590.423.4567', '1990-01-03', 'IT_PROG', 9000, NULL, 102, 60),
    (104, 'Bruce', 'Ernst', 'BERNST', '590.423.4568', '1991-05-21', 'IT_PROG', 6000, NULL, 103, 60),
    (105, 'David', 'Austin', 'DAUSTIN', '590.423.4569', '1997-06-25', 'IT_PROG', 4800, NULL, 103, 60),
    (106, 'Valli', 'Pataballa', 'VPATABAL', '590.423.4560', '1998-02-05', 'IT_PROG', 4800, NULL, 103, 60),
    (107, 'Diana', 'Lorentz', 'DLORENTZ', '590.423.5567', '1999-02-07', 'IT_PROG', 4200, NULL, 103, 60),
    
    -- Shipping (Department 50)
    (124, 'Kevin', 'Mourgos', 'KMOURGOS', '650.123.5234', '1999-11-16', 'ST_MAN', 5800, NULL, 100, 50),
    (141, 'Trenna', 'Rajs', 'TRAJS', '650.121.8009', '1995-10-17', 'ST_CLERK', 3500, NULL, 124, 50),
    (142, 'Curtis', 'Davies', 'CDAVIES', '650.121.2994', '1997-01-29', 'ST_CLERK', 3100, NULL, 124, 50),
    (143, 'Randall', 'Matos', 'RMATOS', '650.121.2874', '1998-03-15', 'ST_CLERK', 2600, NULL, 124, 50),
    (144, 'Peter', 'Vargas', 'PVARGAS', '650.121.2004', '1998-07-09', 'ST_CLERK', 2500, NULL, 124, 50),
    
    -- Sales (Department 80)
    (145, 'John', 'Russell', 'JRUSSEL', '011.44.1344.429268', '1996-10-01', 'SA_MAN', 14000, 0.40, 100, 80),
    (146, 'Karen', 'Partners', 'KPARTNER', '011.44.1344.467268', '1997-01-05', 'SA_MAN', 13500, 0.30, 100, 80),
    (147, 'Alberto', 'Errazuriz', 'AERRAZUR', '011.44.1344.429278', '1997-03-10', 'SA_MAN', 12000, 0.30, 100, 80),
    (148, 'Gerald', 'Cambrault', 'GCAMBRAU', '011.44.1344.619268', '1999-10-15', 'SA_MAN', 11000, 0.30, 100, 80),
    (149, 'Eleni', 'Zlotkey', 'EZLOTKEY', '011.44.1344.429018', '2000-01-29', 'SA_MAN', 10500, 0.20, 100, 80),
    (150, 'Peter', 'Tucker', 'PTUCKER', '011.44.1344.129268', '1997-01-30', 'SA_REP', 10000, 0.30, 145, 80),
    (151, 'David', 'Bernstein', 'DBERNSTE', '011.44.1344.345268', '1997-03-24', 'SA_REP', 9500, 0.25, 145, 80),
    (152, 'Peter', 'Hall', 'PHALL', '011.44.1344.478968', '1997-08-20', 'SA_REP', 9000, 0.25, 145, 80),
    
    -- Administration (Department 10)
    (200, 'Jennifer', 'Whalen', 'JWHALEN', '515.123.4444', '1987-09-17', 'AD_ASST', 4400, NULL, 101, 10),
    
    -- Marketing (Department 20)
    (201, 'Michael', 'Hartstein', 'MHARTSTE', '515.123.5555', '1996-02-17', 'MK_MAN', 13000, NULL, 100, 20),
    (202, 'Pat', 'Fay', 'PFAY', '603.123.6666', '1997-08-17', 'MK_REP', 6000, NULL, 201, 20),
    
    -- Accounting (Department 110)
    (205, 'Shelley', 'Higgins', 'SHIGGINS', '515.123.8080', '1994-06-07', 'AC_MGR', 12000, NULL, 101, 110),
    (206, 'William', 'Gietz', 'WGIETZ', '515.123.8181', '1994-06-07', 'AC_ACCOUNT', 8300, NULL, 205, 110);
GO

INSERT INTO Locations (Location_ID, Location_Name)
VALUES
    (1400, 'Texas'),
    (1500, 'California'),
    (1700, 'Washington'),
    (1800, 'Canada'),
    (2500, 'London');
GO

-- Verify data
SELECT * FROM Departments;
SELECT * FROM Employees;
SELECT * FROM Locations;


-- Task 1
SELECT Employee_ID, Last_Name, Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(SALARY) 
    FROM Employees)
ORDER BY Salary ASC

-- Task 2
SELECT Employee_ID, Last_Name
FROM Employees
WHERE Department_ID IN (
    SELECT Department_ID
    FROM Employees
    WHERE Last_Name LIKE '%u%'
)

-- Task 3
SELECT Last_Name, Salary
FROM Employees
WHERE Manager_ID = (
    SELECT Employee_ID
    FROM Employees
    WHERE Last_Name = 'King'
)

-- Task 4
SELECT Department_ID, Last_Name, Job_ID
FROM Employees
WHERE Department_ID = (
    SELECT Department_ID
    FROM Departments
    WHERE Department_Name = 'Executive'
)

-- Task 5
SELECT Last_Name, Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
    WHERE Employee_ID IN (
        SELECT Manager_ID
        FROM Employees
    )
) AND Employee_ID NOT IN (
    SELECT Manager_ID
    FROM Employees    
)

-- Task 6
SELECT Employee_ID, Last_Name
FROM Employees
WHERE Department_ID = (
        SELECT Department_ID
        FROM Departments
        WHERE Location_ID = (
            SELECT Location_ID
            FROM Locations
            WHERE Location_Name = 'London'
        )
    )

-- Task 7
SELECT Employee_ID, Last_Name, Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
    WHERE Employee_ID IN (
        SELECT Manager_ID
        FROM Employees
    )
) AND Employee_ID NOT IN (
    SELECT Manager_ID
    FROM Employees    
)

-- Task 9
SELECT Last_Name, Job_ID, Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(SALARY) 
    FROM Employees
)

-- Task 10
SELECT Employee_ID, Last_Name, Department_ID
FROM Employees
WHERE Department_ID = (
    SELECT Department_ID
    FROM Departments
    WHERE Department_Name = 'Accounting'
)

-- Task 10
SELECT Last_Name, Salary AS LowestSalary
FROM Employees
WHERE Salary = (
    SELECT MIN(Salary)
    FROM Employees
)

```


---
### 04/07/26 - DCL Activity


```sql
CREATE TABLE Students_Record (

StudentID INT PRIMARY KEY,

StudentName VARCHAR(50),

Course VARCHAR(50)

);

  

INSERT INTO Students_Record VALUES

(1,'Ana Cruz','BSIT'),

(2,'Mark Reyes','BSCS'),

(3,'Liza Santos','BSIS');

  

CREATE LOGIN TeacherUser WITH PASSWORD='Teacher123!';

CREATE USER TeacherUser FOR LOGIN TeacherUser;

  

CREATE LOGIN RegistrarUser WITH PASSWORD='Registrar123!';

CREATE USER RegistrarUser FOR LOGIN RegistrarUser;

  

SELECT name, type_desc FROM sys.server_principals WHERE name IN ('TeacherUser', 'RegistrarUser');

SELECT name, type_desc FROM sys.database_principals WHERE name IN ('TeacherUser', 'RegistrarUser');

  

SELECT * FROM Students_Record

  

GRANT SELECT ON Students_Record TO TeacherUser;

GRANT INSERT, UPDATE ON Students_Record TO RegistrarUser;

  

REVOKE UPDATE ON Students_Record FROM RegistrarUser;

  
  
  

GRANT SELECT ON Students_Record TO TeacherUser;

GRANT INSERT, UPDATE ON Students_Record TO RegistrarUser;

  
  

REVOKE UPDATE ON Students_Record FROM RegistrarUser;

  

--1

SELECT grantee_principal_id, permission_name, state_desc

FROM sys.database_permissions

WHERE grantee_principal_id = USER_ID('TeacherUser')

AND permission_name = 'SELECT';

  

--2

SELECT grantee_principal_id, permission_name, state_desc

FROM sys.database_permissions

WHERE grantee_principal_id = USER_ID('RegistrarUser')

AND permission_name = 'INSERT';

  

--3

SELECT permission_name, state_desc

FROM sys.database_permissions

WHERE grantee_principal_id = USER_ID('RegistrarUser');
```


---

## Finals


### 04/28/26 - Cert Exam Prep

Database - organized, structured collection of data
DBMS - manages how data is stored, retrieved, updated, and protected

Table - like a spreadsheet
Column - also called field/attribute; 1 type of information
Row - also called record/tuple; 1 complete entry

Data Types (choosing the right container)
INT - whole numbers
VARCHAR(100) - variable text
CHAR(2) - fixed text
DECIMAL(10,2) - precise money
FLOAT - approximate decimal (scientific measurements)
DATE - year-month-day

SQL Basics
SELECT
- the most important command
- retrieves data from a table

SELECT full structure:
```sql
SELECT column1, column2        -- what to show
FROM TableName                 -- where the data lives
WHERE condition                -- filter rows (optional)

```



---

# 2nd Semester
## Prelim


### Date - Topic

#### Subtopic



---

## Midterm


### Date - Topic

#### Subtopic



---

## Finals


### Date - Topic

#### Subtopic





