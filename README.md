# Ubuntu-Server
Code to run on freshly checked out Ubuntu 18.04 Virtual Machine.

## Requirements
- Ansible 2.8.1+

## Usage
1. [Installing external dependencies](#installing-external-dependencies) to update your shared roles.

2. [Updating the stack](#updating-the-stack) (optional, but required for `production` deployments).

## Installing External Dependencies
```bash
ansible-galaxy install -r roles/requirements.yaml -p ./roles --force
```

## Updating the Stack
```bash
ansible-playbook deploy.yaml -i inventories/dev/hosts --vault-id ~/.tokens/vault.txt
```
