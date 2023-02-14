# AutowareAuto
AutowareAuto で遊ぶ

# Getting Started
## Requirements
- Docker >= 19.03
- NVIDIA Docker

## Installation
### Docker
- https://docs.docker.com/desktop/install/linux-install/
#### KVM virtualization support
```
// check if the KVM modules are enabled
$ lsmod | grep kvm
> kvm_intel ...
> kvm ...
// add user to the kv group in order to access the kvm device
$ sudo usermod -aG kvm username
$ sudo groups username
> username : users kvm
```
#### Install Docker Desktop
```
// Prerequisites
$ sudo apt install gnome-terminal
$ sudo apt remove docker-desktop
$ rm -r $HOME/.docker/desktop
$ sudo rm /usr/local/bin/com.docker.cli
$ sudo apt purge docker-desktop
```
```
// Install Docker Engine
$ sudo apt remove docker docker-engine docker.io containerd runc
$ apt update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
$ sudo docker run hello-world
$ sudo usermod -aG docker username
// re-login
$ newgrp docker
$ docker run hello-world
```
// Install Docker Desktop
```
$ wget https://desktop.docker.com/linux/main/amd64/95914/docker-desktop-4.16.2-amd64.deb
$ apt install ./docker-desktop-4.16.2-amd64.deb
ToDo: Launch Docker Desktop
```
### NVIDIA Container Toolkit
- https://github.com/NVIDIA/nvidia-docker
### ADE
- https://autowarefoundation.gitlab.io/autoware.auto/AutowareAuto/installation-ade.html
### SVL simulator
- https://autowarefoundation.gitlab.io/autoware.auto/AutowareAuto/lgsvl.html

## Usage