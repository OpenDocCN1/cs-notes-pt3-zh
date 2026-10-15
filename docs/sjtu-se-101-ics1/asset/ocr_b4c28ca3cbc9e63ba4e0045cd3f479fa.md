# Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

Address trace (reads):
0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

| v | tag | data |
|---|---|---|
| 0 |  |  |
| 0 |  |  |
| 0 |  |  |
| 0 |  |  |

![](bbox=[0.7, 0.24, 0.95, 0.32])