# # B样条曲线

+   □ 均匀二次（三阶）B样条曲线

取n=3, m=3, 则n+m=6, 不妨设节点向量为: T=(0,1,2,3,4,5,6):

```
B_{k,1}(t) = \begin{cases} 1 & k \leq t < k+1 \\ 0 & 其他 \end{cases}
```

```
B_{k,m}(t) = \frac{t-k}{m-1} B_{k,m-1}(t) + \frac{k+m-t}{m-1} B_{k+1,m-1}(t)
```