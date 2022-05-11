# Networking and DNS

### How does Networking work on Linux?

Linux refers to anything network related as an interface, but it largely works the same as networking on any other operating system. Just the configuration is a little different.

### How do I get the IP address of the machine i'm currently on?

Run `ifconfig -a` to see the network interfaces currently configured on your system. On most systems at Cerner bond0 is going to be the primary network interface to look at.&#x20;

### How does DNS work in Linux?

DNS server entries are configured in the `/etc/resolv.conf` file. The only thing that bypasses a query of the DNS server is if the IP is listed in `/etc/hosts` file.

### Other Networking Questions?&#x20;

Ping me on Discord if you have questions.&#x20;
