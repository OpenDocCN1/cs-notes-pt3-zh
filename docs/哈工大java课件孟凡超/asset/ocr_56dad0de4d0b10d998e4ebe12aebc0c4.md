# 10.2 基本字节数据流

# 数据数据流示例(2)

```
```java
DataInputStream in = new DataInputStream(
new FileInputStream("D:/java/Java2s.txt"));
double price;
int unit;
String desc;
double total = 0.0;
try {
while (true) {
price = in.readDouble();
in.readChar(); // throws out the tab
unit = in.readInt();
in.readChar(); // throws out the tab
desc = in.readline();
System.out.println( desc );
System.out.println( price );
System.out.println( unit );
total = total + unit * price;
System.out.println( total );
}
} catch (EOFException e) {
}
in.close();
```
```