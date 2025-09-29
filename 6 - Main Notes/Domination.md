
2025-09-29

Tags: [[EECS 677 - Software Security Evaluation]]
# Domination

DOM(X,Y) Paths to Y must go through X
you cannot get to y without going through x
> X guards the path to Y


FDOM(X,Y) Paths from X  must go through Y
> Y is guaranteed to be in the future of X

Control Dependence: Y CD x <-> there is a CFG path from X to Y omitting IFDOM(X)
> it's possible to get from X to Y but it's not guaranteed


# References

