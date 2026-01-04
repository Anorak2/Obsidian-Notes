
2025-02-25

Tags: [[Security]] [[Software Security Evaluation]] [[Tools]]
# Password Cracking
We all know what passwords are, they are a way to authenticate a user to prove identity to either a system or a service. The problem is that passwords have a finite number of possibilities and with weak passwords especially they are easy to guess. The main problem comes from a trade off where the more secure a password is the harder it is for a human to remember, and we should be using unique passwords for everything but that also make it harder for humans to remember. 

**Brute Force**
This is the simplest version, and also the longest. However when we brute force a password, if we wait long enough, we are guaranteed to crack it. We can guarantee this because we iterate through the entire sample space and try every single possible password until we hit the right one. The downside is that this is absurdly difficult and it scales exponentially with length. For example with uppercase, lowercase, and numbers only and a length of 8 characters there are $62^8$ possible combinations or about $2 \cdot 10^{14}$ possible passwords. 

**Dictionary Attacks**
This is a more efficient version of cracking but at the cost of losing the guarantee that we will crack the password. Dictionary attacks work by having an enormous list of passwords that people have actually used before. This means that if the password is in the dictionary we **will** crack it, but otherwise we won't be able to.

**Hybrid Password Attacks**
This version works off of a dictionary but we don't just give up after trying one word, we try a few other common iterations. Examples include ```password```, ```pa$$word```, ```password!!``` etc. This lets us get the best of both worlds since it is much more efficient than brute force while giving us a wider range of passwords we can crack.

**Rainbow Tables**
These are pre-computed lookup tables for recovering plaintext passwords from a password hash. This has a time-space trade-off since the CPU has much less work to do but now we use more storage.
# References
[[Types of Passwords attacks and Defenses]]

[[Hashing]]

[[Using John the Ripper]]