# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p53 11-03-02-视频 -BV1DEFDzGEZW_p53-

Of course， we can choose other set as。

![](img/7b5a7a183b1a655984f5ad562617678d_1.png)

For example， in the Lasso regression。

![](img/7b5a7a183b1a655984f5ad562617678d_3.png)

It there are so rigorous we just to choose。Our S equals again， it is on beta。In R， N plus 1。

But now we restricted the one norm of the a vector smaller than or equals to a number C。For some。



![](img/7b5a7a183b1a655984f5ad562617678d_5.png)

是i。So then。We just saw。Minimization of this beta in S。X beta minus y the2 norm squared。Again。

 we have this constrained optimization。The constraint is that beta in S or the one norm of this A vector is smaller than C。

So that by this way， we find our function on the subset of the a function。



![](img/7b5a7a183b1a655984f5ad562617678d_7.png)

For this constrain optimization， again， by some optimization theory。

We just have that this one is equivalent to an on spin optimization。



![](img/7b5a7a183b1a655984f5ad562617678d_9.png)

X beta minus y the two norms for the plus lambda a1 norm。This is just the Laso model。Laau recation。

Again， here， this no is a constant。Depending on this C。

 depending on the optimal value of this minimization problem and others。



![](img/7b5a7a183b1a655984f5ad562617678d_11.png)

It is an unconstrained optimization。And in this unconstraint optimization， we have two terms。

 the first term x beta minus y the two norm squared， it is the data fittinging term。

It is used to make this F X I is about YI。It makes this fitting error small。



![](img/7b5a7a183b1a655984f5ad562617678d_13.png)

It just makes sure that this F applies to X I is about Yi。So it's the datafi term。And对。

This second term， the one norm of a， is the regularization term。

It is used to make the function F regular。Or equivalently。

 it is used to make the coefficient A in the definition of the function F has a small one norm。



![](img/7b5a7a183b1a655984f5ad562617678d_15.png)

Because in the na model， we find a fine function F。こs。Coefficient a has a small one norm。



![](img/7b5a7a183b1a655984f5ad562617678d_17.png)

Then this term is exactly to make sure that this A has a small one norm。

So that it is called the regularization， it applies to only the function。

It is independent of the data。 The training data X and beta is not involved in this term。



![](img/7b5a7a183b1a655984f5ad562617678d_19.png)

And this lambda is the regularization parameter。Again， here。

 larger lambda means smaller one norm of a means more regular。And loser fitting。

If we choose a small lambda， just means we have less regularity， but we have better fitting。



![](img/7b5a7a183b1a655984f5ad562617678d_21.png)

To the training data。

![](img/7b5a7a183b1a655984f5ad562617678d_23.png)

So these are two different models， the rigid regression and the LaO regression。

 both of them are quite popular in practice。

![](img/7b5a7a183b1a655984f5ad562617678d_25.png)

![](img/7b5a7a183b1a655984f5ad562617678d_26.png)

Then what's the difference between the reach and natural regression？



![](img/7b5a7a183b1a655984f5ad562617678d_28.png)

You can see that the only difference between the rigid regression and the soil regression is that we used different norms here。



![](img/7b5a7a183b1a655984f5ad562617678d_30.png)

![](img/7b5a7a183b1a655984f5ad562617678d_31.png)

In reach regression， we use the two norm squared。 in our soil regression， we just use the one norm。

Just similar to the K means and K media in K means， we used the two norm。In key media。

 we used the one。Here in aO we use the one norm in rigid regression， we use the two norm squared。



![](img/7b5a7a183b1a655984f5ad562617678d_33.png)

This subtle difference just make the solution quite a difference in general。



![](img/7b5a7a183b1a655984f5ad562617678d_35.png)

Mas will give you a spars solution。Now so gives a sparse vector a。

Because of the one normal regularization。And the region regressioning gives。T a。

Spare A means that more zeros。In this a。This a contains little n entries。 As we have said。

 we when this little a is much larger than this capital N we need to use regularization。

 So this little a is just very， very large。

![](img/7b5a7a183b1a655984f5ad562617678d_37.png)

And in this very big vector， there are many entries are 0 in the results produced by Ma Su。

What is the advantage， Actually， Sprs a。Sponsor A just means that F X equals A X plus B。

Equals sigma of I from one to N， AI X， I plus B。Here。

 this X I should not be confused with the X I vector。 It's only the I component of this X。



![](img/7b5a7a183b1a655984f5ad562617678d_39.png)

So then since this A is sparse。So which means that in this sum， many AIs are just0。

 So then it is just a sigma of I in this。Support。Offer this A。AI， X， I， plus B。

Only those non zero AIs will contribute to this sum。

So the support of aim means that the position of non zero entries of a。Right。

 so I just count those nonze terms in this summ。 So I get this one。 So then from here。

 you can see only those X I， I is on the support of a will be involved in this F of X。

 So from here we see that only X I， I on the support of。诶。Contribute。To the。Prediction。Now。

 this is support of a remember because a is sparse。



![](img/7b5a7a183b1a655984f5ad562617678d_41.png)

Just means that this is support of a。It is much， much smaller than I。

The number of non zero entries is just smaller than and much， much smaller than。

This absolute value means the cardinity of this is the code of a just means the number of non zeros in this a。

 So this is only。A few。Entraest。Of this X。So wish is that。

Only very few entries of X contributes to the prediction。



![](img/7b5a7a183b1a655984f5ad562617678d_43.png)

People likes this because fewer variables participate in the prediction。

 we will have a more interpretable prediction。Since there are only very few entries involved in this prediction so that it is more interpretable。

 This linear model is more interpretable。 We just need to look at those entries in the prediction。

And it is possible to find out the mechanism behind this linear prediction。



![](img/7b5a7a183b1a655984f5ad562617678d_45.png)