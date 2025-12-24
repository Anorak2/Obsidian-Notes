
2025-12-16

Tags: [[Data Mining]]
# Self Attention Networks (Transformer)
Pipelined approach:
Tokenization -> Input Layer -> Attention -> Feed Forward -> Output
Word -> token       orient           +context        Aggreggate

**1. Break Each word into a token**
![[Pasted image 20251216005053.png]]

**2. Understand each toke**
This is where each token is seen as it's vectors, for example dog cat and rabbit would have similar vectors.

**3. Attention**
This stage is where we understand the context of each token, or put another way we compute the relevance of each token and then aggregate relevant information. We can accomplish this by using an attention matrix, where we compute the value of all relevant pairs


# References
[[Artificial Neuron and Artificial Neural Networks]]

[[Recurrent Neural Networks]]
