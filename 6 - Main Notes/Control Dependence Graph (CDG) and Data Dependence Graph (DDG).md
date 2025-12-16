
2025-09-29

Tags: [[Software Security Evaluation]]
# Control Dependence Graph (CDG) 

**Control Dependence Graph:** This is the graph that shows which statements must run before another statement is able to execute. 

Fig 1. Control Dependence example; **must** a statement x be executed for y to execute
![[Pasted image 20250929223900.png]]

# Data Dependence Graph (DDG)
![[Pasted image 20250929225631.png]]
```
DDG:
L2 -> L1
L5 -> L1
L5 -> L4
```

# Program Dependence Graph
![[Pasted image 20250929225844.png]]
The program dependence graph is simply an overlay of the CDG and the DDG.

# Examples 
Given Code:
```
1. int main() {
2. 	i = getchar();
3.	if(i == 1){
4.		printf("Hi");
5.	} else {
6.		i = 1;
7.	}
8.}
```
![[Pasted image 20250929225203.png]] 


# References

