
# 宠物商店 —— PetShop.java（增加宠物）

```java
class PetShop {
    private Pet[] pets;                    // 保存多个宠物
    private int foot;                      // 数据的保存位置

    public PetShop(int len) {              // 构造方法，开辟宠物数组的大小
        if (len > 0) {                     // 判断长度是否大于 0
            this.pets = new Pet[len];      // 为对象数组开辟空间
        } else {
            this.pets = new Pet[1];        // 至少开辟一个空间
        }
    }

    public boolean add(Pet pet) {          // 增加宠物
        if (foot < this.pets.length) {     // 判断宠物商店里的宠物是否已经满了
            this.pets[foot] = pet;         // 增加宠物
            foot++;                        // 修改保存位置
            return true;                   // 增加成功
        } else {
            return false;                  // 增加失败
        }
    }

    ...
};
```

# 宠物商店 —— PetShop.java（查询）

```java
class PetShop {
    ...

    public Pet[] search(String keyWord) {       // 关键字查找
        Pet p[] = null;                         // 此为查询之后的结果，此处的大小不是固定的
        int count = 0;                          // 记录有多少个宠物符合查询结果

        // 确认开辟的空间大小，看有多少个宠物符合查询条件
        for (int i = 0; i < this.pets.length; i++) {
            if (this.pets[i] != null) {         // 判断对象数组中的内容是否为空
                if (this.pets[i].getName().indexOf(keyWord) != -1
                    || this.pets[i].getColor().indexOf(keyWord) != -1) {
                    count++;                    // 统计符合条件的宠物个数
                }
            }
        }

        p = new Pet[count];                     // 根据已经确定的记录数，开辟对象数组
        int f = 0;                              // 设置增加的位置标记

        for (int i = 0; i < this.pets.length; i++) {
            if (this.pets[i] != null) {
                if (this.pets[i].getName().indexOf(keyWord) != -1
                    || this.pets[i].getColor().indexOf(keyWord) != -1) {
                    p[f] = this.pets[i];        // 将符合查询条件的宠物信息保存
                    f++;
                }
            }
        }

        return p;
    };
}
```

# 测试宠物商店 —— PetShopDemo.java

```java
public class PetShopDemo {
    public static void main(String args[]) {
        PetShop ps = new PetShop(5);                // 五个宠物
        ps.add(new Cat("白猫", "白色的", 2));       // 增加宠物，成功
        ps.add(new Cat("黑猫", "黑色的", 3));       // 增加宠物，成功
        ps.add(new Cat("花猫", "花色的", 3));       // 增加宠物，成功
        ps.add(new Dog("拉布拉多", "黄色的", 3));   // 增加宠物，成功
        ps.add(new Dog("金毛", "金色的", 3));       // 增加宠物，成功
        ps.add(new Dog("黄狗", "黑色的", 3));       // 增加宠物，失败
        print(ps.search("黑猫"));
    }

    public static void print(Pet p[]) {             // 输出操作
        for (int i = 0; i < p.length; i++) {        // 循环输出
            if (p[i] != null) {
                System.out.println(p[i].getName()
                    + ", " + p[i].getColor() + ", "
                    + p[i].getAge());
            }
        }
    }
}
```

# 面向对象（高级）—— Object 类

# 本章目标

- 掌握 Object 类的作用
- 掌握 Object 类中 `toString()`、`equals()` 方法的作用
- 掌握 Object 接收引用数据类型的操作

# Object 类

在 Java 中所有的类都有一个公共的父类，就是 Object 类。一个类只要没有明显地继承一个类，则肯定是 Object 类的子类。Object 如下两种代码表示的含义都是一样的：

- `class Person extends Object {}`
- `class Person {}`

# Object 类中的主要方法

| No. | 方法名称 | 类型 | 描述 |
| --- | --- | --- | --- |
| 1 | `public Object()` | 构造 | 构造方法 |
| 2 | `public boolean equals(Object obj)` | 普通 | 对象比较 |
| 3 | `public String toString()` | 普通 | 对象打印时调用 |

# toString() 方法

- 在直接输出对象的时候会默认调用类中的 `toString()` 方法

# 应用 toString() 方法取得对象内容

```java
class Person {
    private String name;                 // 定义 Person 类
    private int age;                     // 定义 age 属性

    public Person(String name, int age) { // 定义构造方法
        this.name = name;                // 通过构造设置属性内容
        this.age = age;
    }

    public String toString() {            // 此处覆写 toString() 方法
        return "姓名: " + this.name + "; 年龄: " + this.age;
    }
}

public class ObjectDemo02 {
    public static void main(String args[]) {
        Person per = new Person("李兴华", 30);      // 实例化 Person 对象
        System.out.println("对象信息: " + per);     // 打印对象，调用 toString() 方法
    }
}
```
