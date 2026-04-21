
2025-04-24

Tags: [[Software Security]] [[Networking and Network Security]]
# Intrusion Detection Systems
Fundamentally intrusion is an event that violates the security policy of the system: Physical access, Software vulnerability exploitation, Virus, malware, Social engineering, Password guessing, Network traffic interception, other. Intrusion detection is the process of monitoring and analyzing system events to identify such intrusions. IDS automates the process and uses an audit trail for postmortems.

## Network Intrusion Detection
![[Pasted image 20260326103631.png]]
Intrusion prevention systems detect malicious actions and automatically block them in real-time, rather than just an IDS that only detects. There are a number of remediation operations available, such as logging the event, dropping the connection, resetting the connection, and changing the configuration of router/firewall to block future connections.

**Deep Packet Inspection**
Deep packet inspection looks into the internals of a packet to look for some application/content context. This could be inspecting HTTP for URLs that point to malicious websites, and it can have serious privacy issues if done on a large scale such as by Comcast.

**Signature Based**
Also known as misuse-based or heuristic detection. It uses pre-defined patterns to detect attacks such as sequences of system calls, patterns of network traffic, etc. You define rules to capture the patterns with options like regular expressions (snort) or cryptographic hash (tripwire) to find match. The rule set must be up-to-date in order to be secure, and it can only detect known attacks with adequate precision. Typically signatures are very specific and can miss variants of known attacks.

Open source tools include Bro, Snort, and Suricata

**Anomaly-Based Intrusion Detection**
Define a profile of “normal” behavior and then flag deviations from the “normal” profile.  This works best for “small”, well-defined systems. Using a zero shot algorithm it can classify never-seen-before packets.
- {good, 80, “GET”, “/”, “Firefox”}
- {bad, 80, “POST”, “/php-shell.php?cmd=’rm -rf /’”, “Evil Browser”}

Typically ML techniques are used to build the model, since manual techniques are very hard. This means logging system activities for a while, then train the IDS to recognize normal and abnormal patterns. This comes at the risk of attacker training the IDS to accept his activity as normal. For example daily low-volume port scan may train IDS to accept port scans.

**Hybrid Intrusion Detection**
A mix of the two previous techniques
## Other Types 
There are many different types of detection systems including:
- Network Intrusion Detection System
- Network Node Intrusion Detection System
- Host Intrusion Detection System
- Protocol-Based Intrusion Detection System (HTTPS and HTTP)
- Application Protocol-Based Intrusion Detection System
## Snort
Snort can be considered the industry standard IDS and it can do real time network trafficking, protocol analysis, content matching, OS fingerprinting, and it is compatible with any OS.

**Packet Sniffing**
Snort can serve as a network sniffer that captures all traffic on the local interface, and it can function as a logger to debug network traffic. It can also use IDS/IPS to scan each packet in real time for suspicious activity or potentially malicious payloads. 

**Alerts and Rules**
Snort can generate alerts for any unusual packets discovered in network traffic, based on the rules configured. Doing this can help identify network threats or other risks that could lead to vulnerabilities being exploited. There is also a whole rule language to make it extendable/personal.

**Attack Detection**
Due to the snort rule language and it's compatibility with all OSes, Snort is able to detect any network based attack as long as there is a rule associated with the attack behavior.

**Examples**
Format
```Javascript
// The rule header
<action> <protocol> <src IP/mask> <port> -> <dest IP/mask> <port> (msg:
<alert message>; content: “search packet for”; …; etc.)
// Rule options
```

String Search
```javascript
alert tcp $EXTERNAL_NET any -> $SQL_SERVERS 3306 (msg:"MYSQL root login
attempt"; flow:to_server,established; content:"|0A 00 00 01 85 04 00 00 80|root|00|";
classtype:protocol-command-decode; sid:1775; rev:2;)
```

Stateful inspection + regex matching
```javascript
alert tcp $EXTERNAL_NET any -> $HOME_NET 10202:10203 (msg:"CA license GCR
overflow attempt"; flow:to_server,established; content:"GCR NETWORK<"; depth:12;
offset:3; nocase; pcre:"/^\S{65}|\S+\s+\S{65}|\S+\s+\S+\s+\S{65}/Ri"; sid:3520;)
```
# References
- [[Denial of Service Attacks and DDoS Attacks]]
