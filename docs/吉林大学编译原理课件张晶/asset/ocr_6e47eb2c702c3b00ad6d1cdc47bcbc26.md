# 目标代码

```
1. L1(top)=1
LD R,x
2. LT R,y
3. ST t1,R
4. LD R,t1
5. JMPF R,*(34)
L2(top)=5
6. LD R,y
7. ADD R,1
8. ST t2,R
9. LD R,t2
10. ST y,R
11. LD R,y
12. GT R,0
13. ST t3,R
14. LD R,t3
15. JMPF R,*(22)
L2(top)=15
16. LD R,y
17. SUB R,x
18. ST t4,R
19. LD R,t4
20. ST y,R
21. JMP *(33)
回填22至L2(top)
L2(top)=21
22. L1(top)=22 LD R,y
23. LT R,0
24. ST t5,R
25. LD R,t5
26. JMPF R,*(33)
L2(top)=26
27. LD R,y
28. ADD R,x
29. ST t6,R
30. LD R,t6
31. ST y,R
32. JMP 22:L1(top)
回填33至L2(top)
33. 回填33至L2(top)
JMP 1:L1(top)
回填34至L2(top)
```

```
while (x < y)
{
    y = y + 1;
    if (y > 0)  y = y - x;
    else while (y < 0)
        y = y + x;
}
```