[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/fleet/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/fleet)

# fleet
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines. This is the first piece of code that should be executed against a fresh host on the `diesel.net` domain

## Checking-In New Hosts
To add a new host (or set of hosts) create a new local branch name with the pattern `check-in/*`, add the new hosts and their configuration to the inventory, then push. Please delete your `check-in/*` branch after merging.

## Bootstrap fleet
Pushes to `stable` branches will trigger the entire fleet to be bootstrapped.

## Update host packages
You will need the following installed:
>Python 3.11+<br>

1. Create a Python Virtual Environment (venv) and activate it.
   ```zsh
   python3 -m venv venv
   ```
   ```zsh
   source venv/bin/activate
   ```

1. Install Ansible.
   ```zsh
   pip install --upgrade pip setuptools wheel pip-tools
   ```
   ```zsh
   pip install ansible==7.2.0
   ```

1. Install Ansible roles.
   ```zsh
   ansible-galaxy install --role-file .ansible/roles/check-in_requirements.yaml --roles-path .ansible/roles
   ```

1. Update all the Ubuntu hosts's Apt packages and reboot if necessary.
   ```zsh
   ansible-playbook --inventory .ansible/inventories/dev  --inventory .ansible/inventories/prod --extra-vars auto_reboot=yes .ansible/update.yaml
   ```
