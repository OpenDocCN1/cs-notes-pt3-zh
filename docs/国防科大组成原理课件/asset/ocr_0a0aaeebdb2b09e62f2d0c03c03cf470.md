# LWL/LWR指令举例

• 如果没有它们，取一个不对齐的字需要10条指令

• 包括4个load/store并需要一个临时寄存器：

```
lbu rt,3(base)
sll rt,rt,24
lbu rtmp,2(base)
sll rtmp,rtmp,16
or rt,rt,rtmp
lbu rtmp,1(base)
sll rtmp,rtmp,8
or rt,rt,rtmp
lbu rtmp,rtmp,0(base)
or rt,rt,rtmp
```