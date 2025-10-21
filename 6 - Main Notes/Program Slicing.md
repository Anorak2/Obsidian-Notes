
2025-09-29

Tags: [[EECS 677 - Software Security Evaluation]] 
# Program Slicing
> What if we want to ignore all data that is "irrelevant" for a particular case? The CDG and PDG show all of the information related to the control flow and and dataflow

Introduce slicing:
**Forward Slice**: Everything influenced by the statement K
**Backwards Slice**: Everything that influences the statement K
![[Pasted image 20250929230816.png]]

If we need our slice to be executable we may need to add additional instructions. We may also want our sliced program to behave identically to the original, if so then we'll need additional output dependence edges.

Tooling: DG
https://github.com/mchalupa/dg
This tool is a static slicer for LLVM bitcode.
## Uses:
- Program comprehension, ie what is this statement doing
- Debugging
- Scaling heavyweight analysis so that way you have less program to test
# References
[[Domination and Control Dependence Graph]]
