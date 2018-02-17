## Build a Network Automation LAB
### LAB1 Assignment

I built a physical lab with Juniper and Brocade equipment, as this is the gear that we run in our network.  To keep it simple at this point I have focused on connectivity to the Juniper EX2300 switch stacks in the LAB.  I included the other gear in the LAB topology as I will attempt to build Ansible solutions to them in future labs.

I have built a Vagrant development system on my laptop running Ubuntu/Trusty inside VirtualBox.  I am not yet ready to commit to running Ansible locally on Mac OS X.

!!!!!
Need proof of life for Ansible
!!!!!

#### Topology
```
sw1 ge-0/1/2 <-----> ge-0/1/2 sw2 xe-0/1/3 <-----> xe-0/1/2 sw3
```
#### OOB Interfaces
I plan to use Ansible to manage devices via their OOB or Management VRFs.  That is how I am currently connecting to the EX2300 switches.

Device | Management IP | Interface | Console Port
---|---|---|---
ex2300-sw1 | 192.0.2.15 | vme.0 | 17
ex2300-sw2 | 192.0.2.16 | vme.0 | 18
ex2300-sw3 | 192.0.2.17 | vme.0 | 19

#### VLANS and L3 Interfaces
Device | Layer 3 IP | L3 Interface | Layer 3 VLAN
---|---|---|---
ex2300-sw1 | 10.0.2.254 | irb.101 | 101
ex2300-sw2 | 10.0.2.253 | irb.101 |101
ex2300-sw3 | 10.0.2.252 | irb.101 |101


