

## ADT 5.3

```
template <class K, class E>
class Dictionary {
public:
    virtual bool IsEmpty () const = 0;
        // return true iff the dictionary is empty
    virtual pair<K,E>* Get(const K&) const = 0;
        // return pointer to the pair with specified key;
        // return 0 if no such pair
    virtual void Insert(const pair<K,E>&) = 0;
        // insert the given pair; if key is a duplicate
        // update associated element
    virtual void Delete(const K&) = 0;
        // delete pair with specified key
};
```

## The pair can be defined as:

```
template <class K, class E>
struct pair
{
    K first;
    E second;
};
```

二叉搜索树在需要执行搜索、插入和删除操作时具有更好的性能。

**定义：** 二叉搜索树，若非空，则满足以下性质：

- 1. 根节点有一个键。
- 2. 左子树中的键（如果有）小于根节点中的键。
- 3. 右子树中的键（如果有）大于根节点中的键。
- 4. 左子树和右子树也是二叉搜索树。

注意这些性质意味着键必须是不同的。

## 二叉搜索树

![](img/15e8d7d94d8ddf02cb6839870195a31e_368_0.png)

## 5.7.2 在二叉搜索树中搜索

根据其性质，很容易搜索二叉搜索树。假设搜索键为 k 的元素：

- 如果 k==根节点中的键，则成功；
- 如果 x<根节点中的键，则搜索左子树；
- 如果 x>根节点中的键，则搜索右子树。

假设类 BST 派生自类 Tree<pair<K,E>>。

```
template <class K, class E> // Driver
pair<K,E>* BST<K,E>::Get(const K& k)
{ // Search *this for a pair with key k.
    return Get(root, k);
}

template <class K, class E> // Workhorse
pair<K,E>* BST<K,E>::Get(treeNode<pair<K,E>>* p, const K& k)
{
    if (!p) return 0;
    if (k < p->data.first) return Get(p->leftChild, k);
    if (k > p->data.first) return Get(p->rightChild, k);
    return &p->data;
}
```

## 递归版本可以很容易地改写成
如下的迭代版本：

```
template <class K, class E> // Iterative version
pair<K,E>* BST<K,E>::Get(const K& k)
{
    TreeNode<pair<K,E>>* currentNode = root;
    while (currentNode)
        if (k < currentNode->data.first)
            currentNode = currentNode->leftChild;
        else if (k > currentNode->data.first)
            currentNode = currentNode->rightChild;
        else return &currentNode->data;

    // no matching pairs
    return 0;
}
```

可以看出，高度为 h 的二叉搜索树可以通过键在 O(h) 时间内搜索。

## 5.7.3 向二叉搜索树中插入

要插入一个新元素，先进行搜索，如果不成功，则在搜索终止的位置插入该元素。

![](img/15e8d7d94d8ddf02cb6839870195a31e_373_0.png)

插入 35

![](img/15e8d7d94d8ddf02cb6839870195a31e_373_1.png)

当字典已包含键为 k 的配对时，我们只需将与该键关联的元素更新为 e。

```
template <class K, class E>
void BST<K,E>::Insert(const pair<K,E>& thePair)
{ // Insert thePair into the binary search tree
    // search for thePair.first, pp is parent of p
    TreeNode<pair<K,E>> *p=root, *pp=0;
    while (p) {
        pp=p;
        if (thePair.first < p->data.first) p=p->leftChild;
        else if (thePair.first > p->data.first) p=p->rightChild;
        else // duplicate, update associated element
            {p->data.second=thePair.second;return;}
    }
}
```

```
// perform insertion
p=new TreeNode<pair<K,E>>(thePair,0,0);
if (root) // tree not empty
    if (thePair.first < pp->data.first) pp->leftChild=p;
    else pp->rightChild=p;
else root=p;
}
```

时间是 O(h)。

## 5.7.4 从二叉搜索树中删除

3 种情况：
(1) 删除一个叶子节点：很容易，将其父节点的相应子字段设为 0 并释放该节点。

![](img/15e8d7d94d8ddf02cb6839870195a31e_376_0.png)

