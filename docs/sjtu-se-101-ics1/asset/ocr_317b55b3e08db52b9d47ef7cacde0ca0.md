# Set Associative Cache Simulation

Example

M=16 byte addresses

B=2 bytes/block, S=2 sets, E=2 entry/set

Address trace (reads):
0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

| t=2 | s=1 | b=1 |
| xx | x | x |

| set | v | tag | data |
| 0 | 0 |  |  |
| 0 | 0 |  |  |
| 1 | 0 |  |  |
| 1 | 0 |  |  |