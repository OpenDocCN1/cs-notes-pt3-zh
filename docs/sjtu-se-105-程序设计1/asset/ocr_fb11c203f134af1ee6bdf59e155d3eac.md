+   - 类必须将重载函数集中每一个希望设为友元的函数都声明为友元：

```
extern std::ostream& storeOn(std::ostream&, Screen&);
extern BitMap& storeOn(BitMap&, Screen&);
class Screen {
    friend std::ostream& storeOn(std::ostream&, Screen&)

```

+   - 类Screen将接受一个ostream&的storeOn版本设为自己的友元，接受一个BitMap&的版本对Screen没有特殊访问权