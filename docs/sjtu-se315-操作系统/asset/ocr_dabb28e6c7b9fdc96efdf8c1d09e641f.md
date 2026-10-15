# Reader — Writer Locks using Monitors

Note: Implement Reader/Writer Locks as an abstractions, not as an integrated part of code

Central Questions:

+   Shared Data? NumReaders, NumWriters

Ordering Constraints?

+   readerStart must wait if there are writers
+   writerStart must wait if there are readers or writes

How many Condition Variables?

+   One: condRW (no readers or writers)