# 【全集】加州理工学院 C语言系统编程 中英字幕 p12 Lecture 12 - 浮点数 part1 -BV1bUzWBLEiC_p12-

![](img/b5d8c9bff1848023efc4ce9de006a74a_0.png)

Okay， perfect， so the last thing that we need to do in chapter two then just to finish up chapter two so we can move on to more interesting chapters。

 move a little bit away from the theory that drives how we actually store our data in terms of a representational form into our systems and we can start moving more into the actual like machine code on how our systems operate is to handle the。



![](img/b5d8c9bff1848023efc4ce9de006a74a_2.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_3.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_4.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_5.png)

Alternate numerical format that we haven't discussed yet。

 so we spent a lot of time and effort talking about integral data data sets。All right。



![](img/b5d8c9bff1848023efc4ce9de006a74a_7.png)

Just talking about integral data sets right those are the accountable values where there is a discrete step between one unit to the next right so like for instance。

 in our integer space， we move from zero， one two， three， four， five six。

 very powerful arithmetic operations can be dealt with that。

 but one of the things that we lose with that type of those type of number sets。



![](img/b5d8c9bff1848023efc4ce9de006a74a_9.png)

Is that you can't define the amount of space between two values in the set。

 right like one of the big awesome concepts that's given to us in terms of real numbers is that we can have definable sets of values that occur in between infinitesimally between。



![](img/b5d8c9bff1848023efc4ce9de006a74a_11.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_12.png)

And so that's this true value that floating points give to us now I've said this before and i'll restate this again mathematically anything that's represented as a radix point as a fractional number as a floating point number is always an approximation。

This is just it's ingrained mathematically， it's inherent to that representation。

 that's why when you go through discrete mathematics and correct me if I'm wrong。

 you usually have to do the proof that 0。9999 repeating is equivalent to one。

Did everyone kind of accept through that proof？And so the reason why that proof is a valuable isn't just to show you like mathematical trickery。

 right it's to illustrate that。😡，In order for us to map our ra points numbers onto the integer set。

 that has to be a necessary group。O。

![](img/b5d8c9bff1848023efc4ce9de006a74a_14.png)

So with that said， let's see how we can take this idea of our floating point numbers and start encapsulating those。

 start encoding those as a binary sequence as well。



![](img/b5d8c9bff1848023efc4ce9de006a74a_16.png)

And so I'll also highlight。And this should be evident after the course of these slides。

 the reason why the default value of floating point numbers is the double and not float is because you always want the higher precision when you're talking about approximations so recall that integers are 32 bits in terms of its encoding space there are long integer you could use the long data type and get a 64 bit in。

 but typically you don't need a number of that size so the default is is is four bits4 bytes i'm sorry4 bytes。



![](img/b5d8c9bff1848023efc4ce9de006a74a_18.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_19.png)

Whereas with floating point numbers， you you know however。

 whatever the maximum encoding amount of bits you have so in this in this historically it was your your doubles your eight bytes that was always going to perform better is going to be more accurate than your four bytes and we're going to see why that's the case and why that's important and why if you ever need to use a fractional。



![](img/b5d8c9bff1848023efc4ce9de006a74a_21.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_22.png)

If you ever need to use a floating point number， you should always use doubles and offloads。

Another thing is if you can ever model something in terms of integer values， you should never。

 if possible， use floating point value。I think we've probably talked about that already as well。

 right， and we used the movie the office space as an example。Okay， anyway。

 let's get back to the actual box here you can see I I give you the floating point representation。

 which isn't going to encode in the form of this。 So here our。Our value of V。

 which is going to represent our floating point number。Can be defined as this term X。

 which is going to be our significant hand。Or what's called Ar menisa。

 which is the part that holds the precision or magnitude of the number。

 and then here we're going to take two to the power of y and y is going to be the exponent which scales the number by powers of two and determines its magnitude。



![](img/b5d8c9bff1848023efc4ce9de006a74a_24.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_25.png)

So we effectively we have a base and we're going to multiply that by a exponent on two we're going to see how that actually translates。

 but this is typically mathematically how we're going to model all of our floating point numbers。



![](img/b5d8c9bff1848023efc4ce9de006a74a_27.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_28.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_29.png)

Yeah。So one of the powerful things about our floating point numbers is they're very good for large numbers and they're very good for small numbers。

 so numbers that are close to zero。

![](img/b5d8c9bff1848023efc4ce9de006a74a_31.png)

And they're an approximation as well， so they approximate to real arithmetic。

So the we talked about the encoding scheme we use for our integral numbers right we had twos complement form and we had。

The unsigned form， the just traditional way of doing counting and binary。

 the scheme by which we encode our floating point numbers was defined by the IA。

 so this is going to be the iAE representation that we'll go ahead and take a look at。



![](img/b5d8c9bff1848023efc4ce9de006a74a_33.png)

And so one of the big things it's going to explore is the rounding issues which。

Can affect our representation。So we'll cover that a little bit more in detail on these slides and again the mathematical properties are going to be addition multiplication and relational operators。



![](img/b5d8c9bff1848023efc4ce9de006a74a_35.png)

Okay let's take a quick look at what a fractional binary number looks like in practice so here we have a radix point when used on a binary number that would be called a binary point not a decimal point decimal point implies that it's a decimal number so if you were doing a fractional number and a hexademal value that be your hexademal point if you want the generic term for that acceleration。



![](img/b5d8c9bff1848023efc4ce9de006a74a_37.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_38.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_39.png)

So don't by default， call it a decimal point， it's only accurate when you're talking about base 10 numbers。



![](img/b5d8c9bff1848023efc4ce9de006a74a_41.png)

Okay， so we have our binary point， so suppose we have placed it here right so just like with base 10 math it will be similar in base two math。

 you have a left hand side of your binary point and you have a right hand side of the binary point。

So the left hand side will represent where you have。



![](img/b5d8c9bff1848023efc4ce9de006a74a_43.png)

Magnitudes that are in front of your fractional that that adds to your your magnitude so like for instance。

 this would be so if we were to eliminate the righthand side our B0 here would be the equivalent of one if that was in the one space right this would be like24 so2 to the power of zero2 to the power of one2 to the power of two2 to the power of three all the way to whatever value you're encoding this right so the left hand side works the exact same way we've already learned how to go ahead and do our binary count and it works。



![](img/b5d8c9bff1848023efc4ce9de006a74a_45.png)

As an analog to the way we do it in Desal math as well， so that means。

That the right hand side should also work as an analog to the way we would do this in decal based math right but as opposed to being 110th 100th 100th place is it would be the equivalent of like two to the minus one place so like one half or one4th or 18 or 116th or 132 right so based off of where those units appear are going to depend on what the exponential two is so does that much make sense that I mean so far that's an analog and correct me if I do you already cover it in this much detail in assembly or is this effectively all new data I don't know how far we all go into the I E representation kind of over right now we're learning it。



![](img/b5d8c9bff1848023efc4ce9de006a74a_47.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_48.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_49.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_50.png)

Yeah， okay， oh， perfect， so you're actually learning it and。Okay， well， that's。

Good to have a little over。Okay， so one way that we can go ahead and then represent。



![](img/b5d8c9bff1848023efc4ce9de006a74a_52.png)

Is that our bits to the right right represent the fractional powers of a rational number。



![](img/b5d8c9bff1848023efc4ce9de006a74a_54.png)

And so here we can see we can take the sigma summation on the right to be able to actually compute from。

Oh， let's see here。 This is J。I mean， this is B to the minus J。

 right we can sum from there all the way until we get to our I term。

And then here we can take whatever the binary value is at any given time and multiply it by two to the power of k。



![](img/b5d8c9bff1848023efc4ce9de006a74a_56.png)

So does everyone see how this sigma summation term， this mathematical term matches to。



![](img/b5d8c9bff1848023efc4ce9de006a74a_58.png)

This representation is visual representation。Because if so。

 I want to go back towards our linear algebra。

![](img/b5d8c9bff1848023efc4ce9de006a74a_60.png)

Definition here and say this states the same thing it's just instead of sigma summation where we're showing the per element operation right using the sigma summation operation。

 this is a vector times a vector to produce another vector， this is the vectorized operation。



![](img/b5d8c9bff1848023efc4ce9de006a74a_62.png)

Which。Side note。It will seriously behoove you to get well acquainted with vector representations and vector operations so much of modern computer science is driven by linear algebra and we're talking about in a number of different ways graphics。

 anything that's graphically represented is usually done in the form of matrices。

 but so much about what's happening in machine learning and data science is also something that happens with a lot of matrices in fact。

 if you ever wondered what the term a tensor was from tensorflow。

 it relates to linear algebra and tensors are effectively abstract matrices that you do operations on。



![](img/b5d8c9bff1848023efc4ce9de006a74a_64.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_65.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_66.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_67.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_68.png)

So the very name pulls from linearar algebra， you have credits you need to take and map。

Use that for linear algebra， by far one of the most important maths you can have if you are serious about pursuing a software engineering position in fields that are very relevant in today's environment。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_70.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_71.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_72.png)

Okay， let's take a look a example and actually map this to an example in terms of how we might represent our fractional binary number。



![](img/b5d8c9bff1848023efc4ce9de006a74a_74.png)

As a bit sequence。 so here again we've added some notation here Now we have a binary point。

 We have the left hand side and the right hand side of our binary points here and this subtu lets us now know what the base is。

 So this is a base two value If I want to represent that in the form that maps to the sigma summation。

 I can take each of the positions inside of my bit factor and express them as so。



![](img/b5d8c9bff1848023efc4ce9de006a74a_76.png)

So here I can take this most significant value of one and so that so here would be my one's place。

 my two's place， my fourth place so that's two to the power of two。

 so I would take one times two to the power of two。

 then I would add that to the next term in my sequence which is going to be zero times two to the power of one。

 then I would add that to the next term of the sequence， it's going to be here。

 my least significant bit in front of my binary point and left of my binary point and that's going to be one times two to the power of zero。



![](img/b5d8c9bff1848023efc4ce9de006a74a_78.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_79.png)

Now I'm still going to do my sigma sum， but now I'm going to cross over into a negative exponent value。

 one of the beautiful things about having negative exponents is that they represent now the equivalent of having or quartering or whatever right so it gives us that decimal place that's on the right。



![](img/b5d8c9bff1848023efc4ce9de006a74a_81.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_82.png)

Or binary point in this case to the right。So here I'll go ahead and then take I have a one value here so we'll multiply that by two to the power of minus1 and then finally we'll do the same thing for that next position so if I want to then show you the actual evaluation that's the same after we apply the multipllic of property to these exponents would be four plus0 plus one plus one half plus one quarter so when we add that up that is the binary representation of five and three quarters。



![](img/b5d8c9bff1848023efc4ce9de006a74a_84.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_85.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_86.png)

Very simple example， but we've just done something very prolific we just illustrated how we can take an arbitrary。



![](img/b5d8c9bff1848023efc4ce9de006a74a_88.png)

Fraracxictional value and map it。Into a bid vector。

And so this is what's going to allow us to start mapping our floating point value so this concept here。

 so you can see this is an extension of the way we would normally do almost our integer based。



![](img/b5d8c9bff1848023efc4ce9de006a74a_90.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_91.png)

Counting， but it allows us now to start doing our summations where we actually have a inflection points on our rate point value。



![](img/b5d8c9bff1848023efc4ce9de006a74a_93.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_94.png)

Okay， so shifting the binary point， one position to the left has the effect of dividing the number by two。



![](img/b5d8c9bff1848023efc4ce9de006a74a_96.png)

So that's again， let me map an analog to the maths you've had in decimal representation。

 just like shifting a point to the left or the right is the equivalent of increasing something by a magnitude of 10 either way right so you make。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_98.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_99.png)

one go to one10 or you make one go to 10 just by shifting that point。

 so similar concept on how we shift those points and the effect it has on the binary representation。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_101.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_102.png)

Which again is why we use this multipcar property of two to the power of k in our representation。

 so again， if we just want to look at this and prove this conceptually， let's look at this example。

 we saw that on 101。11 that translated into five and three quarters。



![](img/b5d8c9bff1848023efc4ce9de006a74a_104.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_105.png)

If I were to simply shift。出理啊 to理啊。My my binary point by one。

 we can see it's going to have the effect of having that and actually we can actually test that by seeing how that binary sequence changes on a per bit level。

 so that look it would be the equivalent of having a two plus zero plus quarter。

 I mean plus half plus quarter plus eighth， which if we sum that together would be the equivalent of two and seven eighths。

 which is half of our five and three quarters。

![](img/b5d8c9bff1848023efc4ce9de006a74a_107.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_108.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_109.png)

And again shifting the binary point one position to the right has the effect of multiplying the number by two again an analog we should already be familiar with and again we can see if we actually do the math。

 visually inspect it， this holds true in the example we've already illustrated so in this instance we started with five and three quarters we shift our point by one we then retranslate it into the set of integers that we can sum to evaluate what its representation is and we see eight plus two plus one plus half is 11 and one half。



![](img/b5d8c9bff1848023efc4ce9de006a74a_111.png)

And so here is just a table and this table is given to us in the book as well that just shows our binary representation and then what our value would be in terms of a。

In terms of how we might want to think of it， zero over two， one over four， two over eight。

 just notice your denominator here is based off of the maximum number of combinations you can create that's on the right side of your binary point。



![](img/b5d8c9bff1848023efc4ce9de006a74a_113.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_114.png)

And then the numerator， it is the sum of values that make that up。

 so this is just a quick representation of what the fractional。

 what the ratios are between it right one integer denominator over a numerator and then we can also show the decimal representation of that as well。

So depending so again， you already know how to map these concepts， this is normal math， you know。

 you could parse these the same way you would， this is all in base 10。Yes。



![](img/b5d8c9bff1848023efc4ce9de006a74a_116.png)

But just highlights how we can translate between our rate explain value and then our。



![](img/b5d8c9bff1848023efc4ce9de006a74a_118.png)

fractional values here。But of course， the important concept is you can see how they can start。



![](img/b5d8c9bff1848023efc4ce9de006a74a_120.png)

Representing a lot of different decal values or fractional values that are to the right of our binary。



![](img/b5d8c9bff1848023efc4ce9de006a74a_122.png)

And so as I already said it fractional values are inherently approximations。

 so their law seat they're inex that's true in decimal notation that's true in binary notation。

 some examples that I actually like to give to illustrate that this is a deficiency not just in our binary representation。

 but our decimal representation is that we don't actually like have a value。



![](img/b5d8c9bff1848023efc4ce9de006a74a_124.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_125.png)

That means one third in decimal， right we have to just。Represented as 0。

3333 and at some point we just say， yes， it's just that many points like indefinitely。Now。

 interesting enough。If we use the base 12 system， we could represent 0。

3 as something that is not approximation， so actually the choice of your basis actually determines whether a value can be represented。



![](img/b5d8c9bff1848023efc4ce9de006a74a_127.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_128.png)

As a floating point value or not， so there are some values that we can represent。

As a kind of discreteet， countable set of digits。For a fractional value in one base and not in another。

 this is an important concept to know， because this is why。

You might have a value that you can represent in decimal notation。

 but then when you save it and look it up， it becomes a different value。



![](img/b5d8c9bff1848023efc4ce9de006a74a_130.png)

After you do an operation on it， because it might translate into the binary equivalent。

 which doesn't have a actual defined representation and then it becomes an approximation。

 or there already approximation， but then it gets lossy and loses some data and then it gets remapped into a new interpretation。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_132.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_133.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_134.png)

So for instance， in this example， clearly one third。

 five7 is another one that doesn't quite work well in base 10。



![](img/b5d8c9bff1848023efc4ce9de006a74a_136.png)

Whereas in binary， we can only represent numbers that can be written in the form of right x times 2 to the power of y。



![](img/b5d8c9bff1848023efc4ce9de006a74a_138.png)

Any other values are going to end up being approximated。



![](img/b5d8c9bff1848023efc4ce9de006a74a_140.png)

So and then further examples， like one fifth can be represented exactly as a fractional decimal of 0。

2， however， as a fractional binary number， we cannot represent it equally and instead that has to be approximate。



![](img/b5d8c9bff1848023efc4ce9de006a74a_142.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_143.png)

Yeah， just a motivating concept that things that we think are well defined because we're in base 10。

 we lose。

![](img/b5d8c9bff1848023efc4ce9de006a74a_145.png)

That interpretation of when it actually gets translated into a binary representation and then translate it back into a decal representation。



![](img/b5d8c9bff1848023efc4ce9de006a74a_147.png)

Because remember， that's always happening。And that。

Also why we never do equality on floating point values。



![](img/b5d8c9bff1848023efc4ce9de006a74a_149.png)

Okay， so let's talk about why IAE floating point representation is the standard that's used even today in terms of representing our fractional values。

 our floating point values， so the positional notation that's in the previous approach is not efficient for representing very large numbers。



![](img/b5d8c9bff1848023efc4ce9de006a74a_151.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_152.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_153.png)

For example， the representation of， and then here we have five to two to the power of 100。



![](img/b5d8c9bff1848023efc4ce9de006a74a_155.png)

Would consist of bid patterns that would be 101 followed by 100 zeros。Right。

 so what we saw previously is a good way of learning about。



![](img/b5d8c9bff1848023efc4ce9de006a74a_157.png)

How floating point values can be represented， but there's a better way to encode them that compresses the number of bits we need for representation。



![](img/b5d8c9bff1848023efc4ce9de006a74a_159.png)

That's really going to be the huge affordance that our I tripleE floating point representation is going to give us so this efficiency becomes more pronounced when dealing with either。



![](img/b5d8c9bff1848023efc4ce9de006a74a_161.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_162.png)

Extremely large numbers， but also extremely small numbers right， so think about it this way。



![](img/b5d8c9bff1848023efc4ce9de006a74a_164.png)

If we want to grow a number to be very large， we're putting the bit pattern to the left of the binary point。

 but if we want to grow a value to be very to be very infinitesal，😡。

Then we got to grow the binary sequence very far down the right binary point， right？😡。



![](img/b5d8c9bff1848023efc4ce9de006a74a_166.png)

And so if you're looking for precision inside of your binary representation for your fractional value。

 you want as many bits to either the right or the left。

 depending on whether you want a very big value or whether you want a very little value。

 but a very little value that's very precise in terms of how close it is to an you。

 an infiniteimal unit。😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_168.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_169.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_170.png)

Then the current approach we looked at doesn't scale well。Right。



![](img/b5d8c9bff1848023efc4ce9de006a74a_172.png)

So the solution here to address this limitation is to introduce this floating point format。



![](img/b5d8c9bff1848023efc4ce9de006a74a_174.png)

Which will allow us to get these very large or close to zero values and what we're going to see by this。



![](img/b5d8c9bff1848023efc4ce9de006a74a_176.png)

There's some interesting consequences with this standard where we'll actually see a visualization of how this works。



![](img/b5d8c9bff1848023efc4ce9de006a74a_178.png)

So this format is going to save us memory though， and at the end。

 it offers obviously a broader range of values。

![](img/b5d8c9bff1848023efc4ce9de006a74a_180.png)

And so also it's important because this is the standard method for encoding real numbers as a combination of a sign bit an exponent field and a fractional field。

 so these are going to be the three pieces of data we're going to use to be able to encode。



![](img/b5d8c9bff1848023efc4ce9de006a74a_182.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_183.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_184.png)

Our values。So。Now we're going to redefine。How we're going to represent our floating point values based off of this new。

ITle function。So notice here we're going to have negative one to the power of s and so S is going to be the sine s to determine whether the number is negative S is one or positive which is zero so this is where the interpretation of the sine bit and numeric value is zero handled by our special case so now this allows us to have negative。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_186.png)

Real values or positive right in the way we just saw we didnt with the prior definition。

 we were using unsigned values。Then we're going to have our significant。

Which can also be called yourmentza， which is going to be our M value。

 that's going to be our fractional binary value that can have a range between one to two。



![](img/b5d8c9bff1848023efc4ce9de006a74a_188.png)

And then we're going to multiply that by two to the power of our exponent。

 which is going to be the value of a power of two。And so notice most of our binary sequencing then goes will allow us to be able to really translate into this domain here。

So let's take a better look at what that actually represents so in a numerical form。

 given the I tripleE floating point form here。

![](img/b5d8c9bff1848023efc4ce9de006a74a_190.png)

We can see that our most significant bit then here is going to be our sign bit。

 so that is an analog to how we determine the sign bit on interval data。



![](img/b5d8c9bff1848023efc4ce9de006a74a_192.png)

Then here。Typically well have our exponentage field， which is going to encode our E， right？

And then here we're going to have our fractional field， which is going to encode our M。

 which is going to be this unit here。

![](img/b5d8c9bff1848023efc4ce9de006a74a_194.png)

And so typically。In single precision， which is 32 bits and in double precision。

 which is 64 bits based off of the ratio of bits dedicated to your sign bit。

Your exponent and your fractional。Sequences。Is going to be。

 let's see you have one bit dedicated to your sign bit。

 you have eight bits dedicated to your exponent， and you'd have 23 bits dedicated to your effectively your fractional bound。



![](img/b5d8c9bff1848023efc4ce9de006a74a_196.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_197.png)

Whereas if we go to double。Were able to increase the fractional encoding space from 23 bits to 52 bits that makes such a huge difference。



![](img/b5d8c9bff1848023efc4ce9de006a74a_199.png)

Let's see if we have。Some examples here， so here are three cases of our IAA floating point binary values。



![](img/b5d8c9bff1848023efc4ce9de006a74a_201.png)

Where we can either have our normalized values， we have our deormalized values。



![](img/b5d8c9bff1848023efc4ce9de006a74a_203.png)

And then we have our special values， which would either represent infinity or NA。



![](img/b5d8c9bff1848023efc4ce9de006a74a_205.png)

So let's start and so here we can see what determines whether something is considered a normalized value。

 a denormalized value， or one of these special case values is going to depend on how in the blue。



![](img/b5d8c9bff1848023efc4ce9de006a74a_207.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_208.png)

RightWhere our exponent field。😡，What values they hold so notice if it's all ones and this is a binary sequence and that doesn't make any sense。

 that's not a valid representation。😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_210.png)

So in those instances。Our。System would translate that as either an affinity value or not a number bound。

So your exponent field here has to have。

![](img/b5d8c9bff1848023efc4ce9de006a74a_212.png)

A。Value at least it has to have at least a zero value somewhere in there right it can't be all one。



![](img/b5d8c9bff1848023efc4ce9de006a74a_214.png)

Okay， now with that said， we could see that a deormalized value is one where it's all zero。



![](img/b5d8c9bff1848023efc4ce9de006a74a_216.png)

And if it's anything in between。Between having at least one B as。A on bit as a one。

 and orre at least one bit that is a zero bit， that's going to be our normalized values。



![](img/b5d8c9bff1848023efc4ce9de006a74a_218.png)

So let' let's talk a little bit about what it means to be a normalized value or a denormalized value。

 I think it's pretty obvious what it means to be a Nn， a not a number or an afinity value。

So our normalized values represent the most common case。

So it occurs when the exponed field is neither all zeros or all wants。So in this instance。

The exponent field represents a signed integer。In biased form。😡。

Where E will represent our actual exponent of the floating point number。

 the little E here inside of our equation， e minus bias is going to be the unsigned integer value stored in the exponent field。

 and so this bias is going to be a constant value， it's 127 for a sine precision or 1023 for double precision。



![](img/b5d8c9bff1848023efc4ce9de006a74a_220.png)

And so that will either give us this range of between minus 126 to 127 and sign precision or minus 1022 to 1023 in double precision。

And then in our fractional field。We can represent a fractional value where our F here， to our term。



![](img/b5d8c9bff1848023efc4ce9de006a74a_222.png)

I have。I's add it in here。

![](img/b5d8c9bff1848023efc4ce9de006a74a_224.png)

But for a fractional value well want it to be anything obviously between zero and one right that's what we mean by fractional it' it's less than it's less than a whole number。

And just a little bit more explanational in terms of in terms of why we have a bias in there。

 the purpose of our bias term is to introduce。How to efficiently represent our exponents and create a balanced range of exponents。



![](img/b5d8c9bff1848023efc4ce9de006a74a_226.png)

We're going to see what the biasness does when we actually look at the number range of how our approximations work。



![](img/b5d8c9bff1848023efc4ce9de006a74a_228.png)

But it allows us this efficient exponent representation so the exponent field determines the magnitude of the number by specifying the power of two which is raised right so that's like our k term two to the power of k to efficiently represent both the small and large exponents with a fixed number of bits。



![](img/b5d8c9bff1848023efc4ce9de006a74a_230.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_231.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_232.png)

So when we talk about having a balanced range by introducing the bias。

 the exponent field can represent a range of values that include both positive and negative。

 that's where we have the s bit， but the bias also shifts the exponent value making it possible to express small negative exponents as well as large positive exponents。



![](img/b5d8c9bff1848023efc4ce9de006a74a_234.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_235.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_236.png)

So let's see， do I have a representation here？So I kind of want to show that。

So just as a case here so we can see what this looks like， suppose that we have。The following value。

You can see have our E term， we have our bias term。

 which is the constant value in a single precision of 127 and our exponent value。

 which is effectively just our E term plus our bias term。

And so then this term here would be encoded as this sequence here。And if we log。

 this sequence is in the red。Which is in our exponentish field。



![](img/b5d8c9bff1848023efc4ce9de006a74a_238.png)

And then in terms of our significant hand， right， that's going to be our blue term here。



![](img/b5d8c9bff1848023efc4ce9de006a74a_240.png)

We would have our M and so if we look at our formulas here。

 we have let's take a look at the formulas on the right hand side and the map it's the actual example here so we can actually。



![](img/b5d8c9bff1848023efc4ce9de006a74a_242.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_243.png)

Branands light what's happening step by step， so we have our vector our bit vector our bit vector that represents our fractional value can be defined as minus1 to the power of S。



![](img/b5d8c9bff1848023efc4ce9de006a74a_245.png)

Assses are signed bit。Times m， which is going to be our fractional value here times 2 to the power of E。

 which is going to be the exponent field fields here， right？So looking at this。

 I can know what' part of my binary sequence。😡，Goes to each。



![](img/b5d8c9bff1848023efc4ce9de006a74a_247.png)

Attribute to this formula。Okay， so another way I can define M then using this formula is it's the same way as saying just take this vector field。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_249.png)

And right shift it by E spaces。Bye。So if you see， I have this here。😡。

You can see I'm effectively going to right shift it。By 13 spaces。

Which is why I have so many zeros here， So does everyone see how I define my my fraction from my M。

So again， let's jump here， suppose I have this value。15213 right that's my。

That is going to be my decal representation。

![](img/b5d8c9bff1848023efc4ce9de006a74a_251.png)

I can take this decimal representation and convert into this binary sequence here。

I can take this binary sequence and represent that in my formula that I gave here。

 so the equivalent representation is to use my binary point， one point。

 and then I can then define all of these values and multiply it by two to the color of 13。😡。



![](img/b5d8c9bff1848023efc4ce9de006a74a_253.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_254.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_255.png)

Right does everyone say that this formula right here that I have。

 this topmost formula is a way of reexpressing this binary sequence to the equivalent to this formula now？

😡，Okay， once I have that understanding， I can then define what my M term is。

 my M terms is going to be this part here。😡，The part that is now。To the left。Of my binary point。

So again， what we've done here for this representation is take a very big number。😡。

And we can express it。As being a part of was mapping to the right hand side of my binary point？

But I can multiply it by two to a power of something that's bigger。

 like two to the power of 13 right and that makes sense， right？😡。



![](img/b5d8c9bff1848023efc4ce9de006a74a_257.png)

Analoggue just to make sure everyone's on the same page because lots of blank faces if I take。



![](img/b5d8c9bff1848023efc4ce9de006a74a_259.png)

Zero。If I take one。01。And multiply it by。T0 to the power of 100。

 that's going to produce a really big term， right？

![](img/b5d8c9bff1848023efc4ce9de006a74a_261.png)

And so or I could take 1。23456 times 10 to the power of 10 it's still going to create a big term that's the concept we're doing this is effectively using scientific notation to encapsulate very big values or potentially very small values depending on whether the sign bit on my exponent is positive or negative。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_263.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_264.png)

So I take the unsigned。Value the9 fractional value I translated into this form。 and so now I can say。

 okay， I can reproduce that by multiplying it by two to the power of 13。 So if I do that then。



![](img/b5d8c9bff1848023efc4ce9de006a74a_266.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_267.png)

I can then fill this space here， so this my fractional is then going to be the value that we have here。

😡，And if we count the number of zeros， it's going to be two to the power 13。

 that's the actual realization of that。So here you can see my E term is 13， my bias is 127。

 I get 140 and that's going to give me my exponent term here so that I can encode that。

And so my IAAE representation of 15，213 would then be this binary sequence。😡，Does that make sense？



![](img/b5d8c9bff1848023efc4ce9de006a74a_269.png)

Maybe not super obvious initially， but you can see how much more powerful this is using a form of scientific notation to be able to now really represent very small or very large numbers。

 but also it's an approximation like it is。😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_271.png)

What's the purpose of the bias， why can't just like store a 3 red box？

That's a good question that is a very good question I have a visualization that's going to illustrate what that bias does for us and that bias is actually different depending on whether this is single precision or double precision。

 recall single precision it's 127， what we're going to notice in double precision it's what is it it's 1022 to 1023。



![](img/b5d8c9bff1848023efc4ce9de006a74a_273.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_274.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_275.png)

Yeah， it it's going to， yes， it's going to introduce a biasness that's going to allow us to have approximations in places that we're going to want those approximations to occur。



![](img/b5d8c9bff1848023efc4ce9de006a74a_277.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_278.png)

Well， let me see if I have a graphic that makes this a little bit more expressive。

Let me answer that question when I get to it I have a slide to answer that so just so that we can kind of stay on target with what our cases are。

 let me just kind of roll immediately into my deormalized values。

So deormalized values are these instances where my exponent value here is all zeros。

And so my exponent value here deormal is bla bla， bla。

 this case occurs when the exponent fields is all zeros， the exponent value can be defined as。

One minus bias。😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_280.png)

Because remember what our bias term was was 127， so if we do one minus our 127。

 that should zero everything out。

![](img/b5d8c9bff1848023efc4ce9de006a74a_282.png)

And so the significant value then is just going to be m is equal to whatever our F term is。

And remember， our F term is anything between zero to1。



![](img/b5d8c9bff1848023efc4ce9de006a74a_284.png)

So again， the purpose of our deormalized values is it's a way to represent our numeric value of zero。



![](img/b5d8c9bff1848023efc4ce9de006a74a_286.png)

In a normalized number， M must always be greater than or equal to one。

 make it impossible to represent zero， so the bit pattern for zero in our iAAE floating point format consists of all zeros。

 our sign bit as zero and all zeros in the exponent field， that should be obvious but。



![](img/b5d8c9bff1848023efc4ce9de006a74a_288.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_289.png)

It should be also articulated。A weird oddity here is when the sign bit is one。

 but all other fields are all zeros， we do have a representation of minus zero。

Consequence for this representation。Okay， so denoralized values also represent values that are very close to zero right this is approximations so they offer gradual underflow ensuring that the numeric values are evenly spished near zero。

What does that mean？

![](img/b5d8c9bff1848023efc4ce9de006a74a_291.png)

Okay。Remember， the real important thing about floating point numbers is creating definitions for very small units of space between elements。

 that means to we want to be able to represent a number that gets very close to a approach zero but isn't quite zero。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_293.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_294.png)

And then our special values， I think this is kind of obvious special values is when our exponent values all ones。

 then this can be things like undefined numbers， such as if you try to get infinitive。

 like if we take one and divide it by zero， that's going to produce an exponent field that's going to be all one。



![](img/b5d8c9bff1848023efc4ce9de006a74a_296.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_297.png)

So we have our two different values here where we actually show what we can do to go ahead and generate those Okay so this is。



![](img/b5d8c9bff1848023efc4ce9de006a74a_299.png)

Let's start kind of introducing some of these concepts of visualizations so really if we want to think about how we want to think of our normalized versus our deormalized values。



![](img/b5d8c9bff1848023efc4ce9de006a74a_301.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_302.png)

We have our center point here at zero。😡，And we can have positive zero and negative zero， whatever。

It just lets us know what direction we're approaching from zero right so think of it almost as limits in calculus。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_304.png)

So those numbers that are approaching zero that are going to be very close to zero are going to represent our deormalized form that's where our exponent field is all zeros now our our fractional field might not be all zeros so that's an encoding value that's going to put us next to zeros but give us a lot of bit patterns that we can designate as close to zero spaces that are distinguished from one another that are discernible against one another so here we'll have a type mapping of these deormalized spaces and then as we approach further from zero we actually get。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_306.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_307.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_308.png)

Les binary sequences so we actually get holes inside of what we can represent。

 but that's going to represent our normalized space because at this point we're starting to multiply our significant hand by two to the power of some expon right and we're going to see that's going to result in holes。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_310.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_311.png)

Real approximations， I mean it's the same approximation。

 but it's going to be very evident on the amount of gaps you then get depending on your your。😡。



![](img/b5d8c9bff1848023efc4ce9de006a74a_313.png)

How big or little the number is you're trying to represent？



![](img/b5d8c9bff1848023efc4ce9de006a74a_315.png)

Okay， let's see here。We have an example， but let me show you first。

 we'll walk through this example in a moment， but I did want to show you some examples while it's on。



![](img/b5d8c9bff1848023efc4ce9de006a74a_317.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_318.png)

Okay， this is just I was looking for the first visualization to really highlight this。

 imagine if we tried to do a number line of a six bit representation。😡。

Next class I kind of want to walk through these slides and motivate it more。

 but this will actually give you something to map conceptually this is a number line of everything we can represent if we limit ourselves to a six bit encoding using the IAEE format。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_320.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_321.png)

So that means one bit for the s bit that means three bits for our exponent field and two bits for our fractional field notice on here we get tons of values that populate next to our zero。

 but notice our encodedable space are only these purple triangles， so there are literal gaps。😡。



![](img/b5d8c9bff1848023efc4ce9de006a74a_323.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_324.png)

On the number line that just can't be expressed。

![](img/b5d8c9bff1848023efc4ce9de006a74a_326.png)

That's why that bias term is introduced to allow the behavior to be able to bias our terms in certain ways and so we can see here that this would not be a great representation if you needed something like a like minus 11 right you just can't do that you just jump from like minus 10 to like maybe minus 12。

5。

![](img/b5d8c9bff1848023efc4ce9de006a74a_328.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_329.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_330.png)

And again， we'll motivate this a little bit more out of time right now， but。



![](img/b5d8c9bff1848023efc4ce9de006a74a_332.png)

You could see this is a very powerful way of being able to use a finite number of bits to represent these really small and large values and we'll examine it a little bit more maybe we'll play around with the little source code next lecture and then then we'll be done with this chapter and we'll move on to another chapter。

😡。

![](img/b5d8c9bff1848023efc4ce9de006a74a_334.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_335.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_336.png)

Yeah。不。Yeah， all labs just to answer the question on the chat， yes。

 all labs you should use the web terminal floor because there'll be special services that you can use that are preinstalled for you to do your labs。



![](img/b5d8c9bff1848023efc4ce9de006a74a_338.png)

![](img/b5d8c9bff1848023efc4ce9de006a74a_339.png)

That。

![](img/b5d8c9bff1848023efc4ce9de006a74a_341.png)