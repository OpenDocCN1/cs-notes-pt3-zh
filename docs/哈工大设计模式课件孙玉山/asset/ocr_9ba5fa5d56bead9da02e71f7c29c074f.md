# Object adapter pattern-sample source code

```
public class Adapter implements Target {
    private Adaptee adaptee;

    public Adapter(Adaptee adaptee) {//由参数传入
        this.adaptee = adaptee;        //adaptee对象
    }
    public void operation1() {
        adaptee.operation1(); //调用
    }
    public void operation2() {
        // 写新代码
        System.out.print(" I need to write code for operation2.");
    }
}
```