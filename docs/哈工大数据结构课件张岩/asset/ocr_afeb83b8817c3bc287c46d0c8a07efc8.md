# 5.3 折半查找（Cont.）

折半查找的示例：

k = 21
1 2 3 4 5 6 7 8 9 10 11
05 13 19 21 37 56 64 75 80 88 92 F
low=1
low=1
mid=3
low=mid=4 up=5
up=5
mid=6
up=11

k = 85
1 2 3 4 5 6 7 8 9 10 11
05 13 19 21 37 56 64 75 80 88 92 F
low=1
mid=6
low=7
mid=9
up=11
up=11
low=mid=10 up=11
low=10 up=9