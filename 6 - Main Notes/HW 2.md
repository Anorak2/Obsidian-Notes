[[High Performance Computing]]
# Homework Number 2
Adam Berry

I'm sorry for the messy equations, I found these problems hard 


# Problem #1 

**Thm:** LPT scheduling is a $3/2$ approximation of the ideal makespan for $P||C_{max}$ 

**Proof**
Taking the jobs and first  doing some sorting we have $p_1 \geq p_2 \geq ... \geq p_n$
Without loss of generality we can assume that the last job is the job that completes last, since otherwise removing this last job doens't affect the makespan of LPT while possibly improving the optimum makespan. 

Let the start time of $job_n$ be $T_1$, which makes the makespan of LPT is $T_{LPT} =T_1+P_n$, and due to the greedy choice of LPT, $T_1$ is the load of the least loaded processor when assigning job n has to be less than or equal to $T_{opt}$ 
$$ T_1 \leq \frac{\sum_j p_j}{m}$$

We can also assume that the number of jobs n > m, since otherwise LPT is optimal. Thus, the optimal schedule must have at least 2 jobs assigned to the same processor due to the pidgeon hole principle. This implies $T_{opt}\geq 2P_n$ => $P_n \leq \frac{T_{opt}}{2}$.

This leaves us with
$$T_{LPT} = T_1 +P_n$$

$$T_{LPT} \leq \frac{\sum_j P_j}{m}+ \frac{T_{opt}}{2}$$ However we can reduce this since $P_n \in \frac{\sum_jP_j}{m}$, means that we are double counting a portion of $P_n$

**Therefore,** 


$$T_{LPT} \leq \frac{\sum_j P_j}{m}+ \frac{T_{opt}}{2}-\frac{P_n}{m}$$
$$T_{LPT} \leq T_{opt}+ \frac{T_{opt}}{2} - \frac{\frac{T_{opt}}{2}}{m}$$
$$T_{LPT} \leq \frac{3}{2}T_{opt} - \frac{T_{opt}}{2m}$$
$$T_{LPT} \leq (\frac{3}{2} - \frac{1}{2m})T_{opt}$$





# Problem #2 
1.
$$E[t] = P(fail)(T + V + R + E[t]) + (1-P(fail))(T+V+C)$$
	P(fail) = $1 - e^{-\lambda T }$
$$E[t] = (1-e^{-\lambda T})(T+V+R+E[t]) + (e^{-\lambda T})(T + V + C)$$
$$E[t]-(1-e^{-\lambda T})E[t]=(1-e^{-\lambda T})(T+V+R) + (e^{-\lambda T})(T + V + C)$$
$$E[t](1-(1-e^{-\lambda T}))=(1-e^{-\lambda T})(T+V+R) + (e^{-\lambda T})(T + V + C)$$
$$E[t](e^{-\lambda T})=(1-e^{-\lambda T})(T+V+R) + (e^{-\lambda T})(T + V + C)$$
$$E[t]=\frac{(1-e^{-\lambda T})(T+V+R) + (e^{-\lambda T})(T + V + C)}{(e^{-\lambda T})}$$

$$E[t]=(e^{\lambda T})[(1-e^{-\lambda T})(T+V+R) + (e^{-\lambda T})(T + V + C)]$$

$$E[t]=((e^{\lambda T})-(e^{\lambda T})e^{-\lambda T})(T+V+R) + (e^{\lambda T})(e^{-\lambda T})(T + V + C)]$$
$$E[t] = (e^{\lambda T}-1)(T+V+R)+(T+V+C)$$

2. for a first order approximation:
$$H[t] = \frac{(e^{\lambda T}-1)(T+V+R)+(T+V+C)}{T}-1$$
$$H[t] = \frac{(e^{\lambda T}-1)(T+V+R)}{T}+\frac{(T+V+C)}{T}-1$$
$$H[t] = \frac{(e^{\lambda T}-1)(T+V+R)}{T}+\frac{V+C}{T}$$
$$H(T) \approx  \lambda(T + V + R) + \frac{V+C}{T}$$
First derivative with respect to T:
$$\frac{dH(T)}{dt} = \lambda - \frac{V+C}{T^2} = 0$$
$$T^2=\frac{V+C}{\lambda}$$
$$T = \sqrt{\frac{V+C}{\lambda}}=\sqrt{(v+c)\mu}$$


# Problem #3
- With a probability of p, rent up to time T and then buy
- With a probability of (1-p), rent up to time B and then buy

The generalized case can be set up as:
$$
    E[cost_{alg}](\sigma) = \begin{cases} 
          \sigma & \sigma \lt T \\
          p(T+B) + (1-p)\sigma & T \leq \sigma \lt B \\
          p(T+B)+(1-p)(2B) & \sigma \geq B
       \end{cases}
    $$

$$
    E[cost_{opt}](\sigma) = \begin{cases} 
          \sigma & \sigma \lt T \\
          \sigma & T \leq \sigma \lt B \\
          B & \sigma \geq B 
       \end{cases}
  $$
  with $\frac{alg}{optimal}$:

$$
    = \begin{cases} 
          1 & \sigma \lt T \\
          \frac{p(T+B) + (1-p)\sigma}{\sigma} & T \leq \sigma \lt B \\
          \frac{p(T+B)+(1-p)(2B)}{B} & \sigma \geq B
       \end{cases}
    $$

$$
    = \begin{cases} 
          1 & \sigma \lt T \\
          \frac{p(T+B) + (1-p)B}{\sigma} & T \leq \sigma \lt B \\
          \frac{p(T+B)+(1-p)(2B)}{B} & \sigma \geq B
       \end{cases}
    $$
Simplifying
$$
    = \begin{cases} 
          1 & \sigma \lt T \\
          p\frac{(T+B)}{\sigma} + (1-p) & T \leq \sigma \lt B \\
          p\frac{(T+B)}{B}+2(1-p) & \sigma \geq B
       \end{cases}
    $$
    
The critical points are when $\sigma$ is equal to T, equal to B, and greater than B

$\sigma = T:$  $p(B/T+1) + 1 - p$ 
$\sigma \approx B:$  which simplifies to   $p(T/B) + 1- p$ 
$\sigma \gt B:$  which simplifies to  $p(T/B-1)+2$

$$
    = \begin{cases} 
          1 & \sigma \lt T \\
          p((T/B) + 1)+ (1 - p) & T \leq \sigma \lt B \\
          p((T/B)+1)+2(1-p) & \sigma \geq B
       \end{cases}
    $$

$$
    = \begin{cases} 
          1 & \sigma \lt T \\
          p(T/B) + p + 1 -p & T \leq \sigma \lt B \\
          p(T/B)+p+2-2p & \sigma \geq B
       \end{cases}
    $$

$$
    = \begin{cases} 
          1 & \sigma \lt T \\
          p(T/B) + 1 - p & T \leq \sigma \lt B \\
          p(T/B-1)+2 & \sigma \geq B
       \end{cases}
    $$

