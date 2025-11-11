
2025-10-31

Tags: [[Virtual Machines]] [[Programming]]
# Debugging Dnsmasq
https://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/virsh-failed-to-start-network-default-4175672429/


test  ```dnsmasq.service```, ex:
- Check the `GUFW` status log for existing processes
- ```systemctl status dnsmasq.service```
- ```systemctl start dnsmasq.service```
- if those are failing run a ```sudo pkill dnsmasq```
- if problems persist see next

cd to ```/etc/libvirt/qemu/networks``` and look for a ```default.xml```
if it exists go do:
- ```virsh net-define ./default.xml``` assuming  you are in previous directory
- `virsh net-start default` to run the network

if these steps don't work then you are in uncharted territory o7

# References



