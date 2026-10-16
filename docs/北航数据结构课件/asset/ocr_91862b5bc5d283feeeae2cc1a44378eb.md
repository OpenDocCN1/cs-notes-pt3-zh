# 主算法

若已知中序序列 IN[1:n]和后序序列 POST[1:n]，又如何

```
procedure BUILDTREE( T )
T←nil
for i←1 to n do
    call INSERTITEM( T, PREOD[i] )
end
end
```

```
for i←n downto 1 do
    call INSERTITEM( T, POSTOD[i] )
end
```