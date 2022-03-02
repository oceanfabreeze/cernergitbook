# Managing Permissions

### What are permissions?

Permissions are Linux's way of handling security on files and directories. Every file and directory within Linux adheres to this system. Permissions prevent the wrong users getting access to the wrong files.&#x20;

### How do they work?

When you run a long listing on a filesystem you should see something like this.\


![](<../.gitbook/assets/image (1).png>)

The first character represents the file type. Below are some file types you might see. \
\
`- : regular file`\
`d : directory`\
`c : character device file`\
`b : block device file`\
`s : local socket file`\
`p : named pipe`\
`l : symbolic link`\
\
The next three characters represent the owner of the file, the owner of the file is the first username presented in the example above. Which is root in this case. The next three characters represents the groups permissions, the group is represented by the second presented username, this is also root in the example above. The third three characters is everyone else on the system that is not an owner or part of the file group. The first letter is always READ, the second is always WRITE and the third is always EXECUTE. These permissions are defined using the letters in the graphic above.&#x20;

### How do I change File/Directory permissions?

File permissions are changed using the `chmod` command. There are two ways to use chmod, but note the _<mark style="color:red;">**preferred way is by using Binary Definition.**</mark>_&#x20;

#### Using Explicit Definition

To explicitly define permissions you will need to reference the Permission Group and Permission Types.

The Permission Groups used are:

* **u** – Owner
* **g** – Group
* **o** – Others

The potential Assignment Operators are + (plus) and – (minus); these are used to tell the system whether to add or remove the specific permissions.

The Permission Types that are used are:

* **r** – Read
* **w** – Write
* **x** – Execute

So for example, let’s say I have a file named file1 that currently has the permissions set to \_rw\_rw\_rw, which means that the owner, group, and all users have read and write permission. Now we want to remove the read and write permissions from the all users group.

To make this modification you would invoke the command: `chmod a-rw <filename>`\
To add the permissions above you would invoke the command: `chmod a+rw <filename>`

As you can see, if you want to grant those permissions you would change the minus character to a plus to add those permissions.

#### Using Binary Definition

To set the permission using binary references you must first understand that the input is done by entering three integers/numbers.

A sample permission string would be `chmod 640 <filename>`, which means that the owner has read and write permissions, the group has read permissions, and all other user have no rights to the file.

The first number represents the Owner permission; the second represents the Group permissions; and the last number represents the permissions for all other users. The numbers are a binary representation of the rwx string.

* _**r** = 4_
* _**w** = 2_
* _**x** = 1_

You add the numbers to get the integer/number representing the permissions you wish to set. You will need to include the binary permissions for each of the three permission groups.

### How do I change Owner and Group Permissions on a File/Directory?

You can use the `chown` command to change file ownership using the command below.\
\
`chown <owner>:<group> <filename>`



