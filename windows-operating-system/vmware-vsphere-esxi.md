# VMWare vSphere/ESXi

### What is VMWare ESXi?

VMWare ESXi is a Type 1 Hypervisor Operating System offered by VMWare. It's how Virtual Machines (VM) are managed and deployed at Cerner in our Datacenters. The deployment and most of the management is done by provisioning teams outside of ClientOps for the most part.&#x20;

### What is VMWare vCenter?

vSphere/vCenter is a software solution offered by VMWare to manage multiple ESXi hosts all in one place. \
\
Rather then logging directly onto each hypervisor directly to manage the VM's hosted there which can be time consuming and tedious, you can log into vSphere and manage every VM on every ESXi host managed by that vCenter Server.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>vCenter Mangement diagram</p></figcaption></figure>

In the example above, we can see how this all works going from the bottom of the diagram to the top. \
\
The ESXi hypervisor operating system is installed on a server in a rack down at one of our datacenters. This is the software that will host the Virtual Machines and manage the resources (CPU, RAM, Storage) on each server. \
\
Then all of these ESXi servers are connected to the vCenter server which is a centralized management location. This way you don't have to log into each ESXi host separately to manage the VMs hosted on that hardware.&#x20;

In ClientOps, we will always log into a vCenter/vSphere server to manage our clients virtual machines.&#x20;
