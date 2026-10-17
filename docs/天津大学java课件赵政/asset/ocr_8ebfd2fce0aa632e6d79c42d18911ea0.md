# # 例 P59上

# # 将结果转换为byte型

```
```java
// Left shifting a byte value.
class ByteShift {
  public static void main(String args[]) {
    byte a = 64, b;
    int i;   // << 2
    i = a << 2;   // 64=0100 0000->1 0000 0000
    b = (byte) (a << 2);
    System.out.println("Original value of a: " + a);
    System.out.println("i and b: " + i + " " + b);
  }
}
```
```