# 加入验证

+   可以在setter方法中对设置的内容进行验证

```
public void setAge(int a) {
    if (a >= 0 && a < 150) {
        age = a;
    }
}
// 设置年龄
// 在此处加上验证代码
```