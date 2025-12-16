
2025-04-29

Tags: [[Security]] [[Networking]] [[Software Security Evaluation]]
# Firewalls
We use firewalls for perimeter control, firewalls let us secure hosts by limiting the access other people have to our machine by filtering or denying certain content. The main types are Host-based firewalls and network based firewalls, and both of those can either be a packet filter based firewall or a gateway firewalls.

How do we let in the return packets? This is an issue, and its solved with dynamic packet filtering. This means dynamically inserting a new filtering rule to let in return traffic, or the firewall acts as a transparent proxy between the two communication parties.

# References

