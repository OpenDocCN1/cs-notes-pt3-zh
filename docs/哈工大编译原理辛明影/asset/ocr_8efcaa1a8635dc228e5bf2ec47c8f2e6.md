# 从图5-22构造的翻译模式

```
S→ {B.ps:=10}
  B {S.ht:=B.ht}
```

```
B→ {B₁.ps:=B.ps}
  B₁ {B₂.ps:=B.ps}
  B₂ {B.ht:=max(B₁.ht,B₂.ht)}
```

```
B→ {B₁.ps:=B.ps}
  B₁
  sub {B₂.ps:=shrink(B.ps)}
  B₂ {B.ht:=disp(B₁.ht,B₂.ht)}
```

```
B→text {B.ht:=text.h*B.ps}
```