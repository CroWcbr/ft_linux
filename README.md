# ft_linux
Make your own linux distribution

## Linux From Scratch - Version 12.0
- https://linuxfromscratch.org/lfs/view/stable/index.html
- https://linuxfromscratch.org/blfs/view/stable/index.html

## Instaction LFS
- the entire installation follows the book
- additional points are described in the instructions folder

## Instaction BLFS
- some test with BLFS
- I don' install graphic interface - it's too long ))) and I prefer terminal

## Final version
- For KFS modules I am going to use BLFS with ssh and wget installed.

## General instructions
- For this subject, you must use a virtual machine, live VirtualBox or VMWare.
```
Oracle VM VirtualBox
```
- You must use a kernel version >= 4.0. Stable or not, as long as it’s a 4.0 >=
version.
```
uname -r
```
- The kernel sources must be in /usr/src/kernel-$(version)
```
ls /usr/sources
```
- You must use at least 3 differents partitions. (root, /boot and a swap partition). You can of course make more partitions if you want to.
```
lsblk
```
- Your distro must implement a kernel_module loader, like udev.
```
find / -name "udev"
pa aus | grep udev
```
- The kernel version must contain your student login in it. Something like ‘Linux kernel 4.1.2-<student_login>‘
```
uname
```
- You must use a sofware for central management and configuration, like SysV or SystemD.
```
- ps -p 1 -o comm=
```
- Your distro must boot with a bootloader, like LILO or GRUB.
```
mount /boot
```