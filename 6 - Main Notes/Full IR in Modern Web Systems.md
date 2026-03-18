
2026-03-09

Tags: [[EECS 767]] 
# Full IR in Modern Web Systems
This section focuses on what is currently being done in integrated web IR systems.

![[Pasted image 20260309145932.png]]
Fig 1. Example of what the complete IR web model could look like
## Queries
There are a ton of different query types including Boolean Queries, Vector Queries, Extended-Boolean Queries, Fuzzy Queries, Probabilistic Queries, Natural Language Queries, Others?

**Boolean Model**
This is the earliest query model as well as one of the simplest, it is composed of simple Terms and Operators. Terms can include words, normalized (stemmed) words, phrases, thesaurus terms, or others. These terms can then be connected together with operators like AND, OR, NOT (with the implication of in file). Pure boolean also has no ordering, either it's just there or it isn't, but in practice we order chronologically and by number of hits per term. There are also fancier models based on this boolean model.


**Proximity Searches** 
This is based on terms occuring within K positions of another, such as pen within 5 words of paper. There is a lot of flexibility tin this approach: what "near" is can vary, sometimes the order is enforced, we also may want to handle phrases or combined terms like "Bill Clinton", "Information retrieval", "retrieval of information."

**Filters**
Free text query from user may spawn one or more queries to the indexes.

> **Example**
> As an example for query \[rising interest rates\] Run the query as a phrase query. Then If less than K docs contain the phrase \[rising interest rates\], run the two phrase queries \[rising interest\] and \[interest rates\]. If we still have less than K docs, run the vector space query \[rising interest rates\]. Lastly rank matching docs by vector space scoring.

This sequence is issued by a query parser which 

**Query Parsers**
Free text query from the user may behind the scenes spawn one or more queries to the indexes, for example rising interest rates. We can run the query as a phrase query, and if K docs contain that phrase then run two phrases "rising interest" and "rising rates" and this can be repeated again.

**Query Understanding**
In the modern days we do a lot of steps:
- Detect Query type
- Spelling correction + normalization
- Entity recognition/expansion
	- Apple as a company vs fruit
- Query rewriting/expansion
	- synonyms, abbreviation, context
- Generate multiple candidate interpretations and either choose or blend results.
## Ranking
- Classic modes still matter, boolean/Inverted index + phrase/proximity
- Default baseline in practice includes searches like BM-25
- Spelling correction + normalization
- Learning to rank: combine features using BM25, proximity, freshness, authority, etc.
- Neural reranking: Cross-encoder/late-interaction models on top of the K candidates
- Hybrid retrieval: Sparse + dense fusion for semantic matching + exact matching
## Evaluation and Relevance
### Relevance
When we talk about evaluation we have a number of terms we've discussed: Standard document set (TREC), Standard queries, Relevance assessed by experts, Precision,  Recall. But ultimately all of evaluation is based on the concept of relevance. Relevance is a context-dependent, task-dependent property of documents.

> Relevance is the correspondence in context between an information requirement statement ... and an article (a document), that is, the extent to which the article covers the material that is appropriate to the requirement statement.

\- F. W. Lancaster, 1979

**Stability**
For most textual documents, knowledgeable users have a high level of agreement in deciding whether or not a document has the relevant information. However, users tend to be much less consistent with non-textual documents like photographs.

**TREC Relevance findings**
- In the TREC-1 experiments each topic was judged by a single assessor, who also set the topic statement.
- In TREC-2 a sample of the topics and documents was re-judged by second expert. and the average agreement was about 80%.
- In TREC-4 all topics were re-judged by two additional experts, with only a 72% agreement rate among all three assessors.

However In the TREC-4 tests, most assessors agreed on which documents weren't relevant. About  30% of documents judged relevant by the first assessor were also judged non-relevant by both additional assessors. Using data from TREC-4 and TREC-6 Voorhees estimates that human experts have a practical agreement upper bound of 65% precision at 65% recall.
### Evaluation
Fundamental Questions in evaluation are: Is the user satisfied, is the user successful. Really that is all that matters, but practically accomplishing those goals is hard.

**Evaluation:**
- Standard document set (TREC)
- Standard queries
- Relevance assessed by experts

The ultimate goal is relevance, but part of the problem is that relevance isn't stable. In the old days a single domain expert judged the relevance between query and document. In TREC-2 they had a the documents re-judged by a second expert and the average agreement was about 80%. In TREC-4 all topics were re-judged by two assessor and there was an average about 72%.

In 2025:
- Offline: `nDCG@k`, `MRR`, `Recall@k`
- Online: A/B testing, interleaving,  click models. These models are optimized for user success and not just relevance.
- Key metrics include: latency, throughput, cost, tail latency
- For new answer systems based on AI we have to consider: grounding/faithfulness, citation correctness, hallucination rate 
# References
- [[Vector Space Model]]
- [[Boolean Information Retrieval Model]]