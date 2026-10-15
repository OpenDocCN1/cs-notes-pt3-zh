# 例10-26

利用类型特征实现算法：

```
//将来自输入迭代器p的n个数值排序，将结果通过输出result输出
template <class InputIterator, class OutputIterator>
void mySort(InputIterator first, InputIterator last, OutputIterator result) {
//通过输入迭代器p将输入数据存入向量容器s中
vector<typename iterator_traits<InputIterator>::value_type> s(first, last);
//对s进行排序，sort函数的参数必须是随机访问迭代器
sort(s.begin(), s.end());
//将s序列通过输出迭代器输出
copy(s.begin(), s.end(), result);
}
```