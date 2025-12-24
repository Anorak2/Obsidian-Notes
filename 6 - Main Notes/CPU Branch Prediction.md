
2025-12-20

Tags: [[Performance Measurement & Reliability]]
# CPU Branch Prediction
### Static Branch Prediction
Static branch prediction is based on typical branch behavior, for example in loop and if statement branches we may predict that the backward branches are always taken (the loop continues) and that the forward branches are not taken.

### Dynamic Branch Prediction
In this version the hardware measures actual branch behavior and dynamically updates it's prediction. It assumes that future branches will continue the trend, and updates it's history on an incorrect prediction.

![[Screenshot from 2025-12-19 23-21-06.png]]
Above is an actual program I tested using Perf stat, all that is done is a minimal hello world function (with void main) and using <stdio.h> for `printf`. In this version my CPU's dynamic branch prediction was about 93% accurate.

![[Screenshot from 2025-12-20 00-30-18.png]]
For another, albeit simulated run, of a test program the branch mispredict rate was only 0.6%, although this program was very generous with it's design. This program iterated through a large list with random length in the millions, generated a random int for each index, and then did a static op on each index. 

# References
- [[CPU Data Path]]
- [[Multi-Data Path and Pipelining]]

