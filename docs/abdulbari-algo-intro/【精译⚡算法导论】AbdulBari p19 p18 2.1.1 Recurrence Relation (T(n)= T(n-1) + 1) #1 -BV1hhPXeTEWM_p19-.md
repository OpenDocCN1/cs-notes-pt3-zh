# 【精译⚡算法导论】AbdulBari p19 p18 2.1.1 Recurrence Relation (T(n)= T(n-1) + 1) #1 -BV1hhPXeTEWM_p19-

Hi， in this video we'll learn how to trace the recursive function and how to write a recurrennce and how to solve a recurrence solution。

 So I am taking one of the example then in the other videos you can find following examples more examples will come in other videos。



![](img/9c51213eff7d43928c4b66b933cf6733_1.png)

Let us start already I have an algorithm， a function here， a C language function I have written。

 you call it as algorithm also。

![](img/9c51213eff7d43928c4b66b933cf6733_3.png)

Test is a function， which is taking n as input。 And if n is greater than 0， it is printing the value。

 and then it is calling itself for n -1。

![](img/9c51213eff7d43928c4b66b933cf6733_5.png)

So I will take some sample value and test it， suppose。



![](img/9c51213eff7d43928c4b66b933cf6733_7.png)

I'm calling this function by passing three。

![](img/9c51213eff7d43928c4b66b933cf6733_9.png)

Let us see what happens if we pass3。

![](img/9c51213eff7d43928c4b66b933cf6733_11.png)

Test。

![](img/9c51213eff7d43928c4b66b933cf6733_13.png)

3。3 is greater than 0。 Yes，3 is greater than 0。 Pri 3， so it will print 3。



![](img/9c51213eff7d43928c4b66b933cf6733_15.png)

Then call itself  for3 minus-1。 That is 2。 So call test。Do。Then for two， again。

 it's a recursive call。 So for this call， it will print two and call itself for one。

1 is greater than 0。 So it's a recursive call。 again， for this one， as it is greater than 0。

 it will print  one and call itself for test0。

![](img/9c51213eff7d43928c4b66b933cf6733_17.png)

Now when it is0，0 is not greater than0， so it will not call itself and it will stop。



![](img/9c51213eff7d43928c4b66b933cf6733_19.png)

Doesn't go further。

![](img/9c51213eff7d43928c4b66b933cf6733_21.png)

So this is a tracing tree for this particular function， or recursive function。



![](img/9c51213eff7d43928c4b66b933cf6733_23.png)

I have passed to three。

![](img/9c51213eff7d43928c4b66b933cf6733_25.png)

So what is the time taken by this one， So let us see what it is doing。 in this call。

 it is printing a value。

![](img/9c51213eff7d43928c4b66b933cf6733_27.png)

Then calling again， printing a value and calling again， Pri a value and calling again。

 So the amount of work done is just printing value。 How many times it is printing。

 This is the major work done by this function， Pri a value。



![](img/9c51213eff7d43928c4b66b933cf6733_29.png)

![](img/9c51213eff7d43928c4b66b933cf6733_30.png)

![](img/9c51213eff7d43928c4b66b933cf6733_31.png)

![](img/9c51213eff7d43928c4b66b933cf6733_32.png)

How many times it is doing， three times it is doing as I have passed three。



![](img/9c51213eff7d43928c4b66b933cf6733_34.png)

How many times it is calling itself， as I have given three it is calling itself for four times。



![](img/9c51213eff7d43928c4b66b933cf6733_36.png)

Now， what is the time taken for printf。 It is just one unit of time。

 Just it is a single statement a simple statement。 It is taking one unit of time。

 If I say one unit of time， then in each call， it is pending one unit of time that is printing and then calling。

 So one unit of time， one unit of time。

![](img/9c51213eff7d43928c4b66b933cf6733_38.png)

![](img/9c51213eff7d43928c4b66b933cf6733_39.png)

![](img/9c51213eff7d43928c4b66b933cf6733_40.png)

So total how much time it has taken three。If I take number of calls。

 then there are 4 that is 3 plus  one。

![](img/9c51213eff7d43928c4b66b933cf6733_42.png)

It means if we pass 5， then it will be 5 plus 1 calls， and 5 is the number of time。 It is will。

 It will print。So if I pass n， then total harm manyy calls it will make。

 it will make n plus1 calls n plus1 calls。

![](img/9c51213eff7d43928c4b66b933cf6733_44.png)

![](img/9c51213eff7d43928c4b66b933cf6733_45.png)

And how many times printer is executed n times。If I approximate the amount of work done depends on the number of calls。

 if I say， like in the last call， it is not printing。

 just ignore that and say that for every call it is printing so the time depends on what it depends on the number of calls。

 So how many calls it will make for any N it will make N1 calls。



![](img/9c51213eff7d43928c4b66b933cf6733_47.png)

So the time function， if I write F of n， then it is n plus 1。

 Then what is the time complexity in notations， its order of n。



![](img/9c51213eff7d43928c4b66b933cf6733_49.png)

![](img/9c51213eff7d43928c4b66b933cf6733_50.png)

I can use Vigoofphan， Taate ofn or omega oftenn， anything I can write there。



![](img/9c51213eff7d43928c4b66b933cf6733_52.png)

This， we have already discussed in previous videos。So that's it by a tracing tree。

 I have found the time complexity of this one。You can also call it as a recursive tree or a tracing tree or a recursive tree I have used。



![](img/9c51213eff7d43928c4b66b933cf6733_54.png)

Now let us find out how to prepare a recurrent solution for this function and how to solve that recurrent solution。

 Now if any function or an algorithm is given to you。

 you can prepare a recurrent solution as follows like this I am showing you。



![](img/9c51213eff7d43928c4b66b933cf6733_56.png)

![](img/9c51213eff7d43928c4b66b933cf6733_57.png)

Assume that the time taken by this is F of N。 No， usually for recurrennce solution。



![](img/9c51213eff7d43928c4b66b933cf6733_59.png)

![](img/9c51213eff7d43928c4b66b933cf6733_60.png)

Function name is a T。 That is a T of n S U。 So I'll use the same thing。 So instead of F of N。

 I'll call it as T of n time taken by this algorithm as T N or this function is T N。



![](img/9c51213eff7d43928c4b66b933cf6733_62.png)

![](img/9c51213eff7d43928c4b66b933cf6733_63.png)

Then that Tn will be equal to what the total amount of time taken by this one。



![](img/9c51213eff7d43928c4b66b933cf6733_65.png)

So let us observe what is happening inside conditiondition is checked。Let us ignore condition。

Inside that printer is there。1， it will take one unit of time。The next， what is the next one。

 It a recurs call。 It's the same thing。 How much time we mention for this T N then what will be the time for this one。



![](img/9c51213eff7d43928c4b66b933cf6733_67.png)

![](img/9c51213eff7d43928c4b66b933cf6733_68.png)

D， N-1。

![](img/9c51213eff7d43928c4b66b933cf6733_70.png)

Pight。Now， that's it。 So what is the total time T N。

 I said that the total time taken by this part of an algorithm so that T N is equals to T N-1 plus1。



![](img/9c51213eff7d43928c4b66b933cf6733_72.png)

![](img/9c51213eff7d43928c4b66b933cf6733_73.png)

![](img/9c51213eff7d43928c4b66b933cf6733_74.png)

Now， you can ask me why you have ignored condition。



![](img/9c51213eff7d43928c4b66b933cf6733_76.png)

Say if I consider that condition also for one time， then it is just one condition。 So one time。

 then I'll get two here。 If I take two also， then the result of this result of this expression will be same only for the recurrent solution。

 I'll get the same answer。 So if you have any constant value。

 you can simply make it as one and use it。

![](img/9c51213eff7d43928c4b66b933cf6733_78.png)

![](img/9c51213eff7d43928c4b66b933cf6733_79.png)

![](img/9c51213eff7d43928c4b66b933cf6733_80.png)

Or if you can write it as C also and use it constant or some a as a constant。

 some constant also you can write and use it， so I prefer taking it as one。

So if you have more than one， then you can ground it up to one only。あだて。

This is the way we write a cancellation。

![](img/9c51213eff7d43928c4b66b933cf6733_82.png)

Now let us write a recurrent solution。DM。Is equals2。



![](img/9c51213eff7d43928c4b66b933cf6733_84.png)

T N-1 plus 1。 This one， when， when n is greater than 0， Yes， when n is greater than 0 is the time。



![](img/9c51213eff7d43928c4b66b933cf6733_86.png)

What happens if n is equals to 0， It's not doing anything if n is equals to 0。

 So if n is equals to 0， it is not doing anything。 shall shall I write 0 here。 No。

 the time we don't write it 0。 If it is 0。 Also， it's a constant， So we write it as one。

 So I will take it as one， or else you can make it as C or A or K， anything。

 Some constant you can write。

![](img/9c51213eff7d43928c4b66b933cf6733_88.png)

![](img/9c51213eff7d43928c4b66b933cf6733_89.png)

![](img/9c51213eff7d43928c4b66b933cf6733_90.png)

![](img/9c51213eff7d43928c4b66b933cf6733_91.png)

![](img/9c51213eff7d43928c4b66b933cf6733_92.png)

Now， let us solve this recur solution。Now let us solve this recurnceulation by substitution method back substitution。

 we will follow。

![](img/9c51213eff7d43928c4b66b933cf6733_94.png)

![](img/9c51213eff7d43928c4b66b933cf6733_95.png)

Let us take this。This is T N is equal to T N-1 plus 1。 We will solve this one。



![](img/9c51213eff7d43928c4b66b933cf6733_97.png)

That is already solve。 It is one。 we have to solve this one。



![](img/9c51213eff7d43928c4b66b933cf6733_99.png)

Now， for solving this。I can know the answer for Tn if I know what is Tn minus-1。



![](img/9c51213eff7d43928c4b66b933cf6733_101.png)

So what is Tn minus-1？

![](img/9c51213eff7d43928c4b66b933cf6733_103.png)

What is this？If I know， I will use it here。So I don't know T n -1， but I know what is a T N。

 T N is equals to T n-1 plus 1。 Yes， this is the one。 then what will be Tn -1。 So if this is n my n。

 and it is changed to n -1。 So this also n -1。 So this becomes n -1 -1 n-2 plus1。 Okay。

 since this is T N， therefore Tn -1 is this1。

![](img/9c51213eff7d43928c4b66b933cf6733_105.png)

![](img/9c51213eff7d43928c4b66b933cf6733_106.png)

![](img/9c51213eff7d43928c4b66b933cf6733_107.png)

No。

![](img/9c51213eff7d43928c4b66b933cf6733_109.png)

Substitute T N -1 in this equation。 So T N is equals to in bracket。 I'll write this T and -1。

 So what I got T N-2 plus 1 and plus 1。 So this part I have substituted here at this place。



![](img/9c51213eff7d43928c4b66b933cf6733_111.png)

![](img/9c51213eff7d43928c4b66b933cf6733_112.png)

So， I got this one。

![](img/9c51213eff7d43928c4b66b933cf6733_114.png)

Then this is T， N is equal to T N-2 plus 2，1 plus 1，2。If I substitute again。

 then T N is equals to what will be T n -2 T N-3 plus 1。See this T N-2 will be equal to T N-3 plus 1。

 Yes， I have substituted this portion here。

![](img/9c51213eff7d43928c4b66b933cf6733_116.png)

![](img/9c51213eff7d43928c4b66b933cf6733_117.png)

Right at this place。 So I have written on this。 then plus two is as it is。 Now。

 if I solve this one again， then T N is equals to T N-3 plus 3。That's what I got。

So how many times I should do this？See， when I got two times that is sufficient。

 you can continue further。 and I say that I am going to continue this。

 How long for k times continue for k times。

![](img/9c51213eff7d43928c4b66b933cf6733_119.png)

![](img/9c51213eff7d43928c4b66b933cf6733_120.png)

If I continue for k times what I get。 See if you observe when I did for one time， it was two。

 next time it was 3， then it goes on。 So it will be K。



![](img/9c51213eff7d43928c4b66b933cf6733_122.png)

![](img/9c51213eff7d43928c4b66b933cf6733_123.png)

So this will be T N is equals to T n minus k plus k。



![](img/9c51213eff7d43928c4b66b933cf6733_125.png)

![](img/9c51213eff7d43928c4b66b933cf6733_126.png)

So this is the important one for me now。

![](img/9c51213eff7d43928c4b66b933cf6733_128.png)

I'll continue here。 What is the equation I got。

![](img/9c51213eff7d43928c4b66b933cf6733_130.png)

T N is equals to T， N minus。

![](img/9c51213eff7d43928c4b66b933cf6733_132.png)

K plus k。

![](img/9c51213eff7d43928c4b66b933cf6733_134.png)

See， it was T N -1 plus 1 substituted。 I got T N-2 plus 2 substituted。

 I got T N -3 plus 3 Con up to K。 So T and minus k plus k this one。



![](img/9c51213eff7d43928c4b66b933cf6733_136.png)

![](img/9c51213eff7d43928c4b66b933cf6733_137.png)

![](img/9c51213eff7d43928c4b66b933cf6733_138.png)

So I said that I will stop at k K in some some steps after some steps， I will stop after k steps。

 k substitutions， I will stop。

![](img/9c51213eff7d43928c4b66b933cf6733_140.png)

No。What is the smaller value I know。 I know n is equals to 0。 If n is equals to 0。

 I know it is 1 answer is 1。 So here n-1 was there。 So -2 then 3 then 4。

 if you go on subtracting like this at one point， it should become 0。

 So that my purpose was to substitute go on substitute and reach still n equal to 0。

 So I assume that I have reach at 0。 So I assume this。



![](img/9c51213eff7d43928c4b66b933cf6733_142.png)

![](img/9c51213eff7d43928c4b66b933cf6733_143.png)

![](img/9c51213eff7d43928c4b66b933cf6733_144.png)

![](img/9c51213eff7d43928c4b66b933cf6733_145.png)

![](img/9c51213eff7d43928c4b66b933cf6733_146.png)

![](img/9c51213eff7d43928c4b66b933cf6733_147.png)

![](img/9c51213eff7d43928c4b66b933cf6733_148.png)

And minus k is 0。 Al as you does means I have reached till there。

 When I say n minus k is equals to 0， therefore， n is equals to k。



![](img/9c51213eff7d43928c4b66b933cf6733_150.png)

![](img/9c51213eff7d43928c4b66b933cf6733_151.png)

Then what this will be。 This will be T， N is equals to T n minus N plus N。



![](img/9c51213eff7d43928c4b66b933cf6733_153.png)

Then T N is equals to what is this t 0 plus n。 So this is what is the t 0， T 0， We already know it。

 It is one plus n。

![](img/9c51213eff7d43928c4b66b933cf6733_155.png)

![](img/9c51213eff7d43928c4b66b933cf6733_156.png)

That's it。 It is solved。What the answer I got， you see1 plus n is the time。

 So just now I have shown you how we can prepare a recursive tree and find a time for that algorithm。

 Actually， I made it racing as well as along with that recursive tree。

 So there also I got n plus one calls here。 Also I' am getting the answer as n plus1。



![](img/9c51213eff7d43928c4b66b933cf6733_158.png)

![](img/9c51213eff7d43928c4b66b933cf6733_159.png)

![](img/9c51213eff7d43928c4b66b933cf6733_160.png)

So I have prepared a recurrenceciation， solve that recurrenceciation。 And I got this answer。

 And this is， again， order of N。 See， Actually， this belongs to a class linear class order of n。

 that is N。 So I can call it as theta of N。

![](img/9c51213eff7d43928c4b66b933cf6733_162.png)

![](img/9c51213eff7d43928c4b66b933cf6733_163.png)

That's it。 Theres the first recurnce， So I will show you more and more recurrennce。

 So Ill take the program。 I will prepare the recurrennce solution， and I will solve it。



![](img/9c51213eff7d43928c4b66b933cf6733_165.png)

![](img/9c51213eff7d43928c4b66b933cf6733_166.png)

So continue watching rest of the videos。

![](img/9c51213eff7d43928c4b66b933cf6733_168.png)