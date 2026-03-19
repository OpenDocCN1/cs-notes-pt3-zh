# 【精译⚡算法导论】AbdulBari p41 p40 3.2 Job Sequencing with Deadlines - Greedy Method -BV1hhPXeTEWM_p41-

Hi， our next problem is job sequencing with deadlines。This problem。

 we are going to solve it using3D method。So first of all， we will understand what the problem is。

Already I have an example， through an example we understand what the problem is。

 then we'll see how to solve it using GrD method。

![](img/e2bf43acdaab76056b4ad2c9cf102856_1.png)

So let us know about the problem。C。

![](img/e2bf43acdaab76056b4ad2c9cf102856_3.png)

Here in example， five jobs are given。Five tasks are given。And if that task is completed。

 we will get this profit， so associated with each job， there is some profit。But。

That job must be finished within this deadline， it must be completed within the deadline。



![](img/e2bf43acdaab76056b4ad2c9cf102856_5.png)

Like first job should be completed within a deadline2 and deadline job 2 also two， job  three is one。

 so like that every job is having some deadline。

![](img/e2bf43acdaab76056b4ad2c9cf102856_7.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_8.png)

So the problem is jobs are given every job is having some profit and if you complete the job。

 you will get the profit and you have to complete that job within a deadline。

Now let us understand what all these means。Assume that， assume that there is a machine。



![](img/e2bf43acdaab76056b4ad2c9cf102856_10.png)

On that， each job has to be processed。Each job takes one unit of time for completion。

 this is the assumption。

![](img/e2bf43acdaab76056b4ad2c9cf102856_12.png)

This is the assumption in the problem。Right， so what is this one unit， I will assume this as one R。

 So on a machine， each job needs one R for its completion。

 So you can take an example like DTP operator or see mostly for making a legal documents for on a bond paper you will find people in the market who will prepare documents。

 supposeupp that preparation you take the job。 So here's a typist。And he completes each job in onear。

That's it。 So that example you can take。

![](img/e2bf43acdaab76056b4ad2c9cf102856_14.png)

Now， what is the situation， let us understand。C。

![](img/e2bf43acdaab76056b4ad2c9cf102856_16.png)

Assume that in the morning， he has opened the shop。The moment he has opened the shop。

 these five people are standing there for getting their jobs done。



![](img/e2bf43acdaab76056b4ad2c9cf102856_18.png)

All right， so you have to take the situation to understand the problem。



![](img/e2bf43acdaab76056b4ad2c9cf102856_20.png)

And each person is having his own deadline。 He is saying that I want my job to be done fast in fast R only。

 Can you do it or not， if you can do it， do it， And this person is saying that I am ready to wait for three hours。

 Not doubt。 my job needs only one hour， but I am ready to wait for three years。

 Suppose his morning 9 o'clock。 So he is ready to wait till 21 o'clock。

 and he's ready to wait till 11 o'clock， and hes ready to wait till 10 o'clock。

 So whose job should be done first。 This job should be done first。😊。



![](img/e2bf43acdaab76056b4ad2c9cf102856_22.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_23.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_24.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_25.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_26.png)

But what is the profit we are gaining？If this job is done。

 let us say this is rupees and we get just 10 rupees。 and if this job is done， then we get 20 rupees。

 So obviously， which job should be done first。

![](img/e2bf43acdaab76056b4ad2c9cf102856_28.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_29.png)

Highest profit job should be done first。Yes， now the problem is we want a set of those jobs which can be completed within their deadlines such that the profit is maximized。

 the profit is maximized， so there's a maximization problem。



![](img/e2bf43acdaab76056b4ad2c9cf102856_31.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_32.png)

And what is the constraint in the problem， job must be completed within the deadline。Alright。

 so this is suitable for greedy method because its an optimization problem。 It's a maxim problem。

 So we can apply greedy method。 Now， let us solve this problem using greedy method。

 Let us see how we can apply greedy method。 So first of all。

 how many R are available for that typist to complete the job。



![](img/e2bf43acdaab76056b4ad2c9cf102856_34.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_35.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_36.png)

See one of the person or two people are ready to wil till。2 o'clock or for three hours。

 they are ready to wait。So after that， nobody' is there。

Suppose this is the only job that he have when he has opened the shop and he has to complete this within the deadline。



![](img/e2bf43acdaab76056b4ad2c9cf102856_38.png)

How many slots he is having。

![](img/e2bf43acdaab76056b4ad2c9cf102856_40.png)

From 0 to R to first star， one unit of time。 and this R， he can complete one job。

 then first star to second hour。 he can complete second job。 and second to third。

 he can finish third job。 So it means nobody is ready to wait beyond three units of time，3 hours。

 So he has to finish jobs within these three slots only。 If I give the time。

 this is 9 o'clock to 10 o'clock。 And this is 10 o'clock to 11 o'clock，11 to 21 o'clock。 Now。

 there are only three slots。 How many jobs he can do。



![](img/e2bf43acdaab76056b4ad2c9cf102856_42.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_43.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_44.png)

Deadlines are giving just three slots， so he can do only three jobs out of five。

 He has to select just three so that the profit is maximum。



![](img/e2bf43acdaab76056b4ad2c9cf102856_46.png)

Now， if we apply greeding method and on what basis we will select the objects。

 we will select the objects in the order of their maximum profit。

 So first maximum profit and next maximum， next maximum and so on。



![](img/e2bf43acdaab76056b4ad2c9cf102856_48.png)

So let us see how to solve this one。Who is having highest profit？ This one。

 So you can see already that the jobs are already arranged in the decreasing order of the profit。

 So I have to consider them in the same order。

![](img/e2bf43acdaab76056b4ad2c9cf102856_50.png)

This is having highest profit。Now I will select this job for completion， I will select it。

 I will not perform it， but in which slot I should do he is ready to wait for two units of time means he came at 9 o'clock he is ready to wait till 11 o'clock and his job needs only one unit of time。

 so let us do it in this slot。Now， let us pick up the next job。 Second highest profit is 15。

 And what is his deadline，2。 Now， again， go to 1 to 2。

 He's ready to wait till 11 materials units of time。 but this is already occupied。 Now。

 see if there are any slots available on this site。 Yes， it is available。 So that job， too here。



![](img/e2bf43acdaab76056b4ad2c9cf102856_52.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_53.png)

Now， let us select the next job。 Third job。 its deadline is one。



![](img/e2bf43acdaab76056b4ad2c9cf102856_55.png)

Can we do it， Let us see。

![](img/e2bf43acdaab76056b4ad2c9cf102856_57.png)

1 means what，0 to 1 within this one。 No， this slot is already gone。 So this job is rejected。

 We cannot do this job。 So we have selected already these two jobs。



![](img/e2bf43acdaab76056b4ad2c9cf102856_59.png)

Then what about this job。 This can be done because the deadline is 3。

 so he is ready to wait till 21 o'clock or third unit， and every job needs one unit of time。

 Remember that。 So we will do this in this slot。

![](img/e2bf43acdaab76056b4ad2c9cf102856_61.png)

So that's it。 And what about this job， third authority re occupied。

 Is there any slot free on this site， No， if there is no slot available there。

 you can look for the slots in this site。 So there is no job slot available。



![](img/e2bf43acdaab76056b4ad2c9cf102856_63.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_64.png)

That's all。 We have a solution。 What are the jobs that we are going to do。

 We are going to complete jobs 2， then job 1 and job 4。



![](img/e2bf43acdaab76056b4ad2c9cf102856_66.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_67.png)

And in which sequence we have to do them。 So here， both the jobs are having deadline， too。

 so we can do them in sequence J 1 then J 2 then J 4， or else J 2 to J 1， then J 4。



![](img/e2bf43acdaab76056b4ad2c9cf102856_69.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_70.png)

We can complete them in any of the sequences。 So these are the sequences possible for completing those jobs。



![](img/e2bf43acdaab76056b4ad2c9cf102856_72.png)

As both are ready to wait for two hours， total profit will be。



![](img/e2bf43acdaab76056b4ad2c9cf102856_74.png)

This job is 20 and this job is 15 and the profit of this job is 5， so it is 20 plus 15 plus 5 as 40。



![](img/e2bf43acdaab76056b4ad2c9cf102856_76.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_77.png)

So the total profit that we gain will be 40。 Now， let us solve this here I have a taken table。 Now。

 initially， there is nothing and there is nothing in the solution and the profit is also0。

 Let us start First， which job we will consider job to be considered first job。

 I'll write1 or J1 first job I am considering And first job， as the red line is2。

 we will assign a slot from1 to2。

![](img/e2bf43acdaab76056b4ad2c9cf102856_79.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_80.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_81.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_82.png)

1 to 2。 You remember， we have the slots from 0 to 1 and 1 to 2 and 2 to 3。

 because the maximum deadline is3 here。 So these are the slots available。



![](img/e2bf43acdaab76056b4ad2c9cf102856_84.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_85.png)

Now， solution， as this is included， we have allotted this slot。 job one comes into this solution。

 and what is the profit，2 is the profit。

![](img/e2bf43acdaab76056b4ad2c9cf102856_87.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_88.png)

So this first job is included。

![](img/e2bf43acdaab76056b4ad2c9cf102856_90.png)

Then consider second job。 Okay， J 1 I write J 2。

![](img/e2bf43acdaab76056b4ad2c9cf102856_92.png)

Can you assign a slot to this second job like J1 was here。

 Yes J2 can come here so we will assign a slot from0 to1 and already1 to2 was already assigned to this one So already the two slots are over you see and we have the solution J1 and J2 how much profit we have 20 plus the profit of the second job is 15 so this is 35 Im just keeping it as it is。



![](img/e2bf43acdaab76056b4ad2c9cf102856_94.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_95.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_96.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_97.png)

Now next job to be considered， J3。Third jaw as a deadline is one。0 to1 already occupied。

 so no slot is assigned and everything remains the same and jobs are J1 and J2 only。

 and this is 20 plus 15 only。 So this job is not included in the solution。



![](img/e2bf43acdaab76056b4ad2c9cf102856_99.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_100.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_101.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_102.png)

Now next job， J 4。J 4， so we can assign a slot 0 to 1 is already gone。1，2，2 is already gone。

 J 4 can be done in。

![](img/e2bf43acdaab76056b4ad2c9cf102856_104.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_105.png)

Slot 2 to 3。 So this is J 4。 So here we have。

![](img/e2bf43acdaab76056b4ad2c9cf102856_107.png)

2，2，3。And the solution is having J1， J2 job4 is selected and it is5 and。



![](img/e2bf43acdaab76056b4ad2c9cf102856_109.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_110.png)

Job 5， it cannot be selected。 So this remains same。 This remains same， and this total will be 40。



![](img/e2bf43acdaab76056b4ad2c9cf102856_112.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_113.png)

Total will be 14。

![](img/e2bf43acdaab76056b4ad2c9cf102856_115.png)

I have taken one more problem for solving this using greedy method as a problem for job sequencing with deadlines。

 we have to follow greedy method， so we decided that we'll select the jobs in the decreasing order of their profits and that saw we may be getting maximum profit。



![](img/e2bf43acdaab76056b4ad2c9cf102856_117.png)

But the constrain is they have to be finished in a deadline。 So how many deadlines are there here。

 What is the maximum time we have to submit any job， maximum time a job can be submitted as4。



![](img/e2bf43acdaab76056b4ad2c9cf102856_119.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_120.png)

So how many slots are available。

![](img/e2bf43acdaab76056b4ad2c9cf102856_122.png)

Zro to1。Then one to 2。

![](img/e2bf43acdaab76056b4ad2c9cf102856_124.png)

2，2， 3，3 to 4。Maximum deadline 4， after that， nobody is ready to wait。

 The job should be completed within that four units of time。

 but every job needs just one unit of time。 So how many slots we have with1，1 unit，4 slots we have。

 Now there is all this by selecting the jobs。 So the first job。 First job。 What is the deadline。

3 is the slot vacant。2 to 3。 Min not beyond 3。 So 2 to 3 Yes job 1 can be done。

 And we got the profit 35。 I'll write just below this one。



![](img/e2bf43acdaab76056b4ad2c9cf102856_126.png)

Then next job J2 deadline is 4。 so check 3 to 4。 Yes， is free。 It can be done。

 So J2 and the profit that we got is 13。

![](img/e2bf43acdaab76056b4ad2c9cf102856_128.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_129.png)

Then J 3， J 3， S red line is 4。 No，3，24 is already occupied。

 Then check this side if it can be done early。

![](img/e2bf43acdaab76056b4ad2c9cf102856_131.png)

Yes， already occupied here。 Yes， it can be done。 See。

 This means that this person is ready to wait for four unit of time。 So for hours。

 we can finish it early also。😊。

![](img/e2bf43acdaab76056b4ad2c9cf102856_133.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_134.png)

We don't have to do it in 3 to 4 slot。 only。 we can finish it early。 Also。

 no doubt he is ready to wait。 but that' slot Al we are doing it for somebody else。

 So let us bring that one here。 So this third job can be done here。



![](img/e2bf43acdaab76056b4ad2c9cf102856_136.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_137.png)

And its profit is 25。

![](img/e2bf43acdaab76056b4ad2c9cf102856_139.png)

The J 4， what is the red line 1 to 2，2，1 to 2， Are they reoccupied， but can it be done early， Yes。

 this slot is free， so job 4 can be done here and its profit is 20。Now job5， job 6 and 7。

 I even don't have to check them because I see that all the slots are already occupied。

 so those jobs cannot be completed。 so when we have limited slots and we have more jobs then we have to select the jobs such that the profit is maximum。



![](img/e2bf43acdaab76056b4ad2c9cf102856_141.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_142.png)

Final profit is。Add all these。 It is 1，10。 Theys solve。 The problem is very simple to solve， right。

 Once you understand the problem， then it's very easy to solve。



![](img/e2bf43acdaab76056b4ad2c9cf102856_144.png)

![](img/e2bf43acdaab76056b4ad2c9cf102856_145.png)

That's all about job sequencing， a deadline。