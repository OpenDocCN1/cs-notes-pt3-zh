# 【精译⚡算法导论】AbdulBari p59 p58 4.8 Reliability Design - Dynamic Programming -BV1hhPXeTEWM_p59-

The problem is reliability design。In this video， I'll explain you what the problem is。

 then I'll take a example problem from the textbooks mostly found in the textbook。

 then I'll explain how to solve that problem。

![](img/7f67b304b9f0c6d7908b5db17273779f_1.png)

First of all， let us understand what the problem is see the problem is we have to set up a system。

Okay。Set up a。40张。A system consists of some devices。 Let us say D1， D2， D3 D4。

 I have some devices and have to take these devices and set up a system。 For example。

 I have to set up a studio for that。 I need a board and the camera and the batteries and lights and markers。

 These things I need in the setup。 So let us call them as devices。 Now。

 each device is having some cost， say there is some cost cost one cost to cost 3 and cost 4。

And each device is having some reliability means what is the probability of working good like board。

 The reliability is high Light， The reliability is low。

 They may go off and the marker of the reliability is much lower。 It may dry up。 Select that。

 what is the chances that it works perfectly。 That is called as reliability。

 So each device is having some reliability。😊。

![](img/7f67b304b9f0c6d7908b5db17273779f_3.png)

Now， what the problem is， see， the reliability of devices may vary。

 Suppose the reliability of each device is 0。9。 each device is 0。9。

 Then what is the reliability of entire system。 That is product of all the reliability。 So it is 0。

9 power 4。 This is。

![](img/7f67b304b9f0c6d7908b5db17273779f_5.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_6.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_7.png)

。6，5，6，1。

![](img/7f67b304b9f0c6d7908b5db17273779f_9.png)

See， though the reliability of each device is 0。9， but the reliability of entire system is 0。

65 means there are 35% chances that system may fail。

 so it means if I talk about a studio setup so I have to stop recording because of any of the reason that the lights are gone or the camera is not working or marker is dried。

 so this could be the reasons I have to stop my recording。

 so there are 35% chances 65% chances it works perfectly。

So I have to improve my system and the problem is I want to set up a system such that the reliability is maximum。

So what I should do， I should have more than one copies of markers。

 or should have more than one cameras。 I should have more than one lights。

 See if one camera is of or gone damaged， then I should use another camera in its place。

 If the light is gone because of fluctuation， then I should have another set of lights for continuing my recording。

 So that's it。 So I should have the multiple copies of these devices。

 we will call these that these devices are connected in series。

 So now we should have the devices connected in parallel。 So same copies。

 multiple copies of first device and multiple copies of second device。

 So I should have multiple copies。😊。

![](img/7f67b304b9f0c6d7908b5db17273779f_11.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_12.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_13.png)

So we say that these are stages at each stage， stage1 and stage 2， stage 3。

 stage 4 at each stage will have the multiple copies where one of the copy may be working。

 the rest of the copies will be acting as backup if this fails。

 then this will continue working in its place。 So we say they are in parallel and the system is designed with taking parallel copies of devices。

 So what is the meaning here。 So that is I should have the multiple copies of marker or I should have multiple copies of lights。

 that is the meaning Then if I have multiple copies whether the reliability of each will increase。



![](img/7f67b304b9f0c6d7908b5db17273779f_15.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_16.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_17.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_18.png)

Now， let us see how to know whether the reliability of this stage has improved or not。

 So Im having three copies。 The reliability of each device is 0。9。 If I have three copies。

 what will be the reliability of the stage。 So let us learn how to calculate the reliability of a stage。

 See for the first device， the probability of working word is 0。9。

 Then one minus R1 that is the probability of not working good as 0。1。

 then I have three copies of this one。 See， I have three copies here。 So for three copies。

 what is the probability that all three copies has failed。 So all three copies has failed means 0。



![](img/7f67b304b9f0c6d7908b5db17273779f_20.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_21.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_22.png)

Power 3， then this will point 0，0，1。

![](img/7f67b304b9f0c6d7908b5db17273779f_24.png)

This is the probability that all three copies have failed。

 Then1 minus1 minus R1 to the power of three gives me the probability that three copies are working perfectly。

 so that is 0999。 see there is a much improvement in the reliability it was just 09。

 Now the reliability of a stages0999。 Now finally， it means that if I have multiple copies of the same device。

 then the reliability of the system and our system may increase。 and if want maximum reliability。

 So for that I should have the extra amount with me， the extra capital for buying multiple copies。



![](img/7f67b304b9f0c6d7908b5db17273779f_26.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_27.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_28.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_29.png)

So now the actual problem is， if I have some cost with me， C is the cost。

 the total amount in my hand。 and I have to set up a system by buying these devices and connecting them。

 So these devices， how many copies of each device I should buy within that cost such that the total reliability of the system is maximize。

 This is the problem。 Now， let us take an example problem and solve it。 Now， here as an example。

 I have three devices。 and the cost of the devices is given。 Let us say that is in dollars，$30。

$15 and 20 and the reliability of the devices is also given that is 0。9 point and 0。5。



![](img/7f67b304b9f0c6d7908b5db17273779f_31.png)

Then。You为。Is the upper bound so let us understand what this upper bound is see we are trying to set up a system by taking multiple copies so at least one copy I must take so for each device I must take C1 plus C2 plus C3 that is some of C I should take one copy of each so that is 30 plus 15 plus 20 so this will become 65 so definitely I should take one copy of each device then the remaining amount I can spend for buying multiple copies of other devices。



![](img/7f67b304b9f0c6d7908b5db17273779f_33.png)

So what is the remaining amount， So actual cost is given as C。

 So C minus some of all C is the remaining amount。 this is remaining。

So what is remaining1n 5 minus 65 as 40 so $40 are remaining and in that $40 how many copies of first device I can take how many I can take from second device for how many third like that I have to calculate so maximum how many copies I can take for each device so in this 40 I can spend all $40 on the first device only so how many copies I can take so 40 divided by 30 so I can take just one copy。



![](img/7f67b304b9f0c6d7908b5db17273779f_35.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_36.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_37.png)

In this one， so I can take one extra copy Al one copy I said I must take it。

 So how to know this Now let me take it as a formula。

This is the remaining amount in that I have to divide it by C the cost of that device and I should take the floor value plus one copy which I'm already taking plus one so this result remaining amount is $40 and this is $30 this is one then plus one so upper bound is2 so I can take two copies of this device。



![](img/7f67b304b9f0c6d7908b5db17273779f_39.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_40.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_41.png)

This is how we use the formula to find out in the remaining amount how many copies of each device I can take let us do it for the second device see $40 is remaining and the $15 is this one so I can take two copies and plus one that is already there so three copies I can take and similarly this I can take。



![](img/7f67b304b9f0c6d7908b5db17273779f_43.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_44.png)

For the third device I can take 40 by 20 so two copies and plus one copies that I am already having。

 so three copies I can take。 So this means that this gives the upper bound of any device how many extra copies I can take。

 This is the formula So I have upper bound for all this means that after taking one one copy of each by spending $65 in the remaining $40 if I spend all $40 on first device I can take two copies the first actually one that I am taking plus one copy。

 if I spend everything on second device， then total how many copies of second device。

 the one already we are taking here， then remaining two more copies then likewise。

 total three copies here So we have the upper bound for each Now we have to find out how many copies of each device we should take such that the reliability of a system is maximized That's all about the problem I have explained you。



![](img/7f67b304b9f0c6d7908b5db17273779f_46.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_47.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_48.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_49.png)

About the problem。 Now， how to solve it is just like the set method of 0，1 napsack problem。 Now。

 I will show you how to solve this one。 for solving this problem， we will take a set of order pay。

 So each order pay will have reliability and the cost。



![](img/7f67b304b9f0c6d7908b5db17273779f_51.png)

Now first order pay first set set0， this will be having order pair1 and cost is0 see so far nothing I have spent。

 I have not purchased anything there is no system at all so right now the reliability is one starting because reliability will multiply if I take zero then the entire answer will be 0 so that's why we take reliability as1。

Now let us start consider D1 if I consider first device then how many copies I can take I can take two copies if I take only one copy of a device then what happens first device 1 copy device and the copy so the reliability is a 0。

9 multiplied by this one 0。9 and the cost will be how much 030 added。



![](img/7f67b304b9f0c6d7908b5db17273779f_53.png)

So if I take just one copy of the first device， then the reliability will be 0。

9 that is multiplied and the cost is added。 I can take two copies there。

 So I'll prepare one more set， two copies of first device。

 If I take two copies of the device then what will be the reliability of a stage。

 So you remember we have calculated this one for first stage 2 copies we are taking。

 So this is 1 minus1 minus09 whole square。 So this is 1 minus09 this is 01 whole square。 1 minus 0。

01 and the reliability is 0。99。 So this is 0。99 multiplied by one。

 So we get the same thing and we are taking two copies。 So this will be 60。

Will combine these two and form set one。 So this set one is for first device。

 So what are the possibilities we have09 and 30。And。99 and60 if I take one copy。

 if I take two copies。

![](img/7f67b304b9f0c6d7908b5db17273779f_55.png)

That's all， this is the consideration of first device。

Now we are do the same thing for second device let us see consider D2 for second device so I have to prepare this is sets now second device one copy if I take second device one copy what is the reliability 0。

8 and the cost is 15 so that 08 and cost 15 I should multiply with these two other pairs。



![](img/7f67b304b9f0c6d7908b5db17273779f_57.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_58.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_59.png)

Po8 into 09。 So this is 0。72， and the cost is 30， and this is $15。 So this will be 45。干嘛？

Then with this also I should multiply， that is 08 in 2。99。



![](img/7f67b304b9f0c6d7908b5db17273779f_61.png)

。792 and the cost of this device is 15， so 15 added to this will be $75。



![](img/7f67b304b9f0c6d7908b5db17273779f_63.png)

This is one copy we have taken now actually we can take three copies let us take second copy so if I take two copies of this one first of all let me calculate the reliability of this stage if there are two copies point8 is the reliability if there is only one copy。



![](img/7f67b304b9f0c6d7908b5db17273779f_65.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_66.png)

Then if there are two copies， I will calculate here 1 minus-1 minus reliability of second device。

2 copies， And this will be 1-1-08 whole square 1 minus。 This will be0。2 whole square。

 So this will be 1-0。04。 This will be 0。96。 So I'm taking two copies， so the cost will be $30。

 So 096 and 30。 I should multiply and addd with these two order paid。 So 。9 into 096 will be 0864。

 And the cost that is $30， and this is  $30。 it will be $60。 Then next one is。



![](img/7f67b304b9f0c6d7908b5db17273779f_68.png)

096 width this one， this one， so 0。96 into 0。990。9504 and the cost will be 60 plus 3090。

So two copies I have taken， now one thing to observe here。C， when I have two copies。

 the total cost is $90。I am having a 1。5，$95 gone， remaining $15。 Now， if I take this。

That is two copies of。Second device。 Then can I purchase third device。

 Do I have that remaining amount。

![](img/7f67b304b9f0c6d7908b5db17273779f_70.png)

1 not 5， minus 90，15。

![](img/7f67b304b9f0c6d7908b5db17273779f_72.png)

$20 I need $20 in my hand， so based on that， this order payer will become infeasible so we can cut off this one。

Ill just strike off this one so instead of calculating the reliability I could have done it directly just by checking the cost so from now onwards first we will find cost then we will multiply the reliability so in that we can save some calculations。

Now， next。3 copies are possible， so I should take the third copy。 So second device。Third copy。

 So let us see what is the reliability and what is the cost。 So this will be three copies。

 and this is three copy。 So this is 3。 So this is 0，8。 So this is 9，9，2。

 And if you have three copies of 15， this is 45。

![](img/7f67b304b9f0c6d7908b5db17273779f_74.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_75.png)

So I should multiply 0。992 and add 45 in both these order pay。

 this is the result coming from first device。

![](img/7f67b304b9f0c6d7908b5db17273779f_77.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_78.png)

So let me check by adding 45 plus 30 it will be 75 yes we'll be having a remaining amount to buy this one。

 so this is 75 and 0992 and 2。98928。

![](img/7f67b304b9f0c6d7908b5db17273779f_80.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_81.png)

Then。One more this I should multiply an ad with this one，60 plus 45。

 it will be1 not 5 so I cannot buy the third device。

 so no need of this order pair so cut off this one so I'm not calculating it also then I have set2 this is set to is how many order pairs it is having1。

2，3，4 so I'll be reading for order pairs so the order pairs that we got from the second device are。

724，5。7，9，7，5。Im086460。

![](img/7f67b304b9f0c6d7908b5db17273779f_83.png)

And。0892875。

![](img/7f67b304b9f0c6d7908b5db17273779f_85.png)

Now I have to calculate for a third device also， but there is no space so what I do is I will rewrite this one in smaller size so that we get some free space here so that is the last step remaining。

So let me rewrite this again with smaller size。So I have changed the size here I have made it a little small see this is set zero this is for first device one copy。

 one copy two copies and this is the combined form of this one merged of this one then second device first copy two copy and three copy three copies are there so then remaining whatever the other pair we got we have taken。



![](img/7f67b304b9f0c6d7908b5db17273779f_87.png)

Now， one thing we have to do here， see。Rar rate is 0。

72 cost is 4579 so from 72 to 79 it is increasing， reliability increasing cost is also increasing。

 35$30 are added to this one。Now，7，9， then 8，6， So the reliability is increasing， Re is increasing。

 but the cost is from 75 to 60。 How come the reliability increases only if you spend extra money。

 but here you are reducing the amount and the reliability is increasing。 This is wrong。

 So reliability increases， cost should also increase Otherwise you have to cut off one order pay by applying dominance rule and the doance rule says that the first one with higher cost。

 you remove it remove this order pair based on the dominance rule， this order pair is gone。

 So now we are having just three order pairs。 Now let us start working on third device and the third device D 3。

😊。

![](img/7f67b304b9f0c6d7908b5db17273779f_89.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_90.png)

First copy， one copy。 So S 3，1 copy。 So what is the reliability of this third device05 and the cost is。



![](img/7f67b304b9f0c6d7908b5db17273779f_92.png)

20， so multiply with all these three。 So the first one， the reliability is 0。5 is multiply。

 So this is 036。 and the cost 45 plus 20 is 65。And the second this is not there this is 0864 into 0。

5 as 0432 and the cost is 60 plus 20， this is 80。Then。8928 into。5 is4464， and the cost is 20 plus 75。

 This is 95。

![](img/7f67b304b9f0c6d7908b5db17273779f_94.png)

This is when we are taking one copy of a third device now I should take two copies of a third device so for that I should calculate its a reliability see the reliability of third device is 09。

 but if I have two copies how much it will be this is r 3 power 2 so this will be1 minus。



![](img/7f67b304b9f0c6d7908b5db17273779f_96.png)

Po5 square。 So this is 1 minus。05 whole square this is 1 minus0。25。 This is 0。

75 is the reliability of two copies and the cost will be $40 Now these are the things multiply with this and add 40 so one thing I told you that see the total cost now just we are on the third device Lastly there is nothing remaining so the total cost should not exceed one not $5。



![](img/7f67b304b9f0c6d7908b5db17273779f_98.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_99.png)

075 into。72 this will be 54 and the cost is $45 plus 40。 this will be 85 this is done。



![](img/7f67b304b9f0c6d7908b5db17273779f_101.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_102.png)

Now next is 0864 into 2。75， this is 648 and the cost is 60 plus 400。Now， the last one S。

75 plus $40 this will be it will be $115 so this $115 will exceed the total amount we have so no need to calculate the reliability and this will be gone。



![](img/7f67b304b9f0c6d7908b5db17273779f_104.png)

Like I told you， it should be feasible within the given amount， so that is gone。Now， I have to take。



![](img/7f67b304b9f0c6d7908b5db17273779f_106.png)

Third set three copies， so three copies means this will be cube， this will be cube and this is cube。

 so this is 0125 and this will be 875 and this will be 40 plus 43 times this is $60。

Now $60 is there60 in this one。 Yes， we can add so 0。72 into 0。875。

 this will be 63 and the cost is 45 plus 60。 This is1 not 5。And。60 plus。60120 this is not possible。

 so don't take this then 75 plus 60。 This is not possible。 This is 135。 don't take this。

 So we are left with only 63。1 not5 only this order pay now set 3 that is formed is merge all these and purge also。

 so I will write on。36，6，5。43280。4，4，6，4，9，5。See， reliability is increasing， cost is also increasing。

 reliability increasing is perfect。😊，Then 85。 So shall I take 85。5485 C。

 the reliability is increasing， but the cost is decreasing。

 so this will go away then 064 first comes for63， then 64。 So first is 063 and 105。

Then the last one is 064， so I have to take them in order。😡，64。8， comm 100， 100。C，63，64。

 this is increasing， and the cost is 1 not5200 decreasing。 So this is also gone。

 So the order pairs that are remaining are this 1，23 and 4。 Now。

 if you have the final order pay for three devices at the third stage。

 So what is the maximum reliability I'm getting here that is 064800。

 So the reliability of system that can be maximum is 0648。 and the cost will be00。

 So this is the final answer。

![](img/7f67b304b9f0c6d7908b5db17273779f_108.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_109.png)

![](img/7f67b304b9f0c6d7908b5db17273779f_110.png)

Now the question is how many copies of each device I should purchase now。

 so for that I get the answer like this。This order pair 6，4，800， where we got it。 See。

 we have merged these  three， and we got this one。 So that was here， here。 So it means I should take。

2 copies of device 2，3。 So device 3， I should take two copies because I got the answer here。And this。

 we got it by multiplying with these order pairs。 First one was with one This one。

 and the second one was with this one。 So this order pair。

 See the reliability of two copies and the cost is multiplied and added。 We got this one。

 So it was done from here。 This we got where here。 So this is here。 right。

 So this is also for two copies of second device， two copies。😊。

Then this regard by multiplying which one。 See， we multiply these two and got these two answers。

 right， this was multiplied with this one。 So this is from coming from this。

 and this we obtained where here。 So this is just one copy of first device。

 So the answer is first device， one copy， second device， two copies， third device。

Two copies and the cost of the system and the reliability will be this one。 This is the reliability。

 and this is the cost of a system。

![](img/7f67b304b9f0c6d7908b5db17273779f_112.png)

Product of reliability and the submission of it。 So the reliability is this one and the cost is0。

Right total reliability of the system， so we have improved the reliability of entire system if you don't take the multiple copies。

 then the reliability will be less when we have taken multiple copies the reliability has improved。

That's solved with the reliability design。 It is same as 01 Napsack problem。



![](img/7f67b304b9f0c6d7908b5db17273779f_114.png)

I did not make this because there are a lot of calculations。

 so just it is nothing but calculations only， but this is little difficult for the students。

 So I have prepared the video。 So if you face any difficulty， let me know。

 I'll prepare another video for this one。