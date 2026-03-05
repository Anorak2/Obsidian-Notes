
2026-02-09

Tags: [[EECS 767]]
# Vector Space Model
The vector space model has a t-dimensional vector space with the size of the vocabulary, and terms are the axes (dimensions) of the space. If we have a dictionary of 3,000 entries then our vector space will have 3,000 dimensions. In this space documents are points or vectors $d_1$ = (weight of $t_1$, weight of $t_2$, weight of $t_3$)

- Key idea 1: Do the same for queries: represent them as vectors in the space
- Key idea 2: Rank documents according to their proximity to the query in this space
- proximity = similarity of vectors and proximity ≈ inverse of distance

**Model:**
Represent the query as a weighted TF-IDF vector, represent each document as a weighted TF-IDF vector. Compute the cosine similarity score for the query vector and each document vector rank documents with respect to the query by score. Return the top K (e.g., K = 10) to the user.

**Bag of Words Model**
A bag of words model is a lot like a set but it allows for duplicates.
### Distance Measures
**Euclidean Distance**
Our first intuition should be to use euclidean distance, but this is a bad idea because it punishes vectors with different lengths. for example "good" and "good good" will be marked as far away despite the query being identical to the document.

**Cosine Similarity:**
In a vector space model we can instead use the cosine similarity which will rank documents in the order of the angle between queries and documents.
$$cos( \vec q, \vec d) = \frac{\vec q}{|\vec q|}\cdot \frac{\vec d}{|\vec d|} = \hat q \cdot \hat d$$

### BM-25
This is a very well known way to score called best match 25

Philosophy:
- reward multiple occurrences of the term in a document but only up to a point
- reward the rare terms 
- normalize to the length of the document to avoid over rewarding very long documents that mention many terms

BM-25 is a probabilistic ranking function where we have a score where higher means "likely more relevant". To reward rare terms we use IDF with some tricks  

**IDF** - reward rare terms
$$idf_t=\ln \frac{N-df+t+0.5}{df_t+0.5}$$
This version of IDF adds the 0.5 to avoid division by zero or extreme weights, it also makes the IDF more stable for rare terms. This version of IDF could actually be negative though, where highly frequent terms could contribute "negatively" to the search which requires solutions. This could be to remove stop words, normalize all negative idf to zero, or modify the formula to log(1 + {same core}) which is the most popular.


**BM-25's saturation:** - reward multiple occurrences 
$$\frac{tf_{t,d}(k_1+1)}{tf_{t,d}+k_1}$$
where $k_1$ controls how quickly TF saturates. This version rewards multiple occurrences of a term in the document but non-linearly. This is seen how when TF is small it increases quickly but as TF grows it approaches K+1

**Normalize Document Length**
$$k_d = k_1(1-b+b\cdot \frac{|d|}{\text{average document length}})$$
where $b \in [0, 1]$ controls the strength of length normalization

**together:**
$$BM25 = \sum_{t\in q} idf(t)\cdot\frac{tf_{t,d}(k_1+1)}{tf_{t,d}+k_1(1-b+b\cdot\frac{|d|}{\text{average dl}})}$$


# References
- [[Boolean Information Retrieval Model]]
- [[Document Frequency Measures]]
- [[Distance Measures]]

