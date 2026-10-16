# 跳到system模块执行...

+   - system模块(目标代码)中的第一部分代码？ head.s

+   - system由许多文件编译而成，为什么是head.s？

```
disk: Image
  dd bs=8192 if=Image of=/dev/PS0
Image: boot/bootsect  boot/setup tools/system tools/build
tools/build boot/bootsect boot/setup tools/system > Image
tools/system: boot/head.o  init/main.o $(DRIVERS) ...
$(LD) boot/head.o init/main.o $(DRIVERS) ... -o tools/system
```

if=input file
/dev/PS0是软驱A

linux/Makefile

+   - 明白为什么head.s就这样一个名字了吧？