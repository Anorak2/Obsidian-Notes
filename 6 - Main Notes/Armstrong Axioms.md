Status:

Tags: [[Databases]]
# Armstrong Axioms

All implied [[Functional Dependencies]] can be figured out using the Armstrong axioms. What this means is that if we know the [[Functional Dependencies|FD's]] we can derive all implied FD's using the Armstrong axioms and help us determine a key for a relation

* Reflexivity: if all elements of $\beta$ are in  $\alpha$,  then $\alpha \to \beta$ 
* Augmentation: if $\alpha \to \beta$. then $a \cup y \to \beta \cup y$ 
* Transitivity: if $\alpha \to \beta$ and $\beta \to \gamma$ then $\alpha \to \gamma$ 

from these we can derive:
- Union: if $X \to Y$ and $X \to Z$ then $X \to YZ$
- Decomposition: if $X \to YZ$, then $X \to Y$ and $X\to Z$
- Pseudo-transitivity: if $X \to Y$ and $WY \to Z$, then $WX \to Z$ 

# References
[[Functional Dependencies]]