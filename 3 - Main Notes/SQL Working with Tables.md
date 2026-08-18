
2026-05-22

Tags: [[Languages]] [[Software Engineering (SWE)]]
# SQL Working with Tables
## Datatypes and Constraints

| Data Type                                            | Description                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Integer`, `Boolean`                                 | The integer datatypes can store whole integer values like the count of a number or an age.                                                                                                                                                                                                               |
| `Float`, `Double`, `Real`                            | The floating point datatypes can store more precise numerical data like measurements or fractional values. Different types are used based on the level of floating point precision.                                                                                                                      |
| `CHARACTER(num_chars)`, `VARCHAR(num_chars)`, `TEXT` | The text based datatypes can store strings and text in all sorts of locales. Both the CHARACTER and VARCHAR (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables |
| `DATE`, `DATETIME`                                   | SQL can also store date and time stamps to keep track of time series and event data.                                                                                                                                                                                                                     |
| `BLOB`                                               | SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them.                                                                                                                      |

| Table Constraints   | Description                                                                                                                                                                                                                |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `PRIMARY KEY`       | This means that the values in this column are unique, and each value can be used to identify a single row in this table.                                                                                                   |
| `AUTOINCREMENT`     | For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases.                                                                          |
| `UNIQUE`            | Differs from the `PRIMARY KEY` in that it doesn't have to be a key for a row in the table.                                                                                                                                 |
| `NOT NULL`          | This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc. |
| `CHECK(expression)` |                                                                                                                                                                                                                            |
| `FOREIGN KEY`       | ensures that each value in this column corresponds to another value in a column in another table                                                                                                                           |

## Creating Tables
```sql
CREATE TABLE IF NOT EXISTS mytable (
	column DataType TableConstraint DEFAULT default_value,
	anothercolumn DataType TableConstraint DEFAULT default_value,
	… 
);`
```
If there already exists a table with the same name, the SQL implementation will usually throw an error, so to suppress the error and skip creating a table if one exists, you can use the `IF NOT EXISTS` clause.

## Altering Tables
To add a new table the following can be used. Some databases also support where to add the column using `FIRST` and `AFTER` tags but this isn't standard.
```sql
ALTER TABLE mytable
ADD column DataType OptionalTableConstraint
	DEFAULT default_value;
```

Not all databases support dropping a column, such as SQLite, so instead you may have to create a new table and migrate the data.
```sql 
ALTER TABLE mytable
DROP column_to_be_deleted;
```

To rename a table
```sql
ALTER TABLE mytable
RENAME TO new_table_name;
```
## Dropping Tables
If you want to remove an entire table and it's metadata. if you have another table that is dependent on columns in table you are removing (for example, with a `FOREIGN KEY` dependency) then you will have to either update all dependent tables first to remove the dependent rows or to remove those tables entirely.
```sql
DROP TABLE IF EXISTS mytable;
```

# References
- [[SQL Filtering (WHERE)]]