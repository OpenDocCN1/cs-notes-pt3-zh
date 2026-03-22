# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p44 09-01-02-表征学习 -BV1TyFSziEZb_p44-

![](img/a8d93371e225493485aad6a5e59b8f4d_0.png)

We've spent a lot of time on how to build predictive models of data。Classifiers， regressors。

 probability estimators。The whole time， we've been assuming that the representation of the data。

 the features， the distance function， the similarity function。

 that this representation is just given to us and is somehow fixed。But in general。

 this isn't the case， and in fact the efficacy of these predictive methods。

 all of them depends crucially on having a good representation of the data。In a nutshell。

Good representations make learning easier。

![](img/a8d93371e225493485aad6a5e59b8f4d_2.png)

And this happens for a variety of reasons in a variety of ways。



![](img/a8d93371e225493485aad6a5e59b8f4d_4.png)

A good representation brings out the true degrees of freedom in the data。

It captures  structure in the data at many different scales。

Helps screen out noise and down weights irrelevant features。嗯。Now。

 all of these things sound very good。But what do they mean exactly what do I mean， for instance。

 when I talk about the degrees of freedom in data， so let's look at an example to make this a bit clearer。



![](img/a8d93371e225493485aad6a5e59b8f4d_6.png)

Here is a speech signal。It's a one dimensional time series。When I speak。

I agitate the molecules in the air in front of my mouth， and this propagates a wave。



![](img/a8d93371e225493485aad6a5e59b8f4d_8.png)

When this wave reaches your ear， you have this very thin diaphragm in your ear that wiggles in response to this disturbance and the signal over here。

 this one dimensional signal is literally just the displacement of that diaphragm。



![](img/a8d93371e225493485aad6a5e59b8f4d_10.png)

The way in which it's wiggling。Okay， so this is a continuous one dimensional time series。😔。

If we want to process it on a computer， for example， if we want to do speech recognition。

 we have to somehow digitize it and discreitize it， how is that usually done？

Well here's one common way， the first thing is to take the speech signal and to divide it into a bunch of overlapping windows。

 say windows of。25 milliseconds Okay， so you have a particular window， maybe something like this。



![](img/a8d93371e225493485aad6a5e59b8f4d_12.png)

![](img/a8d93371e225493485aad6a5e59b8f4d_13.png)

And then for that window， you apply a variety of filters， so maybe filter number one looks like this。

Okay。And filter number two looks like this。 and filter number  three looks like that。

Each filter yields a number。So maybe this yields 23， this yields negative6， this yields 17 and so on。

And these numbers get stacked together into a vector。



![](img/a8d93371e225493485aad6a5e59b8f4d_15.png)

In this way， that window of continuous sound gets converted to a point in some higher dimensional Euclidean space。



![](img/a8d93371e225493485aad6a5e59b8f4d_17.png)

Now， the more filters we use， the higher the dimension。

 so we can actually get a representation that's super high dimensional。

But there's something a little bit deceptive about this， after all。

Even though it might seem very high dimensional。

![](img/a8d93371e225493485aad6a5e59b8f4d_19.png)

The speech is produced by a physical apparatus by my vocal track。

 and this is a physical system that just has a few degrees of freedom。



![](img/a8d93371e225493485aad6a5e59b8f4d_21.png)

So， they are a way。To take this very high dimensional representation。

 the concatenation of all these filter values。

![](img/a8d93371e225493485aad6a5e59b8f4d_23.png)

And somehow recover。The underlying degrees of freedom。

Is there a way to start with that higher dimensional vector and somehow simplify it or compress it？



![](img/a8d93371e225493485aad6a5e59b8f4d_25.png)

![](img/a8d93371e225493485aad6a5e59b8f4d_26.png)

Into something that really brings out the true underlying structure of this data。

Now this really depends being able to do this really depends on the relationship between these underlying degrees of freedom and the higher dimensional vector representation。

Is it a linear relationship？Is it a nonlinear function？Is it some other type of encoding。

We will be investigating a lot of these different possibilities。



![](img/a8d93371e225493485aad6a5e59b8f4d_28.png)

Another。Important aspect of representation learning is that the structure that we need to discover is often at multiple different scales。

So imagine what's needed， for example， in order to understand an image。

There is some very low level structure， for example， the individual edges。Like this。Okay。

Then there's slightly higher dimensional structure。Where， for example。

A bunch of edges have been combined to yield a familiar object like a window。

And this kind of composition， this combining of simple parts to yield a slightly more complicated object。

 can be applied over and over again to yield progressively more complicated things like the house。

The card， the horse， and so on。So we're interested in representations that have this multi scale aspect to them。

😊，So in representation learning。The goal in a nutshell is to uncover structure in the data。



![](img/a8d93371e225493485aad6a5e59b8f4d_30.png)

And we'll be focusing on certain key types of structure。

 especially cluster structure and linear projections。



![](img/a8d93371e225493485aad6a5e59b8f4d_32.png)

Later on， we'll unify a lot of this under the notion of an auto encoder。



![](img/a8d93371e225493485aad6a5e59b8f4d_34.png)

![](img/a8d93371e225493485aad6a5e59b8f4d_35.png)

Now， once a good representation is learned， then it can be used for subsequent predictive modeling。

 classification， regression， and so on。

![](img/a8d93371e225493485aad6a5e59b8f4d_37.png)

Or sometimes we don't have a specific predictive task in mind。

 but we're merely interested in understanding the data better。At the end。

 what we'll do is to look at ways in which we can combine representation learning with classifier learning。



![](img/a8d93371e225493485aad6a5e59b8f4d_39.png)

![](img/a8d93371e225493485aad6a5e59b8f4d_40.png)

And this is what deep learning strives to do。

![](img/a8d93371e225493485aad6a5e59b8f4d_42.png)

Okay， so this has been a bit of a roadmap。For the upcoming two or three weeks。

What we will do next time is to begin with our first kind of representation learning。Clustering。

