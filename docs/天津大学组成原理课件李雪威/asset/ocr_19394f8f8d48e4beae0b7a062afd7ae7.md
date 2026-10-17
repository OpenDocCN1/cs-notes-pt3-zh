# 3. Stack Canaries can help

+   - **Idea**
+     - Place special value (“canary”) on stack just beyond buffer
+     - Check for corruption before exiting function

+   - **GCC Implementation**
+     - `-fstack-protector`
+     - Now the default (disabled earlier)

```
unix> ./bufdemo-sp
Type a string:0123456
0123456
```

```
unix> ./bufdemo-sp
Type a string:01234567
*** stack smashing detected ***
```