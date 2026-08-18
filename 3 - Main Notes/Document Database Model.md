
2026-07-12

Tags: [[Databases]] [[Data]] [[Designing Data Intensive Applications]]
# Document Database Model
The document model is the newest attempt to replace the relational database model, and is representative of the nosql camp. It excels when data has a tree of 1-many relationships. It also does well with loose schemas, and when joins are less common.

Document-oriented databases like MongoDB, RethinkDB, CouchDB, and Espresso support this data model.

One way to use this model is to store complex objects using encoding formats such as JSON inside of a relational database. This approach can have better locality than a normalized, multi-table schema as well. In the multi-table version you may need to perform multiple queries on several tables or perform a messy multi-way join between tables. In the JSON approach all of the relevant data is already present.

##  Usecases?
If the data in the application has a document like tree of relationships that is often loaded at once, then it is probably good to use the database model. In this case shredding the data into multiple tables can lead to unnecessary schemas and complicated code.

However, if a document becomes too deeply nested then it can cause problems. Likewise if your application needs joins you may run into issues given document databases poor support.

For highly interconnected data the document model falls apart, the relational model is adequate, and the graph model is the most natural option.

# References
- [[NoSQL]]
- [[Relational Database Model]]
- [[Object Relational Mapping (ORM)]]
- [[Unstructured Data]]
- [[Graph Database Model]]