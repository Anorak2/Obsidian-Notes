
2025-01-08

Status:

Tags: [[Databases]] [[Servers]]
# Database Federation
A federated database is a way of combining multiple databases into a single network rather than having a single monolithic database. Some key benefits include scalability and performance by enabling workloads to be shared across multiple locations

**Components**
- Source data and Databases: represents various databases that contain transactional/current data
- Data Federation: This is a virtual layer that integrates the data from the source databases that allows for users to use the database without needing to know how it works ([[Transparency]])
- Data Warehouse and Data Marts: stores historical data for reporting and analysis
- Business Intelligence: represents the tools and applications used for data reporting, analysis, and reporting.

#### Composite
This means taking multiple databases and integrating them so that they can be accessed as if they were a single database. This system uses a central management system in order to manage the integration.

features:
- Centralized query processing
- Unified schema
- High control over access and integration
#### Multi-database System
This is a slightly less tight form of coupling without having a central federated schema. Each database is independent, and the MDBS handles query distribution and result aggregation.

features:
- Centralized Query processing
- Decentralized control
- Autonomy of individual systems
- Heterogeneous database support
#### Virtual Database Federation
This is when you use virtual databases to provide a unified view of multiple underlying databases. The data stays in the databases, and the virtual layer translates and integrates data as it happens.

features:
- No data duplication
- Real time data integration
- Dynamic query translation and integration
#### Middleware Based Federation
This means sitting between the application and the databases, providing a federated interface. The middleware handles query routing, data integration, etc. I imagine this as functioning similarly an [[API]].

features:
- The middleware handles a bunch of stuff for you
- Flexible architecture
- Easier to do data integration
#### Hybrid Database Federation
You can also just mix and match other shit from the other types, such as virtual federation for real time access and a data warehouse for storage/analysis. 

features:
- Combine real time access and historical data
- Flexible architecture since F it we ball
- Good data integration capabilities

# References
[[Distributed Databases and Sharding]]