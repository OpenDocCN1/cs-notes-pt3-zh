# 2. DFA的表示

◆ DFA M=({S, U, V, Q}, {a, b}, f, S, {Q}), 其中 f 定义为:
    f ( S, a )=U
    f ( V, a )=U
    f ( S, b )=V
    f ( V, b )=Q
    f ( U, a )=Q
    f ( Q, a )=Q
    f ( U, b )=V
    f ( Q, b )=Q

|  | 输入字符 | a | b |
|---|---|---|---|
| 状态 |  |  |  |
| S⁺ | U | V |
| U | Q | V |
| V | U | Q |
| Q* | Q | Q |