
## Two-Level Directory

- A master directory and one directory for each user, master directory contains entry for each user, provides address and access control information
- Each user directory is a simple list of files for that user
- Create a separate directory for each user.

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_715_0.png)

- Different users may have files with the same name
- Efficient searching
- Path name
- No grouping capability

## Tree-Structured Directories (1/3)

- Master directory with user directories underneath it
- Each user directory may have subdirectories and files as entries

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_716_0.png)

## Tree-Structured Directories (2/3)

- Efficient searching
- convenient Naming
- Grouping Capability
- Current directory (working directory)
  - cd /spell/mail/prog
  - type list
- Absolute or relative path name
- Creating a new file is done in current directory.
- Delete a file
  - rm <file-name>

## Tree-Structured Directories (3/3)

Creating a new subdirectory is done in current directory.

mkdir <dir-name>

Example: if in current directory /mail

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_718_0.png)

mkdir count

Deleting a subdirectory
- deleting a empty directory.
- deleting all files and subdirectories that it contains.

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_718_1.png)

## Acyclic-Graph Directories (1/2)

- Have shared subdirectories and files.

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_719_0.png)

## General Graph Directory

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_721_0.png)

## How do we guarantee no cycles?

- Allow only links to file not subdirectories.
- Garbage collection.
- Every time a new link is added use a cycle detection algorithm to determine whether it is OK.

## 10.4 File System Mounting

- A file system must be **mounted** before it can be accessed.
- **The mount procedure**
  - The operating system is given the _name of the device_, and the _location_ within the file structure at which to attach the file system.
  - The operating system _verifies_ that the device contains a valid file system by asking the _device driver_ to read the device directory and verifying that the directory has the expected format.
  - The operating system _notes_ in its directory structure that a file system is mounted at the specified **mount point**.

## Example

Existing

Unmounted Partition

Mount point: users

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_723_0.png)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_723_1.png)

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_723_2.png)

## 10.5 File Sharing

- Sharing of files on multi-user systems is desirable.
- Sharing may be done through a *protection* scheme.
- On distributed systems, files may be shared across a network.
  - ftp
  - DFS: distributed file system
  - WWW: World Wide Web
- Network File System (NFS) is a common distributed file-sharing method.

## File Sharing – Multiple Users

- **User IDs** identify users, allowing permissions and protections to be per-user
- **Group IDs** allow users to be in groups, permitting group access rights

## File Sharing – Remote File Systems

- Uses networking to allow file system access between systems
  - Manually via programs like FTP
  - Automatically, seamlessly using distributed file systems
  - Semi automatically via the world wide web
- Client-server model allows clients to mount remote file systems from servers
  - Server can serve multiple clients
  - Client and user-on-client identification is insecure or complicated
  - NFS is standard UNIX client-server file sharing protocol
  - CIFS is standard Windows protocol
  - Standard operating system file calls are translated into remote calls
- Distributed Information Systems (distributed naming services) such as LDAP, DNS, NIS, Active Directory implement unified access to information needed for remote computing
