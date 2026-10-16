
处理逻辑表达式(关系表达式) 的方法与处理算术表达式的方法基本相同。下面是逻辑表达式～( x = y & y≠z | z＜x)生成的指令序列：

```
LOD, (II, on )x
LOD, (II, on )y
EQL
LOD, (II, on )y
LOD, (II, on )z
NEQ
AND
LOD, (II, on )z
LOD, (II, on )x
LES
ORL
NOT
```

## 10.5 赋值语句的处理

```
X:= Y+X;
```

```
LDA ( II, on )x
LOD ( II, on )y
LOD ( II, on )x
ADD
STN
```

```
<assignstat>→@setL↑L<variable>↓L↑t:= @resetL↑L<expr>↑s@stor in↓t,s ;
```

置“左值”特征L为真

被赋变量类型

类型转换，生成 STN指令

置“左值”特征L为假

表达式类型

@setL是设置变量为“左值”（被赋变量），即将属性L置true

@resetL是设置变量为非被赋变量，即把属性L置成false

```
procedure setL;
    return (true );
end;
指示取变量地址
```

```
procedure resetL;
    return (false );
end;
指示取变量之值
```

```
procedure storin(t,s);
    string t, s;
    if t ≠ s
    then /*生成进行类型转换的指令*/
    emit('STN');
end;
```

## 10.6 控制语句的处理

### 10.6.1 if语句

IF <log_expr> THEN <stat list> labA: JMF, labA

IF <log_expr> THEN <stat list> ELSE labA: <stat list> labB: JMF, labA JMP, labB

其属性翻译文法及相应的语义动作程序：

- 1. <if_stat> → <if_head> ↑y <if_tail> ↓y
- 2. <if_head> ↓y → IF <log_expr> @brf ↑y THEN <stat list>
- 3. <if_tail> ↓y → @labprod ↓y | ELSE @br ↑z @labprod ↓y <stat_list> @labprod ↓z

动作程序@brf的功能是生成 JMF指令，并将转移标号返回给属性y

```
procedure brf;
    string labx;
    labx := genlab;
    /*产生一标号赋给labx*/
    emitl('JMF', labx);
    return (labx);
end;
```

动作程序@br是是生成JMP指令，并将转移标号返回给属性z

```
procedure br;
    string labz;
    labz := genlab;
    emitl('JMP', labz);
    return( labz);
end;
```

动作程序@labprod是把从继承属性y得到的标号设置到目标程序中

```
procedure labprod(y);
    string y;
    setlab(y);
    /*在目标程序当前位置设标号*/
end;
```

- 1. <if_stat>→<if_head>_{y} <if_tail>_{y}
- 2. <if_head>_{y}→IF <log_expr>@brf_{y} THEN <stat list>
- 3. <if_tail>_{y}→@labprod_{xy} |ELSE @br_{yz}@labprod_{1y}<stat_list>@labprod_{1z}

## Compiler

```
for <id> := <expr1> to <expr2> by <expr3> do <stat list>
```

```
LDA, (<id>)
LOD, (expr1)
STN
JMP, start
loop:
LOD, (expr2)
LOD, (id)
LOD, (expr3)
ADD
STO, (id)
BGT, end_loop
start: <statement>
...
JMP, loop
end_loop:
```

```
@initload_s
@labgen_r
@loadid_a
@compare_a,s,f
@retbranch_r
@labprod_f
```

![](img/1ebd4dbc150db02388404d0c659c1fd7_651_0.png)

```
```pascal
procedure labgen
  string r;
  r := genlab;
  setlab(r);
  return (r);
end;
```
```

```
```pascal
procedure compare( a, s);
  address a;   string f, s;
  emit(‘ADD’);
  emitl(‘STO’, a );
  f := genlab;
  emitl(‘BGT’, f );
  setlab( s );
  return( f );
end;
```
```

```
```pascal
procedure loadid( a )
  address a;
  emitl(‘LOD’, a);
end;
```
```

```
```pascal
procedure labprod( f )  // 即labemit
  string f;
  setlab( f );
end;
```
```

## 10.7 过程调用和返回

### 10.7.1 参数传递的基本形式

- 1. 传值（call by value） — 值调用

实现：

调用段（过程语句的目标程序段）：
计算实参值 => 操作数栈栈顶

被调用段（过程说明的目标程序段）：
从栈顶取得值 => 形参单元

过程体中对形参的处理：

对形参的访问等于对相应实参的访问

特点：

数据传递是单向的

如C语言，
Ada语言的in参数,
Pascal 的值参数。

### 2. 传地址（call by reference）— 引用调用

实现：

调用段：
计算实参地址 => 操作数栈栈顶

被调用段：
从栈顶取得地址 => 形参单元

> 如：FORTRAN、Pascal 的变量形参。

过程体中对形参的处理：
通过对形参的间接访问来访问相应的实参

特点：
结果随时送回调用段

### 3. 传名（call by name）

又称“名字调用”。即把实参名字传给形参。这样在过程中引用形参时，都相当于对当时实参变量的引用。
当实参变量为下标变量时，传名和传地址调用的效果可能会完全不同。
传名参数传递方式，实现比较复杂，其目标程序运行效率较低，现已很少采用。

```
```pascal
begin
    integer I;
    array A[1:10] integer;
    procedure P(x);
        integer x;
        begin
            ....
            I := I + 1;
            x := x + 5;
            ...
        end;
begin
    ...
    I := 1;
    P(A[I]);
    ...
end;
end;
```
```

假定：A[1] = 1  A[2] = 2

传地址：

传名：

| 传地址调用过程中的值 | 传名调用过程中的值 |
|---|---|
| I：2<br>A[1]：6 | I：2<br>A[I] := A[I] + 5 |

A[1] = 6  A[2] = 2

A[1] = 1  A[2] = 7

### 10.7.2 过程调用处理

与调用有关的动作如下：

- 1. 检查该过程名是否已定义（过程名和函数名不能用错）实参和形参在类型、顺序、个数上是否一致。（查符号表）
- 2. 加载实参（值或地址）
- 3. 加载返回地址
- 4. 转入过程体入口地址

例：有过程调用：
`process_symb(symb, cursor, replacestr);`

```
LOD, (addr of symb )
LOD, (addr of cursor )
LOD, (addr of replacestr)
JSR, ( addr of process_symb)
<retaddr>:....
```

传值调用

若实参并非上例中所示变量，而是表达式，则应生成相应计算实参表达式值的指令序列。

JSR指令先把返回地址压入操作数栈，然后转到被调过程入口地址。
