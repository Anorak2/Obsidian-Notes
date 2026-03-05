
2026-02-17

Tags: [[Data Mining and Machine Learning]]
# Hidden Markov Models (HMM)
In most of these files we are categorizing single events but markov models and RNNs categorize a sequence, such as words. HMM's work by having a series of states, like a finite state machine, and on each sequential input the HMM may transition to a new state or remain in it's current state. In the below image $\pi$ is an entrance, while a is an event. The output of the HMM is the current state.
![[Pasted image 20260217165617.png]]
Markov models operate statistically, so there is a probability that with each input the state will change to a different state. All of the probabilities from a node must equal 1 of course.

Apparently HMM's are still powerful enough to see modern usage, mainly in computational biology and bioinformatics.

## Weaknesses
A HMM assumes the probability of the next state only depends on the current state, and is independent of any previous states. In a lot of cases, knowing previous states would help make a better prediction of the next state. For example, if given the 1st, 2nd, and 3rd letter of a word, you will be able to guess it much better than if I only give you the 1st letter. This weakness in HMMs is usually overcome by creating n-gram models, which treats the last n emissions as one (hence growing exponentially).

## Practical
https://en.wikipedia.org/wiki/Viterbi_algorithm
Scikit Versions
- GaussianHMM
- MultinomalHMM
- GMMHMM
# References

- [[Finite State Machines]]

