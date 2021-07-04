[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/swarm-bootstrapper/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/swarm-bootstrapper)

# swarm-bootstrapper
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines. This is the first piece of code that should be executed against a fresh host on the `diesel.net` domain

## Requirements
- Ansible 2.10+

## Installing Dependencies
```bash
ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
```

## Configure Swarm
Right now each environment is defined as an independent Virtual Machine (single-node swarm leaders)
```bash
ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/dev/hosts --vault-id ~/.tokens/master_id
```
