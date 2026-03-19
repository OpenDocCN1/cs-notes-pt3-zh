# 【精译⚡算法导论】AbdulBari p43 p42 3.4 Huffman Coding - Greedy Method -BV1hhPXeTEWM_p43-

Hi， the topic is Huffman coding。Hoffman coding is a compression technique。

 It is used for reducing the size of data or message。

Suppose you want to store the data in a file so you can store the data in compress form to reduce the size of a file。

When the data is sent over a network， data can be compressed and sent to reduce the cost of transmission In this video。

 I am going to explain you if a normal message is sent what will be the cost and what is the fixed size encoding。

 then what is variable size encoding that is Huffman codingding。Now， let us study the problem。

 I have a message here。 Now， this message， I want to store it in a file。

 or I want to send it over a network。 Then let us understand what will be the cost of a message。

 So the cost of this message or the size of the message will be measured in terms of bits。

 Let us check。 First of all， there are 20 letters in this one。 So the length of this message is 20。

Next。How this message has to be sent。 It has to be sent by using AsI code。

 electronic devices or computers all use。Asi codes for characters or English alphabet。

 So these are all characters。Asi codes are 8 bits。I have used alphabets a to a here。

 so that is easy to understand for us。 So if I say a， it's asI code is 65 and the binary form is。

This one。So total 8 bits， these are 8 bits that are representing decimal 65 and that is representing a Similarlyly。

 if I say B， then it is 66。Theacill  for 6 to 6， likewise。C， D E for everyone we have。 that is 6，6。

7 and 68 and 69。 And here， the binary code will be there。 So 8 Bs are there for each alphabet。 Now。

 if normally， this message is sent 8 B for each alphabet， then total number of bits will be how much。

 as there are 20 alphabets in this message。 So this will be 8 into 20。 That is 1，60 Bs。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_1.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_2.png)

Side of the message will be 1，60 B。Now， this is the simple message sent without encoding。

The size will be 1，60 B。8 bit for each alphabet。 Now， let us look at。

 can we use our own codes instead of ASI codes。How it is possible。 See。

 I am not using all English alphabets or all possible symbols on the keyboard。

 I am not using every symbol from the character set。 I am using only five alphabets。

 that two capital letters。 Then do I need 8 codes，8 B codes for representing just five alphabets。 No。

 few bits are sufficient。 So can I use my own chs with less amount of bits。 Yes。

 so next we will see fixed size codes。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_4.png)

Here I have taken alphabets in this message。 and how many times each alphabet is appearing。

 I have written the count here， or you can also call it as frequency。 A is appearing 3 times 1，2，3。

 Likewise， you can check all how many times they are appearing。 I have written them here。 total。

 there are 20 alphabets。 If you want to see the frequency。 Then you can say this is 3 by 20。

 That is 3 by 20， or this is 5 by 20， because total number are 20。 So this is 6 by 20。

 And you can take the ratios。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_6.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_7.png)

I prefer taking counts that is easy for working。 Even what should be the code。 See。

 I have five characters。 I don't need 8 bits for just five characters。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_9.png)

8 B askci codes are for 1，28 characters or 1，28 symbols， but for only5， let us see。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_11.png)

If I have just one bit。1 bit that either I can write 0 or 1。 So how many symbols I can represent。

 how many characters， only two characters。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_13.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_14.png)

If I have two bits， then how many I can represent， I can write 0，0，0，1，1，0，1，1。

 so I can have four different combination， and each combination can represent 1 symbol。 But I have 5。

 So for that， I can take 3 bits。 So in this how many combinations are possible 02，7。

 That is 8 combinations are possible。 So I will take 5 out of that。 So let us say in 3 bits。

 I will say a is 0，0，0。 B is 0，0，1。 C is 0，1，0。 D is 0，1，1， and E is 1，0，0。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_16.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_17.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_18.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_19.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_20.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_21.png)

I have given my own three bit quotes。I will use this。For ending this message。

And I will read this will reduce the size of the message。 So in me。

 it means here instead of writing ASI code， I will be writing0，0，14 B。And 0，1，0，4， C， likewise。

 go on。When the message is encoded using this one， then what will be the size of the message。

 as we know well that there are 20 characters and each takes three bits， so this will be 60 bits。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_23.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_24.png)

So size of the message will be 60。And one more important thing， we cannot neglect。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_26.png)

What is that when I am sending a message， supposeupp encoded in this one。

 Now how the receiver will know what are the codes。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_28.png)

Even if I store it in a file and then later I want to retrieve。

 how do I remember what are the cores use0，0 means a only is it。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_30.png)

See， for making it easy， I have taken the alphabet A to E here。 the alphabets can be anything。

This can be a。 this can be M。 This can be O。 This can be Q。

 Then how I can know which code is for word。 So I should also have the codes。 That is the table also。

 along with the message。 So this encoded message。 and is the table use this table to decode the message。

 Yes， so message is 60 B。 Then you need the table Also。

 the chart of codes that will help to decode this message。 So let us see， you have to send this one。

 Also， how much size this will take。 See， I have  five alphabets。

 This alphabet should be an original form now。Now， standard is what askci code。

 So I must write aski code of all these。 askci code of all these。 So for this，8 Bs。

 So total how many 5。 So 5 into 8 bits。 This is for what characters are symbols。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_32.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_33.png)

Then for each3 bit code for a， this is the code B， this is the code for everything I should also have the code。

 So total how many5 and how many bits for each code 3。 So this is for codes。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_35.png)

So this makes howage。 This is 40 plus 15。 This is 55。 And what is the size of this original message。

 So message is 60 B， right？ and table or a chart of codes is 55 B。 So total how much this will be 1。

5 Bs。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_37.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_38.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_39.png)

Yes。So total size of the message along with the chart is 1，15 B is not just 60 B。 It is 115 B。

 No doubt the size of the message is reduced， but table is also important。 So it was 160。

 Now it became 115。So around 35 to 40% of reduction in size from 160 to 115。Right。

 so this is one method with fixed size chs。Now we'll go to variable size code and let us follow Hman coding。

 which will still reduce the size of the message。Hauffman encoding。

 Huffman says that we don't have to say， take fixed size codes for the alphabets。

 Some characters or alphabets may be appearing few times less number of times。

 and few may be appearing more number of times。 So if you give small size code for the more appearing characters。

 Then the size of the entire message will be definitely reduced。 So let us see what is his idea。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_41.png)

Already we have this table， all the alphabets。 and how many times they are appearing in a message。

 So that gives the frequency of those alphabets。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_43.png)

Now， Huffman code follows optimal merge pattern。Now， we have to generate our own code。

 So what should be the method for the code。 So Hfman has given an approach for getting our own variable size codes。

 So he says that all those alphabets should be arranged in the increasing order of their count。

 So this is the least one。 and this is the next one and next one and so on。

 So they are arranged in the increasing order of their count or frequencies。 So the first。

 the smallest one then the highest one。 So this optimal merge pattern should be followed on this one。

 So what I should do merge two smallest one and make one node。 So this is two plus3。 This is 5。Now。

 next select two smallerest and form a node。 so 5，4，5，6。

 these are remaining out of this which are two smaller， either I can take this 5。

4 or that 54 so I will take this one， so Ill combine this one with this。 so this is9。Now。

 what are the list I have or the nurse I have 9，5，6 These are the to minimum。 So combine these two。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_45.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_46.png)

This is La。Then combine these two。 two are remaining now。 So this one and this one。

 So this gives what。20。So here we got our optimal merge pattern3。

 So actually for the optimal merge pattern， that is  greedy approach， always select two minimum one。

 and we got this one。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_48.png)

Now， this tree will help us define the codes。 How on the left hand side。

 edges mark them as zeros and on the right hand side edges mark them as one。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_50.png)

That's it。Now， what are the codes for each alphabet， follow apart from root onwards。 so for a。

 what is the code 0，0，1。 So a is 0，0，1。Then， B is1，0。1，0， C，1，1，1，1。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_52.png)

D 0，1。0，1。And a0，0，0。0， zero， zero。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_54.png)

That's it。 These are the new course we have。Now you can see the some code is of three bits and one code is of two bits like that。

 so even we may have the codes with one bit also。Not here in some examples。

 So variable size scoress are there。Now， I can use these chors for encoding my message like B is 1，0。

 C is how much 1，1， C is 1，1。And a is 0，0，1。 B is 1，0。 B is 1，0， and D is 0，1，0，1， gone。

If I use these course， what will be the size of my message。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_56.png)

So for that， how many bits are there for a 3 Bs and how many times a is appearing this is 3 into 3。

9 and two bits and disappearing for five times， into 2，10。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_58.png)

2 bits，2 bits，1，1， appearing for six times， So 6 into 2 to 12。2 bits appearing for four times。

 So 4 into 2，8。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_60.png)

And three bits appearing for two times。 So two into three is 6。 So for entire message。

 I have how many times each character is appearing and their sizes of codes I have taken。

 And I got this one。 Now， total number of bits are 45 bits。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_62.png)

Size of the message is 45 bits。 Once if I encode all， I just。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_64.png)

I just need 45 Bs。So， the message sizes。45 birds。Now， one more thing we should consider。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_66.png)

Along with the message， I should also send this chart or a table or a tree。

 Then only decoding can be done。 Hence， along with the encoded message。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_68.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_69.png)

What is the codes， What are the codes used that should also be there， Then only decoding can be done。

 So somehow this tray should be preserved or the table should be preserved。

 Are you to see what will be the size of the table。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_71.png)

All these alphabets， I should send their ASI codes， the standard code。 So8 bit of ASI code。

How many alphabets are there 5。 So this makes how many40 bits。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_73.png)

Then codes also， I should send。 So this codes， when they are stored。 So how many codes are there。

5 cores。 But what are the number of bits 1，2，3，4，5，6，7，8，9，10112 L。 So this is forming  to 2 bits。

 So together this 40 plus that to L。 So 52 bits are required for3 or a table，3 or table。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_75.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_76.png)

So what is the total size？Message is 45 B。And the table order is 52 Bs， and this will be 97 bits。Yes。

 now you can see that it is still reduced from fixed size chs。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_78.png)

So that's all about Huffman codinging。Now， if you want to know the size of the message that 45。

 you can know it from the tree also。 how see this is the distance。

 how much is the distance 123 and frequency is what2。 So three into2。

 So distance into frequency of each or count of each， you can take sigma。

 Some of all these so this will be distance is 3 and frequency is 2 plus distance is 3 and frequency is 3 plus distance is2 and the frequency 4 distance is2 frequency 5。

And distance is2 and frequency 6。 So this is nothing but this calculation that we got and this will be 45 mi only。

 So if you want to know what will be the size of the entire message from the tree also you can find out by using this formula if you refer a video on optimal merge pattern。

 you find that formulaized defined。Let us see how decoding is done。

This is the message now completely in the binary bits form for the message。For this。

 you must have a34 decoding。So start from root 0， left side，0， left side，1 right side。 This is B。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_80.png)

B。0，0，0，1， completed。 Then again， start from the root 1 right side again， one right side。

 So if we reach the leaf， that is C。 So these two are over。 Then again。

 once you have reached the leaf again， start from the root，1 right side，1 right side。 So this is C。



![](img/0b19cdcd81a73792bf9d818fa3206ce6_82.png)

![](img/0b19cdcd81a73792bf9d818fa3206ce6_83.png)

The next0 left side， one right side。 it is a D。 So these two are complete。In this way。

 this message can be decoded。 And from binary bits， we can get back the original AS code。

 So the receiver can convert the message into ASI code and use it in its machine。

 So inside the machine， it while using， it will not be using the code。 So it has to convert into。

As he quotes， like when you have any zip file or compressed file。

 you have to decompress for using it same way should be decoded and used。

So that's all about halfman coding。

![](img/0b19cdcd81a73792bf9d818fa3206ce6_85.png)