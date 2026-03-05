
2025-12-10

Tags: [[Data Mining and Machine Learning]] [[Data]]
# Recurrent Neural Networks
![[Pasted image 20251210200847.png]]
While CNNs are designed to process image data, RNNs are designed to handle sequential information. RNNs introduce state variables to store past information, together with the current inputs, to determine the current outputs. Due to the way RNNs loop they can actually be thought of as multiple "copies" of the same network, with each copy passing a message to a successor. There are downsides, notably in RNNs they struggle to remember state over the long term.
**Applications:**
- Image Captioning
- Autocomplete Predictions
- Machine Translation (Google Translate)

## Neural Architecture
---
![[Pasted image 20251210200934.png]]
![[Pasted image 20251210201240.png]]
## Bi-directional RNN
Filling in the blank in a text sequence:
- I am ___
- I am ___ hungry.
- I am ___ hungry, and I can eat half a pig.
In this example the end of the phrase (if available) conveys significant information about which word to pick

**Bidirectional RNNs**
- Instead of running an RNN only in the forward mode starting from the first token, we start another one from the last token running from back to front.

## Long Short Term Memory (LSTM)
---
![[Pasted image 20251210205817.png]]
Key to LSTMs is the **memory cell** that has the same shape as the hidden state that are designed to record additional information.

To control the memory cell we need a number of gates; gates are a way to optionally let information through
- forget gate: reset the content of the cell
- input gate: decide when to read data into the cell. We refer to this as the
- output gate: read out the entries from the cell

What information to forget
- The first step in LSTM is to decide what information we’re going to throw away from the cell state.
- The decision is made by a sigmoid layer called the forget gate
	- Input: previous state ℎ𝑡−1 and current input 𝑥𝑡
	- Output: a number between 0 and 1 applied on previous cell state 𝐶𝑡−1
	$$f_t=\sigma(W_f \cdot [h_{t-1,x_t}]+b_f)$$
	- where 1 represents completely keep and 0 represents completely forget
	
**Step By Step**
- Update the cell state
- Update old cell state $C_{t−1}$ to new cell state $C_t$
- Part 1: Multiply the old state by 𝑓𝑡,
	- forgetting the things we decided to forget earlier.
- Part 2: Add $i_t * tanh(C_t)$ 
	- $𝐶^{\sim}_t$  is the new candidate values
	- $i_t$  decides how much we decided to update each state value.
$$C_t=f_t*C_{t-1}+i_t*C^{\sim}_t$$

## LLM usage
Problem Formulation:
- Train an RNN to write text, in this case patent abstracts.
- Input a sequence of words and train the model to predict the very next word.
- The words will be mapped to integers and then to vectors using an embedding matrix before being passed into an LSTM layer.
- To write a new patent abstract:
	1. pass in a starting sequence of words
	2. make a prediction for the next word
	3. update the input sequence
	4. make another prediction
	5. add the word to the sequence
	6. continue for however many words we want to generate

What Johnson just described above is exactly what generative AI does but with a transformer rather than a LSTM layer, and gargantuan datasets.

Example Layers:
![[Pasted image 20260222011639.png]]

## Practical
Features and Classes
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
```Python
from keras.models import Sequential
from keras.layers import LSTM, Dense, Dropout, Masking, Embedding
model = Sequential()
# Embedding layer
model.add(
	Embedding(input_dim=num_words,
		input_length = training_length,
		output_dim=100,
		weights=[embedding_matrix],
		trainable=False,
		mask_zero=True))
		
# Masking layer for pre-trained embeddings
model.add(Masking(mask_value=0.0))

# Recurrent layer (LSTM module)
model.add(LSTM(64, return_sequences=False,
	dropout=0.1, recurrent_dropout=0.1))
	
# Fully connected layer
model.add(Dense(64, activation='relu'))

# Dropout for regularization
model.add(Dropout(0.5))

# Output layer
model.add(Dense(num_words, activation='softmax'))

# Compile the model
model.compile(
optimizer='adam', loss='categorical_crossentropy', metrics=['accuracy'])
```

Other approaches can be seen in [this repository](https://github.com/WillKoehrsen/recurrent-neural-networks/blob/master/notebooks/Deep%20Dive%20into%20Recurrent%20Neural%20Networks.ipynb), some options are:
 - Two LSTM layers stacked on each other
 - Or, one Bidirectional LSTM layer that processes sequences from both directions
 - Or, more Dense layers
# References
- [[Neural Networks]]
- [[Loss Functions]]
- [[Convolutional Neural Networks]]
- [[Large Language Models (LLM's)]]
- [[Tokenization]]