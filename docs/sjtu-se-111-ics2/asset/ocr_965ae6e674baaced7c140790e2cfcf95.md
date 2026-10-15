# Side Effects in Pipeline Processor

```
```asm
# demo-exc3.ys
irmovl $100,%eax
rmmovl %eax,0x10000(%eax) # invalid address
addl %eax,%eax             # Sets condition codes
```
```

![](bbox=[0.058, 0.438, 0.88, 0.699])

+   - **Desired Behavior**
+     - `rmmovl` should cause exception
+     - No following instruction should have any effect