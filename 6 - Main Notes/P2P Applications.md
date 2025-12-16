
2025-12-07

Tags: [[3b - Classes/Networking]] [[Networking]]
# P2P Applications
P2P architecture assumes no always on central server that is able to serve as the head/distributor, instead peers request service from other peers and provide service in return. Since the system is composed of arbitrary end nodes the system self scales, any node added also adds capacity to the system.

## Bit Torrent
Over bit torrent files are divided into chunks and sent between peers. When a peer initially joins it has no chunks, but as it stays in the network it will accumulate chunks that it can then distribute to other nodes. Once the peer has the entire file they can choose to stay and continue distributing the file or selfishly leave.

# References

