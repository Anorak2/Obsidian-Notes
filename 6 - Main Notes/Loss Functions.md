
2025-12-10

Tags: [[EECS 568 - Intro to Data Mining]]
# Loss Functions
The loss function measures the cost incurred at the output (prediction), or put another way just how close our predictions are to reality.

We can measure loss with the following generalized function
$$J(W)=\frac{1}{n}\sum^n_{i=1}L(g(x^i;W), y^i)$$
where the first argument is the prediction and the second argument is the label
### Cross Entropy Loss
---
![[Pasted image 20251210194159.png]]
Measures the loss for binary classification where output is a probability between 0 and 1

### Mean Squared Error Loss (MSE)
![[Pasted image 20251210194517.png]]
Measures the loss for regression where output is a continuous real number

## Loss Optimization
---
Goal: find the “best” values of the model parameters that minimize the loss function. We can help accomplish this by utilizing derivatives and gradients, the derivatives will show the local slope while the gradients show the direction with respect to multiple functions. The negative of the gradient is the direction of function descent -> direction we want to move in the loss function landscape!

## Back Propagation
---
The goal is to update all of our parameters by calculating gradients, and back propagation helps accomplish that. To do it we compute the gradient and then test how one small change affects the final loss
## Loss Optimization: Gradient Descent
---
![[Pasted image 20251210195151.png]]
1. Initialize weights $W ← 𝑊^{(0)}$
2. While not converged do:
	3. 𝑖~𝑈𝑛𝑖𝑓𝑜𝑟𝑚({1,2, … , 𝑁})   // Optionally Add sampling
	4. Compute gradient $∇_𝑊𝐽(𝑊) = \frac{\partial J(W)}{\partial(W)}$
	5. Update weights
		$W ← 𝑊 − 𝛼 \cdot ∇𝑊𝐽(𝑊)$
3. Return 𝑊

Benefit
- Reliable on optimizing networks in the direction of the optimal drawback
- Large computation by go over the the entire data in each iteration

Sampling
- By adding this we converge much faster!
- But performs frequent updates with a high variance that cause the objective function to fluctuate heavily

## Model Regularization
Goal: Control over fitting, improve generalization of our model on unseen data
#### Dropout
During training, randomly deactivate nodes to 0
- For example, drop 30% of nodes in layer (they output 0)
- Forces network to not rely on any single node (each node captures generalized information)
- They don’t perform during testing
#### Early Stop
- Stop training before we have a chance to overfit
	- Monitor training/validation loss during training
	- Trigger if loss reduce reaches threshold

# References

