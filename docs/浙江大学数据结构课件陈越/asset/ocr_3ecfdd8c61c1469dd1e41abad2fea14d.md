# # 关键路径问题

由绝对不允许延误的活动组成的路径

![](bbox=[0.117, 0.192, 0.883, 0.562])

问题1：整个工期有多长？ Earliest[8] = 18 Earliest[0] = 0; Earliest[j] = max <i,j>∈E { Earliest[i]+C<i,j> };

问题2：哪几个组有机动时间？ D<i,j> = Latest[j]−Earliest[i]−C<i,j> Latest[8] = 18; Latest[i] = min <i,j>∈E { Latest[j]−C<i,j> };

Copyright @ 2014, 浙江大学计算机科学与技术学院 All Rights Reserved