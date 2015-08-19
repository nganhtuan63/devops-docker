#Setup Development Environment with Docker

If your host machine is not a linux-based OS, please download VirtualBox and Vagrant to setup a Virtual Linux Host OS.

This guide will be used to install and config docker on Macbook with a Virtual Linux Host OS of Ubuntu/trusty (VirtualBox+Vagrant)

1/ Install Virtual Box - version 4.3.30 (https://www.virtualbox.org/wiki/Download_Old_Builds_4_3)

2/ Install Vagrant 1.7.4 (https://www.vagrantup.com/downloads.html)

3/ Create a folder for virtual machines

```
mkdir ~/VMS
mkdir ~/VMS/ubuntu
```

4/ Create an Ubuntu virtual machine

```
cd VMS/ubuntu
vagrant init ubuntu/trusty64; vagrant up --provider virtualbox
```

5/ Prepare folder structure

- Source code on my lap: **~/Source**
- DevOps on my lap: **~/DevOps** (please clone the source from https://github.com/nganhtuan63/DevOps)
- Virtual Machines on my lap: **~/VMS**

6/ Prepare folder structure