# serialVersionUID

序列化时为了保持版本的兼容性，即在版本升级时反序列化仍保持对象的唯一性。有两种生成方式：

+   一个是默认的1L，比如： private static final long serialVersionUID = 1L;

+   一个是根据类名、接口名、成员方法及属性等来生成一个64位的哈希字段，比如： private static final long serialVersionUID = xxxxL;