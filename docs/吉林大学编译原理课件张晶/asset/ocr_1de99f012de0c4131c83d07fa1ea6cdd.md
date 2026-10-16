跳转法的主要思想是（考虑从后往前的情形）：
> 每当退出一个局部化区时，将一个跳转项添加到符号表中：
 s := s +1 ; SymbTab[s] :=( # ， Scope(l)-1 ) ;POP (Scope).
> 当查表时，从当前符号表的末项SymbTab[s]开始往前查，当遇到跳转项时跳到跳转项的地址部分所指向的地址继续查找。
例如：如果要查的是X的属性，则查表过程大致可描述如下：（ 开始 i 取s 值）
[1] if SymbTab[i].name = X then
    return(SymbTab[i].attrib);
[2] if SymbTab[i].name = #
    then i= SymbTab[i].addr
    else i = i - 1;
[3] if i = 0 then Error else goto [1].