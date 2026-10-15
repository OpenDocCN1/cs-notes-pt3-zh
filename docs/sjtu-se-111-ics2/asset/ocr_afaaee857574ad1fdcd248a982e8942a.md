# Redirection

dup2(4,1)

Descriptor table
(one table per process)

fd0
fd1
fd2
fd3
fd4
fd5
fd6
fd7

open file table
(shared by all process)

file A

file pos
refcnt = 0
...

file B

file pos
refcnt = 2
...

V-node table
(shared by all processes)

file A

File access
File size
File type
...

file B

File access
File size
File type
...