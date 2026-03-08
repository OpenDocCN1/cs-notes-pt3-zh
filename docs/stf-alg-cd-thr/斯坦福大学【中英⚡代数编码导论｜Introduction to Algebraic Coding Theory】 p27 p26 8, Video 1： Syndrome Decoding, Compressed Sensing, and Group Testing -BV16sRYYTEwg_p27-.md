# 斯坦福大学【中英⚡代数编码导论｜Introduction to Algebraic Coding Theory】 p27 p26 8, Video 1： Syndrome Decoding, Compressed Sensing, and Group Testing -BV16sRYYTEwg_p27-

![](img/6718d8020242883ae5e8a8f318e72392_0.png)

In this video， we'll see how the problem of decoding linear error correcting codes is related to two other problems called compressed sensing and group testing。

Let's start with the coding theory。We're going to define a problem called syndrome decoding。

 We've actually seen this before， but now let's give it a name。

Syndrome decoding is just the problem of decoding a linear error correcting code using its parity check matrix。

In more detail， here's the problem。Suppose that H is our parity check matrix。

 So it's n minus K by n over a finite field F Q。And suppose we have an error vector E of weight at most T。

Then the syndrome decoding problem is given H times E。

 This is called the syndrome and the parityche matrix H recover the error vector E。

And our goal is to be able to do this， all while making K。That is the dimension of the code。

 as big as possible。So the picture looks like this。We've got our parity check matrix。

 which is short and fat， our error vector。Which has not too many entries。And the product。

 which I'm defining as the syndrome。So perhaps you already see the connection to decoding error correcting codes from errors。

But， let's spell it out。In particular， if we can solve this problem。Then I claim we can correct C。

The colonel of age。That is the code for which H is the parity check matrix from T errors。

More precisely， given the corrupted code word C twittle。We can compute H times C twiddle。

Which is equal to H times C plus E for some code word C and some error vector E。

 that has weighted most T。Which is equal to H times C plus H times E。

 which is just equal to the syndrome H times E， since C is in the code。 So this is 0。

So if we can solve this problem。Then from this syndrome and also the parodity check matrix H。

 we can recover the error vector E。And then we can just compute the original code word as C twil minus E。

We saw this paradigm earlier in our decoder for Heming codes。

 and the same paradigm is also used by the Burlean Maey algorithm for Read Solomon codes。Thus。

 this part of the problem。Will make us able to decode the code C from T errors。

And this goal is saying that we want the dimension to be as big as possible。 A K。

 we want the rate to be as big as possible。 So this is the same thing that we've always been looking for。

Okay， so that's the syndrome decoding problem。 Now let's see two other problems that look syntactically very similar。

 but have a slightly different flavor。The first of these similar problems is called compressed sensing or sparse recovery。

So， here's the problem。It looks a lot like the problem we had on the previous slide。

What if you pause the video now and try to pick out the differences。Okay。

 so here are the differences。 There's a few cosmetic differences。 Like for some reason。

 I've changed the name H of the matrix into phi。And I've changed the number of rows of the matrix from n minus K to M。

 And E turned into X and stuff like that。I've also changed the names。Of these things over here。

 instead of calling this the parity check matrix， I'm now calling it the sensing matrix。

And instead of calling this the syndrome， I'm now calling these the observations。

 We'll see why in a moment。But those are all just sort of notational changes。

The only big change here is that I have changed the finite field F Q。Into the complex numbers。

Just as an aside， compressed sensing or sparse recovery also works fine over the reels。

 But let's just go with the complex numbers for now。 So that's the only change。

 It's exactly the same problem， except now over C， instead of over FQ。

And my goal now is still to make the number of rows of this matrix as small as possible。

 which was the same as my goal in syndrome decoding。Okay， so why do I care about this problem？

 Why would I want to solve this over the complex numbers。

The reason that we care comes from signal processing。In particular。

 it comes from the fact that lots of naturally occurring data are sparse。And here by sparse， I mean。

 mostly zero or mostly close to zero。For example， many natural images are sparse。

 or at least sparse when you write them in the correct basis。For example。

 here is a nice picture of a castle。 This picture is not especially sparse in the sense that most of its pixels are not 0 or approximately 0。

 However， when you take a discrete wavelet transform of this image or at least the black and white version of this image。

 you get this。And you note that this thing is sparse。

 That is most of the pixels are black or approximately 0。Similarly。

 lots of other naturally occurring signals。 for example。

 audio data are sparse when you put them in the right basis。Okay。

 so given that we have all this data that are sparse。

The reason we might be interested in this problem。Is that sometimes we can measure or observe that data in a linear way。

That is， if our sparse data is denoted by x， just as sum vector。

 If we can measure that data as phi times x for some matrix phi that looks like this。

 that's short and fat。That means that we don't need to store all of X。

 We just need to store p times X。In particular， if M here is really small， much， much less than n。

 And if you can efficiently recover X given Phi X， this is a win。

This general paradigm has applications in streaming algorithms， signal processing。

 and medical imaging。And it turns out that you can actually solve this problem pretty well。

 just like we can solve the syndrome decoding problem。In fact。

 working over the complex numbers or over R can actually make this problem easier than working over a finite field。

Here's a second problem that is syntactically very similar to syndrome decoding called group testing。

To explain this problem， let curly be。Deote this Boolean algebra。 So the elements are 0，1。

 and my operations are plus and times， but now plus is going to mean the Boolean or and times is going to mean the boolean and。

With that definition， we can ask exactly the same problem。Again， here， nothing has changed。

 except I've changed this。From F to C to B， this Boolean algebra。

I've also changed a few cosmetic things like this is a capital end now。

 and I've changed the names of these things。In particular。

 the matrix is now called a pooling design for reasons we'll see in a moment。Okay。

 so exactly the same problem。 But now over this Boolean algebra。Once again， we might ask。

 why do we care？This problem actually comes up in a lot of applications。

 It was originally introduced for testing for disease。 So here's how that works。

So suppose that there are N people。Tea of whom are sick。Say these are the sick ones。However。

 we don't know who is sick。And we need to do a blood test to figure that out。

One option is to do end blood tests， one on each person。So maybe that looks something like this。

This is supposed to be a test tube。And I guess that's supposed to be blood。

So we take N samples and we do N blood tests。And then some of them come up positive。

And we know who the sick people were。Okay， that works fine， but。We used a lot of tests。

If tests are expensive， we might hope to do better。 and， in fact， we can。So。

 here's the second option。Option two is to pool blood samples。That is。

 we're going to have only M tests where M is much less than N。Say just those tests。But in each test。

 we're going to mix multiple different people's samples。So maybe in this test。

 I have samples coming from this person and that person and that person。In this tests。

 I have samples from that one and that one and so on。Then at the end of the day。

 a test is going to be positive if there was any sick person who participated in that test。

So in this little partial example that I've drawn here。

 this test would come up positive because this sick person participated in that test。

Note that there are only two possible outcomes for a test， positive or negative。

 So if lots of sick people participate in a test， it doesn't get super positive or anything like that。

 It's just one bit， positive or negative。Okay， so that's the setup。

And the hope is that from the outcome of these pooled tests， we can figure out。

Who the T sick people are。And ideally， if M is much less than N。

 willll have saved some resources by doing fewer tests。Okay。

 but what does this picture have to do with this problem？Well。

 let's consider setting up the following matrix。

![](img/6718d8020242883ae5e8a8f318e72392_2.png)

So I'm going to set up a matrix that is M by n， which describes my pooling design。

The rows are going to be indexed by the M tests that I'm going to do。

 And the columns are going to be indexed by the N people that I want to test。



![](img/6718d8020242883ae5e8a8f318e72392_4.png)

![](img/6718d8020242883ae5e8a8f318e72392_5.png)

We'll put a one in the matrix。If this person participates in that test。



![](img/6718d8020242883ae5e8a8f318e72392_7.png)

And otherwise， we'll put a zero。

![](img/6718d8020242883ae5e8a8f318e72392_9.png)

Now， given this matrix。

![](img/6718d8020242883ae5e8a8f318e72392_11.png)

Let's suggestively call it Phi。

![](img/6718d8020242883ae5e8a8f318e72392_13.png)

Consider setting up the following equation。So for each person who's sick。

 say that ones sick and that one's sick。

![](img/6718d8020242883ae5e8a8f318e72392_15.png)

I'm going to put a one in the corresponding spot in this vector。

So I get some sparse vector that looks like this。Notice that this vector only has T1s in it if there are T sick people。

And now let's consider this entry of the output。 If I'm doing this matrix vector multiplication here over that Boolean algebra。

 So every time I want to do a multiplication， I just do a and and every time I want to do an addition。

 I just do an or。What am I going to get in this coordinate of the output？

So this is going to be the or。

![](img/6718d8020242883ae5e8a8f318e72392_17.png)

Over all of the people。Of the and。Of the boolean variable that is one， if that person is sick。

That corresponds to the value in this vector。And did。With the Boolean vector， that is one。

If the person participates。In this test here。And this corresponds to the relevant entry in that row。

Okay， but what is this equation saying？This is going to be one。

If and only if this test had any sick people in it。AK A， if and only if that test comes up positive。



![](img/6718d8020242883ae5e8a8f318e72392_19.png)

Therefore， this vector here。Is precisely the vector of test outcomes。

What that means is that if our goal is to find the sick people。

 given the test outcomes with as few tests as possible。That's the same。

As finding X given phi times X with M as small as possible。

And that's the problem that we had on the previous slide。

So that's why this problem has this form the same form as syndrome decoding just over boolean algebra instead of C or FQ。

 and also that's why it's interesting。Group testing was introduced in the 1940s for testing for disease in US Army soldiers。

Since then， it has found uses in a wide variety of applications from high throughput genetic screening to wireless communications。

To recap， we saw this same problem。

![](img/6718d8020242883ae5e8a8f318e72392_21.png)

3 different ways。That is， the problem is。

![](img/6718d8020242883ae5e8a8f318e72392_23.png)

Given the output of a short fat matrix times a long sparse vector。



![](img/6718d8020242883ae5e8a8f318e72392_25.png)

And given a description of the matrix， recover the long sparse vector。



![](img/6718d8020242883ae5e8a8f318e72392_27.png)

We saw that over a finite field。

![](img/6718d8020242883ae5e8a8f318e72392_29.png)

This is the problem of syndrome decoding。Useful for air correcting codes。

Over the complex numbers of the reels， this is called sparse recovery or compressed sensing。

And it's useful for a variety of applications in signal processing。Over a boolean algebra。

 this is called group testing。

![](img/6718d8020242883ae5e8a8f318e72392_31.png)

And it's useful for testing a large population for a rare trait。



![](img/6718d8020242883ae5e8a8f318e72392_33.png)

All of these problems are different， and they come with different algorithms and different solutions。



![](img/6718d8020242883ae5e8a8f318e72392_35.png)

However， as you might imagine， the same techniques can show up in all three。



![](img/6718d8020242883ae5e8a8f318e72392_37.png)

In the next few videos， we'll focus on group testing。



![](img/6718d8020242883ae5e8a8f318e72392_39.png)

And we'll see how ideas from coding theory， in particular Read Solomon codes can be used to get a good solution to the group testing problem。



![](img/6718d8020242883ae5e8a8f318e72392_41.png)