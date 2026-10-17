# # Push 和 Pop 可以穿插交替进行；

按照操作系列
(1)Push(S,A), Push(S,B),Push((S,C),Pop(S),Pop(S),Pop(S)
堆栈输出是？
CBA
(2) 而Push(S,A), Pop(S),Push(S,B),Push((S,C),Pop(S),Pop(S)
堆栈输出是？
ACB

[例] 如果三个字符按ABC顺序压入堆栈
• ABC的所有排列都可能是出栈的序列吗？
• 可以产生CAB这样的序列吗？