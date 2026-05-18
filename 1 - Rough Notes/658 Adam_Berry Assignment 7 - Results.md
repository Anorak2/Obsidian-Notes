# Part 1 
runtime results, using threshold val of 10^-6):

![[Screenshot-2026-04-28-22 24 08.png]]


**Question 1**
I picked the simple convergence check we covered in RL policy since it seemed particularly robust to me, partially out of it's simplicity. It also just seems like the most intuitive way to find a fixpoint since this function uses the definition of a fixpoint almost exactly
![[Pasted image 20260428221348.png]]


# Part 2
![[Pasted image 20260428225519.png]]

**Question 2**
I used the same convergence algorithm, partially for the robustness and partially for the convenience since I had already implemented it

![[Pasted image 20260428221348.png]]


**Question 3**
Value Iterations converges in just k=4 total iterations, while policy took until k=93 which is a massive >20x in number of iterations. When I test again with a grid size of 50, terminal points at (0,0) and (49,49) policy iteration converges in k=7532 steps while value iteration takes until k=49. This also is true with policy having ~20s runtime, with value having ~0.5s runtime. 

Policy Iteration would be better for an example with a smaller policy space, value iteration is able to do very well here since the space is relatively small and uniform. Policy iteration does have a sense of being much more powerful since it makes less assumptions but I'm not sure what problems it would be suited for. I will also say here policy iteration reminds me of a graph display algorithm using springs between every connected node with a physics sim to build a display to show neighbors.



$$\delta_t = Q(s_t, a)-Q(s_{t+1}, a)$$



| $Q(s_t, a)$ | $Q(s_{t+1}, a)$ | $\delta_t$ | e     | $p_t$ | $P(i)$, if a=1 | $P(i)$, if a=0 |     |
| ----------- | --------------- | ---------- | ----- | ----- | -------------- | -------------- | --- |
| 1           | 5               | 5-1 = 4    | 0.001 |       |                |                |     |


