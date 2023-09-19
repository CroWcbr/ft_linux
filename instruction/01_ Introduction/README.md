# Introduction
The LFS system will be built by using an already installed Linux distribution

## setting Virtual Mashine
```
30 GB of dynamic memory (10 is enough)
max avaliable processors (speeds up application building)
max avaliable RAM
network bridge
```
## installing and configuring debian
- install simple debian on VM (only ssh)
- setting up ssh connection by bridge
```
nano /etc/ssh/sshd_config
change "PermitRootLogin prohibit-password" -> "PermitRootLogin yes"

service ssh restart
systemctl restart sshd
```
- check IP
```
ip addr
```
## connecting to a virtual machine
- SSH connection from our system to VM
```
ssh root@<ip addr>
```
