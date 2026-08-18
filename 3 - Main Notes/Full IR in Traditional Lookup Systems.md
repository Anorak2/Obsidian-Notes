
2026-03-02

Tags: [[Information Retrieval]]
# Full IR in Traditional Lookup Systems
This section focuses on traditional document retrieval for cases like libraries

**Legacy Systems**
 - Apache [Lucene](https://github.com/apache/lucene) which is a very fast text based search system that allows you to scan a large number of files from a library.
- Google started a project to digitize every book, and as part of this push the book catalogs become a bottleneck. They looked into putting a single interface before a number of catalogs, but ended up with a distributed interface so that a user can search several different interfaces at the same time. 

Legacy standards for searching
- Standard Query Languages such as `Common Query Language`
- Distributed Searching such as `Z39.50`, `SRW` (Search/Retrieve Web Service), and `SRU` (Search/Retrieve URL)
- Nowadays these systems are primarily used in libraries

**Problems with broadcast search**
- The wait: if one collection doesn't respond the server waits for a timeout
- Recall: if that collection doesn't respond documents aren't found
- Ranking/Duplicates
This broadcast search model doesn't scale beyond about five to ten collections even with strict standards.

In **modern systems** since broadcast doesn't work we instead offer a number of improvements. First use vertical selection/routing so we look at particular collections first, second use asynchronous fan-out + partial results, and fuse the results by normalizing ranks and merging duplicates.

**Union Catalog:**
Catalog the records from several libraries into a single union catalog that can be easily searched.

# References
- [[Boolean Information Retrieval Model]]
- [[Vector Space Model]]
