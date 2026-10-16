# 将之前的程序修改为continue，观察运行结果

```
public class ContinueDemo {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {          // 使用for循环
            if (i == 3) {                         // 如果i的值为3，则退出整个循环
                continue;                         // 退出一次循环
            }
            System.out.println("i = " + i);      // 打印信息
        }
    }
}
```