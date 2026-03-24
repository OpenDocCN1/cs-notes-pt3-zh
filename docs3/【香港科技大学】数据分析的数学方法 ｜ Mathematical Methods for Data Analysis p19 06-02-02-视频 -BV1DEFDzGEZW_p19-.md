# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p19 06-02-02-视频 -BV1DEFDzGEZW_p19-

In this course， I will focus more on the mathematical methods。

Then let's see how to solve this cluster terraining problem mathematically。



![](img/450edea48c4015fcaab2cdb37d1ce175_1.png)

As I have said， I will follow this machine learning equals to representation。Plus， evaluation。Plus。

Optimization framework。So let me do it one by one， let me start from the representation。



![](img/450edea48c4015fcaab2cdb37d1ce175_3.png)

For the representation。The input data， actually， they are well represented by vectors。

 because we are。

![](img/450edea48c4015fcaab2cdb37d1ce175_5.png)

We have already assumed the input data just vectors in R N。So we don't need to represent that。인풋 데이터。

Now we need to represent this learner in our cluster。We needed to。

 because we wanted to group them into different groups。

 we needed to use something to represent different groups。



![](img/450edea48c4015fcaab2cdb37d1ce175_7.png)

Then。😊，Will let。For each point XI， they belongs to some group。

 so Ill just use the CI to denote the group that XI belongs to。



![](img/450edea48c4015fcaab2cdb37d1ce175_9.png)

So then this I is from one to capital n。For example， x1 is in group 2， then C1 equals to 2 and。



![](img/450edea48c4015fcaab2cdb37d1ce175_11.png)

On the other hand， I also need a GJ means to denote the different groups。

Gi1 is just group 1 contains which vectors。So that is G G J is just the。Ind is I。

 such that C equals2 J。For example， x1 belongs to group 2。Then one should be in G2。So in this case。

 J is just from one to。To K， the number of Gs are just the number of groups。



![](img/450edea48c4015fcaab2cdb37d1ce175_13.png)

This representation is a little bit redundant。Because if we know C I， of course。

 we can get a GJ just by use definition。 If we know GJ， obviously， we， we know this C I。

so they have a one to1 correspondence between CI and GJ CI， if we know C。So then I can have GJ。

Just use this formula。RightIf I know GJ， of course， I know C I。And for each vector。

 they must be in one of the GJ， then I just get the C equals to the J。



![](img/450edea48c4015fcaab2cdb37d1ce175_15.png)

So there is a one to one correspondence between CI and GJ。 There are actually some。

 there are some redundancy contained in CI and GG。 In fact， I only need to get one of them。



![](img/450edea48c4015fcaab2cdb37d1ce175_17.png)

Either I can get a CI or I get a GJ， that's enough。



![](img/450edea48c4015fcaab2cdb37d1ce175_19.png)

For our group representation。

![](img/450edea48c4015fcaab2cdb37d1ce175_21.png)

And对。What's more， we even introduce a more concept， which is called the representative vector。



![](img/450edea48c4015fcaab2cdb37d1ce175_23.png)

I call it Z Chi。 So just be there。Represent。T to。Vectctor。



![](img/450edea48c4015fcaab2cdb37d1ce175_25.png)

胭之住。For each group DJ。I just produce a representative vector。Later。

 you will see actually this is the center of this group。So this is just for J from 12 k。

Notice that this ZJ is not necessary。Yin。X 1，2， x capital。



![](img/450edea48c4015fcaab2cdb37d1ce175_27.png)

What I mean is that here this ZJ， this representative vector can be artificial。

 it's not necessary in the given input data。

![](img/450edea48c4015fcaab2cdb37d1ce175_29.png)

This CJ is just some typical vector in this group J， but this typical vector might not be。



![](img/450edea48c4015fcaab2cdb37d1ce175_31.png)

Can be artificial。It can be produced by the algorithm。



![](img/450edea48c4015fcaab2cdb37d1ce175_33.png)

So anyway， so this is just the representation。 I use C I and GJ just to representing the grouping。

 how to group those。

![](img/450edea48c4015fcaab2cdb37d1ce175_35.png)

Points。I introduced the ZJ， just before。To represent those vectors in the same group。Better。

Then we use a representative。Vor to represent this group， E J。



![](img/450edea48c4015fcaab2cdb37d1ce175_37.png)

This is their representation。With the representation， now we need to evaluate each CIGJ and ZJ。

 I want to pick up which CIGJ and ZJ is the best for our clustering task。

 then I need to do the evaluation。

![](img/450edea48c4015fcaab2cdb37d1ce175_39.png)

I needed to set up a standard that show that this CIGJ and VJ sought to satisfy。Let's see。Within GG。

Within the same group， they should be close to each other。Right。

 so then we have a representative vector in in in in GJ， which is ZJ。

 So then I just require all vectors should be close to ZJ。



![](img/450edea48c4015fcaab2cdb37d1ce175_41.png)

Then。To achieve this goal， I want all vectors in in G J in in this group。

 J should be close to its representative。

![](img/450edea48c4015fcaab2cdb37d1ce175_43.png)

To achieve this， I need to set up a quantitative standard for for， for this。Then， I just defy。

I define an objective function。To measure the closeness of all vectors in GJ to Z G。Now。

 we know if for individual， for two individual vectors， we can use the norms to。

Mayor their closeness。 right， So if it for some X I， if X I is in J。For， for any X， I in G J。I want。

 of course， I want this X I close to Z G。So then which means I want this X， I minus Z J， this norm。

Is small。Just means X I is close to Z G。In the Kis algorithm。

 actually what we use here is the two norm squared。We didn't use them。The， the the distance directly。

 because we know that the square function is a monotonically increasing function when the input is positive。

Right。Smaler。22 norm means a smaller two norm squared that they are equivalent。

So then for any XI in GJ， I just want this to be small。Now， we have many， many。

Vctors in G G in the group J。so then what we are going to do that I just。

Which are just to sum up all the vectors in JJ， just the sum。Overall， I such that。This X I is in GJ。

So this function is a quantitative description on how close of vectors in GJ to ZJ。



![](img/450edea48c4015fcaab2cdb37d1ce175_45.png)

So for each lecture in GJ。Its distance to ZJ should be small。Then everyone should be small。

 so their sum should be small。Yeah。So this is that I call this JJ。So of course， we wont。J j small。

Somami is that。The vectors in GJ is closer to the ZJ， the smaller the closer。



![](img/450edea48c4015fcaab2cdb37d1ce175_47.png)

This is the first。Step。Within just consider in one in one group， in one specific group。

 this should be small。

![](img/450edea48c4015fcaab2cdb37d1ce175_49.png)

Now we have K groups。So then consider all groups。So for each group JJ should be small。我 each去。去。

So then we want them， everyone to be small than what we will do we just consider the sum。

 So which means so。Define。We just define J equals to J 1 plus J 2 plus。Its JK。Then， we want't。Jaスも。

Which means that for ECG， I just want EC JJ is small。



![](img/450edea48c4015fcaab2cdb37d1ce175_51.png)

So， then。So then we get an objective here， right， so we just want this J to be small。Then altogether。

 we just saw。We just minimize this J。So what are the variants？What are the variables in this？In this。

You know， J is J 12， JK， right， what are the variables here？What are the unknowns here， Just ZJ GJ。



![](img/450edea48c4015fcaab2cdb37d1ce175_53.png)

So we have many G1 to。CK。Z 1，2， Z， K。Right。So for for each G1 to G K and Z1 to Z K。

 we can define a J。

![](img/450edea48c4015fcaab2cdb37d1ce175_55.png)

Then we wanted to pick those G1 to G K and Z1 to Z K， such that J is minimized。So。

Or if we expand G expand J， we obtain this is the same as I minimize。G one， two g k。



![](img/450edea48c4015fcaab2cdb37d1ce175_57.png)

Z 1，2， Z， K。So J is the sigma。A。You know。This capital J is only the summation of J little J。

 So this little J is from one to K。And each JJ each JJ is defining this way。



![](img/450edea48c4015fcaab2cdb37d1ce175_59.png)

I just copy it。So altogether， we need to solve this。Minimization。



![](img/450edea48c4015fcaab2cdb37d1ce175_61.png)

So in the evaluation step， for each representation of our learner， that is our。



![](img/450edea48c4015fcaab2cdb37d1ce175_63.png)

G and Z actually， we we don't use C here because C C and G are redundant。

 I I only one of them is is enough。 I either use C or use G哎。

 so I used the G and Z here G and Z here。

![](img/450edea48c4015fcaab2cdb37d1ce175_65.png)

![](img/450edea48c4015fcaab2cdb37d1ce175_66.png)

![](img/450edea48c4015fcaab2cdb37d1ce175_67.png)

So for析 G andZ。I， I just assigned an objective to it， A function J to it。

 I want this function to be small。This J can be viewed as cost。

So I want the cost as small as possible。

![](img/450edea48c4015fcaab2cdb37d1ce175_69.png)

So then I just minimize this cost。For different G and Z。



![](img/450edea48c4015fcaab2cdb37d1ce175_71.png)