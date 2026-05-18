
2025-06-06

Tags: [[Networking]] [[High Performance Computing]]
# Interconnection networks
**Metrics**
- Cost, the total number of links
- Degree, maximum number of links connected to a single node
- Diameter, defined as the longest in the sets of shortest paths
- Bisection Width, the minimum number of connections to cut if we wanted to form 2 roughly equal halves
- Switch, the number of switches necessary for the network

## **Static Structures:**

|                      | Cost                    | Degree    | Diameter           | Bisection Width | Switches |
| -------------------- | ----------------------- | --------- | ------------------ | --------------- | -------- |
| Completely Connected | $\frac{p(p-1)}{2}$      | $p-1$     | 1                  | $p/2$           | -        |
| Star                 | $p-1$                   | $p-1$     | 2                  | $p/2$           | -        |
| 1d Array (chain)     | $p-1$                   | 2         | $p-1$              | 1               | -        |
| Ring                 | $p$                     | 2         | $\approx p/2$      | 2               | -        |
| 2d Array (2d mesh)   | $2\sqrt{p}(\sqrt{p}-1)$ | 4         | $2\sqrt{p}-1$      | $\sqrt{p}$      | -        |
| 2d Torus             | $2p$                    | 4         | $\approx \sqrt{p}$ | $2\sqrt{p}$     | -        |
| 3d Mesh              | $(p-p^{2/3})$           | 6         | $3(p^{1/3}-1)$     | $p^{2/3}$       | -        |
| 3d Torus             | $3p$                    | 6         | $1.5p^{1/3}$       | $2p^{2/3}$      | -        |
| Hypercube            | $\frac{p \log p}{2}$    | $\log_2p$ | $\log_2p$          | $p/2$           | -        |
![[Pasted image 20250606233855.png]]

## **Dynamic Structures**
Typically with the following dynamic structures only the leaf nodes are actual compute nodes, with all of the other being switches and used for routing.

| Dynamic              | cost      | degree | diameter  | Bisection Width | switches |
| -------------------- | --------- | ------ | --------- | --------------- | -------- |
| Complete Binary Tree | $2(p-1)$  | 3      | $2 \lg p$ | $1$             | $p-1$    |
| Fat Tree             | $p \lg p$ | p      | $2 \lg p$ | $p/2$           | $p-1$    |
Fat Binary Tree:
![[Pasted image 20250606234040.png]]


# References