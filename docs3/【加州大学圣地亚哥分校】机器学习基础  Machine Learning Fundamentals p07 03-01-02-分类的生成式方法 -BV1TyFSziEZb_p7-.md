# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p07 03-01-02-分类的生成式方法 -BV1TyFSziEZb_p7-

![](img/a57ef406f82a467bc3f3b2efb72a99a2_0.png)

So today we will introduce a simple and powerful approach to building classifiers。

 it's called the geneerrative approach， and it's based on probability distributions。

So the main idea with the generative approach。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_2.png)

Is to fit each class separately。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_4.png)

With a probability distribution， okay， so for example。

 here we have a training set of about 15 to 20 points。

And what we do is that we first look only at one label， so here there are two labels。

 pluses and minuses， so we start by looking just at the pluses and we fit a model to them。

And then we look only at the minuses and we've fit a model to those。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_6.png)

So maybe we get something like this。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_8.png)

so on the left， we have an ellipse shape distribution that we fit through the pluses。

And then we have another ellipse shape distribution that we fitted to the minuses。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_10.png)

That's it for the learning process。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_12.png)

Now， when a new point comes along， let's say a point like this。And we want to classify it。

 we just ask ourselves， was this new point more likely to have come from the red distribution or the blue distribution。

 and which of these two distributions does it have higher probability？



![](img/a57ef406f82a467bc3f3b2efb72a99a2_14.png)

![](img/a57ef406f82a467bc3f3b2efb72a99a2_15.png)

And that's it。Okay， so that's a high level overview of the generative approach。

So let's be a little bit more concrete and put down some details。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_17.png)

Okay。So here's a picture in which there are three classes or three labels。

 let's call them one two and3， so the label space Y is just a set one， two and three。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_19.png)

And let's say that the data is very simple， the data just has one feature。

 so the data points are one dimensional， and they can just be plotted on the line。

So in order to fit a generative model， what we do is we take our training set。And first。

 we look only at the points whose label is one。And we fit a probability distribution to them。

 So maybe， for example， we get this distribution over here， the red one。 Okay。

 let's call that P1 of x， the distribution for label 1。Then。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_21.png)

We take the training set again and look only at the points whose label is too and we've fit a probability distribution to those。

 maybe that looks like P2 of x over here。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_23.png)

And finally， we look at the remaining points， the ones that have labeled three。

 and we've made a probability distribution to that， so that's B3 of x。

 and now we have these three separate probability distributions。

We need a little bit more information as well， let's say， for instance。

 that label 1 makes up 10% of the training set okay， so out of the training points。

110 of them have label 1 so what we'll do is we'll say 51 equals 10% or 0。1。

Let's say label 2 makes up 50% of the training set， so it by2 equals 50% or 0。5。

And the remaining 40% of the training set comes from label 3， so we say pi 3 equals 0。4。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_25.png)

Now， at the end of this， what we have is。The following pieces of information for each class， J。

 so J is 1，2 or3， we have the probability of that class， which is just a number like 0。1 or 0。5 or 0。

4。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_27.png)

![](img/a57ef406f82a467bc3f3b2efb72a99a2_28.png)

And we also had。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_30.png)

The distribution of data in that class， which is what we've been calling piece of J， piece of1。

 piece of two， and piece of three。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_32.png)

And these pieces of information are enough to fully specify the joint distribution between x and Y。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_34.png)

![](img/a57ef406f82a467bc3f3b2efb72a99a2_35.png)

So the probability of any pair XY。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_37.png)

Is the probability of that label， why？Times the probability of seeing data X under that label Y。

 so the probability of x given y。Now the probability of seeing label Y is simply p sub y。

And the probability of seeing point x under the distribution of label Y is piece of y of x。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_39.png)

So we have the full probability distribution over x and Y。

So now a new point x comes along and we want to classify it， we want to determine a label Y for it。

 which label do we pick？

![](img/a57ef406f82a467bc3f3b2efb72a99a2_41.png)

![](img/a57ef406f82a467bc3f3b2efb72a99a2_42.png)

Well， the most likely label， the one that maximizes the probability of x and Y。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_44.png)

Concretely， what we would do in this case with three classes is that we take our point x and we calculate pi 1 times be1 of x。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_46.png)

That's some number。We calculate pi 2 times p2 of effects。And we calculate pi3 times p3 of x。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_48.png)

And we take whichever app pieces is the largest。

![](img/a57ef406f82a467bc3f3b2efb72a99a2_50.png)

If the last one is the largest， for example， we say the label equals 3。



![](img/a57ef406f82a467bc3f3b2efb72a99a2_52.png)

Okay， so that's it for a high level overview of the generative approach to classification。

Some of the details might seem a little mysterious at this point because they rest on various probabilistic concepts。

So what we'll do next is to do a little bit of a review。

 a little bit of a tour of the relevant probability。

 and then we'll come back and we'll flesh out this approach and see an in action。

