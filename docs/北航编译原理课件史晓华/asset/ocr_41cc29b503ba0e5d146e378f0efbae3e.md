# 10.5 赋值语句的处理

```
X:= Y+X;
```

```
LDA ( ll, on )x
LOD ( ll, on )y
LOD ( ll, on )x
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