
2026-03-02

Tags: [[Information Retrieval]] [[Algorithms]]
# Relevance Feedback
Information retrieval is hard, and sometimes our results aren't what the user intended. What if we just ask the user to give feedback about the results post query?
## Motivation
Users prefer short and simple queries since they are fast, but this makes it hard since they don't provide much information. Since 'java' could mean coffee or the programming language, what if we just ask the user to clarify and then expand their query with search terms. Then we can reweigh the documents to improve the results.

## Relevance Feedback
Idea: it may be difficult to formulate a good query when you don’t know the collection well, so iterate as you gain understanding. Relevance feedback is most useful for
increasing recall in situations where recall is important and where users can be expected to review results and to take time to iterate.

**Context Based Image Retrieval**
This is one of the most common use cases for relevance feedback, and the idea is when a user clicks on an image we can search for similar images based on visual features. In google images this happens whenever you expand an image, in the section down below.

event loop:
- User issues a (short, simple) query
- IR system returns first set of results
- The user marks some results as relevant or non-relevant.
- The system computes a better representation of the information need based on feedback.
- IR system evaluates the new query, returns new results.
- Hopefully, new results gives better precision/recall.
- Relevance feedback can go through one or more iterations.

Speaking generally from here, positive feedback tends to be more useful that negative feedback so many systems will actually ignore negative feedback ($\gamma$ in Rocchio).

**Assumptions**
- `A1`: User has sufficient knowledge for initial query.
- `A2`: Relevance prototypes are “well- behaved”.

`A2` means that dissimilar documents will be dissimilar in a similar way, got that? This actually means irrelevant documents will tend to have the same keywords and the term distribution is different from the relevant documents, which isn't always true.

Unfortunately  `A1` also has issues, sometimes they will make spelling mistakes or have other issues like a vocabulary mismatch such as Laptop vs Notebook Computer or Car vs Automobile.

**Issues:**
- Long Queries are slow and inefficient for usual IR problems
- Users often don't want to provide explicit feedback
- It’s often harder to understand why a particular document was retrieved after applying relevance feedback

**How to recompute the query?**
We can change query vector using vector algebra. Do this by adding the vectors for the relevant documents and subtracting the vectors for the irrelevant docs from the query vector. This both adds both positive and negatively weighted terms to the query as well as reweighing the initial terms. In mathematical terms using our polar coordinates scheme we are moving our query vector away from the irrelevant centroids, and towards the relevant centroids where a centroid is defined as 
$$\vec \mu(C) = \frac{1}{|C|}\sum_{\vec d \in C}\vec d$$
where C is a collection of documents.

**Rocchio Algorithm**
The Rocchio algorithm uses the vector space model to pick a relevance fed-back query. Question is if we know all the relevant and non-relevant documents, what is the best query?

First some terms; $\vec \mu(C_r)$ is the centroid of all relevant documents and  $\vec \mu (C_{nr})$ is the centroid of all non-relevant documents.  The optimized query maximizes the first, and minimizes the second, thus we maximize $sim(\vec q, \vec \mu (C_r))-sim(\vec q, \vec \mu (C_{nr})$. To put it all together, Rocchio seeks a query $\vec q _{opt}$ that equals $argmax_{\vec q}[sim(\vec q, \vec \mu (C_r))-sim(\vec q, \vec \mu (C_{nr})]$. The problem is that we don't know all of the truly relevant documents.

In practice we use the following:
$$\vec q_m = \alpha \vec q_0+\beta\frac{1}{D_r}\sum_{\vec d_i \in D_r}\vec d_i-\gamma\frac{1}{|D_{nr}|}\sum_{\vec d _j \in d_{nr}}\vec d _j$$
	where the first $1/d_r$ and sum is the average of known relevant documents, and the second is the average of known non-relevant documents. $q_m$ is the modified query vector, $q_0$ is the original query vector, and $\alpha, \beta, \gamma$ are weights that can be chosen by hand or empirically. Some subtleties is that if we have a lot of documents ranked then we want a higher $\beta$/$\gamma$ since the user is telling us our original query is bad. Some weights can also go negative, which we will ignore and set to 0 in that case. 

## Implicit Feedback
Modern systems rarely ask users to mark results as relevant, rather they infer feedback from clicks, dwell time, reformulations, and abandonment. Ex: The user clicks on the second link, and ends the session, or maybe the user browses through the first three pages, and then revises the query.

This approach is tricky for a number of reasons, for example the first link tends to get a higher click through rate simply because it is first. Alternatively a clickbait title can attract clicks despite having no relevance.

## Pseudo Relevance Feedback
Pseudo-relevance feedback automates the user input part of true relevance feedback.
The idea is to retrieve a ranked list of hits for the user’s query, assume that the top k documents are relevant, and then do relevance feedback (e.g., Rocchio). This works very well on average but can go horribly wrong for some queries since it reinforces a wrong idea.
The more modern approach is to assume the top-k results are relevant, then expand or reweigh the query automatically. This is still useful, but the main risk is query drift when the top results are off-topic. Common safeguards include a  small k, limited expansion terms, and conservative weighting. Modern variants include relevance-model style expansion and hybrid/neural expansion. They also always evaluate PRF empirically. This approach can help some query types and hurt others.

# References
- [[Vector Space Model]]

