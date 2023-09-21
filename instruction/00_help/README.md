## Question

### if VM restart happened
- Setting The $LFS Variable
```
export LFS=/mnt/lfs
```
- Mounting 
```
mount -v -t ext4 /dev/sdb3 $LFS
mount -v -t ext4 /dev/sdb1 $LFS/boot
/sbin/swapon -v /dev/sdb2

mount -v --bind /dev $LFS/dev
mount -v --bind /dev/pts $LFS/dev/pts
mount -vt proc proc $LFS/proc
mount -vt sysfs sysfs $LFS/sys
mount -vt tmpfs tmpfs $LFS/run

if [ -h $LFS/dev/shm ]; then
  mkdir -pv $LFS/$(readlink $LFS/dev/shm)
else
  mount -t tmpfs -o nosuid,nodev tmpfs $LFS/dev/shm
fi

chroot "$LFS" /usr/bin/env -i   \
    HOME=/root                  \
    TERM="$TERM"                \
    PS1='(lfs chroot) \u:\w\$ ' \
    PATH=/usr/bin:/usr/sbin     \
    MAKEFLAGS="-j4"             \
    /bin/bash --login
```
- update setting files after finish
```
mount -v -t ext4 /dev/sdb3 $LFS

chroot "$LFS" /usr/bin/env -i   \
    HOME=/root                  \
    TERM="$TERM"                \
    PS1='(lfs chroot) \u:\w\$ ' \
    PATH=/usr/bin:/usr/sbin     \
    MAKEFLAGS="-j4"             \
    /bin/bash --login

cd $LFS
```