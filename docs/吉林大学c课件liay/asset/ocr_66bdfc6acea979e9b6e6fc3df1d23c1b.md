# 文件流类

在fstream里面定义
ofstream 文件输出类  ifstream 文件输入类  fstream是多继承子类

没有cout和cin这样的标准全局对象。

```
ofstream::ofstream(char * pFilename,
                     int mode=ios::out);
```

| Mode:打开方式 |  |
|---|---|
| ios::app | 如果文件存在末尾追加 |
| ios::trunc | 如果文件存在清除内容（默认） |
| ios::in | 以输入的方式打开文件（ifstream默认） |
| ios::out | 以输出的方式打开文件（ofstream默认） |
| ios::ate | 打开一个已有的文件，指针指向末尾 |
| ios::binary | 二进制方式 |

（可以以位或的方式组合ios::in|ios::binary）