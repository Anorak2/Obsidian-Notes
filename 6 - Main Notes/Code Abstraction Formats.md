
2025-08-20

Tags: [[EECS 677 - Software Security Evaluation]] [[Code Review]]
# Code Abstractions

# Flow Charts
its not super efficient to examine the source code as is, and as such it can be really helpful to use abstractions. These can help highlight underappreciated aspects of the target program (maybe some random method opens an unsecured ftp server briefly) or make it easier to work with in general.

Flowcharts:
Nodes are instructions, and edges point to the next nodes. There is only one instruction per node

# Control flow Graphs
Basic Blocks: A sequence of instructions guaranteed to execute without interruption

Basic Block Boundaries:
- Leader: This is an instruction that begins the block and it is the first instruction in the procedure
- Terminator: This is the instruction that ends the block

# Intermediate Representations


# SSA Form
The idea of static single assignment is that there is only one line of text in which a variable can be assigned:

**Correct SSA form:**
```
	int a = 1;
	int b = 1;
```

**Not in SSA form:**
```
	int a = 1;
	a += 2;
	
	if(b) {
		a = 1
	} else {
		a = 2
	}
```

# References

