# # 例P189

# # 创建自己的异常子类

```
```java
// This program creates a custom exception type.
class MyException extends Exception {
  private int detail;
  MyException(int a) {
    detail = a;
  }
  public String toString() {
    return "MyException[" + detail + "]";
  }
}
```
```