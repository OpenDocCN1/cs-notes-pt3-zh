# Correct Return Example

```
#demo_retb
1: 0x026: ret
2: bubble
3: bubble
4: bubble
5: 0x00b: irmovl $5, %esi #return
```

+   - As ret passes through pipeline, stall at F stage
+     - While in D, E, and M stage
+     - fetch the same instruction after ret 3 times.
+   - Inject bubble into D stage
+   - Release stall when reach W stage

![](bbox=[0.38, 0.18, 0.88, 0.9])