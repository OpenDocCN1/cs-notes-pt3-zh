# Map接口中的方法

| No. | 方法或类 | 类型 | 描述 |
|---|---|---|---|
| 1 | public void clear() | 普通 | 清空Map集合 |
| 2 | public boolean containsKey(Object key) | 普通 | 判断指定的key是否存在 |
| 3 | public boolean containsValue(Object value) | 普通 | 判断指定的value是否存在 |
| 4 | public Set<Map.Entry<K,V>> entrySet() | 普通 | 将Map对象变为Set集合 |
| 5 | public boolean equals(Object o) | 普通 | 对象比较 |
| 6 | public V get(Object key) | 普通 | 根据key取得value |
| 7 | public int hashCode() | 普通 | 返回哈希码 |
| 8 | public boolean isEmpty() | 普通 | 判断集合是否为空 |
| 9 | public Set<K> keySet() | 普通 | 取得所有的key |
| 10 | public V put(K key, V value) | 普通 | 向集合中加入元素 |
| 11 | public void putAll(Map<? extends K,? extends V> t) | 普通 | 将一个Map集合中的内容加入到另一个Map |
| 12 | public V remove(Object key) | 普通 | 根据key删除value |
| 13 | public int size() | 普通 | 取出集合的长度 |
| 14 | public Collection<V> values() | 普通 | 取出全部的value |