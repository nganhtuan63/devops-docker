#Setup Development Environment with Docker

If your host machine is not a linux-based OS, please download VirtualBox and Vagrant to setup a Virtual Linux Host OS.

This guide will be used to install and config docker on Macbook with a Virtual Linux Host OS of Ubuntu/trusty (VirtualBox+Vagrant)

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

- Source code on my lap: **~/Source**
- DevOps on my lap: **~/DevOps** (please clone the source from https://github.com/nganhtuan63/DevOps)
- Virtual Machines on my lap: **~/VMS**

+ **Step 6**: Edit the Vagrantfile to config virtual machine
