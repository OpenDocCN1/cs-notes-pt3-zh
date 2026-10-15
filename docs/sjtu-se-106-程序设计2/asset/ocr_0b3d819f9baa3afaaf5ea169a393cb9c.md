# Introductions

In programming, the use of pointers are the main source of errors (or bugs) when developing code.

The main problem found are the occurrences of memory leaks, this is due to the way pointers interact with memory, such as allocation and deallocation, which when performed inefficiently can cause the pointer to hang (or dangle, meaning that the pointer points to a previous removed object).

The solution to this dilemma is the use of Smart Pointers.