
```
ansible-playbook run_dllama_qwen.yml -e "run_type=long"
```
```
ansible-playbook run_dllama_qwen.yml -e "run_type=leaderboard"
```
```
ansible-playbook run_dllama.yml -e "run_type=leaderboard"
```
## Orange PI's
**Turning Them ON**
Use the good usb serial converter, don't daisy chain wires or it fucking breaks. If you're trying to screen in then unplug the ethernet first, and probably hdmi for good measure.

**Providing Power to the Orange Pi's**
viewing the pin stack so that it's close to you, on farthest right side there is one empty pin, then purple, then white. Purple if 5v and white is ground

```[   ...     ][   white(GRND)     ][     purple(5V)     ][       empty       ]```

 **Pi5**
http://www.orangepi.org/orangepiwiki/index.php/Orange_Pi_5
- `sudo screen /dev/tty0 1500000`

 **Getting into Pi5**
- `screen /dev/ttyUSB0 1500000`
- `ssh orangepi@ip.addr`

## Network Planning
Ethernet connections:
if you view the ethernet ports from the front (where you plug it in) then WAN is on the right and LAN is on the left

| name      | value                   |
| --------- | ----------------------- |
| subnet    | 172.17.1.0/24           |
| da router | 172.171.1.1             |
| dns       | 8.8.8.8 8.8.4.4         |
| dhcp pool | 172.171.100 172.171.200 |
| wan       | enP3p49s0               |
| lan       | enP4p65s0               |

Find the orangepi with `nmap -sN -p 22 172.16.50.*' 
ARP scan
`sudo arp-scan --interface= -l`

The DHCP server 
`isc-dhcp-server.service`

## Ansible
The ansible configuration files are on the head orangepi 5+, the top one on the stack. The password to the locked vault is `orangepi`

```ansible-playbook --ask-vault-pass -i inventory.ini package.yml```


Looking back on the issues we ran across I threw a list together to hopefully make future setup easier. This way the next group will have an easier time, if there's anything in here you don't see mentioned feel free to let me know and I can add it

## General Playbook
1. Make sure every node has a solid image, network booting would be nice for reliability. Could also make a custom image to make the setup easier and tweaks to improve performance instead of just base image.
2. The network is very important and it needs to be reliable otherwise nothing works. We had issues when testing with DHCP/dynamic IPs and MAC address randomization that slowed us down a lot
3. Bring up a small part of the cluster first, and early. It'll make it way easier to pivot early
4. QOL apps and a good understanding of tools like Spack, Slurm, MPI, ansible, NFS, SSH, SCP, Linux CLI, text editors makes a really big difference in the competition day crunch. Grafana could also be something to look into for analytics
5. Install and configure a proper scheduler i.e: Slurm ahead of time and smoke test connectivity between devices with it.
6. Use a single ansible playbook that has every apps dependencies and develop it ahead of time. Double check versioning between nodes to ensure compatibility between them.
7. Run the contest applications across the nodes as soon as the infrastructure is set up
8. Communication is really important since you don't want to solve the same problem 3 times
9. Understand the cluster well going in, one example is to stress test the nodes to find maximum power consumption
10. For security basic things like a head node with multiple user accounts and a simple firewall like ufw go a long way, also ssh keys from the head node <-> every other node is very handy while still being secure. Also better passwords is a super simple way to improve security