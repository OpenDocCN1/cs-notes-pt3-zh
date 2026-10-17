```
String :: String ( const char *init ) {
//复制构造函数：从已有字符数组*init复制
ch = new char[maxLen+1]; //创建串数组
if ( ch == NULL ){
cerr << "存储分配错！\n";
exit(1);
}
curLen = strlen ( init ); //复制串长度
strcpy ( ch, init ); //复制串值
}
```