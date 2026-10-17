# 【例2-6】：++、-- Demo：

```
public class OOperator {
public static void main(String args[]) {
int i=15, j1, j2, j2, j4;
j1=i++;
//在操作数的右面
System.out.println("i++="+j1);
j2=++i;
//在操作数的左面
System.out.println("++i="+j2);
j3=--i;
System.out.println("--i="+j3);
j4=i--;
System.out.println("i--="+j4);
System.out.println("i="+i);
}
}
```

```
i++=15
++i=17
--i=16
i--=16
i=15
```