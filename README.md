# base-ansible
Code to run on freshly checked out VM's in our cluster. This is the first ansible-playbook that should be executed on an Ubuntu VM checked out from Verde.

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
