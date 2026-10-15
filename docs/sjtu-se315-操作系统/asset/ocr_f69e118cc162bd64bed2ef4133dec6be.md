# Linux’s ext3’s Journaling

case study of the details required to add logging to a file system

Stephen Tweedie 2000 talk transcript "EXT3, Journaling Filesystem"

ext3 adds a log to ext2, a previous xv6-like log-less file system

has many modes, start with "journaled data"

log contains both metadata and file content blocks