
2026-05-20

Tags: [[Databases]] [[SQL]] [[Software Engineering (SWE)]]
# SQL Filtering (WHERE)
## WHERE

If there are large tables then reading through all of the rows isn't usually what we want, and to restrict the scope we can enforce constraints. Constraints can also make queries faster since they prevent useless results from being sent, it's faster since queries exist closer to the data.

```sql
`SELECT column, another_column, 
 FROM mytable
 WHERE conditionc 
	AND/OR another_condition
	AND/OR …;
```


**Useful numerical operators include:**

| Operator            | Condition                                        | Example                       |
| ------------------- | ------------------------------------------------ | ----------------------------- |
| =, !=, <, <=, >, >= | The usual numerical operators                    | col_name != 4                 |
| BETWEEN […] AND […] | Number is within range of two values (inclusive) | col_name BETWEEN 1.5 AND 10.5 |
| IN [...]            | Number exists in a list                          | col_name IN (2, 4, 6)         |
| NOT IN [...]        | Number does not exist in a list                  | col_name NOT IN (1, 3, 5)     |

**Useful string operators include:**

| Operator     | Condition                                                                                             | Example                                                          |
| ------------ | ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| =            | Case sensitive exact string comparison                                                                | col_name = "abc"                                                 |
| !=           | Case sensitive inequality comparison                                                                  | col_name != "abc"                                                |
| LIKE         | Case insensitive exact string comparison                                                              | col_name LIKE "ABC"                                              |
| NOT LIKE     | Case insensitive inequality comparison                                                                | cole_name NOT LIKE "ABC"                                         |
| %            | Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE) | col_name LIKE "%AT%"  <br>(matches "AT", "ATTIC", "CAT", "BATS") |
| _ underscore | Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)                    | col_name LIKE "AN_"  <br>(matches "AND", but not "AN")           |
| IN [...]     | String exists in a list                                                                               | col_name IN ("A", "B", "C")                                      |
| NOT IN [...] | String does not exist in a list                                                                       | col_name NOT IN ("D", "E", "F")                                  |

## DISTINCT
Even though the data in a database may be unique, the results of any particular query may not be. In such cases, SQL provides a way to discard rows that have a duplicate column value by using the `DISTINCT` keyword.

```sql
SELECT DISTINCT column, another_column, … FROM mytable
WHERE _condition(s)_;
```

## ORDER BY
Since databases tend to store things in no particular order if we want an ordering we can do that with the `ORDER BY` keyword
```sql
SELECT column, another_column, … FROM mytable 
WHERE condition(s)
ORDER BY column ASC/DESC
```

## LIMIT and OFFSET
Often used with the `ORDER BY` clause is the `LIMIT` and `OFFSET` clauses which further indicate to the database which subset of results you care about. The `LIMIT` clause tells the database how many results to return, and the `OFFSET` specifies where to begin counting rows from.
```sql
SELECT column, another_column, …
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```
This could be used, for example, to return the 5 most liked posts or the 20 users with a highest balance etc.

## NULL
If nulls can't be avoided then the following can be used:
```sql
WHERE column IS/IS NOT NULL
```
# References
- [[SQL]]
- [[SQL Queries (SELECT)]]