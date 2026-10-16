# 实例操作一：创建一个新文件

```
package org.lxh.demo12.filedemo;
import java.io.File;
import java.io.IOException;
public class FileDemo01 {
    public static void main(String args[]) {
        File f = new File("d:\\test.txt");        // 必须给出完整路径
        try {
            f.createNewFile();;                     // 根据给定的路径创建新文件
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```