# 6.1 异常

```
{
    openTheFile;
    if(theFileOpen){
        determine the length of the file;
        if(gotTheFileLength){
            allocate that much memory;
            if(gotEnoughMemory){
                read the file into memory;
                if(readFailed) errorCode==-1;
                else errorCode==-2;
            }else errorCode==-3
        }else errorCode==-4;
    }else errorCode==-5
}
```

虽然程序的鲁棒性加强了，但程序的结构臃肿，大量的错误处理代码混杂在其中，可读性差，目标程序也会增大许多。