
## 10.1 File Concept

- Contiguous logical address space.
- A uniform logical view of information storage.
- A file is a named collection of related information that is recorded on secondary storage.
- Commonly, files represent programs and data.
  - Data files
    - numeric
    - character
    - binary
  - Program
    - source
    - object
- files may be free form or may be formatted rigidly.
- The information in a file is defined by its creator.

## File Attributes

- **Name** – only information kept in human-readable form.
- **Identifier** – non-human-readable name for the file, a unique number that identifies the file within the system.
- **Type** – needed for systems that support different types.
- **Location** – a pointer to the location of the file on device.
- **Size** – current size of the file.
- **Protection** – access-control information, controls who can do reading, writing, executing.
- **Time, date, and user identification** – data for protection, security, and usage monitoring.
- Information about files are kept in the directory structure, which is maintained on the disk.

## File Operations (1/2)

File is an abstract data type

- **Create** – find space, make entry in directory for the file.
- **Write** – file name, information to be written. *write* ptr.
- **Read** – file name, position in memory. *read* pointer.
- **Reposition** within file – file seek, not need I/O.
- **Delete** – name, release file space, erase directory entry.
- **Truncate** – reset length to 0, release file space.
- These primitive operations may be combined to perform other file operations.

## File Operations (2/2)

- Open-file table
- Open(*Fᵢ*) – search the directory structure on disk for entry *Fᵢ*, and move the content of entry to open-file table. Return a pointer to the entry in the open-file table
- Close (*Fᵢ*) – move the content of entry *Fᵢ* in open-file table to directory structure on disk.
- Several users may open the file at the same time. Two levels of internal tables:
  - Process open-file table, a per-process table, tracks all files a process has open.
  - System open-file table, a system-wide table, contains process-independent information, such as file location on disk, access dates, file size.
- information associated with an open file: file pointer, file open count, disk location of the file, access rights.

## Information associated with an Open File

Several pieces of data are needed to manage open files:

- **File pointer**: pointer to last read/write location, per process that has the file open
- **File-open count**: counter of number of times a file is open – to allow removal of data from open-file table when last processes closes it
- **Disk location of the file**: cache of data access information
- **Access rights**: per-process access mode information

## Open File Locking

- Provided by some operating systems and file systems
- Mediates(调停) access to a file
- Shared lock and exclusive lock (similar to reader lock, writer lock)
- Mandatory(强制的) or advisory(劝告的):
  - Mandatory – access is denied depending on locks held and requested
  - Advisory – processes can find status of locks and decide what to do

## File types

| file type | usual extension | function |
|---|---|---|
| executable | exe, com, bin or none | read to run machine-language program |
| object | obj, o | compiled, machine language, not linked |
| Source code | c, cpp, java, psa, asm, a | source code in various languages |
| Batch | bat, sh | commands to the command interpreter |
| text | txt, doc | textual data, documents |
| Word processor | wp, tex, rrf, doc | various word-processor formats |
| library | lib, a, so, dll, mpeg, mov, rm | libraries of routines for programmers |
| Print or view | arc, zip, tar mpeg, mov, rm | ASCII or binary file in a format for printing or viewing |
| archive | arc, zip, tar | related files grouped into one file, sometimes compressed, for archiving or storage |
| multimedia | mpeg, mov, rm | binary file containing audio or A/V information |
