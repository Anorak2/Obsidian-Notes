
2025-09-07

Tags: [[Computer Science]] [[Theory of Computing]]
# The Halting Problem
> Given a description of a Turing machine and its initial input, 
> determine whether the program, when executed on this input,
> ever halts (completes). The alternative is that it runs forever without halting

The fundamental problem is that it can be extraordinarily difficult to determine if a particular Turing machine will ever halt or if it will continue to run indefinitely. 

We can actually prove rather easily that it is impossible to ever determine if a Turing machine halts. If we assume that there is a halting detector that returns true if the function halts, and false if it doesn't then we can defeat it with the following code:
```
black_magic(){
	if (halts(black_magic){
		while(true){} //Spin
	}
	//Halt
}
```


## Theory of computing terms
- If a TM halted on every input that's essentially an algorithm
- Total Function - a function that has a TM that always halts
- Partial Function - a function that has a TM that fails on some inputs
- A language for which there is a TM that always halts (either rejecting or accepting its input) is known as a Turing-decidable language (recursive language)
- A language recognized by a TM that does not halt on every input is known as a Turing-recognizable language (recursively enumerable language)

# References
