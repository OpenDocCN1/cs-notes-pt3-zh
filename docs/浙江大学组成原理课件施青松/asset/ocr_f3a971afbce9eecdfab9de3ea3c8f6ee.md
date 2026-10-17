# lw and sw

From state 1

(Op = 'LW') or (Op = 'SW')

Memory address computation

ALUSrcA = 1
ALUSrcB = 10
ALUOp = 00

2

(Op = LW)

(Op = SW)

3

Memory
access

MemRead
IorD = 1

5

Memory
access

MemWrite
IorD = 1

4

Write-back step

RegWrite
MemtoReg = 1
RegDst = 0

To state 0
(Figure 5.32)