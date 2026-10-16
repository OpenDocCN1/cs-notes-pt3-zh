# 解释器模式

# 模式分析

对于非终结符表达式，其代码相对比较复杂，因为可以通过非终结符将表达式组合成更加复杂的结构，对于包含两个操作元素的非终结符表达式类，其典型代码如下：

```
public class NonterminalExpression extends AbstractExpression {
    private AbstractExpression left;
    private AbstractExpression right;
    public NonterminalExpression(AbstractExpression left,AbstractExpression right)
    {
        this.left=left;
        this.right=right;
    }
    public void interpret(Context ctx)
    {
        //递归调用每一个组成部分的interpret()方法
        //在递归调用时指定组成部分的连接方式，即非终结符的功能
    }
}
```