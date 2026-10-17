```
```cpp
class Simple
{
    int x, y;
public:
    void setXY ( int a, int b ) { x = a; y = b; }
    void setXY ( int a, int b ) { this->x = a; this->y = b; }
};

void main()
{
    Simple obj1 (10, 15), obj2, obj3;
    obj1.printXY ( );
    obj2.setXY (20, 25 );
    obj2.printXY ( );
    obj3.setXY (30, 35 );
    obj3.printXY ( );
}
```
```

![](bbox=[0.53, 0.63, 0.94, 0.88])