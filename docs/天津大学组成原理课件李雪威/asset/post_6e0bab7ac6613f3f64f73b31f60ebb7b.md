

## Counting Down with Unsigned

- **Proper way to use unsigned as loop index**
  ```c
  unsigned cnt;
  for (i = cnt-2; i < cnt; i--)
      ...
  ```
- **See Robert Seacord, _Secure Coding in C and C++_**
  - C standard guarantees that unsigned addition will behave like modular arithmetic
  - `0 - 1 → UMax`
- **Even better**
  ```c
  size_t i;
  for (i = cnt-2; i < cnt; i--)
      ...
  ```
  - Data type `size_t` defined as unsigned value with length = word size
  - Code will work even if `cnt = UMax`
  - What if `cnt` is signed and `< 0`?

## Why Should I Use Unsigned? (cont.)

- **Do Use When Performing Modular Arithmetic**
  - Multiplication arithmetic
- **Do Use When Using Bits to Represent Sets**
  - Logical right shift, no sign extension

## Today: Bits, Bytes, and Integers

- Representing information as bits
- Bit-level manipulations
- Integers
  - Representation: unsigned and signed
  - Conversion, casting
  - Expanding, truncating
  - Addition, subtraction, multiplication, shifting
  - Summary
- **Representations in memory, pointers, strings**

## Byte-Oriented Memory Organization

![](img/be2cf0737cec89669e7b18813ea2d3b7_45_0.png)

- **Programs refer to data by address**
  - Conceptually, envision it as a very large array of bytes
    - In reality, it’s not, but can think of it that way
  - An address is like an index into that array
    - and, a pointer variable stores an address
- **Note: system provides private address spaces to each “process”**
  - Think of a process as a program being executed
  - So, a program can clobber its own data, but not that of others

## Machine Words

- **Any given computer has a “Word Size”**
  - Normal size of integer-valued data
    - and of addresses
  - Until recently, most machines used 32 bits (4 bytes) as word size
    - limits addresses to 4G (2³²) bytes
  - Increasingly, machines have 64-bit word size
    - Potentially, could have 18 EB (exabytes) of addressable memory
    - That’s 18.4 × 10¹⁸
  - Machines still support multiple data formats
    - Fractions or multiples of word size
    - Always integral number of bytes

## Word-Oriented Memory Organization

- **Addresses Specify Byte Locations**
  - Address of first byte in word
  - Addresses of successive words differ by 4 (32-bit) or 8 (64-bit)

![](img/be2cf0737cec89669e7b18813ea2d3b7_45_1.png)

## Example Data Representations

| C Data Type | Typical 32-bit | Typical 64-bit | MIPS64 |
|---|---|---|---|
| char | 1 | 1 | 1 |
| short | 2 | 2 | 2 |
| int | 4 | 4 | 4 |
| long | 4 | 8 | 8 |
| float | 4 | 4 | 4 |
| double | 8 | 8 | 8 |
| long double | - | - | 10/16 |
| pointer | 4 | 8 | 8 |

## Byte Ordering

- So, how are the bytes within a multi-byte word ordered in memory?
- Conventions
  - Big Endian: Sun, PPC Mac, Internet
    - Least significant byte has highest address
  - Little Endian: x86, ARM processors running Android, iOS, and Windows
    - Least significant byte has lowest address

## Byte Ordering Example

- Example
  - Variable x is a 4-byte value of 0x1234567
  - Address given by &x is 0x100

Big Endian

| 0x100 | 0x101 | 0x102 | 0x103 |
|-------|-------|-------|-------|
| 12 | 34 | 56 | 78 |

Little Endian

| 0x100 | 0x101 | 0x102 | 0x103 |
|-------|-------|-------|-------|
| 78 | 56 | 34 | 12 |

## Representing Integers

int A = 15213;

int B = -15213;

Two's complement representation

## Examining Data Representations

- Code to Print Byte Representation of Data
  Casting pointer to unsigned char * allows treatment as byte array

```c
typedef unsigned char *byte_pointer;

void show_bytes(byte_pointer start, size_t len) {
    size_t i;
    for (i = 0; i < len; i++)
    fprintf("%.2x", start[i]);    // Line A
    printf("\n");
}
```

- Print directives:
  - %p: Print pointer
  - %x: Print hexadecimal
  - %lx: Print hexadecimal

## show_bytes Execution Example

```c
int a = 15213;
printf("int a = %d\n", a);
show_bytes((byte_pointer) &a, sizeof(int));
```

Result (Linux x86-64):
int a = 15213;
69 3d 00 00
0xf7fff7c4: 3d
0xf7fff7c5: 69
0xf7fff7c6: 00
0xf7fff7c7: 00

