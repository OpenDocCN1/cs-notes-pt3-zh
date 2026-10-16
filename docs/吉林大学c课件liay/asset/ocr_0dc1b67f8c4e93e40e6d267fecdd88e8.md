# 输出输入

```
#include <iostream>
using namespace std;
void main()
{
char a[20];
cin>>a;
cout<<a<<endl;

cin.getline(a,11,'a');
cout<<endl<<a;
}
```

运行程序结果：
He told me a news
He

told me

输入数据按回车键后，数据才被送入键盘缓冲区，形成输入流 istream流类成员函数的使用可以更加精细的控制输入