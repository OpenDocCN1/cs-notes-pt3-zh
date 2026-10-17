# # 使用对话框输出

需要导入swing包。使用JOptionPane对象的showMessageDialog()方法：
JOptionPane.showMessageDialog(null,输出字符串);

举例：

```
```java
import javax.swing.*;
class T1 {
    public static void main(String args[]) {
        String st = "王小红";
        JOptionPane.showMessageDialog(null, st + "你好!!");
        System.exit(0);
    }
}
```
```

![](bbox=[0.551, 0.717, 0.973, 0.966])