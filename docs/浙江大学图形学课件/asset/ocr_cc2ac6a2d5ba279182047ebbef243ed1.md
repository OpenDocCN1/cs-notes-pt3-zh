# # Digital Differential Analyzer (DDA)

+   - We consider the line in the first octant. Other cases can be easily derived.
+   - Uses differential equation of the line
+   
+   \( y_i=m \cdot x_i+c \)
+   
+   where, \( m=\frac{y2-y1}{x2-x1} \)

+   - Incrementing X-coordinate by 1
+   
+   \( x_i=x_{i\_prev}+1 \)
+   
+   \( y_i=y_{i\_prev}+m \)

+   - Illuminate the pixel \( [x_i,round(y_i)] \)

![](bbox=[0.63, 0.412, 0.986, 0.743])

Discussion1: What technique makes it faster?
Discussion2: Is there any problem in the algorithm?
How to avoid it?