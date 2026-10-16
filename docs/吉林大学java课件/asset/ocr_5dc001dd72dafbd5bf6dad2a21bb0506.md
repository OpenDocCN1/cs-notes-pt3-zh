# 使用方式二

```
public abstract class CalculatorFactory {
    public static Calculator getInstance() {
        return new BasicCalculator();
    }
}
public class TestAbstract {
    public static void main(String[] args) {
        Calculator c=CalculatorFactory.getInstance();
        int i=c.add(1, 2);
        System.out.print(i);
    }
}
```

有什么缺点？