
2026-03-09

Tags: [[Information Retrieval]] [[Textual Data*]] [[Data]]
# Normalizing Text
We need to “normalize” terms in indexed text as well as query terms into the same form since we want to match queries like U.S.A. and USA. This is also relevant in cases like associating " cleanliness" with "cleaning", and "Windows" and "windows". One alternative is to do an asymmetric expansion, so if our user enters "window" we search \["window", "windows", "Windows"\]. Asymmetric expansion is potentially more powerful but also less efficient.

## Unicode Normalization
Normalize to NFC or NFKC depending on your needs (canonical vs compatibility)
- NFC: Make the same character look the same (combine/decompose accents consistently), without changing meaning.
- NFKC: “Also flatten look-alikes” (full-width, ligatures, presentation forms → plain), which improves matching but can lose some distinctions.
Often we want to normalize quotes/dashes and whitespace (smart quotes, non-breaking spaces). It is also important to handle confusables carefully if you have security concerns since this is often a problem with phishing or name squatting attacks.

## Case Folding
Reduce all letters to lower case, but should we make an exception for upper case in mid-sentence? Some examples include General Motors, Fed vs. fed, SAIL vs. sail. 

Solutions, there are some forms of heuristics and machine learning methods that aim for improvements. Often it is just best to lower case everything, since users will use lowercase regardless of ‘correct’ capitalization… for example I tend to google usa instead of USA. This can be tricky though since aggressive normalization can destroy meaning, cat is likely the animal yet CAT is more likely caterpillar inc.

Modern Practice
- index both a case-folded field and a case-preserving field
- use query-time heuristics (all-caps / dotted patterns) to decide which to emphasize.

## Soundex
This is meant to handle synonyms and homonyms. Some easy examples is car = automobile, and color = `colour`.  Soundex rewrites these to form equivalence classes and then index these equivalence classes instead. For example every time we see automobile we index it under "car". We could also take a query expansion approach here though, meaning every time we search "car" we also search "automobile".

Soundex is a traditional class of heuristics to expand a query into phonetic equivalents.  This is language specific and mainly for names, this is also where I encountered it.  It was invented for the US Census and an example is `chebyshev` → `tchebycheff`.

## Lemmatization
Reduce inflectional/variant forms to base form.
- am, are, is → be
- car, cars, car's, cars' → car
- the boy's cars are different colors → the boy car be different color
Lemmatization implies doing “proper” reduction to dictionary headword form
## Stemming
The goal is to "normalize" similar words into a shared base by removing grammatical suffixes. This becomes tricky with the form of words, there is inflectional morphology that never changes the grammatical class (dog, dogs) and there is derivational morphology that looks for roots (building, build).

Ultimately stemming has at best moderate results in English, although it is absolutely useful for Spanish, German, Finish, and other languages.

### Porter's Algorithm
This is the most common algorithm for stemming and results show that it is at least as good as other options.  More information on the five stages is available at [this link](http://tartarus.org/~martin/PorterStemmer/def.txt).

## When to use Stemming / Lemmatization
Sparse IR
- Light stemming can improve recall in some collections, but may hurt precision
- Lemmatization is more linguistically correct but costlier/less predictable
- Often: no stemming + good ranking features is a strong baseline
Dense / neural IR
- Do NOT stem; use the model’s subword tokenizer (`BPE`/`WordPiece`/`SentencePiece`)
- Subwords help `OOV` words, typos, and morphology without manual rules
- Always treat stemming/lemmatization as a measurable ablation, i.e. damaging specific components in the system to improve overall results

# References
- [[Tokenization]]
- [[Data Pre-processing]]