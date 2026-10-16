# 将字节输出流变为字符输出流

```
package org.lxh.iodemo.changeiodemo;
import java.io.File;
import java.io.FileOutputStream;
import java.io.OutputStreamWriter;
import java.io.Writer;
public class OutputStreamWriterDemo01 {
    public static void main(String[] args) throws Exception { // 所有的异常抛出
        File f = new File("d:" + File.separator + "test.txt");
        Writer out = null;
        out = new OutputStreamWriter(new FileOutputStream(f)); // 字节流变为字符流
        out.write("hello world");        // 使用字符流输出
        out.close();
    }
}
```

![](bbox=[0.63, 0.71, 0.92, 0.82])