# 文件更新注意事项2-死循环

```
fseek(fp,0L,1); //若无这一句，就死循环
//fflush(fp); //起的作用和上一句一样
}//end if ch=='c'
ch=fgetc(fp);
}//end while
fclose(fp);
}//end else 文件打开成功！
return 0;
}
```

思考：读取和写入的缓冲区是同一个，还是分开的？