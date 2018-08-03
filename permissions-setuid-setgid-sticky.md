# Special permissions (setuid, setgid, sticky bit)

In Unix there are three special permission bits that can be assigned to directories and / or executable files, setuid (set user information), setgid (set group information)
and sticky.

#### setuid
The setuid bit is assignable to executable files, and allows that when a user executes said file, the process acquires the permissions of the owner of the executed file. The clearest example of executable file and with the bit setuid su.

it serves to execute a shell with group and user identifiers different from ours, so it must have this bit and thus allow the user to temporarily acquire administrative permissions in order to make the user change.

We can see that the bit is assigned (s) by doing an ls:

antonio@antonio-venez:~/devel/packer/b$ ls -l /bin/su
-rwsr-xr-x 1 root root 40128 may 16  2017 /bin/su
antonio@antonio-venez:~/devel/packer/b$ 

