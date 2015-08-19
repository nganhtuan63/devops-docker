#Docker Tutorial - Setup Development Environment with Docker

If your host machine is not a linux-based OS, please download VirtualBox and Vagrant to setup a Virtual Linux Host OS.

This guide will be used to install and config docker on Macbook with a Virtual Linux Host OS of Ubuntu/trusty (VirtualBox+Vagrant)

## Setup Virtual Machine

+ **Step 1**: Install Virtual Box - version 4.3.30 (https://www.virtualbox.org/wiki/Download_Old_Builds_4_3)

+ **Step 2**: Install Vagrant 1.7.4 (https://www.vagrantup.com/downloads.html)

+ **Step 3**: Create a folder for virtual machines
```
mkdir ~/VMS
mkdir ~/VMS/ubuntu
```
+ **Step 4**: Create an Ubuntu virtual machine

```
cd VMS/ubuntu
vagrant init ubuntu/trusty64; vagrant up --provider virtualbox
```

+ **Step 5**: Prepare folder structure
```
Source code on my laptop: ~/Source

DevOps on my laptop: ~/DevOps (please clone the source from https://github.com/nganhtuan63/DevOps)

Virtual Machines on my laptop: ~/VMS
```

+ **Step 6**: Edit the Vagrantfile to config virtual machine

Setup the IP Address for the guest VM. I will use the address 192.168.33.99

```
# Create a private network, which allows host-only access to the machine
# using a specific IP.
config.vm.network "private_network", ip: "192.168.33.99"
```

Share additional folders to the guest VM

```
config.vm.synced_folder "~/Source", "/var/www/html", :mount_options => ['dmode=777', 'fmode=777']
config.vm.synced_folder "~/DevOps", "/Devops"
```

Reload vagrant to apply new config

```
vagrant reload
```

## Setup Docker on guest VM

+ **Step 1**: Log in to the guest VM and switch to root user

```
cd ~/VMS/ubuntu
vagrant up
vagrant ssh
```

When you are inside the virtual machine, switch to root user

```
sudo -s
```

+ **Step 2**: Install Docker
(https://docs.docker.com/installation/ubuntulinux/)

```
apt-get update
apt-get install curl
curl -sSL https://get.docker.com/ | sh
```

Check docker is installed correctly by typing

```
sudo docker run hello-world
```

+ **Step 3**: Install Docker Composer

```
curl -L https://github.com/docker/compose/releases/download/1.4.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

## Use docker to create development containers

+ **Step 1**: Build a custom phpcontainer images
(This step is an example to demonstrate the steps of building an image from a Dockerfile)

```
cd /DevOps/docker/images/phpcomposer
docker build -t phpcomposer:5.6 .
```

Check to see the newly created image

```
docker images
```

+ **Step 2**: Create all containers with docker compose

```
cd /DevOps/docker
/usr/local/bin/docker-compose up
```

You will see a screen like this which means all containers have been created succesfully

