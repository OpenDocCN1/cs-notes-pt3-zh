# # Layered File System

application programs

System calls for file operations

logical file system

Manages metadata information,
Manages the directory structure,
Maintains file structure via FCB.

file-organization module

Translate logical block addresses to
physical block addresses.
Free-space manager.

basic file system

Issue generic commands to the appropriate
device driver to read and write physical
blocks on the disk.

I/O control

Device driver and interrupt handlers.
Transfer information between the main
memory and the disk system.

devices