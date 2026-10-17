# # Branch Prediction

# ## Idea

+   - Guess which way branch will go
+   - Begin executing instructions at predicted position
+     - But don’t actually modify register or memory data

```
```
404663:       mov     $0x0,%eax
404668:       cmp     (%rdi),%rsi
40466b:       jge     404685
40466d:       mov     0x8(%rdi),%rax
        . . .
404685:       repz retq
```
```

![](bbox=[0.641, 0.521, 0.826, 0.551])

![](bbox=[0.594, 0.683, 0.738, 0.781])