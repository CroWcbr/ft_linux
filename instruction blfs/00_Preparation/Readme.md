## Preparation
I try to undestand how it works =)

### VM setting
- clone VM lfs
- run VM
- create sourse dir /sourse/BLFS/

### Install wget
- download Wget using ftp
```
command - ftp ftp.gnu.org
NAME - anonymous
command -cd gnu
command -cd wget
command - bi (binary mode)
command - pass (passive mode)
command - get wget-1.21.4.tar.gz
command - quit
```
- install

### Install SSH
- download OpenSSH using wget
- install ssh
- add PermitRootLogin
- install blfs-bootscripts

### Connect from our system using ssh
- the first step FINISHED!!!