
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




---

## Finals


### Date - Topic

#### Subtopic



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





