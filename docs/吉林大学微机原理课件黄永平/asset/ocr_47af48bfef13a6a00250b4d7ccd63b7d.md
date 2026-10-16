# 三、伪指令

对连接程序进行连接后存储区各段相对位置分布。

```
DATA1      SEGMENT  'DATA'
CODE       SEGMENT  'CODE'
STACK1     SEGMENT  'STACK'
DATA2      SEGMENT  'DATA'
STACK2     SEGMENT  'STACK'
```

经连接程序连接后，各段的相对位置如下：

```
DATA1      SEGMENT  'DATA'
DATA2      SEGMENT  'DATA'
STACK1     SEGMENT  'STACK'
STACK2     SEGMENT  'STACK'
CODE       SEGMENT  'CODE'
```