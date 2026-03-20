# 【精译⚡算法导论】AbdulBari p78 p77 Asymptotic Notations - Simplified -BV1hhPXeTEWM_p78-

Hi， this video is about asymptootic notations。

![](img/b63ae23805a391f21d808ef8675da3d7_1.png)

Asymmptotic notations are used for representing the time complexity of es。



![](img/b63ae23805a391f21d808ef8675da3d7_3.png)

If we analyze the algorithms。

![](img/b63ae23805a391f21d808ef8675da3d7_5.png)

By studying and finding the frequency of execution of their statements。



![](img/b63ae23805a391f21d808ef8675da3d7_7.png)

Then we may get the time complexities Anyone among these like the time complexity may be constant。

 or it may be logarithmic， so that is in terms of login。



![](img/b63ae23805a391f21d808ef8675da3d7_9.png)

![](img/b63ae23805a391f21d808ef8675da3d7_10.png)

Or linear。 Or it may even be。

![](img/b63ae23805a391f21d808ef8675da3d7_12.png)

Anloggan。Or it may be quadratic and square and cube to power。



![](img/b63ae23805a391f21d808ef8675da3d7_14.png)

So these are some of the time complexities。Nontime complexities， any algorithm we take。

The time complexity of the teleorth may be。Anyone among these or the combination of these multiples of these。

So before going to asymptotic notations。Let us look at few algorithms。

And try to find the time complexities for them。Method for finding the time comp it is。

We will find the frequency of execution of statements， like in this algorithm。

 there is only one statement， and the time for execution is one， so it is constant。

If you say F ofn is the function for time。Then we get the value as one。Now this algorithm。

 if you take， this statement we will execute for one time。This will execute for n plus one time。

 and this is n times。This one will execute for one time。

 This fall loop will execute for n plus one time because one to n。

 Then when it is n plus one that time it will stop。 So total n plus one times。 So this gives。



![](img/b63ae23805a391f21d808ef8675da3d7_16.png)

2， n plus 3。So when we find the time complexity by just studying the algorithm state by best statement。

 we get the time in the form of a polynomial。

![](img/b63ae23805a391f21d808ef8675da3d7_18.png)

Right， so2 n plus 3 this。If you see the degree of polynomial， the highest degree is n。

 so the time complexity is linear。

![](img/b63ae23805a391f21d808ef8675da3d7_20.png)

If you take the cell go them。

![](img/b63ae23805a391f21d808ef8675da3d7_22.png)

This is endless one。This is inside the for loop， so this is n。

And this itself will execute for n plus one times， and this will execute for n square times。



![](img/b63ae23805a391f21d808ef8675da3d7_24.png)

So， this will be。2 n square。Plus，2 n。Plus one。So， F of n is。2 n squared plus 2 n plus 1。

The highest degree of polynomial is n square。 so the time complexity is。



![](img/b63ae23805a391f21d808ef8675da3d7_26.png)

Cdratic。

![](img/b63ae23805a391f21d808ef8675da3d7_28.png)

If we take the algorithm for matrix multiplication。



![](img/b63ae23805a391f21d808ef8675da3d7_30.png)

This is n plus one。This is N N to n plus1。This is1。 sorry， this is n squared times。



![](img/b63ae23805a391f21d808ef8675da3d7_32.png)

And this is。N square into N one。Andice is and cube。



![](img/b63ae23805a391f21d808ef8675da3d7_34.png)

So this is 2 n cube。Plus3 n square。Plus，2。

![](img/b63ae23805a391f21d808ef8675da3d7_36.png)

Plus one。So， the function of time。S。So and so we got this polynomial and the highest degrees N cube。

 So the time complexity is cubic。

![](img/b63ae23805a391f21d808ef8675da3d7_38.png)

Here I have binary search algorithm。

![](img/b63ae23805a391f21d808ef8675da3d7_40.png)

This is one。 This is one。And this loop will repeat as long as I is less than J。

 So I is 1 n j is n and it is going to divide I plus j by 2 every time。

 so it will be taking the middle。

![](img/b63ae23805a391f21d808ef8675da3d7_42.png)

![](img/b63ae23805a391f21d808ef8675da3d7_43.png)

So it will be dividing the inds i to j by 2。So， this will repeat for。



![](img/b63ae23805a391f21d808ef8675da3d7_45.png)

Login time， entire thing。 So all the statement inside this will execute for login time。

Either this or this statement would execute any one of them。So finally， it is。3 login plus 2。So。

 we got the function。S so and so。 So this is the highest degree。 So this is。Lomic。



![](img/b63ae23805a391f21d808ef8675da3d7_47.png)

Here I have taken a recursive function。

![](img/b63ae23805a391f21d808ef8675da3d7_49.png)

If the time for this is T N。

![](img/b63ae23805a391f21d808ef8675da3d7_51.png)

This is one。This will be。TN， because its a recursive call。 it is calling itself for n -1。

This is also Tn -1。So。Total time is。2 T0-1 plus1。

![](img/b63ae23805a391f21d808ef8675da3d7_53.png)

Does a requireulation。If you saw this recurrence relation。Then we get the time mass。To part n。

Highest degree in a function will be to per。 I will not show how to solve this one。

You can watch it in other videos。To foreign。 So the time complexity is。Exponential。



![](img/b63ae23805a391f21d808ef8675da3d7_55.png)

So。We can say that the time complexities will be one among these。



![](img/b63ae23805a391f21d808ef8675da3d7_57.png)

Constant locked the manline or quadratic or multiple of these。



![](img/b63ae23805a391f21d808ef8675da3d7_59.png)

I have taken all those time complexities in the increasing order。



![](img/b63ae23805a391f21d808ef8675da3d7_61.png)

No。If for any algorithm。We got the time complexity， as。F of n， z equals。2 n square plus3 n plus 2。

 supposeupp we got this as a polynomial。And the highest degree in this one is n square。Then。

We say that。All these time complexities。Including n square。Becomes。Upper bound of。Functionally for。



![](img/b63ae23805a391f21d808ef8675da3d7_63.png)

And all these time complexities。Including and square。



![](img/b63ae23805a391f21d808ef8675da3d7_65.png)

Becomes。Luerbang。An n square itself becomes。

![](img/b63ae23805a391f21d808ef8675da3d7_67.png)

Dight bond。Now here。So it means we can say f of n is。Big o off。



![](img/b63ae23805a391f21d808ef8675da3d7_69.png)

And square。Upper bound is represented using P O。This is one of the asymptootic mutation。

So even if oftenn can be written as biggoov and cube， Yes true， this is also true。F of n is。Big off。

To boring。As this is also true。So all these statements are true。



![](img/b63ae23805a391f21d808ef8675da3d7_71.png)

We can write any one of these。 We can write all the。



![](img/b63ae23805a391f21d808ef8675da3d7_73.png)

Time complexities。Greateater than and square。

![](img/b63ae23805a391f21d808ef8675da3d7_75.png)

Here I have taken the time complexities and the increasing order of their values。



![](img/b63ae23805a391f21d808ef8675da3d7_77.png)

Suppose the time complexity of an algorithm is given in the form of this。



![](img/b63ae23805a391f21d808ef8675da3d7_79.png)

2 n square plus 3 n plus1。Then the highest degree of this polynomial is n squared。



![](img/b63ae23805a391f21d808ef8675da3d7_81.png)

So all the time complexities greater than equal to n squared comes under。Up by a bound。



![](img/b63ae23805a391f21d808ef8675da3d7_83.png)

All the time complexlicities smaller than equal to n square comes under。Lower bound。



![](img/b63ae23805a391f21d808ef8675da3d7_85.png)

Now， N squared is coming in both。 So this becomes。

![](img/b63ae23805a391f21d808ef8675da3d7_87.png)

Dig棒。

![](img/b63ae23805a391f21d808ef8675da3d7_89.png)

It means。I am making asytootic notations very simple。Here， it means that。



![](img/b63ae23805a391f21d808ef8675da3d7_91.png)

F fourth N is。

![](img/b63ae23805a391f21d808ef8675da3d7_93.png)

Biggo of and square。 So biggo is used for upper bound。



![](img/b63ae23805a391f21d808ef8675da3d7_95.png)

I often。Can also be called as。Big go off and cube。And even because of。



![](img/b63ae23805a391f21d808ef8675da3d7_97.png)

2 par n， I can take any of the time complexities as upper bound that are greater than or equal to n square。

Now， coming to lower Bo。F of n is。Oomega of n squared， this is lower bound。



![](img/b63ae23805a391f21d808ef8675da3d7_99.png)

And even if often， can be called as omega of。En。Or omega。



![](img/b63ae23805a391f21d808ef8675da3d7_101.png)

loggan。So all the time complex that are smaller than n square comes under lower bound。



![](img/b63ae23805a391f21d808ef8675da3d7_103.png)

All these statements are true。So upper bound or lower bound of a function。

Is checked only in these known time complexities when they are arranged in the increasing order。



![](img/b63ae23805a391f21d808ef8675da3d7_105.png)

![](img/b63ae23805a391f21d808ef8675da3d7_106.png)

So if the time complexity for a function， the highest degree gives something。

 then all the time complexity is greater comes under upper bound and all smaller comes under lower bound。



![](img/b63ae23805a391f21d808ef8675da3d7_108.png)

![](img/b63ae23805a391f21d808ef8675da3d7_109.png)

No。F of N is。Big off and square。As well as。F of n is。



![](img/b63ae23805a391f21d808ef8675da3d7_111.png)

Omega n squared。So when it is same for both big and omega， then f of n is。



![](img/b63ae23805a391f21d808ef8675da3d7_113.png)

Ted off and square。Next all。

![](img/b63ae23805a391f21d808ef8675da3d7_115.png)

If I take one function。F of n is equals2。

![](img/b63ae23805a391f21d808ef8675da3d7_117.png)

N plus 5。 suppose this the time complexity。Then。

![](img/b63ae23805a391f21d808ef8675da3d7_119.png)

All these。Time complexity is greater than or equal to n comes under upper bound for this function。



![](img/b63ae23805a391f21d808ef8675da3d7_121.png)

And all these time complicity is smaller than equal to n comes under lower bound for this function。



![](img/b63ae23805a391f21d808ef8675da3d7_123.png)

![](img/b63ae23805a391f21d808ef8675da3d7_124.png)

Now let us see how we define asymptootic notation， the formal way of defining asymptotic notations。



![](img/b63ae23805a391f21d808ef8675da3d7_126.png)

We say that。F fourth N is biggo of G of n。If and only if there exists a positive constant C。



![](img/b63ae23805a391f21d808ef8675da3d7_128.png)

And。N n or n0。Such that。F of n is less than or equal to。



![](img/b63ae23805a391f21d808ef8675da3d7_130.png)

C and2。G of n for all values of n greater than equal to n 0。



![](img/b63ae23805a391f21d808ef8675da3d7_132.png)

Where c and n0 are positive constant， this is the way a big old notation is defined。

As a formal way of defining Bego。Now， if you follow the same way and try to get the answer， then。

If a fourth n is。2 n square。Plus，3 n plus 1。Then， we can say that。



![](img/b63ae23805a391f21d808ef8675da3d7_134.png)

If I make all these as n squares。3 n square plus n square。 Then I get this as。



![](img/b63ae23805a391f21d808ef8675da3d7_136.png)

6 and square。 so I can say that。F of n。That is 2 n square plus3 n plus 1。

Is less than or equal to 6 n squared for some values of n。



![](img/b63ae23805a391f21d808ef8675da3d7_138.png)

You can find some value here。For studying value of n， for some value of n， this will be true。

 this will be smaller than this one， and from that value of n。

 if you take any value greater than that， this will be true。



![](img/b63ae23805a391f21d808ef8675da3d7_140.png)

![](img/b63ae23805a391f21d808ef8675da3d7_141.png)

So now here， this is F of n。And this is less than equal to this is C，6 is C， and this is G of n。



![](img/b63ae23805a391f21d808ef8675da3d7_143.png)

So what is G of G of n is。And square。So， we see。Fness。B of。G ofn。



![](img/b63ae23805a391f21d808ef8675da3d7_145.png)

From the definition， if you see。C of n f sorry f of n is less than equal to c to G of n。

 So here we got f of n is equal is less than equal to G of n。

 So this is f of n that is less than equal to C to G of n， So G of n is n square。



![](img/b63ae23805a391f21d808ef8675da3d7_147.png)

Even I can write it like this。If F of n is equals to2 n squared plus。3 n plus 1。

Then I can replace this width。2 into2 per n plus 3 into2 pour n plus sorry。



![](img/b63ae23805a391f21d808ef8675da3d7_149.png)

2 par n。 And this also2 par n。So， this total is。2，4，5。62 bar n。So， F of n is。

2 n squared plus 3 n plus 1 is less than equal to6 n22 per n。 Yes， it is true。

For some starting value of n。Onwards。He has thisstr。



![](img/b63ae23805a391f21d808ef8675da3d7_151.png)

So I can say that this is a forn。Less than equal to， this is C。And this is G of n。

So why can we can write F of n as。Equal to big of。2 par n。 So even this is true。

 Like in the beginning， I told you that any time complexity greater than equal to n square comes under。



![](img/b63ae23805a391f21d808ef8675da3d7_153.png)

![](img/b63ae23805a391f21d808ef8675da3d7_154.png)

Bgo， that is upper bound for n square。

![](img/b63ae23805a391f21d808ef8675da3d7_156.png)

Now， let us look at。后面一个。Notation， so that is lower bound。



![](img/b63ae23805a391f21d808ef8675da3d7_158.png)

If F of n， okay， formal definition for this one is。F of n S。Omega of G ofn。

If and only if that exist C。And n0 as positive integers。And。A。

Greater than equal to some constant into G of n。For all values of n greater than equal to n0。

Let us take an example。

![](img/b63ae23805a391f21d808ef8675da3d7_160.png)

If a offend is。2 n square plus3 n plus 1。Then here， I will make this as just and square。



![](img/b63ae23805a391f21d808ef8675da3d7_162.png)

So I can say2 n square plus。3 n plus 1 is greater than equal to and square for。Some value off。

For all values of n greater than。Some value， some starting value。You can find that starting value。

Now here。This is a for。This is geon。And there is some constant here。 Constant is one。

So G of n is n squared。 So we can say f of n as。

![](img/b63ae23805a391f21d808ef8675da3d7_164.png)

Oomega and square。

![](img/b63ae23805a391f21d808ef8675da3d7_166.png)

F fair。

![](img/b63ae23805a391f21d808ef8675da3d7_168.png)

Yeah for f of n， we got the answer as big of n square， and even we got omega of n square。

 and we can say that。

![](img/b63ae23805a391f21d808ef8675da3d7_170.png)

![](img/b63ae23805a391f21d808ef8675da3d7_171.png)

F of n is big of n squared， as well as F of n is。Oomega n squared。



![](img/b63ae23805a391f21d808ef8675da3d7_173.png)

So， f of n is。

![](img/b63ae23805a391f21d808ef8675da3d7_175.png)

Theta of and square。 I'll not give the final that is formal definition of theta notation。

 You may be knowing well。You can find it in your book。

So that's how we find the time complexities that is sorry we find the asymptootic notations。



![](img/b63ae23805a391f21d808ef8675da3d7_177.png)

So symtic notations are nothing but just the upper bound， a lower bound and tight bound。



![](img/b63ae23805a391f21d808ef8675da3d7_179.png)

Now， let us take one example。If F forn is n factorial。

 we got the time complexity of some function in。Have some algorithm as n factororial。

Then what is the bound for this？In fact， real is not in the list。



![](img/b63ae23805a391f21d808ef8675da3d7_181.png)

Now， if we try to find a larger function， then actual n factorial is n into2 n minus1 into n minus2。

Into。Suan。

![](img/b63ae23805a391f21d808ef8675da3d7_183.png)

2 and one。Now for finding greater value upper bound， I will make all of these as n。

So this is n par n。So f of n that is n factorial is less than or equal to n power n for some values of n greater than equal to some starting value。



![](img/b63ae23805a391f21d808ef8675da3d7_185.png)

![](img/b63ae23805a391f21d808ef8675da3d7_186.png)

Yes， this is true。So， F of n is。Big off。N power n。Now， I want to find。

Smaller value for n factorial where n factor。 that is lower bound for n factorial。

 N factorial is n into n -1。

![](img/b63ae23805a391f21d808ef8675da3d7_188.png)

![](img/b63ae23805a391f21d808ef8675da3d7_189.png)

N to n，-2。

![](img/b63ae23805a391f21d808ef8675da3d7_191.png)

Into so on。En to2 comma1。What value I should place here， If I keep n。

 then it's going to be N power n。

![](img/b63ae23805a391f21d808ef8675da3d7_193.png)

If I keep login。Or the smallest value if I keep。

![](img/b63ae23805a391f21d808ef8675da3d7_195.png)

Wan。Then all these will be1，1 into1 into one into one， so on。 So this is one。 So finally， it is one。

So we get the answer as F of n is。Oomega of1。

![](img/b63ae23805a391f21d808ef8675da3d7_197.png)

From here， we can say that by looking at this。

![](img/b63ae23805a391f21d808ef8675da3d7_199.png)

Biggo of FO Fness and power N。But， omega is one。

![](img/b63ae23805a391f21d808ef8675da3d7_201.png)

In the previous examples， we were getting。

![](img/b63ae23805a391f21d808ef8675da3d7_203.png)

Oomega also。Example， we got omega also n square， a big also n square and omega also n square。

 So we set theta is n square。 But this in in this example。



![](img/b63ae23805a391f21d808ef8675da3d7_205.png)

Omega and。Bgo are different， biggo is empower and omega is 1。Even if I take make this as logins。

 so this will be login into login。Into goes on。Logan。So this will be。N times， login。So， F of n。As。

Oomega of。

![](img/b63ae23805a391f21d808ef8675da3d7_207.png)

N log n。Gs， this is also true。 Even if for n is omega of n is also true， and n log n is also true。

 Both are true。

![](img/b63ae23805a391f21d808ef8675da3d7_209.png)

![](img/b63ae23805a391f21d808ef8675da3d7_210.png)

We can see that this n power n is not equal to。1， and even it is not equal to n log n。

 So there is no theta for n factorial。 So this n factorial doesn't have。



![](img/b63ae23805a391f21d808ef8675da3d7_212.png)

![](img/b63ae23805a391f21d808ef8675da3d7_213.png)

Tight bone。

![](img/b63ae23805a391f21d808ef8675da3d7_215.png)

So there are some functions which may not have a tide bound。

So that may have only upper bound or lower bond。 we may be able to find only upper bound or lower bond。

 but we cannot find a tight bond。

![](img/b63ae23805a391f21d808ef8675da3d7_217.png)

![](img/b63ae23805a391f21d808ef8675da3d7_218.png)

Like for the previous function， we were able to find the lower bound， upper bound。

 as well as the tight bound。 So tide bound is one where you get omega and big both as same value。



![](img/b63ae23805a391f21d808ef8675da3d7_220.png)

![](img/b63ae23805a391f21d808ef8675da3d7_221.png)

Hope you have understood a symptomotic notation。 Please leave a comment so that I can improve the videos。



![](img/b63ae23805a391f21d808ef8675da3d7_223.png)