# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p13 -13-Lec07 Screencast_ CPU Scheduling (02_11_20).zh_en -BV1iP2CBaEHr_p13-

Okay， so let's start。 So today's lecture is going to be on processor scheduling。

 This is a little bit out of order， because normally we would。

cover process management first whats the process how does theOS create processes and so on and then we talk about how to schedule them but I wanted to do it a bit out of order because I think the next lab might require you to do something with CPU scheduling so I wanted to get that material out。

First and then we can go into the details of process management in Linux and things of that so today's class there are three things I'll talk about first is what what is processor scheduling what are the goals of scheduling processes the second one is going to be a refresher on CPU scheduling This is actually that that second point is a material from an undergrad OS class so depending on how much you remember or how little you remember we can speed it up or slow it down It's entirely going to be based on what I'm going to ask you some questions and depending on how much I see all of you knowing the material we can decide how much time to spend on it the third part is of course how does Linux do it what does CPU scheduling in Linux look like and we'll see the concepts actually directly translate to nice implementation in Linux so it's no surprises there most Os will do their own thing This one。

Does more of a textbook style model of scheduling， as we will see， right。

 So let's start with the first point， which is。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_1.png)

Goals for processor scheduling。 so this picture essentially shows us the process state transition diagram which we haven't encountered it。

 we'll get back to this when we talk about process management but by and large that figure says when processes start there in a new state and then through their execution cycle the cycle through essentially ready running and wait in a ready state a process is actually ready to execute on the CPU is just waiting for its turn to run on the CPU the run state is actually executing it does any IO it sits in a wait state waiting for that IO to complete so you cycle through these states and eventually you are done executing you go to term okay so that's the thing you want to keep in mind the goal of the CPU scheduler is essentially to decide of all the processes that are in that ready state which one is actually going to execute next and youll see that there is one process if you look carefully right about the running。

there is one process in a single processor machine there can only one process executing at any given time of course in a multi processor system multico system there will be as many executing processes as the number of course at I mean that is the limit on the number of processes executed。

So our goal is to design in a multi program system a CPU scheduler and multi programminggram again only means the ability to run multiple processes concurrently on your system Unii program systems is you can only run one application at a time in addition to the OS multi programgram once is you can run multiple so that is the definition of multipro。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_3.png)

So， now。Let's talk a little bit about how。Scheduling works more broadly and then we will talk about specifically processor scheduling so in any OS and it depends on the flavor of the OS there are two kinds of decision being made one is called long term scheduling and the other is called short term scheduling。

Longter scheduling is looking at how many processes can that system accommodate at any time for concurrent execution and the answer to that is going to depend on things like how much Ram do you have you cannot create unlimited number of processes and expect them to run eventually your system will run out of resources so the goal of the longter scheduler is to police the entry of processes into the system so you will see here that there is essentially a queue newly arriving jobs enter that queue longter in this one part of the longter scheduler here which is called admission scheduler is checking have you run out of resources to admit yet another process in the system if so you are not going to let that process run if not you will basically let it actually become a real process and start executing there is another part of a longter scheduler which you don't see often but it's called the memory scheduler and its goal is maybe there。

maxed out your system resources you want to let another process in the only way you are going to do that is is to take an existing process that is executing temporarily swap it out to disk that is what that memory memory schedulers is doing it swapping entire processes in and out of memory just when you run out of resources okay so the two collectively do longter scheduling decisions which basically decide how many processes are actually in executing actively not necessarily in memory because you could be using virtual memory but how many are active processes in the system。

and then that short term scheduler is the one that you see at the top that is called the CPU scheduler of all the processes that are currently active and ready to run which one gets to execute next。

Okay。So， that is the goal of this and that is what we will call a CPU scheduler we wont actually use the term short term scheduling but we will use the term CPU schedule Okay so what I just said on the previous slide is just summarized here so I am going to just skip this slide。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_5.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_6.png)

so now when does the short term scheduler run okay the the short term scheduler or the CPU scheduler is essentially a core functional function of the OS kernel okay so it is going to get invoked when one of a few different events actually occur those are listed there saying if a process is sorry if a process is switching from running to waiting if a process that is executing blocks the CPU becomes id。

Because the currently executing process is blocked。

 so then you run the CPU schedulealrs saying what next？

Then if there is an interrupt same thing happens okay because the interruptranr is going to run and then once the interruptranr is done you have to say what should I run next should I assume the process that was running should I run another process all of that is going to be decided by the CPU scheduler okay of course if a process is created or terminated you also have to run the CPU scheduler。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_8.png)

So the CPU scheduler is going to run when all of those things happen okay and we will see that there is one more event that can occur that triggers the CPU scheduler but for that we need to define two terms non preemptive and preemptive scheduling nonpreemptive scheduling says once the process starts executing on the CPU you cannot actually preemptic which means that the scheduler cannot say that something else has to run it can run for as long as it wants。

Until it blocks or termants。That's a non preemptive scheduler okay most schedulers you see are not nonpreemptive they actually form in the pre fall in the preemptive category and as the name suggests a preemptive system is one where the CPU scheduler can interrupt that process or the over schedule interrupt that process and so this is off used in the context of you what is called quantum based schedulecheduling whenever a process runs is given a fixed time quant can say that's the amount of time slice you have it can use this entire time slice at that point its preempted and something else gets to run so in preemptive scheduling in addition to those three things that cause the CPU schedule to run theres a fourth event which is quantum expired a quantum expired the scheduler will also run and say what gets to run next。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_10.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_11.png)

Is this clear？都。So now let's talk a little bit about some of these policies So before we do that it's good to understand what process behavior looks like so we can design policies that are designed for various kinds of process behaviors by and large when you run a process on your machine it will fall into one of two category it either be CPU intensive or IO intensive at any given instant or the lifetime or that process it can switch from being CPU intensive at any point to IO intensive and back to CPU but at any given instant you have to you can classify a processes as either being CPU bound or IO bound and as the name suggests CPU bound processes are ones that need a lot of computation cycles to execute IO bound processes spend most of that time doing IO those are the two things that are shown in the picture the x axis is time whenever you see a gray bar that means the processes actually executing and then anything in between that means it's not executing its。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_13.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_14.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_15.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_16.png)

And you will see that for IO bond processes， there are short bursts of computation and then long periods of IU。

And for CPU bound processes， it is the opposite a long burst of computation and maybe short bursts of I。

And we will come back to this when we think about what scheduling policies make sense for scheduling processes that exhibit one or the other behavior。

Okay， any questions on this？All right， so now。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_18.png)

Let's talk a little bit about goals for scheduling what are we trying to achieve by scheduling processes okay you can define various metrics and say the goal of the CPU scheduler is to optimize which could we mean maximize or minimize depending on the metric one or more of those metrics and then there are several listed here CPU utilization says the percentage of the time CPU is busy throughput says the number of processes that finish per unit time turnaround time says the time from start to the end of a process waiting time says how much time is it waiting in the run queue waiting for a readyDque excuse me waiting for return turn to execute response time says how responsive is it to I and so on these are different metrics that you will see in a system。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_20.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_21.png)

Now， you might think these are all good metrics to optimize。

why not try to optimize all of them as it turns out any scheduling policy can optimize some of them at the expense of others there is no policy that can actually optimize all of them together so you have to pick what makes sense。

If your machine is going to run lot of interactive jobs。

 if you are a user sitting and interacting with a graphical user interface。

 you want to minimize response time so the system appears to be responsive if your machine is going to run lot of bad jobs maybe you are doing batch processing you are running machine learning computation whatever it is you want to maximize throughput you want to maximize the number of jobs that are finishing per unit time so different metrics will require you to use different CPU scheduling policies。

Yeah， as we will see。对， now。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_23.png)

What I just said is actually summarize again here which essentially makes that same point I said saying if you're a bad system。

 you want to essentially optimize these metrics throughput turnaround time CPU utilization if your interactive systems you want to optimize response time proportionality which is I didnt define it but it says meeting user expectations you could have other kinds of system like realtime system so these systems are maybe systems that are in your car or that are in an airplane that are controlling mission critical systems in those systems you have completely different class of schedulers that try to meet deadlines that give predictable guarantees that can guarantee that such task task can finish in a certain amount of time and things so we are not going to look at realtime systems scheduling there's an entire class of scheduling algorithms and policies that are designed solely for that class of systems but we will not look at that we are going to focus more on general purpose systems which fall into the batch and interactive。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_25.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_26.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_27.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_28.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_29.png)

て。Okay。Yes， question。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_31.png)

Okay， question is in the the scheduling policy where you long term and short term scheduling。

 is there any priorities and things of that So there are no priorities because they run and operate at different levels。

 The long term scheduler is only looking at new processes that are starting。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_33.png)

typicallyically well at least the admission schedules are not the memory scheduler and the CPU scheduler is only looking at processes that are active it does not actually look at process dash so they are actually invoked at different points in time。

So there is no priority per se they are just doing two different things in the system。

Okay so now the question is they need to be coordinated so you cannot run up process that has been swapped okay so you will actually have data structures in the kernel which is called the process table that will tell you the state of each process if you swapped out the process it should not be on your run queue it should be in the weight queue right because it is waiting to be swaped back in right so there are things you will do to make sure the cases that you are mentioning don't happen。

Other question。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_35.png)

Okay， so。Let us go through policies that CPU schedulers use and as I said。

 this is that part is really a refresher， so I am going to present them and maybe see how。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_37.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_38.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_39.png)

how well you remember them or not and then we will decide how much time to spend on each so this I already mentioned which essentially says a scheduler cannot optimize all the criteria together so you are to pick depending on what system you have。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_41.png)

Okay so as far as the scheduling policies I'm going to present are concerned will start simple because it's easier to understand。

 we assume that each user has only one process， not true in practice。

 obviously users can start as many processes as they want will also assume that processes are sequential they have no threads one thread which is a sequential process again not true in practice because you cannot thread processes assume processes are independent which means they don't interact with one another。

 that's also not true because processes can communicate and then they are not independent and then we'll say single processes or single core which most systems today are not but this is a set of simplifying assumptions or us just to understand how the policies were but in reality none of those assumptions may be true policies have to deal with all of those issues。

Okay， so lets start very simple with first one which I think doesn' not really need a lot of explanation we will do first come first sir which is 54 okay that is a very simple policy okay you basically schedule processes in the order in which they arrived。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_43.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_44.png)

let us think about this and say is this a preemptive or a non preemptive scheduler？

It's a non preemptive schedule， Okay， because essentially。

As the name suggests you essentially once you schedule that process or for execution is going to run for as long as it wants because that is the concept of first come first serve now there are two variant of FCfS one which is an early one says the job does not give up the CPU even if it is doing IO so that means actually going to run all the way to completion and even it may have long bursts of IO which will idle the CPU but you are not going to schedule anything else in that。

Period more modern variants don't do that。 Okay they are not going to preemp the process。

 but if the process relinquishs the CPU because it wants to do I it is blocked on a lock or something like that。

 then something else gets to okay that maximizes CPU utilization。 It doesnt idle the CPU needlessly。

So thats F cfS。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_46.png)

Yeah， that are some。Advantages， which is very simple disadvantage is that the waiting times are highly variable in FcFs。

waiting time essentially says how long are you waiting in the run queue to get a turn to execute on the CPU？

Is it clear why there is more variance in waiting times？Yes， so tell me why。Okay。

 process lens are different okay it is like you are driving on the highway and you are stuck behind a truck。

Right so there's a long vehicle that is slowing everything down the same thing is true here if a long job runs before a short job。

 okay， that job is going to make the short job wait for a long period because FfS says you cannot run the short job until the long one is done Okay so depending on the arrival order。

 you might have high variance in running if the short job had before just before the long job everything would be reversed okay the waiting time for that arrival sequence would be much lower。

So it depends on the arrival order， and it can be highly variable。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_48.png)

Okay so here is a simple example which I am not going to go into too much detail just shows you how FFS works and it kind of makes the point I said so first one is BC are the three processes that arrive they execute an arrival order。

And the second one AB C arrive can A is longer than B and C as you will see so in some sense B and C have to wait longer than in the previous sequence because they essentially their B and C are shorter jobs the third example is just showing you what happens when you do IO。

It basically says if a makes any blocking calls once it arrives。

 then it has to relinquish the CPU B gets to run and then if it I is done when B complete it can resume execution。

Yeah， yes， question。しじ。He jumps to the front。the question yes。

 that's a good question The question is if a has relinquished the CPU B runs then and A is again done with its Io does a gets to run again is it at the front of the queue at the back of in Ffs since youre scheduling in arrival order what you do is you look at all the jobs that are ready to run you simply sort them in arrival order So a has arrived first in the system the fact that it went off to do IO didn't change that it was still arrived before C So it still gets to run in this case。

AsIO takes like one cent。We run time is 5 seconds。嗯。Is the CPU going on？From B for the entire。

5 seconds。Rightect。お们や。the question is if a does a short IO and B is longer process and is executing does a have to wait。

 remember this is a non preemptive scheduler。So once something runs you don't interrupt it so B is IO is done B arrived first but sorry AS IO is done a arrived first that B is executing cant preempt it until it finishes so it will actually have to wait so you will still see that order there。

That's true of any non preemptive scheduler。Any other questions。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_50.png)

Okay let us move on so the next one is also very straightforward this is called round robin scheduling as the name suggests in this case you are executing jobs in some round robin order。

All right， so you are basically going to have a queue of jobs， you execute one。

 goes back to the end of the queue once its time slice expires then you run the next one and so on and so forth。

So is this preemptive or non preemptive？Okay that is to be preemptive because if round robin is made non preemp to it degene to Ffs。

Okay if C if is essentially roundrop in in a non preemp fashion。

 so here every job is going to be given a time slice also quite quantum there is a duration for which when it is scheduled for execution it gets to run。

If it uses its entire time slice， it has to go back to the end of the queue if it blocks in the middle of each time slice。

 it is going to go to the weight cube。And when it's done with this IO。

 then it comes back and joins then。so that is basically what is going to happen in this case。

 so that is simple roundro in scheduling。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_52.png)

Okay， now。One issue with the roundro in schedulers is how large a time liess to pick。

That is the only parameter really that you have in round up in scheduling that you can play with and depending on the time slice that you pick you will get different properties lets pick a small time slice。

Now we are rapidly cycling between processes because each of them gets to run for a short period of time you switch to the next one and next one。

 so every process gets to make some progress for a little bit of time and then they give up the CPU。

喂。So so that' is good because it allows every process to make some progress。

 but in this case there are a lot of context switches you are switching between processes the thing that you have to remember is when you switch from one process to another there is some bookkeeping that the OS has to do it has to save the state of that process and load the state of the next process that means essentially all the registers have to be saved the stack point or frame point or all those to be saved somewhere you are to load the next processes registers and so on all of that in some over it it may be small but it is not zero。

So the more context switches you have in your system。

 the higher that bookkeeping tax you are paying in that system。

so more responsive but higher overheads okay now on the other hand if you pick a long time slice everything is inverted okay so now essentially a fewer context switches by definition because you have longer time slices but and each process gets to run for longer periods of time but each way process also has to wait for longer to get a turn on the CPU。

Yeah， so you are going to have this overhead。 So then the question is what is the right。Balance。

Between responsiveness to jobs and the amount of overhead you pay so typically those factors are going to determine what time slice you are going to pick for a certain system it is good to keep the overhead small so typically dont want the overhead to be too high so the quantum size is chosen so that the overhead is less than 1 percent thats a rule of them that is not a requirement of course so many systems will have 10 to 100 millisecond quantum slices。

Some might have shorter， some might have a bit longer。

 but that is still by and large what many systems are going to do。Good。All right。

 Any questions on this。So there is an example here which I'm actually going to skip because that's undergrad exercise which you can go back and look as a homework later on okay that just shows how the two work and then what waiting times you see the only thing I want to point out is if you take the same jobs and you schedule them using FCFS and using round robin and you calculate the wait times you will see that the wait times are actually going to be different in this case actually the round robin has higher wait times for this arrival pattern because remember FCFS can be highly variable in terms of wait time doesn't mean that FCFS is better just say that all of the jobs finish more or less at the same time the wait times end up being higher for roundro。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_54.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_55.png)

So that is something you want to keep in mind it is more fair。

 but then in some cases the wait time goes up。😊。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_57.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_58.png)

Okay， so we come to the next one， which is a shortest job first。Does anyone remember what this is？

As's Jeff。Yes。The。The list of products。List of jobs starting with the short。

so you order jobs by their lens and as the name suggests you pick the shortest one for execution next。

系。Preemptive or non preemptive。可以。ItCan be either， actually。

So the nonpreemptive version is called SJf the preemptive version is called shortest remaining time first so you can essentially time slice and at the end of the time slice you can again pick the shortest job the one that you are executing has just become a little shorter because it executed for one time slice but if a new job is arrived in that period that is even shorter it will get to run you say SJf by definition is not preemptive but Srtf which is its preemptive variant can actually use time slicing。

Okay。So you can have either one，What is good about SJF and what is bad about it？Yes。Processes。Okay。

 so one downside of shortest job first is that it requires knowledge of the job length。Okay。

 where is that coming from？Yes。Okay， you can only estimate it at no point when you ever started the process。

Or a browser did the voice says， how long are you going to run it？

RightUse don't know anything about job length always doesn't know anything about job length。

 so you can't really know what job length are only thing you can do as was pointed out is estimate you can use past historing when this job ran previously ran for this long so I estimate that it might run this long but that's an estimate it is not a guarantee so it is by definition since job lens are unknown you cannot actually implement this in practice unless you have a way to estimate that length in some accurate fashion Okay otherwise is not practical to implement。

So that's the downside。What's an upside of this place。です。Okay， shorthorest jobs can be done faster。

 Okay， you had something。L turn。对的。Okay， turn on。Okay， so you。More short jobs finish。

 but what does that do to the system？Okay，So the only policy is you actually read is all said there。

The first advantage is this proably optimal waitinging time is only policy that actually minimizes waitinging time across all processes there is no policy that can actually do any better。

It is optimal in terms of eight times。Because it is actually preferring short jobs and getting them out of the system as quickly as possible the rate times that jobs see are going to be as small as you can make them。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_60.png)

Okay， so that's actually the only reason we've。Even study this policy in。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_62.png)

Operating system textbooks is it does that property which you want in a practical implementation you cannot implement as jf but any any scheduler that you want to implement we would like to have that policy because good low weight times is a good thing。

Okay， yes。Of S R T F with the。quantumantum is smaller。こ大。

Yeah so what happens in SrRTf if the time quantum is smaller than。The length of the job， right。

 So let's take an example。 Let's resume time quantum 1 millisecond。Lth of the job。

5 millisecond okay Another job comes as 10 millise two jobs，5 millisecond job。

10 millisecond job Okay， you are going to pick the shorter job first。We will pick the first one。

 we will run it for a millisecond。K not what happens。Sp the next。So after the job finishes this。对。So。

 in SrDF， if there are no new arrivals， it basically turns into SJf because the shorter job gets keep getting even shorter because it is executed for some time。

 it will run again。not this is not doing round robin he is not going to the end of the queue it is just looking at all jobs and saying what is the shortest job or shortest remaining time which is what is the job the time left on this job that is what is checking so you dont vary from SJf。

Is there a time quantum in SGf SJf is not preemptive so it does not have the notion of time quantum but SrRTf is a preemptive version of SJf which actually has time quantum。

Yes so there are two variants。Any other things here？Okay。

 last thing that is bad about SJF is it can lead to starvation of long jobs。

Okay so it has low wait times because it is preferring short jobs but if theres a steady stream of short jobs arriving and there is a long job that arrive sometime it will never get to run because short jobs are always different and thats something you don't want in a practical policy so you want to do two things you want to get the low optimal wait times or approximate it in a practical policy but at the same time you don't want any starvation either so those are the true properties we will try to actually extract from SJf and see how to get it in a different policy。

Okay。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_64.png)

All right， so we will skip the example but you will see that the weight times are the lowest for SJf if you actually work through that。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_66.png)

Example。So what we now do is start looking at what actually most Os do。

 Well start with priority scheduling， and then we'll make that a little more complicated variant of priority schedul。

 So let's start with what is priority scheduling。 That picture is actually a good one to keep in mind。

 Okay in a priority scheduler， you essentially do。round robin scheduling but you have multiple priority levels or multiple cus okay you do round robin in each queue okay but you start always with the highest priority you do round robin in that queue when that queue becomes empty you go to the next highest priority queue that is not empty you do keep doing round robin and so on and so forth。

So if these were the only jobs in the system no new jobs arrive you will essentially and I am assuming in this case four is the highest priority so you will do round robin at priority4 eventually those jobs will finish then that queue is empty then you will do round robin at priority three eventually those jobs will finish and then one and so okay of course there will be in a real system arrivals in the system that will change that behavior but that is what you should expect。

so it is called priority scheduling keep in mind that in a priority scheduling there are a few things to keep in mind it can have starvation problems if you are a low priority job and there is always a high priority queue that is non empty that low priority job will not run。

Just as an SJF， the longer job interval so it can face starvation。

Okay that's something you want to keep in mind。 The second thing you want to ask is who is going to decide the priority level of jobs。

Where is that going to come from？Any thoughts on that？Whos who's giving priorities to jobs？

Process manager， process manager could assign priorities。

there are only two entities that can give prior user or the OSs。Pros doesn't decide its own priority。

 process just runs。Okay turns out that you can actually have both of these users can assign priorities to jobs or definitely assigns priorities to jobs When you start a process it will have a default priority okay you can actually use some command to assign priorities to your own jobs okay。

Anyone know what that is in Uniix。Nイス。So， nice is a command that allows you to change the prior so if you say nice process ID and give an integer that is a priority level。

 the OS will actually choose that to be the priority。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_68.png)

Typically as the command I suggests it was put in place so that you could lower the priority of your job to be nice to another user but of course you can increase the priority of your job as well。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_70.png)

Alright， so that so users can change priorities of jobs。

 the OS by default gives priorities and you'll see in some schedulers they can change the priority dynamically And then。

 of course， there are really more important things in the system that you want to run at high priorities Okay that includes the kernel itself system processes and so on device drivers So you run all of those at high priorities maybe user processes run at slightly lower priorities。

 so that is how you are going to assign priorities to you。

 but keep in mind you will still have starvation if you don't do this careful。Questions on this。

Okay so now let us go to what is a variant of a priority scheduler that incorporates some of the features of multiple scheduling policies we have talked about okay the name of this policy multilevel feedback your MLlFq you might remember some details from undergrad course but let me go into that again because this is also the policy that Min is going to use。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_72.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_73.png)

， first and foremost MLlFq is a priority scheduler。

Simple priority schedule it has multiple priority levels。Within each level。

 you are going to do round ro in scheduling。First， property of MLFQ。

Anyone remember anything else about MLFQ？Yes。Everything gets reset。 Can you explain what that means。

A certain。包的。这是。スケパン大学。They don't get stuck by。slowly。

Okay so you are talking about the property that essentially allows you to avoid starvation so what MLFQ does is if a process is stuck in a low priority queue for a long time and hasnt gone to execute it is going to bump it up one priority level saying maybe this job is starving lets just increase it a priority a little bit so that it might get a short。

But we will come back to the starvation problem at the end that is just put in place to avoid starvation。

Let's talk about what is there in the policy that is interesting。Anyone remember any more details？

Yes。 so MLFQ prioritizes IO bound processes。That's true。How does it do it and why does it do it yes？

The process stops using。That's amazing。Toは。It keeps it at its current。Assum that it's going to heat。

Not using its full time。Right。The process uses its full。

A lot of time it bumps it down because it assumes it's a。That long。Butですね。Okay， so yes。

 so let me explain the MLlFq rule okay MLlFq is a simple rule whenever you schedule a process for execution and give it a time quantum it says what happened when that process finished its time slice Did it use entire time quantum or did it block before its time quantum expired if it uses its entire quantum you are going to reduce the priority of the job if it actually is blocked in the middle of which time quantum you are going when it becomes runable again you are going to increase the priority of the job by what。

That is the MLFQ rule which allows you to change the priorities of the job as they execute。😊。

But the question is， why does it do it？what makes this a good rule。

 why could I not have done something else？Let not change priorities at all， yes。

Okay so that is a good point。 So if you look at what this rule is going to actually do to this process remember I said at the beginning there are two types of processes CPU bound and IO bound。

So you should ask the quality question if I execute a CPU bound。

Not execute I actually schedule a CPU bound process this on the processor。

 what is the probability to use its entire time slice？Hi， not asking for a number。

 I'm just saying is it high or low。 So it's going to be high because by definition it's CPU bound。

 it needs a lot of cycles。 it will likely use up its entire time quantum execute。

 The opposite is true for IO bound job。 if you schedule an IO bound job The chances that it gives up its the processor before those time has expire is going to be high。

 Thats the behavior expect to see for CPU bound and IO bound Now。

 if you say bump up the priority of any job that does not use it time slice by definition you're going to start favoring IO bound job because those are precisely the jobs that are not going to use their time slice。

 So the priority levels of those jobs is all going to rise。😊。

And the opposite is true of CPU bound jobs because they finish their entire time slice okay。

 their priority levels are going to drop。As a result。

 if you have let us say a4 level or four priority MLFQ scheduler okay over time you should expect all the IO bond jobs to be at the top and and the top being high priority in this case and all the CPU bond jobs to be at the bottom which means they have the lowest priority。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_75.png)

Okay。So we are basically MLFQ is favoring。IO Bo jobs， our CPU Bo jobs。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_77.png)

And now we should ask is this is a good thing， what does this give us？Yes。That's what I said。

It will see faster。You can see。Right。So， you will have more responsiveness to some degree that is true。

 but all we are seeing is the IO bound job is going to go back doing IO。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_79.png)

It is not necessarily saying anything about users interacting with us， but yes。

 what you are saying is also towards an artifact of what actually is happening in terms of favoring iberg。

Any other thoughts here， yes？You are increasing the ion utilization through and you are also increasing CPU utilization to some degree。

ゼーション。公司。你し学。Wing times， yeah。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_81.png)

Okay， so that's true。 You get that behavior because you are favoring IO bound Okay now the other thing you should realize is because you are favor Io bound jobs over CPU bound jobs MlFq is approximating shortest job first。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_83.png)

Because our iobound jobs are actually the shorter jobs in the system if you go back to that picture I showed you at the very beginning。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_85.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_86.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_87.png)

Which is here， So you will see in that picture that because Ibound jobs are short CPU bursts。

 they look like short jobs because we are only talking about when they execute on the CPU and CPU bound jobs look like long jobs。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_89.png)

Okay so by if you just start favoring iObound jobs you are essentially going to start approximating shortest job first without requiring any knowledge of the job length whatsoever。

 you are not asked what the job length is you are simply saying I am favoring shortest short jobs which are in this case IO bound jobs and how do you know a job is iO bound you don't ask for a label or you see if you bond or iO bound you simply observe its behavior did it finish its quantum or not if you didnt you are an iO bound job with high。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_91.png)

Probability if you did then you are a CPU bound job with high probability okay so what MLlFq does essentially has a score is is approximating shortest job first without requiring any job length knowledge and by just assuming that short jobs are also the same as IO bound jobs and long jobs are essentially similar to CPU bound jobs question。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_93.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_94.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_95.png)

Would this also decrease the number？

![](img/eccda023ecfa6a8c75fcf945fd2a285e_97.png)

T switch。Will it decrease the number of context switches in some sense。

 MLllfq has other properties which also decreases the number of context switches which I didn't get into yet because the thing that I didn't show you is along with the priority level being different each queue is also assign a different time slice length the highest priority queue gets the shortest quantum the lowest priority queue gets the longest quantum and this is okay because typically you' are running io bound job in the short quantum So you don't need to give it a long quantum and block immediately short quantum is okay and CPU bound jobs are sitting at the bottom they need to run for long periods of time it's okay not to context switch frequently in that case because you are maximizing CPU utilization so you are actually going to by having different quantum durations across queues youre also reducing the number of context switches because if you had the same quantum duration you would have a lot more context switches。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_99.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_100.png)

Youbound jobs in this case。 so lots of property is thrown in。

approximating shortest job first shortest jobs are the same as iObound jobs change the priorities to actually infer which one is an iO bound。

 which one is a CPU bound job use differentiated time slices to reduce context。

 which is so many things come into plate all at once and then the thing that was mentioned at the very beginning。

 which is you also have to throw in something to avoid starvation because lots of iO bound jobs that keep getting activated your CPU bound jobs are going to sit at the bottom。

 get no CPU time whatsoever so to do this， if you sit in queue and do not get scheduled for a certain period of time。

 you automatically get bumped up so eventually if you have any jobs that are starring they'll rise to the top。

 they at least get one shot at the CPU and then fall back and then that same thing might happen every soft but you wont be perpetually stopped。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_102.png)

对， yes。Smaest。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_104.png)

At the smallest priority， small meaning high or low， what do you mean by small？I有 job。Yes， the high。

 the high。 yes， the I O bound jobs are at the。IS priority level here， the quantum is the smallest。

The lowest priority level time quantum is lovely。Yes， so initially。

 when a our job comic will go to lowest priority level。No。

 so the question what you do in the system is when a job arrives， you started at di highestpar。

 not at the lowest， just to give it some benefit of the door， you don't know what kind of job it is。

Yes， if its CPU bound， it will drop immediately。Okay so all new jobs。

 So that's the one thing I didn't mention。 all new jobs start at highest priority level because you don't know anything about the job when it starts。

Okay。Right right。 So that's。Essentially multi level feedback you。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_106.png)

Okay， so and then I talked about how your existing priorities。There's some exercise。

 which I'm going to skip。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_108.png)

And then talk about some other things Okay， so this also we talked about。

 which is how do you avoid starvation and so on。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_110.png)

Because here' is one policy， which is a randomized policy。

As the last one we are going to talk about before we switch to what Minex does and you will see Minex essentially implements MLlFq。

Okay， that is why I went through MLFQ in some detail。

 but we will talk about one more before we jump to Linux， which is called lottery scheduling。

Does anyone even remember this？Yes， what is it。ど。Okay。

 so lottery scheduling is a randomized policy where every job is given some number of lottery tickets。

😊，and to decide which process gets to go next you essentially run a lottery。

 you take all the lottery tickets from all runnable jobs and then you pick a winning one and the job that has the winning ticket gets to run next。

Okay， so let us say you give one ticket to e job so if there are n runable jobs you will get chosen with probability1 over n。

Okay， so our entry is hopefully you get to run so it is completely randomized there is no guarantee that you are actually going to get one time slot every end time slots but on average or long periods of time that lap。

Now， what is good about this policy， why do we want to do things in a randomized fashion looks like it is doing what roundropbin was essentially doing。

Any thoughts on why we care about lottery scheduling？Yes。Okay。Yes， that's right。Given enough。Yes。

 so over time it is fair。 but remember， nobody said you have to give only one ticket to each process。

 I just made that up as an example。 You can give as many tickets you want you meaning the user or the to each process So what lottery scheduling does is it allows you to control the amount of CPU time each process is going to get over some larger periods of So very simple example if you are two processes and one process has two tickets and the second process is one ticket essentially the second first process is going to get two thirds of the CPU time and the first one is going to get a third you did round droppingping you would have gotten equal you can't control how many times slices you get here you actually control it's randomized but you do control by controlling the number of tickets So if you want to give a lot of CPU time to a process you should give it lot more lottery tickets。

 It's like increasing the priorities in some sense lottery tickets are acting like priorities but not theyre not exactly priority which just increase the chances that。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_112.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_113.png)

That process wins and hence gets to run more often。Okay， so here the。

interesting thing is by controlling how many tickets each process gets carefully。

 you can also control what percentage of the CPU time it actually runs on the processor。That clear。

and because it is randomized over longer periods of time it all ends up being fair and fair here means you should get CPU time in proportion to the number of lottery tickets that is a definition of fairness not that every process gets equal time that is not what is the question。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_115.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_116.png)

Don't you actually have to know which are the short running jobs to give them those tickets。

 so it's kind of just as unrealistic as SJ？But。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_118.png)

So you're asking a question about the third bullet here saying I could give more lottery tickets to shorter jobs and then you would approximate SJf because they get chosen more frequently or run quickly that's indeed true if you to do this you do need knowledge of whether it's a short job or iO bound job and so on and then without that knowledge you cannot accurately give the number but should if you knew that you could so that's indeed the case based on past history and things of that but but that's not only reason you want SGf you can just say this there are two jobs I just need this job to run more because it has more needs as compared to more compute needs I just give it more lottery ticket independent of whether you're iO bound or not even across CPU bound jobs you can partition the CPU time across processes so two to one say 63 sorry66。

33% so that kind of stuff So here is essentially examples which。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_120.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_121.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_122.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_123.png)

Make it a little more complicated than they have to short jobs are being given 10 tickets。

 but you need to know what short jobs are as was pointed or but let's assume you know long jobs get one tickets and say if there are one short job one long job the short job is going to essentially get picked 10 over 11 times and the long job gets picked1 over 11 times okay so 91 and 9% and then you can work out all those other numbers if you want you will see that by varying the number of lottery tickets you can actually vary how much CPU time each job gets yes question。

半家不。Yes， yes。How are you going to be able？That's a good question。

 The question again is you don't know either a job is a short job or a long job Okay and then how do you decide based on if you didn't know how bad tickets to so that's a valid criticism of this policy but that's not how it actually gets used in practice you are not trying to say long jobs get more tickets and short jobs get fewer tickets or the vice versa what you' are actually doing is you are taking。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_125.png)

Some jobs， they may be all similar jobs， not short or long and trying to say this job should get this much time and that other jobs should get this other time。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_127.png)

Like as a user， you run。We don't need。Yes I can。If my。気。Procesす。Yes， so as a yes。

 so as a user you are never asked to assign priorities to jobs， yes。

 in Uni there is nice but nobody uses it。Clearlyly right but same history true of lottery scheduling。

 you are not expected as users to say this and I will mention where actually things like this get used。

😊，So， they are actually used in many other kinds of scenarios like virtualization is a good example if you create multiple virtual machines on on one physical machine you can use variants of lottery scheduling to say this virtual machine。

Has more jobs running in it。 I want to give it 60% of the total CPU cycle and this one needs 30% so you can essentially partition your CPU。

 This is not trying to discm with an I or CPU bond。

 It's simply saying I want to give X percent of the CPU to this job。 How do I do that。

So that is what is actually used for this example is not really the way it gets used at all。😊。

Any other questions。So there are deterministic versions of this which allow you to give something called a weight weight is equal to the equivalent to the number of lottery tickets and those deterministic versions actually guarantee that every time slots some fraction actually goes depending on the weight to a certain job this is a randomized version Its very easy to understand but they are deter which are slightly harder to teach but they do exactly the same thing and that's basically what gets used in many virtualization framework they get used in routers to allocate bandwidth that's another scenario so if youre two users one user needs more bandwidth or a spare for more bandwidth thats how you are actually going to get allocated if your cable provider says you can pay for 50 mebits per second or 100 megabits per second they got to allocate that capacity to you on a larger network these are the kinds of techniques they are using to do that。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_129.png)

![](img/eccda023ecfa6a8c75fcf945fd2a285e_130.png)

but we will keep that aside for now and come back to scheduling and operating systems so with all of what I just said we can now go and look at what is actually happening in minutes。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_132.png)

So Linux is essentially implemented because it's meant for teaching purposes it essentially does what you learn in a textbook it basically implements MLlFQ everything I said about MLlFq and some other concepts actually what Linux does that's not true of more general purpose operating system right Linux does not actually do anything close to what anything we learned here it has its own thing now which does order one constant time scheduling and things of that sort and when you do multiprocessor scheduling things get even more complicated if you didn't talk about multiprocessors at all but Linux is compact and nice to understand what it simply does is MLlFq so as I said when is the scheduler invoke all of what I said earlier is still true and a process exists you got to invoke scheduler and say what gets to run next when the process blocks on Io blocks on a lock some of you got to invoke the scheduler and then when a process new process gets created when an interrupt occursers or when。

Quantum expires also the scheduler gesture everything I said before still too in the Linux case。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_134.png)

This is essentially a picture that shows you the scheduler in Min， it is a 16 level MLlFq scheduler。

Yes has 16 priority levels priority levels go from 0 through 15。0ero is the highest 15 is the lowest。

 so higher numbers are actually lower priorities。It is the opposite to how we think。

 but thats how Uni dusting so they map directly to nice priority levels in nice you can say nice and give it priority4 it will go to the fourth Q。

5th Q action， because you start from 0。Okay， so15 16 level scheduler okay and some。

Priority levels are used for。Scheduling OS level tasks some are used for scheduling user processes Okay kernel tasks run at priority level 0。

 The only two things that run there。 that's our system task and the clock task。

 when we come back to the micro kernel we see again there are two key components in there the system task that essentially implements all system calls and there's a clock task that is implementing time there's also some IP thats happening So all of that is in in the system So that's running at the highest priority level you will see that device drivers and some of the system processes we talked about file server process manager virtual memory manager device drivers that essentially run or priority levels one through four。

Still higher than all user processes。and then user processes according to the book they start at 7 okay I believe five and6 are unused I dont know why but they are not used right so they start at 7 and go all the way up to 14 okay the I task runs at 15。

So， ID task is essentially a task as an infinite loop when there is nothing to schedule you just run the ID task for a time quote。

Okay so it is the lowest it is always the lowest priority task that gets to run when there is nothing else to do because you can't really keep the CPU id if you keep the CPU id the voice will not run so you basically run and that' is not true but I mean you got to run something so you run the IL task。

Okay， now。With that in mind all of what I said about IO bound job， CPU bound job that is still true。

 but only for user level processes you are checking when you run for a quantum did it finish that quantum did it not。

 you bump its priority level one up or one down based on。Okay。

 the priority of the kernel task is not going to change。It is always going to be at0。

 it doesn not matter whether it is used just quantum or not it is statically bound to priority0 same as true of some system level processes。

As far as what the book says I won't verify the code actually because sometimes there's discrepancy between the book and the code。

 the book says that system processes are treated no differently from user processing。

 which means they can be bumped up or down， but I believe that not all system processes are treated that where some are actually pinned to priority levels。

 but some others might be actually floating up or down like any user process。Okay。

So that is the picture you want to keep in mind。as Min is concerned at some point you will start mucking around with the scheduler。

 So you need to know that's how it actually looks pictorially Here is a multilevel feedback you will see that each queue each level is implemented essentially as a Q of task linked list with a head and a tail Okay so essentially it's a single link list not a double link list a single link list and there is always two pointers one pointing to the head of the queue1 pointing to the tail of the。

The head of the Q is what at the beginning you pick a task there and then if you want to put it at the end you have to append it to some。

Okay。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_136.png)

Allright so I said priorities are assigned with nice so since this is the first time some of you heard of nice go to any Linuxux machine or Mac and type nice or man nice and you will see what nice can do can change a priority of a task fairly harmless thing to do okay not going to do anything bad for you okay so idle process runs at 15 system processes kernel task not system processes run at level0 device drivers one through four。

Allright， so。Users can essentially assign priorities， yes， with nice。Nice。Okay。

 that' is a good question。 So does the question is does nice spin up priority or does it actually allow it to change。

The answer is actually， it depends on the OSs。Because you are doing MLlFq scheduling if you nice it and stuck it at some level you cannot do MLFQ on that process so what actually happens in most real shouldnt say real mean this is also real most general purpose operating systems is that there is a concept of a priority and the concept of where you are in the MLFQq there are two different things so the priority level kind of allows you to say how you start off but eventually you are allowed to drift up or down from there。

but yeah， I think the implementation of nice how it maps to any of this is left to the OS。

 there is no set requirement。Any other questions。

![](img/eccda023ecfa6a8c75fcf945fd2a285e_138.png)

Okay， few more things I want to say。 So the other thing you should know about Min is this whole restart task okay which is essentially the way you' are going to invoke the CPU scheduler so the restart task runs every time few different things happen whenever there's an interrupt and there's a system call when the quantum expire you' see that there's a flow chart there which you can ignore for this point in time。

 but essentially many things essentially invoke saying restart restart doesn't mean you rebooted your own it just means that I want to start a new task execute a new task So eventually that task will invoke the CPU scheduler and say a system call has just finished or interrupt handler I just finished quantum measures expire what should we do next so that's the entry point of how the CPU scheduler essentially gets invoked。

So thats an implementation detail， but something you should know because youre going to make some changes to some of these now as far as the scheduler is concerned okay the implementation according to me at least is not as clean as one would like it is spread across multiple files and multiple components it is not hard to understand but they didn't have a schedule dot c which had everything you needed to know about the scheduler it spread across multiple things the restart process is actually not pass task is in main dot C and that main dot C also has all of the cues that I was talking about the heads and tails of all the cues of the MLlF you scheduler can be found in that in that。

肺嘅。So the inqueuing and decoqueuing of processes is actually done in table dot C I don't exactly know why it is different but that is where it does it and then there is a function called SCd which essentially decides which queue should a process be added to that is where the priority levels are getting changed。

Okay and then there is another function called pick process Okay that is the one that is actually deciding okay this is the process that is going to go next it is essentially doing a priority scheduling at that point we take the highest priority non emptyq take the head of that queue schedule that process。

 so it is kind of spread out a little bit， but once you get the hang of it is not hard on。

Happening in the kernel， is this happening？Okay， is this happening in the kernel or the process manager。

 Some of this is actually happening in the process manager， but not everything。

 Some other things are happening in the kernel as well。

A few things are happening in the kernel because some of the data structures are to be changed in the kernel。

But you can implement some aspects of it in the process manager。Any other questions here？Okay。

 so that's the lay of the land as far as how this implementation goes。

 Well come back to this when the next lab actually is given up。

 is something just wanted you to understand。Pplementation and how it maps onto the source3 and things of that。

Any questions on this？Any questions on the lab。Did you see the post I made about the scribe notes？

we implemented lottery scheduling。Some of you want the lottery so keep that in mind so we will essentially have youscribe some notes okay so we can then hand that back to the plus。

😊，Okay， so if that book more questions we end it here on Thursday we will talk about the process manager we will start getting into what processes look like and so on。



![](img/eccda023ecfa6a8c75fcf945fd2a285e_140.png)