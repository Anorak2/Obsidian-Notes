
2025-04-24

Tags: [[Security]] [[Software Security Evaluation]]
# Intrusion Detection Systems
There are many different types of detection systems including:
- Network Intrusion Detection System
- Network Node Intrusion Detection System
- Host Intrusion Detection System
- Protocol-Based Intrusion Detection System (HTTPS and HTTP)
- Application Protocol-Based Intrusion Detection System

There are also different types of ways to detect vulnerabilities
- Signature-Based Intrusion Detection
- Anomaly-Based Intrusion Detection
- Hybrid Intrusion Detection

## Snort
Snort can be considered the industry standard IDS and it can do real time network trafficking, protocol analysis, content matching, OS fingerprinting, and it is compatible with any OS.

**Packet Sniffing**
Snort can serve as a network sniffer that captures all traffic on the local interface, and it can function as a logger to debug network traffic. It can also use IDS/IPS to scan each packet in real time for suspicious activity or potentially malicious payloads. 

**Alerts and Rules**
Snort can generate alerts for any unusual packets discovered in network traffic, based on the rules configured. Doing this can help identify network threats or other risks that could lead to vulnerabilities being exploited. There is also a whole rule language to make it extendable/personal.

**Attack Detection**
Due to the snort rule language and it's compatibility with all OSes, Snort is able to detect any network based attack as long as there is a rule associated with the attack behavior.
# References

[[Denial of Service Attacks and DDoS Attacks]]
