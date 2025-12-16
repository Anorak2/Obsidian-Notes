Status:

Tags: [[Databases]]
# Good DB design

1. Each tuple should only represent one entity/thing or relationship entity. We do this because it prevents anomalies
2. Our schema shouldn't have **any** insertion, deletion, or update anomalies
3. Relations should be designed so that their tuples have as few null values as possible, if there is a frequently null column break it out
4. **AVOID** generating unnecessary tuples
5. Tuples should be designed in order to fulfill the lossless join condition

Beyond this it is very important to use [[Normalization|Normal Forms]] as they are a formal process to make a schema more resilient

# References
[[Normalization]]

[[CAP Theorem]]