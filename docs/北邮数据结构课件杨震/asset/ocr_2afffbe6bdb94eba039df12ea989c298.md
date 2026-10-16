# KMP算法时间复杂度分析

通常，模式串长度m<<主串长度n

求next(nextval)数组： O(m)

主串与模式串匹配： O(n)

整个匹配算法O(m+n)