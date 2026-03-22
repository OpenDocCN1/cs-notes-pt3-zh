# 【加州大学圣地亚哥分校】机器学习基础  Machine Learning Fundamentals p29 06-05-02-线性代数_IV -BV1TyFSziEZb_p29-

![](img/ea32fa6a695f787a519e29020d58cf2d_0.png)

Positive semi definite matrices are square matrices that have many special properties。😊。

They arise all over the place， in machine learning。

So today we'll see what it means for a matrix to be positive semi definite。



![](img/ea32fa6a695f787a519e29020d58cf2d_2.png)

And we look at some of the properties of these matrices。



![](img/ea32fa6a695f787a519e29020d58cf2d_4.png)

We'll also cover the important question of how you figure out if a matrix is of this type。



![](img/ea32fa6a695f787a519e29020d58cf2d_6.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_7.png)

Now， when we were talking about convexity。We said that a function of one variable is convex if its second derivative is always positive。

When you have a function of D variables， however， the second derivative is a D by D matrix。



![](img/ea32fa6a695f787a519e29020d58cf2d_9.png)

What might it mean for a D by D square matrix to be positive？



![](img/ea32fa6a695f787a519e29020d58cf2d_11.png)

How could we define that？Well， one natural notion is to say that a matrix is positive。

 if all the entries in it are positive。

![](img/ea32fa6a695f787a519e29020d58cf2d_13.png)

This is reasonable enough， but it turns out to be a superficial notion that doesn't really help us very much。



![](img/ea32fa6a695f787a519e29020d58cf2d_15.png)

There's a deeper and more insightful notion。We can say。That a matrix， a square matrix。

 is positive if the quadratic function defined by it。Is always positive。嗯。

Let's see what this might mean。Okay， so here's the matrix。

What is the quadratic function defined by this matrix？



![](img/ea32fa6a695f787a519e29020d58cf2d_17.png)

Well， if you recall， the quadratic function defined by this matrix is the function that maps a vector x。



![](img/ea32fa6a695f787a519e29020d58cf2d_19.png)

To x transpose Mx。

![](img/ea32fa6a695f787a519e29020d58cf2d_21.png)

So in this particular example， x has to be a two dimensional vector and the quadratic function sends this vector。

 say x1 x2。

![](img/ea32fa6a695f787a519e29020d58cf2d_23.png)

To x transpose， so x1， x2 times m1，1，1，1 times x x1， x2。



![](img/ea32fa6a695f787a519e29020d58cf2d_25.png)

What is that， well， let's work it out， let's start by doing this。



![](img/ea32fa6a695f787a519e29020d58cf2d_27.png)

Thanks so we get。X1， x2。And here we get x1 plus x2。



![](img/ea32fa6a695f787a519e29020d58cf2d_29.png)

X1+ x2。

![](img/ea32fa6a695f787a519e29020d58cf2d_31.png)

And now we do the last product and we get x1 squared。



![](img/ea32fa6a695f787a519e29020d58cf2d_33.png)

Plus 2， x1 x2。Plus x2 is squared。This is the quadratic function defined by the matrix。



![](img/ea32fa6a695f787a519e29020d58cf2d_35.png)

Okay。Now if you look at that function。You can see。

![](img/ea32fa6a695f787a519e29020d58cf2d_37.png)

That it can also be written like this， x1 plus x2 squared。And when you write it like that。

It's a square， which means that it always has to be greater than or equal to 0。

 no matter what x you plug in。

![](img/ea32fa6a695f787a519e29020d58cf2d_39.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_40.png)

Okay。So we have a matrix in this case， two by two。It defines a quadratic function on two variables。

And this function is always greater than or equal to 0， no matter what x you plug in。

 So we call this matrix n positive semi deffinite。😊。



![](img/ea32fa6a695f787a519e29020d58cf2d_42.png)

More generally， let's say we have a D by D square matrix。



![](img/ea32fa6a695f787a519e29020d58cf2d_44.png)

In that case， the quadratic function defined by the matrix is this one。



![](img/ea32fa6a695f787a519e29020d58cf2d_46.png)

That sends a d dimensional vector x to x transpose mx。 So what exactly is x transpose mx well。

 it works out to a number and if you multiply it out you'll see that it's actually just the summation It's the sum overall IJ of the Ij entry of the matrix。



![](img/ea32fa6a695f787a519e29020d58cf2d_48.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_49.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_50.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_51.png)

Times the I to entry of x times the j to entry of x。 and if you add all those things up。

 that's x transposeium x。

![](img/ea32fa6a695f787a519e29020d58cf2d_53.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_54.png)

So we'll say that a matrix n is positive semi deficitite。If， first of all， it is symmetric。

And second， if this quadratic function， x transpose mx is always greater than or equal to0。

 no matter what x you plug in。

![](img/ea32fa6a695f787a519e29020d58cf2d_56.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_57.png)

This turns out to be a very powerful notion of what it means for a matrix to be positive。



![](img/ea32fa6a695f787a519e29020d58cf2d_59.png)

So let's look at an example so we've seen that this matrix is positive semi deffinite。

 we just work through that example， what about the other matrix over here？😊。



![](img/ea32fa6a695f787a519e29020d58cf2d_61.png)

Is that positive semidefinite as well。Well， it's a 2 by 2 matrix。

 so the quadratic function is the one that sends x1 x2。



![](img/ea32fa6a695f787a519e29020d58cf2d_63.png)

To x transpose N x。 And if we just plug into our usual expansion， this would be。



![](img/ea32fa6a695f787a519e29020d58cf2d_65.png)

You would send this。2。😔，X1 squared。Plus4 x1， x2 plus x2 squared。



![](img/ea32fa6a695f787a519e29020d58cf2d_67.png)

That's the quadratic function， given by the matrix。So is this always greater than or equal to zero？😔。



![](img/ea32fa6a695f787a519e29020d58cf2d_69.png)

You know what， let's try some values。 What about trying x1 equals1。And x2 equals -1。

 What happens then。In that case， we get1 minus4 plus1。Which is negative to。Okay。

 so this matrix is not positive semidefinite。And yet it looks more positive than the other matrix。

 which we know is positive semidefinite。

![](img/ea32fa6a695f787a519e29020d58cf2d_71.png)

Here's another question。Suppose we have a diagonal matrix。



![](img/ea32fa6a695f787a519e29020d58cf2d_73.png)

Under what conditions is it positive semidefinite Okay， so we have some diagonal matrix。

 So the diagonal entries are M11， M22 all the way to M D D。



![](img/ea32fa6a695f787a519e29020d58cf2d_75.png)

And everything else is a zero。

![](img/ea32fa6a695f787a519e29020d58cf2d_77.png)

When is a matrix like this positive semi deffinite？Well。

 we know x transpose Mx has to be greater than or equal to0， why do we try this x？Let's cry。

The vector x， which is0 everywhere， except for one at the height position。 Okay， so it's all zeros。



![](img/ea32fa6a695f787a519e29020d58cf2d_79.png)

Except for a one at the height position。What is x transpose M x？Well， if we think of our summation。

The sum of MI J， X I Xj， you can see that x transpose Mx is just the II entry of the matrix。

And so we know that this has to be greater than or equal to 0。So that gives us a simple condition。

 a diagonal matrix is positive semideinite。

![](img/ea32fa6a695f787a519e29020d58cf2d_81.png)

If and only if。All the diagonal entries are greater than or equal to0。



![](img/ea32fa6a695f787a519e29020d58cf2d_83.png)

So for diagonal matrices， it's very easy to check。Okay。Now。

 suppose we have a positive semi deffinite matrix M。

 What about2 times M is that positive semi definite as well？



![](img/ea32fa6a695f787a519e29020d58cf2d_85.png)

Yes， it is。

![](img/ea32fa6a695f787a519e29020d58cf2d_87.png)

And more generally， what about C times in？Well let's take a look， so we have x transpose C times mx。



![](img/ea32fa6a695f787a519e29020d58cf2d_89.png)

We can sees just a constant so we can pull it out。So it's C times x transpose Nx。

And M is positive semidefininite。So this is greater than or equal to zero。

C times that is that greater than or equal to0， yes， provided C is greater than or equal to 0。Okay。

So the answer is yes。If C is greater than or equal to 0。嗯。



![](img/ea32fa6a695f787a519e29020d58cf2d_91.png)

Here's a related question。 Suppose you have two matrices that are each positive semi definite。

 What about their sum。

![](img/ea32fa6a695f787a519e29020d58cf2d_93.png)

Is that positive semidefinite？Well， again， we can just try directly by plugging into the definition。



![](img/ea32fa6a695f787a519e29020d58cf2d_95.png)

Let's take their sum and plus and look at ex transposed。



![](img/ea32fa6a695f787a519e29020d58cf2d_97.png)

M plus N X。Now we can factor this， this is just equal to x transpose Mx。Plus， x transpose anex。

And each of these are greater than or equal to 0。

![](img/ea32fa6a695f787a519e29020d58cf2d_99.png)

So the whole thing is greater than or equal to0。And so the answer to this question is just a simple yes。



![](img/ea32fa6a695f787a519e29020d58cf2d_101.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_102.png)

Okay， so we've seen many properties of positive semi deffinite matrices。



![](img/ea32fa6a695f787a519e29020d58cf2d_104.png)

But the thing that we're going to have to do pretty often is to figure out whether a given matrix is positive semidefinite。

Now， technically， that means that we have to check if x transpose mx is greater than or equal to0 for all x。

That's difficult to do because there are infinitely many choices for X。

 I there a simple way is there some more direct way of checking whether a matrix is positive semidefinite and indeed there is this very simple condition。

😊。

![](img/ea32fa6a695f787a519e29020d58cf2d_106.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_107.png)

It's positive semi definite if it's of the form U U transpose。



![](img/ea32fa6a695f787a519e29020d58cf2d_109.png)

Okay。So let's just briefly go over the justification for this。So let's say that M is off this form。

 U U transpose and U is just any old matrix， let's say it's an R by D matrix and let's just go and check all the properties for positive semidefinite。

So first of all， is M even a square matrix， Well let's see。M is U U transpose。



![](img/ea32fa6a695f787a519e29020d58cf2d_111.png)

U is R by D and U transposees D by R， so M is an R by R matrix， yes， it's square。



![](img/ea32fa6a695f787a519e29020d58cf2d_113.png)

Okay， we're off to a good start。Now is msymmetric， Okay， let's see。



![](img/ea32fa6a695f787a519e29020d58cf2d_115.png)

Well， you U transpose， what's the transpose of that？What is that equal to Well， if you remember。

 we have this formula for transpose， A B transpose is B transpose A transpose。 So if we apply that。

 we get。U transpose transpose times u transpose。

![](img/ea32fa6a695f787a519e29020d58cf2d_117.png)

What is transpose transpose， Well， if you just transpose a matrix twice。

 you get back the same matrix， so that's just U you transpose。And yes。M transpose equal to M。

 so it is symmetric。Okay， so just one last property to check okay。



![](img/ea32fa6a695f787a519e29020d58cf2d_119.png)

So x transpose Mx， we plug in。UU transpose forM。And now we have this matrix vector product involving four terms。



![](img/ea32fa6a695f787a519e29020d58cf2d_121.png)

We can just parenthesize this however we like， so let's do it like this。

 let's put the parentheses there。

![](img/ea32fa6a695f787a519e29020d58cf2d_123.png)

and let's look at these terms now。X transpose U by again using this transpose formula。

 we can just write that as u transpose x transposed。And now you transpose X is just a vector。

And so we get something of the form vector transpose with itself。

That's familiar if you remember z transpose z is just the length of z squared so u transpose x transposed times u transpose x is just the length of u transpoposedse x squared。



![](img/ea32fa6a695f787a519e29020d58cf2d_125.png)

![](img/ea32fa6a695f787a519e29020d58cf2d_126.png)

And since the squared length， it has to be greater than or equal to0。And so a matrix of this form。

Has to be positive semi definite。This will turn out to be a very useful rule。



![](img/ea32fa6a695f787a519e29020d58cf2d_128.png)

Now， essentially the same argument can be used to show something else that will be useful。

Which is that any covariance matrix is guaranteed to be positive semidefinite。😊。



![](img/ea32fa6a695f787a519e29020d58cf2d_130.png)

So here's a picture that I would like to leave you with。We're talking about square matrices。

 say D by D matrices。Some of these matrices are symmetric， that is M equals m transpose。

 This is a special property。An even more special case。

Is when the quadratic function defined by the matrix。

X transpose M x is always greater than or equal to 0。 no matter what x you plug in。

These are the positive semi definite matrices。They arise all the time in machine learning。

 and we rely upon them very heavily in many different contexts。



![](img/ea32fa6a695f787a519e29020d58cf2d_132.png)

Okay， that's enough for today。We finally seen what it means for a matrix to be positive semi deffininite。

And we've already seen one use of these matrices in deciding whether a function is convex。

We'll soon see many more uses。See you soon。