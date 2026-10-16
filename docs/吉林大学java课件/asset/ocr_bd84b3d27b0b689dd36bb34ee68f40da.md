# System类应用：计算一个程序的执行时间

```
package org.lxh.demo11.systemdemo;
public class SystemDemo01 {
    public static void main(String[] args) {
        long startTime = System.currentTimeMillis();// 取得开始计算之前的时间
        int sum = 0;
        // 声明变量存放累加后的结果
        for (int i = 0; i < 30000000; i++) {    // 执行累加操作
            sum += i;
        }
        long endTime = System.currentTimeMillis();
        // 开始时间减去结束时间
        System.out.println("计算所花费的时间: " + (endTime - startTime)+"毫秒");
    }
}
```