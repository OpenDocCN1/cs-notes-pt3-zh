# # 桥接模式

# ## 模式分析

# ## 典型的抽象类代码：

```
```java
public abstract class Abstraction
{
    protected Implementor impl; //定义实现类接口对象
    public void setImpl(Implementor impl)
    {
        this.impl=impl;
    }
    public abstract void operation(); //声明抽象业务方法
}
```
```