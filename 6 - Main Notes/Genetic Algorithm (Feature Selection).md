
2026-03-26

Tags:
# Genetic Algorithm (Feature Selection)
GA is another non-greedy algorithm for finding the optimal set of features when brute-force selection is impractical due to time complexity and/or space complexity. Like Simulated Annealing, it is a non-probabilistic method which makes no assumptions about the statistics of the feature set.

## Workings
![[Pasted image 20260326231342.png]]
**Initialize**
In a genetic algorithm, an initial population of candidate solutions (feature sets), called individuals, is initialized and then repeatedly optimized. The evolution usually starts from an initial population of individuals (e.g., ML feature sets), and is an iterative process, with the population in each iteration called a generation.

**Evaluation**
In each generation, the fitness of every individual in the population is evaluated. The fitness is usually the value of the objective function in the optimization problem being solved. For ML feature selection, this is usually Accuracy.

**Selection**
The more fit individuals are selected from the current population. Usually, this is as simple as taking the n most fit individuals. For ML, this is the n sets of features with the highest Accuracy. Selection is similar to natural selection in evolutionary biology.

**Crossover**
The more fit individuals are selected from the current population, and each individual’s genome is modified (recombined and randomly mutated) to form a new generation. Recombination is also known as crossover or reproduction. The new generation of candidate solutions is then evaluated in the next iteration of the algorithm.

**Mutation**
In evolutionary biology, reproduction (or crossover) is what carries the “best genes” from one generation to the next. But, mutation is a necessary part of evolution as it creates “new genes” which improve the overall gene pool. It is also what keeps the GA from settling in a non-optimum valley.

**Termination**
Usually, the algorithm terminates when either a maximum number of generations has been produced, or a satisfactory fitness level has been reached for the population. For ML, termination generally occurs after a maximum number of generations, since anything less than 100% is unsatisfactory.

## Pros / Cons
**Optimum Solutions**
In 1992, John Holland showed that Genetic Algorithms converge to an optimization plateau. GAs work surprising well in a large variety of optimization problems, not just ML feature selection.

**Strengths**
- Easy to explain
- It makes no assumptions about problem space
- A fast search technique
- Produces “close” to optimal results in a “reasonable” amount of time
- Suitable for parallel processing
- Fitness of each “individual” can be calculated in parallel with the other “individuals” of a generation
- Fairly simple to develop

**Weaknesses**
- None (?)
- Population considered for the evolution should be moderate or suitable for problems (normally 20-30 or 50-100), Johnson says "Good advice, but not really a weakness"
- Crossover rate should be 80%-95%, Johnson "Once again, good advice but not a weakness"
- Mutation rate should be low (i.e., 0.5%-1%),  Johnson "This is design advice, not a weakness. My research showed a mutation rate of 50% worked quite well. Not sure what the logic is behind this since you always keep the best of the previous generation, so the more mutations, the more likely you are of not getting stuck in a sub-optimal 'valley'."

# References
- [[Dimensionality Reduction]]