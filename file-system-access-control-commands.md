# Management of archives and directories througn commands

The most frequently used commands are briefly described below. For a greater level of detail, it is suggested to consult the Linux online manual (see below the man command) and especially the documentation of the command interpreter used (usually, the bash).

## Linux commands for the management of file and directories

##### cp

The cp command is an abbreviation of copy; allows to copy files and directories. To copy a file the following command is used:
Syntax
````bash
$ cp [Options] source_file destination_directory

$ cp [Options] source_file destination_file
````
Options

-a keeps all the attributes of the files.

-b makes a backup before proceeding to the copy.

-d copies a link but not the file that is referenced.

-i asks for confirmation before overwriting files.

-p keeps the seals of property, permits and date.

-R copies the files and subdirectories.

-s creates links instead of copying the files.

-u only proceed to the copy if the date of the source file is later than the date of the destination.

-v shows messages related to the process of copying the files.

Description

The cp command copies one file to another. You can also copy several files in a certain directory.

Example.
````bash
$ cp manual_linux_v1 ../../../doc/linux
````
In this example, copy the manual_linux file into a directory two levels higher than the current one, in the doc / linux directory.

#### mv
Modify the name of the files and directories by moving them from one location to another.

Syntax
````bash
$ mv [Options] destination source
````
Options

-d backs up the files that will be moved or renamed.

-f deletes the files without requesting confirmation.

-v asks before overwriting the existing files.

Description

The mv command can be used to modify the name or move a file from one directory to another. Works with both files and directories.

Example.
````bash
$ mv manual_linux_v1 manuals / linux

$ mv manual_linux_v1 manual_linux_v1_doc

$ mv manual_linux_cap1 manual_linux_cap2 manual_linux_cap2 / manual / linux
````
#### rm
elete one more files (you can delete a complete directory with the -r option).

Syntax
````bash
$ rm [Options] files
````
Options

-f deletes all the files without asking.

-i ask before deleting a file.

-r removes all the files that are in a subdirectory and finally deletes the own subdirectory.

-v shows the name of each file before deleting it.

Description

The rm command is used to delete the files that you specify. To delete a file you must have write permission in the directory in which it is located.

Example.
````bash
$ rm manual_linux_v1

$ rm -r documents /
````
#### mkdir
create directories.

Syntax
````bash
$ mkdir [Options] dir_name
````
Options

-m mode, assign the specified permission settings to the new directory.

-p creates related directories (in case they do not exist).

Description

The mkdir command is used to create a specific directory.

Example.
````bash
$ mkdir manuals
````
#### rmdir

Delete a directory (as long as it is empty).

Syntax
````bash
$ rmdir [Options] directory
````
Options

-p deletes any related directory that is empty.

Description

The rmdir command removes empty directories. If you have any content, you will have to use the rm -r command to delete the directory and its contents.

Example.
````bash
$ rmdir manual
````
#### ls

List the contents of a directory.

Syntax
````bash
$ ls [Options] [dir_name or file]
````
Options

-a shows all the files. Including the hidden ones.

-b shows the non-printable characters of the file names using an octal code.

-c sorts the files according to the creation date.

-d displays a list in which the directories appear as if they were files (instead of displaying their contents).

-f shows the contents of the directory without sorting.

-i shows i-node information.

-l shows the list of files with long format and with detailed information (size, user, group, permissions, etc.).

-p adds a character to the file name to indicate which type it belongs to.

-r places the list in reverse alphabetical order.

-s shows the size (kb) of each file next to the one requested.

-t sorts the list according to the date of each file.

-R displays a list of the contents of the current directory and all its subdirectories.

Description

The ls command shows the contents of a given directory. If the name of the directory is omitted, it will show the contents of the directory in which it is located. By default, ls does not show the name of files whose name starts with a period; to see them you will have to use the -a option.

Example.
````bash
$ ls -a

$ ls -l

$ ls -la
````
#### cd

Change directory.

Syntax
````bash
$ cd [directory]
````
Options

Any

Description

If you type cd without any directory name as an argument, it will be changed to the user's home directory. In any other case it will move to the indicated directory, if it exists.

#### pwd

Show the current work directory path.

Syntax.
````bash
$ pwd
````
Options

Any

Description

The pwd command prints the working directory (the one in which you are currently working).

#### chmod

Modify the permissions of one or more files or directories.

Syntax
````bash
$ chmod [Options] [permission_description] file
````
Options

-c shows the files to which the permissions have been modified.

-f causes no error message to appear on the screen.

-v shows the changes made to the file permissions.

-R changes the permissions of the files of all subdirectories.

* Permissions_description

* Who Permission Action

* Who:
u: user

g: group

or: others

to all

* Action
+: add

-: remove

=: assign

* Permission
r: reading

w: writing

x: execute

s: adjust with the user ID.

Example.
````bash
$ chmod u + xr manual_linux
````
The user will have read and execute permissions on the manual_linux file

* Description

To use the chmod command effectively, you must specify the configuration of the permissions according to the description_permission table.

For example, so that everyone has read permission in a certain file is typed, chmod a + r filename. You could also have typed chmod u = r, g = r, or = r filename.

Another way to modify the permits is through an octal number of 3 digits a figure for each group of permits, this number comes from making the sum of the permits that they want to assign according to the following values:

Read permission r = 4

Write permission w = 2

Execution permit x = 1

And if any permission is not granted, the assigned value is 0.

The format to use chmod specifying the permissions by means of numbers is the following.
````bash
$ chmod user_pass permission_group permission_other
````
Example, suppose we create the file permission.txt and we want the user to have all the permissions, the group the read and execute permissions and finally the rest of the users have only the execution permission.

For the user: reading r = 4, writing w = 2, execution x = 1; summed = 7

For the group: reading r = 4, writing w = 0, execution x = 1; summed = 5

For the rest of the users: reading r = 0; writing w = 0, execution x = 1; added = 1

Then the command would be: chmod 751 permissions.txt

In the detailed list of the files in a directory (using the ls command), the read and execute read permissions of the user, group and others will be displayed through the rwxrwxrwx sequence, when a permission is not activated a hyphen appears in its replacement.

#### cat

Displays the contents of a file using the standard output (screen).

Syntax
````bash
$ cat [-benstvA] files
````
Options

-b numbers of lines that are not blank.

-e shows the end of a line (like $) and all non-printable characters.

-n number all the output lines, starting with 1.

-s replaces several blank lines with one.

-t shows the tabulations as ^ l.

-v shows the non-printable characters.

-A displays all characters (including non-printable characters).

Description

Normally, cat is used to show the contents of a file or to concatenate several within the same file. For example,

cat file1, file2, file3> all
combines the three files into one called everything.

#### find

Purpose

Displays a list of files that match a specific criterion.

Syntax
````bash
$ find [route] [options]
````
Options

-depth processes, in the first place, the directory in which it is located and then its subdirectories.

-maxdepyh n restricts the search to n levels of directories.

-follow processes the directories that are included within the symbolic links.

-name model locates the names of the files that match the proposed model.

-ctime n locates the names of the files created n days ago.

-user user_name user_name locates the files belonging to the specific user.

-group group_name locates the files belonging to the specific group.

-path path locates the files whose path matches the proposed model.

-perm mode locates the files with the specified permissions.

-size + nK locates files whose size (in kilobytes) is greater than specified.

-print prints the name of the files it finds.

-exec command [options] {} \; executes the specified command by analyzing the name of the localized file.

Description

The find command is very useful when you want to locate all the files that match some criterion. If you type find without any argument, the output will show a list in which the files of all the subdirectories of the folder in which you are located appear.

To see all the files whose name ends with .gz, you will have to write:
````bash
$ find -name "* .gz".
````
To search from the / usr / doc directory for all files with a bak extension and delete them, use the command:
````bash
$ find / usr / doc -name "* .bak" -exec rm -f {} \;
````
where the sequence {} will be replaced by the full name of each file found.

#### grep

Search one or more files for lines that match a regular expression (search model).

Syntax
````bash
$ grep [options] model files
````
Options

-N shows N lines that contain the indicated search model.

-c shows the number of lines that contain the search model.

-f file reads the options of the specified file.

-i ignore letters

-l shows the names of the files that contain a model.

-q returns the line number following those in which the search model is found.

-v shows the lines that do not contain the search model.

Description

The command locates the search model in the specified files. The model is a regular expression in the specified files that have their own rules. It is usually used to search for a sequence of characters in one or more text files.

Example:
````bash
$ grep antonio Listing of tasks.txt
````
#### Other linux commands

* man: Displays sections of the user's manual on screen.
````bash
Format: $ man name of the command.

Example: $ man ls.
````

* mesg: Enables or disables communication between users by means of write.
````bash
Format: $ mesg [n / y].
````

* ipr: Prints the contents of a file.
````bash
Format: $ ipr [Option] File
````
The main options are considered:

-P tail Indicates the print queue to use.

-n <number>: Indicates the number of copies to print, by default it is always 1.

-R: Remove the file after printing.

 
* tree: Lists all directories from the current directory or from the indicated directory.
````bash
Format: $ tree [Directory].
````
* tty: Shows the number of the terminal where the user is working.
````bash
Format: $ tty
````
* who: Displays the users that are active in the system, without any argument this command shows the user names, terminal number and connection time for each active user of the system. Using the arguments who am i the command shows what username you are connected to.
````bash
Format: $ who [Option]
````
* write: Send messages to other users until "Control D" is typed. The reception of these messages can be disabled by the user using the MESG command.
````bash
Format: $ write terminal user
````bash
