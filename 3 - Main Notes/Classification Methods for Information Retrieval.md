
2026-04-06

Tags: [[Information Retrieval]] [[Data Mining and Machine Learning]]
# Classification Methods for IR
**Classification Definition**
Given a description of an instance, $x \in X$, where X is the instance language or instance space, and a fixed set of classes $C =\{c_1, c2_,…, c_J\}$. Then determine the category of $x: c(x) \in C$ , where c(x) is a classification function whose domain is X and whose range is C. The issue with the first part is that it's hard to represent text documents.

**Manual Classification**
When using experts or even a team of experts this method is highly accurate, but expensive to maintain and thus less common. It's very consistent with a small problem size / team size but it becomes very hard to scale.

**Rule Based**
Hand-coded rule-based systems is just one technique used by many spam filters, Reuters, CIA, etc. It is very simple but powerful, similar to yara. To make it easier Companies provide “IDE” for writing such rules, such as to assign category if document contains a given boolean combination of words. In this approach accuracy is often very high if a rule has been carefully refined over time by a subject expert, but building and maintaining these rules is expensive

Standing queries: Commercial systems have complex query languages (everything in IR query languages + accumulators)

**ML**
Supervised learning of a document-label assignment function. Many systems partly rely on machine learning such as Autonomy, MSN, Verity, Enkata, Yahoo!, and so on. Options include k-Nearest Neighbors (simple, powerful), Naive Bayes (simple, common method), Support-vector machines (new, more powerful), or other methods we've talked about

No free lunch: requires hand-classified training data, but data can be built up (and refined) by amateurs

**Rocchio Classification**
Relevance feedback methods can be adapted for text categorization since relevance feedback can be viewed as 2- class classification of relevant vs. non-relevant documents. Use standard TF/IDF weighted vectors to represent text documents.  For training documents in each category, compute a prototype vector by summing the vectors of the training documents in the category where the  prototype = centroid of members of class. After creation, test documents can be assigned to the category with the closest prototype vector based on cosine similarity.

Rocchio forms a simple representation for each class: the centroid/prototype. Where classification is based on similarity to / distance from the prototype/centroid. It does not guarantee that classifications are consistent with the given training data, and it is little used outside text classification, but has been used quite effectively for text classification. It's worth mentioning again how cheap this method is.

**K Nearest Neighbors**
Typically for this use case 5 is used to avoid ties, and it is nice because it has no learning process and scales well with high # of classes. One downside is that changes to a class can ripple, and rather than pay during training time we pay during lookup time.

# References
- [[K nearest Neighbors (kNN)]]
- [[Vector Space Model]]