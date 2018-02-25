# Exercise 1 - Connect Ansible to LAB
The goal of this exercise is to verify Ansible can connect to the [LAB](../LAB) and complete a task.

## Gather Facts
Run an initial ansible playbook to gather facts about the hosts.

```
vagrant@ansible-srv:~/devops/BuildNetAutoSol/Exercise1$ ansible-playbook -i inventory.inv facts.pb.yaml
Username: ansible
password:

PLAY [Get facts] **************************************************************************************************************************************************************

TASK [Get junos facts] ********************************************************************************************************************************************************
ok: [10.100.2.2]
ok: [10.100.1.2]
ok: [10.100.3.2]
ok: [10.100.4.2]

TASK [Print facts] ************************************************************************************************************************************************************
ok: [10.100.1.2] => {
    "junos": {
        "HOME": "/var/home/ansible",
        "RE0": {
            "last_reboot_reason": "Router rebooted after a normal shutdown.",
            "mastership_state": "master",
            "model": "FIREFLY-PERIMETER RE",
            "status": "Testing",
            "up_time": "4 hours, 4 minutes, 28 seconds"
        },
        "RE1": null,
        "RE_hw_mi": false,
        "current_re": [
            "master",
            "node",
            "fwdd",
            "member",
            "pfem",
            "backup",
            "re0",
            "fpc0.pic0"
        ],
        "domain": null,
        "fqdn": "vsrx1",
        "has_2RE": false,
        "hostname": "vsrx1",
        "hostname_info": {
            "re0": "vsrx1"
        },
        "ifd_style": "CLASSIC",
        "junos_info": {
            "re0": {
                "object": {
                    "build": 4,
                    "major": [
                        12,
                        1
                    ],
                    "minor": [
                        47,
                        "D",
                        15
                    ],
                    "type": "X"
                },
                "text": "12.1X47-D15.4"
            }
        },
        "master": "RE0",
        "master_state": true,
        "model": "FIREFLY-PERIMETER",
        "model_info": {
            "re0": "FIREFLY-PERIMETER"
        },
        "personality": "SRX_BRANCH",
        "re_info": {
            "default": {
                "0": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                },
                "default": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                }
            }
        },
        "re_master": {
            "default": "0"
        },
        "re_name": "re0",
        "serialnumber": "d2f157e7ee73",
        "srx_cluster": false,
        "srx_cluster_id": null,
        "srx_cluster_redundancy_group": null,
        "switch_style": "BRIDGE_DOMAIN",
        "vc_capable": false,
        "vc_fabric": null,
        "vc_master": null,
        "vc_mode": null,
        "version": "12.1X47-D15.4",
        "version_RE0": "12.1X47-D15.4",
        "version_RE1": null,
        "version_info": {
            "build": 4,
            "major": [
                12,
                1
            ],
            "minor": [
                47,
                "D",
                15
            ],
            "type": "X"
        },
        "virtual": true
    }
}
ok: [10.100.3.2] => {
    "junos": {
        "HOME": "/var/home/ansible",
        "RE0": {
            "last_reboot_reason": "Router rebooted after a normal shutdown.",
            "mastership_state": "master",
            "model": "FIREFLY-PERIMETER RE",
            "status": "Testing",
            "up_time": "9 minutes, 1 second"
        },
        "RE1": null,
        "RE_hw_mi": false,
        "current_re": [
            "master",
            "node",
            "fwdd",
            "member",
            "pfem",
            "backup",
            "re0",
            "fpc0.pic0"
        ],
        "domain": null,
        "fqdn": "vsrx3",
        "has_2RE": false,
        "hostname": "vsrx3",
        "hostname_info": {
            "re0": "vsrx3"
        },
        "ifd_style": "CLASSIC",
        "junos_info": {
            "re0": {
                "object": {
                    "build": 4,
                    "major": [
                        12,
                        1
                    ],
                    "minor": [
                        47,
                        "D",
                        15
                    ],
                    "type": "X"
                },
                "text": "12.1X47-D15.4"
            }
        },
        "master": "RE0",
        "master_state": true,
        "model": "FIREFLY-PERIMETER",
        "model_info": {
            "re0": "FIREFLY-PERIMETER"
        },
        "personality": "SRX_BRANCH",
        "re_info": {
            "default": {
                "0": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                },
                "default": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                }
            }
        },
        "re_master": {
            "default": "0"
        },
        "re_name": "re0",
        "serialnumber": "4103884e45fc",
        "srx_cluster": false,
        "srx_cluster_id": null,
        "srx_cluster_redundancy_group": null,
        "switch_style": "BRIDGE_DOMAIN",
        "vc_capable": false,
        "vc_fabric": null,
        "vc_master": null,
        "vc_mode": null,
        "version": "12.1X47-D15.4",
        "version_RE0": "12.1X47-D15.4",
        "version_RE1": null,
        "version_info": {
            "build": 4,
            "major": [
                12,
                1
            ],
            "minor": [
                47,
                "D",
                15
            ],
            "type": "X"
        },
        "virtual": true
    }
}
ok: [10.100.4.2] => {
    "junos": {
        "HOME": "/var/home/ansible",
        "RE0": {
            "last_reboot_reason": "Router rebooted after a normal shutdown.",
            "mastership_state": "master",
            "model": "FIREFLY-PERIMETER RE",
            "status": "Testing",
            "up_time": "7 minutes, 16 seconds"
        },
        "RE1": null,
        "RE_hw_mi": false,
        "current_re": [
            "master",
            "node",
            "fwdd",
            "member",
            "pfem",
            "backup",
            "re0",
            "fpc0.pic0"
        ],
        "domain": null,
        "fqdn": "vsrx4",
        "has_2RE": false,
        "hostname": "vsrx4",
        "hostname_info": {
            "re0": "vsrx4"
        },
        "ifd_style": "CLASSIC",
        "junos_info": {
            "re0": {
                "object": {
                    "build": 4,
                    "major": [
                        12,
                        1
                    ],
                    "minor": [
                        47,
                        "D",
                        15
                    ],
                    "type": "X"
                },
                "text": "12.1X47-D15.4"
            }
        },
        "master": "RE0",
        "master_state": true,
        "model": "FIREFLY-PERIMETER",
        "model_info": {
            "re0": "FIREFLY-PERIMETER"
        },
        "personality": "SRX_BRANCH",
        "re_info": {
            "default": {
                "0": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                },
                "default": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                }
            }
        },
        "re_master": {
            "default": "0"
        },
        "re_name": "re0",
        "serialnumber": "1829a2bb88fc",
        "srx_cluster": false,
        "srx_cluster_id": null,
        "srx_cluster_redundancy_group": null,
        "switch_style": "BRIDGE_DOMAIN",
        "vc_capable": false,
        "vc_fabric": null,
        "vc_master": null,
        "vc_mode": null,
        "version": "12.1X47-D15.4",
        "version_RE0": "12.1X47-D15.4",
        "version_RE1": null,
        "version_info": {
            "build": 4,
            "major": [
                12,
                1
            ],
            "minor": [
                47,
                "D",
                15
            ],
            "type": "X"
        },
        "virtual": true
    }
}
ok: [10.100.2.2] => {
    "junos": {
        "HOME": "/var/home/ansible",
        "RE0": {
            "last_reboot_reason": "Router rebooted after a normal shutdown.",
            "mastership_state": "master",
            "model": "FIREFLY-PERIMETER RE",
            "status": "Testing",
            "up_time": "4 hours, 2 minutes, 58 seconds"
        },
        "RE1": null,
        "RE_hw_mi": false,
        "current_re": [
            "master",
            "node",
            "fwdd",
            "member",
            "pfem",
            "backup",
            "re0",
            "fpc0.pic0"
        ],
        "domain": null,
        "fqdn": "vsrx2",
        "has_2RE": false,
        "hostname": "vsrx2",
        "hostname_info": {
            "re0": "vsrx2"
        },
        "ifd_style": "CLASSIC",
        "junos_info": {
            "re0": {
                "object": {
                    "build": 4,
                    "major": [
                        12,
                        1
                    ],
                    "minor": [
                        47,
                        "D",
                        15
                    ],
                    "type": "X"
                },
                "text": "12.1X47-D15.4"
            }
        },
        "master": "RE0",
        "master_state": true,
        "model": "FIREFLY-PERIMETER",
        "model_info": {
            "re0": "FIREFLY-PERIMETER"
        },
        "personality": "SRX_BRANCH",
        "re_info": {
            "default": {
                "0": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                },
                "default": {
                    "last_reboot_reason": "Router rebooted after a normal shutdown.",
                    "mastership_state": "master",
                    "model": "FIREFLY-PERIMETER RE",
                    "status": "Testing"
                }
            }
        },
        "re_master": {
            "default": "0"
        },
        "re_name": "re0",
        "serialnumber": "8d4cc8a5174d",
        "srx_cluster": false,
        "srx_cluster_id": null,
        "srx_cluster_redundancy_group": null,
        "switch_style": "BRIDGE_DOMAIN",
        "vc_capable": false,
        "vc_fabric": null,
        "vc_master": null,
        "vc_mode": null,
        "version": "12.1X47-D15.4",
        "version_RE0": "12.1X47-D15.4",
        "version_RE1": null,
        "version_info": {
            "build": 4,
            "major": [
                12,
                1
            ],
            "minor": [
                47,
                "D",
                15
            ],
            "type": "X"
        },
        "virtual": true
    }
}

PLAY RECAP ********************************************************************************************************************************************************************
10.100.1.2                 : ok=2    changed=0    unreachable=0    failed=0
10.100.2.2                 : ok=2    changed=0    unreachable=0    failed=0
10.100.3.2                 : ok=2    changed=0    unreachable=0    failed=0
10.100.4.2                 : ok=2    changed=0    unreachable=0    failed=0

```
