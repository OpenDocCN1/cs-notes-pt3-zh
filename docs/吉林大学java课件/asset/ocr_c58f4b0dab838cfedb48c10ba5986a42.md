# String类中的常用方法（1）

| No. | 方法定义 | 类型 | 描述 |
|---|---|---|---|
| 1 | public String(char[] value) | 构造 | 直接将一个字符数组变为一个字符串 |
| 2 | public String(char[] value,int offset,int count) | 构造 | 将一个指定范围的字符数组变为字符串 |
| 3 | public String(byte[] bytes) | 构造 | 将一个byte数组全部变为字符串 |
| 4 | public String(byte[] bytes,int offset,int length) | 构造 | 将指定范围的byte数组变为字符串 |
| 5 | public char[] toCharArray() | 普通 | 将一个字符串变为字符数组 |
| 6 | public char charAt(int index) | 普通 | 从一个字符串中取出指定位置的字符 |
| 7 | public byte[] getBytes() | 普通 | 将一个字符串变为byte数组 |
| 8 | public int length() | 普通 | 取得字符串长度 |
| 9 | public int indexOf(String str) | 普通 | 从头开始查找指定的字符串位置 |
| 10 | public int indexOf(String str,int fromIndex) | 普通 | 从指定位置开始查找指定的字符串位置 |
| 11 | public String trim() | 普通 | 清除左右两端的空格 |