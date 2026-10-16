# [例1]设计函数，将键盘上输入的字符串（以ctrl+Z 作为结束字符）逐个字符存储到指定文本文件中

```
void writeFileFromKeyboard(char * filename)
{
    char ch;
    FILE * fPtr=NULL;
    if((fPtr=fopen(filename,"w"))!=NULL){ //打开文件
        while((ch=getchar())!=EOF) //从键盘读取字符写入文件
            fputc(ch, fPtr);
        fclose(fPtr); //关闭文件。执行本语句后，数据将被写入文件中。
        //如果缓冲区未满且不关闭文件，则数据不会写入文件中。
    }
}
```

This is an example
To read and write
^Z