[![Build Status](https://drone-ci.hopto.org/api/badges/Diesel-Net/swarm/status.svg)](https://drone-ci.hopto.org/Diesel-Net/swarm)


# swarm
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines.

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

## Configure Swarm
Right now each environment is defined as an independent Virtual Machine (single-node swarm leaders)
```bash
ansible-playbook deploy.yaml -i inventories/dev/hosts --vault-id ~/.tokens/master_id
```
