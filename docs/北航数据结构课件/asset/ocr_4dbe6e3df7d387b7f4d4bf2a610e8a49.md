# 改进后算法

```
procedure DEL(A, n)
if (n>1) then
[  k←1
for i←2 to n do
if (A[i]≠A[k]) then
[  k←k+1
A[k]←A[i]  ]
end
n←k  ]
end
```