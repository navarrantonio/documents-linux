# Special permissions (setuid, setgid, sticky bit)

In Unix there are three special permission bits that can be assigned to directories and / or executable files, setuid (set user information), setgid (set group information)
and sticky.

##### octal representation is the one that follows
* Sticky bit --> 1000
* Bit setgid --> 2000
* Bit setuid --> 4000

#### About chmod 

chmod is used to change the permissions of files or directories.

In general, chmod commands take the form:
````bash
$ chmod options permissions file name
````
If no options are specified, chmod modifies the permissions of the file specified by file name to the permissions specified by permissions.

permissions defines the permissions for the owner of the file (the "user"), members of the group who owns the file (the "group"), and anyone else ("others"). There are two ways to represent these permissions: with symbols (alphanumeric characters), or with octal numbers (the digits 0 through 7).

Let's say you are the owner of a file named myfile, and you want to set its permissions so that:

* the user can read, write, ande xecute it;
* members of your group can read ande xecute it; and
* others may only read it.

This command will do the trick:

````bash
$ chmod u=rwx,g=rx,o=r myfile
````
This example uses symbolic permissions notation. The letters u, g, and o stand for "user", "group", and "other". The equals sign ("=") means "set the permissions exactly like this," and the letters "r", "w", and "x" stand for "read", "write", and "execute", respectively. The commas separate the different classes of permissions, and there are no spaces in between them.

Here is the equivalent command using octal permissions notation:

chmod 754 myfile

Here the digits 7, 5, and 4 each individually represent the permissions for the user, group, and others, in that order. Each digit is a combination of the numbers 4, 2, 1, and 0:

* 4 stands for "read",
* 2 stands for "write",
* 1 stands for "execute", and
* 0 stands for "no permission."

So 7 is the combination of permissions 4+2+1 (read, write, and execute), 5 is 4+0+1 (read, no write, and execute), and 4 is 4+0+0 (read, no write, and no execute).

#### Bit setuid
The setuid bit is assignable to executable files, and allows that when a user executes said file, the process acquires the permissions of the owner of the executed file. The clearest example of executable file and with the bit setuid su.

it serves to execute a shell with group and user identifiers different from ours, so it must have this bit and thus allow the user to temporarily acquire administrative permissions in order to make the user change.

We can see that the bit is assigned (s) by doing an ls:
````bash
antonio@antonio-venez:~/devel/packer/b$ ls -l /bin/su
-rwsr-xr-x 1 root root 40128 may 16  2017 /bin/su
antonio@antonio-venez:~/devel/packer/b$ 
````
To assign this bit to a file:
````bash
$ chmod u+s /bin/su
````
And to remove it:
````bash
$ chmod u-s /bin/su
````
Logically, it is a good idea to use this bit with extreme care as it can cause privilege escalation in unsafe situations.

#### Bit setgid

It is the same as what we just explained for the setuid, but applicable to the group. If setting the previous bit we were able to establish the permissions as a EUID (Efective UID) in this case what we are going to achieve is the same, but at the level of the EGID group (Efective GID). The way to establish said permits is with 2000, in its octal representation.
````bash
$ chmod 2770 /usr/local/sbin
````
Instead of octal mode you can also assign the setgid permissions as follows:
````bash
$ chmog g+s /shared

And remove it:
$ chmog g-s /shared
````
SET GID is an interesting option if many users are going to access a common storage system, either
SAMBA
FTP
HTTP
Databases

#### Stincky Bit

Although at present it is not widely used, in the old Unix systems this activated bit indicated to the operating system that it kept the program in memory, in order to facilitate its execution. Since it was in memory it is not necessary to reload it and its execution is much faster. With the evolution of technology this bit no longer has that functionality, since the load of programs is now much faster.

Currently, this Sticky bit is used to define those files or directories that only the owner can change. This bit prevails over the rest of the permissions, so only the owner will have access to the file.
An example of use is the / tmp directory, which has the following permissions,

````bash
antonio@antonio-venez:~/devel/packer/b$ ls -l /
total 100
drwxr-xr-x   2 root root  4096 ago  2 12:15 bin
drwxr-xr-x   3 root root  4096 ago  2 12:18 boot
drwxr-xr-x   2 root root  4096 ago  1 11:46 cdrom
drwxr-xr-x  22 root root  4300 ago  3 09:48 dev
drwxr-xr-x 139 root root 12288 ago  2 12:19 etc
drwxr-xr-x   3 root root  4096 ago  1 11:47 home
lrwxrwxrwx   1 root root    33 ago  1 11:49 initrd.img -> boot/initrd.img-4.13.0-36-generic
drwxr-xr-x  23 root root  4096 ago  1 12:08 lib
drwxr-xr-x   2 root root  4096 feb 28 15:26 lib64
drwx------   2 root root 16384 ago  1 11:43 lost+found
drwxr-xr-x   3 root root  4096 ago  1 12:00 media
drwxr-xr-x   2 root root  4096 feb 28 15:25 mnt
drwxr-xr-x   3 root root  4096 ago  1 12:19 opt
dr-xr-xr-x 245 root root     0 ago  3 09:47 proc
drwx------   5 root root  4096 ago  1 16:42 root
drwxr-xr-x  29 root root   940 ago  3 10:24 run
drwxr-xr-x   2 root root 12288 ago  2 12:15 sbin
drwxr-xr-x   2 root root  4096 nov 30  2017 snap
drwxr-xr-x   2 root root  4096 feb 28 15:25 srv
dr-xr-xr-x  13 root root     0 ago  3 09:47 sys
drwxrwxrwt  16 root root  4096 ago  3 11:24 tmp
drwxr-xr-x  11 root root  4096 feb 28 15:35 usr
drwxr-xr-x  15 root root  4096 ago  1 12:18 var
lrwxrwxrwx   1 root root    30 ago  1 11:49 vmlinuz -> boot/vmlinuz-4.13.0-36-generic
````
To establish a file or directory with this property you have to choose one of both options,
````bash
$ chmod 1755 /tmp

$ chmod a+t /tmp
````
