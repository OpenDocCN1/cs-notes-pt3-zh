# new和malloc比较

+   □ 使用方便性
+     ■ malloc需要计算内存空间大小，通常需要与sizeof函数配合使用
+     ■ malloc的返回值为void*，赋值给某一类型的变量时需要进行强制类型转换
+       □ student *s = (student *)malloc(sizeof(student));
+     ■ new运算符自动计算内存空间大小，而且返回的就是具体的数据类型，不需要进行转换