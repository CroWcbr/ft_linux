## Making the LFS System Bootable

- Creating the /etc/fstab File
```
cat > /etc/fstab << "EOF"
# Begin /etc/fstab

# file system  mount-point    type     options             dump  fsck
#                                                                order

/dev/sda3      /              ext4     defaults            1     1
/dev/sda1      /boot          ext4     noauto              1     2
/dev/sda2      swap           swap     pri=1               0     0
proc           /proc          proc     nosuid,noexec,nodev 0     0
sysfs          /sys           sysfs    nosuid,noexec,nodev 0     0
devpts         /dev/pts       devpts   gid=5,mode=620      0     0
tmpfs          /run           tmpfs    defaults            0     0
devtmpfs       /dev           devtmpfs mode=0755,nosuid    0     0
tmpfs          /dev/shm       tmpfs    nosuid,nodev        0     0
cgroup2        /sys/fs/cgroup cgroup2  nosuid,noexec,nodev 0     0

# End /etc/fstab
EOF
```
- Installation of the kernel
```
Important in task requiment:
	- change Makefile info (your login in EXTRAVERSION)
	- move linux-XXX to /usr/src/kernel-XXX

cp -iv arch/x86/boot/bzImage /boot/vmlinuz-6.4.12-<login>
```
- Creating the GRUB Configuration File
```
cat > /boot/grub/grub.cfg << "EOF"
# Begin /boot/grub/grub.cfg
set default=0
set timeout=5

insmod part_gpt
insmod ext2
set root=(hd0,1)

menuentry "GNU/Linux, Linux 6.4.12-<login>" {
        linux   /vmlinuz-6.4.12-<login> root=/dev/sda3 ro
}
EOF
```