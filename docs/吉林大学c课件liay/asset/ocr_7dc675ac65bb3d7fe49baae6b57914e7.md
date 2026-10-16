# 异常处理

```
#define MAX 10
int f(int * a,int j)
{
    if(j>=0&&j<MAX)
        return(a[j]);
    else
        throw "aaaa";
}
void main()
{ int j;
int a[MAX]={0};
    try{
    cout<<f(a,15)<<endl;}
    catch(string s){
        cout<<s<<endl;
    }
}
```

（1）定义异常（try语句块）
将那些有可能会产生错误的语句放在try块中

（2）抛掷异常（throw语句）
检测是否产生异常，若是，则抛掷异常。

（3）捕捉异常,定义异常处理（catch语句块）
将异常处理语句放在catch块中,以便异常被传递过来时就处理它。

C++只理会受监控的异常。
Try块之后必须紧跟一个或多个catch语句。
Catch括号中只能容纳一个形参，与throw抛掷的异常类型匹配时，便捕获了异常。
避免把正常逻辑淹没在错误处理代码中，从而使程序更易于阅读。