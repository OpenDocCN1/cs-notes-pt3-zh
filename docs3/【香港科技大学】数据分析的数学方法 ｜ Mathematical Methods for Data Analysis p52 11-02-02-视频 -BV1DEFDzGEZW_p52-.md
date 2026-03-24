# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p52 11-02-02-视频 -BV1DEFDzGEZW_p52-

Let's check the probabilityability of this list squares problem involved in the linear regression。

We can see that。 there are。Capital N equations。And the we have。Little M plus one。Unknows。



![](img/8a593a5aff4dd3616477cc750c380158_1.png)

So in order this list squares problem to have a unique solution。

 we have to make sure that the number of equations is larger than or equals to the number of unknowns。

N larger than all equals n plus1。miss。Is necessary。For a unique solution。Of linear regression。

Now we should have the number of data should be larger than the number of dimension plus one。

This is one necessary condition。 However， this does not hold true always。



![](img/8a593a5aff4dd3616477cc750c380158_3.png)

In practice， we may have that this。The number of training data might be even smaller than the dimension of the data。

However。In practice。We may have。This N is just much， much less than。你传。

Let me just give you a simple example in。Image of recognition。In the image recognition task。

 this XI input will be the images。The Y I will be the being labels of the images。And for images。

 we know that we can have very high quality images， the number of pixels。Can be。Millions of pixels。

10 million pixels are quite common， nowadays for images。

Which means that the dimension of this X is little n。With in the order of 10 M。



![](img/8a593a5aff4dd3616477cc750c380158_5.png)

But however， capital n is the number of images in the data set。

I even for the most popular image data set， like the image net。

 the number of images is at most 1 million。So this。Capital N is only at。

The scale of order of 1 million。

![](img/8a593a5aff4dd3616477cc750c380158_7.png)

So that you can see in this case， N is just much， much smaller than little N。

Which means that the number of available training data set is much。

 much smaller than the dimension of the input so that this is not satisfied so that this list square in the linear regression will not have a unique solution。



![](img/8a593a5aff4dd3616477cc750c380158_9.png)

This is to say。That the set of all a fine functions in the linear regression is still too large。

That's set。Of fine functions。Is still too large。Then， we needed to。

Srink the size of this function set as。To this purpose， we do the same regularization。

Which means that we use a subset of a functions。So this is the set of all a functions。

Then we use a subset of these fine functions。To our regression task， we call it5 S。



![](img/8a593a5aff4dd3616477cc750c380158_11.png)

In particular， we define P S to be5 S to be this。F。Because F should be a fine。

 which means that the f of x equals a X。Plus， B。And对。Not all fine functions are allowed in this set。

 which means that not all A and B are allowed。 So then I just have some constraint on this， A and B。

We set this A and B in the subset of RN plus1 I call it S。

So that this subscript S here means that the A and B in the subset of RM plus1 S。

Then let's see what we will obtain if we choose a function from a subset of these functions defined in this way。

You knowRe regulation。We choose this as。就B。北塔。With this。

A2 norms smaller than or equals to a constant C。

![](img/8a593a5aff4dd3616477cc750c380158_13.png)

For some。See， larger than 0。

![](img/8a593a5aff4dd3616477cc750c380158_15.png)

So。We needed to solve this minimization。Minimize。你是贝塔。X beta minus y2 norm squared。

 If I don't have any constraint， this beta is in R M plus1。 This is the standard least square。

This is just the standard linear regression。And now， because we have a constraint on this beta。

 we need the coefficient of this A， the A2 norm to be smaller than C。

Then we cannot choose our beta in the whole space R N plus1。 But instead。

 we just choose this beta in this set S。Then by this way， our F will be AX plus B。

 but A and B in this set。

![](img/8a593a5aff4dd3616477cc750c380158_17.png)

So then we choose the a subset of fine functions for the linear regression。For this optimization。

 it is equivalent to。Just by using some optimizationization theory。Just use the na theory。

Because this is a constrained optimization。Actually， this will be equivalent to the minimization。

Of this beta equals A B in R M plus 1。X beta minus y。

 the two norm squared plus lambda times this a2 norm squared。



![](img/8a593a5aff4dd3616477cc750c380158_19.png)

These two will be equivalent just by some optimization theory。Here is Lambda。Is a constant。

This constant depends on。Depends on C， because。In the definition of this， as we have this C。

 this numberda depends on C。And 돼。The optimal solution of this minimization。And some other。Constance。

Then this one is called the Rige regression。

![](img/8a593a5aff4dd3616477cc750c380158_21.png)

So in rigid regression， instead of find a function from the all a functions。

 we find a function from a subset of a fine functions。

 that is we want the two norm of the a vector smaller than all equals to c。

 then we get this constrained least squares probe。

![](img/8a593a5aff4dd3616477cc750c380158_23.png)

![](img/8a593a5aff4dd3616477cc750c380158_24.png)

![](img/8a593a5aff4dd3616477cc750c380158_25.png)

By some optimization theory， this constrained optimization is equivalent to this unconstrained one。

In this unconstrained optimization， we have a parameter lambda。 This lambda is a constant。

 It depends on the set S that is。 it depends on this C。It also depends on some other factors。

Then in Ri regression， we just solve this unconstrained optimization to get the beta。

 and then a inner product with x plus B will be the function in the rid regression。

Let's focus on the optimization in the regression。You can see that here。This extra beha。

Minineus y2 norm squared。This term。We will call it a data fitting term。

Because this is the same as the one in the standard linear regression。

 it is just to make our FXI is about Yi。So it is used to fit the given data X Y。

So that we call it a data fitting term。For this term。This a norm squared the term。

We call it a regularization term。For this regularization term， it applies only to this beta。

It applies to only this， A and B。Or it applies only to the function F。

It does not involve the training data。This term is to make our A and B regular。

 It is used to force our A and B all the beta in this essence。



![](img/8a593a5aff4dd3616477cc750c380158_27.png)

Or equivalently， it is used to force this A X plus B or function in this5 S class instead of the who assign function space。



![](img/8a593a5aff4dd3616477cc750c380158_29.png)

So the role of this term is to make the function in the regression to be regular。



![](img/8a593a5aff4dd3616477cc750c380158_31.png)

In this set， we say a function is regular just means that our function is in the desired subset。

Because we think that the functions in this set is good， is regular for the regression task。



![](img/8a593a5aff4dd3616477cc750c380158_33.png)

So then this term is to make the function， make the F regular。

So that's we call this one a regularization term。

![](img/8a593a5aff4dd3616477cc750c380158_35.png)

Under this lambda。It is now a constant。It serves the same row as this C here。

 It is used to define how large this。

![](img/8a593a5aff4dd3616477cc750c380158_37.png)

Set P essays。This one is called the regularization parameter。

It is used to define how regular this function F is。You can see larger lambda。



![](img/8a593a5aff4dd3616477cc750c380158_39.png)

What do we have？If we have a large lambda， then this term will dominate these two terms。

So that at the minimizer， this a2 norm squared will be relatively smaller。



![](img/8a593a5aff4dd3616477cc750c380158_41.png)

Which means that this C will be smaller。So that this5 S will be smaller。



![](img/8a593a5aff4dd3616477cc750c380158_43.png)

So we will have a smaller F S。And we have a looser fitting。To data。

Because this term will be relatively larger。 Thearrow will be relatively larger。

 so the data fitting is not too restrict。On the contrary， if which was a smaller。Lada。

 then of course， we will have a larger。Phi S because in this case。

 this term will dominant so that we may have a larger two norm squared。

 so then this is C larger so that this set will be larger。



![](img/8a593a5aff4dd3616477cc750c380158_45.png)

And that this will be smaller so that we have a。Better fit to the data。So in rigid regression。

 we just choose our S to be the one。With a small two norm of the a vector。



![](img/8a593a5aff4dd3616477cc750c380158_47.png)