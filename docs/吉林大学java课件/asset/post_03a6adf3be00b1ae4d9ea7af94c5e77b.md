
# 修改Person类并实现Externalizable接口

```
public class Person implements Externalizable {    // 此类的对象可以被序列化
    private String name;                         // 声明name属性
    private int age;                             // 声明age属性
    public Person(){}                            // 必须定义无参构造
    public Person(String name, int age) {        // 通过构造方法设置属性内容
        this.name = name;
        this.age = age;
    }
    public String toString() {                   // 覆盖toString()方法
        return "姓名:" + this.name + "; 年龄:" + this.age;
    }
    // 覆盖此方法,根据需要,读取内容,反序列化时使用
    public void readExternal(ObjectInput in) throws IOException,
        ClassNotFoundException {
        this.name = (String)in.readObject();     // 读取姓名属性
        this.age = in.readInt();                 // 读取年龄
    }
    // 覆盖此方法,根据需要,可以保存属性或具体内容,序列化时使用
    public void writeExternal(ObjectOutput out) throws IOException {
        out.writeObject(this.name);              // 保存姓名属性
        out.writeInt(this.age);                  // 保存年龄属性
    }
}
```

# 序列化和反序列化Person对象

```
public class SerDemo03 {
    public static void main(String[] args) throws Exception {
        ser();                          // 序列化
        dser();                         // 反序列化
    }
    public static void ser() throws Exception {          // 序列化操作
        File f = new File("D:" + File.separator + "test.txt");
        ObjectOutputStream oos = null;
        OutputStream out = new FileOutputStream(f);       // 文件输出流
        oos = new ObjectOutputStream(out);                // 为对象输出流实例化
        oos.writeObject(new Person("张三", 30));         // 保存对象到文件
        oos.close();                                      // 关闭输出
    }
    public static void dser() throws Exception {          // 反序列化操作
        File f = new File("D:" + File.separator + "test.txt");
        ObjectInputStream ois = null;
        InputStream input = new FileInputStream(f);       // 文件输入流
        ois = new ObjectInputStream(input);               // 为对象输入流实例化
        Object obj = ois.readObject();                    // 读取对象
        ois.close();                                      // 关闭输入
        System.out.println(obj);
    }
}
```

# Externalizable接口与Serializable接口实现序列化的区别

| No. | 区别 | Serializable | Externalizable |
| --- | --- | --- | --- |
| 1 | 实现复杂度 | 实现简单, Java对其有内建支持 | 实现复杂, 由开发人员自己完成 |
| 2 | 执行效率 | 所有对象由JAVA统一保存, 性能较低 | 开发人员决定那个对象保存, 可能的速度提升 |
| 3 | 保存信息 | 保存时占用空间大 | 部分存储, 可能的空间减少 |

# transient关键字

- 当使用Serializable接口实现序列化操作时，如果一个对象中的某个属性不希望被序列化的话，则可以使用transient关键字进行声明

# Person中的name属性不希望被序列化

```
package org.lxh.demo12.serdemo;
import java.io.Serializable;
public class Person implements Serializable {    // 此类的对象可以被序列化
    private transient String name;    // 此属性将不被序列化
    private int age;    // 此属性将被序列化
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    public String toString() {    // 覆盖toString()，输出信息
        return "姓名: " + this.name + "; 年龄: " + this.age;
    }
}
```

# Java类集

## —— 认识类集、Collection接口

# 数组的优缺点

- ◆ 数组可以快速地随机访问数组中的元素。数组可以保存基本类型和对象。
- ◆ 数组的容量固定。当数组空间不足的时候需要做数据迁移，效率很低。
- ◆ 经常不知正在编写的程序需要使用多少个对象。

# 容器

# 集合

- 动态的容量
- Collection（类集）：一组单独元素集合
- List：保存的对象有顺序，按照元素的索引位置检索对象。允许重复元素。
- Set：不允许保存重复的元素。元素之间没有顺序。靠元素值检索对象。
- Map（映射）：一组键值对
- 元素包括“键”对象和“值”对象。键必须是唯一的，值可以重复。

# 容器完整关系图

![](img/b706331eacf49a62651c2c9b2de81ca5_659_0.png)

# Collection接口的定义

- Collection是保存单值集合的最大父接口。
- Collection接口定义：
- public interface Collection<E> extends Iterable<E>
- JDK 1.5之后为Collection接口增加了泛型声明

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
