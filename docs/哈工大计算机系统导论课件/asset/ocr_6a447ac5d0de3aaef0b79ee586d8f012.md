# 3. 栈金丝雀(Stack Canaries)

+   - 想法
+     - 在栈中buffer之后的位置放置特殊的值——金丝雀("canary")
+     - 退出函数之前，检查是否被破坏
+   - 用GCC 实现
+     - -fstack-protector
+   - 该选项现在是默认开启的(早期默认关闭)

```
unix> ./bufdemo-sp
Type a string: 0123456
0123456
```

```
unix> ./bufdemo-sp
Type a string: 01234567
*** stack smashing detected ***
```