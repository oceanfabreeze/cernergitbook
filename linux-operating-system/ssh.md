# SSH

### What's SSH?

SSH stands for Secure Shell Protocol. It allows you to access a machine remotely. SSH works as     ( SSH Client --> SSH Server ). It was designed as a replacement for the more insecure Linux remote shell protocols like telnet. \
\
SSH uses public-key cryptography to authenticate the remote computer and allow it to authenticate the user, if necessary. SSH may be used in several methodologies. In the simplest manner, both ends of a communication channel use automatically generated public-private key pairs to encrypt a network connection, and then use a password to authenticate the user. \
\
SSH is typically used to log into a remote machine and execute commands, but it also supports tunneling, TCP, and X11 connections. It also supports a few file transfer services like SFTP and SCP.

Cerner as of today (3/1/2022) uses Oracle Enterprise Linux on all of our production Linux servers. Oracle Enterprise Linux comes with SSH installed and enabled by default.&#x20;

### Common SSH Knowledge

1. SSH runs by default over port 22.&#x20;
2. `~/.ssh/id_*.pub` = public key
3. `~/.ssh/authorized_keys` = all authorized keys
4. `ssh-keygen` = command to generate SSH keys for a server
5. `ssh-copy-id root@<server>` = copies the ssh key to another servers authorized keys file.

### Reverse SSH?

So someone at Cerner asked you to setup reverse-ssh between nodes? Can't find any details online about it? Well it's because "reverse SSH" is a dumb Cerner phrase. What you're being asked to do, is set up passwordless SSH authentication between servers. This should be fairly easy as Cerner has a special script to help you if you don't wanna do it the normal way.&#x20;

#### For Client 724

1. Log onto a 724 node
2. `su - oracle`
3. `dr_menu 724pc`
4. Choose option 2 (Admin Tool Management)
5. Choose option 1 (Reverse SSH Setup for Admin Tool)
6. Enter name of Client PC&#x20;

#### For all other nodes

Run `/usr/local/cwx/ssh_setup.ksh -u root -n <node1,node2,node3,etc>`
