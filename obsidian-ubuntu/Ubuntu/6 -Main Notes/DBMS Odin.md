
2025-09-26  18:30

Tags: [[Coding]] [[Database]] 

# Database Management System


A basic definition of a database is simple "a structured set of data held in a computer."

A database can be described as the spreadsheet; the tables as the worksheet; the rows as the relational data; the column as the data with the same type.

A database is a more powerful and sophisticated version of spreadsheets. It can handle much larger data and is more efficient in query, insertion, and modification of data.

A relational database is a database organized according to the relational model of data. In simple terms, the relational model defines a set of relations (which we can think of as analogous to tables) and describes the relationships, or connections, between them in order to determine how the data stored in them can interact.

All data types:
```
INTEGER
TEXT
BLANK PRIMARY KEY
```

Create a table:
```
CREATE TABLE table_name (variable DATA_TYPE, variable DATA_TYPE);
```

Insert an item:
```
INSERT INTO table_name VALUES (variable, variable);
```

Find an item based on its column:
```
SELECT column_name FROM table_name;
```

Find all items in a table:
```
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

Functions:
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





# References