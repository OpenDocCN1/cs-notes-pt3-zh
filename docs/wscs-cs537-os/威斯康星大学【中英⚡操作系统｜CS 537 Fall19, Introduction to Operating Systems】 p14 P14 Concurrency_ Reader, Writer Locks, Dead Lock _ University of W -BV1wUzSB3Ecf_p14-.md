# 威斯康星大学【中英⚡操作系统｜CS 537 Fall19, Introduction to Operating Systems】 p14 P14 Concurrency_ Reader, Writer Locks, Dead Lock _ University of W -BV1wUzSB3Ecf_p14-

All right。Good morning， everybody。 The microphones working great。

 So today will be our last regular lecture on concurrency。 Next week。

 I'll do a little bit of a review。 kind of go over some sample problems that you might see on the exam。

 So today we'll just finish up semaphos talking about those reader writer examples and then talking about some problems that many applications end up having。

😊。

![](img/19b27f59ecfbe3f6a774612de786eaf9_1.png)

Okay， so some announcements， you've all turned in Project 4。 I think that went pretty smoothly。

 Overall， I didn't see any last minute problems there。problem project 5 is now available。

 So the good news is I decided to make it much， much easier than I initially wanted。 At first。

 I was like， boarding you。 It's going be a lot harder than the scheduler one。😊，😀。😊，So it's less fun。

 in my opinion， it's， you know， but it's more straightforward。 It should be easier。

 But it is the first time like we're doing this particular project。

 What we tend to do in this class is we take inspiration from other semesters and make some changes。

 But then every once in a while， we like to come up with a completely new project。

 So this is like a completely new project。 So that's what takes took me a couple days to make sure it's pretty reasonable。

 So it'll be due on Monday。😊，It should be pretty straightforward。

 So you can get a new project partner。 if you would like one。 There's the web form on canvas。

 if you'd like to request a project partner and we will match you。 But， of course。

 it's always better if you find someone that you know that you'll work well with。

And then midterm 2 is coming up。 It just covers all of our concurrency topics with a tiny bit of retrospective on virtualization。

 Our next lecture Ill spend a little bit of time reviewing concurrency。

 But then we're just going to start going into I O and persistence， which is the next topic。

So any questions about these announcements。

![](img/19b27f59ecfbe3f6a774612de786eaf9_3.png)

All right。Okay， so today， we are going to go back to semaphos and understand the reader writer locks。

 Then we're going understand a whole bunch of bugs that occur in real applications。

 So we'll talk about how you'd fix them。 So it should be a good review for you on how those different primitives work。

 So we'll fix some aity bugs。 We'll fix some ordering bugs。

 We'll understand how deadlock occurs and how we could fix that。



![](img/19b27f59ecfbe3f6a774612de786eaf9_5.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_6.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_7.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_8.png)

Okay， so let us review。 So quickly， with concurrency， we're trying to get two different properties。

 Sometimes we need to provide mutual exclusion， which means just one thread or one process at a time is in a critical section。

 executing a particular piece of code。 So one thread at a time can acquire a lock。

 And then the other primitive that we've been looking at our other requirement。

 is that we sometimes need ordering that we need it to be the case that some code in B runs after some code in A has already executed。

 And so for that， we have conditioned variables to do the signal to wake up a waiting process or a thread or we have some ofs where you're recording some state and then maybe be waking up another process or thread。



![](img/19b27f59ecfbe3f6a774612de786eaf9_10.png)

Okay， so we looked at condition variables。 Remember。

 the key thing about conditioned variables is that they do not track any additional state other than that cu of processes that are waiting for a condition variable。

 A condition variable really is just a cu is what you should think about it as。

So you have to have a lock that's associated with a conditioned variable。 When you call weight。

 you have to have that lock held。 You then go to sleep。

 always go to sleep and wait and you release the lock when you do that。

 and you're sleeping and waiting in that weight statement until another thread or process called signal that will have this process be free from waiting for the condition variable。

 which is what I'm showing here。 A is not waiting for the conditioned variable anymore。

 But now it does need to wait to acquire that lock again that it relinquished when it went into weight。

 And it's possible that another thread could grab the lock next， like thread D。

 And so a would have to wait a while longer before it actually returns from weight。

So that's our really， really quick review of condition variables。

 Does that trigger any questions for people about condition variables。Great。

 so then we contrasted that with semaphos， which are another approach for giving ordering。

 So the main difference between semaphos and conditioned variables。



![](img/19b27f59ecfbe3f6a774612de786eaf9_12.png)

Is what would you say in your head， It's that semaphoes have some state associated with them。

 They have an integer value associated with them that you can initialize the semaphore， too。

 but applications can't then look at the value of that integer that's being stored in the semaphore。

 But that integer is going to determine how the semaphore behaves。 So basically。

 if that integer value is greater than。

![](img/19b27f59ecfbe3f6a774612de786eaf9_14.png)

m。Basically， I think I reversed this compared to some other ones。 You wait while the value is 0 or。

Les， and then after that's the fact， then you decrement it。

 So the behavior of your semapho depends upon what that integer' value is。 Basically。

 you'll only return from a weight when that semaphore is one or higher before you call it。



![](img/19b27f59ecfbe3f6a774612de786eaf9_16.png)

And then when another thread calls post， it increments that value and potentially wakes up some weighting waiters。

 If they saw that the value had been less than 0 before0 or less when it came to the weight。



![](img/19b27f59ecfbe3f6a774612de786eaf9_18.png)

Okay， so we saw in a couple of examples that we would want to initialize the semaphore differently。

 depending upon how it would be used。 So we saw that if we wanted to use a semaphore to join a parent and a child and make sure that the parent waits until the child calls exit。

 Then we initialize that semaphore to 0。 so that when the parent calls weight。

 it will see that it's0， it has to wait there。 And then when the child called exit。 It called post。

 which incremented the semapho by one， which then freed the parent to continue。

 So we saw if you wanted to do ordering， you would usually initialize the semapho to 0。

 And when you wanted to use the semapho for mutex。

![](img/19b27f59ecfbe3f6a774612de786eaf9_20.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_21.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_22.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_23.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_24.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_25.png)

You could initialize that semapho to a1 so that one thread or process at a time would be able to continue through that weight statement。

 And the next thread that calls weight would see now that the semapho is 0。

 and it would act just like a lock and force that next thread to。

 to wait until the thread that had gotten the lock calls post and increments that value back。Okay。

 so that was the basic definition of how semaphores work。



![](img/19b27f59ecfbe3f6a774612de786eaf9_27.png)

So then we looked at this dining philosopher's problem。

 And the reason I want to review this for you all quickly is that because this is emphasizing this deadlock condition。

 we're going to be looking at deadlock a bunch in lecture today。

So this is a classic problem to get you just thinking about how to acquire multiple resources。

 And so we think of the code as there's some threads that are like we have end threads。

 They're all independently doing some computation for some amount of time like thinking。

 they then decide that they need to grab two resources simultaneously。

 And there's kind of a complicated relationship across those resources， right。

 that each of these threads needs to acquire different resources。

 and there's a relationship across different threads with which resources they need。

 So then they grab those resources。 They have a critical section。 You could think that's what eat is。

 It's doing some work。 And then once it's done and puts those resources back。



![](img/19b27f59ecfbe3f6a774612de786eaf9_29.png)

Okay。So we looked at one approach for implementing this。

 where we represented each chopstick with a semaphore。

And so we would initialize each of the semaphos to one so that each philosopher would be able to grab a semaphore。

 grab the chopstick。And when it's done， it's basically putting down the chopstick。

 It's setting the value back to one。 So only one philosopher at a time with his implementation can grab the sepho or grab the resource that's associated with that。

 which is this pretend chopstick。

![](img/19b27f59ecfbe3f6a774612de786eaf9_31.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_32.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_33.png)

Okay， but the problem with this implementation is that there's deadlock。 Remember that that。



![](img/19b27f59ecfbe3f6a774612de786eaf9_35.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_36.png)

So all night。My slides are acting funny today， but what happened in this example was each of the philosophers grabs their chopstick to their left and then they're waiting to get the chopstick on their right and then because of that。

 none of them can ever grab both chopsticks if we have this bad timing and then they all starve to death and starving again being a technical term that we can use when you don't get a resource is that the threads would starve there and will be forever deadlocks because each one of them is already has one resource and they're waiting to acquire the next one。

Okay， so this was a case where we ran into deadlock because of how we set up how we were acquiring resources。

 We had this circularity。 So we said that one way to break that deadlock was to have one of the philosophers grab resources in a different order so that there's not that circular dependency or the other solution we briefly looked at was。



![](img/19b27f59ecfbe3f6a774612de786eaf9_38.png)

How to。Express our constraints in terms of safety and liveness。

 And that really got the maximum throughput where we let the most threads possible grab resources。

 And the key to that was that we didn't represent each chopstick with a semaphore。 Instead。

 we had the threads figure out， are they able to eat now。 And if they are。

 then they did the right work。 So I'll just review that really quickly with you all。



![](img/19b27f59ecfbe3f6a774612de786eaf9_40.png)

So this was the first attempt to fix。Deadlock。 and this did work。

 It's breaking that circularity where we have most of the philosophers grab their right chopstick first。

 And then the other one。 But the last philosopher does things in the opposite order。

 So now we have no circular ring of dependencies。 so we can't have deadlock now。 So in this case。

 this philosopher here would be able to grab both of its。Chopticks， and eventually。

 it will relinquish one of them by calling put down chopsticks， which calls post on those chopsticks。

 which effectively puts them down so that like then this。



![](img/19b27f59ecfbe3f6a774612de786eaf9_42.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_43.png)

Thread over here。 would be able to grab that one。 So that was one way to break deadlock was to make sure that there wasn't a circularity across these。

Depenencies。

![](img/19b27f59ecfbe3f6a774612de786eaf9_45.png)

That was one way to do it。 Another way that was more complicated to fix。

 But I think is really interesting and a very elegant solution。 If and it really。

 once you understand this code， then you will understand how semaphos work。

 So if I go over this too quickly in class， I certainly recommend that you look at this code offline and make sure that you understand it。

 But I'll probably kind of use this as like a exam type question where I say， like， okay。

 imagine one thread runs and get stuck here and then another thread runs。 You know。

 what's going happen。 Just so that you can step through this code and understand how it behaves under different scenarios。

😊，So it just requires understanding really how this code works。

 And then sometimes what I might do is I might switch around some of the statements or make a slight modification and tell you that I made a modification and then ask。

 you know， is that going to work or what kind of problems is that going to lead to。

 But I'll never like secretly change the code and expect you to find that， oh。

 there's one thing in here that you thought was the same， but it's really different。Okay。

 so the key with how this code works is each of the threads， again， is going to call take chopsticks。

 and they are going to figure out。If it is safe to get the resources that are next to them。

 And so the way that that worked is that we have a critical section that's protected by this muttex by a sephore that's been initialized to one。

 And we have to put that in a critical section because we're setting some variables and we're reading other variables and all of the philosophers could be doing that simultaneously。

 So this is clearly a critical section between this weight and this signal on the semaphore that I've called Mutex。

 And there's a similar critical section when you put them down。So within that critical section。

 it's safe to be modifying all of these globally shared variables。 So these are global variables。

 Remember that everybody can see the state of all of the other philosophers。

 So what you want to do when you're taking your chopsticks then is you show that you're hungry。😊。

And then you look to see if the。Philosophers next to you are not eating。

 Then it must be safe for you to eat。 It must be safe for you to get both of those chopsticks because they're not using them。

 So that's our safety requirement。 And so the way that it works。 then is you'll see that within here。

 after you've done your check that it's safe。 You switch your state to eating。

 This is in the critical section so we can change our variables。 But then the neat statement。



![](img/19b27f59ecfbe3f6a774612de786eaf9_47.png)

Is that we call signal on our own semaphore here。 So see we're then incrementing this semaphore to show that we should be able to continue running。

 We're incrementing that semaphore to one。 and it started out at zero。

 So then when we return from test safety and liveness， we exit our critical section。

 this thread can look at that value of that semapho。 And if we called signal on that semaphore。

 this weight will continue。 and we'll effectively have you know。

 Atomically grabbed the two chopsticks that are associated with this philosopher when its neighbors aren't eating。

 And so the key is we signal on that semaphore， and then we wait on that same sephore。

 So if we didn't signal it， we'll be stuck here on weight until some other philosopher eventually calls put chopsticks。

 One of those that are next to us that must have been eating。



![](img/19b27f59ecfbe3f6a774612de786eaf9_49.png)

When they call put chopsticks， they enter this critical section。

 they change their state to thinking now they used to be eating now they're thinking。

 And now they test the safety and liveness for each of their neighbors。

 And so now this would go back and see that the neighbor that got stuck over here before。

 it is hungry and your state is not eating anymore。 Its thinking。

 And so it just needs to check that the state of the philosopher on the other side of the one that was waiting。

 is also not eating。 And if it is okay。

![](img/19b27f59ecfbe3f6a774612de786eaf9_51.png)

It sets the state of that waiting philosopher eating and signals it so that it could continue from that may eat that it was stuck with over there。

So。Any questions about that， yes。So youre in this put thing。

 could we have moved this outside of the critical section， No， because it could then be the cap。

I guess I'm going to say not generally。 I mean， I guess I could would have to really think through。

 Is it somehow safe to do that。But in general， you need to have all of your variable modifications within the critical section。

Am。I I don't I it it would take me a moment to come up with a counter example on where we're going have our race condition。

 But in general， you do not want to move that outside of the critical section there。

But with a little bit of non pressure think time， we should be able to come up with a case where that would not work。

 yes。No， that 1， I can tell you， you cannot。You cannot move this weight up before the signal。

 Is that what you're asking？Because if we did that。

 then we are holding on to the Muts while we're waiting for this。

 and then nobody else would be able to enter the critical section。

So that's kind of the difference between semaphos and conditioned variables。

 And with condition variables， our code tended to look like that。

 We did call weight on a conditioned variable inside of our critical section because we know that the condition variable weight relinquishes the mu text so that someone else could run and change the state here。

 that's why we have to like track the state in the semaphore so that if there was a context switch after we release the mutex。

 and we're not in that critical section。 It's still atomically recorded the fact in this may eat semapho that someone else called signal。

 So there's no race condition after this signal in this weight because the semaphore is atomically tracking that for us。

Yeah。Yeah， yeah， yeah。I use those two terms interchangeably to add to the clarity of the situation。

 Yes， signal and post at the same， yes。Yes。😊，So this， oh， yeah， this， this should be。

 I just shortened that。 It's the same thing as test safety and liveness。 It's the same routine。

My code would definitely not compile that I put on PowerPoint slides。Of， things will get capitalized。

 They shouldn't have been capitalized。's， it's。Close， but not perfect。More questions。Alright。

 so please look that over， and then maybe we'll kind of do some examples that involve this or the next example on Tuesday of next week as well。

 So here's another great example of really using semaphos in nontrial ways。



![](img/19b27f59ecfbe3f6a774612de786eaf9_53.png)

Okay， so we want to use semaphos to implement what's called the reader writer lock。

 So with traditional locks， they just provide mutual exclusion to everybody。

 It treats whether you're reading variables or writing variables exactly the same one thread at a time can acquire a lock。

 But with a reader writer lock， we want any number of readers to be able to acquire the lock because they're not modifying this data in the critical section。

 They're just all reading it。 But we can only have one writer holding that lock at a time。

 And a writer can't hold it at the same time as a reader does。

 because the writer is modifying the data structure。

 And so if a reader then saw the data structure might see it in some， you know。

 some unknown state there。And certainly， two writers can't be modifying the data structure at the same time。

So we're gonna look at two different implementations。

 So is that definition of reader writer locks clear what we need to do there。Okay。

 so reader writer locks are really very popular。 A lot of different applications want this type of support for their data structures。

嗯。So there are two different ways we can implement reader writer locks。

 And the difference comes down to who should have priorities。 should it be a readers or writers。

So we'll look at implementations that work each way。 And so basically。

 we'll look at giving priorities to readers first。 So the only time you won't let a reader grab the reader lock is if a writer is currently holding the lock。

 If there's a writer waiting for its lock， will' let the readers go ahead。



![](img/19b27f59ecfbe3f6a774612de786eaf9_55.png)

So readers get absolute priority。Okay， so this is the first version。

So we are implementing a reader writer lock that we will expose to applications。

 and we're implementing that on top of semaphos， and so we'll have two sephos， both acting as locks。

 and so by that naming convention， you can usually infer that those two sephos are going to be initialized to one that they're acting like mutual exclusion instead of ordering。

And we're going to have some variable that's just tracking the number of readers associated with this reader write lock。

 and there are zero readers know， they have the lock commercial。



![](img/19b27f59ecfbe3f6a774612de786eaf9_57.png)

Okay， so this is the code。So you'll notice that there's a choir， a read lock。

 There's release or read lock， and then there's a choir， a write lock and release a write lock。

 So the readers are going to use this version， and the writers will use this version。

So let's assume we have this call stream and kind of understand the code for that particular call stream。



![](img/19b27f59ecfbe3f6a774612de786eaf9_59.png)

O， so thread1 calls a cho readlock。 And by that， I mean， this whole big long thing。



![](img/19b27f59ecfbe3f6a774612de786eaf9_61.png)

And so what's it going to do， it's going to call Sam Wait on the reader。Lock。

 And so that's just to provide mutual exclusion。 That's what you can see is this weight and post。

 which sometimes I call weight and signal。 But this is providing mutual exclusion over this critical section here with that lock。

 And we have the same thing over here。 We have a critical section between the weight and the post using that lock variable。

 So this is all a critical section in here。 And that makes sense because within that critical section。

 we're modifying our internal variables。Okay， so I grab this lock because I'm T1。

have mutual exclusion。 I increment the number of readers。 So now the system knows we have one reader。

 We say， hey， I'm the first reader。 So Im going to call some weight on the right lock。

 So we're making sure that the right lock is available。

 which is making sure that there are no writers right now。

So we will be able to grab the right lock as well， because that was initialized to one。

 So now the right lock is down to 0。 And then we release the。



![](img/19b27f59ecfbe3f6a774612de786eaf9_63.png)

General lock so that other threads can come into this critical section。

 So now our reader thread has a reader lock， and it can enter the critical section and do all the reading that it once of this data structure。

Then thread2 comes along， and it calls a cho read lock。 goes into the critical section。

 increments the number of readers。 It sees that it's two now。

 So it kind of knows that someone else already has the right lock。 So it doesn't mean to do that。

 And it wouldn't be able to get it anyways。 And so it just releases the regular lock and also goes into the critical section and does all their reading that it wants。

Now， T 3 comes along， and it wants to grab a right lock。 It's a righter thread。

 And so it calls acquire right lock。 It calls some weight on the right lock。

 And so what's going to happen at that point there。

So that's the important thing is that the reader already called some weight on that right lock。

 So when the writer does that， it's not going to be able to get this right lock。

 That value has already been decremented down to 0。 So the rid will be stuck right here， waiting。

And it'll be stuck there waiting until someone calls post。 Someone releases the lock。Okay。

 so we have a writer that's waiting here。 So thats that's the state that this one is in。

 Now let's imagine that T2 releases the read block that it had。 So what does it do。

 It enters the critical section， decrements the number of readers。

 The number of readers it's going to see is one。 And so then it just exits the critical section。

 Then the other thread comes along。 These threads could have run in either order that didn't matter at all。

 But our last thread that had a read block comes through。 It enters its critical section。

 decrements the number of readers， which will now be0。 And it will see now that a writer could run。

 There's no readers that have the readb。 So it posts to that right lock。

And so what happens when we call post on that right lock？



![](img/19b27f59ecfbe3f6a774612de786eaf9_65.png)

The writerer thread that was waiting to acquire the right lock that was waiting here。

 It will return from that statement， right， It's been signaled。

 It's been posted on that particular semaphore。 And so that weight call returns。



![](img/19b27f59ecfbe3f6a774612de786eaf9_67.png)

Good。So then our writer will now have the right lock。And so then while that writer is going。

 if now a thread forward tries to acquire the readb， what happens。

 The first one that comes through tries to enter the critical section。

 It can increments the number of readers， which will now be。1。

So it will call Sm weightade on the right lock， and it won't be able to grab that， right。

 because the writer has already done that。The right lock is at 0 now。

So this is what's really interesting。 So our first reader is going to be stuck here。Now。

 let's imagine another thread T 5 comes and tries to acquire readlock。

How about you talk with your neighbor and try to figure out what's going to happen to threadread 5 when a writer has a right lock。

 One other reader tried to acquire a relock。 What happens to the next reader。

Because it kind of looks like there's something broken， but there's not。 So it's kind of neat。



![](img/19b27f59ecfbe3f6a774612de786eaf9_69.png)

Yeah， so I guess you can ask questions while you're trying to figure this out， yeah。Dear， oh， oh。

 you're just pointing， okay， talk。Is a question now。Yeah。😊。

There are many different ways you could implement。 You could do it with like mu taxes and condition variables。

 but you do need some type of mutual exclusion and ordering， yeah。Oh。They are just。

Each of these in this case。I think。Well， you could have multiple writers that all try to acquire the locke。

So I'm not sure if it would work with a binary semapho or not， but。

Because certainly multiple writers could be waiting there。Yes。Right。

 so line 16 is saying it's only the first reader that comes through that needs to check this condition and make sure that there's no writers right now。

 All of the subsequent readers know that the first writer already checked to make sure there were no。

Writers。Yeah， yeah。 So this se weight is making is the same as this se weight on this right lock。

 It's making sure that the right lock is available And so basically， there。

 that means there are no writersers that have the lock right now if we're able to。



![](img/19b27f59ecfbe3f6a774612de786eaf9_71.png)

Grab that right line， yep， all right。So question for you all now， T 5 that calls acquireir readlock。

 Where is it going to be blocked on what line in this code， and why is that O。

What so who thinks it will be line 14。Yes， line 14。 I started for the beginning。

 And it just coincidentally， that is correct。 Okay。

 so that seems weird that it can't enter the critical section at all。

 And so we want to understand why that's correct。 So T4。

 we said it was trying to acquire the readlock。 and it got stuck here on S weight。

 But it had already acquired the mutual exclusion lock。

 And it's not calling release of that mutual exclusion lock until it's done。

 and it's not going to be done for quite some time。

 So all the subsequent readers that try to acquire the readlock are going to get stuck waiting just for this like mutual exclusion lock。

😊。

![](img/19b27f59ecfbe3f6a774612de786eaf9_73.png)

Which is fine。 So when we need to understand why that's okay。So then when T3， who was our writer。

 they call release。 they're going to call post on rightlock。That will wake up T 4。

 the first reader who got stuck here。That first reader will。Return from some weight。

 And then it will release the mutual exclusion lock。 And once it does that。

 then that reader T 5 that was stuck over here， then it gets to run。

 It'll increment the number of readers to be2， it'll see that it doesn't have to worry about the right lock。

 and it just continues。 So all of the subsequent readers after the first reader got stuck here。

 they just pile up waiting to grab this lock。 But once the first one releases the lock for the mutual exclusion。

 they'll all be able to run and grab the read lock。



![](img/19b27f59ecfbe3f6a774612de786eaf9_75.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_76.png)

So does that make sense to everybody。So I think if you understand that， again。

 it's not the most straightforward stuff。 It's a good indication that you're understanding what's going on。

 And I'm happy to answer more questions about it， yeah。



![](img/19b27f59ecfbe3f6a774612de786eaf9_78.png)

Great， so we can't make any assumptions about who gets to go first。 So for correctness。

 you should just assume it's the worst possible one。 And the scheduler is being malicious。

 But we hope like for performance and fairness that this scheduler is maintaining a cue and it's like first come first serve。

 But there's always glitches that occur。 And you just can't assume that if it's needed for correctness。

Yep， more questions。 Okay， so this is the version of Read Write locks， where readers get priority。

 And so to show that， this is the same code。 And let's just quickly look at a slightly different scenario。



![](img/19b27f59ecfbe3f6a774612de786eaf9_80.png)

So we had two threads， just like before， who acquire readlocks。

So they're in the critical section reading the data structure。 And then just like before。

 we have T 3 who tries to acquire a right lock， and it will be stuck here。 right。

 We saw that exactly before。Now， what I want to have be different is T4 comes along。

 and it wants to acquire the readlock again。 So even though T3， the writer is waiting。

 even though it arrived first， this implementation is going to give priority to this reader that's coming along。

So that's what's going to be different about this implementation versus the next one。 The T 4。

 the reader gets to acquire the read block， even though there's a writer that came earlier that's waiting。

 So look at this code for a cho。 It enters the critical section。

 It increments the number of readers  to 1，2，3。 It's the third reader。

 It doesn't have to wait for the right lock。 and it just exits this and goes and reads。

So what problem could this implementation potentially have。应没事。Yeah。I could just like。Right， right。

 Exactly。 The writer thread might never get access to the resource。

 We might starve it if we have a steady stream of readers that keep arriving。

 just as long as there's one reader that still has the read lock。 when another reader arrives。

 we can just keep that writer from ever getting the lock。



![](img/19b27f59ecfbe3f6a774612de786eaf9_82.png)

Alright， so we're going to look at a different implementation。

 Any questions about this before we move on to the next one。



![](img/19b27f59ecfbe3f6a774612de786eaf9_84.png)

Okay。So next implementation， this one's going to be more challenging。So in this one。

 writers are going to have priority If a writer ever comes。

 we're not going to let readers just get the readlock。

 We're going to make sure that the waiting writer gets to go next。

 and we're going to structure this completely differently。 Then the previous example。

 we're going to structure it much like more like the dining philosopher version where we tested it for safety and liveness where we're using our semapho is to kind of track like can we go or not。

 So we're going to have a semapho that's can a reader go we'll have apho tracking can a rid go。

And we're going to have a bunch of shared variables thatll all be initialized as zero。So。The muttex。

 that'll be initialized to one， because it's acting like a muttex。

 and these other semaphores they'll be initialized to 0 because we're going to be testing first to see if the condition holds。

 and then we'll call post on it。 And then only if we've tested for that condition and seen that it holds should subsequent。



![](img/19b27f59ecfbe3f6a774612de786eaf9_86.png)

Threads get to go， okay。So this is the code， so this will take a minute to understand this。And。

We're going to use this。 I don't know how to fit it on a slide， better than this。

It's really not that bad， it's just slides are horrible。

So we're going to do the exact same example that we started with before where we saw that the readers could starve out the writers。

 So let's just step through the code and see what happens We can all understand code。 Okay。

 so thread1 calls a choir readlock。 So this is the mut text。

 It's guaranteeing that we have mutual exclusion to this critical section because we have a bunch of global state variables in here。

 We're tracking the number of active writers。 We're tracking the number of waiting writers。

 In this case， no writers have gone yet。 So we'll see that this is zero right now。

 So we're going to post on our own that read semapho that's tracking whether or not we can read and we're going to increment that to one。

 and we're going to have some other state we're going to track the number of active readers we have。

 which will now be one。

![](img/19b27f59ecfbe3f6a774612de786eaf9_88.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_89.png)

We won't take the else branch。 We then exit our critical section。 And so it's this S weight。Oh。

I use such different terms each time。 Yeah， post。Okay。

 this is the post or the signal that's incrementing the semaphore so that when we call weight here。

 if we called post we'll be able to continue through。

 so the first reader will continue through this se weight and get to go。

That makes sense to everybody。So first reader saw that there were no waiting writers。

 So it incremented the semapho variable to one。Incremented the active reader count to one。

 exit the critical section， and then sees that the semapho is greater than 0。

 So it's able to continue from the same white statement。All right， so that was the first statement。

 Then thread2 comes along enters the critical section。 The number of waiting writers is still zero。

 so it also posts to it that same semapho incrementous number of readers。

 and then it's able to continue through that se weight down there because it called post on that。

Okay， so the first two readers get through just fine。Now， we have a writer。

 and it wants to acquire the right lock。 And I've put that code over here。We again。

 have a critical section that's protected by a mutex。And again。

 it's always that same form where we then wait on a variable that we are potentially posting to within that critical section。

 So when should a writer get to go。It gets to go as long as there are no other writers。

 no other readers， and nobody else is waiting。If nobody else is waiting， it's the first one。

 it's going to increment the number of writers， and it's going to tell itself that it's okay to write。

 But that's not what we're going to have happen in this case。 because two readers came through。

 So the number of active readers is too。 We're not going to do this code。

 We're just going to increment that we do have a waiting writer。

 Exit our critical section and get stuck here on this semapho。

 That's still at the initial value of 0。I'm looking at some pain expressions in here。 So。

 so please ask questions or just have me repeat stuff because I cannot read your minds。😊。



![](img/19b27f59ecfbe3f6a774612de786eaf9_91.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_92.png)

Okay。All right， so the T3， the writerer thread is not going to be able to acquire the right lock。

 It's going to be stuck here on some weight because it the okay to write semapho was initialized to zero。

 and we did not call post here。 So it's still at zero source。 The writer is stuck here。 All right。

Everybody。Agree with that at this point。Okay， at least I got two knot。

 So that's a good enough for me。 Okay， so threadh 4 now calls acquire readlock。

 And remember in the previous version where readers got preference， this reader would be able to go。

 But in this version， we want this writer to get to go next。 So T 4 is going get stuck。

 We can tell that。😊，So the reader goes into the critical section。

 It sees in our global variable that the number of waiting writers is not equal to 0。

So we are not going to do this if statement， Instead。

 we're going to increment the number of waiting writers， exit our critical section。

 and we're going to be stuck on okay to read because we did not post to it up there。Right。

 so you can see like the way that these semaphoes are being used。

 we're checking a bunch of state in a critical section。

 We're then calling posts within that critical section as a way of like atomically showing that everything was the way we wanted it to。

 And then after we exit that critical section， we can call weight on that semaphore and have all of the concurrency workout。



![](img/19b27f59ecfbe3f6a774612de786eaf9_94.png)

O， but acquire meadlock did not call post。 So it's going to be stuck here for T 4。All right。

Any questions about that， yeah。O to be is initially 0。

 and O to right is initially 0 that whenever we're using these semaphos to do like ordering in this way。

 we're usuallyre gonna initialize them to 0。 And when we're using the semaphore as a mu text。

 we'll initialize it to one， great。More questions。Okay。

 so now let's imagine T 1 and T 2 called release。 We enter the critical section。

 decrement the number of active readers。The first thread。

 we'll see the active number of readers is still one， so it doesn't do this code。

 and it just exits the critical section。 Then the second thread that had the read lock。Calls release。

 enters the critical section， decrements the number of active readers down to 0。

 It sees that the number of active readers is equal to 0。 And there is a waiting writer。

 So it's going to do this。 if statement， It's going to increment the number of active writers。

 It's figuring out that there is going to be now an active writer。

 It's decrementinging the number of waiting writers。

 It's doing that like state management for the thread that's going to wake up。



![](img/19b27f59ecfbe3f6a774612de786eaf9_96.png)

And then we call post。And it's post on that， O K to write that that writer was previously waiting for over here。



![](img/19b27f59ecfbe3f6a774612de786eaf9_98.png)

That when the writer tried to acquire the right lock。

 it wasn't able to call post because there were readers there。 But once all the readers exit。

 they called post on that semapho and exit the critical section。 And so now we go back to T 3。

 It's going to wake up from that semapho because it was incremented to one。

 Itll decremented down to 0 and return。 So our writer has now gotten the right lock。O。

So at this point， we have the writer has the right lock。 You'll remember。

 we had T 4 stuck back trying to get the read lock。

So I can go through this more to show what happens when the writer releases the right block。

 enters the critical section， deccraments the number of active writers to 0。

 There's no waiting writers in our example。 So we go down to this else statement。

 There is a waiting writer There was one。 So we want to tell that waiting reader。 did I say writer。

All right， yes， there was a waiting reader， And so we increment the number of active readers。

 decreement the number of waiting writers， and then tell that one that it can go now。

 So we post to that okay to read that that last reader was stuck on。

And so then they will get the be do， yes。Right， so it should be that then they all wake up。

 We could look at that。 So we have this nice while loop here。

 And so if we had a bunch of readers that had to try to acquire the reader lock。

 they all would have been stuck on okayk to read。 And then this while loop here is taking care of giving them each post or signal to wake each of those readers up。

 So that's why we have to have that wild statement there to keep posting as many times as needed。

 Great，It just。It increments the semapho value by one。 And then if the sepho value is greater than 0。

 Someone who was waiting gets to。Return from their weights。Their their。Their weight statement， sorry。

 and then they'll decrement it。 So the post incremented it。

 The weight waits until it's one or greater and continues。Right。

 so we are directly controlling exactly how many times we call post based on how many active or sorry。

 how many waiting readers we had。So we're doing that very explicitly here where we're in a critical section to make sure there aren't any raised conditions。

We keep calling posts until we've done that one time for every waiting reader。Yes。Yeah， in this code。

 it will starve readers now。 So it has the exact opposite problem of the previous code。

 So we have to give preference to either writers or readers。

 And it's basically because here in our release code， we had the if statement。

 first checking for waiting writers。 So first， we gave preference to waiting writers。

 If there were any， then we let them go。 So we could have slightly modified this to get slightly different policies。

 but we'll go with this policy as our concrete example。 But yeah。

 we first checked to see if there were waiting writers In our example， there were not any。

 So we let the readers go。And if I say the wrong words， sometimes yell at me。

 you just said readers and you to say writers， I don know， O。Yeah， there's no perfect policy。

 You have to give preference or priority to one or the other。 It just depends upon like what。

 you know your workload looks like。 Is it more important for you to get good read throughput。

 or do you know that you have a lot of writers and those writers need to update data structures。

 I mean， you could do something slightly more complicated and kind of alternate between them and。

But these are two basic ones that give priority to one or the other。They are plenty complicated。

Alright， so this is gonna be it for reader writer locks。Unless you have more questions。

So I'll give you all a two minute break。 Ask your people next to you if you have questions。

 and then we will continue。Mmh。😊，ちちちは。So。We're not going to have that。

Situation before we have a bunch of readers that are stuck waiting on the mutts on the outside because the sum weights on the condition variable is outside of the critical section。

啊哈。😊，Yes， we'll wake these all up。U。1。Well， so we're going to we'll end up incrementing okayk to read25 if there were five waiting readers。

 So each of them will decrement it by one， and it will keep staying above0 for all five of them。

 So five of them will be able to return from some weight here。Does it make sense， O， because it does。

 The semaphore records the value of that integer。 It counts how many times you called。U。

Post versus weight， yeah。The other four will continue to wait here until we keep calling。

 but we're going to call you a post for all five of the waiting readers。Okay。Yeah。

So if we have two writers that call Rightlock at the same time。



![](img/19b27f59ecfbe3f6a774612de786eaf9_100.png)

one after another。So the first one。The first one will see that there weren't any waiting writers or anything like that。

 they call post on okay to write， and then they're able to continue through this and they grab the right lock。

 and then the next writer comes along and tries to acquire the right lock。

 That's the case you want to look at。

![](img/19b27f59ecfbe3f6a774612de786eaf9_102.png)

So the next one sees that active writers is equal to one right now。

 so it doesn't do this if statement instead， it increments the number of waiting writers。

Releases the new text for the critical section。 And it's going to get stuck on this statement here。

 on this weight， because it didn't call post for itself。So then in the future。

 when the first writer calls release， it will see that there is a waiting writer that that variable was incremented and it will then call post and let that previously waiting writer continue on that statement。

Does that make sense？Could you say that again？To。I is。Okay， which statement are you talking about。

 You want to。Well， you could come up here and point to the statement that you want me to explain。

Or after。After class， okay， any more quick questions about this？😊，8。All right。



![](img/19b27f59ecfbe3f6a774612de786eaf9_104.png)

But you should be able to just work through each of those cases。 All right。

 so now we're going to talk about how difficult it is to write concurrent programs so you can imagine this seems pretty complex。

 It's pretty easy to have something wrong with this。

 And so people do have things wrong with their concurrent code all of the time。



![](img/19b27f59ecfbe3f6a774612de786eaf9_106.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_107.png)

And we like to think oh， you when you have some concurrency problems， some race condition， oh。

 you just implementedcrement a variable a couple times。

 someone got some extra money in their bank account and their balance。

 but these are certainly very critical problems that were using computer systems for medicine and for real-time systems that control cars and spacecraft and if you have concurrency bugs in your code。

 It can certainly lead to death for people。 So there was a case where people had hardware interlocks。

 locking that made sure that certain things wouldn't all happen together。

 but then they changed it to software with some locking there and they had race condition and they gave too much radiation to a number of individuals。

 So we do not want to have any race conditions in our code。 but that's what's so nice about class。

 We just get to do toy problems with no pressure。 okay so a bunch of people have looked at highly concurrent programs that are written。

 you know this is。

![](img/19b27f59ecfbe3f6a774612de786eaf9_109.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_110.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_111.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_112.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_113.png)

it's been written by many， many people over many， many years。 debugged over many years。

 This is supposed to be very solid code。 and they do find that they have a number of concurrency bugs。

 These are the most difficult bugs to track and find out find and looked at， well。

 how many atimity bugs are there。 So we weren't given mutual exclusion。

 That's the blue ordering bugs。 They didn't use semiphos are conditioned variables correctly or deadlock Also a problem。

 So we'll look at those。

![](img/19b27f59ecfbe3f6a774612de786eaf9_115.png)

Yes。啊哈。😊，要。Yep。Yeah， most like C doesn't have any language support for locks。

 you just have to have conventions and it's usually best if there's one person who wrote all of the code that deals with that essential data structure and understands the locks。

 I mean you can have other languages that have some you know synchronized objects like in Java where there you do have to grab a lock in order to run some of the methods that do write。

 but most language do not have that type of support。 Yeah， so it's dangerous。

 that's especially when multiple people are writing different parts of the code and you have different layers and you have no idea how locks are being used in the libraries that you're calling。



![](img/19b27f59ecfbe3f6a774612de786eaf9_117.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_118.png)

Yeah。

![](img/19b27f59ecfbe3f6a774612de786eaf9_120.png)

Okay， so here was one real bug that occurred in My SQL， and so what is the problem with this code。

 Can you identify it？The big hint is that it's an atimity problem。And the。

Slide nicely shows what happened with the scheduling order。

That the first thread makes sure that this isn't a null pointer， then thread2 comes along and says。

 no it's going to be a null pointer and then we can' switch back to thread1。

 It assumes it's not a null pointer at that point and does something that causes you to have a se fault。

 so this is a critical section and we need to make sure that we can't change the value of that pointer after we've checked it before we use it。

 so how would we fix this problem。We can fix this with locks。

And so the key thing to realize here is that it's not like we're just putting a lock around these two statements。

 like I think you can look at this and say， hey， this is a critical section。

 We better not have a context switch during that。 but what that certainly implies is that this statement over here has to be as protected using the same lock that we can't while we're executing this code then execute this code。

 So even though this single statement， maybe that single statement does execute atomically relative to the other C statement in thread too。

 we need to make sure that that statement doesn't execute in the middle of those two there。

 So that's why we're going to be using the same lock across those two threads。

So any questions about that？All right。Let's look at ordering problems。So this one is harder to see。

 It seems like it should work， and it does not。 So thread 1， the parent thread。

 it's creating this child thread。 and the child thread starts by calling Ma。

I don't know why anyone would write the this code， but this code does not work。

So it helps if you know a little bit about exactly how that thread create works。

 because it seems like this wouldn't have caused a problem。 But thread create。

 it starts off thread 2 and starts running here。

![](img/19b27f59ecfbe3f6a774612de786eaf9_122.png)

And before it returns， you know， this thread is running and it can do this statement here。

 but we haven't yet set the thread。 That's the return value of that。

 By the time threadread 2 gets to that and its routine where it started。

 So it's trying to dereence this variable over here that hasn't been set yet。

So how are we going to ensure that this variable gets set before we read it over here？

Condition variables to the rescue。 And then the question is， exactly how are we going to do that。

 So this is solved with condition variables。 I'm sure we could have solved it with semaphos， as well。



![](img/19b27f59ecfbe3f6a774612de786eaf9_124.png)

So what we're going to have to do is basically， we need to make sure that this statement over here runs after that assignment occurred。

 right， So we're going to use some additional variable to kind of track that this statement。

 This assignment has occurred。 We'll put this in a critical section。 will。



![](img/19b27f59ecfbe3f6a774612de786eaf9_126.png)

Mark our flag that we've initialized it， and then we call signal。

 So this is very much like the join code that we saw before when we need to make sure that this code over here runs first。

 so over here before we access it， if it's the fact that it hasn't been initialized yet and it is still equal to zero。

 we're going to be we're just going to wait until we wake up when the parent later calls signal and then we could be guaranteed that that variable has been setting and go。



![](img/19b27f59ecfbe3f6a774612de786eaf9_128.png)

Right， so that's how we can do ordering across two threads。

 very similar to the join code that we saw before， yeah。



![](img/19b27f59ecfbe3f6a774612de786eaf9_130.png)

If we don't use condition variables， what's wrong with this one。 Yeah。

 so the problem is that thread 2， it's dereencing M thread。

 It's treating it like it's a valid pointer over here。

 but that pointer isn't being initialized until。This create thread returns。 So most of the time。

 this is going to return very quickly and set this pointer to the right value。 But in some cases。

 it doesn't。 And the thread， too that got started up by create thread gets to run a little bit longer。

 And it dereferences this M thread before it's been set。 So we would have a Seg fault in that case。

 So we need to make sure that that assignment happens before the dereference over in this thread。

 And we can fix that order constraints straight with condition variables。



![](img/19b27f59ecfbe3f6a774612de786eaf9_132.png)

Yes。Yes。Sure， so it could grab this lock first， but then the way condition weight works， Remember。

 it releases the lock。That that's how condition variables work。 And so then the。

Parent thread could grab the lock and do that work。 Yeah。

 so that's the key thing about condition variable weight is that it releases this associated lock so that another thread can come through。

 grab the lock， do the work and call signal。Yep， great， yes。😊，Yes， it would have MTt。

 and it would have to be zero to start with。More questions， yes。我要。And。Well。

 so I think you should never do that because implementations sometimes do these spurious wakeups where sometimes they do just incorrectly wake up you。

 even though they shouldn't have。 But you're right， in this case。

 because there aren't multiple children threads。If the implementation works correctly。

You could have an if statement， but we just generally want to assume you should have a w statement there。

 But you're right in this particular case， just like in the join， it could be an if。

But it's never bad to throw in an extra while loop。 You have one extra tiny little check。

 and you're much more guaranteed correctness there。



![](img/19b27f59ecfbe3f6a774612de786eaf9_134.png)

Alright， okay， so let us look at deadlock。Okay， so deadlock kind of intuitively。

 no progress can be made by multiple threads that are waiting because each of them is waiting for someone them else to do some action that they can't do。

 So we're all kind of just stuck。 So I like a little animation to lighten things up。

 So deadlock happens when you're driving all the time， right， We all know the rules to avoid it。

 But let's say we have two cars and they each get a stop sign。 Can we deadlock here。



![](img/19b27f59ecfbe3f6a774612de786eaf9_136.png)

Only if like the drivers don't communicate， but we usually assume we'll have some policy on the driver to the right gets to go first or something like that。

 right， So even if they arrive simultaneously， we're going to have some ordering and let we'll say B gets to go。

 So we didn't deadlock there。Now， four cars arrive at your intersection。

Are we in deadlock at this point？Well， we'll probably communicate in the drivers if as long as they're human beings and they're not automated driving cars。

 they'll probably get through this， right， because if just a goes first。

 if they communicate with the other drivers and A goes first。 then D can clearly go or see， you know。

 we we can， we can communicate and do this one fine。

 This is the point where we do legitimately have deadlock in the system。 So this is why they say。

 you know， state don't ever pull into the square of your intersection until you see that you can get all the way through。

 because deadlock really can occur here。

![](img/19b27f59ecfbe3f6a774612de786eaf9_138.png)

So we're definitely deadlocked because C is waiting for A。 A is waiting for B。 B is waiting for D。

 And we have this circularity of dependencies。 So， you know。

 how could we get rid of deadlock in this system。

![](img/19b27f59ecfbe3f6a774612de786eaf9_140.png)

So there's a couple of。 we can connect this back to the theory that we're going to see。

 So why is deadlock happening here。 Well， we definitely have like mutual exclusion on the squares of cement。

 Only one car can be like in a place at a time without having an accident。

 We have this hold and weight requirement that we're holding on to the position that we have while we wait for the next one。

 We're not。Able to give that up。 we can't just preempt somebody。 So preempting would be like。

 if we could just tell a to back up， that would also fix this。

 Just take away the resource that a is holding on to。 We wouldn't have deadlock。

 So backing up would solve this problem。 And then we have a problem because of the circular weight。

 If any one of these cars wasn't here。 We wouldn't have deadlock。 Okay。

 so we're gonna apply those same for。

![](img/19b27f59ecfbe3f6a774612de786eaf9_142.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_143.png)

Conditions to code and locks。Okay。So let us look at two threads。And they're each acquiring two locks。

 And so the question is， can deadlock happen with just these two threats？Yes， right。

 here's the definition of deathlock， yes。It is so straightforward。 It is the definition of deadlock。

 Okay Well， it deadlock doesn't have to happen。 It's possible that thread1 runs and grabs lock A and B。

 and then it can do whatever it wants。 The deadlock occurs if thread1 grabs a and thread2 grabs B。

 And then we have a context switch back or you know now we're kind of stuck that thread2 is waiting for a and thread1 is waiting for B。

 So that would be they're holding onto one resource。

 or it's definitely mutual exclusion because they're locks。

 We can't take locks away and we have that circular weight。 So， yes， this is deadlock。

 And so you can draw this to see that there's a circular dependency， you can show each thread。

 you can show what it's currently holding what it's currently waiting for。 And if you have a。😊。



![](img/19b27f59ecfbe3f6a774612de786eaf9_145.png)

嗯。

![](img/19b27f59ecfbe3f6a774612de786eaf9_147.png)

Circle in your graph， then it is deadadlock。Okay， so how would we fix this code？

This one looks pretty straightforward。What was my point to this example。

 we're going to acquire the locks in an order？

![](img/19b27f59ecfbe3f6a774612de786eaf9_149.png)

So in this case， we are not going to have any circularity in our dependencies because if thread A。



![](img/19b27f59ecfbe3f6a774612de786eaf9_151.png)

Holds threadhread 1 holds lock A。 Thread 2 needs to get a。And it's not holding on to B。

 So thread1 wants B， that's fine。 So we don't have any circularity if we draw that。



![](img/19b27f59ecfbe3f6a774612de786eaf9_153.png)

All right， so here's a more interesting example for you。 I have to make it。

 So it's not the classic definition of deadlock。 So the question is。

 can we have deadlock if you wrote this code， This is some library you wrote。

 It's calculating if there's an intersection across two sets and you're trying to be good and grabbing a lock on each sets so that nobody can modify the contents of those set sets while we're looking at this intersection。

😊，Because that would certainly change our results if someone was deleting or adding elements。

 And so it's not too important what it's doing within that new text。 You know。

 it's looking at each of the elements that are in S1。 If that element is also in S 2。

 then it adds that element that's in both to some。啊。Pool that's going to track that for us。

 And then we're done with our critical section。 So can we have deadlock with this code。

So it's tricky because this code in isolation looks great。 So you have to think， like。

 we're writing this as a library and someone else can call this code。

And so we have a multithreaded application that's calling this in one of the threads called set intersection over set A and set B in isolation。

 that's great。 But then we have another thread and it decides to do a set intersection of B and A。

 And now we have deadlock where each of them grabs the others lock first and then waits for the other one。



![](img/19b27f59ecfbe3f6a774612de786eaf9_155.png)

![](img/19b27f59ecfbe3f6a774612de786eaf9_156.png)

So this looks like such innocent code。 And then it gets used a little poorly。 And we have deadlock。

So long nights probably finding that problem。

![](img/19b27f59ecfbe3f6a774612de786eaf9_158.png)

Alright， so the point of this is， it's really hard to see that deadlock， even because it's。

It's because of what's happening across those boundaries。

 So how can we fix that the general solution is you grab locks in a certain predefined order。

 so always grab locks from high to low， So grab and you look at just what is the address of that actual lock and grab them in that order。

But you could still have a couple problems。 You could。

 What if someone did a set intersection of the same two sets。

 you would then be trying to grab the muttex stock twice for that set。

 So you do have to actually have some other。YouCner case code。

 making sure that they're not trying to grab the same lock twice and work around that。



![](img/19b27f59ecfbe3f6a774612de786eaf9_160.png)

Okay。So that's one problem。 So that one。We。

![](img/19b27f59ecfbe3f6a774612de786eaf9_162.png)

Made sure。Okay， great。 so that's just kind of an example。

 Let's now remove each of those four criteria。 So if we can get rid of the mutual exclusion problem。

 then we will not have deadlock。So our previous examples all used locks。😊。

Lots of people like to write highly concurrent code that's called lockfree or weightfree。

 where instead of using locks， we're going to use those atomic hardware primitives like compare and swap and test and set and figure out how to use those in more interesting ways to get our concurrent code working。

 so let's go back to that compare and swap hardware primitive that we talked about before where you pass in some address and if the value of the address is equal to some expected value。

 then you set it equal to the new one but if it's not， you don't do any changes。

 and this is implemented in hardware and it's guaranteed to be atomic and if we have this is a primitive。

 it's set of locks， we won't have deadlocks。

![](img/19b27f59ecfbe3f6a774612de786eaf9_164.png)

Okay， so。Let us figure out。So this is the classic problem using locks for how to do an ad atomically to some global。

A variableable。Or we can use our compare and swap instruction and do an ad。

And that we can run multiple ads concurrently， and we will be guaranteed to。Increment。

The value by amount， atically。Even if it's storing things in registers。 So how would we do that。

 What do we need to set into this field here that I've covered up。

 So I'll give you a minute to talk about that。 And I'll try to write something on the board to make that clearer。

Okay， so what are we doing here。

![](img/19b27f59ecfbe3f6a774612de786eaf9_166.png)

Were， we want to be able to add amount to the value that's stored at that address。

 And so what we're going to do is we're going to remember what was the old value that was stored in this address。



![](img/19b27f59ecfbe3f6a774612de786eaf9_168.png)

And then as long as someone else doesn't race in and change that value。

 we are going to be able to update that to a new value， old plus amount。

So how do we figure out if someone has。嗯。Change this。

We basically want value to still be equal to the old value。

So as long as when we do this instruction here， we see that value is what we is still equal to what we remembered it。

 as then we can increment it to the new value and be done。



![](img/19b27f59ecfbe3f6a774612de786eaf9_170.png)

So the way compare and swap works is if Val got set to some new value。

 So let's say v used to be equal to 3。 and we wanted to add you know，2 to it。But then so we remember。

That's。Old is equal to three。But then someone else comes through and we see that Val is now equal to 10。

Then this instruction won't store old plus amount in Val。And so then this condition will be true。

 we'll loop through again。 We'll now remember that old is equal to 10。And now。

 if no other thread races through and changes Valel again。

 then we will autoically update Val to be equal to the desired 12。So basically。

 we need to remember what we thought value was。 Figure out what we wanted to be based upon that。

 And then as long as no other thread raced in and was able to change the value at Val。

 we'll be able to store our new one。 But if anyone else did， we loop through again and keep trying。

Yeah。Yeah， so the way compare and swap works is just it returns true or false。

 depending upon if Val equals old。 So I just don't want to get my true and false reversed here。

 I think it， it returns。嗯。True， if value is equal to gold。

And just the way that instruction works is it returns false if valve is not equal to old。

And so we can use that。 And then it only does that replacement of vow with this value。

 with a new value， If it was equal to the expected value。



![](img/19b27f59ecfbe3f6a774612de786eaf9_172.png)

So we're able to kind of build up these lock free operations that just look to make sure is the value really what you expected to be。

 Nobody changed it since you did your computations based upon that。

 And so you know that the computations you did based upon the old value。

 they're still relevant because nobody else has changed it since then。😊，So。

What's the problem with this， though， You don't have deadlock。

But we have something that's called live lock， that it could still be the case that you have two threads that are getting very unlucky in each of。

 Well you could just have some other threads that are。Constantly changing this。

 And we just keep seeing that。The value is not what we expect it to。

 And we keep failing and trying again and again。 So it's not deadlock。

 but it's live luck where you're starving out a thread。That doesn't get what it wants。

 So usually what people do for that type of thing is they'll do something like exponential back off。

 where instead of trying so quickly over and over again and failing。

 it's better if you just wait a little bit。 Let some other threads get some work done rather than contending with them constantly。



![](img/19b27f59ecfbe3f6a774612de786eaf9_174.png)

Okay， so people do these weightfr or lockfr algorithms in all sorts of places。

 So you can also use that same idea to do inserts of elements into a linked list。

 So you'll remember before we needed to add elements to a linked list。

 we put adding the elements to the front of the list inside a critical section with a lock。



![](img/19b27f59ecfbe3f6a774612de786eaf9_176.png)

And we saw that we needed to put the lock at those exact points that we didn't need to make the lock do the stuff that's just local。

 like setting the value or doing the mallic。 But this is where we needed the lock。

 We saw that back on the first lecture on locks。You can also implement them using this compare and swap。

But I think I'm going to， I'll start the next lecture on this so that you will all have a lot of energy for understanding this one example。

 We'll finish this up， and then we'll start reviewing a bit for the exam and kind of finishing up concurrency and making sure you can do some concrete examples there。

All right， so I will see you all next week and we will continue talking about Comp and swap。



![](img/19b27f59ecfbe3f6a774612de786eaf9_178.png)