# 8. 困惑的解决方案

```
class Automobile{
public:
// ...
int flag;
Automobile(int k):flag(k){}
void Run(){
    cout<< "机械变速" <<endl;
}
};

class Car:public Automobile{
public:
// ...
Car(int k):Automobile(k){}
void Run(){
    cout<< "自动变速 " <<endl;
}
};
```

```
void Fn(Automobile *p){
    switch(p->flag){
        case 1: p->Run();break;
        case 2: //p->Car::Run();
            static_cast<Car*>(p)->Run();
            break; }
    delete p;
}

void main(){
    Fn(new Automobile(1));
    Fn(new Car(2));
}
```

最大的问题在于如果继承体系变动，则需要影响到程序的所有的部分，相互依赖度高，代价太大；