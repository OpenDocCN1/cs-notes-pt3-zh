# 应用桥模式设计的例子

# 抽象部分子类

```
public class SuperCup implements TeaSize{
    private TeaKind tk;
    public SuperCup (TeaKind tKind){
        tk = tKind;
    }
    public float getPrice(){
        float teaPrice = 1.5f * tk.price();
        return teaPrice;
    }
}
```