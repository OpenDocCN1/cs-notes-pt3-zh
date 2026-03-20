# 【精译⚡算法导论】AbdulBari p31 p30 2.6.2 Binary Search Recursive Method -BV1hhPXeTEWM_p31-

Let us write a recurscival algorithm for binary research。

Right as when the research is following divide conquer strategy， let us see a recursive algorithm。

 So here I write algorithm。

![](img/92f7eb167477426dac9426b70cbdab58_1.png)

![](img/92f7eb167477426dac9426b70cbdab58_2.png)

。Ad binary。

![](img/92f7eb167477426dac9426b70cbdab58_4.png)

Search。

![](img/92f7eb167477426dac9426b70cbdab58_6.png)

What are the parameters it takes。L， high and key。

![](img/92f7eb167477426dac9426b70cbdab58_8.png)

![](img/92f7eb167477426dac9426b70cbdab58_9.png)

In dividing conquer strategy， we say that if the problem is large。

 we split it into sub problems and solve。Then you should also mention define what is a small problem。

 When do you say it small。 So if you are able to say this is small。

 then only you can say the other problems are large。 Yes， I say that the size of 15 is large。

 Then what is small， If there's a single element， then this is small。

 So how do you solve it a single element。

![](img/92f7eb167477426dac9426b70cbdab58_11.png)

If。Low is equal to high， Then it means there is a single element。 If low is equal to high。

 theres a single element。 Then what I do， I'll check if。



![](img/92f7eb167477426dac9426b70cbdab58_13.png)

![](img/92f7eb167477426dac9426b70cbdab58_14.png)

Aオ。L is equals to key。 If it is a key， If it is a key， then return that index L。



![](img/92f7eb167477426dac9426b70cbdab58_16.png)

So if there is a single element that is low and higher equal。

 then check if it that is the key element。

![](img/92f7eb167477426dac9426b70cbdab58_18.png)

This is a single element。 See， if it is large， we reduce and reduce it to one element。

 and that one element， if it is a key， then search a successful rate that index L。😊。



![](img/92f7eb167477426dac9426b70cbdab58_20.png)

If there is a single element and it is not a key， then。

Return index0 means the key limit is not found。

![](img/92f7eb167477426dac9426b70cbdab58_22.png)

![](img/92f7eb167477426dac9426b70cbdab58_23.png)

That's it。 There is a small problem。 If there is a single element check， it is a key。



![](img/92f7eb167477426dac9426b70cbdab58_25.png)

Ticket， otherwise， return 0。And the problem islash， what we'll do。Alice。As usual。

 we know we will calculate mid meicals to low plus high divided by 2。 and we check if。

Key is equal to a of M。 that middle element is a key element。 If so， we will return on mid。



![](img/92f7eb167477426dac9426b70cbdab58_27.png)

We find out meet and check if that key element is present in the matter。If not， if yes。

 we will return it。 If not， then we check whether its smaller or greater。



![](img/92f7eb167477426dac9426b70cbdab58_29.png)

If key is less than a of mid。Then if it is less smaller left hand side。

 then we perform that binary search recursively on the left hand side。 See， for this example。

 this will be mid。 So this is low， and this is high。

 So we perform binary search recursively on left hand side。 will perform on the left hand side。

 That is low to mid-1。 so。

![](img/92f7eb167477426dac9426b70cbdab58_31.png)

![](img/92f7eb167477426dac9426b70cbdab58_32.png)

![](img/92f7eb167477426dac9426b70cbdab58_33.png)

![](img/92f7eb167477426dac9426b70cbdab58_34.png)

![](img/92f7eb167477426dac9426b70cbdab58_35.png)

Reone。Are binary research。お。Lu is as it is。 This is mid-1 and key。



![](img/92f7eb167477426dac9426b70cbdab58_37.png)

If key is not equal， key is not less than definitely key is greater。

 So look for the key element on the right hand side。 that is midless  one too high and。



![](img/92f7eb167477426dac9426b70cbdab58_39.png)

![](img/92f7eb167477426dac9426b70cbdab58_40.png)

All on。Our binary search。

![](img/92f7eb167477426dac9426b70cbdab58_42.png)

M plus one。We check from a mid plus one onwards。 That is mid plus one to high and keys， as it is。



![](img/92f7eb167477426dac9426b70cbdab58_44.png)

![](img/92f7eb167477426dac9426b70cbdab58_45.png)

M plus 1，2， Haley。M plus one to high N K is， as it is。 That's it。



![](img/92f7eb167477426dac9426b70cbdab58_47.png)

To losing of elses and unlosing of health。

![](img/92f7eb167477426dac9426b70cbdab58_49.png)

![](img/92f7eb167477426dac9426b70cbdab58_50.png)

Now we have written a divide and conquer algorithm that is recursive algorithm for binary research。

 Now divide conquer algorithm daytime complexities are found using recurnceulation。

 Let us prepare a recurnceulation for this one。

![](img/92f7eb167477426dac9426b70cbdab58_52.png)

If I say this cell algorithm takes T N time。

![](img/92f7eb167477426dac9426b70cbdab58_54.png)

Tell what it is doing。 This is a small problem， right， and this a small This a large problem。

 So in this one， it is calculating mid and also checking conditions。



![](img/92f7eb167477426dac9426b70cbdab58_56.png)

![](img/92f7eb167477426dac9426b70cbdab58_57.png)

So if I take the condition， it will check this one nor this one， right at most。

 it will check two conditions。

![](img/92f7eb167477426dac9426b70cbdab58_59.png)

So I will take these two also。 So 1，1。 Then it is calling by dividing the problem into half either on left side or on the right hand side。

 Anyone one thought of these two， it will call itself for T N by 2。



![](img/92f7eb167477426dac9426b70cbdab58_61.png)

![](img/92f7eb167477426dac9426b70cbdab58_62.png)

DN by度。

![](img/92f7eb167477426dac9426b70cbdab58_64.png)

And when is a small problem， if list size is1， then what it is doing， just making one comparison。



![](img/92f7eb167477426dac9426b70cbdab58_66.png)

This is small。 This is small。 So let me write a recurrent solution。 T N is。Taking one time。

 if number of elements are one， there's a small problem。

If number of elements are greater than one than what it is doing。

 It is calling itself either this one or this one。 So only one time it is calling。

 So this is T N by 2， plus what 1，2，3。 So we write it as constant。 So I'll write it as  one。



![](img/92f7eb167477426dac9426b70cbdab58_68.png)

The cancel。For binary search using divide and conquer strategy。



![](img/92f7eb167477426dac9426b70cbdab58_70.png)

Algothm is calling only one time。 either this left hand side or right hand side， not both。

 So I have written it only T N by2。 Now， this recurnceulation， you are familiar with this one。 Al。

 I have a video for this one。 So this is mentioned there。 T， E， N is equals to。

 this is mentioned there。

![](img/92f7eb167477426dac9426b70cbdab58_72.png)

![](img/92f7eb167477426dac9426b70cbdab58_73.png)

In the title of a video。

![](img/92f7eb167477426dac9426b70cbdab58_75.png)

You can watch that how to solve this one。 And even by master theorem。

 there is a video available for master theorem。 We have already seen it。

 So the time for this one by applying master theorem is。



![](img/92f7eb167477426dac9426b70cbdab58_77.png)

Tat off。Loin。This is one， and this is 2。 So log 1 base 2 is 0， and this is n par 0。 So both are 0，0。

 So it is  one into log n， and it is。

![](img/92f7eb167477426dac9426b70cbdab58_79.png)

1 into login。 So it is login。 So the time complexity of this one is login。

 So we have seen the divide conquer algorithm is also giving the time as login。



![](img/92f7eb167477426dac9426b70cbdab58_81.png)

![](img/92f7eb167477426dac9426b70cbdab58_82.png)

![](img/92f7eb167477426dac9426b70cbdab58_83.png)

That's all I about binary research。

![](img/92f7eb167477426dac9426b70cbdab58_85.png)