# LOOKUP in a Directory

| File name | Inode num | File (inode) | Block num | Disk Block |

```
1  procedure LOOKUP (character string filename, integer dir) returns integer
2      block instance b
3      inode instance i ← INODE_NUMBER_TO_INODE (dir)
4      if i.type ≠ DIRECTORY then return FAILURE
5      for offset from 0 to i.size − 1 do
6          b ← INODE_NUMBER_TO_BLOCK (offset, dir)
7          if STRING_MATCH (filename, b) then
8              return INODE_NUMBER (filename, b)
9          offset ← offset + BLOCKSIZE
10     return FAILURE
```

+   - Name compare method: STRING_MATCH
+   - LOOKUP("program", dir) will return 10
+   - Next Problem: too many files