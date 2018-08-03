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

useradd [options] username

Among the most notable options we have:

* -g: Main group that we want the user to have (it must exist previously).
* -d: User's home folder. It is usually / home / username.
* -m: Create home folder if it does not exist.
* -s: Intérprete de comandos (shell) del usuario. Suele ser /bin/bash.

Example, if we want to create a user named 'antonio' main group is 'devel', whose home folder is / home / antonio and its command interpreter is / bin / bash, we will execute the following command:

$ sudo useradd -g devel -d / home / antonio -m -s / bin / bash antonio

In this way we will have created the user antonio and his home folder. If we do not use the -m option, the user's home folder will not be created; in that case we would have to create it manually. We will only have to set your password with the passwd command:

$ sudo passwd antonio

Then the system will ask us twice the password we want to assign to antonio.

The useradd command allows you to create many users automatically using scripts.

It is recommended that the username be in lowercase and in addition to letters it can also contain numbers and some signs such as normal dashes and underscores. We must remember that unix is case-sensitive, that is, Antonio is different from antonio.



