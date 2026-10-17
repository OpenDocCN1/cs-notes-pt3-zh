# # 定义对象有三种形式

# ## (2) 在声明类类型的同时定义对象

```
```cpp
class Date
{
    public:
        void Set(int m, int d, int y ){…}
        int IsLeapYear() {…}
        void Print( ) {…}
    private:
        int month;
        int day;
        int year;
} d1, d2;
```
```