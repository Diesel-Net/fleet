[![Build Status](https://drone-ci.hopto.org/api/badges/Diesel-Net/swarm-bootstrapper/status.svg)](https://drone-ci.hopto.org/Diesel-Net/swarm-bootstrapper)

# swarm-bootstrapper
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines. This is the first piece of code that should be executed against a fresh host on the `diesel.net` domain

## Requirements
- Ansible 2.10+

## Installing Dependencies
```bash
ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
```

## Configure SSH for _automation_ user
This first playbook only needs to be ran once, when connecting to host for the first time. The second one will update the stack.

```bash
ansible-playbook .ansible/configure_ssh.yaml -i .ansible/inventory/dev/hosts --vault-id ~/.tokens/master_id
```

## Configure Swarm
Right now each environment is defined as an independent Virtual Machine (single-node swarm leaders)
```bash
ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/dev/hosts --vault-id ~/.tokens/master_id
```
