# 算法

```
procedure ADDLINKQUEUE( front, rear, item )
call GETNODE(p)        // 申请一个链结点 //
data(p)←item
link(p)←nil
if (front = nil) then
    front←p                // 插入空队的情况 //
else
    link(rear)←p
rear←p                  // 插入非空队的情况 //
end
```