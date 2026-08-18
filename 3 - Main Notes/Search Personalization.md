
2026-03-27

Tags: [[Information Retrieval]]
# Search Personalization
Generally there are two ways to personalize search, query expansion and re-ranking. Query expansion is covered thoroughly in a different note, meanwhile re-ranking is the idea of ranking differently for different profiles. More specifically in re-ranking you issue the same query and fetch the same results, but re-rank the results based on a user profile. This approach allows for global results while still tailoring to individuals.

**User Interests**
This can be explicitly provided by the user, and this can be useful for new users but generally doesn't work well. I'm not sure why this approach fails, I would imagine because users often don't know what they want or say they want something they actually don't. An alternative is to infer from user behavior and content like previously issued search queries, previous web pages, personal documents, or emails (?!?). My professor says that privacy/user control is important, and I would certainly hope so if I am feeding my personal documents to Google.

**User Location**
This is one of the simplest ways to personalize results, yet simultaneously one of the most powerful features. This is immediately obvious for queries like "zoo," "football," or "restaurants." It's not without challenges, many queries aren't location sensitive for example and it can be hard to tell the difference. "Disney World" may not be about the closest disney world, different parts of a website might be more location sensitive than others, and page content doesn't always tell us if the page is location sensitive. Studies such as [Bennett et al. 2011] show that user statistics are the best predictor of whether a site is location sensitive or not, which can be acquired through anonymous logs.
![[Pasted image 20260327211929.png]]

![[Pasted image 20260327211938.png]]

# References
- [[Relevance Feedback]]
- [[Query Expansion]]