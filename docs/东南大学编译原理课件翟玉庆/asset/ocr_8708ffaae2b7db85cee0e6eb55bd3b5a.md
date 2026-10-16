# Chapter 8 Intermediate code generation
Section 2 Backpatching

# 1. Why and what is backpatching?

+   - When generating code for boolean expressions and flow-of-control statements, we may **not know the labels that control must go to**.

+   - We can get around this problem by generating a series of branching statement with the targets of the jumps temporarily left unspecified.

+   - Each such statement will be put on a list of goto statements whose labels will be **filled in when the proper label can be determined**.

+   - This subsequent filling in of labels is called backpatching.