# 实例操作三：输出全部的key

```
package org.lxh.demo13.mapdemo;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
import java.util.Set;
public class HashMapDemo03 {
    public static void main(String[] args) {
        Map<String, String> map = null;                 // 声明Map对象,
        map = new HashMap<String, String>();            // key和value是String类
        map.put("mldn", "www.mldn.cn");               // 增加内容
        map.put("zhinangtuan", "www.zhinangtuan.net.cn");  // 增加内容
        map.put("mldnjava", "www.mldnjava.com.cn");   // 增加内容
        Set<String> keys = map.keySet();                // 得到全部的key
        Iterator<String> iter = keys.iterator();        // 实例化Iterator
        System.out.print("全部的key: ");               // 输出信息
        while (iter.hasNext()) {                        // 迭代输出全部的key
            String str = iter.next();                   // 取出集合的key
            System.out.print(str + ",");               // 输出内容
        }
    }
}
```