
2026-05-20

Tags: [[Languages]] 
# SQL Joins
Using the `JOIN` clause in a query, we can combine row data across two separate tables using this unique key.

```sql
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table 
    ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column, … ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

![[Pasted image 20260520153151.png]]

To briefly hit the most important ones, inner joins only take values in both tables. 
# References
- [[SQL Joins]]