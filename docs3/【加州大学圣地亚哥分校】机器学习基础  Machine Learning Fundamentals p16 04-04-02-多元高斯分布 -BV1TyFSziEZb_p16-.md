# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p16 04-04-02-多元高斯分布 -BV1TyFSziEZb_p16-

![](img/6cd4b7f8fff42af97d482d7a0c844444_0.png)

Now that we have linear algebra somewhat under control。

 we can take a look at the Gaussian distribution in arbitrary dimension。

So what we're going to do today is to start by looking at the density of the high dimensional Gaussian and getting some intuition for this。

 and then move on to some widely used special cases。



![](img/6cd4b7f8fff42af97d482d7a0c844444_2.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_3.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_4.png)

So let's do a little bit of a rewind if you recall when we were looking at the wine dataset set。

 we pulled out two features， alcohol level and flavoronoids。

 and we fit a twodimenional Gaussian to the data from one of the wineries and we got something like this Okay so this is a 2D Gaussian。

 so it's a distribution over the entire plane over every possible pair x1x2。

So that's the density shown here， so the density here is shown by the height above the surface。

I personally find pictures like this a little hard to understand。



![](img/6cd4b7f8fff42af97d482d7a0c844444_6.png)

So this is another depiction， which just shows the contour lines drawn on the plane。

so the red dots here are the actual data points。And the way we fit a Gaussian to them was to simply compute the mean of each of the features。

 So there's feature number one。Alcohol level。Feature number two， flavoravoids。

 we computed the mean along each feature and the variance of each feature。

 and then the covariance between the two features。And this gave us a2 Gauss。

So the Gaussian parameters were。The mean， which is a two dimensional vector represented by the Greek letter mu。

Which consists of the mean of x1。And the mean of eggs， too。

The other parameter of the Gaussian is a two by two covariance matrix。

 which we denote by the Greek letter sigma， capital sigma。

 and it has only three distinct numbers in it。 It has。The variance of x1。Up here。

 it has the variance of x2 down here。And then it has the covariance between the two features。

Which are the off diagonal numbers。Okay。So this is the mean mu is the center point over here。

And it's the point of highest density。The ellipses show the contour lines of the density。

 and the reason they' tilted upwards is because there is a positive correlation between the two features。

So the two dimensional Gaussian is quite simple， and it turns out that this generalizes in a straightforward way to D dimensions。



![](img/6cd4b7f8fff42af97d482d7a0c844444_8.png)

So let's move to the higher dimensional case， so now we're in D dimensions。

 so we want a distribution over RD。And now instead of two features， we have d features， x1， x2。

 all the way to x D。So in this case， the mean of the distribution mu。Will be a D dimensional vector。

 Okay， it contains the mean along the first feature。

 the mean along the second feature all the way to the mean along the D feature。

The covariance matrix this time is now a D by D matrix。



![](img/6cd4b7f8fff42af97d482d7a0c844444_10.png)

What does it consist of？So it's a D by D matrix。

![](img/6cd4b7f8fff42af97d482d7a0c844444_12.png)

And along the diagonal， it has the variances of each of the individual features。

 So these are D numbers along the diagonal。

![](img/6cd4b7f8fff42af97d482d7a0c844444_14.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_15.png)

The numbers of the diagonals are covariances between all possible pairs of features。

 So in the first row， for example， we start with the variance of x1。

 and then we have the covariance between x1 and x2， followed by the covariance between x1 and x3。



![](img/6cd4b7f8fff42af97d482d7a0c844444_17.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_18.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_19.png)

And so on。

![](img/6cd4b7f8fff42af97d482d7a0c844444_21.png)

In general， the IJ entry of this matrix is the covariance between Xi and Xj。

Okay so these are the parameters of the Gaussian。😊，And in terms of the density。

It's highest at the meanme as always， and as you move away from the mean。

 the density folds off in these ellipsoidal contours。

The shape of the ellipsoids is given entirely by the covariance matrix sigma。



![](img/6cd4b7f8fff42af97d482d7a0c844444_23.png)

つ。And here is the exact equation for the density。Well， let's take a brief look at this。So， in the。

So the first part of the density is just a normalization term that's only there to make sure that the density integrates the one and there's nothing unusual in there perhaps you remember what this is。

 that is the determinant of the matrix sigma so that's just the normalization term it's a constant in front。

The most important part of the density is the paththetics inside the exponent。

Because that's the only part that depends on X。So what does this thing mean。

 what kind of function is this x minus mu transpose sigma inverse x minus mu？Well。

 to simplify it a little bit， let's just imagine that mu equals 0。 Okay。

 so we have a Gaussian that is centered at the origin instead of being centered at some arbitrary point。

 mu。 Okay， so mu is 0。 Let's see what we get。

![](img/6cd4b7f8fff42af97d482d7a0c844444_25.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_26.png)

So the first term over there。

![](img/6cd4b7f8fff42af97d482d7a0c844444_28.png)

X minus mu just becomes x。The second term also becomes x。



![](img/6cd4b7f8fff42af97d482d7a0c844444_30.png)

And what is sigma inverse。 Well， Sigma is some D by D matrix。

 So its inverse is some other D by D matrix。 Let's just call it M。



![](img/6cd4b7f8fff42af97d482d7a0c844444_32.png)

So we get x transpose Mx。And that's something that looks familiar。 That's a quadratic function。



![](img/6cd4b7f8fff42af97d482d7a0c844444_34.png)

Okay， so the density depends only on a quadratic function of x。And indeed。

 an ellipoid is a kind of quadratic。嗯。

![](img/6cd4b7f8fff42af97d482d7a0c844444_36.png)

So now let's go and look at a special case that's of particular interest。

So suppose these different features are independent。What does the Gaussian look like then， Okay。

 so we have D features they' are independent of each other。

 and let's say that the variance of the I feature X is sigma sub I squared。😊。

Let's figure out what the covariance matrix would be in this case。



![](img/6cd4b7f8fff42af97d482d7a0c844444_38.png)

Okay， so we have a covariance matrix， which is always a D by D matrix。

And we know that its diagonal entries are just the variances of the individual features。



![](img/6cd4b7f8fff42af97d482d7a0c844444_40.png)

And the off diagonal entries are covariances between features。 Okay。

 so let's see what is the covariance between X and Xj？😊，Well， in this case， the court。

 the features are all independent of each other， so they are uncorrelated。

 which means that their covariance is 0。So the off diagonal elements are all zero。

 the covariance matrix is a diagonal matrix。Okay， and we can fill in the variances。

 the variance of x1 is sigma 1 squared， then we have sigma 2 squared， all the way to sigma d squared。



![](img/6cd4b7f8fff42af97d482d7a0c844444_42.png)

A nice short form for this kind of matrix is just to say at the diagonal matrix whose entries are sigma 1 squared all the way to sigma D squared。



![](img/6cd4b7f8fff42af97d482d7a0c844444_44.png)

Now in order to compute the density， we also need the inverse of this matrix。

 what is that well it's easy to invert a diagonal matrix。

 you just invert each element along the diagonal， so the inverse is1 over sigma 1 squared。

 all the weight is 1 over sigma d squared。

![](img/6cd4b7f8fff42af97d482d7a0c844444_46.png)

Okay。And that's it。

![](img/6cd4b7f8fff42af97d482d7a0c844444_48.png)

So because this covariance matrix is diagonal， we sometimes call this the diagonal Gaussian。



![](img/6cd4b7f8fff42af97d482d7a0c844444_50.png)

Okay。And the covariance matrix being simple makes it rather easy to simplify the density。

We end up with something like this。It turns out that each feature， if you look at it just by itself。

 is a Gaussian。 It the I feature， x sub I taken just by itself is a Gaussian with mean musab I and variance sigma I squared。

😊，Okay，So this is what x subi by itself looks like a one dimensional Gaussian。

And the density at a D dimensional point x。Is just the one dimensional density at x1 times the one dimensional density at x2 all the way to the one dimensional density at Xd。

The D features are all independent。Now， as always， the density is highest at the mean and folds off in these ellipsoidal contours。

What do the ellipsoids look like in this case。Well， there are no correlations。

 The covariance matrix is a diagonal matrix。 so because there is no correlation。Positive or negative。

 the ellipsoids are not tilted up or down。So the ellipsoids are axis aligned。

 that is to say they are parallel to the coordinate directions， they look something like this。Now。

 they are potentially stretched out differently along different directions。

 The stretch along the x1 direction is just the standard deviation of x1， which is sigma 1。

 so that's the stretch in this direction。The stretch in the x2 direction is the standard deviation of x2。

 which is sigma 2。And so on。So it's a fairly simple distribution。

One of the very nice things about it is that it can be specified using very few parameters okay。

 so how many parameters do you need for a diagonal Gaussian？😊，Well， the mean is d numbers， okay。

 because it's a D dimensional vector。

![](img/6cd4b7f8fff42af97d482d7a0c844444_52.png)

What about the covariance matrix， well， it's a diagonal matrix so you only need D numbers。

 so the total number of parameters is 2D。

![](img/6cd4b7f8fff42af97d482d7a0c844444_54.png)

This is a huge savings over the general Gaussian， which has a full covariance matrix and therefore needs something on the order of d squared parameters。



![](img/6cd4b7f8fff42af97d482d7a0c844444_56.png)

![](img/6cd4b7f8fff42af97d482d7a0c844444_57.png)

This can be a big convenience。 and as a result， the diagonal Gaussian is often used even when the features are not independent of each other。



![](img/6cd4b7f8fff42af97d482d7a0c844444_59.png)

嗯。

![](img/6cd4b7f8fff42af97d482d7a0c844444_61.png)

Now， let's look at an even more special case that's also very popular。

This is when the features are independent as before， but in addition they all have the same variance。

So now the covariance matrix is a diagonal matrix， and in addition。

 the numbers along the diagonal are all exactly the same， in other words。

 the covariance is a multiple of the identity matrix。😊，So the covariance matrix looks like this。

 a multiple of the identity matrix。In this case， the density can be simplified even further。

This is the density function。M as you can see， the density at a point x depends only on the distance from x to mu。

 It depends only on the distance to the center of the Gaussian。So the points of equal density。

Are points that lie on its sphere， centred at mue。So as always。

 the density is highest at mu and as you move away from mu。

The shells of equal density are these concentric spheres。嗯。So another popular Gaussian。



![](img/6cd4b7f8fff42af97d482d7a0c844444_63.png)

Okay， so we have a little bit of insight now into multivariate Gaussians。

 let's turn to a somewhat more concrete and practical question。

 which is how do you fit a Gaussian into data Okay。

 so we have a bunch of data points in D dimensionsal space， let's call them X1 through XM。

How would you go about fitting a galaxysian into them？Well it's quite simple。

 just compute the mean and covariance of these points。And those are the parameters。

 mu and sigma of the Gaussian。 Okay， so the mean of a bunch of data points is often called the empirical mean。

So you take the points， these M data points， and you just add them up。And you divide by M。

 And this is some D dimensional vector。 That's the mean mu。

The covariance matrix finding the empirical version of this is also very simple。

 you just apply the formula for covariance to the dataset set。Okay。

 so so how exactly does that work out？ Well， we now have this D by D matrix。

 What is the IJ entry of the matrix is the covariance between X I and Xj。

And what was the formula for covariance again， Well。

 the covariance between Xi and Xj is the expected value of Xi times Xj。

Minus the expected value of x y。Times the expected value of xj。What is the expected value of Xi。

 Well， we've already computed that。 that's muabbi。

![](img/6cd4b7f8fff42af97d482d7a0c844444_65.png)

What is the expected value of xj that's mu sub J。 So all we need to do is to compute the average value of Xi times Xj in the data set。

 and that's exactly what this term is over here。

![](img/6cd4b7f8fff42af97d482d7a0c844444_67.png)

Okay。

![](img/6cd4b7f8fff42af97d482d7a0c844444_69.png)

So that's it for the multivariate Gaussian。 This is one of the absolutely most popular distributions for modeling high dimensional data。

 and it is now part of your repertoire。