

## 为避免将空列表作为特殊情况处理，引入哑头节点：

![](img/15e8d7d94d8ddf02cb6839870195a31e_208_0.png)

![](img/15e8d7d94d8ddf02cb6839870195a31e_208_1.png)

data link

empty circular list

## 4.5 可用空间列表

-   链和循环列表的析构函数时间与链或列表的长度成线性关系。
-   如果我们维护自己的空闲节点链，则可以将其降低到 O(1)。
-   可用空间列表由 `av` 指向。
-   `av` 是 `CircularList<T>` 的静态类成员，类型为 `ChainNode<T>*`，初始时，`av = 0`。
-   只有在 av 列表为空时我们才需要使用 new。

## 我们使用 `CircularList<T>::RetNode` 而不是使用 `delete`：

```
template <class T>
void CircularList<T>::RetNode(ChainNode<T> * x)
{
    // free the node pointed to by x
    x->link = av;
    av = x;
    x = 0;
}
```

## 循环列表可以在 O(1) 中被删除：

```
template <class T>
void CircularList<T>::~CircularList()
{ // delete the circular list.
    if (last) { ChainNode <T> * first = last->link;
        last->link = av;  // (1)
        av = first; // (2)
        last = 0;
    }
}
```

![](img/15e8d7d94d8ddf02cb6839870195a31e_212_0.png)

## 如果我们知道其首尾节点，则链可以在 O(1) 中被删除：

```
template <class T>
Chain<T>::~Chain()
{ // delete the chain
    if (first) {
        last->link = av;
        av = first;
        first = 0;
    }
}
```

## 4.6 链表栈和队列

![](img/15e8d7d94d8ddf02cb6839870195a31e_214_0.png)

假设 LinkedStack 类已被声明为 ChainNode<T> 的友元。

```
template <class T>
class LinkedStack {
public:
    LinkedStack() { top=0;}; // constructor initializing top to 0
    // LinkedStack manipulation operations
    ...
private:
    ChainNode<T> *top;
};
```

```
template <class T>
void LinkedStack<T>::Push(const T& e) {
    top = new ChainNode<T>(e, top);
}
```

```
template <class T>
void LinkedStack<T>::Pop()
{ // delete top node from the stack.
    if (IsEmpty()) throw "Stack is empty. Cannot delete.";
    ChainNode<T> * delNode = top;
    top = top->link;
    delete delNode;
}
```

IsEmpty 和 Top 函数易于实现，且被省略。

![](img/15e8d7d94d8ddf02cb6839870195a31e_217_0.png)

front

data link

rear

linked queue

LinkedQueue 的函数与 LinkedStack 类似，留作练习。

Exercises: P201-2

## 4.7 多项式

### 4.7.1 多项式表示

由于多项式将由列表表示，我们说 Polynomial 是 IS-IMPLEMENTED-IN-TERMS-OF List。

定义：类型 A 的数据对象 IS-IMPLEMENTED-IN-TERMS-OF 类型 B 的数据对象，如果类型 B 对象是类型 A 对象实现的核心。---通常通过将类型 B 对象声明为类型 A 对象的成员数据来实现。

```
```java
class Polynomial {
public:
    // public functions defined here
private:
    Chain<Term> poly;
};
```
```

![](img/15e8d7d94d8ddf02cb6839870195a31e_220_0.png)

### 4.7.2 加法多项式

要将两个多项式 a 和 b 相加，使用链迭代器 ai 和 bi 沿着 a 和 b 的项移动。

```
1 Polynomial Polynomial::operator+ (const Polynomial& b)
2 { // *this (a) and b are added and the sum returned
3   Term temp;
4   Chain<Term>::ChainIterator ai = poly.begin(),
5                         bi = b.poly.begin();
6   Polynomial c;
```

```
```cpp
while (ai != poly.end() && bi != b.poly.end()) { //not null
    if (ai->exp == bi->exp) {
        int sum = ai->coef + bi->coef;
        if (sum) c.poly.InsertBack(temp.Set(sum, bi->exp));
        ai++; bi++; // to next term
    }
    else if (ai->exp < bi->exp) {
        c.poly.InsertBack(temp.Set(bi->coef, bi->exp));
        bi++; // next term of b
    }
    else {
        c.poly.InsertBack(temp.Set(ai->coef, ai->exp));
        ai++; // next term of a
    }
}
```
```

