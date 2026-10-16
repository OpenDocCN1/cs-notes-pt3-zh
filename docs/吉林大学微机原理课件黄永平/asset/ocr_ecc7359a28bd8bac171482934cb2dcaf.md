# (3). 调整指令

# ASCII Adjust after Addition

# (c)非压缩BCD码加法调整指令 AAA

; AL₇ AL₆ AL₅ AL₄ AL₃ AL₂ AL₁ AL₀

清0

>9 或 AF = 1

+ 6 并且 AH ← AH+1 并且 CF ← 1

非压缩BCD码 + 非压缩BCD码 → 非压缩BCD码

AAA调整

结果在AH AL中，以非压缩BCD码形式存贮