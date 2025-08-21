
2025-02-06

Tags: [[Basic Reconnaissance]] [[Applied Cybersecurity]] [[Security]] [[tool]
# Network Scanning
We scan hosts connected to a network to determine live hosts, network topology, OS on each host, ports on each host, and vulnerabilities.

## Nmap
ping sweeps
- ```nmap -sP target_ip```

**TCP connect** with a three way handshake
```nmap -sT taget_ip```
This version does a complete scan and the main benefit is that it can't cause any problems on the host, but it's extremely easy to detect.

**UDP**
```nmap -sU target_ip```
There is no handshake and no sequence number for this one. We instead send a UDP packet to a target port, if an ICMP Port Unreachable is returned then the port is closed (or filtered). If no response is returned then we assume the port is open. The downsides are that it's easy to detect, unreliable, and potentially slow when the messages are rate limited

**TCP SYN mode**
```nmap -sS target_ip```
This is like the TCP connect but instead we don't complete the handshake, this method is slightly stealthy.

**TCP FIN mode**
```nmap -sF target_ip```
This version sends a TCP FIN to a target port, which is a violation of the TCP specification. If we get an RST back from the server then the port is closed, and if no response is sent then the port may be open. This will have different effects depending on the system, since for example Microsoft doesn't follow the Request For Comment (RFC).

**Xmas Tree mode**
```nmap -sX target_ip```
We send a TCP segment to a target port with ```FIN```, ```URG```, and ```PSH``` code bits set, which is a violation of the TCP specification. If we get back an ```RST``` then the port is closed, and if no response is returned then the port may be open. This mode is also kind of stealthy, and like the FIN mode Microsoft still doesn't follow RFC.

**Null Mode**
```nmap -sN target_ip```
We send a TCP segment to a target port with no code bits set, which again violates TCP. This again won't work on Microsoft systems.

**TCP ACK mode**
```nmap -sA target_ip```
Sends a TCP ACK to a target port (violating TCP specification). If an RST is returned then the packet made it through the filter and the port is unfiltered. If we don't get a response or ICMP port unreachable then it was blocked by a firewall. This mode can be used to determine what rules a packet filter applies.

**Other useful options**
- We can specify selected ports with the -p flag.
- We can set the source port that the package originated from (such as 80 or 25) so that hopefully the packets won't be blocked
- Obscure the source of scans by sending decoy packets with a decoy source address
- -A enables OS detection
- -v increases verbosity

## Open VAS
https://github.com/greenbone/openvas-scanner
# References
[[Basic Reconnaissance]]
