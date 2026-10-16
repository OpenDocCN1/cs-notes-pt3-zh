# 带左递归的文法的翻译模式

例5.14 图5-24的带左递归的文法的翻译模式被转换成图5-25的带右递归的文法的翻译模式。

```
E → E₁ + T   { E·val := E₁·val + T·val }
E → E₁ - T   { E·val := E₁·val - T·val }
E → T        { E.val := T·val }
T → (E)      { T·val := E·val }
T → num      { T·val := num·val }
```