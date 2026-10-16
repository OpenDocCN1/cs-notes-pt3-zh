# 7.4 16550 UART

# Interrupt Identification Register (IIR)

A2A1A0=010 (Read)

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
|---|---|---|---|---|---|---|---|
|  |  | 0 | 0 | ID2 | ID1 | ID0 | IP |

01-Enable FIFO but no use
11-Enable FIFO

Identify the highest priority interrupt pending. ID2 used in FIFO mode only

0-an interrupt is pending
1- no interrupt is pending