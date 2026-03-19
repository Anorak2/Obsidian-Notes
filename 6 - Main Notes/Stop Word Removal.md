
2026-03-09

Tags: [[EECS 767]] [[Data]] [[Textual Data*]]
# Stop Word Removal
With a stop list, you exclude from dictionary entirely the commonest words. Intuition is that they have little semantic content: the, a, and, to, be.  There are a lot of them: ~30% of postings (or more) for top 30 words.

 Our stop word list contains the following:
 - I , a, about, an, are, as, at, be, by, com, `de`, en, for, from, how, in, is, it, la, of, on, or, that, the, this, to, was, what, when, where, who, will, with, `und`, the , `www`

But the trend is away from doing this:
- Good compression techniques means the space for including stop words in a system is very small, and good query optimization techniques mean you pay little at query time for including stop words.
- You need also them for:
	- Phrase queries: “King of Denmark”
	- Various song titles, etc.: “Let it be”, “To be or not to be”
	- “Relational” queries: “flights to London”
# References
-  [[Tokenization]]
- [[Statistical Properties of Text (Zipf)]]