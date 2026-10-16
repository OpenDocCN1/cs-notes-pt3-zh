

## 函数模板的参数示例

累积描述的最常见用途是为模板参数提供返回值类型

可以将 implicit_cast 解释为隐式转换的一个显式模板

```
template<class T, class U> T implicit_cast(U u) {return u;}
void g(int i)
{
    implicit_cast(i); // 拷贝, 无转换, T 推导
    implicit_cast<double>(i); // T 为 double, U 为 int
    implicit_cast<char>(double(i)); // T 为 char, U 为 double, 可以
    implicit_cast<char*>(int(i)); // T 为 char*, U 为 int
    // 错误, 无法将 int 转换为 char*
}
```

## 13.3.2 函数模板的重载

可以声明多个具有同样名字的函数模板，甚至可以声明具有同一个名字的多个函数模板和常规函数数组的组合

```
template<class T> T sqrt(T);
template<class T> complex<T> sqrt(complex<T>);
double sqrt(double);

void f(complex<double> z)
{
    sqrt(2); // sqrt<int>(int)
    sqrt(2.0); // sqrt(double)
    sqrt(z); // sqrt<double>(complex<double>)
}
```

### 模板函数重载规则

找出了与这一重载解析的二维模板参数的专门化。例如，sqrt(z)产生候选函数 sqrt<double>(complex<double>) 和 sqrt<complex<double>>(complex<double>)

如果两个模板函数都可用，而其中一个比另外一个更专一，在随后的步骤中就只有那一个最专一的模板函数被考虑。例如，sqrt(z)意味着 sqrt<double>(complex<double>) 而非 sqrt<complex<double>>(complex<double>)

### 模板函数重载规则

在某些函数上被重载解析，包括那些常规函数，如果某个函数参数数据已经通过模板参数推断确定下来，这个参数就不能同时通过模板推断、标准转换或者用户定义的转换。对于 sqrt(2)， sqrt<int>(int) 是精确匹配，优先于 sqrt(double)

如果一个函数和一个专门化具有相同的匹配，那么就选用函数，因此，sqrt(2.0) 将选用 sqrt(double) 而不是 sqrt<double>(double)

如果找不到匹配者或找到多个匹配，都产生错误

## 模板函数重载示例

```
template<class T> T max(T,T);
const int s = 7;
void f() {
    max(1,2); // max<int>
    max('a','b'); // max<char>
    max(2.7,4.9); // max<double>
    max(3,7); // max<int>(s,7)
    max('a',1); // 错误，歧义
    max(2.7,4); // 错误，歧义
}
void f() { // 显式限定，避免歧义
    max<int>('a',1);
    max<double>(2.7,4);
}
```

### 模板函数重载示例

也可以增加适当的声明来避免歧义

```
int max(int i, int j) { return max<int>(i,j); }
double max(int i, double d) { return max<double>(i,d); }
double max(double d, int i) { return max<double>(d,i); }
double max(double d1, double d2)
{ return max<double>(d1,d2); }

void g() {
    max('a',1); // max(int('a'),1)
    max(2.7,4); // max(2.7,double(4))
}
```

### 模板函数重载示例

重载解析规则保证模板函数能够正确地与继承机制相互作用

```
template<class T> class B{/*...*/};
template<class T> class D : public B<T>{/*...*/};
template<class T> void f(B<T>*);

void g(B<int>* pb, D<int>* pd)
{
    f(pb); // f<int>(pb)
    f(pd); // f<int>(static_cast<B<int>*>(pd))
}
```

### 模板函数重载示例

在对模板参数的推断中未涉及到的那些函数参数，亦完全会按照其模板所求的参数处理。特别是可以使用普通的转换规则

```
template<class T, class C> T get_nth(C& p, int n);
// 取容器C中的第n个元素并将其返回
struct Index {
    operator int();
};
void f(vector<int>& v, short s, Index i)
{
    int i1 = get_nth<int>(v, 2); // 确定匹配
    int i2 = get_nth<int>(v, s); // 标准转换，short到int
    int i3 = get_nth<int>(v, Index); // 用户定义转换，Index到int
}
```

## 13.4 用模板参数描述策略

- 考虑字符串排序，涉及到三个概念：串(容器)、元素类型和排序算法
- 一般来说，无法将排序算法编码到容器中，而且也无法将排序算法编码到元素类型
- 通用解决方法是使用通用的方式描述排序算法，并且该算法可以用于各种类型的数据排序

```
template<class T, class C>
int compare(const String<T>& str1, const String<T>& str2) {
  // 使用中缀表达式的方式进行比较
  for(int i=0; i<str1.length() && i<str2.length(); i++)
    if(C::eq(str1[i],str2[i])) return C::lt(str1[i],str2[i]) ? -1 : 1;
  return str1.length()-str2.length();
}
```

### 用模板参数描述策略示例

```
template<class T> class Cmp { // 采用从此比较
public:
  static int eq(T a, T b) {return a==b;}
  static int lt(T a, T b) {return a<b;}
}
class Literate {
public:
  static int eq(char a, char b){return a==b;}
  static int lt(char,char);
}; // 忽略大小写输入他们的名字

void f(String<char>* swede1,
       String<char>* swede2) {
  compare<char, Cmp<char> >(swede1, swede2);
  compare<char, Literate>(swede1, swede2);
}
```

将比较操作作为模板参数有两个优点：可通过一个参数传递给函数；没有任何运行时额外开销

## 13.4.1 默认模板参数

- 每次调用都需要显式地给出比较准则也会使人厌烦，为此，可以使用函数重载，也可以使默认模板参数

```
// 取消参数
template<class T, class C=... > // 默认比较
int compare(const String<T>& str1, const String<T>& str2);
template<class T> // 默认Cmp<T>比较
int compare(const String<T>& str1, const String<T>& str2);

template<class T, class C=... > // 默认按字符比较
int compare(const String<T>& str1, const String<T>& str2) {
  for(int i=0; i<str1.length() && i<str2.length(); i++)
    if(C::eq(str1[i],str2[i])) return C::lt(str1[i],str2[i]) ? -1 : 1;
  return str1.length()-str2.length();
}
```

### 默认模板参数示例

```
// 然而我们也可以为函数调用使用compare
void f(String<char>* swede1, String<char>* swede2) {
  compare(swede1, swede2); // 默认Cmp<char>
  compare<char, Literate>(swede1, swede2); // 用Literate
}
```

- 通过模板参数支持执行策略，以及在此基础上采用默认值支持最常用策略的技术在标准库中广泛使用
- 用于表示策略的模板参数常被称为“特征”(traits)，例如：标准库string依赖于char_traits，标准算法依赖于迭代器特征，所有标准库容器依赖于allocator

