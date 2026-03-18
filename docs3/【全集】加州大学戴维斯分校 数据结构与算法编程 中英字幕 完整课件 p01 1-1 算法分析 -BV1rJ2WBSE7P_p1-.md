# 【全集】加州大学戴维斯分校 数据结构与算法编程 中英字幕 完整课件 p01 1-1 算法分析 -BV1rJ2WBSE7P_p1-

Hi everybody， happy April Fos Day and welcome to this second lecture。



![](img/95e7598ca030ac47002e841e014007ef_1.png)

So today we're going to stop talking about the new topic， algorithm analysis。

 which is really the topic about big O， you know， this mathematical notation you might have heard of before。



![](img/95e7598ca030ac47002e841e014007ef_3.png)

![](img/95e7598ca030ac47002e841e014007ef_4.png)

hi essentially helps characterizing the behavior of a function according to its argument。

 which is very useful when the argument tends towards infinity。



![](img/95e7598ca030ac47002e841e014007ef_6.png)

And so we use this notation in computer sense a lot to classify different algorithms in terms of running time and memory complexity。

 and according to the size of the input data。

![](img/95e7598ca030ac47002e841e014007ef_8.png)

But no worries， we're going to take our time to get there。

So first we're going to look at the issue of algorithm analysis from different angles and for that we're going to follow three steps。

Step one， we're going to try to see why do we need algorithm analysis in the first place and we're going to look at two examples。



![](img/95e7598ca030ac47002e841e014007ef_10.png)

Then we're going to discuss two different approaches to kind of understand what is algorithm analysis and how do we get it。

 we're going to talk about an experimental approach that's going to be today and then a mathematical approach that's going to be for Friday。



![](img/95e7598ca030ac47002e841e014007ef_12.png)

And finally， early next week， we'll get to this famous big oh， what it is。

 how does it work and everything？So let's start with the examples。

 let's start with the first example。

![](img/95e7598ca030ac47002e841e014007ef_14.png)

Imagine。We're at UC Davisvie and the registrar， you know。

 like there this department at UCDvie or this service who is in charge of scheduling all of the different classrooms for the different classes that we have at UC Davisvie。

 which is a massive struggle every single quarter。

![](img/95e7598ca030ac47002e841e014007ef_16.png)

And so imagine that the registrar is considering to buy a program that would do it automatically right because like there are so many courses and so many classrooms that it cannot be done manually to take weeks。

 so they're trying to invest into a program that would do that automatically。



![](img/95e7598ca030ac47002e841e014007ef_18.png)

![](img/95e7598ca030ac47002e841e014007ef_19.png)

And they're talking to this vendor and the vendor says like， oh。

 our program can schedule 10 classrooms in 1。42 seconds。And so the question is。At the registrar。

 they're like， well， should we buy this program， like， is it good， is it bad？

It's kind of tough to know， right？Actually， the first thing that you can kind of if it were to happen to you that like you would be in a job interview and you were like asked some sort of problem like that。

 the first reflex that you want to have is ask for more questions here clearly like should UCDVs by this program or not we don't have enough information so we want to know more details for example here we know that the program takes about like one second to schedule 10 classrooms。



![](img/95e7598ca030ac47002e841e014007ef_21.png)

![](img/95e7598ca030ac47002e841e014007ef_22.png)

![](img/95e7598ca030ac47002e841e014007ef_23.png)

If we're UC Davis who are like， we don't have 10 classrooms， we have way more than that。



![](img/95e7598ca030ac47002e841e014007ef_25.png)

So that would be a question to be asked， right？So going back to the UC Davis problem。

 let's see at UC Davis， we have 130 classrooms。

![](img/95e7598ca030ac47002e841e014007ef_27.png)

And we also have like thousands of courses every quarter to schedule。

Inside of those physical classrooms。So。Here we know a little bit more。

 but it still doesn't really tell us like how this program that we might buy or not will perform on 130 classrooms。



![](img/95e7598ca030ac47002e841e014007ef_29.png)

And it pretty much depends on what kind of algorithm this program is using inside to do the scheduling right。

 so let me show you a few examples here。

![](img/95e7598ca030ac47002e841e014007ef_31.png)

In the best case scenario， so let me。In thesque so the only data point that we hear that is provided by the vendor is the fact that if we have 10 classrooms。

 then the vendor tells us， oh， it takes 1。42 seconds to schedule。



![](img/95e7598ca030ac47002e841e014007ef_33.png)

And but now we're UC Davis and we have 130 classrooms。

And we would want to know we would want to like have an idea of how much it is going to take for that many crossros。

And it entirely depends on the algorithm that's inside of the program right。

 if we are lucky and the vendor is like pretty good。

 maybe the engineers will have devised an algorithm that is called logariththmic and that would take only three seconds to schedule all 130 classrooms。

嗯。If the engineers are maybe like a little bit less good。

 they would have come up with an algorithm that is called linear and it would take about 18 seconds and if the engineers are not that great。

 they would have encode or programmed in algorithm that is called exponential and here it's like 240 seconds。

 which is about four minutes。

![](img/95e7598ca030ac47002e841e014007ef_35.png)

![](img/95e7598ca030ac47002e841e014007ef_36.png)

So。That's one reason we would want to have algorithm analysis is to be able to given a certain algorithm。

 predict how much time it's going to take when we increase or when we change the size of the input。



![](img/95e7598ca030ac47002e841e014007ef_38.png)

So here we're talking about prediction of a program or an analysis what about now comparing two different algorithms to one another so again let's take an example。



![](img/95e7598ca030ac47002e841e014007ef_40.png)

。Imagine I have a list of numbers。And this list of numbers is already sorted right here， like 6， 12。

 46， and so on。And now we want to come up with an algorithm that searches for a specific number inside of that list。

 right？

![](img/95e7598ca030ac47002e841e014007ef_42.png)

So here imagine like I want to find number 52。In a linear search。

I would start from the very first item 6 and then 12 and then 46， 47 and 52 bingo。

 I found the number that I was looking for， right？So。嗯。That would take one， two， three， four。

 five steps。T路。Another question is like。Could we find a better algorithm that would take advantage of the nature of the list？

That is the fact that the list is indeed solid already。

There's another algorithm that's called binary research。This one works in that way。

In binary research， you jam directly to the middle element。

And then you look at this element and either you go right or left。

 depending on the item that you're looking for， is it bigger than this middle element or smaller than this bigger than this element。



![](img/95e7598ca030ac47002e841e014007ef_44.png)

The rationale here is that。When you're looking for 52 and so you go to 47。47 is smaller than 52。

 so you know that because the list is entirely sorted。

 there's really no reason for you to consider any of those numbers。

 you can directly go to the remaining elements。

![](img/95e7598ca030ac47002e841e014007ef_46.png)

![](img/95e7598ca030ac47002e841e014007ef_47.png)

And so here you would go jump。To the next middle element， which is 73。73 is bigger than 52。

 so you know that you can discard the remaining elements。And finally。

 you get to the one that you were looking for。And so here you can compare the two algorithms， right？

We were saying that in that case， we needed one， two， three， four， five steps。

To find the number that we were looking for。And in that case， we need one， two， three steps。

So technically， it is faster， right？Let me move thisto。O。

The thing is like it's not perfect either because what if。I'm looking for number six。Well。

 with the linear search， if I'm looking for item six， then I'm going to find it right there。

 it's the first one of the list， so it's going to take one step。However， with the binary search。

 if I'm looking for item6， then I'd still go to the middle element。

 six is smaller than 47 so I can cross that out。And then I would jump to the middle element here， 12。

6 is smaller than 12， so that would cross all of those out and from 12 I would jump to finally6。

And so here it would take me like three different steps。



![](img/95e7598ca030ac47002e841e014007ef_49.png)

Overall， we see that like in some cases， the binary search it is not always better than the linear search it also depends on the。

On the items that we're looking for。So maybe we need to compare the best case scenarios and the worst case scenarios。

So what are they for those two algorithms？For the linear search。

 the best case scenario is when we're looking for the number that is very first of the list that's located at the very first of the list。

 so here if we're looking for number six is the first one in the list。

 we would be able to find it right away。The worst case scenario in that case is if we're looking for number 91。

91 is at the very back of the list。If we were to try to find it。

 we'd had to go through the entire list one by one。

 and that would take as many steps as we have numbers in the list。



![](img/95e7598ca030ac47002e841e014007ef_51.png)

On the other hand。The binary research， the best case scenario is when we're looking for the number that's in the middle of the list。



![](img/95e7598ca030ac47002e841e014007ef_53.png)

The worst case scenario is when we have to divide the list further for every step up until we've isolated the number that we were looking for。



![](img/95e7598ca030ac47002e841e014007ef_55.png)

And that's actually that's what we call a logarithmic algorithm here because the population that we're considering at each step is divided by two at every single step。

 but no worries we'll get to talk more about that later， okay。And。Okay。So。So， the question is。

Could we find a better way here to？First of all， like compare different algorithms。

 like be able to assert like， oh， one of them is better than the other。

And that means like we need a certain way to characterize algorithms themselves in a way that's like less complicated than here。

 because here we have to take into account the best case scenario and the worst case scenario and so on。



![](img/95e7598ca030ac47002e841e014007ef_57.png)

So overall， that's why we need algorithm analysis。We need it for three purposes。

 we need it because we want to be able to predict how a certain algorithm will perform。

So if I have an algorithm and I want to predict how long it's going to take to process a certain amount of data。

 algorithm analysis would help me do that。

![](img/95e7598ca030ac47002e841e014007ef_59.png)

We need algorithm analysis because we need a proper way to compare algorithms between one another。

 like be able to determine like is one better than the other and we also need to define what do we mean by better。



![](img/95e7598ca030ac47002e841e014007ef_61.png)

And finally， more generally， we need a way to characterize algorithm。

 like how how what is the worst case scenario for this algorithm。

 like is what is the absolute like worst input that we can give that's kind of yield the worst kind of running time or what is the average case。

 like on average， how does it perform？And so on， and so we're going to be talking about that all through this class。

Okay。Now NRS， the level of what we're going to talk about is extremely like informal。

 I am not a mathematication， so Nris were not going to talk about like proofs or anything that's like mathematically complicated it's rather informal。

 if you want more formal discussion around algorithm analysis。

 it's coming but that be upper division classes such as 122A and 122B。Okay。

 so let's stop talking about。Some details here。We're going to talk about how we can analyze algorithms and we're going to do it in two steps first we're going to talk about how do can we do it experimentally。

And then at the next lecture， we're going to talk about how can we do it mathematically？



![](img/95e7598ca030ac47002e841e014007ef_63.png)

So let's start with the first one， how do we do it experimentally？



![](img/95e7598ca030ac47002e841e014007ef_65.png)

And for this one， we're going to use an example， very simple example。

The example that I took here is called the threesome problem。It's a classic problem in。

Computational geometry， so typically let I added an example here in computational geometry。

 you can have a scenario where you have a bunch of lines。In the plane。

And you want to be able to detect if three lines are all intersecting in one specific point。

 that's pretty much what the threesome problem is。So here we're not going to do it like that complex。

 we're going to actually like do a much simpler example。

 we're to just going to assume that we have a collection or a set of n integer， let's say in a file。



![](img/95e7598ca030ac47002e841e014007ef_67.png)

And we want to be able to compute。How many times we have triplets。

 so three distinct values in this set of n integers。So how many triplets？

Add to one another to be zero。So here is an example here， imagine I have a file with eight integers。

 30 minus 40， minus 20， minus 10 and so on， so eight integers。The threesome。

Will determine which triplet So which set of three values sum to be 0。In that case。

 we have four of those triplets， actually put them in that table。and it's， it's。

 I mean we can do the first one here， for example， like here it tells us that like we have one triplet。

 which is triplet 30， minus 40 and 10。So that's a triple plate。 and when you sum those values。

 it gives you。0。Or we also have like 30 minus。20 and minus 10。

 that's another triplet that sums to zero。And so the goal here is to identify which triplets of three values add up to being zero and then we count how many of them do we have so here we have four of them right。

So let me show you the C++ program that we could use that's actually like behind this here。So。

So that's what we have。So let me try to explain the different lines here。As you can notice。

 and that's something you will see a lot in my slides。

 I often put the main function at the very bottom so that I don't have to write a prototype for the functions that I use。

 I can just declare the functions that I use above the main and this way I don't have to write any prototypes。

That's a very common technique that I find extremely convenient this way if I have to change the function signature。

 I only have to do it once and I don't have prototypes to maintain。Anyway。So I have a main function。

I'm not expecting any arguments coming from the command line。And then I have two local variables。

 I have a local variable and that will be the local variable that I use to read the input from the keyboard。

 so the sequence of numbers， the sequence of integers。And then I declare a vector of integer。

 which I call a。And now I have my Y loop， which will read from the keyboard the sequence of n integers that the user is typing。

And so I read each of them in local variable n， and I push n into vector a。So here at that step。

 after running this Y loop， we've read all of the n integers like that the user wanted us to analyze they' are stored into the vector。

And now we can call this count threesome function that is being defined over there。So quickly。

 you see that in this function， we receive the vector a as a reference。This way。

It's the same object as this local variable that we declared in Ma and we don't have to make any copy。

 which would take a lot of time to perform。Here we give a as the local variable。

 and that's the exact same variable that we retrieve as the input to the function。

 which is very fast。Okay， and so then essentially the body of the function is those what five lines？

And in those five lines， what we're going to do is that we're going to examine every single。

Combination of triplets。That we have in our input data set。

And we're going to examine every single combination of triple plates。

And if we see that for a certain combination。The sequence of triplets adds to being zero。

Then we count plus plus， and so we count the number of triplets that send to zero。

And that's the count that we return back to the main function and that gets printed over here。

 so exactly like we saw in the previous slide。So。Now that we have a program that is able to count the number of。

Ts in a in a set of n integers。Let's try it experimentally。



![](img/95e7598ca030ac47002e841e014007ef_69.png)

So I run some。Some test on C S I F。So on CSIF， I imported the program， I compiled it。

 and that gave me an executable， and now what I would like to do is run this executable on different sizes of the input data。

On the collection of N integers。And depending on the size of the input data。

 I want to know how much time does it take because I want to be able to characterize the algorithm。

 right？So for that， I'm going to prefix the comment with this little tool called time。

If I use time and then I run a certain command， then time will tell me when it's over how much time it took for the program to run and so we're going to do that for different sizes of input data and we're going to be able to extract the running time overall of all of those different like simulations。

Um so yeah， u and one last thing because I'm not going to write。

 I'm not going to want to like use this program manually by typing the numbers myself。

I prepared text files here。That would already contain a bunch of integers。

And the way that I give those integers to the program is through this sign here。

 which is an input redirection， so let me go back to the previous slide very quickly。



![](img/95e7598ca030ac47002e841e014007ef_71.png)

You see here that in my C press program， I read all of the integers through C through like the keyboard input。



![](img/95e7598ca030ac47002e841e014007ef_73.png)

And in fact， here I'm not typing anything on the keyboard by using the sign I am feeding。

Essentially like an emulation of what I would be typing on the keyboard。

 except that everything is just coming through like from a file。

So I just need to like have a file with a bunch of integer and then I can feed that file to the program and the program will think that it's me typing like a bunch of numbers whereas in fact。

 everything is being fed by this input file。

![](img/95e7598ca030ac47002e841e014007ef_75.png)

So， so let's see。So in that input file， I have 1 kilo， so 1000 integer。

 and I give that to the program， the3 sum， which detects。

 you see like a certain number of triplets among that data set。And takes about one second to wrap。

Now let's do the same experiment on a bigger file， so let's actually double the size of the input file。

Let's do it with a file that doesn't have a000 integers， but 2000 integers， 2k。

And you see that now the program takes about eight seconds to run。So let's make it even bigger。

 Let's double it again， Let's go to4 kilo。😡。

![](img/95e7598ca030ac47002e841e014007ef_77.png)

Integers。And now you see that the program takes about 62 seconds， so about a minute。And again。

 let's double。And let's go to an input that has 8，000 integers。

And here we see that the program total takes about 500 seconds。Which is many minutes。So。

That's what we have。We wrote a certain program， a certain algorithm。

That we compiled and then we tried the same program， but on different sizes of input。

And we gathered the reading time， how long does it take to process that input？

And we got a bunch of numbers like we see the evolution of the running time。

The thing is like if I were to just give you that and tell you like， well， analyze it like like。

Tell me how much like can you predict how long it would take if now I were to give you an input of 16。



![](img/95e7598ca030ac47002e841e014007ef_79.png)

Thous0 integers。How from those experiments， how can you predict the running time for input sizes that you don't know？

The thing is here because it's only numbers， it's a little difficult to comprehend right so let's try to do it visually。

 maybe that'll be helpful。So what I did is that I use the size of the input as the x axis as the input。

And the running time here as the output are as like the y axis。

 and I plotted that and that's what I get。

![](img/95e7598ca030ac47002e841e014007ef_81.png)

So again like on the x axis， I have the input size， so 1000 integer， 2000 integer， 4000 and so on。

 and on the Y axis I have the running time in seconds so you see like one seconds here what was it like eight seconds then like 60 and some seconds and then 500 seconds？

The thing here is that like how so I have definitely a curve。Which is not a linear curve。

 as you can see。

![](img/95e7598ca030ac47002e841e014007ef_83.png)

And ideally I would be I would want to be able to predict what will be the running time for an input which I haven't tried yet。

 so for example， if I wanted to feed an input of 60000 integers like how much time would it take and。

Unless I run this simulation。Or unless I find the equation that's behind this curve， I don't know。

So how could I know？Well， one thing that we could do here is change the way that this plot is being traced。

 like how that this curve is being traced。And instead of using a regular plot。

 we could use something that is called a log log plot。

 that's a plot where the X axis is put on a logarithmic scale and the Y axis is put on a logarithmic scale。

So let's see what it looks like。So I haven't changed any of the numbers， I still have like 1000。

 2000， 4，000 8000， and I still have like one second， eight seconds。

 60 seconds and 500 seconds like my data points are still the same。But the plot itself。

 like the way that those data points are being represented is slightly different because now my y axis is on the logarithmic scale and my AX axis is on the logarithmic scale and what's cool now。

 as you can see is that my curve here， is now completely linear。

Which is going to be a lot easier to understand and to analyze。

As you hopefully remember from high school。A linear curve here。

Can be kind of expressed by an equation， and that's the typical equation。We have so F of F of x。

Is equal to M times x M is the slope that's the coefficient that determines like the slope of my curve。

And we have B here， which is the intercept。That's the x value when the curve crosses the zero line。

So what I would want to do here is determine what is M and what is B。

 and this way I'll have an equation that corresponds to this line， right？嗯。

So here let's replace F of x and x by the logarithmic terms。

So that's's that's what we have like that's the actual equation here。That corresponds to this slide。

Now what we need to find is M and B。It's actually possible to find M and B。

 so M we can find the slope here by taking two data points and by essentially dividing them by one another。



![](img/95e7598ca030ac47002e841e014007ef_85.png)

And once you have M and it gives you the slope。You can go back to the equation。

 replace M with its value， and then compute B by itself。

And so eventually we see that like M is about like three。And B is about minus 30。

Now that we have the equation here。That is a typical。

linearinear equation for which we know the slope and the intercept， we can go back。

To the curve that was on the standard plot， on the standard scale。

And here I'm not inventing anything， the typical equation to go from a log log plot back to a standard plot is this equation。

So now that we have M and B。We know that like on the standard scale， the equation is。

N to the power of m times 2 to the power of b， and because we know M and B。

 we essentially have the equation。So let's go back to the standard plot。

The one that I showed you in the beginning where we're back to having like our input size on a linear scale and the running time on a linear scale。

 and you remember like we had this curve here that was not linear because it was like slightly bent。

Now， we know exactly what equation here。Is behind this curve。And so technically。

 now we can run this equation to predict。Values for which that we did an experiment。So for example。

 like we could now calculate for 16 kilo integers as an input。

 we could predict what would be the running time。By applying this equation。

 we would essentially replace n by 16 kilos。Then resolve this equation and that would give us t of n。

 which is the running time for that input size。So let's try it actually。😊，So that's our equation。

N is the input size T of n is the predicted running time。

 how much time does it take to run the program on this input size？

If we apply this equation on n being equal to 8000 or on n equal to 16，000。

Those are the running times that we get， the predicted one。So just by applying this equation。

 so we have 502 seconds。Or 4000 and some seconds， that's the prediction that we can have by applying this formula。

Now let's actually like go back to CSsIF and run。The program on that input size and see if the predictions are being matched。



![](img/95e7598ca030ac47002e841e014007ef_87.png)

And the answer is like， yeah， pretty much。Actually。

 that's a result that we already knew because we already had run the program on that size of input。

 but we can do it again when we run our threesome program on an input of 8，000 integer。

 we get 500 seconds which is。

![](img/95e7598ca030ac47002e841e014007ef_89.png)

Pretty much the same as the prediction。And if we were in the same program on an input of 16。

000 integers， then it takes about like 4，000 seconds。

 which is also like pretty much what we had predicted。

And actually like the only reason that it's not perfect that we have like see like two seconds here of difference and about 10 seconds here of difference is that the coefficient m。

 the slope M。And the intercept B， I truncated them so that they wouldn't be like too long in the equation and by truncetating them。

 we're losing a little bit of precision。But if I were to like leave them exactly like they were and not truncet them at all。

 then the prediction would be almost perfect with like predict perfectly what the experiments actually are。

So that pretty much like concludes this experimental approach， so let's summarize aliobi。



![](img/95e7598ca030ac47002e841e014007ef_91.png)

The problem of this experimental approach， first of all， I think you'll have to agree with me。

 I hope I didn't loss too many of you， it's complicated， right？

You have to like write the program so first of all。

 like you need to actually implement the algorithm that you want to characterize。

 you need to first write it because you need to run it。

And of times that you have data points so that you can extract a certain curve。

 then you need to characterize this curve and find the equation that's behind the curve and once you have the equation。

 then you can apply it to input that you don't know and you can start like predicting oh how long is it going to take if the input is of a certain size。

 but first you have to implement the thing。

![](img/95e7598ca030ac47002e841e014007ef_93.png)

Then the problem is that like once you implement it and you run it on different input size。

 it also like the results you're going to have like the the。

The measurements that you're going to do in terms of running time they heavily depend on external factors。

 so for example like the quality of your input data。

 if your input data always trigger the best case scenario for your algorithm。

 then your measurements are going to be skeweed， if your input data always trigger the worst case scenario of your algorithm。

 then it's going to be skewed in another way。And then you have many other factors like the hardware that you're using。

 the software that you're using to compile the program in the first place。

 are you using optimization of the compiler or not。

 it can also be the system onto which you're running your program， is it Linux。

 is it macro acid windows like you have a lot of different factors that will influence the quality of the measurement that could like almost invalidate your model and also need to you would need to run a lot of experiments to gather as many data points as possible so that the quality of your curve would be really good and you would be able to extract an equation out of it。



![](img/95e7598ca030ac47002e841e014007ef_95.png)

Bottom line。This。Approach is not great。And we're going to need a better model and that's going to be fun next time。



![](img/95e7598ca030ac47002e841e014007ef_97.png)