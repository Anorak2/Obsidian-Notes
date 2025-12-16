
2025-04-25

Tags: [[Security]] [[Operating Systems]] [[Software Security Evaluation]]
# Rootkits
What is a root kit? A root kit is malicious software that is designed to run on a target's computer with elevated permissions while staying undetected. 

## Types of Rootkits
**Kernel-mode rootkit**
This is installed with kernel level, root level, permissions on the target. It gets loaded as a module to the kernel which is dynamic and does not require a full kernel recompilation. This is kind of the holy grail because the attacker can do literally whatever they want now, they can use key loggers or do a ransomware attack or just delete everything if they felt like it.

**Application rootkit**
These target specific applications on the machine and they use vulnerabilities in the software as a foothold. This software might open a network port, hide files and folders, or add and hide registry entries for windows systems. Once installed they are able to do things like modify the behavior of software applications, track keystrokes during application usage, and create network connections.

**Other Types:**
- Memory rootkit
- Bootloader rootkit
- Hardware/firmware rootkit

## Prevention and Mitigation
The only things we can really do are kind of just basic cybersecurity things
- detect and block/filter phishing and spam emails
- keep up to date with security patches and antivirus signatures 
- be careful downloading files from untrusted sources

These are only so effective though, and when it comes to a highly sophisticated kernel level root kit there really isn't anything you can do. the way you actually can mitigate a root kit is by reinstalling the OS and re-image the os and hard drive. Using clonezilla won't work for bootloader or firmware level root kits though. 

# References
[[kernel]]
