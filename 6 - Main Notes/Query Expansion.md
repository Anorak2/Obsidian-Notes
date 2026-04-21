
2026-03-02

Tags: [[Information Retrieval]]
# IR Query Expansion
In query expansion users often don't do anything intentionally, but implicitly give information about what they are looking for. We typically do this by automatically expanding the query to include synonyms of words in the original query. The three main approaches are manual thesaurus, global analysis, and dynamic local analysis.

## Manual Thesaurus
Wordnet is a set of Nouns, adjectives, verbs, and adverbs grouped into about 109,000 synonym sets called synsets. It is a more detailed database of semantic relationships between English words developed by George Miller and a team at Princeton University.

Example relationships:
- Antonym: front → back
- Attribute: benevolence → good (noun to adjective)
- Pertainym: alphabetical → alphabet (adjective to noun)
- Similar: unquestioning → absolute
- Cause: kill → die
- Entailment: breathe → inhale
- Holonym: chapter → text (part-of)
- Meronym: computer → cpu (whole-of)
- Hyponym: tree → plant (specialization)
- Hypernym: fruit → apple (generalization)
## Statistical Thesaurus
Human generated thesauri are limited by the associations that they can make, in a statistical thesaurus we attempt to generate it automatically by analyzing the collection of documents.

In Wordnet the fundamental idea was a synset, in a statistical thesuarus it's the similarity between two words. The idea being co-occurrence is more robust, and the grammatical relations are more accurate.

Definition 1: Two words are similar if they co-occur with similar words.
Definition 2: Two words are similar if they occur in a given grammatical relation with the same words.

**Issues:**
The quality of word associations is often a problem, and term ambiguity can introduce irrelevant terms. For example, “Apple computer” → “Apple red fruit computer." Furthermore since terms are highly correlated anyway, expanding this way may not retrieve many additional documents.
# References
- [[Relevance Feedback]]

