# Fixed-Length Records

+   - Simple approach:
+     - Store record *i* starting from byte *n * (i − 1)*, where *n* is the size of each record.
+     - Record access is simple but records may cross blocks
+       - Modification: do not allow records to cross block boundaries

+   - Deletion of record *i*: alternatives:
+     - move records *i + 1, …, n* to *i, …, n − 1*
+     - move record *n* to *i*
+     - do not move records, but link all free records on a free list

|  | 10101 | Srinivasan | Comp. Sci. | 65000 |
| record 0 |  |  |  |  |
| record 1 | 12121 | Wu | Finance | 90000 |
| record 2 | 15151 | Mozart | Music | 40000 |
| record 3 | 22222 | Einstein | Physics | 95000 |
| record 4 | 32343 | El Said | History | 60000 |
| record 5 | 33456 | Gold | Physics | 87000 |
| record 6 | 45565 | Katz | Comp. Sci. | 75000 |
| record 7 | 58583 | Califieri | History | 62000 |
| record 8 | 76543 | Singh | Finance | 80000 |
| record 9 | 76766 | Crick | Biology | 72000 |
| record 10 | 83821 | Brandt | Comp. Sci. | 92000 |
| record 11 | 98345 | Kim | Elec. Eng. | 80000 |