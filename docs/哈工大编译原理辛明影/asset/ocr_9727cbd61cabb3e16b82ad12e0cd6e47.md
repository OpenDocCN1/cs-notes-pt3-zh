# 过程调用id(E₁, E₂, ..., Eₙ) 的中间代码结构

```
E₁.addr := E₁的代码
E₂.addr := E₂的代码
...
Eₙ.addr := Eₙ的代码
param E₁.addr
param E₂.addr
...
param Eₙ.addr
call id.addr, n
```