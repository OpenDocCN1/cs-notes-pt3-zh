# 设计方案正确吗？

```
public static void resize(Rectangle r) {
    while (r.getHeight() <= r.getWidth()) {
        r.setHeight(r.getHeight() + 1);
    }
    System.out.println("It's OK.");
}
```

```
Rectangle r1 = new Rectangle();
r1.setHeight(5);
r1.setWidth(15);
resize(r1);
```

```
Rectangle r2 = new Square();
r2.setHeight(5);
r2.setWidth(15);
resize(r2);
```

+   ✓ 使用父类（长方形）时，程序正常运行
+   ✓ 使用子类（正方形）时，程序陷入死循环
+   ✓ 设计出问题了？继承出问题了？