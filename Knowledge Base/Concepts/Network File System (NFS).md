# Network File System (NFS)
## Description
*NFS* is a protocol that enables the transfer of files between distant computers on a network and is available on many systems, including Windows and Linux. Thus, NFS makes file sharing very easy. 

Available drives, files, and folders are referred to as *mounted/mounts* or *shared/shares* and proper permissions should be enabled to prevent unauthorized reading, writing, and *mounting* of drives/files. 

Due to its functionality and commonality on systems, it is also a vulnerable point of attack if not properly secured.

See [Filesystem](../Linux%20Fundamentals/16%20Managing%20Memory%20and%20Disk.md#Filesystem) for more information on the *Linux* filesystem in relation to *NFS*. 

## Commands
- `showmount` &mdash; Show the mounted files on the target
	- `-e or --exports` &mdash; Show the NFS server's export list
- `mount` &mdash; Mount a share to our system
	- e.g., `mount 10.10.10.10:/someShare somedir`
	- Once mounted, you may access the contents through `somedir` on your own system. 