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
$ docker compose version
$ docker --version
$ systemctl --user enable docker-desktop
```
### NVIDIA Drivers
```   
$ sudo apt clean
$ sudo apt update
$ sudo apt purge nvidia* libnvidia* cuda*
$ sudo apt autoremove
$ sudo apt autoclean
$ dpkg -l | grep nvidia
$ dpkg -l | grep cuda
> rc  cuda-cudart-11-2  11.2.152-1  amd64  CUDA Runtime native Libraries
> ...
$ sudo dpkg --purge cuda-cudart-11-2
```
```   
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt update
// まずは推奨バージョンのインストール
$ sudo ubuntu-drivers autoinstall
// 依存関係が解決できないなどの問題発生時は手動で別バージョンをインストール
$ ubuntu-drivers devices
$ apt install nvidia-driver-510
// 再起動してから動作確認(モニタ使用時はケーブルをGPUに挿す．)
$ nvidia-smi
```
### NVIDIA Container Toolkit
- https://github.com/NVIDIA/nvidia-docker
```
$ distribution=$(. /etc/os-release;echo $ID$VERSION_ID) && curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg && curl -s -L https://nvidia.github.io/libnvidia-container/experimental/$distribution/libnvidia-container.list | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
$ sudo apt update
$ sudo apt install nvidia-container-toolkit
$ sudo nvidia-ctk runtime configure --runtime=docker
$ sudo systemctl restart docker
$ sudo docker run --rm --runtime=nvidia --gpus all nvidia/cuda:11.6.2-base-ubuntu20.04 nvidia-smi
```
### ADE
- https://autowarefoundation.gitlab.io/autoware.auto/AutowareAuto/installation-ade.html
### SVL simulator
- https://autowarefoundation.gitlab.io/autoware.auto/AutowareAuto/lgsvl.html

## Usage