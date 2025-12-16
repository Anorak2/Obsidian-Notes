Tags: [[Algorithms]] [[3 - Tags/Optimization|Optimization]]
# Measuring Computing Cost
### Technique 1 - Time it
Just measure it, log the time before executing the program and after it finished running.

This does work but the downside is that it is dependent based on hardware or even just different different points in time, as well as it also could just take a very long time to run or the computation power

### Technique 2 - Count Possible Operations
Count possible operations for an array with a size <10,000. This is good because its independent of the machine and input dependence is captured in the model. By count this means literally counting how many times each section of the code will run, == variable assignment etc

This technique is bad because its tedious to compute, the array size was arbitrary, and it doesn't tell you the actual time it takes to run.

**We can improve by using values of N**
This means we categorize each bit in terms of the size of the list. For example we may have 2 to $n^2-n$ array accesses, however this is even more tedious to compute than the previous one.

# References
[[Big O Notation]]

[[Big Theta Notation]]
