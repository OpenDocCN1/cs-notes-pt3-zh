# # example4

R=(A, B, C, D, E), F={A →B, BC →D, D →A}

+   1) Find all candidate keys.

+   2)Whether R is in BCNF or 3NF or neither?

+   3) If it is not in BCNF, decompose R into a set of BCNF relations. Explain that your decomposition is lossless-join.

+   4) Whether the decomposition of 3) is dependency preserving or not? Why?

![](bbox=[0.047, 0.523, 0.289, 0.672])

+   1) Candidate keys: ACE, BCE, CDE

+   2) ‘:’every right attribute in F is in key

+   is 3NF

+   4) BC →D is not preserved

+   3’) R1=(AB), R2=(ACDE),

+   R21=(ACD), R22=(ACE),

+   R211=(AD), R212=(CD)

3) R1=(AB), R2=(ACDE), R21=(AD), R22=(CDE)

方法3 ... 方法7

![](bbox=[0.008, 0.836, 0.078, 0.969])

![](bbox=[0.836, 0.766, 0.992, 0.984])