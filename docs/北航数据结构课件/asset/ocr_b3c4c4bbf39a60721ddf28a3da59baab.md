# 四. 调整子算法

功能：将以编号为 i 的结点作为根的子树调整为一个堆积。

```
procedure ADJUST(K, i, n)
  temp ← K[i]
  j ← 2 × i
  while (j ≤ n) do
    if (j < n and K[j+1] > K[j]) then
      j ← j + 1
    if (temp ≥ K[j]) then
      [ K[⌊j/2⌋] ← temp
        return ]
    K[⌊j/2⌋] ← K[j]
    j ← 2 × j
  end
  K[⌊j/2⌋] ← temp
end
```

K：序列
i：被调整的二叉树的根的序号
n：被调整的二叉树的结点数目