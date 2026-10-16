# 定义一个方法，在主方法中进行调用

```
public class MethodDemo01 {
    public static void main(String[] args) {
        printInfo();     // 调用printInfo()方法
        printInfo();     // 调用printInfo()方法
        printInfo();     // 调用printInfo()方法
        System.out.println("Hello World!") ;
    }
    // 此处由于此方法是main方法直接调用所以一定要加上public static
    public static void printInfo() {     // 此处方法没有返回值
        char c[] = {'H','e','l','l','o',
                    ' ','L','X','H'};          // 定义一个字符数组
        for (int x = 0; x < c.length; x++) {     // 循环输出
            System.out.print(c[x]) ;
        }
        System.out.println("") ;               // 换行
    }
}
```