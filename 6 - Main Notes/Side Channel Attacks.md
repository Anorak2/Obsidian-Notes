
2025-09-24

Tags: [[EECS 677 - Software Security Evaluation]] [[Security]]
# Side Channel Attacks
A side channel is when an adversary is able to glean some type of information about our program through methods that aren't usually considered in security analysis. Examples include heat, electromagnetic emissions,  or importantly timing.


## Timing Side channels
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

The problem is that in ensuring uniform execution we necessarily slow down our computation to the worst case, it may be very difficult to have enough understanding to recognize precise timing issues. It also may not always be obvious what the worst case even is.


# References

