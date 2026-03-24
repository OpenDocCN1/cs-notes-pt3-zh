# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p40 09-03-02-视频 -BV1DEFDzGEZW_p40-

There is still one issue unsolvebed in the kernel K means algorithm that is how to choose the kernel function K。



![](img/325499099f6f50ea1e2273b9bbe70f41_1.png)

![](img/325499099f6f50ea1e2273b9bbe70f41_2.png)

Actually， the kernel function is not arbitrary because from our construction of this kernel function。

 this kernel function must be in the form of the inner product of phi x and p y for some phi and for some inner product space。



![](img/325499099f6f50ea1e2273b9bbe70f41_4.png)

![](img/325499099f6f50ea1e2273b9bbe70f41_5.png)

So let's first find out necessary conditions that a kernel function should satisfy。



![](img/325499099f6f50ea1e2273b9bbe70f41_7.png)

First of all， this K X Y。It is supposed to be phi x and Phi Y in the product for some。5。

Then we know that the inner product is symmetric， so it is just a fire Y， phi x。

Then by our definition， this is just the K Y x。So a first necessary condition for the kernel is thats。

K， X， Y has to be K， Y， X for any X and Y。This is called the symmetry of this kernel。



![](img/325499099f6f50ea1e2273b9bbe70f41_9.png)

We say K is symmetric if this is satisfied。

![](img/325499099f6f50ea1e2273b9bbe70f41_11.png)

Therefore， the first necessary condition for K in a good kernel is that K must be symmetric。Secondly。

The Indian product is linear with respect to its inputs。And also。

 this inner product should satisfy the inner product of the same vector should be non negative。

Let's see。What these conditions imply to the kernel function？Let y 1。To YM。Be in RN。

We just consider M vectors in R， then。For any。We consider a vector C。That is C12 CM。Of M numbers。

We consider the linear combination of this5Yi。Waied by C I。 So it's the sigma of I from1 to M C I。

5 Y， I。This is a vector in the H space， and we consider the inner product of this with itself。This。

 by the definition of the inner product， this has to be non negative。Also。

 because the inner product is linear with respect to both this and this。

 then we expand this inner product to obtain。C， I C J。

And then according to the definition of this kernel function。



![](img/325499099f6f50ea1e2273b9bbe70f41_13.png)

This is just the K， Y， I， Y J。

![](img/325499099f6f50ea1e2273b9bbe70f41_15.png)

![](img/325499099f6f50ea1e2273b9bbe70f41_16.png)

If we define a matrix now。Still denoted by K。For this matrix， it's I J element。



![](img/325499099f6f50ea1e2273b9bbe70f41_18.png)

It is just the K， Y， I，Y J。

![](img/325499099f6f50ea1e2273b9bbe70f41_20.png)

Then you see that this is exactly a quadratic form。Just this a sea transportpose Ca。



![](img/325499099f6f50ea1e2273b9bbe70f41_22.png)

So then you can see here a necessary condition for this K matrix is that this C transpose Kc should be larger than all equals to0 for any C for any C this holdss2。



![](img/325499099f6f50ea1e2273b9bbe70f41_24.png)

![](img/325499099f6f50ea1e2273b9bbe70f41_25.png)

And also， from one。

![](img/325499099f6f50ea1e2273b9bbe70f41_27.png)

This kernel has to be symmetric here。 We know that this KY IY J is K Y J Y I。

 which means that the IJ element of this matrix K is the JI element of this matrix K。



![](img/325499099f6f50ea1e2273b9bbe70f41_29.png)

Then， K transpose equals。Okay。Altogether， these two together。

It's just to say that this K is a symmetric。Positive。This one is not symmetric positive。

 definitely because it might happen we have a non0 C such that C transportse KC equals0。

This is just called the positive semi defite。Or SPSD for short。



![](img/325499099f6f50ea1e2273b9bbe70f41_31.png)

In other words， two necessary conditions for the kernel is that this K is。



![](img/325499099f6f50ea1e2273b9bbe70f41_33.png)

The matrix K is symmetric， positive semideinite。

![](img/325499099f6f50ea1e2273b9bbe70f41_35.png)

We call kernels satisfy this condition a symmetric， positive semidefinite kernel。



![](img/325499099f6f50ea1e2273b9bbe70f41_37.png)

If a kernel satises that the matrix is defining in this way is SPSD。

 then we just call this kernel is SPSD。

![](img/325499099f6f50ea1e2273b9bbe70f41_39.png)

So then from the devation in this one and2， we see that a necessary condition for k function to be a kernel is that this cave must be SPPSD。



![](img/325499099f6f50ea1e2273b9bbe70f41_41.png)

Actually， this SPSD condition is also sufficient。

![](img/325499099f6f50ea1e2273b9bbe70f41_43.png)

This is stated by the well known Mercers I。It just says that if a kernel function is SPPSD。



![](img/325499099f6f50ea1e2273b9bbe70f41_45.png)

Then there exists a Heable space H and a mapping file。



![](img/325499099f6f50ea1e2273b9bbe70f41_47.png)

![](img/325499099f6f50ea1e2273b9bbe70f41_48.png)

![](img/325499099f6f50ea1e2273b9bbe70f41_49.png)

Such of that。K X， Y is exactly。

![](img/325499099f6f50ea1e2273b9bbe70f41_51.png)

5hi x。F away。The inner product。So， from this。We can see that in order to have a good kernel。

 our K has to be SPSD。And SPSD is also sufficient for K being a good kernel。



![](img/325499099f6f50ea1e2273b9bbe70f41_53.png)

Now， let's see which kernel functions are used in practice， some popular kernels。

We can define a kernel to be。This x transpose y。In this case。The corresponding5hi x is just x。

So there is no transform or the identity transform is used。So then the ks。

 the kernel ks is the same as the standard ks。If we use this。X transpose y plus1 to the alpha。



![](img/325499099f6f50ea1e2273b9bbe70f41_55.png)

Where A find is just some integer。This kernel function is called the polynomial kernel。

Because if the polynomial kernel is used the corresponding H。

 the corresponding hereable space is just the space of polynomials on x。

The last one and might be the most popular kernel used is the Gaussian kernel。 K， X。

 Y equals to the exponential of minus x minus Y， the two norm squared define。

Divided by sigma squared。So here sigma is a parameter。This is the standard Gausing kernel。

It is used very frequently in practice。So those are popular kernels。



![](img/325499099f6f50ea1e2273b9bbe70f41_57.png)