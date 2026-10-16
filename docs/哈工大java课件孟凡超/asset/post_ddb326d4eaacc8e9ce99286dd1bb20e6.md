
## 10.4 文件的处理

移动文件读写指针的方法：

- long getFilePointer(): 返回文件指针的当前位置
- void seek(long pos): 将文件指针置于指定的绝对位置。位置值以从文件开始处的字节偏移量pos来计算，pos为0代表文件的开始
- long length(): 返回文件的长度。位置值为length(), 代表文件的结尾

例：

```
myRAFile=new RandomAccessFile("temp.txt",
"rw");
myRAFile.seek(myRAFile.length());
```

文件的读写指针移至文件的末尾，如果调用write()方法，那么所写入的信息就添加到原文件之后。
