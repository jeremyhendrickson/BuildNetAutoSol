# Exercise 1 - Connect Ansible to LAB
The goal of this exercise is to verify Ansible can connect to the [LAB](../LAB) and complete a task.

## Gather Facts
Run an initial ansible playbook to gather facts about the hosts.

```
ansible-playbook -i inventory.inv facts.pb.yaml
Username: ansible
password:

PLAY [Get facts] **************************************************************************************************************************************************************

TASK [Get junos facts] ********************************************************************************************************************************************************
ok: [10.100.2.2]
ok: [10.100.1.2]
ok: [10.100.3.2]
ok: [10.100.4.2]

TASK [Print facts] ************************************************************************************************************************************************************
...
Output omitted for berevity.  
...
PLAY RECAP ********************************************************************************************************************************************************************
10.100.1.2                 : ok=2    changed=0    unreachable=0    failed=0
10.100.2.2                 : ok=2    changed=0    unreachable=0    failed=0
10.100.3.2                 : ok=2    changed=0    unreachable=0    failed=0
10.100.4.2                 : ok=2    changed=0    unreachable=0    failed=0

```
Output omitted for berevity.  See [gather-facts.txt](gather-facts.txt)

