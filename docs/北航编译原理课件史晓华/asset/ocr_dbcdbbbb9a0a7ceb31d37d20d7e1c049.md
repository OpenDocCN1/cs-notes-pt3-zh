# 假设临时寄存器 EAX，EDX 可用

```
（1）t1 = a + b
    t2 = c + d
    t3 = e − t2
    t4 = t1 − t3

mov eax, a    ; t1 = a + b
add eax, b
mov edx, c    ; t2 = c + d
add edx, d
mov [ESP+08H], eax ; t3 = e − t2
mov eax, e
sub eax, edx
mov [ESP+0CH], edx ; t4 = t1 − t3
mov edx, [ESP+08H]
sub edx, eax
```

```
（2）t2 = c + d
    t3 = e − t2
    t1 = a + b
    t4 = t1 − t3

mov eax, c    ; t2 = c + d
add eax, d
mov edx, e    ; t3 = e − t2
sub edx, eax
mov [ESP+0CH], eax ; t1 = a + b
mov eax, a
add eax, b
mov [ESP+08H], eax ; t4 = t1 − t3
sub eax, edx
```