# instanceof操作符

```
```java
public class 人
{
	public 衣食住行 ()
	{
	}
}

public class 男人 extends 人
{
	public 吸烟 ()
	{}
}

public class 女人 extends 人
{
	public 美容 ()
	{}
}

public class Test
{
	public call (人 p)
	{
		if(p instanceof 男人)
		{
			男人 m=(男人) p;
			m.吸烟();
		}
	else if(p instanceof 女人)
	{
		女人 f=(女人)p;
		f.美容();
	}
	}
	public static void main(String args[])
	{
		男人 m=new 男人();
		call(m);
	}
}
```
```