## System Configuration

- LFS-Bootscripts-20230728
- blfs-bootscripts-20230824 (for Intener setting)
- Creating Custom Udev Rules
```
bash /usr/lib/udev/init-net-rules.sh
cat /etc/udev/rules.d/70-persistent-net.rules
```
- General Network Configuration
```
ip link - check name of network device


cat > /etc/sysconfig/ifconfig.<name of network device> << "EOF"
ONBOOT=yes
IFACE=<name of network device>
SERVICE=dhclient
DHCP_START=""
DHCP_STOP=""


cat > /etc/resolv.conf << "EOF"
# Begin /etc/resolv.conf

nameserver 8.8.8.8
nameserver 8.8.4.4

# End /etc/resolv.conf
EOF


echo "student login" > /etc/hostname


cat > /etc/hosts << "EOF"
# Begin /etc/hosts

127.0.0.1 localhost
::1       localhost

# End /etc/hosts
EOF
```
- Configuring Sysvinit
- Configuring the System Clock
- Configuring the Linux Console
```
cat > /etc/sysconfig/console << "EOF"
# Begin /etc/sysconfig/console

KEYMAP="us"
FONT="lat1-16 -m 8859-1"
LOGLEVEL="3"

# End /etc/sysconfig/console
EOF
```
- The Bash Shell Startup Files
```
cat > /etc/profile << "EOF"
# Begin /etc/profile

export LANG=en_US.ISO-8859-1

# End /etc/profile
EOF
```
- Creating the /etc/inputrc File
- Creating the /etc/shells File
