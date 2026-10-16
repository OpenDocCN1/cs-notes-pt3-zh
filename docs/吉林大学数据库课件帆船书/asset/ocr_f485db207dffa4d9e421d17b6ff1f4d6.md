# Bitmap Indices (Cont.)

In its simplest form a bitmap index on an attribute has a bitmap for each value of the attribute

+   - Bitmap has as many bits as records
+   - In a bitmap for value v, the bit for a record is 1 if the record has the value v for the attribute, and is 0 otherwise

| record number | ID | gender | income_level |
|---|---|---|---|
| 0 | 76766 | m | L1 |
| 1 | 22222 | f | L2 |
| 2 | 12121 | f | L1 |
| 3 | 15151 | m | L4 |
| 4 | 58583 | f | L3 |

Bitmaps for gender
m 10010
f 01101

Bitmaps for income_level
L1 10100
L2 01000
L3 00001
L4 00010
L5 00000