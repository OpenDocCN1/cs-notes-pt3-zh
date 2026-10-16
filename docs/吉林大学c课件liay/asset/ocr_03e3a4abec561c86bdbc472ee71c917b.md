# 7. 多态希望

```
class Automobile{
public:
    //...
    void Run(){
        cout<< "机械变速" <<endl;
    }
};

class Car:public Automobile{
public:
    //...
    void Run(){
        cout<< "自动变速" <<endl;
    }
};
```

```
void Fn(Automobile *p){
    p->Run();
}

void main(){
    Fn(new Automobile);
    Fn(new Car);
}
```

机械变速
自动变速