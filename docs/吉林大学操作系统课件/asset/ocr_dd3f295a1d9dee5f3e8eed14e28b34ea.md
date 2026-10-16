# 程序(Cont.)

```
Procedure philosopher(I:0..4)
begin
    cycle
        {thinking}
        P(mutex);
        state[I] := hungry;
        test(I);
        V(mutex);
        P(self[I]);
```