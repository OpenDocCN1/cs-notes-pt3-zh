# 【精译⚡算法导论】AbdulBari p30 p29 2.6.1 Binary Search Iterative Method -BV1hhPXeTEWM_p30-

Yeah， our next topic is binary research。

![](img/836a426b70cc698b151086c2f949a2e7_1.png)

Bary research is a searching technique， This is one the methods third for search。



![](img/836a426b70cc698b151086c2f949a2e7_3.png)

There are two different methods。 One is a linear search and the the second one is binary search。

This binary research follows divide conquered strategy。



![](img/836a426b70cc698b151086c2f949a2e7_5.png)

If you remember in divide and conquer a strategy， we learn that if the size of a problem is large。

 break the problem into some problems， once there is a problem is solve of problem are solved。

 combine them to get the solution from main problem。



![](img/836a426b70cc698b151086c2f949a2e7_7.png)

So I have already taken some set of elements here。 I have a list of elements that is 1 to 15 total 15 elements I have。

 Now， let us learn how binary search works。

![](img/836a426b70cc698b151086c2f949a2e7_9.png)

![](img/836a426b70cc698b151086c2f949a2e7_10.png)

First and foremost thing is。

![](img/836a426b70cc698b151086c2f949a2e7_12.png)

To perform binary search， list one must be in the sorted order。

 All the elements must be already in sorted order。 Then only you can perform binary search。

 This is a prerequisite for binary search。 So here I have the list of elements in the sorted order。



![](img/836a426b70cc698b151086c2f949a2e7_14.png)

![](img/836a426b70cc698b151086c2f949a2e7_15.png)

![](img/836a426b70cc698b151086c2f949a2e7_16.png)

Then let us see the approach of binary research。 So for our performing binary research。

 we need two index pointers。

![](img/836a426b70cc698b151086c2f949a2e7_18.png)

![](img/836a426b70cc698b151086c2f949a2e7_19.png)

One is low， that is a starting point and the second one is high， that is the ending point。



![](img/836a426b70cc698b151086c2f949a2e7_21.png)

So I want to see search for a key element。42， which is already present here。



![](img/836a426b70cc698b151086c2f949a2e7_23.png)

Let us see how my research works。

![](img/836a426b70cc698b151086c2f949a2e7_25.png)

Low and high are taken。 low and high。 Then we calculate mid mid is rope plus high divided by bo。

 and we take。

![](img/836a426b70cc698b151086c2f949a2e7_27.png)

Flow value。What is low here。 This one high is 15。 This is  one plus 15 by 2。 This is 16 by 2。

 that is 8。

![](img/836a426b70cc698b151086c2f949a2e7_29.png)

![](img/836a426b70cc698b151086c2f949a2e7_30.png)

This is Mer。

![](img/836a426b70cc698b151086c2f949a2e7_32.png)

Now， the value what I am searching is 42。 Check at a of mid。 Is it 42。 No。

42 is greater than this one。 So definitely it's on the right hand side。

 how we can ensure that is on the right hand side because the list is sorted order。



![](img/836a426b70cc698b151086c2f949a2e7_34.png)

![](img/836a426b70cc698b151086c2f949a2e7_35.png)

So we ignore this part of a list， and we search for this 42 in the second part for the second half of a list。

 So here we are dividing the list into two hals。 and then we search in the second half。

 So we'll start from here until there。 So we will bring low here where mid plus 1。

 So we'll change low to mid plus 1。 So mid is 8。 So we'll bring low at 9 and high remains at 15 only。



![](img/836a426b70cc698b151086c2f949a2e7_37.png)

![](img/836a426b70cc698b151086c2f949a2e7_38.png)

![](img/836a426b70cc698b151086c2f949a2e7_39.png)

![](img/836a426b70cc698b151086c2f949a2e7_40.png)

![](img/836a426b70cc698b151086c2f949a2e7_41.png)

![](img/836a426b70cc698b151086c2f949a2e7_42.png)

Now， we searched within this list。 So for searching again， we calculate mid。



![](img/836a426b70cc698b151086c2f949a2e7_44.png)

9 plus 15 by 2。

![](img/836a426b70cc698b151086c2f949a2e7_46.png)

So this is2。9 plus 15，2402 is 2。 So we minute， we got it asked 2。 So itll check here。 Min is 2。



![](img/836a426b70cc698b151086c2f949a2e7_48.png)

Is it the number that Im searching for 47。 No， this is 42。 So my number is on the left hand side。

 So again， this sub list， we will split it on two half。 Now， my number is on the left hand side。

 So I'll search in this area。 So I'll bring high here on mid-1。 That is 11。



![](img/836a426b70cc698b151086c2f949a2e7_50.png)

![](img/836a426b70cc698b151086c2f949a2e7_51.png)

![](img/836a426b70cc698b151086c2f949a2e7_52.png)

So， high becomes 11。

![](img/836a426b70cc698b151086c2f949a2e7_54.png)

And this is became。 this is 9 only。For 9 to 11， find out M 9 plus 11 by 2 S 20， So it is 21 it is 10。

 So this is M。

![](img/836a426b70cc698b151086c2f949a2e7_56.png)

![](img/836a426b70cc698b151086c2f949a2e7_57.png)

Is it remember that I am searching 4 36。 No， my number is on the right hand side。 So again。

 we will split this list。 See now the list is narrowing down to a smaller list of just  three elements for a 15。

 we have shden。 Now we are left with only three elements。 Now。

 I should look on the right hand side of this list。 So change， there is low two mid plus one。

 So now this time， low and high， They both come on the same point。 That is 11。

So low become mid plus 1。 So mid is 10。 So low become 11th and high is all 11。 Now。

 find out mid 11 plus 11 by 2。 that is 11 only。 So middle is also here。



![](img/836a426b70cc698b151086c2f949a2e7_59.png)

![](img/836a426b70cc698b151086c2f949a2e7_60.png)

Now check at of mid。 Do you have that element， Yes， this is the element that I am searching for。

 so element is found。

![](img/836a426b70cc698b151086c2f949a2e7_62.png)

![](img/836a426b70cc698b151086c2f949a2e7_63.png)

How many comparisons I have done，1，2，3，4 in four comparison I got an agreement which was present at in depth 11。

If I was performing linear search， then I would have started it from here and compare each element。

 And after 11 completion， I would have got the number。But in binary search。

 Im able to get it in just four comparisons。😊。

![](img/836a426b70cc698b151086c2f949a2e7_65.png)

So that saw behind the research looks faster than linear search。



![](img/836a426b70cc698b151086c2f949a2e7_67.png)

So here are one example I have taken。 Let me take some more examples and quickly solve a few more examples。

 So you get some idea。 Now your search key value。

![](img/836a426b70cc698b151086c2f949a2e7_69.png)

![](img/836a426b70cc698b151086c2f949a2e7_70.png)

2。I'll take a key value as2 n。

![](img/836a426b70cc698b151086c2f949a2e7_72.png)

I'm searching for 12。 If I perform linear search， it can be found in just four comparisons。

 So let us see how binary search works。 So first take low here and high at the ending index。

 So low and high。 And also， we know we have to find out mid that is low plus high divided by two。

 F value。 Low is one high is 15。 Find out M。 This is1 plus 15 by 2。 That is 8。 So 8 is M。

 Is it the element that you are searching， it's 29。 No， my number is 12。😊。



![](img/836a426b70cc698b151086c2f949a2e7_74.png)

![](img/836a426b70cc698b151086c2f949a2e7_75.png)

![](img/836a426b70cc698b151086c2f949a2e7_76.png)

So2l is a smaller。 So look into the first half of a list。

 So move high from here and bring it on mid -1。 So high becomes 7。 high becomes 7 and low is still 1。

 So 1 plus 7 by 2。 That is 8 by 2 is 4。 mid is 4。

![](img/836a426b70cc698b151086c2f949a2e7_78.png)

![](img/836a426b70cc698b151086c2f949a2e7_79.png)

Is it the number that you are searching to Yes， found。 So search is successful at index 4。

 Here you can see just in two comparison， I got a number。😊。



![](img/836a426b70cc698b151086c2f949a2e7_81.png)

Right， so the number of comparison seems to be less than linear search。



![](img/836a426b70cc698b151086c2f949a2e7_83.png)

Now， let us search for any element which is not present in the list and let us see what binary search does。



![](img/836a426b70cc698b151086c2f949a2e7_85.png)

I am taking a key element。

![](img/836a426b70cc698b151086c2f949a2e7_87.png)

30， its not present here。 After 29， we have 31， So 30 is not present here。 So let us trace this one。

 This is low。 It is one， and this is high。 That is 15， low and high and mid。



![](img/836a426b70cc698b151086c2f949a2e7_89.png)

So low is one highest 15， and mid is 1 plus 15 by 2。 That is 8。

 So we know well that it is low plus high divided by 2 and the floor value 8。 See。

 one thing if you observe， I have saw or that it two  Qes。

 every time I was getting mid as 8 only because for this list from 1 to 15 M is always 8。😊。



![](img/836a426b70cc698b151086c2f949a2e7_91.png)

![](img/836a426b70cc698b151086c2f949a2e7_92.png)

![](img/836a426b70cc698b151086c2f949a2e7_93.png)

![](img/836a426b70cc698b151086c2f949a2e7_94.png)

Okay， this is interesting。 We'll see it further。Now，8， the key is 30。

 Is it the key that you are searching for。 No， my number is greater than 29。

 So look on the right hand side。 So change low 2 9。 So low becomes mid plus 1。 That is 9。

 and this remains 15。 So 9 plus 15 by 2 is 12。 So now the new mid value is 12。😊。



![](img/836a426b70cc698b151086c2f949a2e7_96.png)

![](img/836a426b70cc698b151086c2f949a2e7_97.png)

![](img/836a426b70cc698b151086c2f949a2e7_98.png)

This is made。

![](img/836a426b70cc698b151086c2f949a2e7_100.png)

Again， the middle of this list is 2 Elius。 So check here。 Is it the number 30。 No， that is 47。

 So our number is smaller than that。 So change high to mid -1。 That is 11。 high will become 11。

 and this remains 9。 Now， this is 20 by 2。 That is 10。



![](img/836a426b70cc698b151086c2f949a2e7_102.png)

![](img/836a426b70cc698b151086c2f949a2e7_103.png)

So new mid will be at 10。Is it the number 36 is the number that you are searching。 No，30。

30 is smaller。 So go on the left hand side。 So what should change now， high should change to mid -1。

 So high will also become 9。 That is 10-1，9。 So both are 9，9。 So this is 9 plus 9。



![](img/836a426b70cc698b151086c2f949a2e7_105.png)

![](img/836a426b70cc698b151086c2f949a2e7_106.png)

By  to S 9 only。 So what is the mid value I got， Mid value is also 9， right， This is mid。



![](img/836a426b70cc698b151086c2f949a2e7_108.png)

![](img/836a426b70cc698b151086c2f949a2e7_109.png)

Is it the number that you are searching for， No， the number is smaller。

 So it's on the left hand side。 So when it's on the left hand side， we should check this side。

 So what I should change， high should be changed to mid-1。 So high becomes 8 and low is 9， right。

 high becomes 8 and low is 9。 So if you observe now。



![](img/836a426b70cc698b151086c2f949a2e7_111.png)

![](img/836a426b70cc698b151086c2f949a2e7_112.png)

![](img/836a426b70cc698b151086c2f949a2e7_113.png)

If you observe now， this9 is greater than high。 So low has become greater than high。

 But when we start， low will be on the left hand side， high is on the right hand side。

 So low cannot cross high。 if it has crossed means we did not find the element。



![](img/836a426b70cc698b151086c2f949a2e7_115.png)

Element is not found。 That's it。 So if low becomes greater than high， the element is not found。



![](img/836a426b70cc698b151086c2f949a2e7_117.png)

![](img/836a426b70cc698b151086c2f949a2e7_118.png)

Now， let us write an algorithm for binary search。

![](img/836a426b70cc698b151086c2f949a2e7_120.png)

![](img/836a426b70cc698b151086c2f949a2e7_121.png)

Binary search。It takes array of elements and the size。

 that is number of elements and the key to be searched。



![](img/836a426b70cc698b151086c2f949a2e7_123.png)

![](img/836a426b70cc698b151086c2f949a2e7_124.png)

These are the three parameters。

![](img/836a426b70cc698b151086c2f949a2e7_126.png)

And it returns the index of a element found。 So instead of algorithm， I'm writing it like a function。



![](img/836a426b70cc698b151086c2f949a2e7_128.png)

对。

![](img/836a426b70cc698b151086c2f949a2e7_130.png)

L will be at one， and high will be at n。

![](img/836a426b70cc698b151086c2f949a2e7_132.png)

I'm not declaring them。

![](img/836a426b70cc698b151086c2f949a2e7_134.png)

L and and H are the variables。

![](img/836a426b70cc698b151086c2f949a2e7_136.png)

Anteia variables。Now what it does， it will find out mid that is low plus high divided by 2。



![](img/836a426b70cc698b151086c2f949a2e7_138.png)

It will find out met。Then at mid， it will check like we were doing here。 mid we were getting it at 8。

 So at that place， it will check if。

![](img/836a426b70cc698b151086c2f949a2e7_140.png)

![](img/836a426b70cc698b151086c2f949a2e7_141.png)

Key that we are searching is equals to a of me。

![](img/836a426b70cc698b151086c2f949a2e7_143.png)

![](img/836a426b70cc698b151086c2f949a2e7_144.png)

If it is equal to a of mid， a of mid。If sold， then the element is found。



![](img/836a426b70cc698b151086c2f949a2e7_146.png)

Then。What is the index of the element That is matter written the middle element is found。



![](img/836a426b70cc698b151086c2f949a2e7_148.png)

If it is not that same element， then check if key element is。



![](img/836a426b70cc698b151086c2f949a2e7_150.png)

Less than a of。

![](img/836a426b70cc698b151086c2f949a2e7_152.png)

Mid means key element is on the left hand side。 If it is on the left hand side。

 then what we should change， I should be changed to mid -1。 So h should be changed to mid -1。



![](img/836a426b70cc698b151086c2f949a2e7_154.png)

![](img/836a426b70cc698b151086c2f949a2e7_155.png)

![](img/836a426b70cc698b151086c2f949a2e7_156.png)

If it is neither equal nor less， then definitely it is greater。

 So then what we should change low to should change to meta plus 1， so。



![](img/836a426b70cc698b151086c2f949a2e7_158.png)

And。L should change to mid plus 1。

![](img/836a426b70cc698b151086c2f949a2e7_160.png)

Now， this process will repeat， go on repeating until the element is found。

 So this has to be written in the loop。 So I'll write a loop。



![](img/836a426b70cc698b151086c2f949a2e7_162.png)

![](img/836a426b70cc698b151086c2f949a2e7_163.png)

How long this loop should run。As long as low is on this side。



![](img/836a426b70cc698b151086c2f949a2e7_165.png)

Low and high， right， low should not cross high。 If low have crossed high high means element is not found。

 So I should run this loop as long as low is less than or equal to high。



![](img/836a426b70cc698b151086c2f949a2e7_167.png)

![](img/836a426b70cc698b151086c2f949a2e7_168.png)

![](img/836a426b70cc698b151086c2f949a2e7_169.png)

If low became greater than high， it will stop， and I should return not found。

 So I will return index 0。 It means the element is not found。



![](img/836a426b70cc698b151086c2f949a2e7_171.png)

So this a binary search algorithm， and this is a iterative process that is loop using loop。



![](img/836a426b70cc698b151086c2f949a2e7_173.png)

![](img/836a426b70cc698b151086c2f949a2e7_174.png)

Okay， let us already we have taken this example。 we have traced this。

 we have calculated mid and gone on the left hand side or the right hand side。

 all these things we have done， we have checked how it behaves in case of element is found and how it works if the element is not found。



![](img/836a426b70cc698b151086c2f949a2e7_176.png)

![](img/836a426b70cc698b151086c2f949a2e7_177.png)

Now， let us see the tracing of this one。With the help of a train。Let us do it。 As for this example。

 first time when we are calling this algorithm， let us check how the mids are calculated。 First time。

 mid will be 8。

![](img/836a426b70cc698b151086c2f949a2e7_179.png)

![](img/836a426b70cc698b151086c2f949a2e7_180.png)

Yes， we have seen this。And if every element is smaller， then it will calculate mid from 1 to 7。

 That is 4。 So this side， it will be 4。

![](img/836a426b70cc698b151086c2f949a2e7_182.png)

If you are checking on this side that is 9 to 15 and calculate admit， it will be on 12。



![](img/836a426b70cc698b151086c2f949a2e7_184.png)

Then if the element is less than 2 L， then it will calculate admit for this one that is 1212 3。

 So we will get two on this left hand side。

![](img/836a426b70cc698b151086c2f949a2e7_186.png)

![](img/836a426b70cc698b151086c2f949a2e7_187.png)

On the right hand side， if we check it from 5 to 7， then the mid valley will be 6。



![](img/836a426b70cc698b151086c2f949a2e7_189.png)

And on the left hand side， we have one， and the right hand side will get to 3。

 And the left hand side of this one is 7。

![](img/836a426b70cc698b151086c2f949a2e7_191.png)

![](img/836a426b70cc698b151086c2f949a2e7_192.png)

So 5 and the right hand side of this one is 7。 and the left of tool is。



![](img/836a426b70cc698b151086c2f949a2e7_194.png)

See， if you check this one leaving 8，9 to 11， the middle is 10， and the left hand side of desk is 9。

 right hand side is 11。 And on this side， we will have 143 on left hand side。



![](img/836a426b70cc698b151086c2f949a2e7_196.png)

![](img/836a426b70cc698b151086c2f949a2e7_197.png)

15 on right side。 Now， let me show you quickly some examples。 See if I' am searching for 29。

 this algorithm will find out M and go to 8， and that is 1 plus 15 by 2 is 8。 M is 8。

 and element is found。 So in one comparison， the element is found。



![](img/836a426b70cc698b151086c2f949a2e7_199.png)

If I am searching for an element 47， then it will first check at 8。 and if the element is not 47。

 it is greater。 So it will look on this side that is 9 to 15。 and the middle of that one is 47。

 so it will stop here element is 447。 mid of that is 12。 so it will stop at 12。😊。

If the element that I am searching is 14， then first it will check out mid。 This is 29。 No，8 is 29。

 My element is 55， Then it will go on the right hand side。 mid。 that is 2。 So it is 47。

 No element is 55 is greater。 So then mid of this one is 14。 That is 55 Yes element is found。

 So in three comparison， the element is found。😊。

![](img/836a426b70cc698b151086c2f949a2e7_201.png)

![](img/836a426b70cc698b151086c2f949a2e7_202.png)

Then maximum how many comparisons it is taking for searching an element。

 So that depends on the height of a tree。 So at most， how many comparisons are required。

 If I am searching for an element at index 7， that is 25， it will take four comparison。

 So maximum comparisons are dependent on the height of a tree and the height of a tree is log N。



![](img/836a426b70cc698b151086c2f949a2e7_204.png)

That's 4，1，2，3，4。Right， so actually， this is how many。 see， there are8 elements here， then four。

 then two， then one。 or from here， if I see one， then they are becoming 2， then they are becoming 4。

 then they are becoming 8。 So how many times they are getting multiplied。

 How many times they are getting multiplied。 That is  four times。 So that is  four levels are 4。

 So approximately， if I take these elements has 15 plus one， that is 16 elements。

 then log 16 base 2 S 4。

![](img/836a426b70cc698b151086c2f949a2e7_206.png)

![](img/836a426b70cc698b151086c2f949a2e7_207.png)

Right， full comparison required。So the time taken by binary researchers。Login。So from the tree。

 we can analyze。And one more thing， if I am searching for any element。

If I am searching for an nearly man which is not present， then what happens。

 Suppose I am searching for 65。Then firstt will go here， mid 8， then on to 12。Then on 14， then on 15。

 Then it will try to go that side， but the element is not there。 So it will stop on this side。



![](img/836a426b70cc698b151086c2f949a2e7_209.png)

Same way， if I am searching for any elements that are lying in between 55 and 62。

 it will stop on this side。

![](img/836a426b70cc698b151086c2f949a2e7_211.png)

Likewise， I can draw some external notes to represent those elements which are not present in the list。

And how much time it will take for unsuccessful search，1，2，3，4 stop， so again。

 maximum four comparisons are required。Now， one more。

If I am searching for any key minimum how much a time it may take。

 if I am searching for a key element present in the middle that is 29。

 then it will take only one comparison。 So this is order of one。

 then maximum how many comparison it takes。 it depends on the height of a tree。 that is log n。

 So this is order of log n。 So the minimum time of binary search as order of a maximum time is log n。

 So best case is， if you are searching for a key element in the middle of a list。 That is best case。

 and the time is one。

![](img/836a426b70cc698b151086c2f949a2e7_213.png)

![](img/836a426b70cc698b151086c2f949a2e7_214.png)

W case is you are searching for a key element present in the leaf。

And the timeless log in verse here is times log in。That's it。

 This is the analysis of binary search algorithm。 We have seen how it works。

 We have written an algorithm and traces that algorithm in form of the tree。

 And the time we are getting is。

![](img/836a426b70cc698b151086c2f949a2e7_216.png)

Loin。If you want to know the average time， if you want to know the average time。

 then you have to add the time for each and every element and divide by number of elements。

T the time for each and every element。 So for this one comparison and two comparison，3 comparison。

4 comparison。3 for for every element， you should take that and divide it one number of elementsminance。

 and then you get average。 and the average also you get in the form of login。

If you analyze this fund。So best case is， best case time is one。 worst case time is login。

 average case time will also be login。

![](img/836a426b70cc698b151086c2f949a2e7_218.png)