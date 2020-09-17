# DevOps20

This vagrant will install 3 Linux Ubuntu machines in a test cluster on Vagrant, 1 master kubernetes node and 2 worker kubernetes nodes. This DevOps is to practice commands on a Kubernetes cluster.
It will add some default users, groups and directory's. It will install Kubernetes by default with Ansible and the root Kubernetes user is "kuber".
This Vagrant is to practice Kubernetes, commands on Kubernetes and deploy pods.
This repository is intended for educational purpose only.


## Prerequisites

Works on Windows 10 and tested on macOS (macOS needs the Virtualbox extension pack).

Software needed:
* Virtualbox 5.0 or higher
* Git bash for Windows
* Vagrant 2.2.6 or higher
* DevNet account at Cisco 


## Demo installation && use Vagrant

Youtube: https://youtu.be/KABnIuaA8SM


## Demo use Kubernetes

Youtube: 


## Installation

* Install Virtualbox: https://www.virtualbox.org/wiki/Downloads
* Install Git bash for Windows: https://gitforwindows.org/
* Install Vagrant for Windows: https://www.vagrantup.com/downloads.html
* Create an free account at DevNet: https://developer.cisco.com/

## Run this Vagrant VM
Open **Git Bash** in Windows
```
cd Documents
mkdir vagrant && cd vagrant
git clone https://github.com/borahuho/DevOps20
cd DevOps20
vagrant up
vagrant ssh master
```
## Mission

Read your mission in ~/vagrant/mission (on Ansible server)

## Network
Vagrant VM will be set up with 2 network adapters
```
Nat : DHCP
Localhost (master): 192.168.10.160

Nat : DHCP
Localhost (worker1): 192.168.10.161

Nat : DHCP
Localhost (worker2): 192.168.10.162
```
## Vagrant commands
Start VM's with Vagrant
```
vagrant up
```
Pause a VM
```
vagrant suspend
```
Restart a paused VM
```
vagrant resume
```
Stop and shutdown a VM
```
vagrant halt
```
Remove a VM
```
vagrant destroy
```
ssh in to the VM
```
vagrant ssh master
vagrant ssh worker1
vagrant ssh worker2
```

