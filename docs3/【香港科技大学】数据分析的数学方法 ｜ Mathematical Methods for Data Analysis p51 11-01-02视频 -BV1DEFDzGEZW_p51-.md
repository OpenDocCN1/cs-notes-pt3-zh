# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p51 11-01-02视频 -BV1DEFDzGEZW_p51-

We go to applications of linear functions and user representations。In particular。

 we will study linear regression and linear classifier。In your。Make a recipe。And，对。Linyir。Classifier。

We will use linear function to do the regression and use linear functions to do the classification。

We started with linear regression。The task in Indian regression looks like this given。A set of data。

That are in pairs。In the form of x 1， Y，1，1 pair， x 2， Y 2， the second pair， and so on。

 assume that we have。Capital and pairs。Here。This X， I， they are without loss of generality。

 I assume they are in R N。It is the input vector。And why I。Again， for simplicity。

 I just assume why I is a real number is the corresponding output。

Or sometimes we call to the correspondial label。Of X I。Then we want to do the prediction。

Given a new X。We want to predict the corresponding output。In order to solve this problem。

 we need first to turn this into a mathematical。We know that in mathematic。

 we use functions to reflect the relation between input and output。So then。

In order to solve this projection problem， we just find a function。



![](img/7f4500ad58ebccb0146bc01950a4882e_1.png)

This function， of course， maps the input to the output that is from RN to R。I call this function， F。

Such that this function can reflect the relations between the input and output pairs in the training data set。

Which means that we want this F maps the input to the output。for all唉。

Because this function set up a relation between the input and output， then we just use。This F。

Applies to x as the prediction。

![](img/7f4500ad58ebccb0146bc01950a4882e_3.png)

But how， how to find such a function I。This description is a very vague description。

 It's not mathematically rigorous。We need to make this mathematically in rigorous。First of all。

The set of all functions is too large。From R N to R。Its too large。



![](img/7f4500ad58ebccb0146bc01950a4882e_5.png)

When it is too largeur。There are several consequences， first of all。

 because we are given only this finite many pairs of data。If we don't have too many data。

 then if the function is too arbitrary。Then we can not determine this F uniquely。



![](img/7f4500ad58ebccb0146bc01950a4882e_7.png)

We don't have enough data。To fit， to determine this F uniquely。

If the degree of freedom contained in this F function it is more than this capital N。



![](img/7f4500ad58ebccb0146bc01950a4882e_9.png)

But we have only capital and data。In this case， we can have many。

 many F satisfy F X I equals Yi exactly。So we have to restrict a function class such that the degree of freedom contained in that function class is smaller than。

This is the first one。

![](img/7f4500ad58ebccb0146bc01950a4882e_11.png)

A second consequence of this large set of functions is that there are too many strange functions。

That cannot serve for the prediction。That are not good。For prediction。



![](img/7f4500ad58ebccb0146bc01950a4882e_13.png)

Because our task is for prediction。In general， our X cannot be exactly this X I， I from one to n。

This X can only be in the neighborhood of X I。 X I is from one to n。

If this function F is too sensitive to the perturbation on X。Then though X might be very close to Xi。

 but this Fx is just very far away from。FXI， in that case。

 actually the prediction power of this F function is。Quite bad。

So we have to make sure that this function F does not change too much if this X I has only a small change。

This is related to the smoothness of this F。If we just see that we use the set of all functions。

Then this is set that contains too many very， very non smooth functions。So that they cannot。

Be used for the prediction purpose。

![](img/7f4500ad58ebccb0146bc01950a4882e_15.png)

So we find F in the subset of these all functions。I call this a subset of fight。Of course。

 the key question here is that wish find。Actually， the choice of P can be very tricky。

 It is just a fundamental in machine learning。How to choose 5。Is a fundamental problem。

I machine learning。If which is are too big phi， if this phi is too big。

 which means that we have too many functions。Then。You will see that we may not have enough data。

To fit this set。Just as what we have argued here。For example， if this。

Degree of freedom of functions in this by is more than。



![](img/7f4500ad58ebccb0146bc01950a4882e_17.png)

And the capital N here。Then。We don't have enough data to uniquely determine a function in this file。



![](img/7f4500ad58ebccb0146bc01950a4882e_19.png)

We may not have enough data to feed this society。Secondly， if this set file is too big。

 then it may contains too many strange functions。That are not good for the prediction。Therefore。

 we cannot choose a very big vi。On the other hand， we cannot choose a very small file。

If this satisfy is too small。

![](img/7f4500ad58ebccb0146bc01950a4882e_21.png)

Then we will also be in trouble。Because our article goal in this。



![](img/7f4500ad58ebccb0146bc01950a4882e_23.png)

A regression task is to do the prediction。So we want to find a function to approximate this relation between Xi and Yi。

Now， if this set file is too small， then this good approximation the functions that can approximate this underlying function very well may not be in this set。



![](img/7f4500ad58ebccb0146bc01950a4882e_25.png)

![](img/7f4500ad58ebccb0146bc01950a4882e_26.png)

In other words， the approximation power of functions in this file might be too weak。



![](img/7f4500ad58ebccb0146bc01950a4882e_28.png)

We get a weak approximation power。We cannot find a good function because this set is too small。

To approximate the underlying function。So we cannot choose a very big file。

 We cannot choose a very small file。 We have to choose a filehi with a suitable size。

We have to balance。How to choose5。 Actually， it is very difficult。

So I will not give a further discussion on the choice of five。But instead。

 we would like to check a special file。Maybe the symiesister I， there are fine functions。We choose。

Fhi to be the set of all a fine functions。From R N to R。As I have mentioned before， conventionally。

 we call a fine functions， linear functions。

![](img/7f4500ad58ebccb0146bc01950a4882e_30.png)

So then if we choose P to be the setup for all our fine functions。

 we get the so called linear models。And if we go back to the regression。



![](img/7f4500ad58ebccb0146bc01950a4882e_32.png)

We will get the linear regression if we choose F to be an a function。



![](img/7f4500ad58ebccb0146bc01950a4882e_34.png)

Let's see what is exactly a linear regression。So， we choose。And you fine。A fine functions。Now。

 since these Fs are fine。This F X has a representation from the R representation theorem。

A fine functions are linear functions， plus a constant。

And all linear functions can be written into the inproduct form。

So that any a fine function must be in this form with some。A and B。A in R， N and B in R。

So an a function is identified to a vector A and a number B。

RightSo then instead of find a function in this set file， we just need to find a vector A and a B。

 such that this is satisfied。

![](img/7f4500ad58ebccb0146bc01950a4882e_36.png)

![](img/7f4500ad58ebccb0146bc01950a4882e_37.png)

In particular。We just needed to。Find。诶。And the B。Essentially that's。Now， this F， X， I is about Y I。

 F is A X plus B in this form。 So we just want this。



![](img/7f4500ad58ebccb0146bc01950a4882e_39.png)

A X， I plus B is about Y I for all I。Now that。Regression。

 the linear regression is converted to this problem。

 find the A and B such that A Xi plus B is approximately Yi。Of course。

 we need to have a rigorous description on this。In what sense we think it is a good approximation。

There are many， many standards， there are many， many criterias。

So here I just want to use the simplest one， the least square。In each the squares。

 what we are going to do is that we use the sum of the squares。As the arrow。Of the system of。

Equations。In particular， this is the left hand side。 this is the right hand side。

 We make a difference of the left hand side and the right hand side。

This will be the error for this equation I。Of course， we want this error is as small as possible。

Then we just make a square of this one。This is the error of one single equation in this system of equations。

And then， we just。Sum up all the  errors from one to capital。

So this will be the total error of this system of equations here。Then we say a good approximation。

If this error is minimized。Then we just saw this problem。This is what we have。

Used in the list squares。So this is anistta squares。Then。

We get an optimization to solve this linear regression problem。

 we just find the A and B such that they are the solution to this minimization。Then， we write。

This list the square in a standard form。We just define x matrix to B。



![](img/7f4500ad58ebccb0146bc01950a4882e_41.png)

X1 transpose， X 2 transpose to this X， N transpose and 1，1。1。So you can see this is a matrix of size。

We have capital N rows。For the columns。This because this X， I， they are in R N。 R little N。

 This is of N columns。 and we have one extra column here。 So it's。N plus 1。This is the x。

 and also I write this beta。Victor to be this， A and B。A is the unknown vector here。

 and B is the unknown number here， so that this is just a vector in RM plus1。

I also denotes the y vector to be y1 to this y。Capital N。This is in our capital。Now。

 if I introduce these three notations。This x times beta， it will be。

This x1 transpose1 to this X N transpose one。Times beta is just A B。You see。

 this is just by using the product rule of matrices。Just x1 transfers a plus  one times B。

The first component is just the x1 transpose。A plus B， X 2 transpose A plus B。

Just x capitalta n transpose a plus B。This is quite obvious， so that this x beta。us1。 this one。

 It is just。X 1 transfers a plus。Minus y 1 x 2 transpose a plus B， minus y 2。

 and X N transpose a plus B minus Y N。Then if we go back to the optimization here。

 you can see this list square is exactly。The sum of the squares of the components here。You see。

 because this is just。X， I transpose a。I mean， this is in the product is just X I transpose a。

So that's this。Distta squared is exactly the two non squared of this vector。



![](img/7f4500ad58ebccb0146bc01950a4882e_43.png)

So。This is the square。The list square problem is equivalent to。The minimization of this beta in R。

M plus 1 is。X beta minus y the true norm squared。This is the standard form for our distance squares problem。



![](img/7f4500ad58ebccb0146bc01950a4882e_45.png)

In summary， for this India regression， we first solve this minimization。

This needs the square minimization to obtain beta。Because beta equals to A and B， then with A and B。

 we can have this function， A X plus B。Then given a new input X， we just use。

A X in the product plus B as the prediction of the output of X。



![](img/7f4500ad58ebccb0146bc01950a4882e_47.png)