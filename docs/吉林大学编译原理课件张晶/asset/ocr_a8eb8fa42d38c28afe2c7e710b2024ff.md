例： x + f ( H(10), g(Y) )
其中： x是整型变量， H为返回值是整型的形参函数名， H的形参为整型值参， f, g为返回值是整型的实在函数名， f的参数均为整型值参， g的参数为变参。

```
f ()
⇒
⎛
H(10) ⇒ [ ( ValACT, 10, Offset₁, 1 )
          ( CALL, H, false, t₁ ) ]
g(Y) ⇒ [ ( VarACT, Y, Offset₁, 1 )
          ( CALL, g, true, t₂ ) ]
( ValACT, t₁, Offset₁,1 )
( ValACT, t₂, Offset₁+1, 1)
( CALL, f, true, t₃ )
⎞
x + f() ( ADDI, x, t₃, t₄ )
```

注：其中Offset₁表示函数H，g及f的第1个参数的偏移量。