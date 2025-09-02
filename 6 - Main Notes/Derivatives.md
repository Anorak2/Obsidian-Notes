
Tags: [[Calculus Bibliography]] [[Math]]
# Derivatives

$$f'(x)=\lim_{x \to a} \frac{f(x)-f(a)}{x-a}=\lim\limits_{x \to a} \frac{f(a + h) - f(a)}{h}$$
This is the limit definition of a derivative, and it represents the instantaneous rate of change for a function. Another way to express this is if we are looking at a polynomial, say $x^2-7x+9$, then it's derivative, $2x-7$, is a tangent line that will touch the graph exactly once.

## Power Rule
The power rule is probably the most fundamental rule, it says that we can find the derivative of a simple function by doing

$$f(x)= x^2+x+5$$
$$f'(x) = 2x +1$$
what is going on here? We are multiplying the variable by it's power, and then subtracting one from it's exponent which looks like $x^2 \to 2x^2 \to 2x^1$. If we are differentiating a constant it turns into zero, this makes intuitive sense since a derivative represents the rate of change and a constant doesn't change.

## Chain Rule
If a we have two functions F and G that are differentiable at x. Then we can define a function $H=f(g(x))$, then we can calculate it's derivative to be:

$$H'(x) = f'(g(x))g'(x)$$


We can then apply the power rule in a different way now that we know the chain rule
![[Pasted image 20230215132554.png]]
## Product Rule
The product rule covers cases where two functions are being multiplied together, for example:
$$H(x) = f(x)\times g(x)$$
we can take the derivative of this by applying 
$$H'(x) = f'(x)g(x)+f(x)g'(x)$$ 
## Quotient Rule
This is the rule that lets us solve derivatives where we have two functions on top of each other, for example:
$$H(x) = \frac{f(x)}{g(x)}$$
and how we can handle that is by applying the formula
$$H'(x)=\frac{f'(x)g(x)-f(x)g'(x)}{(g(x))^2}$$

## Notations
### Lagrange:
y' = f'(x)
### Leibniz
$\frac{d}{dx}(f(x)) = \frac{dy}{dx} = \frac{df}{dx}$
### Higher Derivatives
$f''(x), f'''(x), f^{(n)}(x)$

$$\frac{d}{dx}(f(x)) = \frac{d^2y}{dx^2}$$

# References
[[Limits]]

[[Derivatives and Limits of Trig Functions]]