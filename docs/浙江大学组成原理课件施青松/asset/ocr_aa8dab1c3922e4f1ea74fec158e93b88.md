# # Example

+   - Show the binary representation of -0.75 in IEEE single precision format

+   - Decimal representation: -0.75 = - 3/4 = - 3/2²

+   - Binary representation: - 0.11 = - 1.1 • 2⁻¹

+   - Floating point

α (-1)^sign • (1 + fraction) • 2^exponent - bias

α (-1)^sign =-1,so Sign = 1

α 1 + fraction = 1.1,so Significand=.1

α exponent -127 =-1,so Exponent=(-1 + 127) = 126

| 31 | 30 ...... 23 | 22 ...... 0 |
|---|---|---|
| 1 | 0111 1110 | 100 0000 0000 0000 0000 0000 |

1 bit 8 bits 23 bits

| 31 | 30 ...... 20 | 19 ...... 0 |
|---|---|---|
| 1 | 011 1111 1110 | 1000 0000 0000 0000 0000 |

1bit 11 bits 20 bits

| 0000 0000 0000 0000 0000 0000 0000 0000 |