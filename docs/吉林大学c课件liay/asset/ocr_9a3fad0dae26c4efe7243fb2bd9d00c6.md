读程序，写结果：

```
#include <iostream>
using namespace std;
class B{
public:
    int i;
    B(int i=0):i(i){
        cout<<i<<"B is constructing\n";}
    B(B& b){i=b.i;
        cout<<i<< " copying B\n";}
    ~B(){ cout<<i<<" destructuring B\n";}
class A{
    int s; static B b;
    B bb;
public:
    A(int k=0,int j=0):s(k),bb(j){
        cout<<s<<"A is constructing\n";};
    ~A(){cout<<s<<" destructuring A\n";}
};
B A::b;
int main()
{
cout<<"main is running\n";
void f(B);
A s1(1,1);
B b1(8);
f(b1);
return 0;
}
void f(B b1){
cout<<"f is running\n";
b1=B(9);
}
A s3(3,3);
```