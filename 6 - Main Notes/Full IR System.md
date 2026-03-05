
2026-03-02

Tags: [[EECS 767]]
# Full IR System
## Traditional Lookup
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

## Modern Web Search
This section focuses on what is currently being done in integrated web IR systems.

| Pipelines     |                                                                                          |
| ------------- | ---------------------------------------------------------------------------------------- |
| Search Engine | crawl/connectors -> parsing/cleaning -> enrichment (language, entities, metadata)        |
| Indexing      | Shard + replicate, usually multiple indexes/fields (text, metadata, vectors)             |
| Query         | query understanding -> candidate generation (BM25) -> Re-ranking LTR / neural -> results |
**Proximity Searches** are now a thing where terms occur within K positions of another, such as K within 5 words of paper. Sometimes it is more vague or can be implemented differently, there is also phrases such as United States that are searched for.

**Query Parsers**
Free text query from the user may behind the scenes spawn one or more queries to the indexes, for example rising interest rates. We can run the query as a phrase query, and if K docs contain that phrase then run two phrases "rising interest" and "rising rates" and this can be repeated again.

**Query Understanding**
In the modern days we do a lot of steps
- Detect Query type
- Spelling correction + normalization
- Entity rewriting/expansion
- Generate multiple candidate interpretations and either choose or blend results.

**Ranking Revisited**
- Classic modes still matter, boolean/Inverted index + phrase/proximity
- Default baseline in practice includes searches like BM-25
- Spelling correction + normalization
- Learning to rank: combine features using BM25, proximity, freshness, authority, etc.
- Neural reranking: Cross-encoder/late-interaction models on top of the K candidates
- Hybrid retrieval: Sparse + dense fusion for semantic matching + exact matching

**Evaluation:**
- Standard document set (TREC)
- Standard queries
- Relevance assessed by experts

The ultimate goal is relevance, but part of the problem is that relevance isn't stable. In the old days a single domain expert judged the relevance between query and document. In TREC-2 they had a the documents re-judged by a second expert and the average agreement was about 80%. In TREC-4 all topics were re-judged by two assessor and there was an average about 72%.

Fundamental Question:
- Is user satisfied?
- is user successful 
In 2025:
- Offline: `nDCG@k`, `MRR`, `Recall@k`
- Online: A/B testing, interleaving,  click models. These models are optimized for user success and not just relevance.
- Key system metrics: latency, throughput, cost, tail latency





# References
- [[Boolean Information Retrieval Model]]
- [[Vector Space Model]]
