Topics
- Class Hierarchy Analysis
- Points-to Analysis
- Reference Monitors
- Program Instrumentation
- Static Instrumentation
- LLVM Instrumentation
- Dynamic Analysis
- Control Flow Integrity
- Fuzzing
- Symbolic Execution
- Concolic Execution
- Sat solving    (The DPLL stuff)
- SMT solving
- SSDLC  (Not On Here)

In terms of levels of complexity
Testing 
	Fuzzing (mutation based or pure random)
		Symbolic Execution (Classes of Input)


Concolic Execution is when we make symbolic execution concrete. We do this when we have issues with budget or when there are things we can't symbolically represent. Conjunctive normal form in the SAT solver. Nelson Oppen.

We may have to do DPLL exactly at it says: this means as much unit propagation as possible, then as much pure literal as possible, then doing case splitting.

**Actual Questions**
- Something points to
- something symbolic execution tree
- something about llvm or static instrumentation
# Exam Questions
## Q1
Base:
If we have to count then we don't count states that are unreachable or states that are not feasible.
![[Pasted image 20251110192534.png]]
#### Spoiler
we say that $\alpha$ is greater than zero and less than `0xFF`
Then we slit so that 
$(4) \space \space \alpha< 0xFF \space | \space \alpha > 10$  and (10) $\alpha \leq 10 \space | \space \alpha \geq 0$
- The right one then terminates here 
- We then try to split the 

![[Pasted image 20251110193134.png]]

## Q2
Understand the specific steps of DPLL and their names

![[Pasted image 20251110193326.png]]
#### Spoiler
Unit Propagation
- Set a to false
- b  &&  !b  &&  c  &&  (d | !b)  && (c | e)
- You could reasonably stop here and be done since we have b & !b
- set c to true
- b  &&  !b  &&  (d | !b)

Pure Literal
- At first A is both negated and not, b is both negated and not, c is never negated
- Set C to true
- (a | b)  &  !a  &  (!b | a)  &  (d | !b)
- D wants to be true
- (a | b)  &  !a  &  (!b | a)            // stop here
## Q3
Skipped

## Q4
![[Pasted image 20251110194801.png]]
Reasoning matters way more to Drew. We may say that blackbox gives more information when we don't have source code. White box may help you bias your random values to more interesting cases.
## Q5
![[Pasted image 20251110195457.png]]
#### Spoiler
if it was just a = b then if b pointed to C then A would also point to. The `a= *b` means it would be two levels deep. Below is an example of what that might look like
![[Pasted image 20251110195731.png]] 

After one round this is what we are left with: 
![[Pasted image 20251110195836.png]]
We then go through this again until we reach a fixpoint which happens after we do one more pass through.

If at any point in the analysis we said something like `c=&y` then B would point to Y right after that, but then we would also have to consider a points to everything that y points to.

## Old Mobile Sec
What is the difference between static instrumentation and static analysis?
#### Spoiler
- what is static instrumentation about
- what is the difference between an inline reference monitor and static instrumentation
		static instrumentation: preserves semantics
		dynamic instrumentation: works when semantics are tampered with

## Other 1
![[Pasted image 20251110201425.png]]
#### Spoiler
We could just do an immediate call to the operating system
ex:     
```
a = sha1(getchar());
if (b > 7) {
	explode;
} else {
	return 0/0;
}
```
## Other 2
![[Pasted image 20251110201751.png]]

#### Spoiler
(a | !b)  &  (!a | b)
## Other 4
![[Pasted image 20251110202004.png]]
#### Spoiler
A reference monitor looks for bad behavior (violation of some sort of policy)...
Killing a program is never enough to make it return some answer eventually.

## Other 5
Anderssons analysis of 
a = &d
a = &b
b = &c
z = &x
z = a

Note: self loops aren't necessarily incorrect
#### Spoiler
![[Pasted image 20251110202324.png]]
## Other Questions
# Other
![[Pasted image 20251116193838.png]]
