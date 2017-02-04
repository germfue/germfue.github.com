1 download from torproject.org
2 find gpg key
    - verify without key
    - check key in tor page
    - import key
    - verify with key
3 unpack
4 sudo pkg install bash linux_base-c7-7.2.1511_3
5 edit /etc/fstab
fdesc           /dev/fd             fdescfs         rw          0       0
linprocfs       /compat/linux/proc  linprocfs       rw      0       0
tmpfs           /compat/linux/dev/shm  tmpfs   rw,mode=1777    0       0
6 sudo mount -a
