# 顺序表元素的添加

```
template<typename T>
Struct Vector {
    void push_back(T const& t)
    {//添加在向量尾部
        if (full())
            reverse(next_capacity());
        elem[size++];
    }
    void insert(Iterator pos, T const &t)
    {
        if (full())
        {//添加在pos之前
            int count offset=pos-elem;
            reserve(next_capacity());
            pos=elem+offset;
        }
        memmove(pos+1,pos,
        sizeof(T)*(elem+size++ -pos));
        *pos=t;
    }
}
```

![](bbox=[0.45, 0.2, 0.995, 0.52])

+   [性能分析]
+   • 最好 i=n 不用移动结点
+     时间复杂度 O(1)
+   • 最差 i=0 需移动所有结点
+     时间复杂度 O(n)
+   • 平均
+     O(n)