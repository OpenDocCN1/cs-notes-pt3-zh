# Advice on Signed vs. Unsigned

```
1 /*
2 * Illustration of code vulnerability similar to that found in
3 * FreeBSD’s implementation of getpeername()
4 */
5
6 /* Declaration of library function memcpy */
7 void *memcpy(void *dest, void *src, size_t n);
8
```