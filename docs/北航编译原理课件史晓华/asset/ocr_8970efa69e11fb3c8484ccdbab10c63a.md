处理逻辑表达式(关系表达式)的方法与处理算术表达式的方式基本相同。下面是逻辑表达式~( x =y & y≠z | z< x ) 生成的指令序列：

```
LOD, ( ll, on )x
LOD, ( ll, on )y
EQL
LOD, ( ll, on )y
LOD, ( ll, on )z
NEQ
AND
LOD, ( ll, on )z
LOD, ( ll, on )x
LES
ORL
NOT
```