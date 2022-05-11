# StickyBit!

### What's a stickybit?

A Sticky bit is a permission bit that is set on a file or a directory that lets only the owner of the file/directory or the root user to delete or rename the file. No other user is given privileges to delete the file created by some other user.

### How do I know if something has a stickybit?

Stickybit is defined in file and directory permissions as a lowercase T. Example below.&#x20;



```
drwxrwxrwt 2 tom tom 4096 Mar 03 16:19 stickyFolder/
```

### How do I set a stickybit?

You can set a stickybit using chmod with binary permissions method or explicit permissions method defined in the Managing Permissions section of this GitBook.&#x20;

#### Binary Permissions

To add a stickybit using binary permissions, instead of using 3 integers you'd use four. So to set a stickybit you'd just add a 1 to the beginning of the permissions, and to remove the stickybit, you'd add a 0. Example below.&#x20;

`chmod 1777 stickyFolder`

#### Explicit Permissions

When using explicit permissions, you can just add a lowercase T to the permissions. Minus to remove. Example below.

`chmod +t stickyFolder`
