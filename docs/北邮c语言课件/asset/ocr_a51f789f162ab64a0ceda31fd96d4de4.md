# 7.4.4 字符处理函数

C语言库函数中除了前面用到的库函数gets()与puts()之外，还提供了一些常用的库函数，其函数原型说明在string.h中

+   1. 字符串拷贝函数： strcpy()

调用格式： strcpy(d_str,s_str);

功    能： 将源字符串s_str复制到目标字符数组d_str中。

说    明： d_str的长度应不小于s_str的长度，d_str必须写成数组名形式。s_str可以是字符串常量或字符数组名形式。

例： char s1[10], s2[8]= “student” , s3[6];
    strcpy(s1, s2); strcpy(s3,”okey”);

将s2中的”student”赋给s1(连同结束标志 ‘\0’ )， “okey”赋给s3; s2的值不变。

注意： 不能直接使用赋值语句来实现拷贝或赋值。

如： s1=s2; s1= “student” ； 都是不允许的