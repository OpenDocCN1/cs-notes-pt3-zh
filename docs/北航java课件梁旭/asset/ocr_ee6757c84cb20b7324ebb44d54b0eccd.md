# 2.6　简单的输出与输入

# 3、整数和双精度数的输入

其他类型的数据输入必须通过字符串输入方法得到数据，再通过基本数据类的方法将字符串转换为相应类型的数据。

+   - `Integer.parseInt(String);` //将数字字符串转换为整数
+   - `Double.parseDouble(String);` //将字符串形式的数字数据转化为双精度数。
+   - 例：`String x="123";`
+     `int m = Integer.parseInt(x); //m=123;`