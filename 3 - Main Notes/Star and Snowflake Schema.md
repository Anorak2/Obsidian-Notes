
2026-07-17

Tags: [[Data Systems]] [[Data]] [[Data Structures]]
# Star and Snowflake Schema
## Star Schema
At the center of this schema is what is called a **fact table.** Each row of the table represents an event that occurred at some time, such as a customers purchase. Usually facts are captured individually since that provides the most flexibility for analysis, but in large organizations this could mean petabytes of fact tables. 

Some of the columns in the fact tables can be primitive attributes, but a column could also be a foreign key reference to what is called a **dimension table**. These tables allow for extra data to be encoded without further increasing the size of the fact tables. In practice, these tables can have over one hundred columns and up to several hundred. Dimension tables can have similarly large number of columns, for example if I am growing and selling fruit as part of the product line. That schema might store the fruit type, fertilizer type, plant date, harvest date, location grown, the cargo ship company, date transport started, date it arrived, and so on. All of these could provide information leading to major changes in the company.

![[Pasted image 20260717174140.png]]

## Snowflake Schema
This is a more normalized version of the star schema, where multiple fact tables are kept. This breaks dimensions down further into sub dimensions, but aren't typically preferred since star schemas are easier to work with.
## Column Oriented Storage
This is an optimization technique used to improve the efficiency of large queries, and more detail can be found in the dedicated page.
# References
- [[Data Warehousing]] 
- [[Column Oriented Storage]]