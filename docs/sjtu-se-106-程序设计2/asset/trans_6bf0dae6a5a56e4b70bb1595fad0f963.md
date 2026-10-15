

## The hashmapimpl1.cpp Implementation

```
/* Constant definitions */
const int INITIAL_BUCKET_COUNT = 101;

/*
* Implementation notes: constructor and destructor
* --------------------------------------------------
* The constructor allocates the array of buckets and initializes
* each bucket to the empty list.  The destructor must free the memory,
* but the clear function already takes care of that.
*/

template <typename KeyType,typename ValueType>
HashMap<KeyType,ValueType>::HashMap() {
    nBuckets = INITIAL_BUCKET_COUNT;
    buckets = new Cell*[nBuckets];
    for (int i = 0; i < nBuckets; i++) {
        buckets[i] = NULL;
    }
    count = 0;
}

template <typename KeyType,typename ValueType>
HashMap<KeyType,ValueType>::~HashMap() {
    clear();
}

template <typename KeyType,typename ValueType>
int HashMap<KeyType,ValueType>::size() {
    return count;
}

template <typename KeyType,typename ValueType>
bool HashMap<KeyType,ValueType>::isEmpty() {
    return count == 0;
}

template <typename KeyType,typename ValueType>
void HashMap<KeyType,ValueType>::clear() {
    for (int i = 0; i < nBuckets; i++) {
        Cell *cp = buckets[i];
        while (cp != NULL) {
            Cell *oldCell = cp;
            cp = cp->link;
            delete oldCell;
        }
    }
    count = 0;
}

template <typename KeyType,typename ValueType>
void HashMap<KeyType,ValueType>::put(KeyType key, ValueType value) {
    int bucket = hashCode(key) % nBuckets;
    Cell *cp = findCell(bucket, key);
    if (cp == NULL) {
        cp = new Cell;
        cp->key = key;
        cp->link = buckets[bucket];
        buckets[bucket] = cp;
    }
    cp->value = value;
}

template <typename KeyType,typename ValueType>
ValueType HashMap<KeyType,ValueType>::get(KeyType key) {
    int bucket = hashCode(key) % nBuckets;
    Cell *cp = findCell(bucket, key);
    if (cp == NULL) error("get: No value for key");
    return cp->value;
}

template <typename KeyType,typename ValueType>
bool HashMap<KeyType,ValueType>::containsKey(KeyType key) {
    int bucket = hashCode(key) % nBuckets;
    return findCell(bucket, key) != NULL;
}

#endif
```

## Part II: Advanced Concepts

Jingyu Zhou

## Map

- 一个非常有用的抽象
  - 任何类型的字典、查找表、索引、数据库等。
- 存储键值对
  - 通过键快速访问
  - 需要优化的操作：put, get

## Basic Idea

- 使用 *hash function* 将键映射到 *hash table* 中的位置
- 如果元素 *e* 的键为 *k* 且 *h* 为哈希函数，则 *e* 存储在表的位置 *h(k)*
- 要搜索 *e*，计算 *h(k)* 以定位位置。如果没有元素，则字典不包含 *e*。

理想情况下

## Example

- 字典 学生记录
  - 键为学号（951000 - 952000），不超过 100 名学生
  - 哈希函数：h(k) = k-951000 将 ID 映射到不同的表位置 0-1000
  - `array table[1001]`

![](img/af430dff16b82a0fe61ce7dee05dcf9c_390_0.png)

## Analysis (Ideal Case)

- 初始化哈希表需要 O(b) 时间（b 为哈希表中位置或桶的数量）
- 执行 *insert*、*remove*、*search* 需要 O(1) 时间

## Ideal Case is Unrealistic

- 可用于实现字典，但许多应用的键范围太大，无法在桶和键之间建立 1-1 映射！

示例：

- 假设键的取值范围为 0 .. 65,535（2 字节无符号整数）
- 预计任何时候约有 1,000 条记录
- 使用 65,536 个槽的哈希表不切实际！

## Hash Functions

- 如果键范围太大，使用更少的桶的哈希表，并使用哈希函数将多个键映射到同一桶：
  h(k₁) = β = h(k₂)：k₁ 和 k₂ 在槽 β 处发生 **collision**
- 流行的哈希函数：除法哈希
  h(k) = k%D，其中 D 为哈希表中的桶数
- 示例：哈希表有 11 个桶
  h(k) = k%11
  80 → 3（80%11 = 3），40 → 7，65 → 10
  58 → 3 发生冲突！

