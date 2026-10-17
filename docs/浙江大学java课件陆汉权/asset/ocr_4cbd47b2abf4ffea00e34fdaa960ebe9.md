# Java实例——以字节流方式写入文件

```
```java
import java.io.*;
public class File2{
    public static void main(String[] args) throws IOException{
        char ch;
        File file1=new File("c:\\jdk1.3\\example\\newFile.txt");
        try{
            FileOutputStream fout= new FileOutputStream(file1);
            System.out.println("输入任一字符串，以?结束");
            ch=(char) System.in.read();
            while (ch != '?'){
                fout.write(ch);
                ch=(char) System.in.read();
            }
            fout.close();
        }
        catch (FileNotFoundException e) { System.out.println(e);}
        catch (IOException e) { System.out.println(e);}
    }
}
```
```