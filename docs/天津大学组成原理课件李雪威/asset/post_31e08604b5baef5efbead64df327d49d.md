
## Encoding Integers

### Unsigned

B2U(X) = \(\sum_{i=0}^{w-1} x_i \cdot 2^i\)

### Two's Complement

B2T(X) = \(-x_{w-1} \cdot 2^{w-1} + \sum_{i=0}^{w-2} x_i \cdot 2^i\)

Sign Bit

### Two's Complement Examples (w = 5)

-16 8 4 2 1

10 = 0 1 0 1 0

-16 8 4 2 1

-10 = 1 0 1 1 0

8 + 2 = 10

-16 + 4 + 2 = -10

## Unsigned & Signed Numeric Values

| X   | B2U(X) | B2T(X) |
|-----|--------|--------|
| 0000 | 0      | 0      |
| 0001 | 1      | 1      |
| 0010 | 2      | 2      |
| 0011 | 3      | 3      |
| 0100 | 4      | 4      |
| 0101 | 5      | 5      |
| 0110 | 6      | 6      |
| 0111 | 7      | 7      |
| 1000 | 8      | -8     |
| 1001 | 9      | -7     |
| 1010 | 10     | -6     |
| 1011 | 11     | -5     |
| 1100 | 12     | -4     |
| 1101 | 13     | -3     |
| 1110 | 14     | -2     |
| 1111 | 15     | -1     |

### Equivalence

- Same encodings for nonnegative values

### Uniqueness

- Every bit pattern represents unique integer value
- Each representable integer has unique bit encoding

### Expression containing signed and unsigned int: int is cast to unsigned!!

## Sign Extension and Truncation

### Sign Extension

### Truncation

![](img/be2cf0737cec89669e7b18813ea2d3b7_60_0.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_60_1.png)

## Today: Bits, Bytes, and Integers

- Representing information as bits
- Bit-level manipulations
- Integers
  - Representation: unsigned and signed
  - Conversion, casting
  - Expanding, truncating
  - Addition, negation, multiplication, shifting
- Representations in memory, pointers, strings
- Summary

## Unsigned Addition

- Operands: w bits
- True Sum: w+1 bits
- Discard Carry: w bits

![](img/be2cf0737cec89669e7b18813ea2d3b7_62_0.png)

- **Standard Addition Function**
  - Ignores carry output
- **Implements Modular Arithmetic**

s = UAdd_w(u, v) = u + v mod 2^w

![](img/be2cf0737cec89669e7b18813ea2d3b7_62_1.png)

![](img/be2cf0737cec89669e7b18813ea2d3b7_62_2.png)

## Visualizing (Mathematical) Integer Addition

### Integer Addition

- 4-bit integers $u, v$
- Compute true sum
  - Add$_4(u, v)$
- Values increase linearly with $u$ and $v$
- Forms planar surface

### Add$_4(u, v)$

![](img/be2cf0737cec89669e7b18813ea2d3b7_63_0.png)

## Visualizing Unsigned Addition

### Wraps Around

- If true sum ≥ 2^w
- At most once

**True Sum**

**Modular Sum**

![](img/be2cf0737cec89669e7b18813ea2d3b7_64_0.png)

## Two’s Complement Addition

- Operands: w bits
- True Sum: w+1 bits
- Discard Carry: w bits

```text
u
+ v
u + v
TAdd_w(u, v)
```

![](img/be2cf0737cec89669e7b18813ea2d3b7_65_0.png)

### TAdd and UAdd have Identical Bit-Level Behavior

- Signed vs. unsigned addition in C:

  ```c
  int s, t, u, v;
  s = (int) ((unsigned) u + (unsigned) v);
  t = u + v;
  ```

- Will give s == t

![](img/be2cf0737cec89669e7b18813ea2d3b7_65_1.png)

## TAdd Overflow

### Functionality

- True sum requires w+1 bits
- Drop off MSB
- Treat remaining bits as 2’s comp. integer

- 0 111...1
- 0 100...0
- 0 000...0
- 1 011...1
- 1 000...0

**True Sum**

- 2^w-1
- 2^(w-1)-1
- 0
- -2^(w-1)
- -2^w
- PosOver
- NegOver

**TAdd Result**

- 011...1
- 000...0
- 100...0

## Visualizing 2’s Complement Addition

### Values

- 4-bit two’s comp.
- Range from -8 to +7

### Wraps Around

- If sum ≥ 2<sup>w-1</sup>
  - Becomes negative
  - At most once
- If sum < -2<sup>w-1</sup>
  - Becomes positive
  - At most once

![](img/be2cf0737cec89669e7b18813ea2d3b7_67_0.png)

## Characterizing TAdd

- **Functionality**
  - True sum requires *w*+1 bits
  - Drop off MSB
  - Treat remaining bits as 2’s comp. integer

![](img/be2cf0737cec89669e7b18813ea2d3b7_68_0.png)

$$
TAdd_w(u,v)=\begin{cases}
u+v+2^w & u+v<TMin_w\quad\text{(NegOver)}\\
u+v & TMin_w\le u+v\le TMax_w\\
u+v-2^w & TMax_w<u+v\quad\text{(PosOver)}
\end{cases}
$$
