
2026-02-02

Tags: [[EECS 767]]
# Evaluating Information Retrieval
We evaluate information retrieval systems because otherwise everything becomes arbitrary, we can't check for quality and we aren't able to make informed decisions. Ideally we want to be constantly validating the quality of our systems, if it's automated then even better.

**Evaluating Traditional IR systems:** In traditional systems we have a large repository of documents that users want to search through using queries. Part of the problem though is what do we evaluate? Coverage, speed, user effort, recall, precision, there are many features that could be meaningful to users and each one could be a business advantage.

**Precision and Recall:** These are the classic gold standard options to prioritize, it is simple to calculate and the results aren't ambiguous.

## Classic Binary P/R
$$Precision = P(relevant|retrieved) = \frac{TP}{TP+FP}$$
$$ Recall = P(retrieved|relevant)=\frac{TP}{TP+FN}$$
$$\text{fallout} = f = \frac{FP}{FP+TN}$$
There is a general F-Score which is a combined measure, using the weighted harmonic mean to measure both precision and recall together. This is often used with an $\alpha = 0.5$, called the F1 score.
$$F_1 = \frac{2pr}{p+r}$$

**Limitations:**
- these are binary notions
- we don't always care about recall, like in web search

**Precision@K:** This is just the idea of calculating the precision for the first K values, this is important because we often care not just about total recall but the rank as well

## Mean Average Precision
MAP is the average precision among multiple queries, with each query ranked with the same value. This is now one of the most used metrics for many research papers.

## MRR - Mean Reciprocal Rank
When there's only one relevant document or we only care about the first relevant document, like for a fact like the population of Kansas. In this case we consider the rank position, K, of the first relevant doc. This would be especially relevant in cases like google or other search engines, where often users get frustrated quickly.
$$\text{Reciprocal Rank Score} = \frac{1}{k}$$
## Discounted Cumulative Gain
This metric relies on two assumptions: Non-binary relevance where some documents are more useful than others, and discounted relevance where the lower ranked a relevant document the less useful it is to a user.

Relevance, or the gain of a document, is on a scale of $[0, r]$ where $r > 2$

**Cumulative Gain:** is the sum of gain in the first n documents

**Discount Gain:** The cumulative gain multiplied by the discount factor

**Discounted Cumulative Gain (DCG):** A logarithmic discount is used to assign lower gain when relevant documents are ranked lower in the list.
$$\text{in this classs always discount by } \frac{1}{\log _2 (i+1)}$$
$$\text{DCG@K}=\sum^K_{i=1}\frac{r_i}{log_2(i+1)}$$

**Ideal DCG (IDCG):** The DCG for the ideal scenario for the best possible search engine

**Normalized DCG:** divide the DCG@K by IDCG@K to get the normalized value $\in [0,1]$

# References
[[Information Retrieval Basics]]
