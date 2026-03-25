# 【麻省理工】计算机科学与编程导论 ｜ MIT 6.00SC Introduction to Computer Science and Programming p25 25 -BV1a5BZBkEP6_p25-

The following content is provided under a creative Commons license。

 Your support will help M I T Open Coseware continue to offer high quality educational resources for free。

To make a donation or view additional materials from hundreds of MI T courses。

 visit M T OpenCourseware at Ocw。 MT Eduu。

![](img/2d6bf2bd4bf148c20433007b9471786f_1.png)

All right。So we've got three main topics to talk about， one is distributions。

 the other is Monte Carlo methods， and one is on regression。For distributions。

Which distributions have we learned about in class？嗯。有。Okay， so we have normal。What's another one？

Okay。And there's one more that he's kind of mentioned， I think， in passing。Yes， so exponential。

So for uniform， what would this look like if I were to plot this as a histogram？And I have。

Endpoints A and B。咁们。Quormium。So it's going to be a horizontal line， right？

And if we were to look at the function for this， it would be。Kown。没说。

The probability would be1 over B minus a。4。All points between A and B。

So let's look at this graphically。So this chunk of code should not be too difficult to understand at this point。

 right？All we're doing is we're using the random number generator Rant。

 it's going to return us an integer。Random minister from a uniform distribution between A and B。

S anyone that's puzzled by that？是。Alright。We're going to do that for numb points。

 and then we're going to plot a histogram。 The only parameter I don't think you've seen here is this normed equal true。

嗯。What this does is。Normally， when you use the hist command in Python。

 it's going to give you raw frequency counts on the Y axis。

 what norm equal true does is it gives you the proportion of the points that wound up in a particular bin。

So。I can。Actually， show you both ways。So。Does that look about right for 100 bins？What 100，000 points？

Each one has about 0。01， so that looks right。1% in each bin。So that was normed if we do it unored。

See how the Y axis here has changed before it was from like 0 to 0。

12 or 01 now it's from0 to like 1000。That's all that norms parameter does。

 but this is what we would expect。 and this is for integers and then。Of course， Python also has。

A way of doing it for floating point。 So here we are going to use the uniform command。

And then when I say show continuous uniform， I'm going to give it the A and B0 and 1。0。

And it's really not going to look all that much different。

It's just that the y axis here is from zero to or the x axis is from zero to1。Okay， so。

Uniform is easy。What does a Gaussian look like or a normal？上。Like if I were to plot it。

 what should this look like？Okay， it'll be a bell curve。Where's its peak going to be？就系佢。That me。

 Thank you。So the peak is going to be at the mean。We usually denote it with mu。

And then it's going to fall off。Asymmetrically or symmetrically off on either side。Symsymmetrically。

 all right？Now， the Gaussian can be specified fully using two parameters， what are they？

You have one here， and then you have standard deviation。Ming。And sigma。

Now the function for this is not something you're going to have to know。

 but I wanted to show it to you。And the stats major can correct me if I'm wrong。Yes。So。

ItMight be a little scary， I don't know， it intimidated me the first time I saw it。

 does I look about right to you， all right？So the reason why I threw that up there is because what I want to do is show you。

What happened or the ideal form？When we plot out。This function versus a bunch of random samples we've drawn from a distribution that is Gaussian。

So。I have a function make Gaussian plot。All it takes is the mean standard deviation。

 how many points we want to draw from the distribution。And then I have a parameter here show ideal。

 and we'll get to that in a second。Their function that we use is called dot Gauss。

And it just takes a mean and the standard deviation。We're also going to compute。The ideal points。

 so if I。Take the mean and I go a couple standard deviations in either direction on the x axis。

 and I can plot out what the y should be according to this function here。So。

And then just do a histogram。If I want to show the idea， if I want to show this plot。

 that's what that parameter controls。It'll plot out the function， and if not。

 then it'll just plot the histogram。So let's see what this looks like with just the histogram。

All right， so。It looks like what we would expect， we have the nice bell shape， it's centered at zero。

 and it's got a standard deviation of one。And these are just this is just。

 these are the relative frequencies of a random sampling of points。For a Gaussian distribution。

And we can see that。If we look at the ideal version or the actual function。It matches very closely。

All right， and then for various shapes。Standard deviation of  two。Different mean。

 different standard deviation。It's pretty easy， right？

Are there any questions on Gaussian distributions or normal distributions？ok。So。The last one we have。

哋双少嘢。Oh， F range is a custom function， so we actually define it up here。

Just was kind of hoping I could slip that pasture。嗯。It's just like range except instead of integers。

 it returns a list of floating point numbers separated by a step argument。

It starts at a lower end range start。Stops at the stop and then increments by step。Until it cell。

 it returns a bunch of floating point numbers。The last one is the exponential distribution。

 and I don't know， did he really explain what the shape looked like for this？大ello。Okay。

 so we can go really quickly through it because you know。

 it doesn't sound like he actually expects you to know it too deeply。Basically， it'll look like that。

Alright。And the function。Is。You don't need to know it， it's just there for your edification。

Lambda is greater than zero。So。I'm just going to show you what it looks like and then we'll move on。

So here we the blue is the sample points。And the red is the ideal curve。

Just different values of lambda。Does it always have downward look like that for it to be exponential？

Yeah， in this case。There's another family of distributions that we're not going to touch on。

But that is that for distributions for today。Unless anyone has any questions， I'm going to move on。O。

So the next big topic。They are。is Monte Carlo methods。So can someone give me an informal？

Definition of what a Monte Carlo method is。Really gr is it basically using。Using your random。

To try to approximate something that's not random by doing it。Yeah， more or less。

 it's trying to arrive at a solution by repeated sampling or random sampling。So。

 and we've we've seen many different applications of this。

 but we're going to review them and kind of。You know， try and get a better understanding。

 so the Monty Hall problem。This is a Monte Carlo simulation。So one。

 what's the action that a person should take？All right。

 and does anyone remember what proportion of the time if they switch they won？Two thirds， okay。

I happen to know this works。Maybe。I think my program died。Okay， so。It works。Is this code？You know。

 confusing to anyone or cryptic。I tried to make it a little bit simpler than the code that was in the handout for glass。

嗯。We have a number of trials， we're going to pick a door for the price。

 the player is going to choose a door。嗯。If they choose to stay and the prize is in the door that they chose。

 then stay wins。They choose to switch and。The prize door is not the door that they originally chose。

 then switch wins。谢谢。What I wanted to try and do is look at kind of an intuitive explanation for this。

We were at office hours， we were kind of kicking around different ways of explaining this。

We went to Wikipedia and we found this explanation。

The idea is that let's say that the contestant chooses door one。

 so there's a one third probability that they've chosen the door that has the prize behind it right and then。

There's a one third probability that it's behind door number two。

 one third probability is behind door number three。

The key to this kind of explanation is that if you consider both two and three together。

 then there's a two third probability that the prize is behind one of those two doors。So。

Monty so the player chooses， and then Monty opens a door， there's a goat behind door number three。

This new knowledge actually doesn't change， though， the probability that you chose the correct door。

So you still have one third chance that one was the correct door。

And there's still two thirds chance on this side。But you know。

 this one is zero because you see the goat， so this door has to have a two third chance。

Of having the prize。Does that agree with you？All right。So。It's one way of explaining it。

 I don't know， I had problems kind of getting this into my head。Does anyone want me to try again？通り？

Here go， there's going be。对对自己。sameme idea， but kind of negating it and thinking from the negative direction。

Okay。Another explanation that was good was if you had a million doors and you had 999，999 goats。

And you had one prize， you have a one in a million chance of choosing the right door。

 So now imagine Monty walking down and opening up 999998 doors， each with a goat behind it。

 Well now you have your door that's still closed and the door that's mystery。Also closed， right？

The probability that you chose the correct door is still one in a million。So if you see 999。

998 goats。And one closed door， and you know that your door only has a1 in million chance。

 probably want to switch to the other door because that probably has a price。

So different ways of thinking about it， the probability problems and statistics problems。

 it always helps to or at least I think it does to have an intuitive idea of what's going on。

So with that said， let's talk about pi。Because this is one of my。Favorite Monte Carlo methods。

Because it's got a nice explanation。Does anyone？Need me to talk about the idea behind this。

You know how this method works or to go through it， its like with all right。Someone's nodding。So。

The idea is。We have a square。And each side or its side is two are。Units long。

So what's the area of the square？So， ASQ。Square， right？

Now we have a circle that's inscribed in the square。And it's got a radius of R。So area of circle。

If we take the ratio of the circle。To the area of the square。And we find we have pi over four。Now。

 let's assume。That I throw darts at this。Wakes people up。And there's a uniform probability。

That the point will land somewhere in the square here。If I throw n of these。Then I can expect。

Pigh over four of them。Times N to wind up in the circle。

And since I can find this number and this number， and I want to find pi， I can just rearrange this。

That's how we get pi。Alright。So let's go to the code。We just have some easy code。

 gets a random point within a square that's from minus r to r， so two are units long。

I have a function that makes a whole bunch of points。

And then I have a function that checks if a point is within a circle of radiusR。

And another function that looks at a bunch of points and counts how many are within the circle。

And then I have my compute pi function here。And all it does is you can either pass it some points that already made or just。

Say I want to have 100，000 darts thrown at this square。

And it'll make a whole bunch of those random points， figure out how many are in the circle。

And then we have。This would be。M。And none points n。And we multiply it by four that gives us pi。

More or less。So。Let's look at a couple plots。I have a function here run trials and what it's going to do is it's going to run a number of trials。

For a given number of points。So。What I want to do。Is I'm going to run 50 trials for each number of points。

And I'm going to have a points list that goes from 10 to 10，000 in000 point increments。

I'm going to run the trials and get the results， and then I'm going to plot my results。

And why don't we just throw that up there？Okay。So on the plot， the blue line， blue horizontal line。

 that's the actual value of pi。As near as a computer can approximate it。On the X axis。

 we have the number of darts that we threw at the square。

And each red dot represents the result of one trial of throwing。

You know however many darts at a board。So。When you're down here and you're only throwing 10 darts。

Tend to have a very wide spread for the estimated value of pi。As you increase。The number of darts。

Yet much closer， I would say shot group， but grouping is probably more appropriate。嗯。

And that's much closer to the actual value of pi。There's nothing really unusual about this， right？

Nothing confusing。So。Another way of visualizing this。Is to actually， well， look at。

The darts that are thrown。So。I have a function here， plot pi scatter。

 and this is actually just going to。Pt。This。And it's going to do it for 10 points， 100 points。

1000 points and 10，000 points。And we'll see why we can start converging。Onpai。

So this is with only 10 darts thrown at this square。The value for pie is really。

Pretty off and it doesn't really look very compelling。So。In fact， only one。In fact， one of the darts。

Actually。Fell outside the circle， nine of the darts fell inside the circles。

 you're not going to get a real good estimate there。

The blue dots there represent being in the circle， red is outside。So if we do it with 100 points。

 it starts getting a little better。If we do it with  a thousand0 points。starts getting better。

IfWe do it with 10，000 points。So。Anyone confused？So I'm going to move on。

And show you how we can use the same method。To do numeric integration。Here we go。So。

Here's that F range function again。So it's not confusing anyone。What we're going to do。

Is we're going to。Use a Monte Carla method。To integrate。A polynomial。So let's say that I have。

What I want to find。I'm not going to do it for something because this is a numeric method。

Let's say I do it from negative five to five， so I want to do this。Yes。

If you haven't had calculus or anything like that， don't worry about this。

 but I think a lot of people have so。With a couple of exceptions。So。

This is an easy function to integrate， right， but there are also some functions that are really hard or impossible to。

That's where。A lot of software packages actually use Monte Carlo methods to do numeric integration for you。

But。The idea is the same。I'm going to take a function， and this is going to be x squared。

And then I'm going to take an x min and an X max。Right。These become my left and right boundaries。

 and then I'm going to find the minimum of the function between these limits。

And the maximum of the function。So you see what I'm doing， I'm defining。A rectangle。Right。So again。

 same thing。Or same principle， I of the area of the rectangle。And then。I cant don't have the area。

Of this guy， that's what I'm trying to find。But I know that if I find。The ratio。

 the number of points that land。In this square or the ratio of that land in this curve。

Versus the total in the square。Then I can find this area pretty easily。So。This function。

 fine function， Y Min， Y max， does exactly what it says。Allright。

Just goes between X min and X max and then finds where the function is a minimum。

And where it's a maximum， So the function I'm calling F。

It's one of the few single letter variable names that I'll use that isn't an。Isn't an index counter。

Rightright。My random point generator is going to take the bounds X min， X max， y min， Y max。

 So it's going to uniformly produce a point that falls within this rectangle。My make points。

 it just makes a whole bunch of these。Then I have this function between curve。

What this tells me is if I have a point here。It'll return true。Because it's between the curve。

And the X axis。If it's up here， it's false， right？Doess anyone not understand how that works？

You're all smart。So。Here is our estimate of our main function， estimate area。

You giveive it a function， X min， x max， I'm going to tell how many points to toss。And optionally。

 we can tell it that we already have points that have been tossed。

And we find first thing we do is find the Yman and the Y max。And then if we don't have points。

 we make them。And then point counter counts how many times。A point wound up。

Between the curve and the X axis。And we just iterate to the points。If it's between the curve。

That means it's here。Then if it's above the x axis， we're going to increment the point counter。

 and then if it's below the or the X axis， we're going to decrement the point counter。

 So we're accounting for signs here。 So if we had a function。That did this。

We'd be able to properly handle it。Then we get the rectangular area。

And then all we do is we multiply。The recectangular area by the ratio of the number of points between the curve and the X axis and the number of total number of points thrown。

And that gives us the function area。So。Here's my function， x squared。

And this is just plot function scatter， all this is going to do is just do the same thing I did with the circle。

And。I am going to do this for a number like if I toss 10 points， 100 points，000， 10，000 or 100，000。

 so let's see what this looks like。Assuming that Python doesn't crash。So。Not too nice。Hund0 points。

Asm points。10000 points。Then a whole mess of points。So。Oho， I crashed him。いいですね。I'm sorry， Sby。

T the why。这个啲一啲。我快到睇解当算。You're talking about doing a reman approximation。Or even some so。

So his question is。Why don't you do something like this。Divide up the X axis。Into very small。

Portions。Like that。And then sum up the areas of these rectangles， right？嗯。Yeah， you can do that。嗯。

You know， I don't have an answer for that， I can't say which one would work better。嗯。

Do you know Serena？Yeah。I would say that。Right now。Whichever one you prefer。嗯。

But I'll see if there's any actual research on whether or not one is better than the other。

It might turn out that there are certain instances where doing this sort of approximation is better than doing the approximation I'm talking about。

So。But I， I don't know。不样。Yeah， for this problem， you could definitely。Use that。So。

Is everyone good with us？Anyone confused， any questions？Yeah系 think系。Im concerned that you need a。

Fantastically large number of darts。系你す会。Yeah， I mean。

 that is one issue with Monte Carlo methods is that you know they do rely on large numbers。So。嗯。Yeah。

 sometimes it can take a while。O。Just for at least for the purpose。This class。

 we don't need to be able to。It sort of quantified the error。😔，No。Yeah， you didnt。

You do need to understand that there can be error。And that you should also understand stuff like confidence intervals and confidence levels。

嗯。Are you okay with that？But in order to get a confidence。Interval， you'd have to。

Few several trials at。あだ。Right， exactly。Yeah。You。You could estimate。Error。Like you could estimate it。

But in order to like really get a good sense for how much variance there is。

 you'd have to do repeated trials。So。mean what I guess was getting was in order to get a sense of how big the error is relative to the number of trials。

是两问题。Yes that' that's probably know。I'm sorry that's not something that we're going to be asked。Yeah。

 no， we just， we want you to， you know， the purpose is we want you to understand that when you do stuff。

 do things like this that you know， there there is some。A thought that has to go into well。

 how many trials do I need to do， how many points do I need to throw？And you have to ask yourself。

 how much air am I willing to tolerate？You know， there's。

The joke that mathematicians call pie pie and then。Engineers call it 3。14， right？So。Okay。

 so if everyone's done with integration。I'm going to move on to regression。15。

You got plenty of time oh wait now there's one thing I wanted to。Touch on。So。It kind of looked at。呃。

Some toy problems with Monte Carlo。 And this is， I guess， a toy problem， too。

 because it has to do with a toy。 It's everyone familiar with the game of Monoppoly。All right。

 so I don't have to explain the rules too much in depth。Okay， so。Let's assume that there are no。

Factors that modify this distribution。If I roll the dye twice。

Then each one of these spaces has an equal probability of being landed on， right， it's about2。

 a half percent。But。There are certain rules that distort this distribution so like you can land on go to jail。

You can roll three doubles and get sent to jail， you can draw a chance card and get sent to jail sent to go or sent anywhere on the board with a and there are 10 out of 16 chance cards that modify this distribution。

And for community chs， same thing， there's two out of the 16 cards that distort the distribution。

 So the question is。How do you do this analytically？And I've tried， it's hard。

And I'm actually not sure if it's possible。Well， this is a perfect example of where you would use a Monte Carlo simulation in order to arrive at the answer。

So if you actually want to take a whack at this problem， you can go to this site called Projectouler。

net。They have a whole bunch of Matthewy questions on there that are meant to kind of get people to think about math and computer programming。

And you get like little rankings， the more questions you answer correctly and stuff like that。

 So there's a little competition but。The question in this particular case was。

 what are the top three？Places you land on with all these factors。

And if you represent them as a number that is concateed one after the other， what is the number。

 what is a six digit number？So。But that's a fun problem。So。Going on something that's less fun。

 regression。So。Can someone tell me what purposes we would use regression for？Take step。

I an experiment with data。She believed to fit some type of theoretical model。

But experiments being experiments， they're not。Right， you can't。系。

So the data points exactly fault the model， is you have to find which parameterss in the model to pick so that you'。

You're experimentally a best fit。嗯m哼。So。I mean， the idea is that you have a bunch of experimental data that has error。

And you want to be able to。Maybe find the underlying function。OfOf those observations。

And you would do that using regression。We have a couple of nice tools in Python for doing that。

And another reason， actually， before I move on， another reason is you can find the function。

 but you can also then once you find that function， you can use it to predict additional values。

 so say you have a gap in your data。Or you want to predict values beyond the range that you collected observations for if you do a regression。

 you find the function， find the parameters for the function。

 then you can use it to predict those values。Right。And。

What we mainly want you to understand here are the functions that you would use to do it and how you would tell if you have a good fit or not a good fit or and the idea of overfitting。

So。We have a little bit of code that represents or that kind of demonstrates this。

So a couple of helper functions that compute。Various。Values that you've seen before。

So MSE is the sum of the residual squares and then you have the total sum of squares。

These will help you compute the coefficient of determination。And。What I'm going to show is。

Let's say I define a function here。In this case， I have it defined as x cubed plus 5 x plus 3。

I am going to。For a certain number of x values。Apply the function and get the y value。

And then to simulate observational data。I'm going to perturb it。Using a Gaussian distribution。

So it's going to jitter the points。And that's what the make observations function does。

 is it just adds noise to the y values。And then I'm going to this function here。Plots out。

The measured are observed values。That simulated。It computes a fit。For。One degree。

 so in this case I have two parameters，5 degree one and fifth degree two because I want to do comparisons。

So it'll compute a fit using the first degree。And predict some values for the curve。

And then it'll compute the residual error and the coefficient of determination。And plot it out。

And then it'll do the same thing for。The second degree。So。Let's see what this looks like。

Let's see Python that。Behave。Bad way。So。The function that we plotted was what x。

Squared something 5 x squared。我也谁。X Q plus 5 x plus3。So。And we're plotting it from negative two to2。

 So this is what I'm talking about with the noise， right。

 So each of these red dos represents some observation that's been disturbed a little bit。

And then I I try to fit this with a first degree polynomial and then a second degree。I see。Well。

 actually my residual error is lower from my one first degree fit。That's interesting。嗯。So。

I don't know， at this point I'd say just stop and don't proceed further。

 but we know that that's not the right function。So。

Let's look at what we have for a third degree fent。It's actually worse。H。

This is problem with random programs is that sometimes they fail you。So。Anyway。

I would say that these are nice， pretty plots， but they're not really telling me much。

Other than I can fit some lines to some points。我吃的不可以我。It's not there。Well。

So we know that the function that we made the observations on is a third degree polynomial， right？So。

It's a little puzzling。Why。This。First degree fit。Is better。Then。Our third degree fan。That's。

 that's kind of the the。The conundrum。So maybe Im wonder what would happen if I expanded the X range。

 So let's say。I go from negative five to five。And maybe it's。Just too little data。

That's looking a little better。So。Now I feel better。

So the issue was that we just were going from negative two to two。Basically， they look linear there。

The first degree polynomial is doing fine， but as soon as we go out get a little curvy in there。

We see that both the first and the second degree fits， they have pretty high air。

There are pretty gun。But when you compare them with a third degree fit。

 you see that the error drops down dramatically。And it's got a higher coefficient of determination。

 So what we would say in this case is that the third degree fit here。

Is a lot better than the first or second degree fit。And then we can also look at， say。

 a fourth degree fit， which in this case happens to have a higher error。So。That's a good thing。

 And then if we look at a fifth degree fit。It also has a higher error。 So we'd say in this case that。

The third degree fit is probably our best bet， and we probably have a pretty good idea of what the function is for the underlying model。

嗯。Which part of this is？Well， the part of this is regression is。

The part that actually does the regression is this polyfit method here。

And what you do is you pass it in， the x values， the y values。

 and the degree of the polynomial that you want to fit to it。So。

I've kind of hit the end of my material unless someone has questions。Comments， fears， jopditions。反い。

I thinkve done some stuff。Exelling thick firmbs with the R squares， the R square values are really。

 really high。Like really， really just one in these fits， you know the fits are pretty terrible。Yeah。

That is puzzling。And you know it's quite possible that I have a bug。

The different definitions are where that are maybe fully around。

Now I made a correction to this earlier and maybe like I said， maybe I introduced a bug。

 so I'm going to have to double check my math。Unfortunately， I'm not perfect。



![](img/2d6bf2bd4bf148c20433007b9471786f_3.png)

W I was。

![](img/2d6bf2bd4bf148c20433007b9471786f_5.png)