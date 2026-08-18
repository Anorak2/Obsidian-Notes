
2026-05-22

Tags: [[SQL]] [[Software Engineering (SWE)]]
# SQL C,R,U,D Rows
## INSERT
When inserting data into a database, we need to use an `INSERT` statement, which declares which table to write into, the columns of data that we are filling, and one or more rows of data to insert. In general, each row of data you insert should contain values for every corresponding column in the table. You can insert multiple rows at a time by just listing them sequentially.
```sql
INSERT INTO mytable
VALUES (value_or_expr, another_value_or_expr, …),
	(value_or_expr_2, another_value_or_expr_2, …),
	...;
```
If there is incomplete data columns can also be specified
```sql
INSERT INTO mytable (column, another_column, …)
	VALUES (value_or_expr, another_value_or_expr, …),
	...;
```
Part of the benefit is that with this approach if another column is added then the INSERT statement won't fail

## Update 
Similar to the `INSERT` statement, you have to specify exactly which table, columns, and rows to update. In addition, the data you are updating has to match the data type of the columns in the table schema.
```sql
UPDATE mytable
	SET column = value_or_expr,
	other_column = another_value_or_expr,
	… 
WHERE condition;`
```
Be extremely careful with update statements. One tip is to always write the constraint first and test it in a `SELECT` query to make sure you are updating the right rows, and only then writing the column/value pairs to update.

## Deleting
```sql
DELETE FROM mytable
WHERE condition;
```
A handy shortcut and something to be aware of is that without a `WHERE` statement all rows will be selected. It's also important to test with a `SELECT` first since it is very easy to permanently delete data. 

**Truncating**
This command deletes all rows from a table while preserving the structure of the table. Unlike DELETE it doesn't log individual row deletions, this makes it faster for large tables but also means that for most databases you can't roll it back after.

# References
- [[SQL Filtering (WHERE)]]