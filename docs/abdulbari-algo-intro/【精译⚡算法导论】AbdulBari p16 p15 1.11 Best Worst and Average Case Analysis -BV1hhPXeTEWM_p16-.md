# 【精译⚡算法导论】AbdulBari p16 p15 1.11 Best Worst and Average Case Analysis -BV1hhPXeTEWM_p16-

In this video， we will learn about best， worst and average case analysis of Elgar。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_1.png)

So for example， Ill be taking two algorithms that is linear search。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_3.png)

And binary search tree。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_5.png)

I'll take two examples linear search and binary search so first commonly we examples on linear search this is common thing I will take binary search tree also and I'll show you the time case analysis on binary search also so well learn about best case and best case time worst case and worst case time and minimum time and worst case maximum time in worst case and average case so you will come to know all these things so in this video you are going to learn these things the first one is linear search linear search。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_7.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_8.png)

Lar search。If a set of elements list of elements are given。

 then when we are searching for any element in that list。

 then we have different search methods available like linear search and binary search。

Let us see how linear search works here I have a list of 10 elements and in this I want to search for some key element。

 Let us say I want to search for key element。7。What is the method for searching for a key element？

For looking for a key element， the linear search will start scanning the list from left hand side by checking each element at a time。

 so it will start checking whether this is seven no go to the next element is it seven no is it7 is it seven so it will go on checking all the element until either it finds an element Yes the element is found so here is an element so totally how many comparisons will get an element that is in six comparisons we get an element。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_10.png)

Soose I'm searching for a key element。对地。Then that is startling near search。

20 it will check for the first element， no， it is not present the next one， next one， next one。

 next one， it will check all the elements and it finds that。20 is not present in the list。

So when we search in a list， the search may be either successful or it may be unsuccessful。

 so for seven it was successful and we found it at index 5 and 20 is not found when we have checked the entire list。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_12.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_13.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_14.png)

So this is how linear search works。Now let us understand what is best case and what is best case time。

 what is worst case， what is worst case time we will find out in this linear search of've God。Fust。

Let us see what is the best case？Best。オッケース？In case if you are searching for a key element。

 which is present at first index。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_16.png)

Then it is best case。 in case the case。 you may be searching for any element from the list。

 But if you are searching for a key element， which is present at index， fast index。

 the very beginning index， then that is best case。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_18.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_19.png)

Seing。今业美门。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_21.png)

Present at。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_23.png)

First index。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_25.png)

This is best case。Then what the time it will take if I'm searching for the first key element here in my example。

8 is the first key element， if I'm searching for eight then it will take constant time。

Best case time。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_27.png)

Is constant exchange。I can write it as order of1， so best case time is for n element is order of1。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_29.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_30.png)

Best is time for and elements is out of fun So here I like。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_32.png)

B of n as order of one。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_34.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_35.png)

Now big omega， what is that we will see afterwards， so first I have written that function。Now，我ky is。

Often algorithm linear search algorithm。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_37.png)

What's the worst case when the algorithm will take maximum time if I'm searching for the key。

 which is at the last index？

![](img/82d5f8aa44612dfed32101c2bc1c42c2_39.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_40.png)

索请。呃 key。哎。Last。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_42.png)

エネックス。In my example， 18 is the key which is presented at last index。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_44.png)

So that is the worst case。What is the time taken for searching that key element so I have to check for all the n elements that I can reach there now what is the time taken in this first case？

Was。Gs。当然。As。And。So worst case for any ims N， and that is order of n。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_46.png)

So here right， worst case for n elements is order of n。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_48.png)

So now I have best case as well as worst case times given for linear search。Now average case is time。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_50.png)

Average case is defined by。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_52.png)

On保分。Gs done。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_54.png)

Divided by。Number of cases。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_56.png)

So for average case， you have to find out all possible cases and the time taken in each possible case and then divide it by number of cases。

So this type of analysis is very difficult， it may not be possible on every algorithm。

 so rarely we do it。And mostly for average case， the time that we get will be similar to worst case。

 so that's why we prefer finding worst case time for algorithms。

Average case analysiss may not be possible always。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_58.png)

Let us check for linear search， what are the cases？



![](img/82d5f8aa44612dfed32101c2bc1c42c2_60.png)

So let me tell you just。In case if you're searching for a key present on first index index。

In case if you are searching for a key presenter second index， or in case third index。

 in case fourth index in case anything。それざらの決算。So in case if you're searching for a key present at first index。

 then。Outage time。For this one， it is one， if I'm searching for a key presented second index。

 it will take two comparisons and third index three comparisons， then so on， last index n comparison。

 total how many cases are there and cases are there。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_62.png)

So what is the s to this is n into n plus1 by2 and divided by n this is canceled and this is n plus1 by 2。

 so average case time for n elements is n plus1 by 2。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_64.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_65.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_66.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_67.png)

All these cases and the time complexities we are finding based on number of comparisons。

 how many comparisons are required for finding an element？All， so now I have。

B case and time and the worst case and time and the average case。

 so in average case I consider all possible cases and elements are there and possible cases you may be searching for first element or second element or third element any element so for each I have taken the time and the number of cases by n so this is n plus one by2。

Now let us apply asymptotic notations on this one， see I have told you in some video in one video in asymptotic notation that cases are nowhere way related to notations notations are for the functions cases are the just a type of analysis done on Al。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_69.png)

Let us see how you can apply notations， see I have V case time as one。

Canly right this has best keys is。Big of n。 sorry big of one yes。

I can write we go of1 Can I write it as omega1 yes， can I write it as theta of1 yes。

 see how what is the function， function is one constant so when you have a function constant this belongs to constant class so when it directly belongs to constant class I can use the of1。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_71.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_72.png)

And even they can use a going end the word bond also。

This we have already we studied a syntic notation， so any function greater than equal to comes as a upward。

 less than equal to comes as a lower bond and exactly same function at this theta， so this is theta。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_74.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_75.png)

那我s case。The time is M。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_77.png)

This belongs to a class that is linear， function is linear。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_79.png)

Can I write this as worth his time as。B go of n yes， words case of n is omega of n。 yes。

 I can write worst case of n is theta of n yes。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_81.png)

I can use any of these notations。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_83.png)

There is no fixed notation to show that this is best case， this is worst case。

 best case can be written using any notation， and the worst case can also be written using any notation。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_85.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_86.png)

RightDon't take it wrong， BigO is for worst case or omega is for best case， no it's wrong。

 you can use thes for best case or worst case， you can use bigO for any case and even for average case I have a function N one by two this belongs to which class it belongs to linear class n。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_88.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_89.png)

And so even that I can write it as a be omega theta。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_91.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_92.png)

Right。So don't mix up with the cases that's already Ive told you now I have proved this one right when you have a function for a function。

 you can use big so makego so theta all or true， all our cut。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_94.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_95.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_96.png)

Most of people confuse that this worst case should be below， this is upperborn， maximum home。

 upper bond。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_98.png)

Like lower soomeが no nothing like that。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_100.png)

You can use an innotation。Now next example is binary search tree here I have a binary search tree。

 I guess I hope that you already know binary search tree。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_102.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_103.png)

The purpose of binary search is useful for searching。

 the elements are organized such that for every node all the elements smaller are on the left hand side。

 all the greater elements on the right hand side so for searching if you are searching for a smaller element it goes on left side or greater element we go on the right side。

Suppose I am searching for 15， let me show you the working。

If I am searching for 15 and start from 20， is it 15， no， 15 is a smaller than this one。

 so go to left tax site。Is it 15 no 15 is greater than this one so on right hi side。

 yes 15 is found so what is the time taken for searching， total how many comparison I have done。

 only three comparisons I have done so the time taken is three so actually that is equal to the height of a tree。

Hight of a。 So what's the high we usually call it as log n。login is the height， so around 7。

7 elements I have means eight elements， so log at a is3， so three conversions are required。

 so the height of a tree is login， so the time taken is。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_105.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_106.png)

Loggan 4，15。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_108.png)

Now let us understand what is best case and what is the best case time。

 worst case and worst case time。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_110.png)

Best cases。Best case is if I am searching for the element which is present in the root。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_112.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_113.png)

Best case。色精。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_115.png)

Root element in shorthand writing means I am searching for the key element。

 which is present in the root。 So how much time it will take for searching for that particular element just constant a time if I'm searching for 20 just check it in the root Yes the element is form So the best case time is best case time has。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_117.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_118.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_119.png)

B in as one。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_121.png)

Me and this one。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_123.png)

Then what is worst case？Was case。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_125.png)

Worsse cases searching for the element which is present in the leaf。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_127.png)

舍经佛。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_129.png)

Leave any。So what are the leaf elements in my example， 5， 15， 25 and 40。

 if Im searching any one of those elements， then the time will be maximum that is worse case。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_131.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_132.png)

So what is most case time？

![](img/82d5f8aa44612dfed32101c2bc1c42c2_134.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_135.png)

Worst case time depends on the height of a binary search tree。 What is the height。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_137.png)

Log in。 So the worst case is log and。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_139.png)

Worse cases alogan。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_141.png)

はい。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_143.png)

No。Will not go on the average case。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_145.png)

No。This is a binary source tree。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_147.png)

For the same elementsers， even I can have a binary surgery tree like this。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_149.png)

In the root， I have4 teeth。And on the left child I have 30， and on's left child， 25。

 and on its left child， 20， and its left child is 15 and 10。And five。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_151.png)

This is also by the research tree。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_153.png)

This is a left skewed binary search tree， this is height balanced binary search tree by using seven elements。

 this is the minimum height that I can have， this is the maximum height that can I have。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_155.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_156.png)

Now what is the best case in this binary search tree， best case is same for binary search tree。

 best case is same searching for the loop to that one。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_158.png)

Then what is the worst case， searching for a leaf。 So who will leave only one element。

 searching for this one is a worst case。But what is the time taken depends on the height of a tree and here also it was dependent on the height of a tree and the height was log n and here the height is n。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_160.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_161.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_162.png)

H就 n。So， it means that。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_164.png)

In worse case， minimum worst case time is how much login。

And maximumzema worst case times is how much and？So I repeat the once again。

 I repeat the point once again， see what is the worst case for binary search tree searching for an element present in a leaf。

 searching for an element present in a leaf。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_166.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_167.png)

That is worst case then what is the worst case at time it depends on the height of a tree leaf element will be at the last level so that depends on the height of a tree so what could be the height of a binary search tree the height of a binary search tree can be minimum as login and maximum as n。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_169.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_170.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_171.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_172.png)

So minimum birth case time， maximum birth case time。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_174.png)

Usually the type of questions we find in some competitive exams。

So world case means we know it is a maximum， how it can you minimum。

So it depends on the type of data structure or type of an algorithm。

 so I have chosen a worst binary search tree in which we get minimum worst case time as well as maximum worst case time so minimum worst case time is login maximum worst case time is n because the worst case time depends on the height of a tree I should not write login here I should write height of a binary search h then what that h can be h can be as minimum as log n as maximum mass n。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_176.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_177.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_178.png)

![](img/82d5f8aa44612dfed32101c2bc1c42c2_179.png)

That's it， so these are the best worst case analysis for binary research now this best case worst case we can write using an notation just like how I have shown in linear search。

 I can use Vigo omega theta any notation。So the things that we studied here is that how to find best case and worst case and average case and what notation should be used。

 we got answer for it and sometimes minimum time in worst case。

 maximum time in worst case means what that also have explained you this cannot be possible on every algorithm or data structure in some situations it is possible so this can be raised as a question。

 what could be the minimum time， what could be the maximum。



![](img/82d5f8aa44612dfed32101c2bc1c42c2_181.png)

That's song for the video。Thank you for watching。

![](img/82d5f8aa44612dfed32101c2bc1c42c2_183.png)