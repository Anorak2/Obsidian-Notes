
[[Information Retrieval Basics]]

 **Pre-processing text**
- [[Tokenization]]
- [[Statistical Properties of Text (Zipf)]]
- [[Normalizing Text]]
- [[Stop Word Removal]]

**text algorithms and features**
- [[Document Frequency Measures (TF, IDF)]]
- [[BM-25]]

**IR Systems**
- [[Evaluating Information Retrieval]]
- [[Boolean Information Retrieval Model]]
	- add query processing
- [[Vector Space Model]]
	- [[Efficient Cosine Ranking (*pruning)]]
- [[Full IR in Traditional Lookup Systems]]
- [[Full IR in Modern Web Systems]]

 **Other**
 - [[Relevance Feedback]]
 - [[Query Expansion]]
- [[Search Personalization]]

**Web:**
- [[Web Crawlers]]
- [[Intro to Web Link Analysis]]
- [[Page Rank]]
- [[Hyperlink-Induced Topic Search (HITS)]]

**ML:**
- [[Classification Methods for Information Retrieval]]
- [[Clustering for Information Retrieval]]

#### Social Networks
- [[Basic Social Networks]]
- [[Measuring and Analyzing Social Networks]]
- [[Social Network Search and Recommendations]]




## Topics
we might need some of old stuff like cos similarity but focus is on new stuff
web basics
- indexer
web crawling
- basic crawler architecture and roughly how it works
- polite web crawlers mercator scheme
- web communication between nodes
web search
- relevance vs importance
page rank
- random walk basis stochastic, steady state
HITS
- hubs and authority analysis + calculation
Document Classification
- Rocchio, kNN
- with rocchio we train an average document vector for each label and on a new document we train a doc specific vector so it's a more global view while KNN is a more local view
clustering
- flat algorithms
- hierarchical algorithms, understand the different types of how to build
social networks
- Calculate density, clustering coefficient, distance types geodesic etc

what we could have covered with ML for IR
- TF/IDF model is very high dimensional space. King and Queen are unrelated, but Car/Automobile are related
- in real world we want a lower dimensional but relatively dense space, this means only hundreds or thousands of dimensions. We would like to associate King and Queen with also man vs woman with some link between monarchy etc.
### J
topics in order:
- IR systems
- text algorithms
- inverted index
- boolean model
- vector space model
- evaluation
- relevance feedback, query expansion, personalized search

---
### ⚠ Unfiled — tagged this index but not placed above
```dataview
LIST
FROM [[]]
WHERE !contains(this.file.outlinks, file.link) AND contains(file.folder, "Main Notes")
SORT file.name ASC
```
