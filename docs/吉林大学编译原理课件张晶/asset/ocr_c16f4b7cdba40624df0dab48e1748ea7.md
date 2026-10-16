# # 优化前四元式序列：

```
```
i:=1
while i<=100 do
begin
z:=i*k*5;
a:=2*k+2*k*2;
i:=i+1;
end
```
```

LoopDef = {t1, t2, t3, z, t4, t5, t6, t7, a, t8, i}

+   1. (ASSIG, 1, —, i)
+   2. (WHILE, —, —, —)
+   3. (LE, i, 100, t1)
+   4. (DO, t1, —, —)
+   5. (MULTI, i, k, t2)
+   6. (MULTI, t2, 5, t3)
+   7. (ASSIG, t3, —, z)
+   8. (MULTI, 2, k, t4)
+   9. (MULTI, 2, k, t5)
+   10. (MULTI, t4, 2, t6)
+   11. (ADDI, t4, t6, t7)
+   12. (ASSIG, t7, —, a)
+   13. (ADDI, i, 1, t8)
+   14. (ASSIG, t8, —, i)
+   15. (ENDWHILE, —, —, —)