
2025-12-10

Tags: [[Data Mining and Machine Learning]] [[Data]]
# Neural Networks
![[Pasted image 20260206223031.png]]
*Fig. General Topology* 

**Strengths:**
- Non-probabilistic, i.e., no assumption of Gaussian distribution or independence of input features
- Capability to learn non-linear models.
**Weaknesses:**
- Training a neural network is known to be NP-complete meaning there is no known way to find a solution quickly, thus heuristics are used that find non- optimal solutions
- Different random weight initializations can lead to different test results, i.e., two runs with the same training data may produce different test results (e.g., accuracy).
- Requires tuning a number of hyper-parameters such as the number of hidden neurons, layers, and iterations
- Sensitive to feature scaling
- Susceptible to over-fitting.
## Artificial Neurons
---
An artificial neuron is a mathematical model based on the og biologic, which sounds complicated but ultimately a neuron is a single function. It takes in N inputs, performs a function, and then carries outputs away from it.

$$\hat y = g(b + \sum^m_{i=1}x_i\cdot w_i)$$
or,
$$Output = (Non\text{-}linear \space activation \space Function)(constant+\sum^m_{i=1}inputs_i \cdot weights_i)$$
## Activation Functions
---
An Activation Function is a function that adds a degree of non-linearity to the function, this is important since otherwise no matter how large our network is our output will be linear. Adding a non-linear component allows us to model arbitrarily complex functions rather than basic ones.
![[Pasted image 20251210192053.png]]

## Types of Neuron Connections
---
**Multi-Class**
In a multiclass network there are a number of nodes serving as outputs, and the node with the highest score determines the class

**Multi-Layer Perceptron**
A neural network - each neuron is fully connected with all the input nodes in the previous layer, and all the output nodes in the next layer

**Forward Propagation**
![[Pasted image 20251210193220.png]]
- The input data is fed in the forward direction through the network
- Each hidden layer accepts the input data, processes it as per the activation function
- Passes to the successive layer till outputs generated


## Training Process - Back Propagation
Neural networks are trained by iteratively updating their weights (w) and biases (b) to minimize the difference between the predicted output and the actual target values of the training data. A gradient descent method called back propagation is usually used to estimate the weights of the network.

![[Pasted image 20260206223501.png]]
![[Pasted image 20260206223523.png]]
The "magic" happens in the backpropagation and update stages. The chain rule is used to determine how much to tweak the weights,  the gradient ∇ is the "transpose of the derivative of the output in terms of the input". More can be learned at [this link](https://en.wikipedia.org/wiki/Backpropagation)
## Practically Training Neural Networks
The scikit library has two functions:
- `neural_network.BernoulliRBM`
	- The Bernoulli Restricted Boltzmann Machine (RBM) is a binary neural network classifier.
- `neural_network.MLPClassifier`
	- The Multi-layer Perceptron (MLP) is a multi-class neural network classifier.
	- This method has an input parameter, hidden_layer_sizes, that allows the programmer to specify the number of hidden layers and the number of nodes in each layer

It also has a method for regression
- `neural_network.MLPRegressor` - Multi-layer Perceptron regressor.

## Deep Belief Networks
 In simple words, a deep belief network is just a multi-layer Neural Network. Calling it a Deep-Belief Network makes it sound like something new related to “deep learning” when it really isn't.

Johnson called this a good example of a DBN
https://github.com/albertbup/deep-belief-network

There is a library [here]( https://github.com/albertbup/deep-belief-network) that will be needed for assignment 3. Copy and paste the dbn folder located in the main deep-belief- network-master folder into the same directory as your Python code.
# References
- 

