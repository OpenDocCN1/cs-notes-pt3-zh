# # Signed Power-of-2 Divide with Shift

+   - **Quotient of Signed by Power of 2**
+     - `x >> k` gives ⌊x / 2^k⌋
+     - Uses arithmetic shift
+     - Rounds wrong direction when **u < 0**

![](bbox=[0.069, 0.393, 0.933, 0.691])

|  | Division | Computed | Hex | Binary |
|---|---:|---:|---|---|
| y | -15213 | -15213 | C4 93 | 11000100 10010011 |
| y >> 1 | -7606.5 | -7607 | E2 49 | 11100010 01001001 |
| y >> 4 | -950.8125 | -951 | FC 49 | 11111100 01001001 |
| y >> 8 | -59.4257813 | -60 | FF C4 | 11111111 11000100 |