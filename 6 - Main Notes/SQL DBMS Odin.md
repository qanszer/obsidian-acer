
2025-09-26  18:30

Tags: [[Coding]] [[Database]] [[SQL]] [[Odin]]

---

# Structured Query Language & Database Management System


## Definition and Overview

A basic definition of a database is simply "a structured set of data held in a computer."

A **database** can be described as the **spreadsheet**;
the **tables** as the **worksheet**; 
the **rows** as the **relational data**; 
the **column** as the **data with the same type**.

A **database is a more powerful and sophisticated** version of spreadsheets. It can handle much larger data and is more efficient in query, insertion, and modification of data.

A **relational database** is a database organized according to the relational model of data. In simple terms, the relational model **defines a set of relations** (which we can think of as analogous to tables) and **describes the relationships**, or connections, between them in order to determine how the data stored in them can interact.


---

## Master List

**ALL CLAUSES**

```sql
SELECT
DISTINCT
FROM
(INNER/RIGHT, LEFT, OUTER) JOIN .. ON
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT .. OFFSET
CASE
```


**ALL FUNCTIONS**

```sql
AVG
SUM
COUNT
MAX
MIN
UPPER
LOWER
LIKE
COALESCE
```


**OTHERS**

```sql
AS
AND/OR
IN
NULL (IS NULL/IS NOT NULL)
BETWEEN
```


---

## Syntax Guides, Examples, and Good Practices

The following are long or short syntax guides for SQL commands and processes.

### Create a table

**Syntax**
```sql
CREATE TABLE TableName (
	variable DATA_TYPE,
	variable DATA_TYPE
);
```

**Example with Foreign Key**
```sql
CREATE TABLE Inventory (
  InventoryID INT PRIMARY KEY, -- PK
  ProductID INT NOT NULL, -- FK Column Declaration
  QuantityOnHand INT NOT NULL,
  UnitCost INT NOT NULL,
  RetailPrice INT NOT NULL,
  CONSTRAINT FK_Inventory_Products -- FK
  FOREIGN KEY (ProductID)
  REFERENCES Products(ProductID)
);
```

**For Copy Paste**
```sql
CREATE TABLE TableName (
  ColumnName INT PRIMARY KEY, -- PK
  ColumnName INT NOT NULL, -- FK Column Declaration
  ColumnName VARCHAR(100) NOT NULL,
  ColumnName NVARCHAR(100) NOT NULL,
  ColumnName DECIMAL NOT NULL,
  CONSTRAINT FK_TableName_TableName -- FK
  FOREIGN KEY (ForeignTableID)
  REFERENCES ForeignTable(ForeignTableID)
);
```


### Insert an item

**Syntax**
```sql
INSERT INTO TableName
	VALUES
		(value, 'value'),
		(value, 'value');
```

**Good Practice / Example**
- Add a column description on top for easier viewing
- Use `[]` for sql keyword column names when necessary (makes the compiler ignore it as a keyword)
```sql
INSERT INTO Products (ProductID, ProductName, Category, [Date])
	VALUES 
	  (1, 'Magic Sarap', 'Cooking', 'YYYY-MM-DD'),
	  (2, 'Marlboro Light', 'Cigarette', '2025-02-23'),
	  (3, 'Pochi', 'Snacks & Candies', '2026-02-23');
```

**For Copy Paste**
```sql
INSERT INTO TableName (ColumnName, [ColumnName], ColumnName)
	VALUES 
	  (value, value, value),
	  (value, value, value);
```


Find an item based on its column:
```sql
SELECT column_name FROM table_name;
```

Find all items in a table:
```sql
SELECT * FROM table_name;
```

![[Pasted image 20250926183024.png]]

Order the items according to 1 column:
```
SELECT * FROM table_name ORDER BY column3;
```

Find items based on your condition:
```
SELECT * FROM table_name WHERE column3 > 5 ORDER BY column3;
```
(This presents all items that are above 5 on column3)



AGGREGATE function - useful for getting the maximum, minimum, sum of values in a database
```
MAX
SUM
MIN
```

Sums up all of the items in the selected column:
```
SELECT SUM(column_name) FROM table_name;
```

Sums up all of the items in the selected column, while still retaining each item:
```
SELECT column2, SUM(column1) FROM table_name GROUP BY column2;
```


# Functions:

Example = SELECT COUNT( * ) FROM favorites;

```
AVG
COUNT
DISTINCT
LOWER
MAX
MIN
UPPER

GROUP BY
LIKE
LIMIT
ORDER BY
WHERE
```

NULL - conscious deliberate absence of a value in SQL




Shows clear expertise of the subject
Easy-to-understand teaching style
A very understanding professor. Displays Adamsonian values
Thank you for all the effort you've given to teaching us, ma'am!



# SQL Teaching

### SELECT

```sql
SELECT * FROM family_members;
```

### SELECT specific columns

```sql
SELECT name, num_books_read FROM family_members;
```

### WHERE ... Equals

```sql
SELECT * FROM family_members WHERE species = 'human';
```

### WHERE ... Greater than

```sql
SELECT * FROM family_members WHERE num_books_read > 0;
```

### WHERE .. Greater than or equal

```sql
SQL accepts various inequality symbols, including:  
`=` "equal to"  
`>` "greater than"  
`<` "less than"  
`>=` "greater than or equal to"  
`<=` "less than or equal to"
```

### AND

```sql
SELECT * FROM friends_of_pickles WHERE height_cm > 25 AND species = 'cat';
```

### OR

```sql
SELECT * FROM friends_of_pickles WHERE height_cm > 25 OR species = 'cat';
```

### IN

```sql
SELECT * FROM friends_of_pickles WHERE species IN ('cat', 'human');
```

### DISTINCT

```sql
SELECT DISTINCT gender, species FROM friends_of_pickles WHERE height_cm < 100;
```

### ORDER BY

```sql
SELECT * FROM friends_of_pickles ORDER BY name;
```

### LIMIT # of returned rows

```sql
SELECT * FROM friends_of_pickles ORDER BY height_cm LIMIT 2;
```

### COUNT( * )

```sql
SELECT COUNT(*) FROM friends_of_pickles;
```

### COUNT( * ) ... WHERE

```sql
SELECT COUNT(*) FROM friends_of_pickles WHERE species = 'human';
```

### SUM

```sql
SELECT SUM(num_legs) FROM family_members;
```

### AVG 

```sql
SELECT AVG(num_legs) FROM family_members;
```

### MAX and MIN

```sql
SELECT MIN(num_legs) FROM family_members;
```

### GROUP BY

```sql
SELECT COUNT(*), species FROM friends_of_pickles GROUP BY species;
```

### Nested queries

```sql
SELECT * FROM family_members WHERE num_legs = (SELECT MIN(num_legs) FROM family_members);
```

### NULL

```sql
Sometimes, in a given row, there is no value at all for a given column. For example, a dog does not have a favorite book, so in that case there is no point in putting a value in the _favorite_book_ column, and the value is `NULL`. In order to find the rows where the value for a column is or is not `NULL`, you would use `IS NULL` or `IS NOT NULL`.
```

### Date

```sql
SELECT * FROM celebs_born WHERE birthdate < '1985-08-17';
```

### Inner joins

```sql
SELECT character.name, character_tv_show.tv_show_name  
FROM character  
INNER JOIN character_tv_show  
ON character.id = character_tv_show.character_id;
```

### Multiple joins

```sql
SELECT character.name, tv_show.name  
FROM character  
INNER JOIN character_tv_show  
ON character.id = character_tv_show.character_id  
INNER JOIN tv_show  
ON character_tv_show.tv_show_id = tv_show.id;
```

### Joins with WHERE

```sql
SELECT character.name, tv_show.name  
FROM character  
INNER JOIN character_tv_show  
ON character.id = character_tv_show.character_id  
INNER JOIN tv_show  
ON character_tv_show.tv_show_id = tv_show.id WHERE character.name != 'Barney Stinson' AND tv_show.name != 'Buffy the Vampire Slayer';
```

### Left joins

```sql
SELECT character.name, tv_show.name  
FROM character  
LEFT JOIN character_tv_show  
ON character.id = character_tv_show.character_id  
LEFT JOIN tv_show  
ON character_tv_show.tv_show_id = tv_show.id;
```

### Table alias

```sql
SELECT c.name, t.name  
FROM character AS c  
LEFT JOIN character_tv_show AS ct  
ON c.id = ct.character_id  
LEFT JOIN tv_show AS t  
ON ct.tv_show_id = t.id;
```

### Column Alias

```sql
SELECT character.name AS character, tv_show.name AS tv_show  
FROM character  
LEFT JOIN character_tv_show  
ON character.id = character_tv_show.character_id  
LEFT JOIN tv_show  
ON character_tv_show.tv_show_id = tv_show.id;
```

### Self joins

```sql
SELECT r1.name AS object, r2.name AS beats  
FROM rps AS r1  
INNER JOIN rps AS r2  
ON r1.defeats_id = r2.id;
```

### LIKE

```sql
SELECT * FROM robots WHERE name LIKE "%Robot%";
```

### CASE

```sql
CASE WHEN *first thing is true* THEN *value1*  
WHEN *second thing is true* THEN *value2*  
...  
ELSE *value for all other situations*  
END


SELECT *,  
CASE WHEN species = 'human' THEN 2 ELSE 4 END AS num_legs  
FROM friends_of_pickles;
```

### SUBSTR

```sql
SUBSTR(_column_name_, _index_, _number_of_characters_)


`SUBSTR(name, 1, 5)` is the first 5 characters of the name.  
`SUBSTR(name, -4)` is the last 4 characters of the name.  
  
`SELECT * FROM robots WHERE SUBSTR(name, -4) LIKE '20__';` is another way of returning all of the robots that have been released between 2000 and 2099.
```

### COALESCE

```sql
SELECT name, COALESCE(gun, sword) AS weapon FROM fighters;
```




# SQL Bolt


### Query Order of Execution

1. FROM and JOINs
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. DISTINCT
7. ORDER BY
8. LIMIT / OFFSET



Only use GROUP BY if you will use an aggregate function.

The HAVING clause only applies to the rows made by GROUP BY





# Good Practices


**When updating or deleting from a table, always start with `WHERE`**

```mssql
UPDATE Student
	SET Name = "Jayson Ocampo"
	WHERE ID = "0001"
```

Here, type `WHERE` first before anything else. Because forgetting the `WHERE` parameter, usually when you're tired, costs millions of dollars to fix


**When inserting values into a table, add a column indicator**

```mssql
INSERT INTO Student(Id,[Name],Course)
	Values (001, 'Jayson Ocampo', 'IT')
```

Also, you can use `[]` if the word you use for the column indicator is a keyword


**Use Stored Procedures to have reusable functions for established databases**




---

# References

https://www.theodinproject.com/lessons/node-path-databases
https://www.theodinproject.com/lessons/node-path-databases-databases-and-sql
https://www.sqlteaching.com/#!coalesce