# Managing Users

### What commands do I use to manage users?

The commands in linux to manage users are `useradd`, `userdel`, `usermod`, `chage` and `passwd`. When creating backend users for our app tier nodes in CernerWorks, we want to make sure these users are added to the correct domain groups, and have the correct CCL access. So we'll rarely use most of these commands in a standalone use case.&#x20;

### How do I add users then?

For users wanting command line access, we can use this spreadsheet designed by our friendly neighborhood guy, Josh. You enter the users name, their username, and domain. The spreadsheet will then spit out the commands you need to run to create their user, assign a password, and the command to use in CCL to give them Group 00.

{% file src="../.gitbook/assets/UserAdd.xlsx" %}
Users with Command Line
{% endfile %}

{% file src="../.gitbook/assets/UserAddMenu.xlsx" %}
Users with Menu Script
{% endfile %}

### Other Common User Issues

#### My user has an account already, but can't access it

Their account 9 times out of 10 their account is expired. Run `chage -l <username>` if it is, you can run `chage -E YYYY-MM-DD <username>` if not they probably forgot their password. Change it by su to the user and running passwd or the two commands below. \
`echo -e "Cerner123\nCerner123" | passwd <username>`\
`chage -d 0 <username>`

#### Easy way to tell if a user exists already?

Sure! `cat /etc/passwd | grep <username>` should do the trick.

#### My user has an account, but can't newgrp or envset to a specific domain on the node.

Easy peasy. They're probably not a part of the group for the domain. Check by running \
`groups <username>`, if they aren't part of the domain group they're trying to access you can add them to the group by running `usermod -a -G <group> <username>`
