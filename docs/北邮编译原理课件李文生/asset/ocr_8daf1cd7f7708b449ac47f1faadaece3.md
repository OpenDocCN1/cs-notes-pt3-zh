# 三地址语句的实现——四元式

四元式
（op, arg1, arg2, result）
（op, arg1, , result）
（param, arg1, , ）
（goto, , , 语句标号）

赋值语句a:=b*-c+b*-c的四元式表示

|  | op | arg1 | arg2 | result |
|---|---|---|---|---|
| (14) | uminus | c |  | t₁ |
| (15) | * | b | t₁ | t₂ |
| (16) | uminus | c |  | t₃ |
| (17) | * | b | t₃ | t₄ |
| (18) | + | t₂ | t₄ | t₅ |
| (19) | := | t₅ |  | a |