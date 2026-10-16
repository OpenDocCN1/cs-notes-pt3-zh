# Case study 1. Legacy File Update

# Design issue 1: How to make the 4 filter objects work simultaneously?

# Solution:

All the 4 filters should have multi-thread properties. So, let Filter class implements interface Runnable.