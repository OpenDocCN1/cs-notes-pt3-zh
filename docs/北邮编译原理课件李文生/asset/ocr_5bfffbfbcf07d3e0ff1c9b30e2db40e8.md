# case栈

底

符号表

| name | type | address |
|---|---|---|
| L₁ | label | nextstat |
| L₂ | label | nextstat |
| ... |  |  |
| Lₙ₋₁ | label | nextstat |
| Lₙ | label | nextstat |

| 值 | 指针 |
|---|---|
| V₁ | L₁ |
| V₂ | L₂ |
| ... | ... |
| Vₙ₋₁ | Lₙ₋₁ |
| t | Lₙ |

顶

```
test: if t=V₁ goto L₁
if t=V₂ goto L₂
...
if t=Vₙ₋₁ goto Lₙ₋₁
goto Lₙ
```