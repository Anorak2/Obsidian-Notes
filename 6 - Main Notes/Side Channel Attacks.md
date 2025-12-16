
2025-09-24

Tags: [[Software Security Evaluation]] [[Security]]
# Side Channel Attacks
Sometimes we have to deal with unconventional adversaries and threats we don't typically think about. A side channel is one such threat where an adversary is able to glean some type of information about our program. Examples include how hot our computers are (or how heavy the fans are running), electromagnetic emissions, execution time, and certainly others.

Something particularly damaging about side channels is that even partial information can be very damaging. For example if a side channel leaks half of a password then the brute force space is massively decreased, but this is true even if we only have one character or even just the length of the password.

## Timing Channels
Threat Model: 
- Interactive
- low-latency
- black box access to the program
- access to a precise timer
```
bool checkPW(const char * given){
	const char * expected = "12345"
	int gLen = strlen(given);
	int eLen = strlen(expected);
	if(gLen != eLen){ return false; }
	for(int i = 0; i < expected; i++){
		if(given[i] != expected[i]){
			return false;
		}
	}
}
```
This approach has a lot wrong with it, and attackers could gain a large amount of information from code built this way.

Better Code:
```
bool checkPW(const char * given){
	const char * expected = “12345”;
	int gLen = strlen(given);
	int eLen = strlen(expected);
	bool ok = true;
	
	if (gLen != eLen){
		ok = false; 
	}
	
	for (int i = 0; i < eLen; i++){
		int gIdx = math.min(gLen - 1, i);
		if (given[gIdx] != expected[i]){
			ok = false;
		}
	}
	return ok;
}
```

There are a number of issues that come with ensuring uniform execution. For one we necessarily slow down our computation to the worst case, the above example perfectly illustrates that. Many might not have enough understanding to recognize precise timing issues, especially among less senior developers. Lastly It also may not always be obvious what the worst case even is since in a system with tens of thousands of lines a single loop could sometimes represent massive amounts of execution time.

## Fixing Timing Side Channels
One potential way we could fix timing side channels is by combining several previous techniques:
- Instruction transformer to map out how much time that instruction takes
- Block Composition: Store the sum total of instruction times in a block
- Merge operation: Check that all operations have a comparable execution time
# References
[[Threat Models]]

[[Dataflow Frameworks]]