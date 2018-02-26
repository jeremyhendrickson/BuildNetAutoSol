# IpSpace - Building Network Automation Solutions 

## LAB
The [LAB Directory](LAB) contains my Vagrantfile and topology for my Lab.  The Lab consists of an Ubuntu server running Ansible, 4 Juniper vSRX hosts, and a lightweight Ubuntu server connected to the network as a host.

## Exercise 1 - Connect Ansible to LAB
The goal of this [exercise](Exercise1) is to verify Ansible can connect to the LAB and complete a task. I chose to gather facts as the the initial proof of life for Ansible connectivity to my LAB topology. I then used an existing Ansible Example to generate a Network Graph from LLDP neighbor relationships.



