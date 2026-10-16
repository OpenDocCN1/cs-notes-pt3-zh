# 用数值表示布尔值的翻译

*nextquad*是下一条三地址码指令的序号，每生成一条三地址码指令*gencode*便会将*nextquad*加1

```
B → B₁ or B₂  {B.addr := newtemp;
    gencode(B.addr':='B₁.addr'or'B₂.addr)}
```

```
B → B₁ and B₂  {B.addr := newtemp;
    gencode(B.addr':='B₁.addr'and'B₂.addr)}
```

```
B → not B₁  {B.addr := newtemp;
    gencode(B.addr':=' 'not'B₁.addr)}
```