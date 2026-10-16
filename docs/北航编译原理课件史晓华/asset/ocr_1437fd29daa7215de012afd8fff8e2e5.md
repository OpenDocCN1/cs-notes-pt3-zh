# 10.6.4 for 循环语句

for 语句例子：

```
for i:= 1 to n by z do
    <statement>
    ...
end for;
```

# ATG文法

```
1.<for loop>→<for head>↑a, f, r < rest of loop>↓a, f, r
2.<for head>↑a, f, r →for <id>↑a := <expr> @initload↑s
                         to @labgen↑r <expr> by
                         @loadid↓a <expr> @compare↓a, s↑f
3.<rest of loop>↓a, f, r →do <stat list> end for
                         @rebranch↓r @labemit↓f
```

@initload 只生成给循环变量赋初值的指令。