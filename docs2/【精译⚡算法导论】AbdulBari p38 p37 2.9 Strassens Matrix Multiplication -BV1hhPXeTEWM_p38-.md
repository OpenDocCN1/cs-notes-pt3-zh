# 【精译⚡算法导论】AbdulBari p38 p37 2.9 Strassens Matrix Multiplication -BV1hhPXeTEWM_p38-

Hi， our next topic is Str matrix multiplication。This topic belongs to divide and conquer。

So Strat andmatics multiplication follows divide and conquer strategy。



![](img/4ffb19dedea7f70ce2528c177f2071d2_1.png)

First we will see how matrix multiplication is done normally。

 second thing we'll see how divide and conquer strategy can be applied for solving matrix multiplication problem。

Then third thing we'll see what Strasum has done for improving matrix multiplication using divide and conquer strategy。

Let us start with matrix multiplication， so I'll take some matterses。

 then we'll see how multiplication stop。

![](img/4ffb19dedea7f70ce2528c177f2071d2_3.png)

I have taken two matisees here， a with。Some elements。 So the order of this matrix says2 by 22 cross2。

 and this is also two cross2。 When we multiply two matrix says。

They can be multiplied if the number of columns of the first matrix are equal to number of rows or second matrix。



![](img/4ffb19dedea7f70ce2528c177f2071d2_5.png)

And the result and matrix will have this dimension。So the resultant matrix will also be2 cross2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_7.png)

Now this is two cross2 two cross two mat。 Now we have to multiply and get the third matrix that is C。

How we multiply this a simple problem。Any term of that C matrix that a C of I comma J is obtained by。

Some of。A of iK。And to be off。K J， where K takes the values from1 to this a dimension。

 If you call this as M to n M cross n， then this is1 to n。This是不钱都房。

For multiplying two mates of any dimensions here we are just taking an example of two cross two matrix where we want to multiply these two mates and get the result in matrix that is C matrix。

 if I use the general formula and write down the algorithm or a piece of code for multiplying twomates。

 let us see how the code looks like。

![](img/4ffb19dedea7f70ce2528c177f2071d2_9.png)

For preparing C matrix， I will take clues for IS sign0 I less than N I plus plus。4 J sign 0。

 J is less than N， J plus plus。Then third matrix C of i comma J is initialized to 0。

 then follow loop k assign values from0 and k is less than n k plus plus。

And C of Ia J is plus assignment。A of icona K N B of。



![](img/4ffb19dedea7f70ce2528c177f2071d2_11.png)

给讲界。Close this loop and this loop and this loop。If I write a simple algorithm for multiplying twomat。

 then it will be written like this using34 loops。

![](img/4ffb19dedea7f70ce2528c177f2071d2_13.png)

For accessing all the elements of any matrix， we actually require two follows。



![](img/4ffb19dedea7f70ce2528c177f2071d2_15.png)

Then here for finding the product each element C11。

 we obtain it by multiplying all the elements of a row with all the elements of a column。

 So for that we need acquire one more loop。

![](img/4ffb19dedea7f70ce2528c177f2071d2_17.png)

So that's how it is taking three for loops。 What will be the time complexity if three for loops are there now this statement is inside three for loops who are running for n times。

 then this will be N Q。So that I am taken for multiplying two matcees order of N cube。

 this is the simple method。Now let us try to adopt divide and conquer strategy for solving this one。

 so let us first observe what we can do such that we can apply divide and conquer strategy now let us see how divide and conquer strategy can be applied for multiplying twomat。



![](img/4ffb19dedea7f70ce2528c177f2071d2_19.png)

In divided conquer strategy， we say that if the problem is large。

 we break the problem into sub problems and solve those sub problems。

 combine the solutions of sub problems to get the solution for main problem。Now。

 when you say the problem is large， then you should also define what is a small problem。

If it is a small problem， we will directly solve it。Anyway， if the problem is large。

 we will break and break and break at one point， we have to say that this is small and we have to solve it。

So that's why， first of all， we will define a small problem。So in divide and conquer strategy。

 which size and matrix we should say is small， so we will say a two by2 that is two cross to matrix is small。

 multiplying two cross two mates is small if they are two cross two。

 then we will directly solve them。

![](img/4ffb19dedea7f70ce2528c177f2071d2_21.png)

If they are bigger than that， larger than that， if the dimensions are 4 by 4 or 8 by 8。

 any dimension， then we applied divided conquer strategy。 That is。

 we break the problem into some problems。 to see how to solve a small problem。

 Al we have here on board two mattices of order 2 by 2 to cross 2。

 And we have to get the reant matrix after multiplying them。 How we can get the terms of C matrix。

 all these terms。 Let us prepare them。

![](img/4ffb19dedea7f70ce2528c177f2071d2_23.png)

If I have to get c11， it can be obtained by multiplying a11。With。B1，1。And。A 1，2， but。B，2，1， A 1。

2 with B 2，1。

![](img/4ffb19dedea7f70ce2528c177f2071d2_25.png)

This is the first term， this one， then how to get this term。



![](img/4ffb19dedea7f70ce2528c177f2071d2_27.png)

C 1，2。 First row。 Second column。A 1，1， multiplied with B1，2 plus。A 1，2， multiplied with B2，2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_29.png)

We got this term now let us see how to get this term。

 that term is obtained by second row first column。

![](img/4ffb19dedea7f70ce2528c177f2071d2_31.png)

C 2，1 S A 2，1 into B1，1 plus A 2，2 into B2，1。

![](img/4ffb19dedea7f70ce2528c177f2071d2_33.png)

And how to get this term。

![](img/4ffb19dedea7f70ce2528c177f2071d2_35.png)

C 2，2 as second row， second column， A 2，1 into B，1，2 plus a 2，2 into B 2，2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_37.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_38.png)

That's it。 Now here。If the mates of order to cross to two mat。

 then we can multiply them by directly using these formulas。 Now。

 here for multiplying2 by two matrix， I am not using three4 loops here。

 but I am directly using the formula。 So if I save the time taken by this one。

 how much time it is taken。 So I can consider each statement is taking one unit of time。

 So total time is four unit of time。 That is constant。



![](img/4ffb19dedea7f70ce2528c177f2071d2_40.png)

If I say no no multiplications are there， you count them。 So 1，2，3，4，5，6，7，8。

 total 8 multiplications are there。 that is also constant，8 is constant。

 So anyhow these force formulas are constant。 Now this is defined as a small problem。And。

If you want to reduce the size and say if it is one by one matrix， then they will be having just one。

1 element， and just single product will be there。 That is。

 if imagine just this one element and this one element， I will draw this is a 1，1。 That's all。

 and B is。

![](img/4ffb19dedea7f70ce2528c177f2071d2_42.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_43.png)

B11。Then， see is。

![](img/4ffb19dedea7f70ce2528c177f2071d2_45.png)

A11 into B1，1。So I can say that if the dimensions are less than or equal to 2。

 then it's a small problem。 So if it is two by two， then these are the four formulas I will use。

 if it is one by one， then I will use this formula。 Direct multiplication is there。



![](img/4ffb19dedea7f70ce2528c177f2071d2_47.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_48.png)

All late。Now， what if it is greater than2 by2？Then I have to divide the problem into some problems。

 and solve them。So for that， I'll take some examples and explain you。

 but one important thing is as it is2 by 2， we assume that we assume that the mates are having the dimensions in powers of two only。

Like two by2 or four by4，8 by8，16 by 16。256 by 256， so the dimensions are in powers of 2。

 so that will be even we divide and divide we reach to the size of 2 by 2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_50.png)

Or if you further divide it， then you may go till up to one by one。If it is not of power 2 by2。

 then you can fill zeros and make it square matrix of powers of 2 by 2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_52.png)

Now， let me show you if it is4 by four， how we will apply dividend and conquer strategy。



![](img/4ffb19dedea7f70ce2528c177f2071d2_54.png)

Now here I have four by four mates， two four by four mates。And I say that this problem is large。

 that we have to divide the problem into sub problemsble and then solve those sub problems and combine the solution。

How I can do that。This is 4 by 4， and if you see the dimensions they are from one to four。

 rows are from one to four， columns are also from one to4。

So rows are starting from one ending at four， columns are starting at one and ending at4。

 so same way here also  one to  four and  one to four。Now。

 I say that this dimensions must be divided by two， so this matrix get splited into two。

By 2 Now I got four mattresses Similarlyly， this matrix also if I divide by 2。

 then it will be splited and we get four mattresses。



![](img/4ffb19dedea7f70ce2528c177f2071d2_56.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_57.png)

Now we got four mattresses of size 2 by 2， and that I will consider this matrix itself as an element a11。

So let us call that matrix as a11， and this matrix has a12。And second matrix。

Right and this also has a matrix that is a21 and a22。I can consider them like this。 Now， each。

 I should consider it as a matrix。 Then here also， I should say B1，1， B1，2， B2，1， B2，2。 Now。

 if I consider this matrix as a single element， then now this became what tomatics。😊。



![](img/4ffb19dedea7f70ce2528c177f2071d2_59.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_60.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_61.png)

Can't I solve this two by2 matrix directly， Yes， how does A 11 with B11 and A 12 with B21 and add them。

So yes， we follow the same form allow， even for multiplying these twomates。

 we treat this as a element。Now， let us look at the algorithm。

 how we can write a dividend conquer algorithm for multiplying two matches。

 I will call the algorithm name as。

![](img/4ffb19dedea7f70ce2528c177f2071d2_63.png)

嗯。MN， that is matrix multiplication， which will take A and B and dimension M。



![](img/4ffb19dedea7f70ce2528c177f2071d2_65.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_66.png)

Now the parameters can be anything， it is not a direct program you cannot directly convert what I am showing now。

 you cannot directly convert into a program， you have to define more things for making it as a program now to get the IM writing an algorithm。



![](img/4ffb19dedea7f70ce2528c177f2071d2_68.png)

See， if that n is less than or equal to 2 and dimensions are less than or equal to2。

 then directly you find out C by using those four formulas。



![](img/4ffb19dedea7f70ce2528c177f2071d2_70.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_71.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_72.png)

Right four formulas are there。 we can use those four formulas for getting C matrix。

 So if it is small， then actual multiplication will be done here。



![](img/4ffb19dedea7f70ce2528c177f2071d2_74.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_75.png)

Right， else， if it is large， then what we do here， we will split it and again join it。

 So let us see how we can split and then combine the solutions。 So here we find out mid。



![](img/4ffb19dedea7f70ce2528c177f2071d2_77.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_78.png)

That is and by2 we will do。 This is not a detailed code， I am saying。



![](img/4ffb19dedea7f70ce2528c177f2071d2_80.png)

RightNow， when you have divided the matrix by two every by two， both of them by two。

 if you have done， then you have to multiply these two mates as if these are elements。

 So you have to multiply these two plus these two。 So how you can do that is again。

 called the algorithm recursively matrix multiplication called the matrix multiplication bypassing this matrix。

 That is。

![](img/4ffb19dedea7f70ce2528c177f2071d2_82.png)

A 11 gama。B11。

![](img/4ffb19dedea7f70ce2528c177f2071d2_84.png)

And the dimension is N 2 plus。

![](img/4ffb19dedea7f70ce2528c177f2071d2_86.png)

Matic multiplication of。

![](img/4ffb19dedea7f70ce2528c177f2071d2_88.png)

A 1，2， V B，2，1。A 1，2， comma， B2，1， and dimensions are n by 2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_90.png)

See these lines， if I write them here， C 1，1 is obtained by multiplying this element。

With this element， actually， these are not elements。 These are matisees plus。A1，2 with B2，1。

 So this is matrix multiplication。 And again， we are using a formula for getting the first element。

 So we are treating these as elements。 But actually， those are mates。

 and we are applying the same formula。 So for multiplying these two。

 I am using a function matrix multiplication。 This is this will be getting the first term。

 Then again， next term。 So what that next term will be C1，2。 that is multiply this one with this one。

 first row with second column， right， So a1，1 with B， it will be M M A1。

1 comma and the dimensions are n by2 half。😊。

![](img/4ffb19dedea7f70ce2528c177f2071d2_92.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_93.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_94.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_95.png)

That's it。 See here I have written the recursive code。 So again。

 it is calling itself for the reduced size of mattresses。 So I am naming them as even 1 and B 11。

The remaining four。 So like this， when I said these are elements。 I again， four formulas apply here。

 So C 2，1， C 2，2， all these I have to write on。 So here it will be。



![](img/4ffb19dedea7f70ce2528c177f2071d2_97.png)

A21 and here it will be matrix multiplication of a21 another dimension is N2。

Then the last term is a 2，1 into B，1，2 plus a 2，2 width。



![](img/4ffb19dedea7f70ce2528c177f2071d2_99.png)

B，2，2。Mex multiplication of。B2，2， and send by2。Once again， when 4 by  four mates are given。

 for example， then they can be divided into small problems of sizes 2 by 2。

 and these 2 by 2 mates can be multiplied like this。

 So I have it on a dividend conquer algorithm here， which is recursively calling itself。

 If the dimensions are less than or equal to2 directly used those formulas。 Otherwise。

 it will call itself recursively。 and this plus is matrix addition。

 It is not normal integer addition。 It not skill or， It matrix addition。

 Now let analyze how much time this will take for execution。

 What is the time complexity of this algorithm。

![](img/4ffb19dedea7f70ce2528c177f2071d2_101.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_102.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_103.png)

Let us find a time complexity。 This is using divide and conquer strategy。

 So this is a recursive algorithm。 You can see that it is calling itself how many times it is calling itself 1。

2，3，4，5，6，7，8，8 times it is calling itself。 So let us prepare a recurrence solution for this one。

 Recurrence will be T N is equals 2。

![](img/4ffb19dedea7f70ce2528c177f2071d2_105.png)

It is calling itself on the reduced problem of n by 2 which is splitting by 2 right and we are assuming that the dimension of the mals are in powers of 2 t n by 2 t half half how many times it is calling8 times。



![](img/4ffb19dedea7f70ce2528c177f2071d2_107.png)

Plus。What is the work done for combining this addition， edition。

 I said that those are not normal scalar value additions。 Those are matrix addition。

 How much time it will take for adding dumat。 I suppose I have to add them。

 suppose then how much time each an element I pseudo corresponding element。

 So there are n square elements。 So time taken for adding S n square。



![](img/4ffb19dedea7f70ce2528c177f2071d2_109.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_110.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_111.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_112.png)

See， I should add this corresponding elements like this。 If I talk about only adding， right。

 only adding， then this is n square。 Time is n square。



![](img/4ffb19dedea7f70ce2528c177f2071d2_114.png)

So the time for combining is n square。

![](img/4ffb19dedea7f70ce2528c177f2071d2_116.png)

This is when n is greater than。

![](img/4ffb19dedea7f70ce2528c177f2071d2_118.png)

2， if n is less than or equal to2 than these just four formulas。

 How much time those formula takes we'd say it is one constant。That's it。 Does the re inulation。

Now if I apply master theorem on this one， a value is8。

 B value is a 2 and the function f of n is n squared find out log a base B that is log of a base2。

 it is 3， then what is power of n K K is n power 2， so K is 2。This is 3。 This is 2。

So logger base B is greater than k。 So then this comes under which case。 If I apply master theorem。

 this logger base B is greater， So it comes under case 1。

 Then what will be the time complexity of this one。 This will be。Ted off and cube。



![](img/4ffb19dedea7f70ce2528c177f2071d2_120.png)

The time complexity of divide conquer algorithm is also N cube。

 whether you use a simple algorithm by using three for loops Also is N cube。

 If you apply divide conquer also is N cube。 but the dividend conquer algorithm is recursive。

 So it internally uses a stack。 So that will be consuming extra space。 So in terms of space。

 if you see， then the algorithm with just three follow loops is better than divide conquer algorithm。



![](img/4ffb19dedea7f70ce2528c177f2071d2_122.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_123.png)

Now as this is taking more time compared to other algorithms we see mostly we have the time complexities like n square and loggan。

 so this N cube is there any chance is there any possibility to reduce the time of this algorithm so this is a research topic this is a research area if you can find out any faster method for multiplying twomates then that will be better for humanity。



![](img/4ffb19dedea7f70ce2528c177f2071d2_125.png)

So。What Strasson has done， Let us see。So now let us talk about stress。 see。

 we have seen this four formulas although they have shown you four formulas for multiplying twomates directly and those formulas I have used them here in the form of functions。

 recursive functions。 and in this you can see that there are total eight multiplications。



![](img/4ffb19dedea7f70ce2528c177f2071d2_127.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_128.png)

So what Strasson has done the major work inmatics multiplication is multiplication only so if we can reduce number of multiplications then that will make the algorithm faster。

 So this is the approach he has taken So instead for this8。

4 formulas with eight multiplications he has given different formulas instead of following those four he has given different formulas with seven multiplications。

Which will reduce the time complexity of Elgar little bit。Little less than in cube。

So let us see what he has given。 Look at Strasson's formula。

 These are the four formulas for directly multiplying two matisees for getting the third mats that is multiplying A B to get C。



![](img/4ffb19dedea7f70ce2528c177f2071d2_130.png)

With8 multiplications。 so these may be simple elements， or these may be mattresses。

 We have already seen divide and conquer method。Now， this is having eight multiplications。

 So what Strasson has done is he has reduced the number of multiplication。

 And one more thing is this additions are also there for additions。

 Ed or subtractions will take less time compared to multiplication。 Strasson's formula。

 if you see the number of multiplications are reduced。 No doubt。

 additions and subtractions has increased。 So here are his。



![](img/4ffb19dedea7f70ce2528c177f2071d2_132.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_133.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_134.png)

Here are his formulas。 Let us see what he has given。 He said that find out these formulas， P Q， R， S。

 T， U V， And that is involving these elements， A and B elements。 So if you see the multiplications。

 this is one multiplication， two multiplications，3 multiplication。



![](img/4ffb19dedea7f70ce2528c177f2071d2_136.png)

4，5，6，7。 So he has given7 of formulas named as P2 V with7 multis。

 And those formulas are utilized to get the elements that is C 1，2。



![](img/4ffb19dedea7f70ce2528c177f2071d2_138.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_139.png)

C2，2， C 1，1，2 C 22。 So instead of these four formulas for getting these values。

 So we have these formulas。 Now， what are these P Q R S C they are given here。



![](img/4ffb19dedea7f70ce2528c177f2071d2_141.png)

![](img/4ffb19dedea7f70ce2528c177f2071d2_142.png)

So thats all no doubt， the number of formulas has increased and number of additions and subtractions has increased。

 but the number of multiplications has reduced。 If you apply divide and conquer strategy。

 then the algorithm is called will be calling itself multiple times but total only 7 times instead of8 times。

 So what will be the recur solution for this one， that will be T n is equals to 7 T n by2 plus n square When n is greater than 2。

 when n is less than equal to2， it will be1。

![](img/4ffb19dedea7f70ce2528c177f2071d2_144.png)

This order recurrent solution has changed， and this is log 7 base2。 It will be to。Po81。And K is 2。

 So this is greater。 So it will be order of N power log 7 base 2 or。Ader of N power 2。81。



![](img/4ffb19dedea7f70ce2528c177f2071d2_146.png)

So Strasson has reduced the time complexityities not N cube， but N power 2。81。

 it is little less than n cube tall with Strins multiplications。



![](img/4ffb19dedea7f70ce2528c177f2071d2_148.png)