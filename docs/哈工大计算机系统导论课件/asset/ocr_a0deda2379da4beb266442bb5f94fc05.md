# IEEE 754标准

规格化数：+/-1.xxxxxxxxxx two x 2Exponent

规定：小数点前总是“1”，故可隐含表示。

# Single Precision（单精度）：

| S | Exponent | Significand |
|---|---|---|
| 1 bit | 8 bits | 23 bits |

+   - Sign bit: 1 表示 negative；0 表示 positive

+   - Exponent（阶码）：全0和全1用来表示特殊值！

+   - SP规格化阶码范围为0000 0001 (-126) ~ 1111 1110 (127)

+   - bias为127 (single), 1023 (double) 为什么用127？若用128，则阶码范围为多少？

+   - Significand（部分尾数）：

+   - 规格化尾数最高位总是1，所以隐含表示，省1位

+   - 1 + 23 bits（single），1 + 52 bits（double）

SP: (-1)^S x (1 + Significand) x 2^(Exponent-127) 0000 0001 (-127) ~ 1111 1110 (126)

DP: (-1)^S x (1 + Significand) x 2^(Exponent-1023)