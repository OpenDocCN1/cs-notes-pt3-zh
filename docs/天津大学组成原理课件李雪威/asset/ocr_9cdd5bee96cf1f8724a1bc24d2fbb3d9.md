# # Nested Array Row Access Code

![](bbox=[0.047, 0.161, 0.721, 0.292])

![](bbox=[0.522, 0.302, 0.974, 0.459])

![](bbox=[0.054, 0.469, 0.793, 0.603])

# ## Row Vector

+   - `pgh[index]` is array of 5 int’s
+   - Starting address `pgh+20*index`

# ## Machine Code

+   - Computes and returns address
+   - Compute as `pgh + 4*(index+4*index)`

Bryant and O’Hallaron, Computer Systems: A Programmer’s Perspective, Third Edition