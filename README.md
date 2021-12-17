[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/swarm-bootstrapper/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/swarm-bootstrapper)

# swarm-bootstrapper
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines. This is the first piece of code that should be executed against a fresh host on the `diesel.net` domain

## Toolchain

- ansible 4.7.0
- ansible-core 2.11.6
- python 3.9.7

## Installing Dependencies

Install necessary ansible roles.
```bash
ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
```

Install `dns-python` required for [`community.general.dig`](https://docs.ansible.com/ansible/latest/collections/community/general/dig_lookup.html)
```bash
pip3 install -r .ansible/files/requirements.txt
```

## Configure Swarm

You will need to have the ansible-vault password file configured on your machine. Please read the relevant [ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/vault.html#setting-a-default-password-source) for more information.

Bootstrap the `development` fleet.
```bash
ansible-playbook .ansible/deploy.yaml -i .ansible/inventory/development
```
