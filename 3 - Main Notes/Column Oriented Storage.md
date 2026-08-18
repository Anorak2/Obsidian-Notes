
2026-07-17

Tags: [[Data Systems]]
# Column Oriented Storage
When there are trillions of rows in fact tables storing and querying these tables efficiently is difficult. Fortunately, the naive model has waste. This is because even though fact tables can be wide in the hundreds, most queries only access ~5 at a time. This leads to the idea, what if we store all values from each column together rather than grouping by row. Each column can be stored independently in it's own file so that a query only needs to parse the columns that are relevant.

**Column compression**


# References
- [[Data Warehousing]]
- [[Star and Snowflake Schema]]