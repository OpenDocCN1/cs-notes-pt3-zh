# 悬空else的二义性

描述if语句的文法：

```
stmt→if expr then stmt
|if expr then stmt else stmt
|other
```

用I表示if expr then， e 表示else ,a表示other, 文法可改为：

改写后的文法G(S’)：

```
S’ → S
```

```
S→iSeS|iS|a
```