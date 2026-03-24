# 【香港科技大学】数据分析的数学方法 ｜ Mathematical Methods for Data Analysis p86 14-14-02-视频 -BV1DEFDzGEZW_p86-

Solving a list squares problem is equivalent to solve a normal equation。

There is a geometric interpretation。

![](img/4510d7b04ff027f52e096ad008dc17c1_1.png)

We want to solve the Vta squares problem。I wanted to do some conversion。

 I wanted to introduce a new variable， which is called Y。 Y equals to A X。

Then the least squares problem becomes。Minimize Y in RM。Half of this y minus be the two norm squared。

 but I have a constraint。 This constraint is just y equals to 8 times x。I eliminate this X。

 Y should be a times some X。 or in other words， Y should be in the range of a。Therefore。

 this list square。Is converted to a constrained optimization。InR M。



![](img/4510d7b04ff027f52e096ad008dc17c1_3.png)

Now， in this RM。This whole space is R M because usually M is larger than the number of equations。



![](img/4510d7b04ff027f52e096ad008dc17c1_5.png)

Is more than the number of unknowns。 So M is larger。And the range of a， because a is only m by n。

The range of a is undisal， in general。It's a lower dimension of space in。RM， so this is range of a。

We go back to this problem。 B is a given vector in RM， so B。Might be here。So from here。

 you can see we want to find a Y that is on the range of a such that it is closest to B。



![](img/4510d7b04ff027f52e096ad008dc17c1_7.png)

This is exactly a projection problem。We want to project this be onto them。Rin Jiaofei。

 this will be the wise star。So this is indeed a projection。



![](img/4510d7b04ff027f52e096ad008dc17c1_9.png)

Projecting。Be onto range of a。

![](img/4510d7b04ff027f52e096ad008dc17c1_11.png)

Where this。Y star， we use this relation。 Y should be a X for some X。

 This x is the solution of the original Easter square。 So this y star should be。A times x star。

 then x star is the solution of the list squares probe。Now， in order to find out this。

X star or Y star。 We needed to use the projection theorem。

 recall that the projection onto the hyperplane。 we have proved that this residue has to be orthogonal to this。

Hyperplay。Here should be orthogonal to this range of a。Then we should have that。

This B minus A X star。B minus y star R。Should be orthogonal to the range of a。In other words。

 for any。Zig。RN。This B minus a X star。Should be orthogonal to this A Z。

 because any vector on the range of A is in the form of Az。



![](img/4510d7b04ff027f52e096ad008dc17c1_13.png)

![](img/4510d7b04ff027f52e096ad008dc17c1_14.png)

This inner product is 0。Now， again， I use the formula here。



![](img/4510d7b04ff027f52e096ad008dc17c1_16.png)

A transpose UV equals UAB。So now I move with A here to here， so then I should have a transse here。



![](img/4510d7b04ff027f52e096ad008dc17c1_18.png)

This is。The same as。A transpose。B minus A X star。Z equals0 for any Z on R N。

Since it is true for anything on R， And， I can choose Z to be E I。

 then I will get every component of this。Vectctor should be zero so that this should be a zero vector。

This is just the equivalent to。A transpose B minus a X star。



![](img/4510d7b04ff027f52e096ad008dc17c1_20.png)

Equs 0。Then we obtain that this a transpose a X star。Equals a transpose。

We obtain the normal equation， again。

![](img/4510d7b04ff027f52e096ad008dc17c1_22.png)

So this normal equation can also be derived in this geometrical way。

We view we convert this list square to a projection problem。

It is equivalent to re project this B onto the range of a。

 then this B minus y star or B minus Ax star has to be orthogonal to the range of a。

Then by some algebra， we just obtained the normal equation。



![](img/4510d7b04ff027f52e096ad008dc17c1_24.png)

![](img/4510d7b04ff027f52e096ad008dc17c1_25.png)

Or we can just use the gradient。Use that。Results that we obtained in the previous section to obtain this。



![](img/4510d7b04ff027f52e096ad008dc17c1_27.png)

Normal equation， the solution X star of a least square must satisfy the normal equation。

A solution of the normal equation must be a solution of the least square。

So we characterized the solution of that。This the squares problem that is it is just given by the normal equation。

Therefore， to solve。A list squares problem。 You may just solve this normal equation。

That is actually many numerical software package do。

But we can also use a gradient descent and iterative algorithm to solve these list squares。



![](img/4510d7b04ff027f52e096ad008dc17c1_29.png)

We may use the gradient descent。The least， the least squares。

We just just produce juice X size plus one。Given given X， K by by X， K K minus gradient of F。

Now the gradient is a transpose Ax minus B。

![](img/4510d7b04ff027f52e096ad008dc17c1_31.png)

Apha K， A transs of A X K。Minus B。4 k equals 0，1，2， and so。This is the gradient。

As I have mentioned for many times。How to choose alpha K is crucial in the gradient the distant algorithm。

But here it is not a big problem because we can have an optimal choice of RFK。How to choose。阿法系。

We choose。And all。O。Because our X K plus1 is in this form。And assume that this alpha K is unknown。

So we view this alpha K as a variable。We choose the best ava。Because our answer goal is minimize。

This half of a X minus B2 norm squared。Now， this X in the next iteration is choosing in this form。

 So I just plug it in the form of this Xk plus1 here。



![](img/4510d7b04ff027f52e096ad008dc17c1_33.png)

X，k。Mus alpha K， a transpose。A Xk。Minus B。In this form。We need to tune this alpha K。

 Then I just view this alpha K is a。Unknown is a variable。

 Then I minimize this objective function in the least square to obtain the best alpha K。

In particular， we are。Remove with a subscript here。Find the alpha， such that。This A X。

 K plus 1 minus B， the two norm squared is minimized among all alpha。



![](img/4510d7b04ff027f52e096ad008dc17c1_35.png)

This is the alphapha K。So this alpha K will be the optimal。Once this gradient direction is chosen。

 the only degree of freedom we can choose is the alpha。

T the optimal alpha such that the objective function in the least square is minimized。Again。

 we need to solve this minimization。To solve this minimization， I will call。This。

This is a function of alpha。 I just call this one G of alpha。



![](img/4510d7b04ff027f52e096ad008dc17c1_37.png)

Now for的是几 function。

![](img/4510d7b04ff027f52e096ad008dc17c1_39.png)

It is convex。Because this function is a quadratic function on alpha。

Under the coefficient before the alpha squared the term is just a positive。



![](img/4510d7b04ff027f52e096ad008dc17c1_41.png)

Then the graph of this G of alphava looks like this。



![](img/4510d7b04ff027f52e096ad008dc17c1_43.png)

Thus， G of alpha is convex。 You can check it and。Therefore。

 alpha K is a solution of this minimization， is equivalent to the G prime at alpha K equals 0。

By some calculation， you will find the form of alpha K。 Al K is just given by。A transpose of A X， K。

Minus b， the two norm squared divided by。A A transportse of A X， K minus B。The two norm squared。

The calculation of this alpha K is tedious。It is skipped。

 You can check it if you are interested in that。Therefore。

 this choice of alpha K is the optimal step size。So finally we get the algorithm。



![](img/4510d7b04ff027f52e096ad008dc17c1_45.png)

We first choose our our alpha K by this formula。Once alpha K is choosing。

 we just obtain our Xk plus1。

![](img/4510d7b04ff027f52e096ad008dc17c1_47.png)

By this formula。This is the final algorithm for solving this instant squares problem。This is Cardia。

Sep is the decent。Because here we used the optimal step size。So that the descent is the steepest。

And also， this implementation is not optimal。Because we need to compute this a times X K。

 A transport times Xk for many times。For at least three times here。

We have some efficient implementation。

![](img/4510d7b04ff027f52e096ad008dc17c1_49.png)

We just use a variable to denote this a transs AxK minus B。Then we use this G K。

To replace a transpose of A X， K。Mus B。With G， K， our alpha K will be very simple。 It is just G， K。

The norm squared over A G K。Then norm squared there。And X， K。Plus，1， just X K minus alpha K G K。



![](img/4510d7b04ff027f52e096ad008dc17c1_51.png)

And that we needed to do。Tring it to a loop。And， of course， we need to initialize。X 0。

This is an implementation of the steepest descent。It works very well。But of course。

 we have more advanced， more efficient algorithms for the list squares。It is the conjugate gradient。

CG method， The CG method actually is only a variant of this steepest descent。

 It's the steepest descent with momentum。If you wanted to know this。

You need to take an advanced optimization course。

![](img/4510d7b04ff027f52e096ad008dc17c1_53.png)