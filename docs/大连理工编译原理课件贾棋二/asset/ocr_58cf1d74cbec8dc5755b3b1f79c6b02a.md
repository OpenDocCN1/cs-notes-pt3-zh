# 第四章 语法制导的定义

# 简单台式计算器的语法制导定义

| 产生式 | 语义规则 |
|---|---|
| $L \to E\ n$ | $print(E.val)$ |
| $E \to E_1 + T$ | $E.val := E_1.val + T.val$ |
| $E \to T$ | $E.val := T.val$ |
| $T \to T_1 * F$ | $T.val := T_1.val * F.val$ |
| $T \to F$ | $T.val := F.val$ |
| $F \to (E)$ | $F.val := E.val$ |
| $F \to digit$ | $F.val := digit.lexval$ |