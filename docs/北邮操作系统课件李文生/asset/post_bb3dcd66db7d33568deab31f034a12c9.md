
## File Sharing – Failure Modes

- Remote file systems add new failure modes, due to network failure, server failure
- Recovery from failure can involve state information about status of each remote request
- Stateless protocols such as NFS include all information in each request, allowing easy recovery but less security

## File Sharing – Consistency Semantics

Consistency semantics specify how multiple users are to access a shared file simultaneously

- Similar to Ch 6 process synchronization algorithms
  - Tend to be less complex due to disk I/O and network latency for remote file systems
- Andrew File System (AFS) implemented complex remote file sharing semantics
- Unix file system (UFS) implements:
  - Writes to an open file visible immediately to other users of the same open file
  - Sharing file pointer to allow multiple users to read and write concurrently
- AFS has session semantics
  - Writes only visible to sessions starting after the file is closed

## 10.6 Protection

- **File owner/creator should be able to control:**
  - what can be done
  - by whom
- **Types of access**
  - **Read**: read from the file
  - **Write**: write or rewrite the file
  - **Execute**: load the file into memory and execute it
  - **Append**: write new information at the end of the file
  - **Delete**: delete the file and free its space for possible reuse
  - **List**: list the name and attributes of the file
  - Other operations, such as **renaming**, **copying**, or **editing** the file, may also be controlled.

## Access control (1/2)

- Mode of access: **read, write, execute**
- Access-control list (ACL): associates with each file and specifies the user name and the types of access allowed for each user.
- Three classes of users
  - **Owner**: the user who created the file.
  - **Group**: a set of users who are sharing the file and need similar access.
  - **Universe (Public)**: all other users in the system.
- Access-control information
  - User access: RWX (111 – 7)
  - Group access: RW– (110 – 6)
  - Public access: ––X (001 – 1)

## Access control (2/2)

- Ask manager to create a group (unique name), say G, and add some users to the group.
- For a particular file (say game) or subdirectory, define an appropriate access.

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_731_0.png)

- Change user’s access methods
  chmod go -RW file
- Attach a group to a file
  chgrp G game.

## A Sample UNIX Directory Listing

| permissions | links | owner | group | size | date | name |
|---|---|---|---|---|---|---|
|-rw-rw-r-- | 1 | pbg | staff | 31200 | Sep 3 08:30 | intro.ps |
|drwx------ | 5 | pbg | staff | 512 | Jul 8 09:33 | private/ |
|drwxrwxr-x | 2 | pbg | staff | 512 | Jul 8 09:35 | doc/ |
|drwxrwx--- | 2 | pbg | student | 512 | Aug 3 14:13 | student-proj/ |
|-rw-r--r-- | 1 | pbg | staff | 9423 | Feb 24 2003 | program.c |
|-rwxr-xr-x | 1 | pbg | staff | 20471 | Feb 24 2003 | program |
|drwx--x--x | 4 | faculty | faculty | 512 | Jul 31 10:31 | lib/ |
|drwx------ | 3 | staff | staff | 1024 | Aug 29 06:52 | mail/ |
|drwxrwxrwx | 3 | pbg | staff | 512 | Jul 8 09:35 | test/ |

## Windows XP Access-control List Management

![](img/9321d6c42b8369e67ceb1f1d7e27b09c_733_0.png)

## Homework (page 408)

- 10.1
- 10.2
- 10.9

## Supplement:
Overview of File Management

- **File Management**
  - File management system is considered part of the operating system
  - Input to applications is by means of a file
  - Output is saved in a file for long-term storage
- **File Management System**
  - The way a user of application may access files
  - Programmer does not need to develop file management software

## Supplement:
Objectives for a File Management System

- Meet the data management needs and requirements of the user
- Guarantee that the data in the file are valid
- Optimize performance
- Provide I/O support for a variety of storage device types
- Minimize or eliminate the potential for lost or destroyed data
- Provide a standardized set of I/O interface routines
- Provide I/O support for multiple users
