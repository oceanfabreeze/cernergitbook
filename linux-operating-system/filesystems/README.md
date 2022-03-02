# Filesystems

Filesystems as a BE SE in ClientOps are pretty simple. The main filesystem types we use are ext3, ext4, xfs, and nfs. There's such a thing as a gluster/bricks filesystem but i'll cover that in another part of this guide.&#x20;

### How do I view the filesystems on a Linux node?

Using the command below we can list the filesystems on the node.

```
df -h
```

This command lists the filesystems in a human readable format. It should give you the space in each filesystem. The `-h` is the option flag for the command. You can add more options or remove options to manipulate the data the command comes back with. You can see all the options using \
`man df` command.

### How do I extend a filesystem?

You can extend a filesystem using the method below as long as the Volume Group that filesystem is a part of has free space.  You can check how much space a Volume Group has using the `vgs` command. \<filesystempath> is the path of the filesystem. You can change out +2G to any amount of space you want to add as long as it is available.&#x20;

#### For EXT filesystems

```
lvextend -L +2G <filesystempath>
resize2fs <filesystempath>
```

#### For XFS filesystems

```
lvextend -L +2G <filesystempath>
xfs_growfs <filesystempath>
```

### What if my Volume Group doesn't have enough space?

This isn't ideal. I like to be proactive and keep the VG's on the nodes I manage with a little freespace so I can extend in a pinch, but sometimes you take a look and bam. No free space. Sometimes we can steal a drive from the system if its a physical node or extend a drive if its a virtual node to add space. With the exception of VG00. VG00 should always only have 1 PV assigned to it.&#x20;

#### Lets see if we have a free drive available.&#x20;

Run `./disk_usage_report.sh` from `/usr/local/bin/` to see if any free disks are available.&#x20;

If there are disks available, you're in luck! You can run the below commands to add one to your VG and grab some free space. <mark style="color:red;">(Note: Don't add PV's to VG00!)</mark>

`pvcreate /dev/<diskname>`\
`vgextend <vgname> /dev/<diskname>`

#### I don't see a drive available on the system! Help!

Tough break there kid. Your options are...\
\
1\. Figure out how to free up some space for your needs.\
2\. Have someone add a new drive to the system for you to use.\
3\. Either you/someone else needs to extend or add a drive in vSphere if it's a VM.

#### My VG00 is full and I don't wanna add another PV cause you told me not to. What do I do?

Your options are...

1. If its a VM, extend the drive in vSphere.
2. If its a Physical Node it gets more complicated. You need someone to add another larger drive to the server. Then create a PV and add it to VG00. Then use `pvmove` or `rsync` to move all the files off of the old PV to the new larger PV. Then use `vgreduce` to remove the original, now empty PV from VG00.&#x20;

### Common Issues

#### /boot is full

Check to see if there is more than 2 Linux Kernels installed using `yum list kernel` and `yum list kernel-uek` if more than 2 Linux Kernel versions return, we can remove the old ones. \
\
<mark style="color:red;">Note: Don't remove the currently used kernel! You can find out what the current kernel version you're using is by running</mark> `uname -r`\
``\
``Once you've determined you have some old kernels lingering around, you can remove them using `yum remove <kernelname>`

#### Filesystem isn't mounting on boot/reboot! What gives?

Filesystems are mounted at boot using the /etc/fstab file. Make sure your filesystem is in /etc/fstab using vim `/etc/fstab`

If your filesystem is in fstab, then it could be corrupt. If you can, unmount the partition the filesystem exists on, then run `fsck -y /dev/<drivename>`\
``If you are unable to unmount the filesystem due to it being on the root partition, you'll need to run these commands in rescue mode, or force to run on reboot. I recommend running in rescue, but if you'd rather it autorun you can do  `touch /forcefsck`on the root partition of the system. This may mean reboot will take a while so plan accordingly.&#x20;

#### My filesystem is full and I see a bunch of files that show 0 bytes. What gives?

Even though these files show 0, they do take up space when there's enough of them. Remove them if they're not important, but you should do your due diligence and try to figure out where they're coming from.
