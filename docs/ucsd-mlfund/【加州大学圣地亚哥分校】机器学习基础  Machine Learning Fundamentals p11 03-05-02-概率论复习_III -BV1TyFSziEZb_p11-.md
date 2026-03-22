# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p11 03-05-02-概率论复习_III -BV1TyFSziEZb_p11-

![](img/3d99d6b09ea9b0de84899b04aa352e3c_0.png)

When we are dealing with multiple random variables， for instance， a patient's heart rate。

 cholesterol level， blood pressure， whether they're ill and so on。

 the easiest situation is when all these random variables are independent of each other。

 when they don't influence each other。In those cases。

 we can just model each of them separately and not worry about interactions between them。

The more interesting situation by far， though， is when they are dependent。

And then we need ways of understanding and quantifying this dependence。

So today we'll begin by formally defining what it means for two variables to be independent。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_2.png)

And then we'll start looking at dependence more closely。Okay。

So this is the formal notion of independence。 We say two random variables。

 X and Y are independent if。The probability that x takes on some value， little x and simultaneously。

 Y takes on some value。 little Y is just the probability that x is little x and that y takes on the value little Y。

 In other words， X being equal to little X does not either make it more likely or less likely that y will be equal to little y。

They don't influence each other。Let's see an example of this Okay。

 so suppose you have a standard deck of 52 cards and you pick a card at random。

And you define two random variables based on this card。 X is the suit， clubs， spades。

 hearts and so on。 And y is the number on the card 6，7， a Jacque King。R X and Y independent。Yes。

 they are。 Okay， and let's see let's see why that's the case。 So intuitively， it makes sense。

 but formally， let's look at an example。 What is the probability， for example， that x。Is hard。

And why。Is 6。What is the probability of getting the six of hearts， Well， it's one out of 52 cards。

 so it's one over 52。Now， what is the probability just by itself that xs hearts。

If you pick a card at random， the probability of getting a hard is a quarter since there are four suits。

And what's the probability that y by itself， is 6。If you pick a card at random。

 the probability of getting a six is one out of13。And indeed。

 one over 52 is equal to a quarter times 1 over 13。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_4.png)

And so these two variables are independent。Let's do another example。

 supposeupp you have a fair coin and you flip it 10 times。

And you' let x be the total number of heads you see。And let why be the very last toss。

 heads or tails。A these independent of each other。So intuitively， these do not seem independent。

 for example， if x is large， if there were lots of heads。

Then it makes it more likely that the last dots was also aheads。

So it seems like they really influence each other。But let's see more precisely why this formula breaks down okay。

Why is this formula violated。Look at a particular setting。 What is the probability that excess 10。

And why is tails？

![](img/3d99d6b09ea9b0de84899b04aa352e3c_6.png)

Okay， so what is the probability that。All 10 tosses are heads。

But the last osses attaintails clearly0。 It cannot happen。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_8.png)

But now if you look at these two events separately。The probability that all 10 tosses are heads。

Is greater than0， it's a half timesns a half timesns a half ten0 times。

 so it's  one over two to the 10。And the probability that the last asses tails。It's just a half。

And clearly，0 is not equal to1 over2 to the 10 times a half。

 And so these variables are not independent。 They are dependent。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_10.png)

Okay， here's another example， so now we have two variables， x and Y。Which each decon values minus-1。

0 or plus 1。And the distribution is summarized in this table over here。 So， for example。

This entry over here。Means that the probability。That x is negative 1。And。Y is 1 is 0。24。Okay。

 so that's what this table means。So needless to say the numbers in the table add up to one。

So now are X and Y independent。Well， we have to check this formula。 And in order to do that。 So we。

 we have everything we need for the left hand side。 But now for the right hand side。

 we need the individual distributions for x just by itself and y just by itself。

 So let's obtain those。 Okay， so let's look at X by itself。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_12.png)

X can take on value either minus1， 0 or plus 1。And what are the probabilities of these？Well。

 the probability that x is minus1， x can be minus1 in three ways。

Any of the three situations on this line， so we just add them up the probability that x is minus 1 is 0。

4 plus 0。16 plus 024 which is 0。8。What is the probability that x is zero， though that's on this line？

So we add up those numbers and we get 0。1。And what is the probability that x is 1。

 Well that's this line？And that's again， point1。 And of course， these things add up to1 again。 Okay。

 so that's the distribution of x。 Now， let's go ahead and do the same thing for y。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_14.png)

So we have Y over here。And it takes on values minus-1，0 or plus 1。

And probability that y is minus1 is this line over here， so it's 0。5。

The probability that it's 0 is this line here， so it's0。2。And the rest is of co 0。3。

So that's the distribution of why。Now to check if these are independent。

We have to check that every entry in this table。Of the joint distribution is the product of the corresponding entries in the individual distributions。

So for example， let's look at this entry here for x equals minus1 and y equals 1。

Is this equal to this number？Timens this number。Yes， it is。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_16.png)

Okay， so that entry is okay。 and in that way， we keep going and we check all nine of these entries。

 and it turns out that in every case， the entry in this table。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_18.png)

Is equal to the product of the corresponding entries in the individual table， so this， for example。

 is equal to this。Times this。And so， X and Y are independent。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_20.png)

Okay， so now we'll start talking about dependence。 and let's just start with a little bit of a thought experiment。

 So suppose you pick a person at random from whatever city you're living in。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_22.png)

And let H be their height and W be their weight。Are H andW independent of each other。So intuitively。

 one would think that they are not okay， and the reason for that is that people who are taller are also likely to be heavier。

So it seems like there's some sort of correlation between them， a positive correlation， in fact。

 we would expect height and weight to be positively correlated。Okay。

So here's a picture of what it might look like， and so what I've drawn over here is， you know。

 suppose one took a sample of about 20 people。And plotted their heights and weights。

It might look something like this。 Okay， there's a general upward trend。

 People who are taller tend to be heavier。Now， of course， knowing someone's height。

 you can't exactly predict their weight and nor is it a hard and far rule。 So， for example。

This person over here is taller than that person and is also lighter。

 But there is a general trend that the points are sloping upwards。

 And what this also means is that we would expect the average of height times weight。

To be greater than the average height times the average weight。

 And this is because the large values of H tend to be paired with the large values of W。

 So if you multiply them together， you get a sort of squaring effect。Okay。

And so the average of h times W。Is likely going to be higher than the average H times the average W。

And so this is what positive correlation looks like。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_24.png)

Now the other two types of correlation are negative correlation and a complete lack of correlation。

So in negative correlation， the points rather than seeming to slope upwards are sloping downwards like this。

And in this picture， the larger values of x tend to get paired with the smaller values of y。

 As a result， one would expect that the average value of x times y。

Is actually less than the average x times the average y。And then there's a situation。Where。

No matter how large or small x is。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_26.png)

The wise， on average。Tend to have the same mean。And that situation is called uncorrelated。 Okay。

 And over there， we would expect that the average value of x times y is just the average x times the average y。

 Okay， so this is a spread of points that's neither sloping upwards or downwards。

So this is a very hand wavy and qualitative view of correlation。

Can we come up with a precise formula for this， an actual number that captures correlation。

 and this was something that was done by Carl Pearson at the beginning of the 20th century。

So he was interested in the correlation between a father's height and his son's height。

And so what he did is he obtained data from about 2000 father son bears， and he plotted them。 Okay。

 and that's the scatter plot you see over here。 So on the X axis are the father's heights。

 and on the Y axis are the son's heights。 Okay， so， for example， this over here。

comeses from a father son pair in which the father is about 66 inches and the sun is about 60 inches。

Okay。And what you can see over here is a general upward trend。

 so there does seem to be a positive correlation。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_28.png)

Now what Pearson did is to define something called a correlation coefficient。

This is a number between minus1 and plus1 that captures the degree of correlation。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_30.png)

So a value of -1 means perfect negative correlation and a value of plus1 means perfect positive correlation。

 Okay， so let's see some examples of these values。 Okay。

 so when the correlation coefficient is one like in this picture。😊。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_32.png)

There's a perfect linear relationship between the two variables。

Then when the correlation drops a little bit to say 0。75， there's still a very clear upward trend。

When the correlation drops further to 0。25， the points start to look a little bit more like a blob。

 and the case when R equals0 is the uncorrelated situation。Now。

 when the values start to drop below  zero， then we get the symmetric situation with negative correlation so it moves more and more towards a perfect。

 linear but negatively slope relationship。Okay。So what is the formula。

 how does one obtain this value are？Well， in many ways we anticipated it when we were back here。

 we said that one way to determine correlation is to compare the expected value of X Y。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_34.png)

With the expected value of x times the expected value of y。

 So let's just look at these two quantities， the left hand side and right hand side and look at their difference。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_36.png)

And this is what we call the covariance。So the covariance between two variables。

 X and Y is just the expected value of x， Y minus。Expected value of x times expected value of y。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_38.png)

When this is positive， it means we have a positive correlation， when it's negative。

 we have a negative correlation， and when it's0， x and y are uncorrelated。It's a very nice。

 simple measure of dependence。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_40.png)

Now， the one draw back to this is that it actually is not necessarily in the range minus1 to plus one。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_42.png)

![](img/3d99d6b09ea9b0de84899b04aa352e3c_43.png)

So you can show mathematically that actually the range that covariance lies in。

Is minus the standard deviation of x times the standard deviation of y。

 that's the smallest it can be all the way to the standard deviation of x times the standard deviation of y。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_45.png)

It lies somewhere in that range。So if we want to normalize it to a value in the range -1 to plus1。

 what should we do， Well， let's just divide it by the standard deviations of x and y。

And that is Pearson's correlation coefficient。So there's a nice normalized value in the range minus1 to plus1。

Now。One interesting question is how this relates to independence。When two variables are independent。

 we know that they are going to be uncorrelated。But it turns out that the reverse need not be the case。

Correlation variables being uncorrelated is actually a much weaker condition than them being independent。

 It's quite possible to have two variables that have zero correlation。

But are dependent on each other。Okay， so it's a one way relationship。 Independent means uncorrelated。

 but uncorrelated does not mean independent。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_47.png)

Let's finish with an example， a numeric example where we can actually see these numbers at work Okay so here we have a pair of variables。

 X and y， and we want to figure out the covariance and correlation between them。

 We want to figure out the level of dependence between these two variables。😊。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_49.png)

![](img/3d99d6b09ea9b0de84899b04aa352e3c_50.png)

so let's write down formula again just to remind ourselves the covariance of it。

X and Y is the expected value of X， Y。Minus the expected value of x times the expected value of y。

So in order to figure this out， we do need to figure out the expected value of x and the expected value of y so let's start by doing that Okay。

 so let's just look at x by itself。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_52.png)

Okay。X takes on values either minus1 or plus 1。The probability that x is minus1， well。

 x is minus1 in these two lines， so the probability is a sixth plus a third， which is a hat。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_54.png)

And so the probability that x is plus1 is also have。

And this means that the expected value of x is just 0。And while we're at it。

 let's also do the variance。The variance of x is the expected value of x squared。

Minus the expected value of x。Squared。And let's see what that is。Well， x is either minus1 or plus1。

 so x squared is always one， so the expected value of x squared is just  one。And this window is 0。

 so the variance is more。And that means that the standard deviation of x is also one。

The typical distance of x from the mean is one。 And in fact， that makes perfect sense。

 the distance of x from the mean is always exactly one。Okay。Now let's go ahead and do why。

So y is either minus3 or plus 3？And it's minus3 in these two lines。

And so that's what probability have。And as plus3 with probability half。

 so the expected value of y is again 0。And the variance of y。

Is the expected value of y squared minus the expected value of y the holding thing squared。Okay。

 so y squared， y is e minus3 or plus 3， so y squared is exactly 9。

 so the expected value of y squared is9。So the variance of y is 9。

 which means its standard deviation is 3， so the typical distance of y from its mean is 3。

And in fact， it's always distance three from its meeting。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_56.png)

Great， now in order to compute the covariance we also need x times y， so let's do that too。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_58.png)

Let's leave a little space for it here。X times y is either minus 3 or plus 3。

The probability of minus3。It's-3 in these two lines。

 so it's -3 with probability 2 third and plus 3 is probably one third。

 which means that the expected value of x Y。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_60.png)

![](img/3d99d6b09ea9b0de84899b04aa352e3c_61.png)

I is minus3 times2 third plus three times 1 third， which is minus-1。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_63.png)

Okay。Good， so now we have everything we need for the covariance of xy， it is minus1 minus0。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_65.png)

![](img/3d99d6b09ea9b0de84899b04aa352e3c_66.png)

So it's minus one。There's a negative correlation between x and y。

Now to get the actual correlation coefficient。We divide by the standard deviations。

So we take the covariance and we divide by the standard deviation of x and the standard deviation of y。



![](img/3d99d6b09ea9b0de84899b04aa352e3c_68.png)

And so that's minus1。The standard deviation of x is 1， the standard deviation of y is3。

So the correlation is minus1 third。There's a weak negative correlation between these two variables。

Okay， well， that's it for our probability review。

![](img/3d99d6b09ea9b0de84899b04aa352e3c_70.png)

We are now in a situation where we can start doing generative modeling in which we are able to actually capture the dependence between features in order to get more accurate classification。

