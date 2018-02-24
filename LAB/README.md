## Build a Network Automation LAB

I built a virtual lab with Juniper VSRX, based upon Topology and Vagrant found at [JNPRAutomate/vagrant-junos](https://github.com/JNPRAutomate/vagrant-junos).

I have built a development system on my laptop using Vagrant to spin up the topology below.  I am running Ubuntu/Trusty inside VirtualBox as my Ansible host.  I am not yet ready to commit to running Ansible locally on Mac OS X.

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
ansible-srv | eth1 | 10.100.0.10/24
vsrx1 | ge-0/0/3 | 10.100.0.1/24
vsrx1 | ge-0/0/3 | 10.100.0.2/24
vsrx1 | ge-0/0/3 | 10.100.0.3/24
vsrx1 | ge-0/0/3 | 10.100.0.4/24
srv1 | eth2 | 10.100.0.5/24
ansible-srv | eth1 | 10.100.0.10
