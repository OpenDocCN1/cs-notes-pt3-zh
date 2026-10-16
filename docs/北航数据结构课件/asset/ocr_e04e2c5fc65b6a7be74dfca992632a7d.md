```
procedure PREORDER(T)
    if (T=nil) then
        return
    top←0
    p←T
    repeat
        while (p≠nil) do
            call VISIT(p)
            if (top=M) then
                [ call ERROR('overflow!')
                  return ]
            top←top+1
            STACK[top]←p
            p←lchild(p)
        end
        p←STACK[top]
        top←top-1
        p←rchild(p)
    until (p=nil and top=0)
end
```

![](bbox=[0.6, 0.18, 0.97, 0.88])