```
r←T
while (link(r) ≠ nil) do
    r←link(r)
end

if (i=0) then
    [   link(r)←S
        S←T    ]
else
    [   link(p)←T
        link(r)←q   ]
end
```

// r指向T的最后那个字符 //

// 将T插在S的最前面 //

// 将T插在S的第i个字符后面 //

![](bbox=[0.232, 0.664, 0.475, 0.867])