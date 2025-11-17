
2025-11-16

Tags: [[EECS 677 - Software Security Evaluation]] [[Dynamic Analysis]]
# Fuzzing
How do we generate good test cases?
- Cases that exercise unexpected behavior
- Cases that increase coverage of program behaviors

How do we predict unpredictable behavior? well the truth is that it is strictly impossible, so what if instead we threw all expectations away and we expose our program to **random** behavior. The key principle here is that given any input the error should be anticipated and handled gracefully, ideally with an informative error message. 

It turns out that random input is very good at finding bugs, and fuzzing has some very nice benefits such as:
- Very easy to run
- Instant results
- Highly scalable

#### Simplest Form
` cat /dev/random | program`
A study in the 90s basically did this, finding bugs in:
```
adb, as, bc, cb, col, diction, emacs, eqn, ftp, indent, lex,
look, m4, make, nroff, plot, prolog, ptx, refer!, spell, style,
tsort, uniq, vgrind, vi
```
The challenge of fuzzers is (usually) getting past the first validation check, or put another way most input isn't "interesting" and will fail in the same ways.

#### Mutation Based Fuzzers
- Explore deviations from known input

Example mutations on binary input:
-  bit flips
- byte flips
- change random bytes
- insert random byte chunks
- delete random byte chunks
- set randomly chosen byte chunks to interesting
Values e.G. Int_max, int_min, 0, 1, -1, … §
Text input
- insert random symbols or keywords from a dictionary
#### Black Box Fuzzing
The idea is to just not over complicate things, just throw input at the application interface.
For example `zzuf` is considered a multipurpose fuzzer. 
```Example
	zzuf cat /dev/zero | hd -vn 32
	zzuf -r 0.05 hd -vn 32 /dev/zero
```

#### American Fuzzy Lop (AFL)
AFL is a fuzzer created by google and generally considered state of the art.

```Basic-Run
mkdir in_dir
echo “hello” > in_dir/hello
afl-fuzz -n -i in_dir -o out_dir cat
```
# References
[[Dynamic Analysis]]

