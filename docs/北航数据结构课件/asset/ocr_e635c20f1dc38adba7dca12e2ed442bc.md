# 前序遍历

```
procedure PREORDER( T )
    if (T≠nil) then
    [ call VISIT( T )
      call PREORDER( lchild(T) )
      call PREORDER( rchild(T) ) ]
end
```

# 后序遍历

```
procedure POSTORDER( T )
    if (T≠nil) then
    [ call POSTORDER( lchild(T) )
      call POSTORDER( rchild(T) )
      call VISIT( T ) ]
end
```