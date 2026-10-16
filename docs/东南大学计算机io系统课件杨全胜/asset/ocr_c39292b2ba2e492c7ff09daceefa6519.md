# 2.6.1 Data Movement Instructions

# PUSH Instruction

```
PUSH SRC
```

+   - Save data to LIFO stack
+   - For 16-bit
+     1. SP<--(SP)-2
+     2. ((SP)+1,(SP))<--(SRC)
+   - For 32-bit
+     1. ESP←(ESP)-4
+     2. ((ESP)+3,(ESP)+2,(ESP)+1,(ESP))←(SRC)