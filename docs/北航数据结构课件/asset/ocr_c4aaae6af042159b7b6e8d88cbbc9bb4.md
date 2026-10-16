# 算法

O(n²)

O(n)

```
procedure DEL(A, n)
    i ← 1
    while (i < n) do
        if (A[i] ≠ A[i+1]) then
            i ← i + 1
        else
            [ for j ← i+1 to n do
              A[j-1] ← A[j]
              end
              n ← n - 1 ]
        end
    end
```

删除一个元素