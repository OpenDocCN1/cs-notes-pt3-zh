# jmp i go, INITSEG

jmp i (jump intersegment段间跳转): cs=INITSEG, ip=go

```
go: mov ax,cs //cs=0x9000
    mov ds,ax  mov es,ax  mov ss,ax  mov sp,#0xfff0
load_setup: //载入setup模块
    mov dx,#0x0000  mov cx,#0x0002  mov bx,#0x0200
    mov ax,#0x0200+SETUPLEN  int 0x13 //BIOS中断
    jnc ok_load_setup
    mov dx,#0x0000
    mov ax,#0x0000 //复位
    int 0x13
    j load_setup //重读
```

为call做准备!

0x13是BIOS读磁盘扇区的中断: ah=0x02-读磁盘, al=扇区数量(SETUPLEN=4), ch=柱面号, cl=开始扇区, dh=磁头号, dl=驱动器号, es:bx=内存地址

![](bbox=[0.03, 0.68, 0.72, 0.92])

启动盘

boot扇区

setup的4个扇区

system模块(OS代码)

Operating System