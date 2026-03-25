# 【麻省理工】计算机科学与编程导论 ｜ MIT 6.00SC Introduction to Computer Science and Programming p24 24 -BV1a5BZBkEP6_p24-.f30216

The following content is provided under a creative Commons license。

 Your support will help M I T Opencourseseware continue to offer high quality educational resources for free。

To make a donation or view additional materials from hundreds of M T courses。

 visit M I T OpenCseware at O C W dot M I T dot E Du。

I want to go back to where I stopped at the end of Tuesday's lecture。

When you let me pull a fast one on you。I ended up with a strong statement that was effectively a lie。

I told you that when we drop a large enough number of pins and do a large enough number of trials。

We can look at the small standard deviation we get across trials。

And say that means we have a good answer。Doesn't change much。And I said。

 so we can tell you that with 95% confidence， the answer lies between X and Y， where we had the。

2 standard deviations from the mean。That's not actually true。

I was confusing the notion of a statistically sound conclusion with truth。

The utility of every statistical test rests on certain assumptions。

So we talked about independence and things like that。 But the key assumption。

Is that our simulation is actually a model of reality。U。

You can recall that in designing the simulation， we looked at Buffon depl mathematics。

And did a little algebra， which from which we derived the code， wrote the code， ran the simulation。

 looked at the results， did the statistical results and smiled。Well。Suppose。

I had made a coding error。 So， for example， instead of that for there。

 which the algebra said we should have， I had mistakenly typed a 2。Not an impossible error。 Now。

 if we run it。What we're going to see here。Is that it converges quite quickly。

 It gives me a small standard deviation。And I can feel very confident that my answer that pi is somewhere around 1。

569。😊，Well， it isn't， of course。We know that that's nowhere words is close to the value of pi。So。

 but there's nothing wrong with my statistics。It's just that my statistics are about the simulation。

 not about pi itself。So。What's the moral here before believing the results of any simulation。

We have to have confidence that our conceptual model is correct。And。

That we have correctly implemented that conceptual model。Well， how can we do that？Well。

 one thing we can do is test our results against reality。So if I ran this and I said pi is about 1。

57。I could go draw a circle， and I could。Crudely measure the circumference。

 And I would immediately know I'm nowhere is close to the right answer。

And that's the right thing to do。 And， in fact， what a scientist does。

 when they use a simulation model to derive something。

 they always run some experiments to see whether their derived result is actually。

 at least plausibly correct。Statistics are good to show that we've got the little details right at the end。

 but we've got to do a sanity check first。So that's a really important moral to keep in mind。

 Don't get seduced by a statistical test and confuse that with。Truth。All right。I now want to move on。

To use look at some more examples that do the same kind of thing we've been doing。And， in fact。

 what we're going to be looking at is the interplay。Between physical reality。Some physical system。

 just in the real world。Some theoretical models。Of the physical system and computational models。

Because this is really the way modern science and engineering is done。

We start with some physical situation。And by physical。

 I don't mean it has to be bricks and mortar or physics or biology。

 The physical situation could be the stock market。 if you will， some real situation in the world。

We use some theory to give us some insight into that。

 And when the theory gets too complicated or doesn't get us all the way to the answer。

 we use computation。And I now want to talk about how those things relate to each other。So imagine。

 for example， that you're a bright student in high school biology， chemistry or physics。

A situationation probably all of you have been in。And you perform some experiment to the best of your ability。

But you've done the math。 and you know， your experimental results don't actually match the theory。

What should you do？嗯。Well， I suspect you've all been in this situation。

 You could just turn in the results and get。And risk getting criticized for poor laboratory technique。

Some of you may have done this。 More likely what you've done is you've calculated the correct results。

And turn those in。😡，Risking some suspicion that they're too good to be true。But being smart guys。

 I suspect what all of you did in high school is you calculated the correct results。

 looked at your experimental results and met somewhere in between to introduce a little error。

 but not look too foolish。 Have any of you cheated that way in high school。Yeah， well， all right。

 We have about two people who admit it。 The rest of you are either exceedingly honorable or just don't want to admit it。

I confess I had fud experimental results in high school， but no longer I have seen the truth。

All right。To do this correctly。You need to have a sense of how best to model not only reality。

 but also experimental errors。Typically， the best way to model experimental errors。

 and we need to do this， even when we're not attempting to cheat。

Is to assume some sort of random perturbation of the actual data。And in fact。

 one of the key steps forward， which was really Gaus's big contribution。

 was to say we can typically model experimental error as normally distributed。

As a Gaussian distribution。So let's look at an example。 Let's consider a spring。

Not the current time of year or a spring of water， but the kind of spring you looked at in in 8，01。

 right， the things you compress with some force， then they expand or you stretch。

 and then they contract。Springs are great things。 We use them in our cars and our mattresses。😊。

Seat belts， we use them to launch projectiles， lots of things。And in fact， as we'll see later。

 they're frequently occurring in biology as well。嗯要。I don't want to delabor this。

 I presume you've all taken 801。 Do they still do springs in 801。Yes， good。 alright。So as you know。

 in 1676， maybe didn't know the date。 the British physicist， Robert Hook。Forulated hook's law。

To explain the behavior in springs and the law is very simple。It's F。Equals minus。Kx。In other words。

 the force F stored in a spring。Is linearly related to X。

The distance the spring has been either compressed or stretched。Okay， so that hooks law。

 you've all seen that。The law holds for a wide variety of materials and systems。

Including many biological systems， Of course， it does not hold for an arbitrarily large force。

All springs have an elastic limit。And if you stretch them beyond that， the law fails。

Has anyone here ever broken a slinky that way？We've just taken the spring and stretched it so much that it's no longer useful。

 Well， you've exceeded its elastic limit。The proportionate of constant here， K。

Is called the spring constant。And every spring has a constant。K， that explains its behavior。

If the spring is stiff， like the suspension of the automobile。K is big。If the spring is not stiff。

 like the spring in a ballpoint，10 K is small。The negative sign is there to indicate that the force exerted by the spring is in the opposite direction of the displacement。

If you pull a spring down， the force exerted by the spring is going up。Knowing。

The spring constant of a spring is actually a matter of， of considerable practical importance。

It's used to do things like calibrate scales one can use to weigh oneself。

One wants to know the truth。U。Atomic force microscopes， lots of kinds of things。And， in fact。

 recently， people have started worrying about thinking that you should model DNA as a spring。

And finding the spring constant for DNA turns out to be of。

 of considerable use in some biological experiments。All right。

So generations of students have learned to estimate springs using this very simple experiment。

You've probably most of you have done this。Get a picture up here。 Allright。

So what you do is you take a spring。And you hang it on some sort of apparatus。And then you put。

A weight of known mass at the bottom of the spring。And you measure how much the spring has stretched。

You then can do the math if f equals minus Kx。We also have to know that F equals M times a mass times acceleration。

We know that on this planet， at least， the acceleration due to gravity is roughly 9。

81 meters per second per second。And we can just do the algebra， and we can calculate K。

So we hang one weight in the spring。We measure it， we say we're done。

We now know what the K is for that spring。Not so easy， of course。

 to do this experiment if the spring is a strand of DNA。

And so you need a slightly more complicated apparatus。To do that。

This would be all well and good if we didn't have experimental error。But we do。

Any experiment we typically have errors。 So what people do instead is rather than hanging one weight on the spring。

They hang。Different weights， weights of different mass。

 They wait for the spring to stop moving and they measure it。 And now they have a series of points。

And they assume that， well， I've got some errors。 And if we believe that our errors are normally distributed。

 some will be positive。 some will be negative。 And if we do enough experiments。

 it will kind of all balance out and we'll be able to actually。

Get a good estimate of the spring constant K。I did such an experiment。Put the results in a file。

 this is just the format of the file， the first line tells us what it is。

 it's a distance in meters and a mass in kilograms。

And then I just have the two things separated by a space， in this case。So my first experiment。

 the distance I measured， was 0。0865。 and the。Weight was 0。1 kilograms。All right。

 so I've now got the data。So that's the physical reality I've done my experiment。

I've done some theory。Telling me that how to calculate K。 And now I'm going to put them together。

And write some code。So let's look at the code。We'll skip over this。

 and I'll comment this out so we don't see Pi get estimated over and over again。

So the first piece of code is pretty simple。It's just getting the data。And again。

 this is typically the way one ought to structure these things。

 I O input output is typically done in a separate。Function so that if the format of the data were changed。

 I'd only have to change this and not the rest of my computation。It opens the file。

Discards the header。And then， uses split。To。Get the x values and the Y values。All right。

So now I just get all the distances in all the masses， not the x's and the y's yet。

 just distances in masses。Then I close the file and return them。Nothing that you haven't seen before。

Nothing that you won't get to write again and again and again。Similar kinds of things。

Then I plot the data。 So here we see something that's。

A little bit different from what we've seen before。

So the first thing I do is I get my X and Y by calling get data。Then I do a type conversion。

What get data is returning is a list。I'm here going to convert a list to another type called an array。

😡，This is a type implemented by a class supplied by P labb。

 which is built on top of something called nu Pi， which is where it comes from。

An array is kind of like a list。It's a sequence of things。There are some list properties， it。

 some list operations， methods I'm not available， like a pen。

But it's got some other things that are extremely valuable。 For example。

 I can do point wise operations on an array。So if I multiply an array by3。

 what that does is it multiplies each element by 3。If I multiply one array by another。

It does cross products。Okay， so they're very valuable for these kinds of things。 Typically in Python。

 one starts with a list because lists are more convenient to build up incrementally than a raise。

And then converts them to an array so that you can do the math on them。

For those of you who've seen MA Lab， you're very familiar with the concept of what Python calls an array。

those of you who know C or Pascal， what it calls an array。

 has nothing to do with what Python or Py labb calls an array。So。Can be a little bit confusing。

Anyway， I convert them to a raises。And then what I'll do here is now that I have an array。

 I'll multiply my X vows by the acceleration due to gravity， this constant 9。81。

And then I'm just going to plot them。Alright， so let's see what we get here。

So here I've now plotted the measured displacement of the spring。啊。Force in Newtons。That's the。

In standard international unit for measuring force。

 It's the amount of force needed to accelerate a mass of 1 kg at a rate of 1 m per second per second。

So I app plotuded the force in Newton's against the distance。In meters。Okay。Now。

I could go and calculate K。Well。How am I going to do that？Well， before I do that。

I'm gonna do something to see whether or not my data is sensible。What we often。

Do is we have a theoretical model。And the model here is that。The data should fall on a line。

 roughly speaking， modular experimental errors。I'm going now find out what that line is。

Because if I know that line。I can compute K。How does K relate to that line？So I plot a line。

And now I can look at the slope of that line， how quickly it's changing。

And K will be simply the inverse of that。How do I get the line。Well。

 I'm going to find a line that is the best approximation to the points I have。So if， for example。

I have two points。A point here and a point here。I know I can quote。

 fit a line to that curve to those points。And it will always be perfect。It will be a。

So this is what's called a fit。Now。If I have a bunch of points。Sort of scattered around。

I then have to figure out， okay， what line is the closest。To those points， what fits it the best。

 And I might say， okay， it's a line like this。But in order to do that。

 in order to fit a line to more than two points。😡，I need some measure of the goodness of the fit。

Because what I want to choose here is the best fit。What line is the best approximation。

Of the data I've actually got。But in order to do that， I need some objective function。

That tells me how good it。How good is a particular fit。

It lets me compare two fits so that I can choose the best one。Okay， now。If we want to look at that。

 we have to ask， what should that be？There are lots of possibilities。 One could say， all right。

 let's find the line that goes through the most points that actually touches the most points。

The problem with that is it's really hard to， and it may be totally irrelevant。And in fact。

 you may not find a line that touches more than one point。So we need something different。

And there is a standard measure that's typically used。And that's called the least squares fit。

That's the objective function that's almost always used in measuring how good any curve or how well。

 Excus me。 Any curve fits a set of points。What it looks like。Is the sum。From I equals 0。To I equals。

The L。Of the observed point。-1， just because of the way things will work in Python。

 But the key thing is what we're summing。Is。The observed。At point I。Minus the predicted。😡。

At point I squared。And since we're looking for the least squares fit， we want to minimize that。

The smallest difference we can get。So there's some things to notice about this。Once we have。A quote。

 fit in this case， a line for every x value。The fit predicts O Y value。Right。

 that's what our model does。A model in this case will take the independent variable。X， the mass。

 and predict。The dependent variable， the displacement。But in addition to the predicted values。

 we have the observed values。These guys。And now we just measure the difference between the predicted and the observed。

 square it。And notice， by squaring the difference。We have discarded whether it's above or below the line。

 because we don't care。 We just care how far it's from the line。And then we sum all of those up。

 And the smaller we can make that， the better our fit is。Makes sense。So now。

 how do we find the best fit。Well， there are several different methods you could use。

You can actually do this using Newton's method。嗯。Under many conditions。

 there are analytical solutions。 So you don't have to use approximation。 You can just compute it。

And the best news of all， it's built into Pwab。So that's how you actually do it。

 You call the P labb function that does it for you。That function。Is called polyfit。Polyfit。

Takes three arguments。It takes。All of the observed X values。All of the observed Y values。

And the degree of the polynomial。So I've been talking about fitting lines， as we'll see。

 polyfit can be used to fit polynomials of arbitrary degree to data。So you can fit a line。

 You can fit a parabola。 You can fit a cubic。I don't know what it's called。

 You can fit a10th order polynomial， whatever you you choose here。And then， it returns some values。

So if we think about it being aligned。We know that it's defined by the y value。Is equal to Ax。Plus。

 B。Some constant times， the x value plus B， the y intercept。So now let's look at it。We see here。

In fit data。What I've done is I've gotten my values as before。

And now I'm going to say A B equals pi labda polyfi of x values， Y values and one。

 since I'm looking for a line。The degree is one。Once I've got that。

 I can then compute the estimated y values。A times p lab dot array。

 I'm con the X values into an array。 Actually， I didn't need to do that。 did I。

 since I'd already done it。 That's O。Plus， B。And now I'll plot it and。By the way。

 now that I've got my line。I can also compute K。And let's see what we get。All right， I Fiddle line。

And I've got a nice。 I've got a linear fit。 And I said， my spring constant K is 21 point。

AndI've rounded it to five digits， just so it would fit nicely。On my plot。Okay。The method。

That's used to do this in P lab， is called linear regression。Now。

 you might think it's called linear regression because I've just used it to find a line。 But。

 in fact， that's not why it's called linear regression。

Because we can use linear regression to find a parabola or a cubic or anything else。

The reason it's called。Linear。Well， let's look at an example。So if I wanted a parabola。

 I would have y equals a X squared。Plus Vx plus C。😡，We think of the variables。

 the independent variables as x squared and x。And then y is indeed， a linear function of those。

Variables。Because we're adding terms。Not important that you understand the details。

 It is important that， you know that linear regression can be used to find polynomials other than lines。

All right。So， we've got this done。Should we be happy？We can look at this。

 We fit the best line to this data point。 We computed K。Are we done？Well。

 I'm kind of concerned because when I look at my picture。It is the best line I can fit to this。But。

 wow。It's not a very good fit， in some sense， right， If I look at that line。

The points are pretty far away from it。And if it's not a good fit。

 then I have to be suspicious about my value of K。Which is derived from having the model I get by doing this fit。

Well， all right， let's try something else。Let's look at fit data 1。Which。

 in addition to doing a linear fit。I'm going fit a cubic。Partly to show you how to do it here。

 I'm gonna say ABCD equals pla polyfi of X vows， Y vows and three instead of one。

So it's a more complex function。Let's see what that gives us。First， let me comment that out。

So we're going to now compare visually。What we get when we get a line fit versus we get a cubic fit to the same data。

Well。Looks to me， like a cubic。Is a much better description of the data。

 a much better model of the data than a line。嗯。Pretty good。Well， should I be happy with this？Well。

 let's ask ourselves in one question， why are we building the model。

We're building the model so that we can better understand the spring。

One of the things we often do with models is use them to predict values that we have not been able to run in our experiments。

So for example， if you're building a model of a nuclear reactor。

You might want to know what happens when the power is turned off for some period of time。In fact。

 if you read today's paper， you notice they've just done a simulation model of a nuclear reactor in I think Tennessee。

And discovered that if it lost power for more than two days。

 it would start to look like the nuclear reactors in Japan。Not a very good thing。But， of course。

 that's not an experiment anyone wants to run。No one wants to blow up this nuclear reactor just to see what happens。

So they do use a model， a simulation model to predict what would happen in an experiment you can't run。

So let's use their model here。To do some predictions。So here， I've taken the same program。

 I've called it fit data 2。But what I've done is I've added a point。So， I。

Instead of just looking at the X vows， I'm looking at something I'm calling extended X。

Where I've added。A weight of one and a half kilos。To the spring， just to see what would happen。

What the model would predict。And other than that， everything is the same。Ops。What's happened here。

Probably shouldn't be computing K here with a nonlinear model。Oh， alright。 Why is it not。Come on。

 There it is。Now， we have to uncomment this out。Or comment this。Well。

It fit the existing data pretty darn well， but it has a very strange prediction here。

If you think about our experiment， it's predicting not only that the spring。Stop stretching。

 but that it goes to above where it started。Highly unlikely in a physical world。

So what we see here is that， while I can easily。Fit a curve。To the data。It fits it beautifully。

 It turns out to have very bad， predictive value。What's going on here？Well。

 I started this whole endeavor。😡，Under an assumption that there was some theory about Springs。

 Hook's Law and that it should be a linear model。Just because my data maybe didn't fit that theory。

Doesn't mean I should just fit an arbitrary curve and see what happens。

It is the case that if you're willing to get a high enough degree polynomial。

 you can get a pretty good fit to almost any data。But that doesn't prove anything。 It'。

 it's not useful。It's one of the reasons why when I read papers， I always like to see the raw data。

I hate it when I read a technical paper， and it just shows me the curve that they fit to the data rather than the data。

Because there's often it's easy to do get to the wrong place here。So let's for the moment。

Ignore the curves and look at the raw data。What do we see here about the raw data。Well。

It looks like at the end。It's flattening out。Well， that violates H's law。

Which says I should have a linear relationship。Suddenly， it stopped being linear。

Have we violated Hook's law？Have I done something so strange that maybe I should just give up on this experiment。

What's the deal here， so。Does this data contradict Ts law， Let me ask that question。Yes or no。

Who says no？ Why no。Hokelo applies only for small displacement。Well， not necessarily small。

 but only up to an elastic limit， which is。Sme of infinity， it's small。Compared to infinity，s， sorry。

 up to the limit where the linearity bringss Exact right。I overthre my man here。这くら怎こ啊。啊。Exactly。

 it doesn't。 It just says probably I exceeded the elastic limit of my spring in this experiment。Well。

 now。Let's go back。And let's go back to our original code。And see what happens。If。I discard。

The last six points。Where it's flattened out， the points that seem to be where I've exceeded the limit。

So I can easily do that。To this little coding hack。

It's so much easier to do experiments with code than with physical objects。Now。

 let's see what we get。Well， we get something that's visually a much better fit。

And we get a very different value of k。So we're a lot happier here。And if I fit a cubic to this。

 you would find that the cubic in the line actually look a lot alike。So。This is a good thing。

 I guess。On the other hand。How do we know which line is a better representation。Of physical reality。

 a better model。After all， I could delete all the points except any two。

And then I would get a line that was a perfect fit。 R squared， know。

 the mean squared error would be 0。Right， because you can fit a line to any two points。Um。

So what again， we're seeing that we have a question here that can't be answered by statistics。

It's not just a question of how good my fit is。I have to go back to the theory。

And what my theory tells me。😡，Is that it should be linear。

 And I have a theoretical justification of discarding those last six points。

It's plausible that I exceeded the limit。I don't have a theoretical justification of deleting six arbitrary points somewhere in the middle that I didn't happen to like because they didn't fit the data。

So， again， the theme that I'm getting to is this interplay between physical reality。In this case。

 the experiment， that theoretical model。 in this case， hook flaw and my computational model。

 the line I fit to the experimental data。Okay， let's continue down this path。

And I want to look at another experiment， also。With the spring， with this is a different spring。

Maybe I'll bring in that spring in the next lecture and show it to you。

 This spring is a bow and arrow。 Actually， the bow is the spring。

Anyone here ever shot a bow and arrow？Well， what you know is the bow has the limbs in it。

And when you pull back the string。You are putting force in the limbs， which are essentially a spring。

And when you release this。The spring goes back to the place it wants to be， and fires the projectile。

On some trajectory。嗯。And now， I'm interested。In looking at the trajectory。

 followed by such a projectile。This， by the way， is where a lot of this math came from。

 People were looking at projectial tiles， not typically of bows， but of artillery shelvess。

Where the force there was the force of some chemical reaction。Okay， so once again。

 I've got some data。嗯。In a file， similar kind of format。And I'm going to read that data in。

 in plot it。So， let's do that。So I'm going to get my trajectory data。The way I did this， by the way。

 is I， I actually did this experiment。 I followed， fired four arrows。

From different distances and measured the， the mean height。Of， of the four。

 So I'm getting it heights 1，2，3， and 4。Again， don't worry about this。

 And then I'm going to try some fixs。AndLet's see what we get here。So， I got my。

Data inches from launch point。And inches above launch point。And then I fit a line to it。

And you can see there's a little point way down here in the corner。The。

 the launch point in the target were at actually the same height。For this experiment。

 and not surprisingly， the bow was angled up， I guess and。The arrow went up。

 and then it came down and ended up in the target。I fit a line to it。

 That's the best line I can fit to these points。Well。It's not real good。

So let's pretend I didn't know anything about projectiles。

I can now use computation to try and understand the theory。

ItSm I didn't know the theory and what the theory tells me here or what this computation tells me。

 the theory that the arrow travels in a straight line is not a very good one。Right， it says。

 all right， this does not actually。Conform at all to the data。

 I probably should reject this theory that says the arrow goes straight。If you looked at the arrows。

 by the way， in a short distance， it would kind of look to your eyes like it was actually going straight。

But， in fact， physics tells us it can't。 And the model tells us it didn't。Alright。

 let's try a different one。But 6。Let's compare the linear fit to a quadratic fit。

So now I'm using polyfit with a degree of 2。See what we get here。Well， our eyes tell us。

 it's not a perfect fit。But it's a lot better fit。Right。So this is suggesting。

That maybe the arrow is traveling in a parabola rather than a straight line。The next question is。

 our eyes tell us it's better。How much better。How do we go about measuring？Which fit is better。

Recall that we started by saying what Polyfit is doing is minimizing the mean square error。

So one way to compare two fits would be to say， what's the mean square error of the line。

What's the mean square error of the parabola？Well， pretty clear it's going to be smaller for the parabola。

So that would tell us， okay， it is a better fit。 and in fact。

Computing the mean square error is a good way。To compare the fit of two different curves。

On the other hand。It's not particularly useful。For telling us the goodness of the fit。

 in an absolute terms。So I can tell you that the parabola is better than the line。But in some sense。

 mean square error can't be used to tell me how good it is in an absolute sense。Why is that so？

It's because。Mean square error。 There's a lower bound，0， but there's no upper bound。

It can go arbitrarily high。And that is not so good for something where we're trying to。

Measure things。So instead， what we typically use is something called the coefficient of determination。

Usually written for reasons you'll see shortly as R squared。

So the coefficient of determination are squared。Is equal to one。Minus。The estimated error。😡，一一。Over。

MV。Which is the variance in the measured data。So we're comparing the ratio of the estimated error。

 Our best estimate of the error。And a measurement of how variable the data is to start with。

As we'll see， this value is always less than one， less than or equal to1。 And therefore。

 R squared is always going to be between 0 and 1。Which gives us a nice way of thinking about it in。

 in an absolute sense。Allright， so what are these values。How do we compute them。Well。

I'm going explain it the easiest way I know， which is by showing you the code。

So I have the measured values in the estimated values。The estimated error。😡，Is going to be。

 I take the estimated value。The value given me by the model。Sotract the measured value and square it。

 And then I just thumb them。Alright， this is like what we looked at for the mean square error。

 but I'm not computing the mean， right。I'm getting the total of the estimated errors。I can then get。

The measured mean， which is the measured sum divided by the length of the measurement。

That gives me the mean of the measured data。And then my measured variance is going to be the mean of the measured data。

😡，Minus。Each point of the measure data squared， and then summing that。So just as we looked at before。

 when we looked at the coefficient of variation and standard deviation by comparing how far things stray from the mean。

 that tells us how much variance there is in the data。And then I'll return one minus that。Okay。

 Tuesday， we'll go look at this in more detail。Thank you。

