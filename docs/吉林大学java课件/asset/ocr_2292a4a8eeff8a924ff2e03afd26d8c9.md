# 使用foreach输出

```
package org.lxh.demo13.iteratordemo;
import java.util.ArrayList;
import java.util.List;
public class ForeachDemo01 {
    public static void main(String[] args) {
        List<String> all = new ArrayList<String>();    // 实例化List接口
        all.add("hello");                             // 增加元素
        all.add("_");                                 // 增加元素
        all.add("world");                             // 增加元素
        for (String str : all) {                       // 输出foreach输出
            System.out.print(str + ",");               // 输出内容
        }
    }
}
```