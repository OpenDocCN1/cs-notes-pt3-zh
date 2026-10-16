# 将字节输入流变为字符输入流

```
package org.lxh.iodemo.changeiodemo;
import java.io.File;
import java.io.FileInputStream;
import java.io.InputStreamReader;
import java.io.Reader;
public class InputStreamReaderDemo01 {
    public static void main(String[] args) throws Exception { // 所有的异常抛出
        File f = new File("d:" + File.separator + "test.txt");
        Reader reader = null;
        reader = new InputStreamReader(new FileInputStream(f)); // 将字节流变为字符流
        char c[] = new char[1024];
        int len = reader.read(c);
        reader.close();
        System.out.println(new String(c, 0, len));
    }
}
```