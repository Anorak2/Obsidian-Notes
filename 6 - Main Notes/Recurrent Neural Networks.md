
2025-12-10

Tags: [[Data Mining Lecture]] [[Data]]
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

# References
[[Artificial Neuron and Artificial Neural Networks]]

[[Loss Functions]]

[[Convolutional Neural Networks]]