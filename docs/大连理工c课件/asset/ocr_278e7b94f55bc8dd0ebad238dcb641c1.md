# # 9.4 文件流

# ## 例9.10 使用getline从文件中读取字符串

```
char filename[10]="D://test",str[20];
ofstream outfile(filename,ios::out|ios::app);
outfile << filename <<endl;
cout<<"input a string:";
cin.getline(str,20);    // 键盘输入字符串
outfile << str <<endl;  // 向文件写入字符串
outfile.close();
```