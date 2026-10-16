# System类

System类是一些与系统相关的属性和方法的集合，而且在System类中所有的属性都是静态的，要想引用这些属性和方法，直接使用System类调用即可。

| No. | 方法定义 | 类型 | 描述 |
|---|---|---|---|
| 1 | public static void exit(int status) | 普通 | 系统退出 |
| 2 | public static void gc() | 普通 | 运行垃圾收集机制，调用的是Runtime类中的gc方法 |
| 3 | public static long currentTimeMillis() | 普通 | 返回以毫秒为单位的当前时间 |
| 4 | public static void arraycopy(Object src,int srcPos,Object dest,int destPos,int length) | 普通 | 数组拷贝操作 |
| 5 | public static Properties getProperties() | 普通 | 取得当前的系统全部属性 |
| 6 | public static String getProperty(String key) | 普通 | 根据键值取得属性的具体内容 |