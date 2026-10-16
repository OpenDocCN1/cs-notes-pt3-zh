# CallTail:

```
<ProcFunCall> → id #CallHead#
( <ParamList> ) #CallTail#
<ParamList> → ε | <ExpList>
<ExpList> → E #ActParam#
<NextList>
<NextList> → ε | , <ExpList>
```

+   - 取出 id 的所有语义信息。
+   - 检查形、实参个数是否一致，检查形容；
+   - 产生送实参信息到形参信息的 Vai Act.
+   - 根据 f 是实在过程(函数)名或形式过程 的 CALL 代码；
+   - 删除当前过程 / 函数调用语句所占的语义栈单元，如果 f 是函数，则把返回值的类型和语义信息压入 Sem 栈。

```
Sem
( Eₙ . typ , Eₙ 语义信息 )
....................
( E₁ . typ , E₁ 语义信息 )
( — , id )
```