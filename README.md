[![Build Status](https://drone.kiwi-labs.net/api/badges/Diesel-Net/fleet/status.svg)](https://drone.kiwi-labs.net/Diesel-Net/fleet)

# fleet
Leveraging Docker Engine's built-in [Swarm Mode](https://docs.docker.com/engine/swarm/) on Ubuntu Server LTS Virtual Machines. This is the first piece of code that should be executed against a fresh host on the `diesel.net` domain

## Checking-In New Hosts
To add a new host (or set of hosts) create a new local branch name with the pattern `check-in/*`, add the new hosts and their configuration to the inventory, then push. Please delete your `check-in/*` branch after merging.

## Bootstrap fleet
Pushes to `stable` branches will trigger the entire fleet to be bootstrapped.
