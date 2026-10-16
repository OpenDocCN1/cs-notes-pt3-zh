# 7.3.1 简单赋值语句的翻译

```
S → id := E    {p := lookup(id.name);
if p ≠ nil then
gencode(p, ‘:=’, E.addr)
else error }
```

```
E → E₁ + E₂ {E.addr := newtemp;
emit(E.addr, ‘:=’, E₁.addr, ‘+’, E₂.addr)}
```

```
E → −E₁ {E.addr := newtemp;
emit(E.addr, ‘:=’, ‘uminus’, E₁.addr)}
```

```
E → (E₁) {E.addr := E₁.addr }
```

```
E → id  {p := lookup(id.name);
if p ≠ nil then E.addr := p else error }
```