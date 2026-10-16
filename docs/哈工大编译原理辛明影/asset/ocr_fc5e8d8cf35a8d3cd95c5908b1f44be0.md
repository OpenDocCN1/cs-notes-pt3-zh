②. merg(p1, p2)：连接由指针p1和p2指向的两个表并且返回一个指向连接后的表的指针。
Merg(p1, p2) = { P1  p2=0
P2  p2≠0 }

# 代码描述：

```
function MERG(P1, P2) :POITER
{
  IF P2=0
  THEN merg=P1
  ELSE {  P=P2
    while 四元式P的第4分量不为0  do
      { P=四元式P的第4分量内容}
    把P1填入四元式P的第4分量
    MERG=P2
  }
```