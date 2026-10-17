# # 选择结构 Demo2:

```
public class Root { // [例3-5]:求解ax+b=0(a≠0)的根
public static void main(String args[]) {
    float a, b, x;

a=Float.parseFloat (args[0]); // 输入a
b=Float.parseFloat (args[1]); // 输入b

if (Math.abs(a)>0.000001f) { // a!=0
    x=-b/a;
    System.out.println("x="+x); // 输出x
    }
}
}
```