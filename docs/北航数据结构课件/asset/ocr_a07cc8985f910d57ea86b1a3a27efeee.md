# 算法

```
function HASHSEARCH(HT,M,key)
i←H(key)
D←i
while (HT[D]=空 and HT[D]≠key) do
    D←(D+1) MOD M
    if (D=i) then        // 转了一圈回到开始点（表满）//
        return (−D)
    end
    if (HT[D]=key) then
        return(D)        // 查找成功 //
    else
        return(−D)       // 查找失败 //
    end
```