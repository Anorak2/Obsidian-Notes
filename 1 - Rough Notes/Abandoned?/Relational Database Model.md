
2024-12-23

Tags: [[Databases]] [[Data Systems]]
# Relational Models
A relational database is a number of tuples with a defined format, each assigned to a table. This is by far the most popular and influential data model, and it has dominated the industry for an entire ~40 years at time of writing. Relational models are generally very capable, however critics say that strict schemas are restricting. 

In cases where the data has a tree-like dependency of 1-many relationships a document data model may be better, and in cases where everything could be connected to everything (many-many) a graph data model may be better. That said even in those cases relational models are able to proceed, granted with difficulty.

## Definition
it defines:
- Names of relations or tables in the database
- The attributes or columns of each table, i.e., the column name and the data types of each column
- Integrity constraints, i.e., conditions that data entered into the tables is required to satisfy

Each table has:
- A name
- A sequence of attributes (columns), and
- A set of tuples (rows)
## Formal Definition
Formally, a relation (table) is a subset of the Cartesian product of the domains of the column data types
- A relation in the mathematical sense
- Given n domains are denoted by $D_1, D_2, … D_n$ and
- r is a relation defined on these domains, then
- r ⊆ D1 × D2 × … × Dn

## Drawbacks
SQL struggles to deal with many to many relationships, since when a database is normalized many awkward joins can be required in order to reassemble the data. If we instead choose to store an entire JSON or XML document inside of a text field then we lose the ability to query this data on the database layer, instead having to handle it at the application layer.

## Convergence with Document Models
Most relational databases have supported XML since the mid 2000's, including the ability to make local changes to an XML document and query inside an XML document. PostgreSQL has had this ability for JSON since version 9.3 (Released September 2013)
# References
- [[Structured Data*]]
- [[SQL]]
- [[Normalization- The Normal Forms (NF)]]
- [[JSON]]
- [[XML]]
- [[Document Database Model]]
- [[Graph Database Model]]
- [[PostgreSQL]]