# ## 3)整数 Bresenham算法

//Bresenham's integer line rasterization algorithm
for the first octal.
//The line end points are (xs,ys) and (xe,ye) assumed
not equal. All variables are assumed integer.
//initialize variables
x=xs
y=ys
Δx = xe -xs
Δy = ye -ys
//initialize e to compensate for a nonzero intercept
NError =2*Δ y-Δx

> ( Error =Δ y/Δx-0.5 )