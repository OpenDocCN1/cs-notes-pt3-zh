# 斯坦福大学【中英⚡代数编码导论｜Introduction to Algebraic Coding Theory】 p04 p3 2, Video 1： Hamming Code (Revisited) -BV16sRYYTEwg_p4-

In this video， we will revisit an example we saw before called the Hamming code。

Recall this example that we saw in a previous video。This is an example of a code with message length。

 K equals 4。Block length n equals 7 over the alphabet 0，1， and it was defined as follows。

We have our encoding map， innc。Which takes our four message bits， X 1， X 2， X 3， and x 4。

And it encodes them like this。 So the message bits themselves appear as the first four Bs of the code word。

And then the last three bits of the code word are these linear combinations mod 2 of the various message bits。

Our code C is defined as the image of the encoding map。

We also saw in a previous video this nice way of looking at this code using circles。

Where we put the message bits in the middle here。And the parody check bits。Sho it up there。

This example has a name， it's called the Hamming code or ahamming code。So from now on。

 instead of calling it example  three， I'm going to refer to it as the handming code of length 7。

In this video， we will see two new ways of looking at the Hamming code。Here's the first one。

We can view the encoding map as multiplication by a matrix mod 2。In more detail。

 we can write the encoding。Of a vector X。 So think of x as the vector of length 4， x 1， x 2， x 3。

 x 4。This is equal to the following matrix vector product。So in this vector here。

 this is just going to be x， x1， x2。X3， x4。And this matrix is going to capture these linear relationships。

So the first four bits are just x1， x2， x3， x4。The fifth bit is x2 plus x3 plus x4。

 the sixth bit is x1 plus x3 plus x4， and the seventh bit is x1 plus x2 plus x4。

And everywhere I haven't drawn a one， there should be a zero。And of course， all of this is modD too。

So if we label this matrix G， then the encoding of the vector X is just G times that vector x mod 2。

The matrix G here is called a generator matrix。We'll see a formal definition in a future video。

But informally， a generator matrix is just a matrix so that you can think of the encoding map as multiplication by that matrix。

Now that we have this matrix vector way of looking at this encoding map。

 let's make a few linear algebraic observations。To make these observations， I'm going to assume。

That linear algebra works mod2。We'll see what this means in a moment。

But assuming that linear algebra works kind of as we expect。

 even though we're doing everything mod too。Here are some observations that we can make based on this characterization that we just had。

The first observation is that the code C。Is closed under addition。What that means is that。

 for any code words。See and see prime in my code， C。C plus C prime is also in my code C。

And to see this。We can write C plus C prime。Well， by the definition of the encoding map as multiplication by some matrix G。

 this is G times X plus G times x prime for some vectors X and x prime。And because this is linear。

 this is G times X plus x prime。And by definition， anything of this form is in C。

 So this is in the code C。And here what I'm writing， plus， I mean， plus mod 2。A related observation。

Is it C。Is a linear subspace。Of01 to the7。Of dimension 4。

So you might remember from linear algebra class that a linear subspace is defined to be anything that is closed under linear combinations。

 Yet that is addition and scalar multiplication。We just said that this thing was closed under addition。

Scalar multiplication mod 2 just means multiplication by one。 So， of course， it's closed under that。

 So this is a linear subspace， assuming that that notion makes sense， Mo 2。More precisely。

 C is the subspace， which is the column span。Of the matrix G。

And we can see that it has dimension 4 by looking at this matrix G。

So I've just copied and pasted G over here。And we can see that the column span should have dimension 4 because these columns are all linearly independent to see that they're linearly independent。

 observe that there's little identity matrix just sitting right there。Okay。

 so C is a linear subsspace of dimension 4。These facts also imply the extremely useful fact。

That the distance of C。Remember， that's defined as the minimum hamming distance between any pair of distinct code words in C。

This distance is the same。As the minimum weight。Of any nonze vector in C。

And remember that we defined the weight of a vector as just the number of non zero entries。

To see why this statement is true。Let's observe that the distance between any two code words。

 C and C prime。Well， this is the same as the distance between G times x and G times x prime。

For some appropriate ex and X prime。And this is the same as the distance between G X minus G X prime and 0。

That is， it's just the weight of Gx minus Gx prime。But， again， by linearity。

This is the distance between G of x minus x prime。And0。

And this is the weight of G times x minus x prime。But G times x minus x prime itself is a code word in C。

So that means if there's any pair of code words which have some distance。

 there is some other code word that has。As its weight， that distance。 So therefore。

 the minimum distance is the same as the minimum weight of any non0 codeward。Okay。

 so let's just make a note of those linear algebraic observations。 we'll come back to them later。

And let's go back to this slide。Let's see yet another way to write the haming code。

Let's recall this circle definition of the code。We observed in a previous video。

That each one of these circles constituted some sort of parity check。

That is the sum of the bits in each circle has to be zero mod2。Once again。

 that's sort of a linear relationship mod too。 so we can write it as a matrix vector product。

 In this case， it would look something like this。So here I've written our potential code word there。

And I'm going to fill in this 3 by 7 matrix so that each of the three rows corresponds to the constraints given by each of these three circles。

Let's start with the blue circles constraint。The blue circles constraint says that x 2 plus x 3 plus x 4 plus C 5。

Better some to0 mod，2。So let's put a one in the second， third， fourth and fifth place。

And say that that better be equal to 0， mod2。Next， let's look at the yellow circle。

That's this one here。This says that x 1 plus x 3 plus x 4 plus x 6 better be equal to 0， mod 2，1，3，4。

6。Better be equal to 0，1，2。And lastly， let's look at the red circle。This one here。

 this says that x1 plus x2 plus x 4 plus c7。Should be 0 mod，2。1，2。4，7 is going to be equal to 0，12。

And again， where I haven't written a one in this matrix， I mean， for there to be a 0。Okay。

 let's call this matrix H。So what we've just seen is that any code word C in C satisfies the equation H times C is equal to 0。

Another way to say that。Is that C is contained in the kernel of this matrix H Mauud 2。

Let me add mod2 up here。And in fact， I claim that actually C is equal to the kernel of H。

We can see this again， assuming that linear algebra works by counting dimensions。

That is the dimension of the kernel of H。Is equal to 7-3。

That's because the dimension of the kernel of this matrix is equal to 7 minus the rank of the matrix。

And I claim that this matrix has rank 3。And that's because all of the rows are linearly independent。

 Again， you can see this because there's a little identity matrix sitting right there。

So that means that the dimension of the kernel of this matrix is 7-3， also known as 4。

On the other hand。The dimension of the code， C。We saw in the previous slide was also equal to 4。

So now I have that C is contained in the kernel of H， but they both have the same dimension。

 so they better be equal。So let's erase this containment and write equals。

 C is equal to the kernel of H。A matrix H like this is called the parity check matrix for a code。

Again， I'll define parity check matrix formally in a later video， but informally。

 a parity check matrix is just a matrix so that the code is equal to the kernel of that matrix。

It turns out that this parity check matrix view that is viewing C as the kernel of some matrix can be really useful。

Let's do a couple of examples。The first example is that using this view of C we'll be able to see really easily that this code C has distance 3。

This is something we asserted in an earlier video， and perhaps you stared at those circles for a little while and convinced herself that it was true。



![](img/cc9891f1bf6da18f855868d7b7d28000_1.png)

But now we can prove it formally， pretty easily。First。



![](img/cc9891f1bf6da18f855868d7b7d28000_3.png)

We saw from our linear algebraic observations earlier。That it suffices to show。



![](img/cc9891f1bf6da18f855868d7b7d28000_5.png)

That the minimum weight of c is3。That is that there is no code word in C with weight less than three。

To see that this is true， supposed towards a contradiction。That there's some code word， C and C。

It has weight 1 or2。Then the picture with this parodity check matrix looks like this。That is。

 there is some Colel vector C， which has weight 1 or 2。Of H。

 So when I multiply H times this vector C， I'm going to get the all zeros vector。

But that means that there is some non zero linear combination of one or two of these columns。

It's equal to 0。

![](img/cc9891f1bf6da18f855868d7b7d28000_7.png)

And since any pair of the columns of H are linearly independent。That means that this can't happen。

So when I say that any pair of columns are linearly independent。

 that means first that no column is 0。 That's certainly true。

 And also that I can't take any pair of these columns。

 say this one or this one and take some non trivial linear combination against 0。Mod 2。

 that can only happen if two columns are the same， and they're not。Great。So， that implies that。

For all sea。In my code C， the weight of C。Is at least three。

And this implies that the distance of C of the code C。Is also at least three。

To see that the distance is at most 3。Just consider the code word。0，1，0，1，0，1，0。

And observe that this has weight three。So， that means。The distance of the code C。

Is less than or equal to three as well。And combining these two things。

 we see that C has distance exactly three。Okay， so that's one benefit of this parity check matrix view of a code C。

At least for this code， we can read off the distance pretty easily。

Here's another example of a benefit。This actually gives us a really slick decoding algorithm。



![](img/cc9891f1bf6da18f855868d7b7d28000_9.png)

Let's recall this puzzle that we had in an earlier video。



![](img/cc9891f1bf6da18f855868d7b7d28000_11.png)

So I told you that C Twiddle was equal to the corrupted code word 0，111，0，1，0。



![](img/cc9891f1bf6da18f855868d7b7d28000_13.png)

![](img/cc9891f1bf6da18f855868d7b7d28000_14.png)

And I asked you to decode this。 So I asked you to find some C in my code C。

 such that the haming distance between C and C twittle。



![](img/cc9891f1bf6da18f855868d7b7d28000_16.png)

![](img/cc9891f1bf6da18f855868d7b7d28000_17.png)

Is at most one。And you did this either by staring or we saw sort of how to do it by looking at those circles。

 but here's one way to do it， looking at this parity check matrix。So on the one hand。



![](img/cc9891f1bf6da18f855868d7b7d28000_19.png)

We can compute H times C twiddle。

![](img/cc9891f1bf6da18f855868d7b7d28000_21.png)

Here， I've just copied and pasted H over。 And here's C Twiddle。

We can compute this and it turns out to be 110。On the other hand。

Let's consider what H times C Twiddle actually is。So we have C twiddle is equal to C plus Z。

 where C is our original code word。And Z is the error that got added。Here， whenever I write， plus。

 I mean plus mod 2。So， Z here is some。Weight one error vector。And this is all mod too。

But that means that。H times C twiddle。Is equal to H times C plus Z。

Is equal to H times C plus H times z。And that's just equal to H times Z。Again， Mau， too。

And the reason is that， age times C。0。

![](img/cc9891f1bf6da18f855868d7b7d28000_23.png)

Because C is in my code， and my code is the kernel of H。So together。

 this tells me that H times Z is equal to H times C twiddle， which we just computed was equal to 1，1。

0。Mou。But if Z has weight 1， what does it mean for H times Z to be equal to something， Basically。

 that means that Z is just picking out one of the columns of H。 And that's what it comes out。

So if we look at which column of H this happens to be。 Well， it's this one， the third one。

So this implies that Z has to be the vector。0，0，1，0，0，0，0， which implies that our correct code word。

 C is equal to C twiddle plus Z。Which is equal to C Twil， except we flip the third bit。Again， here。

 plus means plus minus2。And so that's going to be 0，1，0，1，0，1，0。

Which is exactly the same thing we got before。So this gives us a really quick decoding algorithm for C。

 We just compute H times C twiddle。And that we see what column of H is that。Okay。

 so what's the moral of the story？

![](img/cc9891f1bf6da18f855868d7b7d28000_25.png)

First。😡，We saw that the hamming code， C。

![](img/cc9891f1bf6da18f855868d7b7d28000_27.png)

Of length 7。Is a linear subspace。

![](img/cc9891f1bf6da18f855868d7b7d28000_29.png)

Of 0，1 to the 7。And that meant that we could look at C in two different ways。



![](img/cc9891f1bf6da18f855868d7b7d28000_31.png)

First， we could write C。As the set G times x。

![](img/cc9891f1bf6da18f855868d7b7d28000_33.png)

For x in0，1。To the for。Again， all the arithmetic mod， too。Which is the column span。



![](img/cc9891f1bf6da18f855868d7b7d28000_35.png)

Of G。For some matrix G， which we call a generator matrix。We saw that。 We could write， C。



![](img/cc9891f1bf6da18f855868d7b7d28000_37.png)

As the set of vectors C。In 0，1 to the 7。Such that H times c is equal to 0， again， mod 2。

Which is the kernelel of H Mu2。For some appropriate matrix， that we called a parodity check matrix。

And finally， we saw that this linear algebraic view was super useful。



![](img/cc9891f1bf6da18f855868d7b7d28000_39.png)

In particular， it gave us an easy way to compute the distance of C。

And also gave us an easy way to decode a corrupted code word from one error。However。

 all of this was sort of predicated on the assumption that quote linear algebra works over 0，1 mod2。

For example， when we said that C was the kernel of H。Moud 2。

 we relied on this dimension counting argument， which is implicitly relying on fact that dimension makes any sort of sense。

 Mod 2。Before you move on to the next video。It might be a good idea to stop and first check where we used the fact that linear algebra quote unquote works。

 and also to reflect on whether or not it does work。

