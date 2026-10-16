# 三、伪指令

HYPer

+   • 字符串

```
ORG 100H
```

```
DATA1  DB 'abcd'
```

```
DATA2  DB 'AB'
```

```
DATA3  DW 'AB'
```

|  |  |  |  |
|---|---|---|---|
| DATA1→ | 100H | 61H | a |
|  | 101H | 62H | b |
|  | 102H | 63H | c |
|  | 103H | 64H | d |
| DATA2→ | 104H | 41H | A |
|  | 105H | 42H | B |
| DATA3→ | 106H | 42H | B |
|  | 107H | 41H | A |