# 使用break

```
public class BreakDemo {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {          // 使用for循环
            if (i == 3) {                       // 如果i的值为3，则退出整个循环
                break;                          // 退出整个循环
            }
            System.out.println("i = " + i);     // 打印信息
        }
    }
}
```