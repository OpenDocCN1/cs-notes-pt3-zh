# 折半查找算法

```
```text
function BINSEARCH(KEY, n, k)
    low←1
    high←n
    while (low≤high) do
        mid←⌊(low+high)/2⌋
        if (KEY[mid]=k) then
            return mid        // 查找成功 //
        if (k>KEY[mid]) then
            low←mid+1         // 查找后半部分 //
        else
            high←mid-1        // 查找前半部分 //
        end
    return(0)                 // 查找失败 //
end
```
```