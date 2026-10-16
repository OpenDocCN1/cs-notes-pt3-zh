# 4. 继承与指针（3）

```
class Automobile{
public:
//...
void Turn(){
    cout<< "助力转向" <<endl;
}
};

class Car:public Automobile{
public:
//...
};
```

```
void main(){
    Automobile ObjA;
    Car ObjB;
    Automobile *pA = &ObjA;
    Car *pB = &ObjB;
    pA->Turn();
    pB->Turn();
}
```

助力转向

助力转向