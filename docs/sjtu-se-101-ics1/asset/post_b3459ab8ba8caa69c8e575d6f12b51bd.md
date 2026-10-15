
## Dynamic Range (Denormalized numbers)
- s exp frac E Value
- 0 0000 000 -6 0
- 0 0000 001 -6 1/8*1/64 = 1/512
- 0 0000 010 -6 2/8*1/64 = 2/512
- ...
- 0 0000 110 -6 6/8*1/64 = 6/512
- 0 0000 111 -6 7/8*1/64 = 7/512

## Dynamic Range
- s exp frac E Value
- 0 0001 000 -6 8/8*1/64 = 8/512
- 0 0001 001 -6 9/8*1/64 = 9/512
- ...
- 0 0110 110 -1 14/8*1/2 = 14/16
- 0 0110 111 -1 15/8*1/2 = 15/16
- 0 0111 000 0 8/8*1 = 1
- 0 0111 001 0 9/8*1 = 9/8

## Dynamic Range (Denormalized numbers)
- s exp   frac   E   Value
- 0 0111   010   0   10/8*1 = 10/8
- ...
- 0 1110   110   7   14/8*128 = 224
- 0 1110   111   7   15/8*128 = 240
- 0 1111   000   n/a   inf

## Distribution of Representable Values
- 6-bit IEEE-like format
  - K = 3 exponent bits
  - n = 2 significand bits
  - Bias is 3
- Notice how the distribution gets denser toward zero.

## Distribution of Representable Values
![](img/b3f8b91675c485f1e811aa092ebbf3d4_734_0.png)

## Interesting Numbers

| Description | exp | frac | Single Precision |  | Double Precision |  |
|---|---|---|---|---|---|---|
|  |  |  | Value | Decimal | Value | Decimal |
| Zero | 00...00 | 0...00 | 0 | 0.0 | 0 | 0.0 |
| Smallest denorm. | 00...00 | 0...01 | $2^{-23} \times 2^{-126}$ | $1.4 \times 10^{-45}$ | $2^{-52} \times 2^{-1022}$ | $4.9 \times 10^{-324}$ |
| Largest denorm. | 00...00 | 1...11 | $(1-\epsilon) \times 2^{-126}$ | $1.2 \times 10^{-38}$ | $(1-\epsilon) \times 2^{-1022}$ | $2.2 \times 10^{-308}$ |
| Smallest norm. | 00...01 | 0...00 | $1 \times 2^{-126}$ | $1.2 \times 10^{-38}$ | $1 \times 2^{-1022}$ | $2.2 \times 10^{-308}$ |
| One | 01...11 | 0...00 | $1 \times 2^{0}$ | 1.0 | $1 \times 2^{0}$ | 1.0 |
| Largest norm. | 11...10 | 1...11 | $(2-\epsilon) \times 2^{127}$ | $3.4 \times 10^{38}$ | $(2-\epsilon) \times 2^{1023}$ | $1.8 \times 10^{308}$ |

## Rounding Mode
- Round down:
  - rounded result is close to but no greater than true result.
- Round up:
  - rounded result is close to but no less than true result.

## Rounding Mode

| Mode | 1.40 | 1.60 | 1.50 | 2.50 | -1.50 |
|---|---|---|---|---|---|
| Round-to-Even | 1 | 2 | 2 | 2 | -2 |
| Round-toward-zero | 1 | 1 | 1 | 2 | -1 |
| Round-down | 1 | 1 | 1 | 2 | -2 |
| Round-up | 2 | 2 | 2 | 3 | -1 |

## Round-to-Even
- Default Rounding Mode
  - Hard to get any other kind without dropping into assembly
  - All others are statistically biased
    - Sum of set of positive numbers will consistently be over- or under- estimated

## Round-to-Even
- Applying to Other Decimal Places
  - When exactly halfway between two possible values
    - Round so that least significant digit is even
  - E.g., round to nearest hundredth
    1.2349999    1.23    (Less than half way)
    1.2350001    1.24    (Greater than half way)
    1.2350000    1.24    (Half way—round up)
    1.2450000    1.24    (Half way—round down)

## Rounding Binary Number
- "Even" when least significant bit is 0
- Half way when bits to right of rounding position = 100...₂

| Value | Binary | Rounded | Action | Round Decimal |
|---|---|---|---|---|
| 2 3/32 | 10.00011 | 10.00 | Down | 2 |
| 2 3/16 | 10.0011 | 10.01 | Up | 2 1/4 |
| 2 7/8 | 10.111 | 11.00 | Up | 3 |
| 2 5/8 | 10.101 | 10.10 | Down | 2 1/2 |

## Floating-Point Operations
- Conceptual View
  - First compute exact result
  - Make it fit into desired precision
    - Possibly overflow if exponent too large
    - Possibly round to fit into `frac`

## FP Multiplication
- Operands
  $(-1)^{s1} M1\ 2^{E1}$
  $(-1)^{s2} M2\ 2^{E2}$
- Exact Result
  $(-1)^{s} M\ 2^{E}$
  - Sign $s$: $s1 ^ s2$
  - Significand $M$: $M1 * M2$
  - Exponent $E$: $E1 + E2$

## FP Multiplication
- Fixing
  - If M ≥ 2, shift M right, increment E
  - If E out of range, overflow
  - Round M to fit `frac` precision
