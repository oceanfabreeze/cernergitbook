# SFTP

### What's SFTP?

SFTP (SSH File Transfer Protocol) is a secure file transfer protocol. It runs over the SSH Protocol. It supports the full security and authentication functionality of SSH. SFTP also protects against password sniffing and man-in-the-middle attacks. It protects the integrity of the data using encryption and cryptographic hash functions, and authenticates both the server and the user.\
\
SFTP port number is port 22. There is no separate SFTP port exposed on servers. No need to configure another hole into firewalls. SFTP is installed and enabled by default on most linux distributions including the ones currently used by Cerner at the time of writing (Oracle Enterprise Linux).

### How do I use SFTP to transfer a file?

Type `sftp <username>@<server>` and enter the password at the prompt. \
\
Once you've initiated an SFTP connection there are a few commands you can use to navigate the local machine and remote machine and transfer files between them. Type `help` to see the commands. The few main ones are below.&#x20;

`lpwd` = current directory on the local machine\
`pwd` = current directory on remote machine\
`lcd` = change directory on local machine\
`cd` = change directory on remote machine\
`lls` = local directory listing\
`ls` = remote directory listing\
`get` = download file from remote machine to local machine\
`put` = upload file from local machine to remote machine

### Why use SFTP in my Job?

Well, my main reasoning for using SFTP is for downloading/uploading files from a Linux machine to my local desktop using one of Cerner's front-end FTP repo's for SR's,\
(`ftp3.cerner.com`, `ftp4.cerner.com`). I have used it to quickly transfer files between my local machine and APP/DB nodes as well. PowerShell in Windows 10 has SFTP by default so you can use it there to connect to servers in the CernerASP domain. I prefer the command line SFTP over WinSCP or FileZilla. For transferring files between 2 hosts both on the CernerASP domain, SCP is prefered over SFTP for ease of use, but you could use SFTP if you'd like.&#x20;
