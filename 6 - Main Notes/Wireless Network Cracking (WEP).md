
2025-04-10

Tags: [[Security]] [[Applied Cybersecurity]] [[Networking]]
# Wireless Network Cracking (WEP)
## Security
WEP is one of the wireless security protocols like WPA and WPA2, and the acronym stands for Wired Equivalent Privacy. This protocol is a security algorithm for IEEE 802.11 wireless networks. WEP uses the stream cipher R4 for confidentiality and the ```CRC-32``` checksum to verify integrity, however WEP has many flaws and has been deprecated.

![[Pasted image 20250424145951.png]]

One of the biggest issues with WEP security is that because it uses a stream cipher we need to ensure that we never use the same key twice, but the problem is that a 24 bit IV isn't good enough to ensure that on a busy network. This is such a bad problem that there is a 50% chance of a key repeating after 5,000 packets.

## Exploiting
we can exploit this vulnerability and crack the network quite easily using ```aircrack-ng```.

1. Make sure that the wireless card on the attackers system is showing using ifconfig
2. ```aircrack-ng start wlan0``` This will put the wireless interface into monitor mode so that we can monitor and capture wireless frames from other devices
3. ```airodump-ng mon0``` we use the dump command to list all networks we can pick up in the nearby area.
4. ```airodump-ng –w [ESSID] –c [Channel] –bssid [BSSID] mon0```, we tell the card to start listening to all of the traffic on a given wireless network and we can write it to a file using ```airodump-ng mon0 –[file-name]```. We want as many packets as we can possibly get, we want at least 10,000 but we may need more.
5. Now that we have the data captured from the WEP device we can crack the password with ```aircrack-ng [file-name].cap``` 
# References
[[Wireless Network Cracking (WPA & WPA2)]]

[[Stream Ciphers]]

[[Pigeonhole Principle]]
