# 访问者模式

# 模式分析

+   典型的抽象元素类代码如下所示：

```
public interface Element
{
    public void accept(Visitor visitor);
}
```