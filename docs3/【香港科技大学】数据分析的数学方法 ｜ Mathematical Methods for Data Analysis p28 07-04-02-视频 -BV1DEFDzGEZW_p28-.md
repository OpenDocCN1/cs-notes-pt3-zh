# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p28 07-04-02-视频 -BV1DEFDzGEZW_p28-

I would like to give you two applications of convergence and limit in normal vector spaces。

You supervise thener。We are going to find some functions in the hypothesis space。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_1.png)

This hypothesis space has to be complete。Otherwise， we will be in trouble。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_3.png)

To see this， let's consider a very simple setting where we are given a training data set， X， I，Y I。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_5.png)

I from one to M。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_7.png)

Here I just assume our X is a number in between A and B。And Y I is a real number for simplicity。

Now we would like to find a function F。I will assume the hypothesis space for this F is the CAB。

That is， I find a continuous function such that F X I is about Yi。Now。

 in order to solve this problem， assume that we have an algorithm。We have an iterative algorithm。

Which generates。A sequence of of functions， F of K。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_9.png)

For k equals to1，2 and。It3 to algorithm just means we start from X F 0， we generate F1， F 2。

 F3 and so on。 We expect this FK when K grows， it becomes more and more closer to our expected solution。

Of course， our FK is in CAAB。Because we want to find a function in C AB。

Then we needed to study the convergence of this FK。

Now we can have many choices of the norms on the CAB。If we choose the two norm。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_11.png)

Now， if I assume this FK is good enough， in a sense， it's a co sequence。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_13.png)

Then this FK should be convergent。 Asum we have that this FK。mininus F。Limit K approaches infinity。

 This equals to 0 for some。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_15.png)

F。From our previous example， we know that CA A B with P norm P largergen than1 is incomplete。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_17.png)

This just implies that it might happen that。This F is not in CA AB。

Just means that F is not a continuous function。Then we didn't find unexpected expected solution。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_19.png)

Because we。We set the Ca， A B， as the。Hypotheesis space。 we want to find a continuous function。

 though we can make sure that each iteration is just continuous， but their limit is not continuous。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_21.png)

So， of course， this， we don't like it。Then to make sure we get an limit that is continuous。

We have to make sure CA A B under that norm is complete。

We know that CAB under the Infin norm is complete。Then we just use the infinity norm。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_23.png)

Again， we assume。FK is。Is cost sequence。And the limit of FK minus F， the infinity norm。

Its0 for some F。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_25.png)

Then， because we know that this is C A B。Under the finishing norm。Is company。Then。

A limit of the cautious sequence in the complete's normal vector space must be in that space as well。

So we know that this F must be in CAAB。Then we find a good solution because our limit F is continuous。

Its in our hypothesis space。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_27.png)

So this example tells us that we have to choose a proper。Norm， Wn Wei。Study convergence。 Otherwise。

 we may get an unexpected solution。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_29.png)

The second example。Again， un iterative algorithms。We have seen that many algorithms in machine learning are just iterative algorithms。

 like in the K means， we generate a sequence of vectors。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_31.png)

Any iterative algorithm just generate a sequence of。Vectctorors。Xk。

Then we want to check whether or not that the sequencing is convergent。

But now here we have only the XK， we don't have the is limit。Then how could we check the convergence？



![](img/1ba8cdcddb47c1450663e10bb2f7da59_33.png)

We just used that， remember。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_35.png)

When we study the convergence， you study the completeness， we defined the co sequence。

In the definition of the Ca sequence， we use the sequence itself。

 Only we didn't use its supposed limit。

![](img/1ba8cdcddb47c1450663e10bb2f7da59_37.png)

Then here we can use a similar idea。 We just use the Cast sequence。Use。Concious sequence。

To check the convergence。Which means that we are given。A precision Yipson， right。

 This Yon is just a precision we want to achieve like an Ypson equals to 10 to the negative 3。

Then in order to check whether or not this sequence， X K is a co sequence， we just need to check X。

 K。Minus Xl is sufficiently small， is smaller than our prede precision。Of course， here。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_39.png)

This K and L has to be very large。For all large cave and。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_41.png)

We needed to check this。If this is satisfied， then this sequence is a cautious sequence。

 so it is convergent。But this again， this is impractical because we need to check all K and L。

 large K and L。Then， practically。We have to。Reduce the。Competitional complexity in this check。

 This is too complicated because we need to， we need to try all K and L。Practically。

 to reduce the computation。We don't check。Oh，可安。Instead， we check only one。Pair of K and L。

 we just check K and K minus1 or K and K plus one。XK minus X K minus-1。Smallller than all ys or not。

This is very easy to do， right， because we just need to check the current iteration。

 the distance between the current iteration and the previous iteration。

Whether or not their distance is smaller than our prescribed precision。

If it is smaller than the Epsson， then the sequence is convergent。 We just stop the algorithm。

 If this is not satisfied， then the sequence is still not be convergent。

Then we just continue our iteration until this is satisfied。



![](img/1ba8cdcddb47c1450663e10bb2f7da59_43.png)