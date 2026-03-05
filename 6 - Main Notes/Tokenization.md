
2026-02-22

Tags: [[Data Mining and Machine Learning]] [[EECS 767]]
# Tokenization


## Keras
As with most text related applications the data is tokenized by:
1. Removing punctuation and split strings into lists of individual words.
2. Converting the individual words into integers.
These two steps can both be done using the Keras Tokenizer class. By default, this removes all punctuation, changes upper-case to lower-case, and then converts words to sequences of integers. A Tokenizer is first fit on a list of strings and then converts this list into a list of lists of integers. Each abstract is now represented as a list of integers.

Example Keras code
```Python
# Create Tokenizer Object
tokenizer = Tokenizer(num_words=None,
                      filters='!"#$%&()*+,-./:;<=>?@[\\]^_`{|}~\t\n',
                      lower = True, split = ' ')

# Train the tokenizer to the texts
tokenizer.fit_on_texts(abstracts)

# Convert list of strings into list of lists of integers
sequences = tokenizer.texts_to_sequences(abstracts)

sequences[100][:15]
```
In this version the model won't learn proper english since we removed all punctuation, but this can be customized.

The following code will give 50 words and ask the model to predict the 51st word. This will work, although it may not be optimal, there is no fully correct way to go about this. some other ways include having it predict the next word at each point in the sequence, making a prediction for each input word rather than once for the entire sequence, or training the model using individual characters.

```Python
features = []
labels = []
training_length = 50
# Iterate through the sequences of tokens
for seq in sequences:
	# Create multiple training examples from each sequence
	for i in range(training_length, len(seq)):
		# Extract the features and label
		extract = seq[i - training_length:i + 1]
		
		# Set the features and label
		features.append(extract[:-1])
		labels.append(extract[-1])
features = np.array(features)
```
# References
- 

