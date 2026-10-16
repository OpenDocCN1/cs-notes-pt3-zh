# ADD指令和SUB指令

例如：

```
.data
var1: .int 0x10000
var2: .int 0x20000
.text
mov var1, % eax
add  var2, %eax,
```

; eax=30000h,var1=10000h,var2=20000h
; CF=0,SF=0,ZF=0,OF=0