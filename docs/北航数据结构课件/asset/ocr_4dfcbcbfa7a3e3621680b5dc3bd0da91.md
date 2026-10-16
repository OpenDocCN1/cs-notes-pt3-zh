# 算法

```
procedure INSERT(A, n, item)
    if (item ≥ A[n]) then
        A[n+1] ← item        // 插入表的末尾 //
    else
        [ i ← 1
          while (item ≥ A[i]) do
              i ← i+1
          end
          for j ← n downto i do
              A[j+1] ← A[j]
          end
          A[i] ← item ]        // 插入表的第i个位置 //
        n ← n+1
end
```