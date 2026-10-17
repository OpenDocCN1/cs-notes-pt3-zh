

## 例P179

### 发生被零除错误，程序继续运行

```java
// Handle an exception and move on.
import java.util.Random;
class HandleError {
    public static void main(String args[]) {
        int a=0, b=0, c=0;
        Random r = new Random();
        for(int i=0; i<32000; i++) {
            try {
                b = r.nextInt();
                c = r.nextInt();
                a = 12345 / (b/c);
            } catch (ArithmeticException e) {
                System.out.println("Division by zero.");
                a = 0; // set a to zero and continue
            }
            System.out.println("a: " + a);
        }
    }
}
```

## 10.4.1 显示一个异常的描述

- Throwable重载toString()方法（由Object定义），它返回一个包含异常描述的字符串。
- 你可以通过在println()中传给异常一个参数来显示该异常的描述。

catch块可以被重写成

```java
catch (ArithmeticException e) {
    System.out.println("Exception: " + e);
    a = 0;   // set a to zero and continue
}
```

输出：
Exception: java.lang.ArithmeticException: / by zero

## 10.5 使用多重catch语句

- 由单个代码段可能引起多个异常。
- 可以定义多个catch子句，每个子句捕获一种类型的异常。
- 每一个catch子句被依次检查，第一个匹配异常类型的子句执行。
- 当一个catch语句执行以后，其他的子句被旁路。
- 继续从try/catch块以后的代码执行。

## Ans:

C:\>java MultiCatch   // 无命令行参数
a = 0
Divide by 0: java.lang.ArithmeticException: / by zero
After try/catch blocks.

C:\>java MultiCatch TestArg   // 有命令行参数
a = 1
Array index oob: java.lang.ArrayIndexOutOfBoundsException
After try/catch blocks.

## 例P181 父类异常和子类异常的catch语句的顺序

```java
/* This program contains an error. A subclass must come before its
   superclass in a series of catch statements. If not, unreachable
   code will be created and a compile-time error will result. */
class SuperSubCatch {
   public static void main(String args[]) {
      try {
         int a = 0;  int b = 42 / a;
      } catch(Exception e) {
         System.out.println("Generic Exception catch.");
      }

      /* This catch is never reached because
         ArithmeticException is a subclass of Exception. */
      catch(ArithmeticException e) {  // ERROR - unreachable
         System.out.println("This is never reached.");
      }
   }
}
```

## 10.6 嵌套try语句

- 一个try语句可以在另一个try块内部。
- 每次进入try语句，异常的前后关系都会被推入堆栈。
- 若一个内部的try语句不含匹配的catch处理程序，堆栈将弹出，下一个try语句的catch将检查是否与之匹配。
- 过程继续直到一个catch语句匹配成功，或直到所有嵌套try语句被检查耗尽。
- 若无catch匹配，Java运行系统将处理这个异常。

## 例P181

### 嵌套try语句

```java
// An example of nested try statements.
class NestTry {
    public static void main(String args[]) {
        try {
            int a = args.length;
            int b = 42 / a;
            System.out.println("a = " + a);
            try {
                if(a == 1) a = a/(a-a);
                if(a == 2) {
                    int c[] = { 1 };
                    c[42] = 99;
                }
            } catch(ArrayIndexOutOfBoundsException e) {
                System.out.println("Array index out-of-bounds: " + e);
            }
        } catch(ArithmeticException e) {
            System.out.println("Divide by 0: " + e);
        }
    }
}
```

## Ans:

C:\>java NestTry
Divide by 0: java.lang.ArithmeticException: / by zero

C:\>java NestTry One
a = 1
Divide by 0: java.lang.ArithmeticException: / by zero

C:\>java NestTry One Two
a = 2
Array index out-of-bounds:
java.lang.ArrayIndexOutOfBoundsException

## 例P182 嵌套的try块移到了方法nesttry()内部

```java
/* Try statements can be implicitly nested via calls to methods. */
class MethNestTry {
    static void nesttry(int a) {
        try {                                  // nested try block
            if(a==1) a = a/(a-a);              // division by zero
            if(a==2) {
                int c[] = {1};
                c[42] = 99;                    // generate an out-of-bounds exception
            }
        } catch(ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index out-of-bounds: " + e);
        }
    }

    public static void main(String args[]) {
        try {
            int a = args.length;
            int b = 42 / a;
            System.out.println("a = " + a);
            nesttry(a);
        } catch(ArithmeticException e) {
            System.out.println("Divide by 0: " + e);
        }
    }
}
```

![img/489adce8323ca3a7b0e9fe701e6e665c_469_0.png](img/489adce8323ca3a7b0e9fe701e6e665c_469_0.png)

