# Committing a transaction to disk

open a new transaction, for subsequent syscalls

mark transaction as done

wait for in-progress syscalls to stop()

(maybe it starts writing blocks, then waits, then writes again if needed)

write descriptor to log on disk w/ list of block #s

write each block from cache to log on disk

wait for all log writes to finish

append the commit record

now cached blocks allowed to go to homes on disk (but not forced)