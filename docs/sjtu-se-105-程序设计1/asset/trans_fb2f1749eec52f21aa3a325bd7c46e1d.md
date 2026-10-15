

- 下面是这个抽象数据类型的“不完整”的定义：
```
class IntSet {
    // OVERVIEW: a mutable set of integers
public:
    void insert(int v);  // MODIFIES: this
                    // EFFECTS: this = this + {v}
    void remove(int v); // MODIFIES: this
                    // EFFECTS: this = this - {v}
    bool query(int v);   // EFFECTS: returns true if v is in this
    int size();          // EFFECTS: returns |this|
}
```

- 这个类不完整是因为我们还没有为这个集选择一种表示法
- 选择表示法涉及到：
  - 确定什么样的具体数据元素将被用来表示集中的值
  - 为每个方法提供一个实现
- 即便如此，这个不完整的定义也已经为IntSet的用户提供了所需了解的全部内容：
  - 这个抽象数据类型的概况
  - 以及每个方法的规格说明

- 首先，从set自身的表示法开始
- 使用数组：
  - 将尺寸为N的集表示成为一个无序的整数数组
  - 由于没有重复元素，所以存储在这个数组的前N个槽位(slot)中
- int numElts: 表示数组中当前的元素个数
- 红色的两句话被称为表示不变式( representation invariants)

## IntSet示例

- 表示不变式:
  - 在任何方法执行前和执行后都必须遵守的规则
- 由于是数组，并且数组具有最大尺寸，因此:
  - 我们需要选择最大尺寸，并修改类的概述
  - // OVERVIEW: a mutable set of integers, |set| <= 100
  - 我们还需要修改insert函数的effect注释
  - // EFFECTS: this = this + {v} if room, throws int 100 otherwise

## IntSet示例

```cpp
const int MAXELTS = 100;
class IntSet { // a mutable set of integers, |set| <= MAXELTS
int elts[MAXELTS];
    int numElts;
  public:
    void insert(int v); // MODIFIES: this
                      // EFFECTS: this = this + {v} if room,
                      //throws int MAXELTS otherwise
    void remove(int v); // MODIFIES: this
                       // EFFECTS: this = this - {v} if v is in this
                       // throws int v otherwise.
    bool query(int v); // EFFECTS: returns true if v is in this, false otherwise
    int size();        //EFFECTS: returns |this|
};
```

- 在这样的表示法和不变式下，可以很容易地写出各个方法
- 从最容易的size()开始：
- 由于不变式要求numElts 始终表示集的尺寸，因此可以立即返回它：

```
int IntSet::size()
{
    return numElts;
}
```

## IntSet示例

- 接下来考虑其他三个函数
  - query: 在数组中查找某个指定的数字
  - remove: 在数组中查找某个数字，如果该数字存在，则移除它
  - insert: 在数组中查找某个数字，如果该数字不存在，则插入它
- 所有这些函数的共同点就是都有“查找”部分
- 大家可能会想到使用 query 来编写 insert 和 remove
  - 但是这对 remove 行不通
  - query 只能告诉我们元素是否存在，但是不能告诉我们其位置
- 因此，我们还需要一个方法
  - indexOf(int v): 如果 v 在集中，则返回 v 在集合中的位置

```
const int MAXELTS = 100;
class IntSet { // OVERVIEW: a mutable set of integers, |set| <= MAXELTS
    int elts[MAXELTS];
    int numElts;
    int indexOf(int v); // EFFECTS: returns the index of v if it exists in the array
                        // MAXELTS otherwise

    void insert(int v); // MODIFIES: this
                        // EFFECTS: this = this + {v}, throws int MAXELTS otherwise
    void remove(int v); // MODIFIES: this
                        // EFFECTS: this = this - {v} if v is in this; throws int v otherwise
    bool query(int v); // EFFECTS: returns true if v is in this, false otherwise
    int size();        // EFFECTS: returns |this|
}
```

## IntSet示例

- indexOf(int v)必须是private的
- 这是因为它暴露了具体表示的细节
- 这些细节向这个类的客户暴露是不恰当的

```
int IntSet::indexOf(int v)
{
    for (int i = 0; i < numElts; i++) {
        if (elts[i] == v) {
            return i;
        }
    }
    return MAXELTS;
}
```

- 有了 indexOf， query 就容易编写了：
```
bool IntSet::query(int v)
{
  return (indexOf(v) != MAXELTS);
}
```
- insert 也不会困难多少：
  - 首先查找待插入元素的索引
  - 如果不存在，则需要插入该元素
  - 插入的方式是在数组末尾添加

## IntSet示例

- 由于**numElts**存储了数组中元素的个数
  - 当前的末尾就是
- 将待插入元素插入到这个槽位，然后更新numElts
- 唯一的例外就是当 numElts 等于MAXELTS时，插入失败

```
void IntSet::insert(int v){
    if (indexOf(v) == MAXELTS) {
    if (numElts == MAXELTS) throw MAXELTS;
    elts[numElts++] = v;
    }
}
```

- **remove 工作方式类似**
  - 如果元素在集中，则移除
- 移除后在数组中留下了一个“洞”
- 消除“洞”的方式之一：
  - 将空洞之后的所有元素都向左移动 1 个槽位
- 我们选择更好的方式：
  - 将当前最后一个元素移动到这个洞中
- 这个操作同样会违反有关numElts的不变式，因此需要订正

## IntSet示例

```
void IntSet::remove(int v){
    int victim = indexOf(v);
    if (victim != MAXELTS) {
        elts[victim] = elts[numElts-1];
        numElts--;
    } else {
        throw v;
    }
}
```

- 这就是完整的IntSet版本了吗？

