# Administration of users and groups in linux

User and group management can only be performed by the root user using the user management commands.
The tasks and commands to perform them are:

* Creation of users / useradd
* Modification of users / usermod
* Removal of users / userdel
* Creation of groups / groupadd
* Modificación de grupos / groupmod
* Elimination of groups / groupdel
* Add users to a group / adduser
* Remove users from a group / deluser

#### Creation of users
The useradd command allows to add a user indicating as parameters the particular information to create 
the user in the same line of commands.
````bash
$ useradd [options] username
````
Among the most notable options we have:

* -g: Main group that we want the user to have (it must exist previously).
* -d: User's home folder. It is usually / home / username.
* -m: Create home folder if it does not exist.
* -s: Intérprete de comandos (shell) del usuario. Suele ser /bin/bash.

Example, if we want to create a user named 'antonio' main group is 'devel', whose home folder is / home / antonio and its command interpreter is / bin / bash, we will execute the following command:
````bash
$ sudo useradd -g devel -d / home / antonio -m -s / bin / bash antonio
````
In this way we will have created the user antonio and his home folder. If we do not use the -m option, the user's home folder will not be created; in that case we would have to create it manually. We will only have to set your password with the passwd command:
````bash
$ sudo passwd antonio
````
Then the system will ask us twice the password we want to assign to antonio.

The useradd command allows you to create many users automatically using scripts.

It is recommended that the username be in lowercase and in addition to letters it can also contain numbers and some signs such as normal dashes and underscores. We must remember that unix is case-sensitive, that is, Antonio is different from antonio.

#### Modification of users

The usermod command is used and it allows to change the name of the user, its home folder, its interpreter of commands, the groups to which it belongs and some other parameters.
````bash
$ sudo usermod -d / home / antonio folder antonio
````
#### Removal of users

It is done with the userdel command followed by the user's name. With the -r option, you will also delete your home folder, example:
````bash
sudo userdel -r antonio
````
I would remove the user antonio and his home folder.

#### Creation of groups

The groupadd command allows you to add a group by indicating the name of the group as a parameter. Example, if we want to create a group called 'devel' we will execute:
````bash
$ sudo groupadd devel
````
#### Modification of groups

The groupmod command allows modifying the name of a group or its gid. The syntax is: sudo groupmod [-g new-gid] [-n new-name] group-name, example:
````bash
$ sudo groupmod -g 1000 devel
````
#### Elimination of groups

It is done with the groupdel command followed by the name of the group, example:
````bash
sudo groupdel devel
````
I would eliminate the devel group. If any user had that group as a primary group, the groupdel command will not delete the group.

#### Add users to a group

The adduser command is used followed by the name of the user and the name of the group to which we want to add it, example:
````bash
$ sudo adduser mariano devel
````
#### Remove users from a group

The deluser command is used followed by the name of the user and the name of the group from which we want to remove it, example:
````bash
$ sudo deluser mariano devel
````
For more information on all these commands, you can consult the help of the manual by executing man followed by the name of the command, example man adduser.

#### Graphical user management tool

Ubuntu has a graphical user management tool that is 'users-admin'. To execute it we can open a root console and run users-admin or if we have logged in as root, we can press Alt + F2 and run users-admin.





