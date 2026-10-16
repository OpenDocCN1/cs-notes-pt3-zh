# 7.5 COM in IA-32

# 16550 initialize

```
mov     dx,3fbh    ; LCR
mov     al,80h
out     dx,al       ; DLAB=1

mov     dx,3f8h    ; Divisor latch Lsb
mov     al,78h     ; 9600 Baud rate
out     dx,al
mov     al,00      ; Divisor latch MSb
inc     dx
out     dx,al
```