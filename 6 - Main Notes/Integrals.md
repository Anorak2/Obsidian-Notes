
2025-09-02

Tags: [[Calculus Bibliography]] [[Math]]
# Integrals
An Integral is a way to measure the area of the function "under the curve", with the parts of the function above the x-axis counting as positive and the parts below counting as negative.  

**Fundamental Theorem of Calculus**
The FTC states that f is continuous and finite on the interval [a,b ] then the following holds:
$$\int_a^bf(x)dx = F(b)-F(a)$$
This is incredibly important since it really doesn't get any simpler, and this method is far far easier than the methods involving Riemann sums 

## Definite Integral
> The definite integral calculates **net area**; the area below the positive part of the graph minus the area below the negative part.

The definite integral of a function f on the interval [a,b] is
$$\int_a^b f(x) \space dx = \lim_{n\to \infty} \sum_{i=1}^n \space f(x_i) \Delta x$$
where $\Delta x = \frac{b-a}{n}$ and $x_i = a + i \Delta x$, provided that this limit exists.

Notice how the definition relies on limits, how do we know if a function is integrable? 
> if f is continuous on [a,b], or if f has only a finite number of jump discontinuities, then f is integrable on [a,b]


## Definite Integral Properties
#### Property 1
$$\int_a^b f(x) \space dx = -\int_b^a f(x) dx$$
#### Property 2
$$\int_a^a f(x) \space dx = 0$$
> This is because the interval [a, a] has a length of 0

#### Property 3
$$\int_a ^b c \space dx = c(b-a)$$
#### Property 4
$$\int_a^b F(x)\space dx = \int_a^c f(x) \space dx + \int _c^b f(x) \space dx$$
## Integral Comparison
#### Property 1
$$\text{If f(x)} \geq 0 \text{ for } a \leq x \leq b \text{, then } \int_a^b f(x) \space dx \geq 0 $$
> If a function is greater than 0 over the range [a,b], then the integral over [a,b] will also be greater than 0
#### Property 2
$$\text{If } f(x) \geq g(x) \text{ on the interval } [a,b] \text{, then} \int_a^b f(x) \space dx \geq \int _a^b g(x) \space dx$$
> If a function is always bigger than the other, then the integral will also be larger
#### Property 3
If $m \leq f(x) \leq M$ on the interval [a,b], then
$$m(b-a) \leq \int_a^b f(x) \space dx \leq M(b-a)$$
> If the function is bounded then the integral will also be bounded
## Indefinite Integral

The Indefinite integral is an "anti-derivative" of a function is a function F(x) such that:

$F'(x) = f(x)$


when working with integrals we always have to add a constant c because the constant could be anything, this is because doing a derivative can destroy some information and we must account for the possibility. if F and G are both integrals of f(x) then g(x) = F(x) + c, n where c is some constant


## Integral Techniques

#### Inverse power rule
if we have $x^n$ we first add one to the exponent to get $x^{n+1}$ and then divide by the exponent to get:
$$\frac{x^{n+1}}{n+1}$$

if we have $x^{-1}$ we must do the absolute value of natural log instead since we can't divide by 0.

for $a^x$ it becomes
$$ \frac{a^x}{ln(a)}+c$$

#### UV methods
$$ \int u \space dv= uv - \int v \space du$$
I mean it's the u/v method, when doing this make sure you make "similar" choices.  What I mean is if you use something as the derivative, keep doing that otherwise things may break.

#### Partial Fractions
![[Pasted image 20230920110542.png]]

#### Trig Substitution
There are several forms that have been proven to be equivalent and by substituting one function for another we can sometimes simplify our functions further

with these forms we can substitute in a trig function in the same way where we would sub something in with u sub.
$$\sec^2\theta = \tan^2\theta+1$$ $$\sin^2\theta = 1-\cos^2\theta$$ $$\tan^2\theta = \sec^2\theta-1$$ 

# References
[[Limits]]
