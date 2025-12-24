
2025-12-22

Tags: [[Performance Measurement & Reliability]] 
# Chaos Testing
Chaos testing is the practice of introducing randomized faults into software, designed to simulate real world failures, as a way of testing systems for fault tolerance. This kind of testing is able to hit mechanisms like autoscaling, failover, and redundancy. The main advantages include increased resilience, proactive problem solving, increased confidence in integrity, and enhanced incident response. The downsides for such an approach are the resource costs, potential for disruption, and complexity.

### Chaos Monkey
Chaos monkey is a tool designed by Netflix to test the resiliency of it's AWS deployment and is a case study in chaos testing. Chaos monkey accomplishes it's goal by randomly shutting down virtual machines that are running live services, simulating real world failures.

**Features**
1. Random Failure Injection
2. Fault Tolerance testing
3. Automated testing on a schedule
4. Customizable chaos
5. Cloud-native support

# References
- [[Failover]]