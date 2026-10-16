# 格式化输入



```
```
int fscanf( FILE * fp ,
char * format , arg_list );
```
```



从fp所指文件，按format规定的格式进行转换，读取arg_list对应的数据

返回值 = \begin{cases} 实际读取的参数个数 & 操作成功 \\ 一个负数 & 否则 \end{cases}