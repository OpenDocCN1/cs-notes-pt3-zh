# 13.4 用模板参数描述策略

+   - 考虑字符串排序，涉及到三个概念：串(容器)、元素类型和排序算法
+   - 一般来说，无法将排序算法编码到容器中，而且也无法将排序算法编码到元素类型
+   - 通用解决方法是使用通用的方式描述排序算法，并且该算法可以用于各种类型的数据排序

```
template<class T, class C>
int compare(const String<T>& str1, const String<T>& str2) {
  // 使用中缀表达式的方式进行比较
  for(int i=0; i<str1.length() && i<str2.length(); i++)
    if(C::eq(str1[i],str2[i])) return C::lt(str1[i],str2[i]) ? -1 : 1;
  return str1.length()-str2.length();
}
```

# 用模板参数描述策略示例

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

# 13.4.1 默认模板参数

+   - 每次调用都需要显式地给出比较准则也会使人厌烦，为此，可以使用函数重载，也可以使默认模板参数

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

# 默认模板参数示例

```
// 然而我们也可以为函数调用使用compare
void f(String<char>* swede1, String<char>* swede2) {
  compare(swede1, swede2); // 默认Cmp<char>
  compare<char, Literate>(swede1, swede2); // 用Literate
}
```

+   - 通过模板参数支持执行策略，以及在此基础上采用默认值支持最常用策略的技术在标准库中广泛使用
+   - 用于表示策略的模板参数常被称为“特征”(traits)，例如：标准库string依赖于char_traits，标准算法依赖于迭代器特征，所有标准库容器依赖于allocator