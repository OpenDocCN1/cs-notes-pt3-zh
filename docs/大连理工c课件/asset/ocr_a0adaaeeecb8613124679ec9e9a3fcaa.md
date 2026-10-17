# 9.3 流操作

# 字符输入函数

```
istream& istream::get(char &ch);
```

功能:带参数的get函数也能从流中读取一个字符，
所读取的字符存储在参数ch中。
如果读取字符不成功，设置错误标志并在ch中存储EOF

```
while(cin.get(c)) cout.put(c);
while(cin >> c) cout<<c;
```

![](bbox=[0.75, 0.62, 0.95, 0.75])