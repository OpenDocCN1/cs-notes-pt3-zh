# 语句序列的回填式翻译

![](bbox=[0.42, 0.18, 0.92, 0.62])

S → S₁; M S₂

```
{backpatch(S₁.nextlist, M.quad);
S.nextlist:=S₂.nextlist}
```