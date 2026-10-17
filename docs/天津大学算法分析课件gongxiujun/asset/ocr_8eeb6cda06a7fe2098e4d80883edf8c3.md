# # Step 4. Deriving the recursive equation

n=5, c=10

p= 6 3 5 4 6
w= 2 2 6 5 4
X= x1 x2 x3 x4 x5

To calculate _f(i,y)_ from _f(i+1,y)_, we only need know <u>if item _i_ could be included</u>

+   - If _w<sub>i</sub> > y_, item _i_ couldn’t be included, _f(i, y) = f(i+1, y)._