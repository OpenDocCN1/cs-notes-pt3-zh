# fopen使用惯例

+   - 只在windows下可用
+     - FILE *fp = fopen("C:\\AUTOEXEC.BAT", "r+");
+   - linux和windows下都可用
+     - FILE *fp = fopen("..\\AUTOEXEC.BAT", "r+");
+   - 一定要判断fopen是否成功！

Demo 1: open and close file

```
1 FILE *fp = fopen("test.txt", "w+");
2 if(fp == NULL){
3     printf("%s file failure","test.txt");
4     exit(1);
5 }
6 
7 fclose(fp);
```