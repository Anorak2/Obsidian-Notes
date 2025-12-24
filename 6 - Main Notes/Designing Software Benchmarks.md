
2025-12-17

Tags: [[Performance Measurement & Reliability]]
# Designing Software Benchmarks

What is a benchmark? One definition is a "Standard tool for the **competitive** evaluation and comparison of competing systems or components according to speciﬁc characteristics, such as performance, dependability, or security" (1). Most of this sheet will be heavily based on that paper, what can I say the authors did a good job.

## Three General Categories:
#### Speciﬁcation Based:
Speciﬁcation-based benchmarks describe functions that must be achieved, required input parameters and expected outcomes. The implementation to achieve the speciﬁcation is left to the individual running the benchmark. Speciﬁcation-based benchmarks begin with a deﬁnition of a business problem to be simulated by the benchmark. The key criteria for this deﬁnition are the relevance topics discussed in section 3 and novelty. Speciﬁcation-based benchmarks have the advantage of allowing innovative software to address the business problem of the benchmark by proving the speciﬁed requirements of the new implementation. On the other hand, speciﬁcation-based benchmarks require substantial development prior to running the benchmark, and may have challenges proving that all the requirements of the benchmark are met.

Pros:
- Room for individual Innovation
Cons:
- Requires the user to produce an implementation
- May be difficult to prove that requirements are correct
#### Kit Based:
Kit-based benchmarks provide the implementation as a required part of oﬃcial benchmark execution. Any functional diﬀerences between products that are allowed to be used for the benchmark must be resolved ahead of time and the individual running the benchmark is typically not allowed to alter the execution path of the benchmark.

Pros:
- Easy to run
Cons:
- No room for flexibility
#### Hybrid Approach
A hybrid of these may be necessary if the majority of the benchmark can be provided in a kit, but there is a desire to allow some functions to be implemented at the discretion of the individual running the benchmark.

## Properties
- Relevance, how closely the benchmark behavior correlates to behaviors that are of interest to consumers of the results. Many benchmarks require scalability, hence multi-threading / multi-process, in order to actually be relevant to servers .
- Fairness, allowing diﬀerent test conﬁgurations to compete on their merits without artiﬁcial limitations. This is relevant since due to the arbitrary nature of benchmarks artificial limitations will often need to be placed in order to keep things fair.
- Veriﬁability, proving that the benchmark result was accurate
- Usability, making it easy for users to run the benchmarks in their test environments

# References
1. https://dl.acm.org/doi/epdf/10.1145/2668930.2688819

[[Software Metrics]]