# SCP (Secure Copy)

### What's SCP?

Secure copy protocol (SCP) is a means of securely transferring files between a local host and a remote host. It's based on the SSH protocol.&#x20;

### Why use SCP in my Job?

SCP is a great way to transfer files between two servers quickly and securely. I've used SCP for Linux upgrades and while doing storage maintenance to back up files. I've also used it to provision new servers by copying configuration files from built servers rather than retyping them.

### How do I use SCP?

`scp <LocalSourceFile> <user>@<remotehost>:<directory/TargetFileName>`
