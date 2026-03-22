# 耶路撒冷希伯来大学《从零开始构建现代计算机｜Build a Modern Computer from First Principles》中英 - P20：20_05_02_单元-3-1-时序逻辑.zh_en - GPT中英字幕课程资源 - BV1Zp421y7Ex

![](img/d74d95192c23dd896188ce8946a596bc_0.png)

So in this week， we're going to start talking about how computers do one thing after another。Really。

 in the first two weeks， we've completely ignored the issue of time。 Everything happened immediately。

 There were inputs。 and immediately， the outputs were some function of them。 The inputs never change。

 We didn't have any notion of change。 We didn't have any notion of things happening one thing after another。

 Just was some kind of logical mapping from inputs to outputs。 But that is， of course。

 not what really happens in real life。 We need to be able to take care of time。

 We need to be seen to think about time because computers worked during time。

So what kind of thing do we need from time。 Well on the positive side。

 there are two issues that we want to do。 The first thing is we want to be able to use the same hardware to compute many things。

 one time after another。 If we know how to add two numbers。

 we don't want to just use certain piece of hardware to just once add two numbers。

 We want to use the same piece of hardware to add numbers every time we have two numbers that we need to add we just want to add them one after another。

 So we need to be able to reuse our hardware。 For example。

 if we take some kind of loop in in some kind of software program that the loop calls for doing the same thing many times。

 we want to be able to use the same hardware to do that。😊。

Another important thing that we need time for is to actually remember things from the past when we。

 we need to remember intermediate results。 We need to remember where we are in a computation。

 For example， if we have a loops that adds 100 numbers to each other and get a total sum， we。

 of course， we need to add then intermediate sums。 Otherwise。

 there is no way for us to actually get buildup the total sum。

And these are the two things that we really want to think about time for。

 And yet there's another thing that we really don't want to think about time for。

 but we need to basically， you know， sweep it under the rug in a satisfactory manner。

 And that is the fact that computers work in some finite speed。

 And we need to be able to make sure that we don't ask the computer to perform computation faster than it can。

 or at least we know how fast can our computer run。

So let's see how what is the way we're going to deal with it？So really， in physics。

 in the physical world， time is a continuous era of time。 starts at time， negative infinity， maybe。

 you know， maybe the big bang and keep that advancing in seconds， milliseconds， microseconds。

 speakerseconds， maybe to some limit of quantum time， but maybe not。

What we're going to do what everyone does in computer science。

 We're going to actually convert this continuous physical time。

 which is very complicated to think about into discrete time。

We're going to have what's called the clock， which is some kind of oscillator going up and down at a certain fixed rate。

 And each cycle of the clock we're going to treat as one digital integer time unit。

So once we have this clock， it will basically break up our physical continuous time into a sequence of time equals1。

 time equals 2， times equals 3 and so on。 Within each time unit。

 we're going to deal as a time within each time unit as though it is one individualdi thing。

 Nothing changes within a time unit， within an integer time unit。😊，So， for example。

 if we have a Na gate， for example， if we look at its input and its output at every different time unit。

 it can have a different input。 And at that time unit。

 it will compute the output from that input in an instantaneous manner as we think about it。

Every time unit， the input could change， and then the output would follow。

 So if you look at the diagram we see here， we see that in time 1， the input is one。

The output is then， of course，0 because that's what an node gate does。 At time too。

 the input was was went down to 0。 For example， it could be stay 1。 But if it went out to 0。

 immediately， the output goes up to one and so on。So this is the way we are thinking about it。

 And this is the way we build all our sequential logic and computers。

 one after another in integer time steps。So at this point。

 now is the time to actually sweep under the rug。 the issue of delays。

When you really look at a physical signal that's really implemented somehow。

 maybe probably with some electrical signals， it doesn't change instantaneously in0 time between time logical time 1 and logical time2 between logical time 0 and logical times 1。

 Really， the electricals current builds slowly and the voltage maybe if that's how we it present actual bits。

 It changes slowly。 And then what we really see if we look at it's a actual analog signal inside our implementation of the gate。

 is going to be some kind of waveform like we see here， a new time unit 1。

 It takes time for the input to reach its final stage。😊。

And then it will also take some time for the output to reach at foundal stage。

 Probably it will take more time than it takes for the input because there is an additional delay。

 the delay of the gate itself。The the whole point of this logical way that we treat。

 we break time into digital， into integer units is the fact that you'd' want to think about these delays。

As long as our clock cycle is not too fast， as long as we take give ourselves enough time between consecutive time units。

 we can ignore everything that happened at the beginning of the cycle， all the gray area here。

And as long as by the end of the gray area， all the signals reach their true and final and consistent state。

 where all done。In fact， the way we choose the cycle of the clock is to make sure that all the hardware there really stabilizes and the implementations give you the logical operations by the end of the grey unit。

 and the clock need to be just a little bit wider than that。😊，So really， in reality。

 there is going to be all these gray areas where voltages changes and the system basically tries to stabilize into the new logical situations。

 And what happens at the end of the clock cycle is what we view as a real logical state of the system。

 and then we can simply ignore these inconsistencies because now whatever happened before the gray area。

 we don't need to worry about it because we know it's gone by the end of the clock cycle。

 So that ends are the way that we sweep under the rug the issue of delays。

 And that really justifies the way that we can think about time in integer steps one after another。😊。

So now we've reached a situation that we have integer time units。

 and we know that something can happen at every different time unit。 under this perspective。

 alls logic that we talked about in lectures 1 and 2。 is was combinatorial。

 The output at time T completely depended on the input at time T。

 There was now information moved from time T -1 to time I to time T。

What we're talking about when we say sequential logic。

 what we mean is that the information at time T， the output at time T depends on the input at time T-1。

 We remember things from last period。 And and based on the previous input as the previous time step。

 we actually compute output as a new time step。 So if we look at the diagram of time units，1，2，3，4。

 And if the input is A， B，C， D， whatever input it can be a single bit， it can be a multibus bit。😊。

In combbininatorial logic。At each time unit point， a was converted to some function of a。

 So the output at time2 was the in was a function of the input at time 2。 And each time unit。

 we could have a different input and different output。 When we have sequential logic。

 The output at time T， it depends on the input at time T -1。 and what happened previously。

In principle， we could also have a depend on what is happening now at time T itself。

 But it's probably best to actually to actually split the two types of computation we do。

 The combinatorial logic， which happens instantaneously within a time unit and the sequential logic where we don't want to mix new information with old information。

 usually。 So we just think about that time at time T plus one depends on the and the input as a previous time unit。

 a time T。😊，Once we have this point of view， we can do a really interesting point of view。

 We can actually have the input and the output be the same bits， the same buses。

 the same locations in our hardware。😊，We and we can now recall it a state as long as now what's of our value。

 a time T depend on the previous value， a time t -1。

 we can have these values live in the same wires in the circuit。 So now we can have a single bit。

 for example， that holds a called state。 And it's a time1， it was some kind of input a。 at time two。

 it will be some kind of function of a F of a at time 3， it will be some function， F of F of a。

 basically F of the previous value that we have and so on。 This now lets us for the first time。

 actually change state as we go along along， never remembering and always building an L previous results。

 So this ends the basic abstract way we're thinking about time in in digital circuits。

 The fact that we actually break it into integer time steps and we look at what happens it sequentially one time step after another。

 rather than continuous。😊，And what we're going to do in the next unit is actually describe the chips that allow us to do this kind of manipulation。



![](img/d74d95192c23dd896188ce8946a596bc_2.png)