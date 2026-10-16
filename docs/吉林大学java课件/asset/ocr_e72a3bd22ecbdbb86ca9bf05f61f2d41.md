# 乱码产生

```
package org.lxh.demo12.charsetdemo;
import java.io.File;
import java.io.FileOutputStream;
import java.io.OutputStream;
public class CharSetDemo02 {
    public static void main(String[] args) throws Exception {
        File f = new File("D:" + File.separator + "test.txt");        // 实例化输出流
        OutputStream out = new FileOutputStream(f);                  // 指定ISO8859-1编码
        byte b[] = "中国, 你好!".getBytes("ISO8859-1");             // 保存转码之后的数据
        out.write(b);                                                // 关闭输出流
        out.close();
    }
}
```