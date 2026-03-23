# 鲁汶理工学院【中英⚡高级编程语言概念｜LINFO1131, Advanced programming language concepts】 p38 P38 FO1131 Lecture 13 (2022) -BV1UDffBbEBZ_p38-

![](img/72a5b0b4bb394ddc5d82cbef83ca4b3a_0.png)

不是。

![](img/72a5b0b4bb394ddc5d82cbef83ca4b3a_2.png)

Which is a form of shared state concurrency。Before we start a few seconds。

Of respect for the Ukrainians who are fighting for their freedom and for our freedom。Okay。

 today I'm going to talk about。An extension of locks， monitors。

 and monitors are used when we want threads to collaborate， to work together。start。

 I can use some intuition， then I can view the semantics。Monitors have three operations， wait。

 notify， notify all。Then I'll show you an example， a bounded buffer。

 so again we go to the bounded buffer， this one is not declarative。

 you can call it for multiple threads non interministically。

I show you how to implement it with the monitor。And I also show you a small variation。

 a buggy version， and it's really interesting to see why this buggy version is buggy to show you why monitors are a little bit tricky。

 okay？And after that， this will teach us a programming pattern。Mometertorters。

 you have to use them in certain ways to make sure they're correct， because of。

The problems of the interleavings， and this is the most useful pattern for monitors。

I showed you a bookConcurrent Programming and Ja by D Leah。

 which is all about programming with monitors and has showed you many other kinds of possibilities。

 but by far the most useful pattern is this one when I'm going to show you。

And then I will end by showing show you how the monitors are implemented。This is。

Starting with our reentrrant。Marock。We go further， we separate the entry and the exit。

 that cause a get release lock， I add a Q， this is for the weight set of the monitor。

And then I show you the code。And I'll explain in a bit how it works。But I won't prove no's correct。

确情。Okay， definition of monitors。So a monitor is a lock。Okay， it's lot with extra operations。

And the used is when you have data abstraction， a buffer to database， whatever。

 and you have multiple threads accessing it。And somehow they have to coordinate these threads it's like you put an element in a queue and you can only take an element out when there's an element in and so Locks are not enough。

Okay if you just have locks， you can do it so here's an example。

 let's say if we have a bounded buffer， okay it has a five spaces inside。

 you can put five elements and take five elements out and you could protect that with the lock。Okay。

 fine。And many threaten to connect it。But that's not going to work。

What happens if a thread wants to put an element in the buffer and the buffer is full？As five。

 all five slots are full。Well， the lock is not going to solve that because sure you get in。

 the lock is just guaranteeing that the buffer code is running only on one thread at a time。

But we need something more if you want to put an element in the buffer and the buffer is full。

You can't do it， you cannot do it， and usually well you could make an error an exception。

 but that's not really how you use bounded buffers。What you want to do is wait。

Wait until another thread takes an element out， okay。

And then the threat that's once to put the animal in can go on。

 so you see there's like a coordination between the two threads。And in the other direction too。

 let's say if the thread wants to take an element out， remove an element， and the buffer is empty。

Well， you could raise an exception， but that's not。The way buffers are supposed to be used。

 that's a normal up thing for a buffer。 It's not exceptional。 What you have to do is wait。

Until another thread puts on in。So you see， you have threads putting elements in and threads taking elements out。

And they coordinate， sometimes they have to wait。 So we say the friends are coordinating。Okay。

 so you cannot do that with just locks because locks will only manage the。The atomic execution。

 they will not handle the weighting if the buffer is full。Okay， so you need something more。

So monitors is the thing。And they were introduced or invented by Pebra Han in 1972。

 15 years old already。And they were essentially turned into the modern for by Tony Goer。

Both of these are famous computer scientists in 1974， so this is long time ago。So they're old things。

 it seems a lot of things happened around this time？

Multti agentent programming was also invented around this time。

Functional programming was also invented throughout this time。

The Terministic daga flow was also invented around this time。

 so around 10 years around 1970 was a really interesting time。For concepts in computer science。

 some of those concepts， they are good and they survive， and they are the ones we need。

Mulultti agentent deterministic data fo， some of them are not the right ones。

And monitor is kind of one that's not the right one。We know that， but it's still used a lot。Today。

 because many very popular languages use it， for example， Java， like in the book。

 concurrent programminging and Java， and if you want to do reliable programming。

The same kind of reliability as airline， it's much harder to do that。Each which you can see。

 if you look how they do it in the look。But it's still widely used。

 but today people are going away from mind。Okay， but still I have to show them to you and I will explain exactly how they work。

Okay， so monitor is a lock。But it has two extra operations called weight。And notify。

And it has internally an extra data structure called a weight set。

So that's basically how it extends the lock， okay， so awaits set is a set of suspended threads so the monitor can force threads to wait to suspend。

And it can wake them up and it can put those suspended threads while they're waiting in this data structure。

 so this is an interesting data structure because what it contains is threats， okay。

 suspended threads。And the late set is managed using wait and notify operations Okay。

 so wait and notify are the way that the threads kind of signal talk to each other okay one important thing is that。

It's still a walk。And wait to notify， you have to do them inside the box。

 these are operations that you do when you're inside the log and not outside so always the way the notify are done inside。

Very important， okay。Okay， so how does it work？Okay， well， intuitively。The weight。

Puts a thread in the website。Okay，When the thread calls weight。

 it is suspended and put in the weight set and then the lock is released， so it leaves the loga。

 when it's in the weight set， otherwise it would be dead loga。

 it releases the lock to another thread and takes the lock。

So that's the way goes into the way it set。And notify。When a thread calls notify， it will wake up。

One of the threads in the way said， anyone， okay， but the thread that's calling notified just keeps going。

But it wakes up one of the threads in。The way its it。And that thread that's woken up。Of course。

 what does a threadread do when it's broken up， It starts running and it tries to get to luck again。

 Okay， so the weight。Is executing somewhere inside the lock。And when the thread is waiting。

 it's in the weight set and when it wakes up， it tries to keep going where it stopped。

 so it tries to get the lock again， of course the place where it was。

So that's basically how it works。诶。Let me make it very precise now。

 so I'm going to give you the Java semantics。Because this one is simple， it's also very popular。

 there's many variations of this， okay， but the Java semantics is a nice one。

 so I will give it to you。Let me draw some pictures。别人。So here I have a thread executing。

 so time goes down。So it's executing and it gets the law。Okay， it keeps going。Eventually。

 it does wait。Well， it then releases the lock。And it goes into the weightet。Okay。

 and it's sitting there。And。That's what happens then if then T2， another thread。

 so the lock is released。This one gets the lot。谁？And that thanks it doesn't notify。

Okay and then it keeps going and eventually it releases along。Okay， so what happens。

 this notify will wake up a thread in the way set。That thread will get the lock again。

 try to get the lock again。And when it succeeds， it executes at the point the weight stops。

And it keeps going。Until it releases。So you see how it works？This looks quite simple。But actually。

 if you look exactly what happens， it's a little bit subtle。 So let's say T1 is in the way set。Okay。

T2 does notify。Okay， like there。T1 then leaves the way it sit。Okay， it tries to get the locked。

But it won't get it right away， Why not， I know it won't get it because T2 is still inside， okay。

 T2 is still inside。And then T2 eventually releases the lot。Okay。And then the lock is free。

 and now T1 can get the lock。So you see how it works， okay？Now there's an interesting point here。

 T1 getss the luck。But after T2 releases the lock。It's not guaranteed that T1。

 maybe there's another threat T3 that tries to get the lockcut。Okay， T1 gets the lock， but in fact。

 when T2 wakes up T1。And T1 tries to get the log。 It's not guaranteed that T1 will get to log。

 Some thread。Maybe T33， when this log is released and this log is released here。

 maybe T3 gets the log， but if there's no T3， then it will be t1 so this shows you the little dense that goes on。

Between the。The threats and the no function and the weight， okay？Okay， let me recapitulate。

 this is now the Java themans， so when you start programming the Java it will be very familiar。

You have actually three operations。Wait， notify， and a third one。A third one is total notice by all。

 showing explain。Which is just an little small extension of non fire。

 So the weight will do three operations in order。 It suspends the current thread。

At the place there when you do the weight， it puts the thread in the way it set。

And then it releases the lock。So the thread is in the ways it suspended and the lock is free， okay？

And when the thread is woken up later removed from the weight set and woken up。

 it tries to get the locked again and it will keep running exactly at the sit part where it was waiting okay so the weight is just like a temporary。

Stop there。that's wait。Notify。If the weightside is none empty D， it takes an arbitrary thread。

 maybe there's more than one then the weightside removes it and wakes it up and that thread。

Then resumes execution as I show in the diagram， okay。

 that threat T will try to get the lock like any other threat。

Notice tea will always suspend again briefly。Here are the T is the T1 here。It tries to get the lock。

 but since the T2， which did to notify， is still in。

The lock T1 will always suspend for a short time for sure， usually this isn't near the end。

 so usually the notify is done very close to the release， so T1 does not have to suspend very much。

So that can seem kind of complicated and it is kind of complicated， but we can use it to write。

To make programs with multiple threats okay。So。Let me show you another numbers like all。

Notify wakes up one of the threads。In the way it's sit， but that's kind of a problem sometimes。

 so this is semantically very clean， okay， one thread。

But maybe there's multiple threads and that's not the right one somehow for the application。

So usually the notify is not used， it's defined because of reasons of simplicity。

 but usually there's another operation called notify all。So basically it's very simple。

 you notify for all the friends in the wait Center。You wait for them all。

So if there's 100 threads in there。They're all woken up and they all try to get the laugh。

 okay you can see it's kind of messy， but that is the thing you will make if you do that。

 you're guaranteed that the thread that you want to adapt doubt is woken up。

So the white set becomes empty after that。It's indeed all the threats are resumed。

 they all try to get to up， of course only one is going to get it， the others will keep waiting。

So once they' ready， get the lot。And if that's not the one you want。

 let's say you're doing puts in a buffer。And the buffer is full。 you have 100 puts。In the way set。

 all way in。And one， get。Okay。So arrives， so the get does notify。100 puts them woke up。And。呃。

They all try to get to luck， the first one， the lucky one that gets luck。Will do。

So the get has emptied the slta that first put will be able to put an element and 199 other threads will just go to sleep again。

 so you see it's kind of overhead to do that。So this is called contention。

Where all the threads are kind of fighting， they're not really fighting。

 but one of them is lucky and the others are not lucky， okay。

 so this can be a problem if you have lots of threats。And but usually there's not that many。

 hopefully， so it's not really a problem， it' only small percentage at the time。But you can fix it。

 so there's extensions of monitors where you can have multiple weightss。For example。

 in the about buffer you you click and yes。But in Java， every synchronized company has only one one。

Well， you could have two。You can have a weight set of the threads that are trying to do a put another weight set of the threads trying to do against。

And some versions of monitors have multiple way sets， but that's not how Java does it。

 and you could simulate that in Java by having multiple synchronized objects， okay。

But that it starts getting more complicated， so that's all that to avoid contention。ok。

 so you see how。Theoretically how it works。Okay， now let's write notification with that。

What I want to show you now is the our good old founded buffer。

This time it's not declarative bond and buffer。 So remember we did already a declarative bond buffer where。

There's always one thread putting elements in and another thread taking them out。

 so that's like a pipeliner as a clarity bounded buffer is what like a Unix pipeline。

 which is always getting from one place。And going to one place。

 but you could have a more general bound buffer where multiple threads are putting elements in and maybe multiple elements or threads are taking elements out okay so this is the more general one。

So this one will be non determinative， if you have two threads， no input。

Then the scheduler decides who does it first，So the bone bufferer has a size。

 a maximum number of elements like 10 here。And it has two operations。P and yet。

It also has a creation and operation。So， we'll have a。We'll make it like an object。

 so a buffer will be like the class， and B is the buffer object。

So this B new buffer in it and creates a buffer of size n， and you have two operations， put X。

And get X。When you call the put X， it just puts X in the buffer， if the buffer is full。

 this operation will wait。It will wait until， until there's room in the buffer。

 and the other operation is get。And this one will remove the element from the buffer and bind it to eggs。

And if the buffer is empty， it waits again okay so it's very intuitive until there's at least one element。

 so these can be done by multiple threads， so you see there's kind of interaction between the threads so the monitors is going to be inside there and it's going to make sure that everything works right。

Okay， so that's kind of the specification， so we'll implement it like this。

We'll have an array of sized n， but organized like a ring okay， from0 to n minus1。

 but if you keep going past n minus1， you go back to zero， so there's a wraparound。

And we have two pointers， two indices， first and last。The first points to the first element。

And then we keep going and last points to the first empty slot。After the last element， okay。So here。

 for example， ABCD is in the buffer and here's a free slot the last is pointing to。

To remove an element， you take the element that's under first and then you increment first。

 so the first moves like this。To add an element， you put the element here at the right neck where the last is pointing to and then your increment last。

 so you see first and the last they're going to be like going round and round。

If the index goes outside of the range。Zero n minus1， it is replaced by modlo operation。

The number of elements。Is going to be last minus first， so here's4。

Last minus first will always be the number of elements。Notice there's a problem。

 if you have zero elements， then less and first are pointing to the same place。Okay。

 if you have any governments。Okay， then again。They're pointing to the same place。

 so you have to keep track of the number of elements。And if it's empty。If。

The puts for the get would make the buffer。Negative size are bigger than N。

Then the operation is blocked， okay？Sorry， this has to be anythingpath if you not then notice one。可以。

So that's how it works， you have these two numbers going round and round。

And you have also the number of elements in the buffer。ok。So here's the code。

So this is the Oz classification not， so we used it already before。

 I also find an array as we did already before with Flavavivis Josephus。

 so I'm not going to really explain。What happened， so we had local attributes， Buff first， last。

 and an I， so Buff is an array from  zero to and minus one。

First and last are the two indices and is a constant， which is the number of。Elements。

And I is how many elements are in the buffer， okay， how many elements are actually in。

 and we have two methods put。单表。Okay， so here's how it works。 then， very simple。

To put an element in the buffer。You put it in the so the do operational will index the array。

 the you read the last， So this is index， so the buffer。That last gets x。

 so that means you put yellow in， you increment last。来年。So the last is moving around like that。

And you just add one the size， okay？Now， you can do this if I is less than n。

So you have to wait until I is less than n now the monitor is going to arrange for that so so far I want to show you this is just the operation。

And the get is doing the opposite。Again， you have to wait， you wait until I is greater than zero。

 so the monitor is going to do that。You remove an element， so the what is underneath the first。

 so x is bound to。The index underneath the first， you implementcrement the first and I gets I minus1。

Pty。Stand right another trick is you have to use monitors because I have multiple stateful operations here。

 I have two assignments， I have a bunch of reads， so I have to put this inside a lock。

You totally need luck here， you have multiple stateful operations。

 you want to make a big atomic action there and there。That's reason world。ok。So。

How do we do that now we' let had the monitor。So we define a bunch of abstraction。

So this is how we will define it in the US code。You have to create。

 you can create instances of monitors because each monitor has its own lock and has its own weight setcycl locks。

 you create them when you need them， so the buffer needs a monitor。

We define an operation called New Monit， which creates M which is a monitor。

An M is a record and it has。One， two， three， four operations， so that you know the lock， it's a lock。

 so you have well just like before the lock。But you have also these four extra operations， wait。

 notify and notify all。Okay， so it's a record with four elements。

The lock is like before it's a reenting the lock。And done lock， and you have here the statement。

 okay protecting the statement with the lock， so that's just a regular old reenterrant block。

Then you have the end that weight， end up notify， end up notify all。Okay， so these three operations。

Okay， have to be done inside the market。It's an error to do them outside， okay。

 you have to do them inside。Okay so that's very nice。 Now let's write some code here。Okay。

Sos this is the color that I'm going to write to explain to how it works。

 it's a little bit tricky and I'll explain that。So I add another attribute M。

 I create the monitor here M。And now the weight， the Co， I add the red part here。So first of all。

 I have the luck。So procedure， this is all a procedure。With a statement that I'm protecting him。

So in the red part plus this， it's all protected。And now I have to wait until I is less than N。

So how do I do that， if I is bigger， braver than our people to end， then I wait。

and then the thread will wake here。Eventually， some other thread will do get。

And it will cause this one to wake up right here。And it will continue。Okay， so what we do。

 we try again。 And the way to try again is to do another。Put X。 We try again to do put X。

 So this is the correct way to do it。 When you wait， you basically call， put again， you try again。ok。

Now， if I is less than n。Then then you're good， then there's root in the buffer and you do this。

And you do notify all at the very end。This will tell the other thread。To wake up。

 so you might have other friends。Trying to do guests。Or good。Of course you're not helping them。

But the guests will be very happy。They will wake up and one of them will succeed。

The others will go back to sleep， okay？So one of them will succeed。

So the way the get has a similar code， it waits until I is greater than zero。一て。Let me now run this。



![](img/72a5b0b4bb394ddc5d82cbef83ca4b3a_4.png)

你。It use the。Those are systems here have two files。On the left， I have the Mon implementation。

There's a queue here。hi全。7。So they问题。还有人。I'll explain it later， but let me just run it know。

And then I have the actual monitor implementation。It's very nice come belt heres a new monitor。诶。是好。

我意。monitor。可别。李你军。そる罪。So that's the monitor。Here's the bone of buffer。And the spectrum else。

So this this is aet object it's an an active object。行。嗯。이준。Now let's run the。The buffer。

 the buffer is there now。Here it is。我不。Let me just copy this code。Do some buffer for operations。嗯。

So here's now let's pray the buffer。New bathroom and it three。诶。So the buffer exists。

Now this quick pay in the buffer。佢哋。And I can browse， I can do a get。And don't get eggs。And browse。

 and then browse it。This will show up a， wow， amazing。There you see the A。So that's book。

 I mean the board in the course。Okay， let's now do a whole bunch of puts。

 so the buffer has size three。I can do ABC。And now I try to do a put D。

But let me just to show how it's running， and so it's going to wait here。

It's going to try to put a fourth element， but it's going to wait here and when it actually succeeds。

 it will do end for them。So now it has put ABC。It is displayed trifor。

 so this is actually when I feed this， it creates a thread。And in that thread。

 I have this sequence of instructions。And the three puts are to work here at ABC。

 but the D is going too late。Okay， so what happens now？If I do it again。So if I do what gets to you。

What's going to be displayed。你 tell明。If I do this。What's going to be displayed and？呃。

So it's a buffer。 So the first element you put in is the first one that comes out。

 So what is this split， sorry。It's going to stay and forth and what else？B。我系李系。Because we didn't。

 okay， the first A。So we put in another area， so we a， okay， so that's a good。

 so you'll have A and fourth。In what order will they be displayed， the A and the and forth？

So here I have a thread doing get X， browse X， so this will display A。

 and then this one will actually continue and do n forth in what order will the end forth and the A be displayed。

我是。So they're running in separate depends。Sorry it depends exactly， it depends on the scheduler。

Probably you can say， you can probably estimate what is the one that's going to happen？The most。

Likely， but both solutions are possible， so if I run this。People say A and fourth。Okay。

And I can do yellow。F another room。Be after forget。I do another one。See I forget。

 if I do another one now， what's going to happen？If now I've displayed ABC， if I do this again。

 but it's going to be displayed。I didn对 sir。If I do of now and this now。

 what am I going to display for simple question of？do you have to forget？D after get。 Yeah。

 I think that's right。 D after get。They have to get。And if I run this again， now once more。

 what's going to be displayed？Nothing， nothing that is I think correct。Nothing is sorry。

 nothing is displayed here， but I ran this， and now let me do put F。

Now what will happen if I put that。So here， this get this is suspended enough。So this thread here。

 it's suspended hero。So when I do put F， what's going to happen？And it's going to get F out exactly。

 so it's going to display F and F get。诶。After to。It's nice， Sir。It's a beautiful concurrent program。

 right？O。So， that's good。Let me go back to the studies。Because， oh sorry。

 before going back to the slides， let me show you the code for。For the get。

 which I didn't show you before。I didn't show to you on the slider。

 so this is the code the code for the get， I have a lock。This is the work statement that's protected。

If I equals 0， so the buffers and T， then weight。And I try again。 Okay， when the when it comes back。

Else， I removed one element and I to notify that， so it's very similar to the pro。Okay。

So there you see all the color。But now I want to do a little bit more。

I want to do little bit I want to， so this works。But maybe you don't really maybe or maybe you do understand exactly why this one works because I'm going to show you a variation of that。

Here's a variation。Which is buggy。Okay， so here's the variation。

 I have another version of the block here。If I is greater than equal， so the buffer is full away。

But when I do notify it， this one wakes up and it continues。So this is么病。So the question for you is。

Tell me， explain why it's bug， find a scenario。That shows me why it's funny。

 so the difference just to be very clear， the difference between the preceediving one。

 when the weight returns， it tries again to do a put。Doesn't mean you go here。

 tries again to build point， and that is correct。This version。When the weight returns。

It immediately does the buffer operations here and then notify。So this is buggy。Why is it个。Yeah。

 because Fred is our think the。Can enter at the same time。

So where exactly is multiple threads are waiting in the if condition？Wait， if condition doesn't wait。

对 there there is M。Okay， I think you're on your own track。

 but you have to be very precise if this thread is wakes up。

 it tries to get to locked that's the first thing the thread when you move it where the weight set。

 it tries to get to locked。And wouldn it bit lucky it does this？So why is that wrong？

Because you keep very fresh and get to the。两个年四低。Well， they can be waiting for the luck。

 they can't get the luck at the same time，precise I think you understand the problem。

 but you have to be very precise in explaining， so when this one wakes up。It tries to get the luck。

But maybe there are already other threads trying to get the lock。

So maybe there's another put operation。This is notified Allla。

 another put operation that wants to get the lock， so when this one waits up。

 it tries to get the lock， but there might be other threads trying to get the lock。

 and if another thread succeeds。And getting it before this one。

 that other thread will do a put and the buffer will be full again。

 and then this one will get the lock and it will do this and and buffer is fulls， that's buggy。ok。

So the problem is that when you wake up。By between the time you wake up and you get to luck。

Other threads might get in， it's not atomic。To here and here， it's not atomic。

 the other threads might get in。 And then when you reach here， the condition。

That the buffer is not full， is not true anymore。So you can't do like that， okay？

So that's important to understand that，Okay， in this one。So this one look what happens here。

 if the buffer， so I'm， I go here， I'm in the lock， I make the test。Now， if I is less than 10。

I do the else part。And then I start executing this， but I'm in the lock， so if I is less than n。

 it will still be less than n here， no of the thread can get in between because I'm already in the lock。

That means before doing the operations， I always have to do the test again。

 but if I do awake and I wake up。And then I get log again， and then I do， I have to do a put X。

 This put X will do again the test。You have to do the test again。

Because another thread might get in before you when you wake up， okay。

 so that means you can only do the put operation directly after this test fails。ok。

Because then you're guaranteed no other thread will get in。You see that。

So she's a little bit simple啊。So you have to be there， it has to be very， very clear。

Why this one does not work and you should be able to make a precise scenario with threats and scheduler choices wake sleep where this thing turns into a bug。

 where this thing will try to do a put when the buffer is already full which is not。

 which is totally incorrect？It will do it， in fact。

 it will do an exception because the aus will not have so no eye will be too big。

 no you will overrite one of the elements of the buffer if you do that though。可以。

So that's just an example of。Trickiness with the。With the monitors， okay。Okay。

 let me make a break now。And then we'll talk about programming patterns。

 and I'll also explain how they could。The monitors are implemented，Continue now。Before the break。

 we saw how to do mountain buffer。Monitorors and how we have to be very clear。

That the condition is still true when you do the code。

Which means that you have to try the condition to test it again when you're inside the lock。 Okay。

 So now I want to show you a few things。 First， a programming pattern。To use monitors。

 so if you see this code here。This is a way that is correct。

 this will you work for any kind of abstraction so we can kind of turn that into a programming pattern。

And there's two ways that I can show the pattern， one of them is using a wire loop。

And the other one which is equivalent is using recursion， okay。

 tailor recursion and wire loops are equivalent， as you know， they's just syntactic。Variation。

So here's the pattern using a wild loop。And I'm going to have a little bit of syntactic sugar。

 so I have a lock here， this is the monitor lock， while not expression do wait。

 it caning if it has to be a while。Statement。Because when you wake here， when this one wakes up。

It's inside the while loop and before executing statement。

 it will check the truth of the expression again， okay？

That means this expression is guaranteed to be checked when I'm in the log。

 so this has to be a Y loop and not an if okay， so why not expression do wait。

 then the statement that's inside and then the notify al at the end， okay。

And this is equivalent to the tailcursive one， if not expression， then wait。Self and I try again。

 okay， so this is basically a recursive call to the method。

So this is equivalent to the to the wildlife。Okay， and you know， ours does not have wire loops。

 It's very interesting。 The one which is no wire loops。

 So the I showed you the solution using recursion， and it's very logical。

 You have to when you wake up， you have to try again。The full method， this one will try again。

 including。The test since it's reent block， when you gave it to the block here。

This one will already be in them， so you're doing this test。Again。

 before you do the statement in the law， okay？So the point is before doing the statement。

You have to do the test of the expression， and it has to be in the same block， no gap。

So the pattern would guarantee that。And that means if you use the weight and the notify in this way or this way。

 you're guaranteed that it will be correct。Okay。You see that。So that's the simple pattern。

 there's more complicated ways of using monitors， this is in you can see that there's many books explaining that。

But。I don't recommend writing applications that way， if you can avoid it。Unfortunately。

 people might ask you to extend or debug an existing application。So。

So that's why I am explaining lot one。Okay， let me now explain how the monitors are implemented。

This is an extension again， remember we went from the simple lock to the reentrant block。

And now we'll go to the monitor， which extends again the concept of log。

 and next week we'll do another extension we'll go from Gr and block to transaction。

Where you can do a board and do it。So that's another extension。But number show monitors。

And there's basically two extensions， so it's important to understand the implementation。

 I will explain as much as far as I can， the implementation。

 and it's important for you to understand really how it works。The first thing is the lock。

 it's still reentrant， but it's called a get release lock。Because going in and going out。

Will now be separate operations。In the previous one， you entered。The critical section。

 you do the instruction， and then you leave。And that's one like block of code。

 but now you have a new thing in the weight。You can do weight anytime and in the weight。

 you have to release the lock， go into the weight set。

 and then try to get the lock again so that they're releasing the lock and they' getting the lock。2。

Separate operations now that you can call any time。So we split them out。

 so the lock is kind of separated into a get and a release operation， so I'll show you the code。

 but it's otherwise it's still exactly the same reent lock as we saw before It's just that get and release are separate。

That's the first thing， the second thing is the weight set。

So we need a data structure and I will use a queue to do this。So semantically， this is a set。

 so there's no order。But。Practically， it's good to make a cu because that means that there are threats that are we the longest。

Will be released first。So that adds some fairness， if you would do a stack here。

 then you could have starvationfish。Because if new threads were coming in。

 the old ones would never be maybe never be woke up， okay？So that Q ensures fairris， okay。

 it's not possible for threat to stay forever while other threads are leaving。ok。

And it's very similar to the queue we saw before， it has a couple of extra operations。

 delete all because of the notify。Okay， also a science operation and a non blocking delete。

Which is important for the not self for notify。 So this one for notify all this one for notify。 Okay。

 so let me show you the get release log。So remember we had two things getting in and doing the instruction and leaving。

But now we separate them。We have pitlock and release lock。The get log is very similar to before。

 so first of all we have the exchange， the weight。And we have also this current thread for the reentrancy。

Okay， and this part is I'm getting in， I actually am doing the work to enter the log and so this one returns true。

 so get log is a function， it returns true， if it actually had to do work to get in。

 if it's already in。Then it returns false， okay， because once you're in its reentance。

 if you do a getlog again， you don't have to do any of this， so then in that case it returns false。

And then you do the operations， and then at the end you do release log。

 so the release log is the leaving the critical section， basically you have to pass the token。

But the token is this variable。So how do you pass this variable nu between these two functions？

On this variable new here well， but because the release log can be called anywhere。

 it's called the weight which can be anywhere in the code of the function of the procedure in the middle。

 sorry。You can't just put a variable there。So what we do is we use another cell for that。Okay。

 so this blue variable， the variable is stored in a cell talking。And then here。I get the variable。

 so this is the variable nu that corresponds to the getlock， and I bind it to unit。

 so this is passing the token to the next guy because the next guy is waiting on the new。

K whenever you do it change。Each thread that's weighting。

 gets a new variable that it weights on and when you bind that variable。

To unit unit was just a constant then。The threat can continue， so this is passing the token。

 so we need an extra thread， an extra cell for this，Okay， see that， see how it works。

So basically that's it， we need to separate those two。And then I'll show you how it works。

 I'll show you that in a minute how the weight is implemented。So， the queue。

It's very similar to the we saw before。 So I'm using the queue with a difference list， but。

And it actually has its own little lock here， which is kind of funny。Has its own luck。

 which is a standard entrance block。Probably you could rewrite it to not need that。

 but it's nice to put that here， so we have insert and delete， which are the same as before。

But then we have three new functions。The size， the delete hole and the delete non block English。

So the delete哦。Basically， it accesses the Q， the difference list S， and it makes the Q empty。

 so delete all x is the way its center， so 0 x x is an empty cube。

 and then it binds E to n and S will then be the fullest study。

So the difference list to make it a standard list， you have to bind the ends to know。So。

 this returns。哦子。Fends。We'll see in a minute how threads are stored in queue。

And the delete non blocking， this one is used for notify。Okay。

 so this also returns a list of threads。But only one， so if the size is greater than zero。

It will return a list with only one deleted elephantton。

So this is a delete here will return a single thread。

It's actually an unboundary bullet we' return that in a list， so if the size is greater than zero。

 otherwise it's n so that the notify， if there's no thread in the way it set。

 the notify does nothing happen。Okay。So the queue has then this。A couple of extra operations。

And then the monitor code itself looks like this。So basically I have a queue and I have a get release lock。

And the lock， this is the lock like before， if get， then tryP finally release， Okay。

 this is exactly the。Bri had loved before， if this returns true。If this function returns true。

 then then I did work to get in， okay？诶。And that means I have to do a release to get out if this function returns false。

Then I'm already in so I can execute good P right away， and then you have wait。

 notify and notify all。So the weight is a very interesting one。Okay， so the weight has to。

Suspend the thread， nice to release the buck。Suspend the thread。And then when it's weight up。

 try to get the lock again。So how do I suspend put a suspended thread inside？Inside a Q， well。

 I have a variable X。And this one will cause the threat to suspend。 so I define an un variable。

 which I put in the cu。I release the lockrk here。Then I do away X， so this will suspend。Okay。

 this will suspend until the notify， which we'll see later。And then when it continues。

 so when it wakes up， this weight will continue。And then it will do the get， okay。So here the get。

 I don't care what the value is for the get。So， that's1 I don't care。So there's nothing。

 I don't care whether it's true or false because I know it's going to be false actually。

It because I'm in， because the weight is always done inside the locker。Or no。Then no。

 that's not true， sorry， skip that， I leave the lock。And。

This one may actually do work again to try to get in， okay？And then the notify and the notify all。

So the notify will remove one。T so it's one variable。And if they're it or nothing。

 so if there's a variable， it binds to units， and this causes the weight to start running again on and we see that。

So this comes into start writing。And the notify El does the same thing for all of them。

So L is a list of all the unbound variables， and for x and L， it does x equal unit。

 so all of them will start。我会家佢嘅。ok。Because each of the weight has its own thread。So， that's how。

That's how it works。Okay， so you see， you see that。 And let me show you the。The actual code。嗯。这设计一人。

It's slightly different， but basically the same just very minor differences， so the gap here。

The release log。 So again a second。So for the variable lu。

 the lock is just doing get luck and release lock。The weights will do a release log。W X。

And then I get luck afterwards， so instead doing it in the opposite direction I release and then gets and then the notify and then notify all okay here I'm using for all。

 there's a procedure called for all that executes this。Procedure for all elements of the list。

 So it's small differences， but it's essentially the same component。

 So this is the actual code that runs。 So I'm not hiding anything。ok。

So now we get to the end of what I wanted to say about monitors。So monitors are extending blocks。

 just given a summary， it has a weight set and way to notify operations。

The white set is the set of suspended threads and it's kind of tricky to use because you have to be very careful when you are getting the lock and when the condition is true。

 it happens to be true in the abstraction。So monitors are March program and this use a pattern。

So I showed you the patterns。And why do they use the legacy code？Okay。

 but I don't recommend it for a new code。And next week， we will see transactions。Okay， let me。

 since we're a little bit early， I will show you a small。

Introduction to this and then will stop for today。So that's all I wanted to say about monitors。

I could spend more time。No really want to。Let me just give a very brief introduction to transactions now。

 so now they we finished part of shared state monitors， so you see how they work。

And you see everything， you see the implementation， and everything else is built on top of the a。

But that's all I want to say about monitors， action transactions are much more important than monitors。

 transactions is a very good thing， so I will give you a small introduction to transactions and then we stop early today。

 but I want to already prime your thinking for transactions。Okay， so now we switch。

 now we thought the transactions。So transactions are used for databases。

And so they're using all over the place。诶。They will keep being used， okay？For critical information。

 high performance， scalability and fault tolerance resilience。

 Okay so let me give you just simple motivated example。And then we stop today。So here's the database。

嗯。A large array of cells， basically， so here it's not very big it's only 1000。

But people have millions。And there's a lock。And this database has all the information on your bank account。

And I want to transfer money from one account to the other。

And other clients want to do the same thing。So there's lots of concurrent updates to this。

So how do we implement this， Well it's very easy， we have the lock， so I get the lock。

 I do the transfer， and then I release the lock。So we can use one do to protect the whole array。

It's perfectlyly correct。But it's very slow。Because what if this guy wants to transfer and this guy wants to transfer and this guy and all three of them ones to do it at the same time？

Well， they all have to get the lock， so they have to serialize， so it's very slow。Okay。

 so that's not the way we really implement this。Oh， even though it's correct， it's much too strong。

So the real database， it has one mark per cell。ok。So let's say I want to do a transfer。Okay。

 from one to two。T1 transaction T1， I want to move money from T1 to2。Well， I get those two locks。

And I know that nobody else will touch those two cells and I transfer。Okay。

 and let's say I have another one that does from two to three。Transform money from three to two。

 for example。Again， I have to get to two locks， these two then。Do the transfer。But。Be careful。

 we have concur program here。Okay， what if the updates are done in the wrong order？ok。So呃。

So the example here is when you don't have the locks， but to lock though， if I lock。

 I get the locks one after the other， getting locks is not at。Okay， so I have to be very careful。

If I get this log。And then the other one gets this lock， the T2。

 and then T2 gets this lock and writes and releases， and this one gets the lock and writes。

 I can have overlap and money can disappear。Okay， so I need a clever way。Of managing all these lung。

And that is。What transactions provide？ok。So the condition is。You want， first of all。

 large atomic actions， so every transaction has to be one atomic actions。

The second thing is this is a database。Sttored on a disk， so we add robustness to this and。

The database is stored permanently on the disk。オ。And so how do we ensure that there's no corruption when we write things to the disc？

ok。Well， because this can crash at any time and when we reboot the system。

 the data has to be consistent。Well， you're writing many things on the disc， so how do you do that？

When I do a transaction from two to three， I will write two and I will write three。

 so I'm doing two rights， What if there's opion in the middle。Well。

 the way it's done is that all the rights for a transaction are stored on one place in the disk。

And when it's all done， a single word is written。就 switch。The content from the old to new value。

And the only thing that this has to satisfy is。Single word right must be a time。

 and that is what the hardware sat if there is a crash。Before one word， write。

Then when the system reboots。Use used to get the old value back okay。

 if there is a crash after the one word right， you will when it reboots。

 you will see the new value and you will never see anything else Okay。

 so that is how you can guarantee that it's consistent even if you have。Prash anytime。And finally。

 you can have。A actions， transactions， executing in parallel。ok。And that's where you need to handle。

一啲需要。One more thing。And then we're done for today。Just to get you。In成。Okay。

 let's say you have two transactions。That are updating money。And so they need two cells。ok。

Transaction。T1， it locks。The cell first cell with L1 against the data。And it releases the vt。

 and then it locks T2 against the data and writes the data。

But what if there's a transactions2 that is executing in the middle， it logs t1， C1， C2。

 it does an update of L1， and then this one does an update of M2 where the data is inconsistent。Okay。

 so that means the way you manage the Mars。Has to be very smart。

And today I just give you a little bit of intuition， you need。

 you cannot just manage lu in any old way， you have to do them in a very smart way that it's still atomic。

It's basically what is called serializability that means the transactions are atomic。ok。

So we have to have some kind of a discipline how we manage the locks， for example。

 T1 will get both of its locks， do the work， then release T2， we'll get both of its locks。

 do the work， and then release， okay and if we do this， then you won't see the money disappear。Okay。

Okay， so let me stop there。today， I think we're a little bit early， but that's okay。

 so you have seen monitors， I will put the code for the buffer and the monitor on the bole。

 so please run that code。And make sure youll understand how it's working， okay？

And so that's it for today， so that's all you will understand monitors next week。

 I will present transactions， but I will also give you kind of overview of the whole course and also explain little kinds of things I will expect from you for the exam so well stop up today a little bit early。

