# 二、 fread函数和fwrite函数

一般调用形式：

```
fread(buffer,size,count,fp);
```

```
fwrite(buffer,size,count,fp);
```

其中：

buffer:是一个指针(起始地址)。
对fread来说，它是读入数据的存放地址。
对fwrite来说，它是输出数据的地址。

size:要读写的字节数。

count:要进行读写多少个size字节的数据项。

功能：对fp所指的文件读写buffer所指的size*count个字节数据。

例如： fread(f,4,2,fp); （其中f是实型数组名）