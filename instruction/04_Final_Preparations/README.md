## Final Preparations

- Creating a Limited Directory Layout in the LFS Filesystem
- Adding the LFS User
- Setting Up the Environment
'''
check .bashrc info and clear it
[ ! -e /etc/bash.bashrc ] || mv -v /etc/bash.bashrc /etc/bash.bashrc.NOUSE
'''
- extra action
'''
add flag MAKEFILES="-jX" to lfs user ~/.bash_profile and read new profile "source ~/.bash_profile"
'''