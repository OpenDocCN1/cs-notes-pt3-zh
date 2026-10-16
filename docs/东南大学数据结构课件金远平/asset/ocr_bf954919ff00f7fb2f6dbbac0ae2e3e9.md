# 7.5.2 Iterative Merge Sort

# Basic idea:

At the beginning, interpret the input as n sorted sublists, each of size 1. These lists are merged by pairs to obtain n/2 lists, each of length 2 ( if n is odd, then one list is of length 1). These n/2 lists are then merged by pairs, and so on until only one list is get.

As shown in the following: