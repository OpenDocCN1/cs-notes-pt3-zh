# 17.4.1.5 比较

+   1. 为了能在map中找到对应于确定关键码的元素，map必须能够做关键码比较，此外，迭代器也会按照递增的方式遍历map，因此，插入元素时通常也需要元素比较
+   2. 按默认规定，关键码比较采用<，map的value_type是(关键码, 值)对偶，因此提供了value_compare()来进行比较

# 比较

```
template <class Key, class T, class Cmp = less<Key>,
          class A = allocator<pair<const Key,T> > > class map
{
public:
    typedef Cmp key_compare;
    class value_compare : public
        binary_function<value_type,value_type,bool> {
        friend class map;
    protected:
        Cmp cmp;
        value_compare(Cmp c) : cmp(c) {}
    public:
        bool operator()(const T& x, const T& y) const
        { return cmp(x.first, y.first); }
    };
    key_compare key_comp() const;
    value_compare value_comp() const;
};
```

# 比较

```
map<string,int> m1;
map<string,int> m2; // 通过比较类（§17.4.1.4）
map<string,int, Cmp> m3; // 明确比较类（§17.4.1.4）
map<string,int> m4(String cmp(literary)); // 传递比较对象

有关key_comp()和value_comp()成员函数，算法可以按其对一个map的关键码和值做各种比较

需要注意是有另外一个容器没有这种比较机制但仍能遍历map
void f(map<string,int>& m)
{
    map<string,int> mm; // 按默认方式使用关键比较
    map<string,int> mm(m.key_comp()); // 使用m的方式比较
    // ...
}
```

# 17.4.1.6 映射操作

```
template <class Key, class T, class Cmp = less<Key>,
          class A = allocator<pair<const Key,T> > > class map {
public:
    // 散射操作
    iterator find(const key_type& k); // 查找关键码为k的元素
    const_iterator find(const key_type& k) const;
    size_type count(const key_type& k) const; // 关键码为k的元素个数
    iterator lower_bound(const key_type& k); // 首个键为大于等于k的元素
    const_iterator lower_bound(const key_type& k) const;
    iterator upper_bound(const key_type& k); // 首个键为大于k的元素
    const_iterator upper_bound(const key_type& k) const;
    pair<iterator,iterator> equal_range(const key_type& k);
    ...
};
```