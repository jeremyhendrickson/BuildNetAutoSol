## Build a Network Automation LAB
### LAB1 Assignment

I built a physical lab with Juniper and Brocade equipment, as this is the gear that we run in our network.  To keep it simple at this point I have focused on connectivity to the Juniper EX2300 switch stacks in the LAB.  I included the other gear in the LAB topology as I will attempt to build Ansible solutions to them in future labs.

I have built a Vagrant development system on my laptop running Ubuntu/Trusty inside VirtualBox.  I am not yet ready to commit to running Ansible locally on Mac OS X.

!!!!!
Need proof of life for Ansible
!!!!!

#### Topology
```
+-------+          +-------+          +-------+
|       |1-3    1-3|       |3-4    3-4|       |
| vsrx1 |----------| vsrx3 |----------| vsrx4 |
|       |          |       |          |       |
+-------+          +-------+          +-------+
    | 1-2           2-3|                  |4-1
    |                  |                  |
    |                  |                  |
    |                  |                  |
    | 1-2              |                  |4-1
+-------+              |              +-------+
|       |2-3           |              |       |
| vsrx2 |---------------              | srv1  |
|       |                             |       |
+-------+                             +-------+
```

#### Interfaces

Device | Interface | L3 IP | Device | Interface | L3 IP
---|---|---|---|---|---
vsrx1 | ge-0/0/1 | 10.99.12.1/24 | vsrx2 | ge-0/0/2 | 10.99.12.2/24
vsrx1 | ge-0/0/2 | 10.99.13.1/24 | vsrx3 | ge-0/0/1 | 10.99.13.3/24
vsrx2 | ge-0/0/1 | 10.99.23.2/24 | vsrx3 | ge-0/0/2 | 10.99.23.3/24
vsrx3 | ge-0/0/3 | 10.99.34.3/24 | vsrx4 | ge-0/0/1 | 10.99.34.4/24
vsrx4 | ge-0/0/3 | 10.4.0.1/24 | srv1 | eth1 | 10.4.0.2/24

