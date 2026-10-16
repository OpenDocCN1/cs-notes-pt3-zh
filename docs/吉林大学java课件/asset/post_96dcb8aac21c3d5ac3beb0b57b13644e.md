
## 定义和使用三维数组

```
public class ArrayDemo10 {
    public static void main(String[] args) {
        // 定义一个三维数组，使用静态初始化的方式
        int score[][][] = { { { 5, 1 }, { 6, 7 } }, { { 9, 4 } }, { { 8, 3 } } };
        for (int i = 0; i < score.length; i++) {                     // 第一层循环
            for (int j = 0; j < score[i].length; j++) {             // 第二层循环
                for (int k = 0; k < score[i][j].length; k++) { // 第三层循环
                    System.out.println("score[" + i + "][" + j + "][" + k + "] = " + score[i][j][k]);
                    // 输出每一个元素
                }
            }
        }
    }
}
```

## 数组与方法
—— 方法的声明及使用

## 目标

- 掌握方法的作用、定义格式
- 掌握方法重载的概念及使用
- 可以使用 return 结束一个方法
- 掌握方法的递归调用

## 方法的定义

- 方法就是一段可重复调用的代码段，例如：有某段长度约100行的代码，要在多个地方使用此段代码，如果在各个地方都重复编写此部分代码的话，则肯定会比较麻烦，而且此部分代码如果修改的话也比较困难，所以此时可以将此部分代码定义成一个方法，以供程序反复调用。
- 方法的定义格式：
  - `public static 返回值类型 方法名称 (类型 参数1, 类型 参数2, ...)` {
    方法的主体
    程序语句；
    [return 表达式];
  }
  方法的主体
  - 在本节中定义的方法，因为其可以直接使用主方法（main()）调用，所以将方法声明处加上了 public static 两个关键字

## 定义一个方法，在主方法中进行调用

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

## 注意：方法命名规范要求

- 定义类的时候，类的命名规范是：“全部单词的首字母必须大写”。那么在定义方法的时候也是有命名规范要求的：“第一个单词的首字母小写，之后每个单词的首字母大写”，那么这就是方法的命名规范，之前的printInfo()方法也是按此规范定义的。这一点希望读者在日后的开发中一定要养成好的习惯。

## 有返回值的方法

```
public class MethodDemo02 {
    public static void main(String[] args) {
        int one = addOne(10, 20);                // 调用整数的加法操作
        float two = addTwo(10.3f, 13.3f); // 调用浮点数的加法操作
        System.out.println("addOne的计算结果:" + one);
        System.out.println("addTwo的计算结果:" + two);
    }
    // 定义方法，完成两个整数的加法操作，方法返回一个int型数据
    public static int addOne(int x, int y) {
        int temp = 0;                           // temp为局部变量，只在此方法中有效
        temp = x + y;                           // 执行加法计算
        return temp;                            // 返回计算结果
    }
    // 定义方法，完成两个浮点数的加法操作，方法返回一个float型数据
    public static float addTwo(float x, float y) {
        float temp = 0;                         // temp为局部变量，只在此方法中有效
        temp = x + y;                           // 执行加法计算
        return temp;                            // 返回计算结果
    }
}
```

## 方法的重载

☞ 方法的重载就是方法名称相同，但参数的类型和参数的个数不同，通过传递参数的个数及类型不同以完成不同功能的方法调用。

## 验证方法的重载

```
public class MethodDemo03 {
    public static void main(String[] args) {
        int one = add(10, 20);                 // 调用有两个参数的整型加法
        int two = add(10, 20, 30);             // 调用有三个参数的整型加法
        float three = add(10.3f, 13.3f);       // 调用有两个参数的浮点型加法
        System.out.println("add(int x, int y)的计算结果: " + one);
        System.out.println("add(int x, int y, int z)的计算结果: " + two);
        System.out.println("add(float x, float y)的计算结果: " + three);
    }
    public static int add(int x, int y) {      // 定义add方法，完成两个整数相加
        int temp = 0;                           // 定义局部变量
        temp = x + y;                           // 执行加法计算
        return temp;                            // 返回计算结果
    }
    public static int add(int x, int y, int z) { // 定义add方法，完成三个整数相加
        int temp = 0;                           // 定义局部变量
        temp = x + y + z;                       // 执行加法操作
        return temp;                            // 返回计算结果
    }
    public static float add(float x, float y) { // 定义add方法，完成两个浮点数相加
        float temp = 0;                         // 定义局部变量
        temp = x + y;                           // 执行加法操作
        return temp;                            // 返回计算结果
    }
}
```
