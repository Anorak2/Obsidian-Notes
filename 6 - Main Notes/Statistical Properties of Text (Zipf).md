
2026-02-16

Tags: [[Information Retrieval]] [[Data]]
# Statistical Properties of Text (Zipf)
When we are analyzing text we'll notice something rather immediately, tokens are not uniformly distributed an they also aren't normally distributed. Rather, they exhibit a Zipf distribution.
## Zipf
![[Pasted image 20260309135823.png]]
Example frequency curve

Simply put Zipf can be summarized as a few elements occur very frequently, a medium number of elements have medium frequency, and many elements occur very infrequently. A consequence of this is that the product of the word frequency and their rank is approximately constant.
$$Freq = \frac{C}{rank}$$
$$C \approx \frac{N}{10}$$
Another way to state this is with an approximately correct rule of thumb: Say the most common term occurs C times, the second most common occurs C/2 times, the third most common occurs C/3 times, ...

**What kinds of data have Zipf curve:**
- Words in a text collection, regardless of virtually any language
- Library book checkout patterns
- Incoming Web Page Requests (Nielsen)
- Outgoing Web Page Requests (Cunha & Crovella)
- Document Size on Web (Cunha & Crovella)


![[Pasted image 20260309140349.png]]
Information Retrieval, by C. J. van Rijsbergen, 1979. This image demonstrates the "resolving power" of words,  if we have a super common word then it doesn't narrow down our search. However very rare words, while powerful, are also much less likely to appear in queries and not as powerful as the "middle" of the pack words.

**Consequences:**
- There are always a few tokens that are not good discriminators, Usually called “stop words” in IR. These tokens usually correspond to linguistic notion of “closed-class” words with English examples: to, from, on, and, the, and so on. 
- There are always a large number of tokens that occur once and can mess up algorithms.
- Medium frequency words most descriptive


# References
- [[Tokenization]]

