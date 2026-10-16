```
procedure DEL( G, n, item )
  k←0
  for i←1 to n do
    if (vertex[i]=item) then
      [ k←i
        exit ]
  end
  if (k=0) then
    return
  p←link[k]  // p的初值
  for i←k+1 to n do
    vertex[i-1]←vretex[i]
    link[i-1]←link[i]
  end
  n←n-1    // 顶点的个数减1 //

while (p≠nil) do
  q←p
  p←next(p)
  call RET(q)
end

// 释放第k个链表中所有链结点的存储空间
```