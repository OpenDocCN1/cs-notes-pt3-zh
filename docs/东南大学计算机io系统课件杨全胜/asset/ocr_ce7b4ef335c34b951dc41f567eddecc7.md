# 4.2 8259A PIC

# Operation and commands

# ◆ Initialization Command Words 3(ICW3)

![](bbox=[0.094, 0.259, 0.891, 0.375])

ICW3 of master controller

![](bbox=[0.098, 0.481, 0.894, 0.544])

ICW3 of slave controller

```
Master: MOV AL, 14H
        OUT 21H, AL
Slave A: MOV AL, 04H
         OUT 0A1H, AL
Slave B: MOV AL, 02H
         OUT 0C1H, AL
```

![](bbox=[0.759, 0.821, 0.909, 0.859])