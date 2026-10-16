# 示例

```
// 标准库提供了 一个模板类basic_string，其中，string被定义为 basic_string<char>，构造又可 typedef basic_string<char> string;

int main()
{
    string buf;
    map<string, int> m;
    while(cin>>buf) m[buf]++;
}
```

# 13.2.1 定义一个模板

+   - 一个由类模板生成的类也是一个完全正常的类
+   - 方法：先做好特定的类，如String，并排除其中错误，然后再将它转化为String<C> 一类的模板
+   - 模板类中成员的声明和定义与在非模板类里完全一样，模板类的成员也不一定要在类内部定义，可以在外部定义，成员本身也是模板参数化的

# 定义一个模板示例

```
template<class C> class String
{
    struct Srep;
    Srep* rep;
public:
    String();
    String(const C*);
    String(const String&);
    C read(int i) const;
    //...
};

template<class C> struct String<C>::Srep {
    C* s;
    int sz;
    int n;
};

template<class C> String<C>::String(const C* s) {
    return rep->s[i];
}

template<class C> String<C>::String()
{
    rep = new Srep(0,C());
};
```

# 定义一个模板示例

类模板的名字不能重载

```
template<class T> class String{...};
class String{...}; // 错误，重复定义
```