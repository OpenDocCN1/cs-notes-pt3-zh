# 静态数据成员

□ 必须在类外定义，定义时可以进行初始化

数据类型 类名::静态数据成员名 = 值;

```
class A
{
	static int shared;
	int x,y;
public:
	A(){x=y=0;}
	void increase_all()
	{...}
};
```

int A::shared=0;
A a1,a2;

+   shared: 0
+   a1.x: 0
+   a1.y: 0
+   a2.x: 0
+   a2.y: 0