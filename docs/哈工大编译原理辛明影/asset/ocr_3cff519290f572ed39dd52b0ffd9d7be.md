# if-then-else语句的回填式翻译

![](bbox=[0.05, 0.15, 0.95, 0.75])

```
S → if B then M₁ S₁ N else M₂ S₂
{
backpatch(B.truelist, M₁.quad);
backpatch(B.falselist, M₂.quad);
S.nextlist := merge(S₂.nextlist,merge(N.nextlist,S₁.nextlist))}

```