
2026-02-09

Tags: [[EECS 767]] [[Data]] [[Textual Data*]]
# Document Frequency Measures (TF, IDF)
**Document Frequency:** or $tf_{t,d}$ of term $t$ in document $d$ is defined as the number of times that $t$ occurs in $d$.

However sometimes words have very high frequency, such as "a" or "and", meaning that rare terms will give us more information. This leads to a trade off where the higher the term frequency the more frequent terms, but less useful, and with a dower $df$ there are rare more informative terms.

**Inverse Document Frequency:**
$$idf_t = \log_{10} \frac{N}{df_t}$$
We use $\log N/df_t$ instead of $N/df_t$ to “dampen” the effect of $idf$.

$$idf_t=\ln \frac{N-df+t+0.5}{df_t+0.5}$$
This version of IDF adds the 0.5 to avoid division by zero or extreme weights, it also makes the IDF more stable for rare terms. This version of IDF could actually be negative though, where highly frequent terms could contribute "negatively" to the search which requires solutions. This could be to remove stop words, normalize all negative IDF to zero, or modify the formula to log(1 + {same core}) which is the most popular.

Example using log 10:

| term      | DF        | IDF |
| --------- | --------- | --- |
| calpurnia | 1         | 6   |
| animal    | 100       | 4   |
| sunday    | 1,000     | 3   |
| fly       | 10,000    | 2   |
| under     | 100,000   | 1   |
| the       | 1,000,000 | 0   |

## TF-IDF 
This is the most well known weighting scheme in information retrieval, and it increases with the number of terms in the document and with the rarity of terms in the collection
$$w_{t,d}=tf_{d,f}*idf_t= tf_{t,d}*\log_{10}\frac{N}{df_t}$$

# References
- 

