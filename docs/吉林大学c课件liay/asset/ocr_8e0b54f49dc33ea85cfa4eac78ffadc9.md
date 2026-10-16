# 无名参数

函数的定义和声明中，都可以省略形参名。

```
void print (int ,int);
```

```
void print(int a,int){
    cout<<a<<endl;
}
```

```
void func(){
    print(1,2);
}
```