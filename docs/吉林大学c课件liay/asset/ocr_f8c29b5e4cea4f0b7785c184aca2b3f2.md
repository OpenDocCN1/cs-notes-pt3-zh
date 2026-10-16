# 构造、析构函数

```
class A{
public:
    int s;
private:
    A(){cout<<"A is constructing\n";};
    ~A(){cout<<"~A\n";}
};
int main(){
    A s;  //出错
    return 0;}
//构造函数&析构函数的属性影响
```