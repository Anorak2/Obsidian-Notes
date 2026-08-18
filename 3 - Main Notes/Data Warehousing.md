
2026-07-17

Tags: [[Data Systems]]
# Data Warehousing
Large enterprises can have dozens of different systems that each have their own data-stores and teams to maintain them, and often these systems behave fully independently of eachother. These teams typically don't want to let analysts onto their systems since they often run expensive queries that scan large parts of the dataset, harming the performance of the system. To solve this problem a separate database called a data warehouse was invented.

These systems are fully independent, that analysts can query without any restrictions and without interfering with operations. Warehouses contain a read only copy of the data in all the various OLTP systems in the company.

Unfortunately, the indexing models that work well for OLTP query patterns, such as LSM-Trees and B-Trees, don't work as well for analysis. Thus new models were created. In particular the star/snowflake model, and the column oriented storage models are generally more efficient for analytics.


# References
- [[LSM Trees]]
- [[B-Trees]]
- [[Star and Snowflake Schema]]
- [[Column Oriented Storage]]