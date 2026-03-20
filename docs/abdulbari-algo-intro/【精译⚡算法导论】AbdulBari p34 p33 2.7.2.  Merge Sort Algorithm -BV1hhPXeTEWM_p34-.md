# 【精译⚡算法导论】AbdulBari p34 p33 2.7.2.  Merge Sort Algorithm -BV1hhPXeTEWM_p34-

![](img/00bf5453a8764569b692f30edf8d98e8_0.png)

Now， we have seen what is merging and also we have seen how multiple list can we merge together that is in two way merg or M merg we have seen。



![](img/00bf5453a8764569b692f30edf8d98e8_2.png)

And if there are multiple lists， then we can merge them in different patterns we have seen that。



![](img/00bf5453a8764569b692f30edf8d98e8_4.png)

Now let us see merge salt that is a recursive procedure。



![](img/00bf5453a8764569b692f30edf8d98e8_6.png)

And this is divide and conquer procedure。The dividing conquer strategy says that if a problem is large。

 then bake the problem into sub problemsble， and if the problem becomes small。

 then solve it and combine the solutions of the small problems or sub problems to get the solution for main problem。



![](img/00bf5453a8764569b692f30edf8d98e8_8.png)

So here the problem is to sort these elements and we say that the list is very large。

Then what is small。 So basically if there is a single element， then we say it's small。

 So single elements， we don't have to sort it。 So yes。

 in merge sort we say if there is just a single element， then we don't have to sort it。 Otherwise。

 if there are two elements also， we have to call it as a bigger problem or large problem。



![](img/00bf5453a8764569b692f30edf8d98e8_10.png)

![](img/00bf5453a8764569b692f30edf8d98e8_11.png)

If there's a single element， then we say it's a small problem。



![](img/00bf5453a8764569b692f30edf8d98e8_13.png)

Mert follows divide and conquer， therefore， is a recursive algorithm。Let me write the algorithm。

 let me write the algorithm， then I will trace the algorithm。



![](img/00bf5453a8764569b692f30edf8d98e8_15.png)

![](img/00bf5453a8764569b692f30edf8d98e8_16.png)

Literacy。Algom。Mge thought。What are the parameters it takes。



![](img/00bf5453a8764569b692f30edf8d98e8_18.png)

It takes two parameters that is beginning of a list and ending of a list。



![](img/00bf5453a8764569b692f30edf8d98e8_20.png)

So， low and high。

![](img/00bf5453a8764569b692f30edf8d98e8_22.png)

Then。

![](img/00bf5453a8764569b692f30edf8d98e8_24.png)

We check if low is less than high。

![](img/00bf5453a8764569b692f30edf8d98e8_26.png)

Means if low is equal to high eight means， there is a single element。 low is less than high means。

 at least there are two elements。 So list is large。



![](img/00bf5453a8764569b692f30edf8d98e8_28.png)

If low is less than high， then we will find out mid that is low plus high by 2。

 What for we are finding me like if I find one plus 8 by 2 that is 9 by 2， I get 4。

 so this will be mid。

![](img/00bf5453a8764569b692f30edf8d98e8_30.png)

![](img/00bf5453a8764569b692f30edf8d98e8_31.png)

What for， we say that this problem is large， So we break it into two sub problems。



![](img/00bf5453a8764569b692f30edf8d98e8_33.png)

That's what we find mid。Then what to do with the left hand side。Performers thought recursively。

Perform a sword on the right hand side ticker simply。 So perform mid。

 find out mid and perform merge sort from low to mid。



![](img/00bf5453a8764569b692f30edf8d98e8_35.png)

And also， perform merge salt。From mid plus 1。

![](img/00bf5453a8764569b692f30edf8d98e8_37.png)

Do系。So by performing more sort on the left hand side we will sort this one and we sort the right hand side。

 So when tool list are sorted， we are breaking this into tool list and when they are sorted we can merge them together so perform merge。



![](img/00bf5453a8764569b692f30edf8d98e8_39.png)

![](img/00bf5453a8764569b692f30edf8d98e8_40.png)

![](img/00bf5453a8764569b692f30edf8d98e8_41.png)

Merch from there low to mid is one list and mid plus one to high。 So we pass three parameters。

 So that's all This is a simple algorithm for So this is divided in conquer。 How merging is done。

 We have already seen the procedure， How merging is done。



![](img/00bf5453a8764569b692f30edf8d98e8_43.png)

![](img/00bf5453a8764569b692f30edf8d98e8_44.png)

![](img/00bf5453a8764569b692f30edf8d98e8_45.png)

But the point here is when the single array is given for sorting。

 we are breaking into two sub arrays， and we are saying this is one first list and that is second list。

 So single array will be containing two list and we have to merge them。

 So can a single array have more than one list Yes a single array can have many number of list。



![](img/00bf5453a8764569b692f30edf8d98e8_47.png)

![](img/00bf5453a8764569b692f30edf8d98e8_48.png)

![](img/00bf5453a8764569b692f30edf8d98e8_49.png)

![](img/00bf5453a8764569b692f30edf8d98e8_50.png)

Let us see how it works。

![](img/00bf5453a8764569b692f30edf8d98e8_52.png)

Let us see the tracing。 Now， based on this algorithm only。

 I will do tracing initially will be passing low as one and high as 8。 So let us take。



![](img/00bf5453a8764569b692f30edf8d98e8_54.png)

For these set of elements。 So first time we will pass1 and 8。



![](img/00bf5453a8764569b692f30edf8d98e8_56.png)

It will find out mid and it will divide the list and this side that side。

 so mid is perform and perform a sort from low to mid that is from 1 to4。



![](img/00bf5453a8764569b692f30edf8d98e8_58.png)

![](img/00bf5453a8764569b692f30edf8d98e8_59.png)

![](img/00bf5453a8764569b692f30edf8d98e8_60.png)

It will go the site。And it has to go on the right hand side also， but not now it will go afterwards。

 but I will draw this one also， so let us take this one so it will call itself from5 to8 on the right hand side。



![](img/00bf5453a8764569b692f30edf8d98e8_62.png)

![](img/00bf5453a8764569b692f30edf8d98e8_63.png)

So it has broken them into two list， first part and the second part。



![](img/00bf5453a8764569b692f30edf8d98e8_65.png)

And then afterwards， merge。 So first of all， let us finish this and this。Now。

 Mererard calls itself low is less than high。 Yes，1 is less than 4。 So again。

 find out mid and call these two。 So it means these four elements are also large。 Divide them。



![](img/00bf5453a8764569b692f30edf8d98e8_67.png)

![](img/00bf5453a8764569b692f30edf8d98e8_68.png)

So this side， one to2 and this side。3 to4。

![](img/00bf5453a8764569b692f30edf8d98e8_70.png)

Now， when we take this again， low is less than high。 Yes， there are two elements。

 so this is still large。

![](img/00bf5453a8764569b692f30edf8d98e8_72.png)

Again， split it。 So one to one on this side。And2，22 on the side。Now， there are just one1 elements。

See， if you have seen previous video， you may know how do a merge works， to where emerge sort works。



![](img/00bf5453a8764569b692f30edf8d98e8_74.png)

![](img/00bf5453a8764569b692f30edf8d98e8_75.png)

See， if you have seen previous video， you know how two way Mer sort works。



![](img/00bf5453a8764569b692f30edf8d98e8_77.png)

Now here also MerO is working in a similar way。 One1 array was given so it has splited and then splited。

 then splited。 Now it has reached one1 element。 Now。

 one element as their means is a single list with one element。 Now， these two can be merged together。



![](img/00bf5453a8764569b692f30edf8d98e8_79.png)

![](img/00bf5453a8764569b692f30edf8d98e8_80.png)

3 and 9 are merged together。 So the first merging is done for these two elements。

 and their result is obtained here。 So this is the first merge done。



![](img/00bf5453a8764569b692f30edf8d98e8_82.png)

![](img/00bf5453a8764569b692f30edf8d98e8_83.png)

This is the first merge done。 It will merge these two elements。



![](img/00bf5453a8764569b692f30edf8d98e8_85.png)

So three and9 a。Then coming to this site， it will split them and get 3，3 on the side and 4。

4 on the side。Then it will merge the elements，3 and 4 are merged。



![](img/00bf5453a8764569b692f30edf8d98e8_87.png)

So first，9 and three very merge， so the result was 3，9 and now5 and。7 and 5 are merge。 result is 5。

 and7。

![](img/00bf5453a8764569b692f30edf8d98e8_89.png)

This is combined。 Now， I will go back and perform merge here。 So this's the third merge。

 So it will merge these two。 So the result is 3，5，7，9。



![](img/00bf5453a8764569b692f30edf8d98e8_91.png)

![](img/00bf5453a8764569b692f30edf8d98e8_92.png)

Now， this side is sorted。Actually， we have to sort this whole array。 B it and break it and break it。

 Now two elements。 merge， two elements merge。 Now merge needs to also。 So this side is sorted。 Now。

 same thing is done on the right hand side。 Also，5 to 8 is there。 So on that side。

 it will divide this。

![](img/00bf5453a8764569b692f30edf8d98e8_94.png)

From 5 to 6。On that side， it will be7 to8。And 5 to 6 will become 5 comma 5 and 6 comma 6。Now。

11 element each。 this is again split 11 element。 So these two are merged。 So it becomes 4，6。

So this is the fourth merging。Then it will go this site。



![](img/00bf5453a8764569b692f30edf8d98e8_96.png)

It will split again，7，7 this side and 8，8 this side， so it will split this also。



![](img/00bf5453a8764569b692f30edf8d98e8_98.png)

Then again， these two are merge， so it becomes to weight， one mo， so this is fifth merging。



![](img/00bf5453a8764569b692f30edf8d98e8_100.png)

Now， as these two are already sorted， it will merge these two so it becomes2，4，6， eight。So。

 this is sixth merging。And then these two lists are merged to get a single list that is 2，3，4，5，6，7。

8，9。 This is a single sorted list that is seventh me here。



![](img/00bf5453a8764569b692f30edf8d98e8_102.png)

![](img/00bf5453a8764569b692f30edf8d98e8_103.png)

So this is how my sword works。When a single array is given recursively it will divide that array into smaller pieces until it reach 11 element。

 then it will start merging them。

![](img/00bf5453a8764569b692f30edf8d98e8_105.png)

So you can see that eight elements were given splited， then splited， then split it。

 Now they are merge， merge， merge。

![](img/00bf5453a8764569b692f30edf8d98e8_107.png)

So this is the working of myar。

![](img/00bf5453a8764569b692f30edf8d98e8_109.png)

Allright， so it is similar to two way， but in two way merge sort we just take first2 element the next two。

 the next two， but this is divide and conquer and this is recursive so it will simply divide and divide and then thats how it reaches one1 element then it will start merging。



![](img/00bf5453a8764569b692f30edf8d98e8_111.png)

![](img/00bf5453a8764569b692f30edf8d98e8_112.png)

So what is different is only the pattern is changing the approach， rest of the things are same。



![](img/00bf5453a8764569b692f30edf8d98e8_114.png)

Right， result is sorted and it is also merging to is at time， so it is also too way。

 but as it is recursive， we need some another name so we call it as merge sort。



![](img/00bf5453a8764569b692f30edf8d98e8_116.png)

Let us see the time taken by Mu sortt。So from the tree， the recursion tree。

 that is the tracing of that algorithm I have done， so I will show you how the time is。

 how I will show you how much time it takes。C。The merging has started in this level。

 This was just splitting。So how many elements are merged here，2， two elements merge，2 elements。

 two elements， total， how many elements，8 elements are there，2，4，6，8，8 elements are merged here。

 So I will say n elements are merged。 all n elements。 then again， merging is done at this level。

 So eight elements are merge。 Then again， eight elements are merged here。

 So n elements are merged each time。 So total how many levels are there。



![](img/00bf5453a8764569b692f30edf8d98e8_118.png)

![](img/00bf5453a8764569b692f30edf8d98e8_119.png)

1，2，3， or 1，2，3。 So total  three levels are there。 So for8 elements， I got three levels。

 it means it is log of 8， log of 8。1， and then two， then 4。

 So when something is raising by two every time and there is power of two， Lastly， power of two。

 that is  three at the last， we are having one8 elements total。 So three is log of 8。

 So how many passes are there。 So actually， these are not passes because it is recursive First。

 it will enter this side， then it will go that side。 So it is not passes right， first。

 it will finish left side then right side。But levels， if you see。

 So total how many levels login levels are there。 So this will be n。

 How many times log n times So the time taken by mass sort is tee off。



![](img/00bf5453a8764569b692f30edf8d98e8_121.png)

![](img/00bf5453a8764569b692f30edf8d98e8_122.png)

And log in。That's it。So the time for this one is also analog end。



![](img/00bf5453a8764569b692f30edf8d98e8_124.png)

Now， taking these numbers， I'll show you how this merge works。



![](img/00bf5453a8764569b692f30edf8d98e8_126.png)

Low and high are taken。 So example is 1 and 8，1 and 8。



![](img/00bf5453a8764569b692f30edf8d98e8_128.png)

So let us see， using the numbers Ill show you。First of all。

 it will find out and it will call Mer on the left hand side。

 so it will take these numbers and call 9，3，7，5。

![](img/00bf5453a8764569b692f30edf8d98e8_130.png)

Mada is column on this。Then now this is 1 to 4，1 to 4。



![](img/00bf5453a8764569b692f30edf8d98e8_132.png)

Again， this becomes one to4。So this is the first call， right， first call。 then 1 to 4。

 the first recursive call，1 to 4 is1 is less than 4。 So again， it will call itself by finding mid。

 it will call itself。 So again， it will split。 So this is 9 and 3。 So just  one and 2。



![](img/00bf5453a8764569b692f30edf8d98e8_134.png)

![](img/00bf5453a8764569b692f30edf8d98e8_135.png)

1 and2。Then again， this is also low is less than high。 This is low and this is high。

 just you can follow that one。 find out mid and split it。 So9 on this side。

 this is just one comma1 and three on this side。 This it is two comma2。Right。

 so it has called itself and itself and itself again。 So this is one list。 It has split。 Then again。

 this is split。 again， this is split on this side。 Now， these two are merge。

 So the result become what 3，9。Rightい。Then it will go on the right hand side， so this becomes 7，5。

That is three， four。Then it will come on the left hand side， this is just 7，3， then it is just five。

So these two are merge， so it becomes。5， and，7。Second call has finished。Now， this side is completed。

 This side is completed。 So what is the next step merge。 So these two are merge。

 So this becomes what first 3， then 5， then 7， then 9。So that's how it has splited， then splited。

 then splited， then merged。 So till here it got the result。 Now。

 it will go on to the right hand side。 So this part， second part for this one。



![](img/00bf5453a8764569b692f30edf8d98e8_137.png)

![](img/00bf5453a8764569b692f30edf8d98e8_138.png)

So this will be 6，4，8，2， And this is from 5 to 8。

![](img/00bf5453a8764569b692f30edf8d98e8_140.png)

Thiss fun。Now， on this， sorry。5 to 8 on this one。 it is called 5 is less than 8。 Yes， again。

 find out mid and call must this one。 So on the left hand side， it will be called。

 So this will become。

![](img/00bf5453a8764569b692f30edf8d98e8_142.png)

![](img/00bf5453a8764569b692f30edf8d98e8_143.png)

![](img/00bf5453a8764569b692f30edf8d98e8_144.png)

6，4， It will be 5，6。 ind is our 5，6。Then on this again mes artt is called so five is less than6 so again find mid and call mes。

 so it will become6。

![](img/00bf5453a8764569b692f30edf8d98e8_146.png)

![](img/00bf5453a8764569b692f30edf8d98e8_147.png)

And this is index 5。Now， low is also6， high is also 6， it will go on the right hand side， this call。

For this one。 So this will be 4， and the index is 6。 So low is also 6。 high is also 6。 Then merge。

 These two are merge。 So it becomes。4 first。Sorry。Then it becomes four first， then 6。

Then it will go on the right hand side of this one。 So right hand side is。



![](img/00bf5453a8764569b692f30edf8d98e8_149.png)

8 and2。 this is index 7 and 8。

![](img/00bf5453a8764569b692f30edf8d98e8_151.png)

Now， low is 7 high is 8。 So low is less again， find out mid and call this one。

 So this side it will be 8 and it will be 7。

![](img/00bf5453a8764569b692f30edf8d98e8_153.png)

![](img/00bf5453a8764569b692f30edf8d98e8_154.png)

Now， just one element。 So go to the right side。

![](img/00bf5453a8764569b692f30edf8d98e8_156.png)

2 single element。Now merge， So left side completed， right side completed now merge。 So2。

8 and becomes28。

![](img/00bf5453a8764569b692f30edf8d98e8_158.png)

![](img/00bf5453a8764569b692f30edf8d98e8_159.png)

Now， this side， this side， both are sorted， merge， both are sorted， then merge。 So this becomes 2，4。

6，8。

![](img/00bf5453a8764569b692f30edf8d98e8_161.png)

So， this becomes。

![](img/00bf5453a8764569b692f30edf8d98e8_163.png)

2，4，6，8。 Now， this is also sorted。 This was already sorted beforehand。 Left hand side it went。 Now。

 these two are mergeed together 2，3，4，5，6，7，8，9。 So in this way， this list becomes。



![](img/00bf5453a8764569b692f30edf8d98e8_165.png)

2，3，4，5，6，7，8，9， so it。

![](img/00bf5453a8764569b692f30edf8d98e8_167.png)

This is how my heart works。

![](img/00bf5453a8764569b692f30edf8d98e8_169.png)

Tracing， I have done。See earlier I have shown just indices now in this。

 I am showing numbers and as it is calling itself two times the tracing tree will be more like a binary tree。

 It will be like a binary tree。

![](img/00bf5453a8764569b692f30edf8d98e8_171.png)

![](img/00bf5453a8764569b692f30edf8d98e8_172.png)

![](img/00bf5453a8764569b692f30edf8d98e8_173.png)

And if I say the traverse cell， then in which traveral merging is done post order first left， left。

 left， then right， then root merge。

![](img/00bf5453a8764569b692f30edf8d98e8_175.png)

Right， then right， left， then right， then root， merge， root merge。

 So merging is done in post order traveral。That's it。

 So I have shown you tracing in two different ways。



![](img/00bf5453a8764569b692f30edf8d98e8_177.png)

Now let us find out the time complexity of this algorithm by using recurnceulation。



![](img/00bf5453a8764569b692f30edf8d98e8_179.png)

For this recursible algorithm， let us prepare recur resolution and find out the time complexity of more sort。



![](img/00bf5453a8764569b692f30edf8d98e8_181.png)

If I say this algorithm takes TN time。Then this is one condition and this。

 if I ignore condition and I say this is calculating mid。

Then it is calling itself So T of but half of the list low to mid half of the list for n by 2 and again calling itself。

 So this is also n by2， then it is merging， merging from where low to high two list are there low to mid mid plus one to high2 list total n elements。

 so merging takes n。

![](img/00bf5453a8764569b692f30edf8d98e8_183.png)

![](img/00bf5453a8764569b692f30edf8d98e8_184.png)

So if I prepare a current inulation by adding all these， ignore one there。

 Now this is T N is equals to two times。T N by 2 plus N。



![](img/00bf5453a8764569b692f30edf8d98e8_186.png)

So the recurrennceulation is T， N as equals to。

![](img/00bf5453a8764569b692f30edf8d98e8_188.png)

2 T， N by 2 plus N。 when n is greater than one。 what it is doing when n is equals to1。

 it's not doing anything。 So we don't write 0。 We can write  one or some constant。



![](img/00bf5453a8764569b692f30edf8d98e8_190.png)

![](img/00bf5453a8764569b692f30edf8d98e8_191.png)

Okay， some conments 1，10， anything you write。 It's not doing anything。 So better write one。

Theres very translation。Now， by using masters theorem。

 a values is how much to B value is how much to an F of n is what。嗯。Now， find到。Log A base B。

 So that is log 2 base 2， S 1。And power of N K， it is1。 So this is log 2 base 2 is equal to K。

 They are equal。 So we compare these two， and this is falling in case 2。



![](img/00bf5453a8764569b692f30edf8d98e8_193.png)

![](img/00bf5453a8764569b692f30edf8d98e8_194.png)

Case 2。 So case2 says what， whatever f ofn is。

![](img/00bf5453a8764569b692f30edf8d98e8_196.png)

Multiplied by login。Rightrite F of fanities and multiply it by log then。

 So I am using master theorem Al， this recur installationulation is solved in another video。

 You can look for that video。

![](img/00bf5453a8764569b692f30edf8d98e8_198.png)

RightIt is in the second topic that is divided and conquer。 I have solved few recurnceulation。

 This you will find in the title of a video itself。



![](img/00bf5453a8764569b692f30edf8d98e8_200.png)

Now， here I directly am using masters theorem。 There are videos on master theorems， also。



![](img/00bf5453a8764569b692f30edf8d98e8_202.png)

So time is tee off and law again。

![](img/00bf5453a8764569b692f30edf8d98e8_204.png)