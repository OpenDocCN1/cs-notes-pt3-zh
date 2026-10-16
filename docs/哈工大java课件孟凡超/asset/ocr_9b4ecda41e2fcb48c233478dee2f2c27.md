# 10.2 基本字节数据流

![](bbox=[0.85, 0.02, 0.98, 0.15])

程序
(内存)

数据

write

输出流

file2.txt

```
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class FileStream1 {

    /**
     * @param args
     */
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        try{
            FileOutputStream out=new FileOutputStream("file2.txt");
            out.write('h');
            out.write('a');
            out.write('r');
            out.write('b');
            out.write('i');
            out.write('n');
            out.close();
        }catch(FileNotFoundException e){
            System.out.println("Error:cannot open file for waiting.");
        }catch(IOException e){
            System.out.println("Error:cannot write to file.");
        }
    }
}
```