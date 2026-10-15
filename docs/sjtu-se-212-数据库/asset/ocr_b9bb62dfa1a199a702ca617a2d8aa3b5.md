# Schedule 1

| T₁ | T₂ |
|---|---|
| read (A)
A := A - 50
write (A)
read (B)
B := B + 50
write (B)
commit | |
| | read (A)
temp := A * 0.1
A := A - temp
write (A)
read (B)
B := B + temp
write (B)
commit |

A serial schedule in which T₁ is followed by T₂