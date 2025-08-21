
2025-01-28

Tags: [[Operating Systems]] [[kernel]]
# Boot Sectors
A boot sector is a very small section of code that tells the BIOS how to load the operating system properly. This code is essentially the first domino in the chain for booting up properly. It can be a couple of different sizes, such as 512 or 4096 bytes and it can come in a couple of different versions such as MBR or GPT.

You do also have to be careful as viruses historically love to target the boot sector, so in response most computers have safeguards against writing to the boot sector. An example is [[Not Petya]] which would attempt to gain admin perms and then attempt to write to the boot sector.
# References
[[Boot Loaders]]


