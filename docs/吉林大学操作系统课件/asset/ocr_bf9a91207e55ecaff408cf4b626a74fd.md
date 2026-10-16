# 互斥例子：借书系统(revisited)

```
Var mutex:semaphore; (initial value is 1)

终端1:                     终端2:
CYCLE                     CYCLE
  等待借书者;              等待借书者;
  P(mutex)                 P(mutex)
  IF x>=1 Then             IF x>=1 Then
    Begin                  Begin
      x:=x-1;               x:=x-1;
      V(mutex)              V(mutex)
      借书                   借书
    End                    End
  Else V(mutex);无书;      Else V(mutex);无书;
End                       End
```