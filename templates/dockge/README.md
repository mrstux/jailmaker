# Debian Docker with Dockge Jail Template

## Setup

Docker is used to run containerized workloads. Docker Compose allows assembling containers using a yaml file description, typically
in a compose.yaml, or docker-compase.yaml file.

Dockge is a GUI for managing docker compose stacks

The philosophy of a dockge jail is that the actual jail should be disposable, and the stacks and all data are mounted into the jail, much like a docker container.

This config file will prepare a jail to host docker with dockge pre-installed, and ready to manage compose stacks

It is assumed that you will create a few data sets on your pool, assuming it is called "tank"

- tank/docker
- tank/docker/data
- tank/docker/stacks

The docker/data dataset is used to contain any data created by docker containers,

Edit the config to refere to the actual datasets on your pool, adjust the networking, and then create the jail.

Once created you can check `docker ps` to see if the dockge process has started, `ip a` to see the allocated IPs, and then connect to <ip>:5001 to signin to your dockge environment.

Check out the [config](./config) template file. You may provide it when asked during `jlmkr create` or, if you have the template file stored on your NAS, you may provide it directly by running `jlmkr create --start --config /mnt/tank/path/to/dockge/config mydockerjail`.