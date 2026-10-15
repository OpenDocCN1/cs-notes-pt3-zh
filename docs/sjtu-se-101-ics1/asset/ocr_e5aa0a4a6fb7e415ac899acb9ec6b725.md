# Direct-mapped cache simulation

Example

M=16 byte addresses

B=2 bytes/block, S=4 sets, E=1 entry/set

t=1 s=2 b=1
x xx x

Address trace (reads):

0 [0000] 1 [0001] 13 [1101] 8 [1000] 0 [0000]

miss hit miss miss miss

(5) 0 [0000] (miss)

| set | v | tag | data |
|---|---|---|---|
| 0 | 1 | 0 | m[0]m[1] |
| 1 | 0 |  |  |
| 2 | 1 | 1 | m[12]m[13] |
| 3 | 0 |  |  |