[![Build Status](https://drone-ci.hopto.org/api/badges/Diesel-Net/swarm/status.svg)](https://drone-ci.hopto.org/Diesel-Net/swarm)


# swarm
Docker Swarm Mode on Ubuntu 18.04 Virtual Machines.

## Requirements
- Ansible 2.10+

## Installing Dependencies
```bash
ansible-galaxy install -r roles/requirements.yaml -p ./roles --force
```

## Configure SSH for _automation_ user
This first playbook only needs to be ran once, when connecting to host for the first time. The second one will update the stack.

```bash
ansible-playbook configure_ssh.yaml -i inventories/dev/hosts --vault-id ~/.tokens/master_id
```

## Provision VMs
```bash
ansible-playbook deploy.yaml -i inventories/dev/hosts --vault-id ~/.tokens/master_id
```
