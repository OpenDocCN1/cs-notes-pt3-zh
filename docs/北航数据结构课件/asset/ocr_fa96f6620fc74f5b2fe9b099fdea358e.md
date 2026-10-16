```
procedure CREATBT(T)
  T←nil  top←0
  loop
    read( ch )                          // 取表中一个元素 //
    case
      ch='@': return                     // 取到结束符号 //
      ch='(' : top←top+1                // 取到左括号 //
               STACK[top]←p
               flag←1
      ch=')' : top←top-1                // 取到右括号 //
      ch=',' : flag←2                   // 取到逗号 //
      : else : call GETNODE(p)          // 取到字母 //
               data(p)←ch
               lchild(p)←rchild(p)←nil
               if (T=nil) then
                 T←p
               else if ( flag=1 ) then
                 lchild( STACK[top] )←p
               else
                 rchild( STACK[top] )←p
    end
  forever
end
```