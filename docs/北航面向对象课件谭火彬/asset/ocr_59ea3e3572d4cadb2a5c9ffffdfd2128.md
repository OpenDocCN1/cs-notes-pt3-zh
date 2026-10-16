# 面向对象的编程—C++语法

```
class Item{
public:
        Item* source;
        Item (Item* src) {source=src;}
        virtual int out() {return 0;}
};

class Counter: public Item{
        int value;
public:
        int out() {return value++;}
        Counter(int v):Item(0){value=v;}
};
```