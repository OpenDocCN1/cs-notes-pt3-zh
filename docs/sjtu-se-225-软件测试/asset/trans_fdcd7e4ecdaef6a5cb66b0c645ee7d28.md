

## 精炼决策

- c1: a < b + c;
- c2: b < a + c;
- c3: c < a + b;
- c4: a = b;
- c5: a = c;
- c6: b = c;

## 表 7.3 三角形问题的精炼决策表

| 条件/动作 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| c1: a < b + c? | F | T | T | T | T | T | T | T | T | T |
| c2: b < c + a? | — | F | T | T | T | T | T | T | T | T |
| c3: c < a + b? | — | — | F | T | T | T | T | T | T | T |
| c4: a = b? | — | — | — | T | T | T | T | F | F | F |
| c5: a = c? | — | — | — | T | T | F | F | T | T | F |
| c6: b = c? | — | — | — | T | F | T | F | T | F | T |
| a1: 不是三角形 | X | X | X |  |  |  |  |  |  |  |
| a2: 不等边 |  |  |  |  |  |  |  |  |  | X |
| a3: 等腰 |  |  |  |  |  |  | X |  | X | X |
| a4: 等边 |  |  |  | X |  |  |  |  |  |  |
| a5: 不可能 |  |  |  |  | X | X |  | X |  |  |

## NextDate 函数的测试用例

### 第一次尝试，等价类集合接近：

- M1 = {month: month has 30 days}
- M2 = {month: month has 31 days}
- M3 = {month: month is February}
- D1 = {day: 1 ≤ day ≤ 28}
- D2 = {day: day = 29}
- D3 = {day: day = 30}
- D4 = {day: day = 31}
- Y1 = {year: year is a leap year}
- Y2 = {year: year is not a leap year}

| Conditions |  |  |
|---|---|---|
| c1: Month in M1? |  |  |
| c2: Month in M2? |  |  |
| c3: Month in M3? |  |  |
| c4: Day in D1? |  |  |
| c5: Day in D2? |  |  |
| c6: Day in D3? |  |  |
| c7: Day in D4? |  |  |
| c8: Year in Y1? |  |  |
| a1: Impossible |  |  |
| a2: NextDate |  |  |

将有 2⁸ = 256 条规则！

## 第二次尝试，关注 NextDate 函数的闰年方面

M1 = {month: month has 30 days}

M2 = {month: month has 31 days}

M3 = {month: month is February}

D1 = {day: 1 ≤ day ≤ 28}

D2 = {day: day = 29}

D3 = {day: day = 30}

D4 = {day: day = 31}

Y1 = {year: year = 2000}

Y2 = {year: year is a non-century leap year}

Y3 = {year: year is a common year}

## 这些条件将导致一个包含 36 条规则的决策表

| | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| c1: Month in | M1 | M1 | M1 | M1 | M2 | M2 | M2 | M2 |
| c2: Day in | D1 | D2 | D3 | D4 | D1 | D2 | D3 | D4 |
| c3: Year in | — | — | — | — | — | — | — | — |
| Rule count | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 |
| a1: Impossible |  |  |  | X |  |  |  |  |
| a2: Increment day | X | X |  |  | X | X | X |  |
| a3: Reset day |  |  | X |  |  |  |  | X |
| a4: Increment month |  |  | X |  |  |  |  | ? |
| a5: Reset month |  |  |  |  |  |  |  | ? |
| a6: Increment year |  |  |  |  |  |  |  | ? |

## 第三次尝试，具体说明二月和十二月中的天数

M1 = {month: month has 30 days}

M2 = {month: month has 31 days except December}

M3 = {month: month is December}

M4 = {month: month is February}

D1 = {day: 1 ≤ day ≤ 27}

D2 = {day: day = 28}

D3 = {day: day = 29}

D4 = {day: day = 30}

D5 = {day: day = 31}

Y1 = {year: year is a leap year}

Y2 = {year: year is a common year}

## 表 7.14 NextDate 函数的决策表

| | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| c1: Month in | M1 | M1 | M1 | M1 | M1 | M2 | M2 | M2 | M2 | M2 |
| c2: Day in | D1 | D2 | D3 | D4 | D5 | D1 | D2 | D3 | D4 | D5 |
| c3: Year in | — | — | — | — | — | — | — | — | — | — |
| Actions |  |  |  |  |  |  |  |  |  |  |
| a1: Impossible |  |  |  |  | X |  |  |  |  |  |
| a2: Increment day | X | X | X |  |  | X | X | X | X |  |
| a3: Reset day |  |  |  | X |  |  |  |  |  | X |
| a4: Increment month |  |  |  | X |  |  |  |  |  | X |
| a5: Reset month |  |  |  |  |  |  |  |  |  |  |
| a6: Increment year |  |  |  |  |  |  |  |  |  |  |

## 22 条规则

| | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| c1: Month in | M3 | M3 | M3 | M3 | M3 | M4 | M4 | M4 | M4 | M4 | M4 | M4 |
| c2: Day in | D1 | D2 | D3 | D4 | D5 | D1 | D2 | D2 | D3 | D3 | D4 | D5 |
| c3: Year in | — | — | — | — | — | — | Y1 | Y2 | Y1 | Y2 | — | — |
| Actions |  |  |  |  |  |  |  |  |  |  |  |  |
| a1: Impossible |  |  |  |  |  |  |  |  |  | X | X | X |
| a2: Increment day | X | X | X | X |  | X | X |  |  |  |  |  |
| a3: Reset day |  |  |  |  | X |  |  | X | X |  |  |  |
| a4: Increment month |  |  |  |  |  |  |  | X | X |  |  |  |
| a5: Reset month |  |  |  |  | X |  |  |  |  |  |  |  |
| a6: Increment year |  |  |  |  | X |  |  |  |  |  |  |  |

