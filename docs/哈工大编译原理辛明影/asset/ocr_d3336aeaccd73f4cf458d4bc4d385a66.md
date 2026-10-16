# while语句的回填式翻译

S → while M₁ B do M₂ S₁

```
{backpatch(S₁.nextlist,M₁.quad);
backpatch(B.truelist,M₂.quad);
S.nextlist:=B.falselist;
gencode('goto'M₁.quad)}
```

![](bbox=[0.48, 0.02, 0.98, 0.82])