# Unix I/O、标准 I/O 和 RIO之间的关系

标准 I/O 和 RIO 是基于较低级的 Unix I/O 函数来实现的。

```
fopen  fdopen
fread  fwrite
fscanf fprintf
sscanf sprintf
fgets  fputs
fflush fseek
fclose
```

```
open  read
write lseek
stat  close
```

![](bbox=[0.31, 0.38, 0.78, 0.7])

```
rio_readn
rio_writen
rio_readinitb
rio_readlineb
rio_readnb
```

我该使用哪些 I/O 函数？