## Build a Network Automation LAB

I built a virtual lab with Juniper VSRX, based upon Topology and Vagrant found at [JNPRAutomate/vagrant-junos](https://github.com/JNPRAutomate/vagrant-junos).  I have also included the Ansible [install script](https://github.com/ipspace/NetOpsWorkshop/tree/master/install) created by Ivan with IpSpace.net.  The script should be run after the Ansible VM is up for the first time.

I have built a development environment on my laptop using Vagrant to spin up the topology below.  I am running Ubuntu/Trusty inside VirtualBox as my Ansible host.  I am not yet ready to commit to running Ansible locally on Mac OS X.

!!!!!
Need proof of life for Ansible
!!!!!

#### Topology
```
                      +-------------+
                      |             |
                      | ansible-srv |
                      |             |
                      +-------------+
                             |
                             |
                             |management 
                             |
                             |
  -------------------------------------------------------
  |       |                  |                  |       |
  |       |                  |                  |       |
  |       |                  |                  |       |
  |       |                  |                  |       |
  |   +-------+          +-------+          +-------+   |
  |   |       |1-3    1-3|       |3-4    3-4|       |   |
  |   | vsrx1 |----------| vsrx3 |----------| vsrx4 |   |
  |   |       |          |       |          |       |   |
  |   +-------+          +-------+          +-------+   |
  |       | 1-2           2-3|                  |4-1    |
  |       |                  |                  |       |
  |       |                  |                  |       |
  |       |                  |                  |       |
  |       | 1-2              |                  |4-1    |
  |   +-------+              |              +-------+   |
  |   |       |2-3           |              |       |   |
  ----| vsrx2 |---------------              | srv1  |---- 
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

Device | Interface | Management IP
---|---|---
ansible-srv | eth1 | 10.100.1.10/24
ansible-srv | eth1:1 | 10.100.2.10/24
ansible-srv | eth1:2 | 10.100.3.10/24
ansible-srv | eth1:3 | 10.100.4.10/24
ansible-srv | eth1:4 | 10.100.5.10/24
vsrx1 | ge-0/0/3 | 10.100.1.2/24
vsrx2 | ge-0/0/3 | 10.100.2.2/24
vsrx3 | ge-0/0/3 | 10.100.3.2/24
vsrx4 | ge-0/0/3 | 10.100.4.2/24
srv1 | eth1 | 10.100.5.2/24
