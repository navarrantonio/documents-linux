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
In this example, copy the manual_linux file into a directory two levels higher than the current one, in the doc / linux directory
