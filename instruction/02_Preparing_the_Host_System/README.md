## Preparing the Host System

### Host System Requirements
```
Check all using script in book version-check.sh and if somthing wrong, update it.
For example, I have wrong symbol link "/bin/sh -> dash" but must be "/bin/sh -> bash" :
check bash link   : ls -la /bin/sh
delete link       : rm /bin/sh
create right link : ln -s bash /bin/sh
```

### Creating a New Partition
```
using fdisk /dev/sdb partition the disk :
Device     Boot   Start      End  Sectors  Size Id Type
/dev/sdb1          2048   514047   512000  250M 83 Linux
/dev/sdb2        514048  6805503  6291456    3G 82 Linux swap / Solaris
/dev/sdb3       6805504 62914559 56109056 26.8G 83 Linux
```

### Creating a File System on the Partition
```
mkfs -v -t ext4 /dev/sdb1
mkfs -v -t ext4 /dev/sdb3
mkswap /dev/sdb2
```

### Setting The $LFS Variable
```
export LFS=/mnt/lfs
```

### Mounting the New Partition
```
mkdir -pv $LFS
mount -v -t ext4 /dev/sdb3 $LFS
mkdir -v $LFS/boot
mount -v -t ext4 /dev/sdb1 $LFS/boot
/sbin/swapon -v /dev/sdb2
```
