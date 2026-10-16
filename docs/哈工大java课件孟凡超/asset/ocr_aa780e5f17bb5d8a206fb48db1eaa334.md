# 4.3 字符串类型

# StringBuffer类

系统为String类对象分配内存时，按照对象中所含字符的实际个数等量分配，而为StringBuffer类对象分配内存时，除去字符所占空间外，再加16个字符大小的缓冲区。

对于StringBuffer类对象，使用length方法可获得字符串的长度，另外，还有capacity()方法返回缓冲区的容量。

```
StringBuffer sb=new StringBuffer("Hello world!");
StringBuffer sb1=sb.append(" My name is Zhangsan.");
sb1.append(" How are you!");
System.out.println("length="+sb.length());
System.out.println("capacity="+sb.capacity());
System.out.println("sb="+sb);
System.out.println("sb1="+sb1);
```