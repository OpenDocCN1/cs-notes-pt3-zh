# # Typical 80x86 instruction format

a. JE EIP + displacement

b. CALL

c. MOV EBX, [EDI + 45]

d. PUSH ESI

e. ADD EAX, #6765

f. TEST EDX, #42

| 4 | 4 | 8 |
|---|---|---|
| JE | Condition | Displacement |

| 8 | 32 |
|---|---|
| CALL | Offset |

| 6 | 1 1 | 8 | 8 |
|---|---|---|---|
| MOV | d w | r-m postbyte | Displacement |

| 5 | 3 |
|---|---|
| PUSH | Reg |

| 4 | 3 1 | 32 |
|---|---|---|
| ADD | Reg w | Immediate |

| 7 | 1 | 8 | 32 |
|---|---|---|---|
| TEST | w | Postbyte | Immediate |

![](bbox=[0.536, 0.194, 0.579, 0.231])

![](bbox=[0.831, 0.323, 0.897, 0.36])

![](bbox=[0.604, 0.452, 0.667, 0.489])

![](bbox=[0.337, 0.609, 0.404, 0.646])

![](bbox=[0.831, 0.71, 0.897, 0.747])

![](bbox=[0.894, 0.855, 0.96, 0.892])