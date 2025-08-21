
2025-08-19

Tags: [[Programming]]
# Piet

Piet is an esoteric programming language that uses colors to encode meaning, due to this programs are images that look similar to abstract paintings.


## Important Links:
* Piet official Website(https://www.dangermouse.net/esoteric/piet.html)
- Assembler/Compiler (https://www.toothycat.net/wiki/wiki.pl?MoonShadow/Piet)
- Asm/Compiler github (https://github.com/sl236/Piet/blob/master/README.md)
- Npiet (https://www.bertnase.de/npiet/)
- npiet online (https://www.bertnase.de/npiet/npiet-execute.php)

## Colors:
![[Pasted image 20250820150221.png]]

Piet uses 20 colors that are related cyclically in two ways
- Hue Cycle:  red -> yellow -> green -> cyan -> blue -> magenta -> red
- Lightness Cycle: light -> normal -> dark -> light 

additional colors can be used and their meaning varies by implementation, but in the simplest implementation they are treated the same as white hence having no semantic meaning.

## Commands

|         |           | Color Change |            |
| ------- | --------- | ------------ | ---------- |
|         | None      | 1 Darker     | 2 darker   |
| None    |           | push         | pop        |
| 1 Step  | add       | subtract     | multiply   |
| 2 Step  | divide    | mod          | not        |
| 3 Steps | greater   | pointer      | switch     |
| 4 Steps | duplicate | roll         | in(number) |
| 5 Steps | in(char)  | out(number   | out(char)  |
Explanations:
- **push**: Pushes the value of the colour block just exited on to the stack. Note that values of color blocks are not automatically pushed on to the stack - this push operation must be explicitly carried out.
- **pop**: Pops the top value off the stack and discards it.
- **add**: Pops the top two values off the stack, adds them, and pushes the result back on the stack.
- **subtract**: Pops the top two values off the stack, calculates the second top value minus the top value, and pushes the result back on the stack.
- **multiply**: Pops the top two values off the stack, multiplies them, and pushes the result back on the stack.
- **divide**: Pops the top two values off the stack, calculates the integer division of the second top value by the top value, and pushes the result back on the stack. If a divide by zero occurs, it is handled as an implementation-dependent error, though simply ignoring the command is recommended.
- **mod**: Pops the top two values off the stack, calculates the second top value modulo the top value, and pushes the result back on the stack. The result has the same sign as the divisor (the top value). If the top value is zero, this is a divide by zero error, which is handled as an implementation-dependent error, though simply ignoring the command is recommended. (See note below.)
- **not**: Replaces the top value of the stack with 0 if it is non-zero, and 1 if it is zero.
- **greater**: Pops the top two values off the stack, and pushes 1 on to the stack if the second top value is greater than the top value, and pushes 0 if it is not greater.
- **pointer**: Pops the top value off the stack and rotates the DP clockwise that many steps (anticlockwise if negative).
- **switch**: Pops the top value off the stack and toggles the CC that many times (the absolute value of that many times if negative).
- **duplicate**: Pushes a copy of the top value on the stack on to the stack.
- **roll**: Pops the top two values off the stack and "rolls" the remaining stack entries to a depth equal to the second value popped, by a number of rolls equal to the first value popped. A single roll to depth n is defined as burying the top value on the stack n deep and bringing all values above it up by 1 place. A negative number of rolls rolls in the opposite direction. A negative depth is an error and the command is ignored. If a roll is greater than an implementation-dependent maximum stack depth, it is handled as an implementation-dependent error, though simply ignoring the command is recommended.
- **in**: Reads a value from STDIN as either a number or character, depending on the particular incarnation of this command and pushes it on to the stack. If no input is waiting on STDIN, this is an error and the command is ignored. If an integer read does not receive an integer value, this is an error and the command is ignored.
- **out**: Pops the top value off the stack and prints it to STDOUT as either a number or character, depending on the particular incarnation of this command.

int a = input(num)
for(int x = 0; x < a; x++){
	if(x % 10 && x % 5){
		print(fizz buzz)
	} else if (x % 10){
		print(fizz)
	} else if (x % 5){
		print(buzz)
	}
}

index
range

asm version 
	in        # to choose the number to run to
	push 0
	{     # For statement
		{      # if statement 1
			push f
			out
			push u
			out
			...
		}
		{      # if statement 2
			push f
			out
			...
		}
		{        # if statement 3
			push b
			out
			...
		}
		DUP
		ROLL 3 - 1
		DUP
		GREATER
	}
	
# References

