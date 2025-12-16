
2025-12-10

Tags: [[Data Mining]] [[Data]]
# Artificial Neuron and Artificial Neural Networks
## Artificial Neurons
---
An artificial neuron is a mathematical model based on the og biologic, which sounds complicated but ultimately a neuron is a single function. It takes in N inputs, performs a function, and then carries outputs away from it.

$$\hat y = g(b + \sum^m_{i=1}x_i\cdot w_i$$
or,
$$Output = (Non\text{-}linear \space activation \space Function)(constant+\sum^m_{i=1}inputs_i \cdot weights_i)$$
## Activation Functions
---
An Activation Function is a function that adds a degree of non-linearity to the function, this is important since otherwise no matter how large our network is our output will be linear. Adding a non-linear component allows us to model arbitrarily complex functions rather than basic ones.
![[Pasted image 20251210192053.png]]

## Types of Neuron Connections
---
**Multi-Layer Perceptron**
A neural network - each neuron is fully connected with all the input nodes in the previous layer, and all the output nodes in the next layer

**Forward Propagation**
![[Pasted image 20251210193220.png]]
- The input data is fed in the forward direction through the network
- Each hidden layer accepts the input data, processes it as per the activation function
- Passes to the successive layer till outputs generated


# References

