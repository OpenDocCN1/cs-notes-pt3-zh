# # I type Instruction & Data stream

Sw $t0, 200($s2)

op(6)
rs(5)
rt(5)
Immediate data

bit21-25
bit16-20
bit0-15
16

control

Read reg. address1
Read data1
Read reg. address2
Registers
Write reg. address
Read data2
Write data

RegWrite

Sign extend
32

3
ALU operation

ALU
ALU result
Zero

32bits data

MenWrite
address
Read data
Data
Memory
Write data
MenRead

lw $t0, 200($s2)
if $s2=1000, it will load word in element number 1200 to $t0