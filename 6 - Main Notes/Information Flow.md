
2025-09-29

Tags: [[Software Security Evaluation]] [[Data]]
# Information Flow
We must first remember the [[CIA Triad]], balancing between confidentiality, availability, and integrity. When formalized into what it means with respect to data flow:
- **Confidentiality**: high security data should not influence low security functionality
```
string loc = getUserLocation();  // High security source
if (inKansas(loc)){
	print “Watch out for tornados!”;
}
writeToNetwork(loc);  // Low security Sink
```
- **Integrity**: low security data should not influence high security functionality
```
string netVal = readFromNetwork(); // Low security source
setPassword(“root”, netVal);   // High security sink
```

## Sources and Sinks
- A **source** operation – an operation that generates data
- A **sink** operation – an operation that consumes data
- A **flow** – a program path segment that begins at a source and ends at a sink

how do we know what should be a source and a sink? Three main ideas: Programmer annotations, build annotations into the system, "something something inferencing hardware".

**Programmer Notation:** The basic idea is that we ask the programmer what is a source and what is a sink, and we can then either store the inline or in a separate file of info. The problem is that humans are fallible and that we're trying to solve a human made problem with humans. This opens us up to issues such as laziness and incorrect annotations.

**Built in Annotations:** What if instead we bake capabilities into the system and these annotations can be retrofitted into the analysis engine. This again has the issue of the semantic gap, it can be really hard to predict what is security relevant and the analysis engine needs to be in perfect sync with the system.

**Inferencing:** What if we try to automatically discover "source like" and "sink like" operations 
# References
[[CIA Triad]]

[[Dataflow Frameworks]]