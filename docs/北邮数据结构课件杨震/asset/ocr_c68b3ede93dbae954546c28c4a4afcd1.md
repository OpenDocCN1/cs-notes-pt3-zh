```
```cpp
template<typename NT>
NT* merge(NT* a, NT*&b)
{
    NT* const END = 0;
    if(b->value_ < a->value_)
        std::swap(a, b);
    NT* pa = a;
    NT* ca = pa->next_;
    while(ca != END && b != END)
        if(b->value_ < ca->value_)
        {
            pa->next_ = b;    pa = b;
            b = b->next_;     pa->next_ = ca;
        }
        else
        {
            pa = ca;           ca = ca->next_;
        }
    if(ca == END)
        pa->next_ = b;
    return a;
}
```
```

时间复杂度：**O(nlog₂n)**

空间复杂度：**O(1)**---键值不需要做移动，修改指针即可