
## Logical Operations in C

- Logical Operators
  - &&, ||, !
  - View 0 as "False"
  - Anything nonzero as "True"
  - Always return 0 or 1
  - Early termination (short cut)

## Logical Operations in C

- Examples (char data type)
  - `!0x41  -->  0x00`
  - `!0x00  -->  0x01`
  - `!!0x41 -->  0x01`
  - `0x69 && 0x55  -->  0x01`
  - `0x69 || 0x55  -->  0x01`

## Short Cut in Logical Operations

- a && 5/a
  - If a is zero, the evaluation of 5/a is stopped
  - avoid division by zero
- Using only bit-level and logical operations
  - Implement x == y
  - it returns 1 when x and y are equal, and 0 otherwise

## Shift Operations in C

- Left Shift: x << y
  - Shift bit-vector x left y positions
  - Throw away extra bits on left
  - Fill with 0's on right

| Argument x | 01100010 |
| << 3 | 00010000 |

| Argument x | 10100010 |
| << 3 | 00010000 |

## Shift Operations in C

- Right Shift: x >> y
  - Shift bit-vector x right y positions
    - Throw away extra bits on right
  - Logical shift
    - Fill with 0's on left
  - Arithmetic shift
    - Replicate most significant bit on right
    - Useful with two's complement integer representation (especially for the negative number)

| Argument x | 01100010 |
| Log. >> 2 | 00011000 |
| Arith. >> 2 | 00011000 |

| Argument x | 10100010 |
| Log. >> 2 | 00101000 |
| Arith. >> 2 | 11101000 |

## Shift Operations in C

- What happens ?
  - `int lval = 0xFEDCBA98 << 32;`
  - `int aval = 0xFEDCBA98 >> 36;`
  - `unsigned uval = 0xFEDCBA98u >> 40;`

- It may be
  - lval     0xFEDCBA98    (0)
  - aval     0xFFEDCBA9    (4)
  - uval     0x00FEDCBA    (8)

- Be careful about
  - `1<<2 + 3<<4` means `1<<(2 + 3)<<4`

## bitCount

- Returns number of 1's a in word
- Examples: bitCount(5) = 2, bitCount(7) = 3
- Legal ops: ! ~ & ^ | + << >>
- Max ops: 40

## Sum 8 groups of 4 bits each

```
int bitCount(int x) {
    int m1 = 0x11 | (0x11 << 8);
    int mask = m1 | (m1 << 16);
    int s = x & mask;
    s += x>>1 & mask;
    s += x>>2 & mask;
    s += x>>3 & mask;
```

## Combine the sums

```
/* Now combine high and low order sums */
s = s + (s >> 16);

/* Low order 16 bits now consists of 4 sums.
   Split into two groups and sum */
mask = 0xF | (0xF << 8);
s = (s & mask) + ((s >> 4) & mask);
return (s + (s>>8)) & 0x3F;
}
```

## Information Storage

## Computer Hardware - Von Neumann Architecture

![](img/b3f8b91675c485f1e811aa092ebbf3d4_132_0.png)

## Storage

- The system component that remembers data values for use in computation
- A wide-ranging technology
  - RAM chip
  - Flash memory
  - Magnetic disk
  - CD
- Abstract model
  - READ and WRITE operations

## READ/WRITE operations

- Tow important concepts
  - Name and value
- WRITE(*name*, *value*)　　 value ← READ(*name*)
- WRITE operation specifies
  - a value to be remembered
  - a name by which one can recall that value in the future
- READ operation specifies
  - the name of some previous remembered value
  - the memory device returns that value

## Outline

- Virtual Memory
- Pointers and word size
- Suggested reading
  - The first paragraph of 2.1
  - 2.1.2, 2.1.3, 2.1.4, 2.1.5, 2.1.6

## Computer Hardware - Von Neumann Architecture

![](img/b3f8b91675c485f1e811aa092ebbf3d4_137_0.png)

## Storage

- The system component that remembers data values for use in computation
- A wide-ranging technology
  - RAM chip
  - Flash memory
  - Magnetic disk
  - CD
- Abstract model
  - READ and WRITE operations

## 模具的失效形式与寿命

### 一、模具的失效

模具的失效是指模具失去正常工作的能力。模具的失效分为非正常失效和正常失效两类。非正常失效(早期失效)是指模具未达到一定寿命时的失效。正常失效是指模具经过大量的生产制件后,因缓慢地塑性变形或磨损等而最终失效。

模具的失效形式有断裂、塑性变形、磨损、疲劳等。断裂是指模具出现裂纹或开裂,是模具最严重的失效形式;塑性变形是指模具在受力过程中发生屈服,导致尺寸变化;磨损是指模具表面材料逐渐损失,影响制件精度;疲劳是指模具在循环应力作用下产生裂纹并扩展。

不同失效形式之间存在相互联系,如磨损和疲劳往往同时发生。模具的失效过程与其材料、热处理、使用条件等因素密切相关。

### 二、模具的寿命

模具的寿命是指模具在正常使用条件下,从开始使用到失效所能完成的制件总数。模具寿命的高低直接影响制件成本和模具费用。

提高模具寿命的途径包括:合理选择模具材料、优化模具结构设计、改进制造工艺、合理使用与维护等。

### 三、影响模具寿命的因素

影响模具寿命的因素主要有:模具材料、模具结构、加工精度、热处理质量、使用条件及维护保养等。

| 模具类型 | 寿命(万次) |
|---------|-----------|
| 冲裁模 | 50~100 |
| 弯曲模 | 100~200 |
| 拉深模 | 20~50 |
| 塑料模 | 10~50 |
