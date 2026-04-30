
2026-04-30  05:19 pm

Tags: [[Coding]], [[SQL]], [[The Odin Project]]

---
# SQL From SQLBolt


## 01 - SELECT
*Retrieve data*

```sql
-- Complete SELECT Query

SELECT DISTINCT column, AGG_FUNC(column_or_expression), … 
FROM mytable 
	JOIN another_table 
		ON mytable.column = another_table.column 
	WHERE constraint_expression
	GROUP BY column 
	HAVING constraint_expression
	ORDER BY column ASC/DESC 
	LIMIT count_num OFFSET count_num
;
```

Each query begins with finding the data that we need in a database, and then filtering that data down into something that can be processed and understood as quickly as possible. Because each part of the query is executed sequentially, it's important to understand the order of execution so that you know what results are accessible where.

### Query order of execution

#### 1. `FROM` and `JOIN`s

The `FROM` clause, and subsequent `JOIN`s are first executed to determine the total working set of data that is being queried. This includes subqueries in this clause, and can cause temporary tables to be created under the hood containing all the columns and rows of the tables being joined.

#### 2. `WHERE`

Once we have the total working set of data, the first-pass `WHERE` constraints are applied to the individual rows, and rows that do not satisfy the constraint are discarded. Each of the constraints can only access columns directly from the tables requested in the `FROM` clause. Aliases in the `SELECT` part of the query are not accessible in most databases since they may include expressions dependent on parts of the query that have not yet executed.

#### 3. `GROUP BY`

The remaining rows after the `WHERE` constraints are applied are then grouped based on common values in the column specified in the `GROUP BY` clause. As a result of the grouping, there will only be as many rows as there are unique values in that column. Implicitly, this means that you should only need to use this when you have aggregate functions in your query.

#### 4. `HAVING`

If the query has a `GROUP BY` clause, then the constraints in the `HAVING` clause are then applied to the grouped rows, discard the grouped rows that don't satisfy the constraint. Like the `WHERE` clause, aliases are also not accessible from this step in most databases.

#### 5. `SELECT`

Any expressions in the `SELECT` part of the query are finally computed.

#### 6. `DISTINCT`

Of the remaining rows, rows with duplicate values in the column marked as `DISTINCT` will be discarded.

#### 7. `ORDER BY`

If an order is specified by the `ORDER BY` clause, the rows are then sorted by the specified data in either ascending or descending order. Since all the expressions in the `SELECT` part of the query have been computed, you can reference aliases in this clause.

#### 8. `LIMIT` / `OFFSET`

Finally, the rows that fall outside the range specified by the `LIMIT` and `OFFSET` are discarded, leaving the final set of rows to be returned from the query.

### Conclusion

Not every query needs to have all the parts we listed above, but a part of why SQL is so flexible is that it allows developers and data analysts to quickly manipulate data without having to write additional code, all just by using the above clauses.


---

## 02 - INSERT
*Insert data*

Syntax:

```sql
INSERT INTO mytable (column, another_column, …) 
VALUES
	(value_or_expr, another_value_or_expr, …), 
	(value_or_expr_2, another_value_or_expr_2, …),
	…
;
```

Copy-paste:

```sql
INSERT INTO mytable (column) 
VALUES
	(value),
;
```

---

## 03 - UPDATE
*Update existing data*

Syntax/Copy-paste:

```sql
UPDATE mytable
SET column = value_or_expr, 
	other_column = another_value_or_expr
WHERE condition;
```

#### Careful Advice:

One helpful tip is to always write the constraint first and test it in a `SELECT` query to make sure you are updating the right rows, and only then writing the column/value pairs to update.


---

## 04 - DELETE
*Delete existing data*

Syntax/Copy-paste:

```sql
DELETE FROM mytable 
WHERE condition;
```

#### Careful Advice:

Like the `UPDATE` statement from last lesson, it's recommended that you run the constraint in a `SELECT` query first to ensure that you are removing the right rows. Without a proper backup or test database, it is downright easy to irrevocably remove data, so **always read your `DELETE` statements twice and execute once**.


---

## 05 - CREATE
*Create a new table*

Syntax:

```sql
-- Create table statement w/ optional table constraint and default value

CREATE TABLE IF NOT EXISTS mytable (
	column DataType TableConstraint DEFAULT default_value,
	another_column DataType TableConstraint DEFAULT default_value, 
	… 
);
```

Copy-paste:

```sql
CREATE TABLE IF NOT EXISTS mytable (
	column DataType,
	another_column DataType
);
```

### Table Data Types

| Data type                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `INTEGER`,<br>`BOOLEAN`                                    | The integer datatypes can store whole integer values like the count of a number or an age.<br><br>In some implementations, the boolean value is just represented as an integer value of just 0 or 1.                                                                                                                                                                                                                                                   |
|                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `FLOAT`,<br>`DOUBLE`,<br>`REAL`                            | The floating point datatypes can store more precise numerical data like measurements or fractional values. <br><br>Different types can be used depending on the floating point precision required for that value.                                                                                                                                                                                                                                      |
|                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `CHARACTER(num_chars)`,<br>`VARCHAR(num_chars)`,<br>`TEXT` | The text based datatypes can store strings and text in all sorts of locales. The distinction between the various types generally amount to underlaying efficiency of the database when working with these columns.<br><br>Both the CHARACTER and VARCHAR (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables. |
|                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `DATE`,<br>`DATETIME`                                      | SQL can also store date and time stamps to keep track of time series and event data. They can be tricky to work with especially when manipulating data across timezones.                                                                                                                                                                                                                                                                               |
|                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `BLOB`                                                     | Finally, SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them.                                                                                                                                                                                                                                                           |
|                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Docs: <br>                                                 | - [MySQL](http://dev.mysql.com/doc/refman/5.6/en/data-types.html "MySQL Data Types"),<br>- [Postgres](http://www.postgresql.org/docs/9.4/static/datatype.html "Postgres Data Types"), <br>- [SQLite](https://www.sqlite.org/datatype3.html "SQLite Data Types"), <br>- [Microsoft SQL Server](https://msdn.microsoft.com/en-us/library/ms187752.aspx "Microsoft SQL Server Data Types")                                                                |

### Table Constraints

We aren't going to dive too deep into table constraints in this lesson, but each column can have additional table constraints on it which limit what values can be inserted into that column. This is not a comprehensive list, but will show a few common constraints that you might find useful.

| Constraint           | Description                                                                                                                                                                                                                                                                                                                                                                                        |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `PRIMARY KEY`        | This means that the values in this column are unique, and each value can be used to identify a single row in this table.                                                                                                                                                                                                                                                                           |
|                      |                                                                                                                                                                                                                                                                                                                                                                                                    |
| `AUTOINCREMENT`      | For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases.                                                                                                                                                                                                                                                  |
|                      |                                                                                                                                                                                                                                                                                                                                                                                                    |
| `UNIQUE`             | This means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table. Differs from the `PRIMARY KEY` in that it doesn't have to be a key for a row in the table.                                                                                                                                            |
|                      |                                                                                                                                                                                                                                                                                                                                                                                                    |
| `NOT NULL`           | This means that the inserted value can not be `NULL`.                                                                                                                                                                                                                                                                                                                                              |
|                      |                                                                                                                                                                                                                                                                                                                                                                                                    |
| `CHECK (expression)` | This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc.                                                                                                                                                                         |
|                      |                                                                                                                                                                                                                                                                                                                                                                                                    |
| `FOREIGN KEY`        | This is a consistency check which ensures that each value in this column corresponds to another value in a column in another table.  <br>  <br>For example, if there are two tables, one listing all Employees by ID, and another listing their payroll information, the `FOREIGN KEY` can ensure that every row in the payroll table corresponds to a valid employee in the master Employee list. |


---

## 06 - ALTER

Add column/s:

```sql
ALTER TABLE mytable
ADD column DataType
	OptionalTableConstraint
	DEFAULT default_value
;
```

Remove column/s:

```sql
ALTER TABLE mytable
DROP column_to_be_deleted;
```

Rename the table:

```sql
ALTER TABLE mytable
RENAME TO new_table_name;
```


Each database implementation supports different methods of altering their tables, so it's always best to consult your database docs before proceeding: 
- [MySQL](https://dev.mysql.com/doc/refman/5.6/en/alter-table.html "MySQL Alter Table"), 
- [Postgres](http://www.postgresql.org/docs/9.4/static/sql-altertable.html "Postgres Alter Table"), 
- [SQLite](https://www.sqlite.org/lang_altertable.html "SQLite Alter Table"), 
- [Microsoft SQL Server](https://msdn.microsoft.com/en-us/library/ms190273.aspx "Microsoft SQL Server Alter Table")


---

## 07 - DROP

```sql
DROP TABLE IF EXISTS mytable;
```

`DROP` differs from the `DELETE` statement in that it also removes the table schema from the database entirely.

In addition, if you have another table that is dependent on columns in table you are removing (for example, with a `FOREIGN KEY` dependency) then you will have to either update all dependent tables first to remove the dependent rows or to remove those tables entirely.


---

## 08 - Subqueries

```sql
SELECT * 
FROM sales_associates 
WHERE salary > (
	SELECT AVG(revenue_generated) 
	FROM sales_associates)
;
```

A subquery can be referenced anywhere a normal table can be referenced.
- inside a `FROM` clause, you can `JOIN` subqueries with other tables, 
- inside a `WHERE` or `HAVING` constraint, you can test expressions against the results of the subquery, 
- and even in expressions in the `SELECT` clause, which allow you to return data directly from the subquery

If possible, try and give meaningful aliases to the temporary values and tables. 

In addition, correlated subqueries can be difficult to optimize, so performance characteristics may vary across different databases.

### `IN` and Subqueries

The `IN` operator is used to test whether the column value in the current row existed in a fixed list of values. In complex queries, this can be extended using subqueries to test whether a column value exists in a dynamic list of values.

```sql
SELECT *,
FROM mytable 
	WHERE column IN/NOT IN (
		SELECT another_column 
		FROM another_table);
```

When doing this, notice that the inner subquery must select for a column value or expression to produce a list that the outer column value can be tested against.

This type of constraint is powerful when the constraints are based on current data.


---

## 09 - Unions, Intersections, and Exceptions

These operators **assume that both tables have the samecolumn count, order, and data type**.

```sql
SELECT column, another_column 
	FROM mytable 
UNION / UNION ALL / INTERSECT / EXCEPT 
SELECT other_column, yet_another_column 
	FROM another_table 
ORDER BY column DESC
LIMIT n;
```


It's not common to use `UNION`s, but if you have data in different tables that can't be joined and processed, it can be an alternative to making multiple queries on the database.


---
# References

https://sqlbolt.com/