
2025-04-22

Tags: [[Security]] [[Applied Cybersecurity]]
# Logging
We need to log record to store entries for successful and/or failed:
- User logins and logouts
- Creation of user accounts
- Execution of certain commands like sudo
- file access 
- starting and turning off the system or different system statuses 

Though personally I don't think we really need to log users unless it is some sort of secured or semi-secured system since otherwise we are overreaching a bit. But logs provide a mechanism for analyzing the system's security state. It allows us to determine if a requested action will put the system in an insecure state, and determine the events that lead towards that insecure state.

**Syslog Standard**
This is a protocol for computer message logging that is generally based on UDP. Using this standard allows separation between the generating entity from the storing and analysis entity.

**Protecting log and Audit Data**
The bare minimum is to enable sensible logging, set proper permissions on log files, and make log file append only.  To make the process acceptable we need to encrypt log files so that they can't be altered without the proper key, that way if an attacker removes the logs then we know something is up. 

We also should use a separate log server so that the attacker needs to breach yet another computer if they want access. All we need to do is configure the hosts to send their logs to the dedicated server. This approach also has the benefits of centralized logs which makes analysis easier. We can also transfer logs to a write-once media (which is a slow process) but this means it can't possibly be modified. Think of a printer for example.
# References

