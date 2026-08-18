
2026-05-20

Tags: [[Languages]] [[Software Engineering (SWE)]]
# SQL Aggregation

## Functions
SQL Aggregation ways are an easy way to summarize information about groups of rows of data. Below are some common ones but it is database specific.

| Function       | Description                                                                                                                                                                                     |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| COUNT(column), | A common function used to counts the number of rows in the group if no column name is specified. Otherwise, count the number of rows in the group with non-NULL values in the specified column. |
| MIN(column)    | Finds the smallest numerical value in the specified column for all rows in the group.                                                                                                           |
| MAX(column)    | Finds the largest numerical value in the specified column for all rows in the group.                                                                                                            |
| AVG(column)    | Finds the average numerical value in the specified column for all rows in the group.                                                                                                            |
| SUM(column)    | Finds the sum of all numerical values in the specified column for the rows in the group.                                                                                                        |

## GROUP BY
In addition to aggregating across all the rows, you can instead apply the aggregate functions to individual groups of data within that group. This create as many results as there are unique groups defined as by the `GROUP BY` clause.
```sql
SELECT AGG_FUNC(_column_or_expression_) AS aggregate_description, …
FROM mytable 
WHERE _constraint_expression_ 
GROUP BY column;
```

## HAVING 
Since Where clauses execute before a `GROUP BY` clause, this means we can't actually filter down the groups without the `HAVING` statement. The `HAVING` clause constraints are written the same way as the `WHERE` clause constraints, and are applied to the grouped rows.
```sql
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, … 
FROM mytable 
WHERE conditio 
GROUP BY column
 HAVING group_condition;
```

# References
- [[SQL Queries (SELECT)]]
- [[SQL Filtering (WHERE)]]