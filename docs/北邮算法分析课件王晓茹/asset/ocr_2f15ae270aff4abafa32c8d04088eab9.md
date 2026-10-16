# Recursive solution

hanoi(#disk, source, buffer, target):

hanoi(n, left, middle,right);=>

```
hanoi(n-1, left, right, middle);
move(1, left, _, right);
hanoi(n-1, middle, left, right);
```

![](bbox=[0.48, 0.45, 0.88, 0.88])