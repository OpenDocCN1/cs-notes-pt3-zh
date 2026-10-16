# 非递归算法：

```
function F( m, n )
    top←0
    repeat
        if (m×n ≠ 0) then
        [   top←top+1
            STACK[top]←m−1        // 进栈 //
            n←n−1   ]
        else
        [   f←m+n+1
            if (top>0) then
                m←STACK[top]        // 退栈 //
                top←top-1
                n←f   ]
    until top= −1
    return( f )
end
```