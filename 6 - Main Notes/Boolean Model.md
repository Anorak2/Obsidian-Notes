
2026-02-02

Tags: [[EECS 767]]
# Boolean Retrieval
This is the most basic model possible, we don't care about any fancy notions we simply return items with keyword matching.

### Overview:
- A document is represented as a set of keywords.
- Queries are Boolean expressions of keywords, connected by AND, OR, and NOT, including the use of brackets to indicate scope.
- `[[[Rio & Brazil] | [Hilo & Hawaii]] & hotel & !Hilton]`
- Output: Document is relevant or not. No partial matches or ranking.

external merge sort
### Term-Document Incidence Matrix
This matrix has a series of binary values showing whether or not a term appears in a given file, we can then represent these as binary strings. The text Caesar might appear in documents in the way 110110101 while Caligula might be in 0010000, with not Caligula as 11011111. This naive approach can become difficult very quickly, with the index actually being significantly larger than the base documents themselves.

### Inverted Index
However if the matrix is **sparse** then we can instead only store the 1's, we do this by dedicating a list to each dictionary value with indices storing the document id's. We can do better, instead of just having a dictionary and the postings we can store the terms, document frequency, and total frequency in our dictionary. Then we can also store the postings with the document number and the term frequency for each document.

**Positional Index**
To complete the inverted index, in the modern day we also store the indexes of where each term appears in each document.
![[Pasted image 20260202201203.png]]

### Query Processing


# References

