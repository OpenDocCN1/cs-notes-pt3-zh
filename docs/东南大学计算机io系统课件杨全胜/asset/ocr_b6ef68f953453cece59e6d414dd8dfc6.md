# 5.2 Structure and pins of 8254

# Operation and Command

+   Method of read data from T/C

+   Read current data by Read-Back Command (A1A0=11)

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
|---|---|---|---|---|---|---|---|
| 1 | 1 | COUNT | STATUS | CNT 2 | CNT 1 | CNT 0 | 0 |

D5: 0 = Latch count of selected counter(s)

D4: 0 = Latch status of selected counter(s)

D3: 1 = Select counter 2

D2: 1 = Select counter 1

D1: 1 = Select counter 0

D0: Reserved for future expansion; must be 0

+   Count latch command can only latch one counter

+   Read-back command can latch multiple counter at the same time