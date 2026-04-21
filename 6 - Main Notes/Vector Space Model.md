
2026-02-09

Tags: [[Information Retrieval]]
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

# References
- [[Boolean Information Retrieval Model]]
- [[Document Frequency Measures (TF, IDF)]]
- [[Distance Measures]]

