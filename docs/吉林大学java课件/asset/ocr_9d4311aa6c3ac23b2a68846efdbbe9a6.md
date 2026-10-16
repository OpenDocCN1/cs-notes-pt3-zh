# Collection接口的方法定义

| No. | 方法 | 类型 | 描述 |
|---|---|---|---|
| 1 | public boolean add(E o) | 普通 | 向集合中插入对象 |
| 2 | public boolean addAll(Collection<? extends E> c) | 普通 | 将一个集合的内容插入进来 |
| 3 | public void clear() | 普通 | 清除此集合中的所有元素 |
| 4 | public boolean contains(Object o) | 普通 | 判断某一对象是否在集合中存在 |
| 5 | public boolean containsAll(Collection<?> c) | 普通 | 判断一组对象是否在集合中存在 |
| 6 | public boolean equals(Object o) | 普通 | 对象比较 |
| 7 | public int hashCode() | 普通 | 哈希码 |
| 8 | public boolean isEmpty() | 普通 | 集合是否为空 |
| 9 | public Iterator<E> iterator() | 普通 | 为Iterator接口实例化 |
| 10 | public boolean remove(Object o) | 普通 | 删除指定对象 |
| 11 | public boolean removeAll(Collection<?> c) | 普通 | 删除一组对象 |
| 12 | public boolean retainAll(Collection<?> c) | 普通 | 保存指定内容 |
| 13 | public int size() | 普通 | 求出集合的大小 |
| 14 | public Object[] toArray() | 普通 | 将一个集合变为对象数组 |
| 15 | public <T> T[] toArray(T[] a) | 普通 | 指定好返回的对象数组类型 |