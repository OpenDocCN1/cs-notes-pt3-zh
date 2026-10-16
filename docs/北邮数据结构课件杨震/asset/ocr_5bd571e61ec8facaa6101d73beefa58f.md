# [串的基本操作]

(1)用串常量赋值    StrAssign(&T,chars)
    用串变量赋值    StrCopy(&T,S)

(2)判等函数    StrCompare(S,T)（词典次序,>=<=0）

(3)求长函数    StrLength(S)

(4)连接函数    Concat(&T,S1,S2)

(5)求子串函数    SubString(&Sub,S, pos,len)

(6)定位函数    Index(S,T, pos)

(7)置换函数    Replace(S,T,V)

(8)插入操作    StrInsert(S,pos,t)

(9)删除操作    StrDelete(S,pos,len)

**线性表的操作通常以“数据元素”为操作对象；串的操作主要以“串的整体”为操作对象。