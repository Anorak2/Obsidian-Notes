
[[Stats Bibliography]]
A [[Bivariate RVs|Joint PMF]] contains information about both RVs G and H, and their relationship. Information about the individual RVs is contained in the PMFs $P_g(g)$ and $P_H(h)$ which are called the **marginal PMFs** 

**FINDING**
$$P_G(g) = \sum_{h \in S_H} P_{G, H}(g,h)$$
$$P_H(h) = \sum_{g \in S_G} P_{G, H}(g,h)$$
We are just adding up all of the rows or columns in order to eliminate a variable

**PROBABILITIES**
To find the probability of a range of events, we double integrate the PDF with the bounds representing the interval,
Ex:
$$\int_{8.5}^{10.5} \int_{120}^{240} c \space dh \space dg $$
this would be for a uniform distribution where $f_{G,H}(g,h) = c$ within the given range, and 0 otherwise. (c = 1/240) 

**INDEPENDENCE**
If one RV restricts the range of the other, they are NOT independent

We can also test by finding the marginals, and then multiplying them. if $F_G(g) \cdot f_H(h)$ = the inside of the joint PMF then they are independent

**EXPECTED VALUE**
The expected value of K = $j(G,H)$ is
Discrete: $E[k] = \sum _g \sum_h j(g,h)P_{G,H}(g,h)$
Continuous: $E[k] = \int _g \int_h j(g,h)F_{G,H}(g,h) \space\space dh\space dg$
