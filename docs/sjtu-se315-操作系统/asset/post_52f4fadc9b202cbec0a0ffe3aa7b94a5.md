
## How does recovery work?

+   1. find the start and end of the log
+      log "superblock" at start of log file
+      log superblock has start offset and seq# of first transaction
+      scan until bad record or not the expected seq #
+      go back to last commit record
+      crash during commit -> last transaction ignored during recovery
+   2. replay all blocks through last completed xaction, in log order

what if block after last valid log block looks like a log descriptor?

+   - perhaps left over from previous use of log? (**seq...**)
+   - perhaps some file data happens to look like a descriptor? (**magic #...**)

when can ext3 free a transaction's log space?

after cached blocks have been written to FS on disk
free == advance log superblock's start pointer/seq

## Question

what if not enough free space in log for a syscall?

suppose we start adding syscall's blocks to T2

half way through, realize T2 won't fit on disk

we cannot commit T2, since syscall not done

can we free T1 to free up log space?

maybe not, due to previous issue, T2 maybe dirtied a block in T1

deadlock!

## Solution: Reservations

syscall pre-declares how many block of log space it might need

block the sycall from starting until enough free space

may need to commit open transaction, then free older transaction

OK since reservations mean all started sys calls can complete + commit

## Durability of ext3

ext3 not as immediately durable as xv6
creat() returns -> maybe data is not on disk! crash will undo it.
need fsync(fd) to force commit of current transaction, and wait
would ext3 have good performance if commit after every sys call?
would log many more blocks, no absorption
10 ms per syscall, rather than 0 ms
(“Rethink the Sync” [OSDI’06] addresses this problem)

## Issues with ext3

disks usually have write caches and re-order writes, for performance

sometimes hard to turn off (the disk lies)

often with re-ordering enabled for speed, out of ignorance

bad news if disk writes commit block before preceding stuff

then recovery replays "descriptors" with random block #s!

and writes them with random content!

how to solve this problem?

using checksum

## Ordered Mode vs Journaled Mode

journaling file content is slow, every data block written twice

perhaps not needed to keep FS internally consistent

can we just lazily write file content blocks?

no:

+   - if metadata updated first, crash may leave file pointing to blocks with someone else's data

ext3 ordered mode:

+   - write content block to disk before committing inode w/ new block #
+   - thus won't see stale data if there's a crash

most people use ext3 ordered mode

## Xv6 vs. ext3

does ext3 fix the xv6 log performance problems?

+   - only one transaction at a time -- yes
+   - synchronous write to on-disk log -- yes, but 5-second window
+   - tiny update -> whole block write -- yes (indirectly)
+   - synchronous writes to home locations after commit -- yes

ext3 very successful

+   - but: no checksum -- ext4
+   - but: not efficient for applications that use fsync()

## Questions

+   - In commit_trans, there are three steps
+     - Write_head: log “done” to disk
+     - Install_trans: checkpointing metadata to home location
+   - Can these two operations get reordered or mixed together?
+   - How can we make then reordered?

```
void
commit_trans(void)
{
    if (log.lh.n > 0) {
        write_head();    // Write header to disk -- the real commit
        install_trans(); // Now install writes to home locations
        log.lh.n = 0;
        write_head();    // Erase the transaction from the log
    }
}
```

## T2 starts while T1 is committing to log on disk

+   - what if syscall in T2 wants to write block in prev xaction?
+   - can't be allowed to write buffer that T1 is writing to disk
+     - then new syscall's write would be part of T1
+     - crash after T1 commit, before T2, would expose update
+   - T2 gets a separate copy of the block to modify
+     - T1 holds onto old copy to write to log
+   - are there now *two* versions of the block in the buffer cache?
+     - no, only the new one is in the buffer cache, the old one isn't
+   - does old copy need to be written to FS on disk?
+     - no: T2 will write it
