# 7.5.2 常见控制结构的翻译

S → S₁; S₂

```
{S₁.next:=newlabel;S₂.next:=S.next;
S.code:=S₁.code||gencode(S₁.next,':')||S₂.code}
```

![](bbox=[0.52, 0.52, 0.82, 0.78])