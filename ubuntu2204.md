## Summary

**-> [Back to Index](./README.md)**

* [Server Setup](#server-setup)
* [Docker Install](#docker-install)
* [UFW](#ufw)

## Server Setup

When you first create a new Ubuntu 22.04 server, you should perform some important configuration steps as part of the initial setup. These steps will increase the security and usability of your server and will give you a solid foundation for subsequent actions.

### Before you start

Make sure that:
- You have a DigitalOcean Droplet with Ubuntu 22.04 running

### Setup

1. Logging in as root

```bash
ssh root@your_server_ip
```

2. Creating a New User

```bash
adduser enzo
```

3. Granting Administrative Privileges

To add user to sudo group:

```bash
usermod -aG sudo enzo
```

4. Setting Up a Firewall (If you need to open ports)

To list installed UFW profiles:

```bash
ufw app list
```

To allows SSH connections:

```bash
ufw allow OpenSSH
```

To enable UFW:

```bash
ufw enable
```

To check firewall status:

```bash
ufw status
```

5. Check External Access for Your Regular User

```bash
ssh enzo@your_server_ip
```

### References

- [DigitalOcean](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-22-04)

[Back to top](#summary)

## Docker Install

This tutorial will explain how to install and setup Docker CE on Ubuntu 22.04

### Before you start

Make sure that:
- You have an Ubuntu 22.04 server set up with a sudo non-root user and a firewall

### Install

Some introductory information.

1. Update list of packages

```bash
sudo apt update
```

2. Install prerequisite packages

```Bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```

3. Add GPG key of the official Docker repository

```Bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. Add the Docker repository to APT sources

```Bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. Update your existing list of packages again for the addition to be recognized

```bash
sudo apt update
```

6. Install Docker

```bash
sudo apt install docker-ce
```

7. Check Docker status

```bash
sudo systemctl status docker
```

### Setup Docker without sudo

1. Add user to the docker group

```Bash
sudo usermod -aG docker ${USER}
```

2. Log out and log back in
3. Check if you are in the Docker group

```bash
groups
```

4. Run Docker commands !

### References

- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04)

[Back to top](#summary)

## UFW

### Introduction

UFW is installed by default on Ubuntu. If it has been uninstalled for some reason, you can install it with `sudo apt install ufw`.

### Getting Started

#### Allow SSH connections

If you are connecting to your server remotely, you will need to allow SSH connections before doing anything else. You can allow SSH connections by typing:

```bash
ufw allow OpenSSH
```

Afterwards, you can enable UFW with:

```bash
ufw enable
```

#### Check UFW status and rules

You can check the status of UFW by typing:

```bash
ufw status
```

You can check the rules of UFW by typing:

```bash
ufw status numbered
```

#### Allow other connections

If you want to allow other connections, you can allow ports by typing:

```bash
ufw allow <port>/<optional: protocol>
```

Or you can allow services by typing:

```bash
ufw allow <service>
```

You can also allow connections from a specific IP address by typing:

```bash
ufw allow from <ip address>
```

There are many other options available. You can check them by typing:

```bash
ufw --help
```

#### Deny connections

If you want to deny connections, you can deny ports by typing:

```bash
ufw deny <port>/<optional: protocol>
```

You can do the same for services and IP addresses.

#### Delete rules

You can delete rules by typing (type `ufw status numbered` to get the rule number):

```bash
ufw delete <rule number>
```

Alternatively, you can delete rules by typing:

```bash
ufw delete allow <port>/<optional: protocol>
```

You can do the same for services and IP addresses.

#### Disable or reset UFW

You can disable UFW by typing:

```bash
ufw disable
```

You can reset UFW by typing:

```bash
ufw reset
```

### References

- [How To Set Up a Firewall with UFW on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-22-04)

[Back to top](#summary)