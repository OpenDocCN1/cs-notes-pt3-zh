# 堆栈—stack

stack就像是容器的一个简单界面。容器类作为参数模板参数适配器stack，stack所做的全部事情就是从它的容器的界面中删除所有非stack操作，并将back()、push_back()和pop_back()改为它们习惯的名字top()、push()和pop()

top()函数只读取，pop()操作只删除栈顶元素

按默认设定，stack使用一个deque来保存自己的元素，但也可以采用任何提供了back()、push_back()和pop_back()的序列

```
stack<char> s1; // 用deque<char>作为char类型的元素
stack<int, vector<int>> s2; // 用vector<int>作为int类型的元素
```

# 17.3.2 队列—queue

queue在概念上定义它也是一个容器类适配器。该类接受元素在back()处进入队列，且能从front()处取出来

```
template <class T, class C = deque<T> : class std::queue {
protected: C c;
public:
typedef typename C::value_type value_type;
typedef typename C::size_type size_type;
typedef C container_type;
explicit queue(const C& c0 = C()) : c(c0) {}
bool empty() const { return c.empty(); }
size_type size() const { return c.size(); }
value_type& front() { return c.front(); }
const value_type& front() const { return c.front(); }
value_type& back() { return c.back(); }
const value_type& back() const { return c.back(); }
void push(const value_type& x) { c.push_back(x); }
void pop() { c.pop_front(); }
};
```

# 队列—queue

按照默认规则，queue用deque保存自己的元素，但是任何提供了front()、back()、push_back()和pop_front()的序列都可以用(vector没有提供pop_front()，所以不能作为queue的基础容器)

对于queue，也是使用push()添加元素，使用pop()删除元素

# 17.3.3 优先队列—priority_queue

```
template <class T, class C = vector<T>>
class Cmp = less<typename C::value_type>> class std::priority_queue{
protected: C c; Cmp cmp;
public:
typedef typename C::value_type value_type;
typedef typename C::size_type size_type;
typedef C container_type;
explicit priority_queue(const Cmp& a1 = Cmp(), const C& a2 = C())
: c(a2), cmp(a1) {}
template <class It>
priority_queue(It first, It last, const Cmp& a1 = Cmp(), const C& a2 = C());
bool empty() const { return c.empty(); }
size_type size() const { return c.size(); }
const value_type& top() const { return c.front(); }
void push(const value_type&);
void pop();
};
```