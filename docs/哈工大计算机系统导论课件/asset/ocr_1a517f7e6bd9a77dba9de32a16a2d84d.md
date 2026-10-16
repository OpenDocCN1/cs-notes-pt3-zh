# 压缩BCD码加法调整指令——AAA

# AAA(ASCII adjust after addition)

**操作内容：**

AL ← 将AL中的加法和调整为□压缩的BCD码(AL□4位清0);

AH ← AH + 调整产生的进位

**用法：**

该指令跟在以al为目的操作数的add或adc指令后，如果调整产生进位，CF = AF = 1,否则CF = AF =0.