# # 教程结构 精品课件

首页  例题

课件 > 第一讲 基本概念（1-1... > 1.3 应用实例：最大子...

1. int Max(int a, int b, int c )
2. {
3. /* 返回三个整数中的最大值 */
4. return A > B ? A > C ? A : C : B > C ? B : C;
5. }
6. }
7. int DivideAndConquer( int list[], int left, int right )
8. {
9. /* DivideAndConquer(list, left, right)返回list中左端为left、右端为right子段的最大和*/
10. int MaxLeftBorderSum, MaxRightBorderSum; /* 存放左右子段问题解 */
11. int MaxLeftBorderSum, MaxRightBorderSum; /* 存放跨分段分段的结果 */
12. }
13. int leftBorderSum, RightBorderSum;
14. int center = ( left + right ) / 2; /* 找到中分点 */
15. if( left == right ) /* 递归的终止条件，子序列只有一个数字 */
16. if( list[left] > 0 ) return list[left];
17. else return 0;
18. }
19. /* 下面是“分”的过程 */
20. center = ( left + right ) / 2; /* 找到中分点 */
21. MaxLeftSum = DivideAndConquer( list, left, center );
22. MaxRightSum = DivideAndConquer( list, left+1, right );
23. MaxLeftBorderSum = 0; leftBorderSum = 0;
24. for( i=center; i>=left; i-- ) /* 从中线向左扫描 */
25. {
26. leftBorderSum += list[i]; /* 求左部的和 */
27. if( leftBorderSum > MaxLeftBorderSum )
28. MaxLeftBorderSum = leftBorderSum; /* 左部边界和取最大值 */
29. }
30. MaxRightBorderSum = 0; rightBorderSum = 0;
31. for( i=center+1; i<=right; i++ ) /* 从中线向右扫描 */
32. {
33. rightBorderSum += list[i]; /* 求右部的和 */
34. if( rightBorderSum > MaxRightBorderSum )
35. MaxRightBorderSum = rightBorderSum; /* 右部边界和取最大值 */
36. }
37. /* 下面返回“治”的结果 */
38. return Max3( MaxLeftSum, MaxRightSum, MaxLeftBorderSum + MaxRightBorderSum );
39. }
40. int MaxSubseqSum( int list[], int n )
41. { /* 保持与旧算法相同的函数原形 */
42. return DivideAndConquer( list, 0, n-1 );
43. }

公告
评价分析
课件
编程作业
测验与作业
教材与参考资料
考试
讨论区
课程分享
微信群课程互助
扫码下载APP
帮助中心

评价课程