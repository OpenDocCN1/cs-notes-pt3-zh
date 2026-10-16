# 5.3 Randomized algorithms

# 5.3.1 The hiring problem

For the hiring problem, the algorithm is deterministic.

+   For any given input, the number of times we hire a new office assistant will always be the same. (给定输入，则雇佣的人数确定)

+   The number of times we hire a new office assistant depends only on the input. (雇佣的人数〔资源消耗〕依赖于输入)

+   Some rank orderings will always produce a high hiring cost. Example: <1,2,3,4,5,6>, where each is hired.

+   Some will always produce a low hiring cost. Example: <6,*,*,*,*,*>, where only the first is hired.

+   Some may be in between.

![](bbox=[0.45, 0.08, 0.97, 0.55])