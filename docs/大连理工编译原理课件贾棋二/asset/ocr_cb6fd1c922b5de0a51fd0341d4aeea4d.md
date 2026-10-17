# 4.3 L属性定义的自上而下计算

# 4.3.4（通过改写文法）用综合属性代替继承属性

Pascal的声明，如 m, n : integer

```
D → L : T
T → integer | char
L → L, id | id
```

![](bbox=[0.465, 0.531, 0.866, 0.913])