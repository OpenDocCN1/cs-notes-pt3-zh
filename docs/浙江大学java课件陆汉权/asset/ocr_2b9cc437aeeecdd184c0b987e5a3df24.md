# 例一以字符流方式读取文件

```
```java
import java.io.*;
public class File9
{
    public static void main(String args[]) throws Exception
    {
        FileReader fr1 = new FileReader("c:\\jdk1.3\\example\\dataFile.txt");
        BufferedReader br1 = new BufferedReader(fr1);
        BufferedWriter bw1 = new BufferedWriter(
        new FileWriter("c:\\jdk1.3\\example\\targetFile.txt"));
        int lineNum=0;
        String s=br1.readLine();
```
```