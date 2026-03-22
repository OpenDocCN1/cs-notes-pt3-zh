# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p53 10-05-02-特征值与特征向量 -BV1TyFSziEZb_p53-

![](img/5cb7385b75f21818f594f97f0b3ac2e9_0.png)

The notion of eigenvectors and eigenvalues have been popppping up now and again。

And we keep postponing the discussion。Well， the time is finally upon us。

So what we'll talk about today is finding a natural coordinate system for a data set。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_2.png)

When we think of data， we used to thinking about it in terms of the features we have selected。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_4.png)

The individual coordinates of the data vectors。But it turns out that data analysis often becomes much simpler if we move to an alternative coordinate system。

And this is what leads ultimately to the notion of an eigenvector。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_6.png)

So in this picture， we have a simple two dimensional data set。The two features。

And they are positively correlated。If we were to fit a Gaussian into this data。

 it would look something like this。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_8.png)

嗯。So what I'm going to do is to show you an alternative coordinate system for this data。

This one over here。Instead of the regular coordinate axes E1 and E2， we have these tilted axes。

 U1 and U2。We could move quite easily between these two systems。 It's a simple rotation。

And in many ways， these red coordinates， U1 in U2， are more natural for this data。

What's so good about them， Well， if you tilt your head slightly， you'll see that in this new basis。

 the two coordinates are actually uncorrelated。For instance。

 we could fit a diagonal Gaussian to them。Things get simpler in this alternative coordinate system。

Okay， so let's try and formalize some of this， and for that we're going to need linear algebra。

So let M be any D by D matrix， any square matrix， and as we've seen。

 a matrix like this defines a linear function。A function that takes a vector x。

And sends it to some other de dimensional vector Mx。So okay。

 it's a linear function and we've seen examples of this， but what exactly is this function doing？

It's hard to visualize or imagine what this transformation is from one day D dimensional vector to another。

But that's a special case in which these transformations are actually very simple to understand。

 and that is when the matrix is diagonal。😊。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_10.png)

Okay， so here we have an example of a diagonal matrix， a three by three matrix。

So this defines a linear transformation from three dimensional vectors to three dimensional vectors。

 and because this matrix is diagonal， it's very easy to say what this transformation is。

It takes a vector x1 x2 x3。And simply doubles x1。Multiplies x2 by minus1 and multiplies x3 by 10。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_12.png)

A diagonal matrix is easy to understand because it is simply scaling each coordinate separately。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_14.png)

The coordinates don't get mixed up at all。Okay， so that's a diagonal matrix。

 what about a more general symmetric matrix？

![](img/5cb7385b75f21818f594f97f0b3ac2e9_16.png)

In that case， there are lots of off diagonal entries and they mix up the different coordinates。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_18.png)

Which can be confusing。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_20.png)

But， it turns out。That if we simply change the coordinate system。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_22.png)

If we move from our own coordinate system， the x1， x2， x3 axis to a different coordinate system。

 a coordinate system that is more natural for the matrix。Well， in that alternative basis。

The matrix again becomes something very simple。It becomes a diagonal matrix。Okay。

 so any symmetric matrix。Is actually once again a simple diagonal matrix if we move to its own coordinate system。

So what， what might these natural coordinates be， How might mine to them？Well。

 if we look at this diagonal example over here。So what we are saying is that for a diagonal matrix。

Its natural coordinates are just the regular coordinates， okay， so for example， the X1 coordinate。

 which we can write like this。Okay。So what happens when we apply M to E1？



![](img/5cb7385b75f21818f594f97f0b3ac2e9_24.png)

Well， we simply get， we simply double that first coordinate， so we get twice a E1。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_26.png)

In other words， M Sen Z1。To another vector in exactly the same direction。

It does not bleach into other directions， and that's why things are so simple。

So this gives us an idea for how we might define the notion of a natural direction。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_28.png)

So let M be any D by D matrix。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_30.png)

And we'll say you。Is an eigenvector of M。If M sends you to another vector in the same direction。

 so in some sense， this means that U is a natural direction for M。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_32.png)

![](img/5cb7385b75f21818f594f97f0b3ac2e9_33.png)

M keeps you in exactly the same direction。 M times U is just a constant， a scaling constant times U。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_35.png)

And the scaling constant is called the eigenvalue associated with that particular eigenvector， U。

So eigenvalues and eigenvectors come in pairs。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_37.png)

Okay， so let's return to the example of the diagonal matrix we just saw。

Whatutter its eigenvectors and eigenvalues。Well， we've already suggested that the natural directions for this matrix are just the coordinate directions。

 So let's try those the coordinate directions are E1。Which is 1，0，0。E2。Which is 0，1，0 and E3。

 which is 0，0，1。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_39.png)

What does M do to these directions？So M times E1。Is simply coy one。

It sends Iwan in the same direction， and so Iwan really is an eigenvector of this matrix。

So E1 is an eigenvector。And the corresponding eigenvalue is just the scaling factor， too。

So iconconvector E1。Ienvalue too。Now M sends E2。To simply minus E2。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_41.png)

And so E2 is also an eigenvector。And the eigenvalue in that case is the scaling factor minus1。

And M send E3。To 10 times E3。So E3 is an eigenvector with corresponding eigenvalue 10。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_43.png)

Okay， so E1， E2 and E3 are natural directions or eigenvectors for this diagonal matrix。

Are there any other eigenbacterctors？

![](img/5cb7385b75f21818f594f97f0b3ac2e9_45.png)

There are actually lots of other eenvectors， because。If E2。Is。An eigenvector。

Then any multiple of E2 is also by definition automatically an eigenvector okay， so for example。

 if we take some multiple of it like 0，80。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_47.png)

![](img/5cb7385b75f21818f594f97f0b3ac2e9_48.png)

That's also an eigenvector because m times that is minus1 times that so any multiple of E2 is also an eigenvector with the same eigenvalue minus1。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_50.png)

For this reason， what we often do is to normalize eigenvectors to unit length。Just like E1， E2， N3。

Okay， so let's rephrase the question then， are there any other unit length iconigenvectors of this matrix and no there aren't？

😊，So we have a  three by3 matrix with exactly three unit length iconenvectors。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_52.png)

Is that always the case， is the number of distinct unit length eigenvectors always just the dimension of the matrix？

And for our purposes， the answer is yes。Okay。The other thing to note over here is that。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_54.png)

The eigenvectors are all autogonal to each other。 The dot product of any pair of them is0。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_56.png)

Is that also always the case， Are different eigenvectors always orthogonal to each other。 And again。

 the answer is yes。And this means that the eigenvectors constitute a basis。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_58.png)

So let's go ahead and see how this channelizes Okay， so let's take any symmetric square matrix。😊。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_60.png)

If it's a D by D matrix， then it has D eigenvectors you want through UD。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_62.png)

And these are orthonormal。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_64.png)

Okay， so in other words， they all have unit length。The length of each of them is one。

 and any pair of them are orthogonal to each other。 So U I dot UJ is 0。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_66.png)

![](img/5cb7385b75f21818f594f97f0b3ac2e9_67.png)

For any I not equal to J。This means that these D eigenvectors constitute a basis。

And well think of them as the axes of a natural coordinate system for this matrix。

It turns out that transforming data into this coordinate system simplifies a lot of different operations。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_69.png)

Okay。So before we get into that， let's see another simple example and one in which the eigenvectors are not the coordinate directions。

Okay， so here's a two by two matrix。And I'm giving you the eigenvectors for the matrix you1 in year2。

And what we want to do is to compute the corresponding eigenvalues。 Okay。

 so these are the eigenvectors。 Let's first check that they really do constitute an autonormal basis Okay so。

We have two of them， okay， which makes sense for a two by two matrix。 Are they unit length。 Yes。

 their length is one。 Are they at right angles to each other。 What is U1 dot U2。



![](img/5cb7385b75f21818f594f97f0b3ac2e9_71.png)

Well， the dot product in this case is zero。So indeed， these two eigenvectors are orthonormal。

What are their eigenvalues Okay， so let's see M times u1。Well。

 we can bring the square root2 in front。So one over square root2 times 1， negative2。

 negative to1 times 1，1。And this works out to。AN one。Negative。Two plus one， so negative one。Okay。

So it sends the vector u1 to minus1 times the same vector。

So the corresponding eigenvalue is negative one。Now let's look at the other vector m times u2 and again。

 we just pull the square root 2 out in front。So we have one minus2， minus21。Times negative 11。

And we have the square root two again。And this time we have -1 so -3。And 3。

So this is exactly three times U2。And so the second eigenvalue is3。And that's it。Okay。

 so that's enough for today。

![](img/5cb7385b75f21818f594f97f0b3ac2e9_73.png)

We started by asking about what might be considered a natural coordinate system for a data set。

And this LED to the notion of an eigenvector。Next time we'll see how any matrix and in particular。

 a data matrix can be rewritten in terms of eigenvectors and eigenvalues。

This turns out to be a very powerful tool for data analysis called spectral decomposition。

See you name。