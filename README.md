[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/fleet/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/fleet)

# fleet
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines. This is the first piece of code that should be executed against a fresh host on the `diesel.net` domain

## Toolchain
- ansible-community 7.2.0

## Installing Dependencies

Install necessary ansible roles.
```bash
ansible-galaxy install -r .ansible/roles/requirements.yaml -p .ansible/roles --force
```

Install [`dnspython`](https://www.dnspython.org/) required for [`community.general.dig`](https://docs.ansible.com/ansible/latest/collections/community/general/dig_lookup.html)
```bash
pip3 install -r .ansible/files/requirements.txt
```

## Bootstrap Docker Swarm hosts

You will need to have the ansible-vault password file configured on your machine. Please read the relevant [ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/vault.html#setting-a-default-password-source) for more information. It is typically a good idea to test changes against one or a few hosts in order to iron out any kinks.


#### Scan for SSH host keys and then bootstrap the hosts but limited to just the `dev` host group:
```bash
ansible-playbook .ansible/scan_hosts.yaml --inventory .ansible/inventories/proxmox.yaml --limit dev.diesel.net
ansible-playbook .ansible/bootstrap.yaml --inventory .ansible/inventories/proxmox.yaml --limit dev.diesel.net
```
