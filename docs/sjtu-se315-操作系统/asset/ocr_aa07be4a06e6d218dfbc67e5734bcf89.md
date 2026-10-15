# FAT Root Folder

+   - FAT Root Folder Structure

| Root Folder Entry | Size | Description |
|---|---|---|
| Name | 11B | Name in 8.3 format |
| Attribute Byte | 1B | Information about entry (e.g. archive, system, hidden, and read-only) |
| Creation Time and Date | 5B | Time and date file was create |
| Last Access Date | 2B | Date file was last accessed |
| Last Modification Time and Date | 4B | Time and data file was last modified |
| First Cluster | 2B | Starting cluster number in the file allocation table |
| File Size | 4B | Size of the file |