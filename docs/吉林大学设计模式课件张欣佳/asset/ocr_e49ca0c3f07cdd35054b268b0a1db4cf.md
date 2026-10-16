# 模板方法模式

# 模式分析

在模板方法模式中，抽象类的典型代码如下：

```
abstract class AbstractClass {
    //模板方法
    public void TemplateMethod() {
        PrimitiveOperation1();
        PrimitiveOperation2();
        PrimitiveOperation3();
    }
    //基本方法—具体方法
    public void PrimitiveOperation1() { //实现代码 }
    //基本方法—抽象方法
    public abstract void PrimitiveOperation2();
    //基本方法—钩子方法
    public virtual void PrimitiveOperation3() { }
}
```

对于所有子类都相同的基本方法可在父类提供具体实现，否则在父类声明为抽象方法或钩子方法，由不同的子类提供不同的实现。