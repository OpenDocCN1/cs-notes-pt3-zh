# 【精译⚡算法导论】AbdulBari p51 p50 -New- Matrix Chain Multiplication using Dynamic Programming Formula -BV1hhPXeTEWM_p51-

はい。Topic of this video ismatic exchange multiplication， Al I have one video in my playlist。

 but there are a few things I have missed there in that video。

 so it may be a little bit confusing for the students who are making a new video on the same topic。

The problem in YouTube is we cannot edit the video。 I cannot add something to the video。

 So I have to make a new video once again。 So the contents of the video are。



![](img/82f0a604397bb1d4fed8f2ace87dd093_1.png)

What is matrix multiplication， I'll explain this， then what does it mean by matrix chain multiplication and。

How to apply dynamic programming。 So here I'll be giving you the idea approach for solving a problem using dynamic programming。

 right。Then if you are interested in learning problem solving， then don't miss this part。

Then I'll use the formula of dynamic programming and show you how to solve the problem。

 what should be the approach for solving the problem。



![](img/82f0a604397bb1d4fed8f2ace87dd093_3.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_4.png)

Then the last thing I'll show you a example problem。

And if youre here one day before the examination then you need this one directly so you can directly jump onto this part of the video and you can finish it so youll learn how to solve a problem that solved right so how the formula is obtained and all details you have to spend time definitely and if you are watching for learning the problem and learning problem solving then this there are a lot of things to learn from this video so let us start with matrix maliccation。



![](img/82f0a604397bb1d4fed8f2ace87dd093_6.png)

First of all， matrix multiplication， see， there are two mates in this example， A and B。

 A's of dimension， two rows， three columns， two rows and three columns。

 and B's of dimension three rows and two columns， three rows and two columns。



![](img/82f0a604397bb1d4fed8f2ace87dd093_8.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_9.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_10.png)

First of all， the condition for multiplying two mattresses is。

The number of columns of the first matrix must be equal to number of rows of second matrix means these two must be equal。



![](img/82f0a604397bb1d4fed8f2ace87dd093_12.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_13.png)

That is these two must be equal then multiplication can be done this is the condition for multiplication and how we multiply s we multiply all the elements of a row single row with all the elements of a single column。



![](img/82f0a604397bb1d4fed8f2ace87dd093_15.png)

Multiply the elements and add their products。 So that is shown here。

 This is how multiplication is done。

![](img/82f0a604397bb1d4fed8f2ace87dd093_17.png)

So this is how one single element is obtained。But what is the dimension of the resultant matrix。

 the resultant matrix A to B that us call it a C。 This is of dimension 2 cross 2。



![](img/82f0a604397bb1d4fed8f2ace87dd093_19.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_20.png)

Then one more thing， To how many multiplications I have done。 Let us see。



![](img/82f0a604397bb1d4fed8f2ace87dd093_22.png)

1，2，3。1，2，3。 So 3， how many times， four times。 So2 well multiplications I have done。 So actually。

 if you see the number of multiplications I have done for getting this result as。



![](img/82f0a604397bb1d4fed8f2ace87dd093_24.png)

2，3，2。22，4，4，3，12，2 multiplications I have done for obtaining this resultant matrix。

 that is a into B。So from this， we have to pick a few things。

 First is when two mates can be multiplied。 this condition that this must be equal。

 then only multiplication can be done。 This is the important thing。 Second thing。

 what will be the resultant matrix， dimension of the resultant matrix。

 The dimension of the result matrix will be these two extremes。

 that is number of rows of first matrix and the number of columns of second matrix that is two cross through。

 This is the second point。 And the third point that we have to pick up is for generating or multiplying the matrix。

 total how many multiplications are required。 That is this dimension into this one and this one。

 this is common， right， this is same。 So two into three into two。 So two into three into two。

 these many multiplications are required。 So these are the important things。

 and one more important thing I will show you that we must know for further understanding。 See。

 I have two minuses A and B。 And if you take dimensions， total how many are there。



![](img/82f0a604397bb1d4fed8f2ace87dd093_26.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_27.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_28.png)

Fster。Second。Thirdd。Fourth， so two mates， total four dimension， but these two must be same。

 so let us call it as one。 So if you call it as one then total ho many dimensions，1，2，3。

 So total three dimensions are there， three different values are there。

 right and this is the first matrix dimension and these are the second matrix dimension and one of the dimension is common。

 So for the two matisees， total three different dimensions are there where one of the dimension is common for them。



![](img/82f0a604397bb1d4fed8f2ace87dd093_30.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_31.png)

So that's all the important things I have highlighted here that is useful for matrix chain multiplication Now let us learn about what does it mean by matrix chain multiplication。

For explaining mat chain multiplication， I have an example here。

 I have three mates even a2 a3 and I want to multiply them so there are more than two matisees so and I want to multiply them so first of all check whether they can be multiplied or not see if I take these two matisees then the dimensions they should be matching number of columns of first one should be equal to number of rows of second one Yes they are matching they can be multiplied and if I take these two and then see this are matching Yes。

 they can be multiplied。

![](img/82f0a604397bb1d4fed8f2ace87dd093_33.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_34.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_35.png)

Now these are A 1 A2 a3 dimensions also I will label them。

 let us call this as a D0 and these two are same so let us call both of them as a D1 D1 and these two are same so this let us call this as a D2 D2 and D3。



![](img/82f0a604397bb1d4fed8f2ace87dd093_37.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_38.png)

This labeling may help us afterwards， Let us， I have given the labels。



![](img/82f0a604397bb1d4fed8f2ace87dd093_40.png)

Now， let us proceed。So I want to multiply these three mat Now the question is can I multiply all three together No。

 I have to multiply two mates at a time then what are the possible ways see the first methodist I can multiply a1 with a2。



![](img/82f0a604397bb1d4fed8f2ace87dd093_42.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_43.png)

And the result of it a3。This is one possible。

![](img/82f0a604397bb1d4fed8f2ace87dd093_45.png)

And another possible method is， even as it is， then。A2 and a 3， I should multiply first。

 then the A1 should be multiplied with the result of。Product of A2 and A3。

 So there are two possible methods。

![](img/82f0a604397bb1d4fed8f2ace87dd093_47.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_48.png)

See whether this one and this one gives same result。Yes， they are associative。

 Associative property holds on matrix multiplication。

 whether you multiply these two first then the result with this one or first these two。

 And this with the result， you get the same answer。 So the product of three mates will be same。

 so I can multiply in either way。 Now， whatever the elements maybe they in even 823。

 I am not interested in that。 I am not really trying to multily them。

 I want to know how much efforts I have to put in for multiplying them。



![](img/82f0a604397bb1d4fed8f2ace87dd093_50.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_51.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_52.png)

So let us see if I multiply a1 with a2， then total how many multiplications I have to do。

 how many multiplications I have to perform。 So what are those dimensions。



![](img/82f0a604397bb1d4fed8f2ace87dd093_54.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_55.png)

2，3。And 3，4。 So total how many multiplications will be done here for multiplying this。

 This is 2 into 3 into4。 These are 24 multiplications。This side total 24 multiplications。

 So if I'm multiplying matters a1 with a2， total 24 multiplications。

 I have to perform for those elements。 Now， what about this one， This is dimensions are4，2。

 But how many if you take this separately no multiplications required for this one。

 So 24 multiplications for this and this is nothing。 Now I have to multiply these two together。

 right， this whole thing this whole thing with this one。

 So total how many multiplications required for this， this will be having dimensions to cross 4。

 right， So you remember， the result matrix will have the dimensions of these two number of rows of first one and number of columns of second one。

 these two and this one，4，2。 So these two are same。 Yes， multiplication can be done。

 So total how many multiplications for this。 this is two into4 into two。

 So these are 16 multiplications right these。

![](img/82f0a604397bb1d4fed8f2ace87dd093_57.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_58.png)

Total 16 now， if you find out altogether 24 multiplications this site plus zero multiplications that site plus 16 multiplication。

 so this is how much 24 plus 16 40 multiplications I have to do。

Multiply these two takes 24 multiplications。 and this is nothing。 This a single matrix 0。

 Then multiplying these two together。 S 2，4，2。 So total 40 multiplications are required。

 What about this， let us take this the dimensions are 2，3， and this is 3，4 and 4，2。 first of all。

 I have to multiply this， This is 3 into 4 into2。 So this is 24。

 And the result of this is the dimensions will be 3，2。 And what about this side， This side will be 0。

 No multiplications required on this side。 Now， when I have to multiply these two together。

 the dimensions are 2，3， and this is 3，2， right， these are the dimensions like this one and this one。

 So these two are common。 So same， we can multiply these two are same， we can multiply。

 So total how many multiplications required for this one。2 into 3 into 2。

 then plus what about this side 0。

![](img/82f0a604397bb1d4fed8f2ace87dd093_60.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_61.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_62.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_63.png)

What about this side， This is total multiplications are 24，24。 So 24 plus this is 2，36 to well。

 So this is 36 multiplication So total 36 multiplications are required So observe this carefully。

 you wash it once again this portion is very important。

 this calculation and from this we can say that if I multiply these two first and the result with this one or this with the result of this one the cost of multiplication is different I mean the number of multiplications I have to perform for getting the results are different。

 So which parentization is better means first I should multiply these two mates then this with the result of this one that will take only 36 multiplication So it's a small example of just three mates and there are there is a difference of just four So four is not a small figure right because the number of mates are very small we are looking at at a very small level if suppose you have mates。



![](img/82f0a604397bb1d4fed8f2ace87dd093_65.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_66.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_67.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_68.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_69.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_70.png)

One multiplied with a2 multiplied with a3 goes on to a10。



![](img/82f0a604397bb1d4fed8f2ace87dd093_72.png)

There total cost of multiplication means which mates should be multiplied first。

 it is a big problem there， so you cannot simply start multiplying a A1 with a2 then the result with a3 result with a2。

 so it will be maybe very huge， if you find out a easier method for multiplying them then is better。

 So first find out how to multiply them then multiply the mates。

 So that's it if you have the chain of matisees for multiplication。

 then first of all find out which multiplication should be performed such that the total efforts put for multiplying them should be minimize。



![](img/82f0a604397bb1d4fed8f2ace87dd093_74.png)

This is mat chain multiplication problem。 So if the chain of mattresses are there that has to be modified how the parentheization should be done。

 such that the efforts required for multiplying the mattresses should be less。

 See here you can see that if you multiply these two and the result with this one is 40 and this way is 36。

 So this is better。 And if you have 10 mattress， then there may be a different possibility and one of the possibility may be a best possibility。

 So that's it we have to find out the best possible parentheization such that the total cost of multiplication is minimize。

 Now we need a approach for finding the minimum one So dynamic programming approach says that you should try all possible parentheization and pick up the best one。

Possible all possible one and pick up the best one So for 10 we have to post try all possibilities and then whichever is giving minimum you have to take that pattern of multiplication。



![](img/82f0a604397bb1d4fed8f2ace87dd093_76.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_77.png)

So for three， how many are there， only two are there， so we tried both of them。

 and we found this is better。 So we have already done this。

 but this we can't think of doing on 10 matters。 Imagine how many possibilities you will have。



![](img/82f0a604397bb1d4fed8f2ace87dd093_79.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_80.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_81.png)

But we must find out all possible methods from that， we should pick up the best one。 So for this。

 we need some formula that is by using this approach。 we need some formula。

 Let us frame a formula for dynamic programming for math chain multiplication。

 So here already I have an example。 So this I will convert it into a formula right。

 I have two examples here from this only I will make a formula first of all。

 watch this very carefully。 I creating or generating a formula from this example。



![](img/82f0a604397bb1d4fed8f2ace87dd093_83.png)

So let us say I want to find out the minimum cost for multiplication。

 So I have to find out the cost of one2 3。 So there are three mates。 let us say cost of one to3。

 So I'll just write c now for cost。 Okay， then let us look at this。 Abserve this。 What is this24。

 This is the cost of multiplying 1 and 2。 So I'll remove this I'll remove this。

 and this I will say cost of multiplying  one to2。 and what is the0。

 Ca was writing0 that was not required that time。 I should have skip。 but now this is useful。

 You see this is cost of multiplying third matrix with the third matrix only So the cost of this side is one to2 cost of that side is3 to 3 and that was0 and this was 24。

 This was 24。 I will write it。 right This is0。24 and0。So cost of this one and cost of this one。

 So final result， what I was getting， this was cost of 1 to 2。

And this was cost of 3 to 3 and 3 to 3 is 0 because the single matrix。 Then what was this。

 the cost of multiplying these two together， these two together。 So these are the dimensions I have。

 What is this dimension， this one， This is D 0。 This is D 0。 What is this dimension， this one。

 This is what D2， This is D2。 So this is D2。And what is this dimension， this one， last one， right。

 what is that D3， this is D3。So what are these， this is D0 and this is D2， and this is D 3， D0， D 2。

 D3， I have multiplied these three。

![](img/82f0a604397bb1d4fed8f2ace87dd093_85.png)

And I got the result as  for T。 Now， let us convert this also into the formula。

 This is worst cost of one come of1 cost of multiplying 1 come of one itself。 Thats 0。

 It a single matrix only。 And what is this cost of。



![](img/82f0a604397bb1d4fed8f2ace87dd093_87.png)

2，23。 and what is this 24。 How to get this one， This is 3 into 4 into 2。 We know it well。 So。

 and it is cost of multiplying2 with three。

![](img/82f0a604397bb1d4fed8f2ace87dd093_89.png)

Then。

![](img/82f0a604397bb1d4fed8f2ace87dd093_91.png)

What is this cost of Lcom oven？And this is what cost of2 comma 3 and what are these dimensions。

 this is this is the first one and that is d0， this is d0， right？And this is3， this is a D1，3。

3 is a D1。 Yes， this is D1。

![](img/82f0a604397bb1d4fed8f2ace87dd093_93.png)

And this is the last one that is D3。 this is D3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_95.png)

And this is 36。 So I have made it like a formula cost of this site， left side， cost of right side。

 then cost of multiplying two together。 So I got it in the form of formula。 Let us observe this。



![](img/82f0a604397bb1d4fed8f2ace87dd093_97.png)

If you observe1，2。

![](img/82f0a604397bb1d4fed8f2ace87dd093_99.png)

3，3，1，1，2，3。So if you observe the first one and the last one are same。

 let us call this as I and this as J and this as I and this as J in both I and G are same。



![](img/82f0a604397bb1d4fed8f2ace87dd093_101.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_102.png)

Then what about this D0， d3， d0 d3， and this is d1 and this is d2。

 so let us call this as D I minus1 and this is j is 3 right this is Dj。



![](img/82f0a604397bb1d4fed8f2ace87dd093_104.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_105.png)

Let us call this as D of I -1， and this is DJ。

![](img/82f0a604397bb1d4fed8f2ace87dd093_107.png)

Then what is this。This is2 and3。 This is one and2。 So if this is one， this is2。 If this is2。

 this is3。 This is what I am observing， right， this is my from the observation。

 I am creating a formula。 then this is it even and this is D2。

 So it means that part should come first。 So let me write a formula。 So I'll write the formula here。

 I'll write it here。 See I have to find out the cost of I comma G。



![](img/82f0a604397bb1d4fed8f2ace87dd093_109.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_110.png)

Ass what。This site cost of I comma， What is this， I should call it as K， and this is K plus 1。

 So and here also， I should call it S K， and this is K plus 1。

 So now if you observe everything is perfect。 see， C of I K， K plus 1 to J， C of I K， K plus1 to J。

 So when you say I J， there are 1，3， and these are also 1，3。



![](img/82f0a604397bb1d4fed8f2ace87dd093_112.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_113.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_114.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_115.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_116.png)

K is here 2 and 3。 K is here 1 and 2。 And this is 0 and 3。 This is 0 and 3。 So I -1 J， I -1 J。

 And this is D， K。 K is one first time。 and K is2 second time。 So let us call it as D K。 Okay。

 this is K。

![](img/82f0a604397bb1d4fed8f2ace87dd093_118.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_119.png)

So based on this， I will write a formula now this side C of IK cost of left side plus cost of right side。



![](img/82f0a604397bb1d4fed8f2ace87dd093_121.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_122.png)

G plus1，2 J。

![](img/82f0a604397bb1d4fed8f2ace87dd093_124.png)

Then plus。D of I -1 K and DJ。

![](img/82f0a604397bb1d4fed8f2ace87dd093_126.png)

Dimenssion I-1 into。 I'll remove this dimension K into dimension J。



![](img/82f0a604397bb1d4fed8f2ace87dd093_128.png)

So I have combined these two together。

![](img/82f0a604397bb1d4fed8f2ace87dd093_130.png)

In terms of I J K， then what K is taking the value K is here， first time1 and second time 2。

 So that should come first then this one。 So K1 takes the values that are studying from I what1，1。

 So K takes the values from。

![](img/82f0a604397bb1d4fed8f2ace87dd093_132.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_133.png)

I， but less than J。 K is not becoming3。 K became 1， and K became 2。 That's all。Out of these two。

 I want minimum。I want minimum。 So this is the formula for mat multiplication。

 So from examples of just three mat， I have prepared the formula。

 So the idea here is that once again， I will tell you this is the cost of multiplying these two sides。

 Then what is the cost of left side cost of right side。 those two are it done here。

 cost of left side and cost of right side。 How I multiply these by multiplying three dimensions。

 right， What about this cost， this also multiply these。



![](img/82f0a604397bb1d4fed8f2ace87dd093_135.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_136.png)

Dimmensions， three dimensions and get the result。 Moly these three dimensions and get the result。

 It's the same thing。

![](img/82f0a604397bb1d4fed8f2ace87dd093_138.png)

So the cost of multiplying twoysis， you have to multiply the dimensions and you get the number of multiplication。

So here is a formula。 This formula will give you minimum。

 so you should try different values of k here we tried k as 1 than k as 2 as you have three matrices。

 So only K value can be  one n 2。 if you have more mates then K value can be 1，2，3，4， so on。



![](img/82f0a604397bb1d4fed8f2ace87dd093_140.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_141.png)

If you have 10 mes up to 9， it will go。So this formula says that try all possibilities and pick up the best one minimum one。

 what are the possibilities you change the K value。So some on this side， some on that side。

 So now I will write on the formula here and I will remove this and Ill show you how it looks like for four mattresses。

 then afterwards we will solve a problem。

![](img/82f0a604397bb1d4fed8f2ace87dd093_143.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_144.png)

Here I have four mates and let us say dimensions are D0 to1 and D2 D3 D4， these are dimensions。

 What are the possible ways of multiplying those mates before match actually multiplying mates we want to know which parentheization will require less efforts of multiplication So there are many methods of parentheization this is the first one A1 with this one a2 with the result of2。

3 right 34 then a then inside this3 first I can multiply the studentend this one so there is another parentization or even a2 with result of a3 a4。



![](img/82f0a604397bb1d4fed8f2ace87dd093_146.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_147.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_148.png)

Or this site， a4 is left over A 1 with result of A2， A3， then this entire thing with a4 or first A 1。

 A2 result with a 3 result with a 4。There are five different methods of parenttheization。



![](img/82f0a604397bb1d4fed8f2ace87dd093_150.png)

So if you want to know for formatmates， how many parentizations are possible 5。

 So if you want to know how many multiplications required for this one。

 So there is a formula called Cat number。 as we have foures。 So you can use that。

 Actually the formula is a 2 n c by n plus1。 but here you have to take n as number of mates -1。

 So n should be 4-1。 you should not take n as a 4， just you take3， and then you get the answer。

 So if there are formates， then actual value。 if I write here is2 into n-1 C of n-1。



![](img/82f0a604397bb1d4fed8f2ace87dd093_152.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_153.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_154.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_155.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_156.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_157.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_158.png)

By n -1 plus1 is n only。 So this will be the formula modified for mat chain multiplication。

 So let us put this one。 I have four mates。 So this will be what if I take four mates2 into4 minus-1。

 that is 3 and C， this is also 3 by this is n 4 mates are there where n is 4， I have taken n S4。

 So this will be 6， C 3 by4 So 6，3 by 4 is 6 into 5 into 4 divided by3 into。

2 into1 whole divided by 4，44 gets cancel take 2，3，6 cancel。 So 5 is the answer。

 And if you take n is equals to5 mates， then take1 less for n and put this in this formula then youll get 14。

 So 45 mates，14 multiplications are required。 right4 and possible parents are there for this。



![](img/82f0a604397bb1d4fed8f2ace87dd093_160.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_161.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_162.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_163.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_164.png)

Possible parenttheization are there。 So out of these five。

 we have to pick up the best parentheization that is giving minimum result。

 So this we will do it using the formula。 So now I will remove this。

 I will use this formula and show you how I can apply that formula on these four mattresses and if I apply what problems I face then I will show you the solution for that problem。

 then later on we will find solve example problem。 So I will use the formula on this four mattresses。

 we don't have the dimensions， let them be d0 to even D2 only when we see the example that time might take some values if I apply the formula the cost of。



![](img/82f0a604397bb1d4fed8f2ace87dd093_166.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_167.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_168.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_169.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_170.png)

C of1，2，4， because four matches is other there that are 1 to 4。 So I is1 and J is 4。

This should be minimum of minimum of k should take the values greater than equal to i is what 1 and less than j that is 4 so what are the possible values k can take k can be 1 k can be 2 and k can be 33 values are possible for k。



![](img/82f0a604397bb1d4fed8f2ace87dd093_172.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_173.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_174.png)

Less than 4。 So if I put a K as one in this one， right， what it looks like， C of I is 1， Js 4。

 Remember this1 comma Cha is what1。Plus C of K plus 1 K is1 minus K 2 k plus1 is 2。

 and j is 4 plus this is D of I1 I is what I what 1， this is 0 D0 plus K， D K。

 K is what now K I'm taking as1 K is 1， and this is into sorry， and this is into d 4。



![](img/82f0a604397bb1d4fed8f2ace87dd093_176.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_177.png)

This is K value as one。 If I take K value as a2， this is one to 2 plus C of a 3 to 4 plus D 0 plus D 2。

 sorry into。D 2 into D 4。Then if I take K value as a  three， then this is 1，3 plus C of。44。Plus。

D 0 into D 3 into D 4。

![](img/82f0a604397bb1d4fed8f2ace87dd093_179.png)

If I expand the formula， I get three different terms， three different values out of this。

 I have to take minimum。 I'm not writing them in a single line。

 It will be very lengthy on paper and you can do that right So comm comm this comm this comm this one So k is one case2 case 3 out of this it is trying all possible parentheization right So actually these means if I draw first one means a1 width。



![](img/82f0a604397bb1d4fed8f2ace87dd093_181.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_182.png)

A2， a 3， a 4。 how they are multiplied。 we don't know。 So this is a 11。 This is2 to 4。

 the cost of this and how what is the cost of multiplying these two their dimensions， D 0， D1 and D4。

Then what the second one means， second one means a1 with a2 and this parentheesis then this is a3 and a4。

 so the parentheization is done at matrix 2 k is2， so1 to2 on this side3 to4 on this side。

 then cost of this and cost of this， then cost of multiplying these two cost of multiplying these two。



![](img/82f0a604397bb1d4fed8f2ace87dd093_184.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_185.png)

Then this one， last one says a1， a2， a3 and this side is a4。

 so the cost of multiplying all three with this result， one23 and 4 to4， one，23 and 4 to4。

 then the cost of multiplying these two together， these two together。

So this is trying all possibilities。Now， if I know the answer， if I know the values。

 I can put these values and get the answer。

![](img/82f0a604397bb1d4fed8f2ace87dd093_187.png)

So from this， you already know two values。 what are those。C one one。Single matrix，0。 you remember。

 we have taken it and C 4，4， it is a 0。 This is 0。 Then what about C 2，4， Let me put it here。



![](img/82f0a604397bb1d4fed8f2ace87dd093_189.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_190.png)

This， I can take it as0， but C 2，4。 let me expand C2，4 is minimum of it's a formula again。

 K takes the values from2 till 4。 So K can take what values K can be 2 and K can be 3。

 So two values it can take Now from this， if I take the formula。

 C I is 2 J is the 4 I is the 2 J is 4。 remember this。



![](img/82f0a604397bb1d4fed8f2ace87dd093_192.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_193.png)

2 comma 2 plus C of 3 comma 4 plus dimension 2 into dimension。Sorry， this is one and 2。

 and this is dimension 4。

![](img/82f0a604397bb1d4fed8f2ace87dd093_195.png)

C。

![](img/82f0a604397bb1d4fed8f2ace87dd093_197.png)

I K， K plus 1，2 J， K is 1， right， This is D I-1， D， K and DJ。



![](img/82f0a604397bb1d4fed8f2ace87dd093_199.png)

So you can check it。 You can pause and check it。 I have used the formula here where K values to I G N R 2。

4。 Now C， I， K， K is 3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_201.png)

Plus c of k plus 1 that is4 to J that is 4， then plus D I minus1 i is 2， so d1 into D K K is 3。

3 into d 4。

![](img/82f0a604397bb1d4fed8f2ace87dd093_203.png)

Oh， it means that for finding C of2 coa 4 again， I need formulas。



![](img/82f0a604397bb1d4fed8f2ace87dd093_205.png)

To come4 I need again formula。 So in this one， this value， I know，0。4，4，0。



![](img/82f0a604397bb1d4fed8f2ace87dd093_207.png)

Then what about the 3，4。 So again， I will find out， see this thing This thing。

 this entire formula is just one cost here， This one， What about this， What about this。

 What about this， I have to find out all of them。 So it's too Ly for finding this one。 Firsts of all。

 I should find out this， right。

![](img/82f0a604397bb1d4fed8f2ace87dd093_209.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_210.png)

And find out these。 So why can't if we first find out these smaller values， then go for larger value。

 So what does it mean by smaller value， La value， Let us check this 4-1。



![](img/82f0a604397bb1d4fed8f2ace87dd093_212.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_213.png)

How much3。 So this require three formula， three values， right，3 different values。 This is 4-2。

 This is 2。 So this required two values out of which。 We will pick up anyone。



![](img/82f0a604397bb1d4fed8f2ace87dd093_215.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_216.png)

Then what about。31 go12。It will have only one value。 And what about three comma 4。

 It will have only one value。 See， the difference is one。 difference is one and difference is 0。

 difference is 2。 right， difference is 2。 So it means first。

 I should find out which formulas where the difference of I and J is 0。 Then it is one。

 then it is a two。 Then it is a three in this way， I should proceed。 I should not put the formula。

 And first find out this one。 Then for this， I have to find out this。

 it will be going explaining like this。 It's not practical。 It's not practical。

 Then how I should do this one。 So first， I should find smaller values。

 Then I can get the larger value。 And one more important thing。 You observe here。 See。

 I have three comma 4 in this formula。 I have three comma 4 here Also。

 So if I find out three comma 4， it is useful at different places。



![](img/82f0a604397bb1d4fed8f2ace87dd093_218.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_219.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_220.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_221.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_222.png)

Right not just at one place， it is useful at different places forcom of4。

 at the same thing only right。So it means how actually we should solve this problem。 So for this。

 we will prepare a table。 We will prepare a table。

![](img/82f0a604397bb1d4fed8f2ace87dd093_224.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_225.png)

4 rows，4 columns。 Now， this represents。So this is 1，2，3，4 and 1，2，3，4。 These are row numbers。

 Let us call them as I， and these are column numbers。 Let us call them as J。

 So what I will do is first I will find out smaller values。 That is C of 1，1， C of 2，2， C of 3。

3 and C of 4，4。 this I will find out when 11，2，2，3，3，4，4。 So this will already 0。 I know it right。

 So already I have shown you this one。 So this will be 0。 So I fill them with 0 already。



![](img/82f0a604397bb1d4fed8f2ace87dd093_227.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_228.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_229.png)

Then I will find out the values which differences one differences one means more。



![](img/82f0a604397bb1d4fed8f2ace87dd093_231.png)

1，2，2，3，3，4。

![](img/82f0a604397bb1d4fed8f2ace87dd093_233.png)

Right， see 1，2 and 2，3 and 3，4。 these values， I will find out。

 Then with difference with the two difference with the three。 Finally， So in this way。

 I will have filled this diagonal than this diagonal than this diagonal and this diagonal。

 So in this way， let us find out the cost。 So let us start finding the cost from smaller values。

 not from the larger value。

![](img/82f0a604397bb1d4fed8f2ace87dd093_235.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_236.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_237.png)

This is okay。And what should be the name of that？

![](img/82f0a604397bb1d4fed8f2ace87dd093_239.png)

Table， let us call it as I am calling it a sin cost cost。 So let us say see。



![](img/82f0a604397bb1d4fed8f2ace87dd093_241.png)

In the previous video I wrote it as M because this was this I was taking it as MM。

 so M formatics multiplication it's the cost of matrix multiplication you can use any name that is not an issue。



![](img/82f0a604397bb1d4fed8f2ace87dd093_243.png)

Now one more table I will make。 what is that table， I'll prepare a table first， so this is again。



![](img/82f0a604397bb1d4fed8f2ace87dd093_245.png)

4 rows，4 columns，4 rows，4 columns。 I will prepare。 This is 1，2，3，4， and 1，2，3，4。



![](img/82f0a604397bb1d4fed8f2ace87dd093_247.png)

What is this for See out of these three， I'll be taking the minimum1 and that cost I'll be writing there。

 Yes， you remember this out of these two I'll beating the minimum 1。

 and I will be writing the cost of two co of4 here， two co of 4。 I'll be filling it。

 So I will find out minimum of these two。 So what is the difference between these two K value is different。

 K value。 So K values is2 and K values 3。 So I need to know for which K value I got this minimum answer。

 K can be 1 K can be 2 K can be 3。 So which k has given me a minimum answer。 So this a table。

 let us call it as a K table。

![](img/82f0a604397bb1d4fed8f2ace87dd093_249.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_250.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_251.png)

Okay， on the previous video， I was calling it as S a table。 So in the textbooks。

 you will find S as a name。 So I have taken S only。 but now here I am using variable K。

 So let us call it as K table。

![](img/82f0a604397bb1d4fed8f2ace87dd093_253.png)

Kは be there。Now I will take an example problem and I will solve it。

 Let us see how we can solve it by first solving smaller problems than with the larger problem。

 So in this table already we know this 1，1，2，2，3，3 right and 4。

4 Now let us fill up the list of the value。 So I will take some dimensions for the formates and I will solve it。

 So I have taken the dimensions4 mates are there this is dimension D0 and this is D1。



![](img/82f0a604397bb1d4fed8f2ace87dd093_255.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_256.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_257.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_258.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_259.png)

This is D 2。D 3。Before。

![](img/82f0a604397bb1d4fed8f2ace87dd093_261.png)

F dimensions that is total five dimensions starting from 0 onwards，0，1，2，3，4。 so four mat I have。



![](img/82f0a604397bb1d4fed8f2ace87dd093_263.png)

Now， as I said that we will use this formula， but we will not directly put one comma4 here。

 we will put smaller values。 so in which way we will start with differences。

 that is a difference0 difference1 than difference2 different0 already I have filled there。

 So it is just like c of1 comma 1 if it want c of1 comma 1 So formula says minimum of right k takes the values greater than or equal to1 but less than1 so greater than equal to1 equal to1 I can take but less than1 how it can take so I cannot take any k value。

 So the result of c of1 comma 1 is0。 That's why all the is 0 similarly for2，2，3，3，4 for all。

 So it is 0。

![](img/82f0a604397bb1d4fed8f2ace87dd093_265.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_266.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_267.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_268.png)

Now， we will find out difference one。 So here I will write down C of1 comma 2。

 So let us find out C of1 comma2， this 1 I am finding。

So it is minimum of let us put it in the formula formula says that k10 take the values starting from one。

 but it should be less than 2。So yes， k can take only one value。 That is one。 so let us put it。

 if I make K as1， then what it will be C of one comma。



![](img/82f0a604397bb1d4fed8f2ace87dd093_270.png)

K， K is what1， K， I'm taking it as one。 So one， C of 1， come1 plus C of K plus 1， K what1。 So2。

 then J， J is what 2。 This is I。 This is J。 Remember this。 So 2，2 plus。



![](img/82f0a604397bb1d4fed8f2ace87dd093_272.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_273.png)

D of I minus1 case1， so D 0 into D K， that is a D1 into DJ， that is D2。



![](img/82f0a604397bb1d4fed8f2ace87dd093_275.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_276.png)

With only one k value possible， so this is only the value so that itself is minimum。

 so find out what are d0 d1 d2 so d0 is how much a 3 right and d1 is how much d1 is a 2 and d2 is how much d2 is a 4。



![](img/82f0a604397bb1d4fed8f2ace87dd093_278.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_279.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_280.png)

Then what about C 00 already we have it in a table that is the benefit we will get now。

 if you start from smaller values for solving such formulas。

 this is 0 plus 0 plus this one how much it is 2，3，6。

6434 so the result of one comm 2 is 34 so I'll write here 24。



![](img/82f0a604397bb1d4fed8f2ace87dd093_282.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_283.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_284.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_285.png)

First value I got and for which value of k I got that 24，1 comm2 here k value， k value was1。

 so put it as1。

![](img/82f0a604397bb1d4fed8f2ace87dd093_287.png)

So k of1 comma2 is 1。 That K value has given us the result。 Now。

 let us find out C of2 comma 3 cost of2 comma 3。 So here right， cost of 2，3 I is 2 and J is 3。

 So this is minimum of K can take the values starting from 2， but should be less than 3。

 So only one value that K can take That is 2。 So C of I comma K K is what only possible values 2 I comma K plus C of K plus1 to J。

 J is 3， right， then plus。

![](img/82f0a604397bb1d4fed8f2ace87dd093_289.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_290.png)

Dimenssion of a k -1。 That is given into。

![](img/82f0a604397bb1d4fed8f2ace87dd093_292.png)

K then J。C 2，2， we already have it in the table，0。

![](img/82f0a604397bb1d4fed8f2ace87dd093_294.png)

3，3， also，0 plus。

![](img/82f0a604397bb1d4fed8f2ace87dd093_296.png)

D1， D2， D3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_298.png)

D1， D2， D 3，2，4，2， So 2，4。2， so how much this is0 plus 0，2，4s，8 and 8 into 2，16。 So this value is 16。

 So I will write on the value 16 here。 This is 16。

![](img/82f0a604397bb1d4fed8f2ace87dd093_300.png)

And for which value of a k we got that as 16，4 k value as 2， so 2 comma 3 is 2。



![](img/82f0a604397bb1d4fed8f2ace87dd093_302.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_303.png)

Right， now， next value， C of。Next is。Take广 four。Okay， so I will not explain simply I will write out。

 okay， to save your time and my time。So here already I have written it。

 So only your time is saved because I have written this one。 So C of 3，4，3，4。

 So k takes values from 3 to 4。 So only one K values is possible。 that is 3。

 So I have taken k value as 3。 So these are the cost plus a dimension。

 So cost is 0 cost is 0 and this is 4 into2 into 5。 So that is 4 into 2 into 5。

 So 54 is 20 into 20 into 2 that is 404 is the answer。 So the cost of 3。

4 is how much 40 cost of3 comm of 4 is。

![](img/82f0a604397bb1d4fed8f2ace87dd093_305.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_306.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_307.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_308.png)

40 for which value of k we got this K value as a  three。 So this is3 comm of 4 as 3。



![](img/82f0a604397bb1d4fed8f2ace87dd093_310.png)

Which key value has given？

![](img/82f0a604397bb1d4fed8f2ace87dd093_312.png)

So one diagonal is over now next diagonal these two values with a difference of two so I will remove this and I will find out the values for those two so the first one is1 comma 3 so cost of1 comma 3 cost of1 comma 3 formula is that minimum k takes the values greater than equal to1 and less than 3。



![](img/82f0a604397bb1d4fed8f2ace87dd093_314.png)

Right， so what are the possible values K can take， K can be1。And K can be2。

K cannot be3 because it should be less than3。 So let us try both these K S 1。 see， I is 1 and J is 3。

 Remember this，1 comma 3。 You remember this。 So one comma 1。



![](img/82f0a604397bb1d4fed8f2ace87dd093_316.png)

C of two to three。Plus， D 0 and 2。

![](img/82f0a604397bb1d4fed8f2ace87dd093_318.png)

D1 into D 3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_320.png)

K value is one here。 You put this in the formula。 You get this one， then here。



![](img/82f0a604397bb1d4fed8f2ace87dd093_322.png)

C of 1，2， C of 3，3。Plus。D 0 into D2 into D 3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_324.png)

These are the two。 So what are the values， This is 0，1，1 is 0，2，3， C 1，1 is 0，2，3 is 16。



![](img/82f0a604397bb1d4fed8f2ace87dd093_326.png)

16。Plus， this has to be added。 dimensions，0，1，3，0 is a 3。One is a do。3 is two。 so how much this is3。

2，6，6，2，12，12 plus 16 S 28。

![](img/82f0a604397bb1d4fed8f2ace87dd093_328.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_329.png)

So this is 28。 So here I will write on 28 when the K is 1。 What about this C 1，2， C 12 is 24。

 This is 24。 C 3，3 is 0 plus。

![](img/82f0a604397bb1d4fed8f2ace87dd093_331.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_332.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_333.png)

D 0， D 2， D 3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_335.png)

D，0，3。4 and 2。 So 3 into 4 into，2，3，4，12，12 into 2，24，24 plus 24。 This is 48。



![](img/82f0a604397bb1d4fed8f2ace87dd093_337.png)

So which one is minimum， This one is minimum。So what is the value of k， K is 1， and it is 28。

 So C of 1，3 is 28。

![](img/82f0a604397bb1d4fed8f2ace87dd093_339.png)

And for which value of a K we got this one K value is one。



![](img/82f0a604397bb1d4fed8f2ace87dd093_341.png)

That's it。Now， the next one， this one， right？ This is 2 to 4， C of 2 to 4。

 I will write on this and explain you。 So here C of 2 to 4 k can take the values from 2 to 3。

 So 2 and 3。 So if I put2 here， I'll get this and 3， it is this one。 So what is this。

 let us take the values，2 to 2 is 0 and 3 to 4，3 to 4 is how much 4。



![](img/82f0a604397bb1d4fed8f2ace87dd093_343.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_344.png)

4。Plus dimensions I will write afterwards first let us fill of this C of 223。

 C of 223 is how much is 16。

![](img/82f0a604397bb1d4fed8f2ace87dd093_346.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_347.png)

16 plus 0。 So this looks smaller。 Okay， let us first put the dimensions of first one， right。

 What are the dimensions of this D 1， D2， D，4， D 1， D2， D，4，2，4，5。



![](img/82f0a604397bb1d4fed8f2ace87dd093_349.png)

2 into four into5。 What about this D1 D3， d4。2，2，5。 So 2 into 2 into 5。

How much is this54 20 into 2 that is 40，4080。 This is 80 and how much is this to do4 for 5，20。

 and this is 36， this is 36。 So this is minimum What is the value of k K is 3 right？

 So how much is this36。 So 2 co of 4 is 36。 and for which value of a k we got this1 K as3。 So k as 3。

 this is2 co of 4 is 3。

![](img/82f0a604397bb1d4fed8f2ace87dd093_351.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_352.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_353.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_354.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_355.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_356.png)

Only one value is remaining。 What is that C of1 comma4。 So I'll remove this。

 and I will find out C of1 comma 4。

![](img/82f0a604397bb1d4fed8f2ace87dd093_358.png)

C off when咁 off four。Minimum， what are the possible values of K。 K can take the values from1 to。

Less than4 is 3， so K can be1， K can be2 and K can be 3。So I will expand these。

 then you will put the values and see the result。So here I have taken different k values K1 and ks 2 and ks 3。

 so let us write on the values and get the result。 C 11 is 0 C2，4 is 36。

 this is 36 and plus d0 d1 D0 and d4 see this is3 and this is 5 so this is 3 and this is 5 and in between d1 is 2 D1 is 2 And what about this C of 1212 is 24。



![](img/82f0a604397bb1d4fed8f2ace87dd093_360.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_361.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_362.png)

And 3，4，3，4 is how much 4 tea。40 plus。These dimensions， this is3 and this is a5。

 and in between we have D2 D2 is 4。Then one comma 3，1 comma 3 is 28。



![](img/82f0a604397bb1d4fed8f2ace87dd093_364.png)

28，1 gumma3s，28， this one。

![](img/82f0a604397bb1d4fed8f2ace87dd093_366.png)

Plusus。4 commmophore is 0 plus this is 3 and this is5 in between D3 is there that is2。So out of this。

 which is minimum。 Let us check。3，2，6，6，5，30， And this is 36。 So this is 86。And this is 4，5， 20。

202 3，60， so this is 10124， this is 124。And this one is 28， and this is。3，2，6，6，5，30， 30 and 28。

 this is 58。

![](img/82f0a604397bb1d4fed8f2ace87dd093_368.png)

So which value K as a 3 has given us minimum value that is 58 and K as 3。



![](img/82f0a604397bb1d4fed8f2ace87dd093_370.png)

That's it。 So I got the table filled based on the formula。

 Now this means that cost of multiplying these foures of these dimensions， minimum cost is 58。



![](img/82f0a604397bb1d4fed8f2ace87dd093_372.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_373.png)

Imagine if you follow other methods， the number of multiplications maybe be 124 or maybe this is 86。

 so it is much more than this one。 this is more than double。

 So if you have a 1020 mates and you want to multiply them first of all find out how you should multiply to save your time then start multiplication right so we got that the best method will give you 58 number of multiplications so you have to perform only 58 multiplications for performing multiplication of these four mates so that is the optimal result。

 a minimal result right now how the parentheization should be done。



![](img/82f0a604397bb1d4fed8f2ace87dd093_375.png)

Wwhichch should be multiplied first then next what how the multiplication should be done That's what the important task is we want the parentheization So who will give you the parentization this table will give you the K values will give you so let us find the parentheization by following this K table right that is S table so I'll remove this and I will parentheize these four mattresses based on this。



![](img/82f0a604397bb1d4fed8f2ace87dd093_377.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_378.png)

So I have four mates that is A1， a2。

![](img/82f0a604397bb1d4fed8f2ace87dd093_380.png)

83。

![](img/82f0a604397bb1d4fed8f2ace87dd093_382.png)

A 4， right。Now how the parentization should be done follow this see this is the final answer this is the final answer remember this this is one come of four so when you have one to four then where the parentization should be done at a three at a three you have to do from one to four you have to do parent at three so at a three you put the parentheesis first step。



![](img/82f0a604397bb1d4fed8f2ace87dd093_384.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_385.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_386.png)

I'll wear them once again so that you can separately see them， okay。This is a4。

 so I have written them once again， so this is the first parent I have put。

 so I have taken once again。

![](img/82f0a604397bb1d4fed8f2ace87dd093_388.png)

Now， this is only one matrix。 when one matrix is there。

 you don't have to worry what about these three，1 comma 3，1 comma 3 is how much1。

 So parentis should be done at1。 So this has to be separated。

 then definitely what is left over now this is2 to3 is leftover because youll be multiplying two mates。

 this is separated。 like how I have separated this okay I should have put parenthees here Also See when it was one24。

 again， I am showing you so it was said that k is3， it said that k is 3。

 So at three I have separated and that side separated。 Now within this bracket 1 to 3。

1 to 3 said that1 to 3 is1 support a bracket at1。 then 2 to 3 goes on that side。

 Now this is complete。 this is total parentisization So this means that a1 should be multiplied with the result of a2 a3 and their result should be multiplied with a4 So Ill show you diagrammatic。



![](img/82f0a604397bb1d4fed8f2ace87dd093_390.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_391.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_392.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_393.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_394.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_395.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_396.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_397.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_398.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_399.png)

So as per the brackets， if you see a2， a3 are multiplied， right these two are multiplied。

 then a1 is multiplied with this， then a4 is multiplied with this final result。

So this is how multiplication should be done， this should be multiplied with the product of this and this should be multiplied with the product of this。

That's all。 So from this table I have done the parentheization once again I will show you one to 4 says3。

 so put a bracket at a 3 so from one to3 right this is4 to4 separate then to 3 says one to3 says put a bracket on one put a bracket one。

1 remaining R2 and three， so2，3 is a single product that is two minus one multiplication。



![](img/82f0a604397bb1d4fed8f2ace87dd093_401.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_402.png)

Right don't have to check further。 So if you check this is2 command3， then you will get two only。

 so this says that put a bracket like this like this okay so you don't have to do it further。

If you' are doing also， you'll get the brackets like this。

So this algorithm the multiplication should be done。All right。

So that's all about the example problem。 Now， if you're interested in knowing how much time it will take for。

Finding out the parentheization of math exchange multiplication， how much time it has taken。

 so I have filled the table。

![](img/82f0a604397bb1d4fed8f2ace87dd093_404.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_405.png)

Right that table and this one， how many values are there in that one， So if you count from here one。

 then two， then three， then4， so it means one plus2 plus3。



![](img/82f0a604397bb1d4fed8f2ace87dd093_407.png)

Plus4。So this is nothing but4 into5 by 2 for nnemat， it will be n into n plus 1 by2。

 so the time taken for filling that is n square。But how I am getting each value。

 so if you consider this 158， I tried all possible values of K and I got that one。

So K is taking the values from I to j。 So let us assume that is also n。

 So that value is not just computed in a。

![](img/82f0a604397bb1d4fed8f2ace87dd093_409.png)

![](img/82f0a604397bb1d4fed8f2ace87dd093_410.png)

So that value is computed by taking different k values， so let us say n values we are taking。

 so it is into n n squared into n， so it is n cube and we can say this is upper bound。

 we can say upper bound。

![](img/82f0a604397bb1d4fed8f2ace87dd093_412.png)

Bgo and cube。 so at most and cube， that is the meaning。Because K is not always taking n value。

 So if you want to go in detailed analysis and take all possible values of ks and check thoroughly also it may be somewhat less than Nq。

 So let us say upper bound as Nq。So that's all aboutmatic chain multiplication problem。

That's all in the studio。

![](img/82f0a604397bb1d4fed8f2ace87dd093_414.png)