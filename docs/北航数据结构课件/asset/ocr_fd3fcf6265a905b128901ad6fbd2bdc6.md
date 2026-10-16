```
procedure BININSERTSORT( K, n )
  for i←2 to n do
    temp←K[i]
    low←1
    high←i-1
    while (low≤high) do
      mid←⌊(low+high)/2⌋
      if (temp<K[mid]) then
        high←mid-1
      else
        low←mid+1
    end
    for j←i-1 downto low do
      K[j+1]←K[j]
    end
    K[low]←temp
  end
end
```

采用折半查找方法确定插入位置

![](bbox=[0.72, 0.25, 0.88, 0.62])