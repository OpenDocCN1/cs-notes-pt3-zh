# 2.1 Java的基本语法单位

# ■1 空白、注释及语句

空白：在Java程序中，换行符及回车都可以表示一行的结束，它们可以被看作是空白，另外，空格键、水平定位键(tab)亦是空白。为了增加程序可读性，Java程序元素之间可以插入任意数量空白，编译器忽略多余的空白。

(2)提倡的程序风格

# 口两种程序风格比较：

(1)不提倡的程序风格

```
/*
package example.Charpter_2;

/**
 * @author Fanchao Meng
 *
 */
public class Point {
int x,y;Point(int x1,int y1){x=x1;y=y1;} Point(){this(0,0);}
void moveto(int x1,int y1){x=x1;y=y1;}
```

```
/*
package example.Charpter_2;

/**
 * @author Fanchao Meng
 *
 */
public class Point {
    int x,y;            //点的x轴,y轴坐标
    Point(int x1,int y1){  //带参数的构造方法
        x=x1;
        y=y1;
    }
    Point(){            //不带参数的构造方法
        this(0,0);
    }
    void moveto(int x1,int y1){ //点移动到(x1,y1)
        x=x1;
        y=y1;
    }
}
```