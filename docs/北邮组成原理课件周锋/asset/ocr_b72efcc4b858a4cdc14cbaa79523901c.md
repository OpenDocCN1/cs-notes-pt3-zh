# 文件以文本/二进制打开区别1-测试程序

```
```c
for(i=0;i<4;i++)
{
	fputc(s[i],fp1); //以文本方式向文件中写入数据
	fputc(s[i],fp2); //以二进制方式向文件中写入数据
}
fclose(fp1);
fclose(fp2);
if(((fp1=fopen("test1.txt","rt"))==NULL)
{
	printf("can not open file\n");
	exit(0);
}
}
if(((fp2=fopen("test1.txt","rb"))==NULL)
{
	printf("can not open file\n");
	exit(0);
}
}
```
```