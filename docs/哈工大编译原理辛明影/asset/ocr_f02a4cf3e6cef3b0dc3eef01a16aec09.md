# 程序例子

本节所用的例子

```
i = m -1; j = n; v = a[n];
while (1) {
  do i = i +1; while(a[i]<v);
  do j = j -1; while (a[j]>v);
  if (i >= j) break;
  x=a[i]; a[i]=a[j]; a[j]=x;
}
x=a[i]; a[i]=a[n]; a[n]=x;
```

+   (1) i := m -1
+   (2) j := n
+   (3) t₁ := 4 * n
+   (4) v := a[t₁]
+   (5) i := i + 1
+   (6) t₂ := 4 * i
+   (7) t₃ := a[t₂]
+   (8) if t₃ < v goto(5)