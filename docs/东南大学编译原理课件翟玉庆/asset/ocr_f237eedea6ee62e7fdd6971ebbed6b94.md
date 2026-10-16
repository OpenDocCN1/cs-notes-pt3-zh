# Chapter 9 Code optimization

# Section 2 Optimization of basic blocks

# 3.Generating code from dags

+   - Rearranging the order(Heuristic Order)

![](bbox=[0.06, 0.32, 0.78, 0.92])

T1=a+b
T2=c+d
T3=e-t2
T4=t1-t3

T2=c+d
T3=e-t2
T1=a+b
T4=t1-t3