# 麻省大学《操作系统 设计与实现｜CS 577 Operating Systems Design and Implementation 2020》中英字幕 p14 -14-Lec07 Video_ CPU Scheduling (02_11_20).zh_en -BV1iP2CBaEHr_p14-

Okayそレスタちょっとレ。Mcture is going to be on processor of scheduling。 It is a little bit out of order。

 because normally。Go and process management first， what's the process， our just this？

Create processes。 and so。 And then we talk about how to schedule them。

 But I wanted to do it a bit out of order， because。

I think the next lab might require you to do something with CPU scheduling。

 so I wanted to get that material。First， and then we can go into the details of process management。

Make set things up。So today's last are three things I' talk about first is what is processor scheduling。

 what are the goals of scheduling processes？The second one is going to be a re on CQ scheduling。

That accepted point is some material from an undergrad over。

Depending on how much you remember or how little you remember。

 you can speed it up or slow it targets entirely going to be based on water。

I want to ask you some questions in the particular。what。いやの。two years the。这个 third把这个货超的。

What does CPU scheduling in Mid look like？And well see the concepts actually directly translate to。

AN implementation。说的。Surpriss that most us will do their own thing。

 This one does more of a textbook stay money of schedule。

So let's start with the first point which is。Process of scheduling。

 so this this picture essentially shows us the process state transition diagram。

 which we haven't encountered it。 will'll get back to this。What process management。

 but by and large that figure says when processes start theyre in a new state and then through their execution cycle they cycle through essentially ready running and wait in a ready state a process is actually ready to execute on the CPU is just waiting for external to run on the CPU。

 the runstead is actually executing if it does any IO it sits in a each state waiting for that IO to complete。

So you cycle through these states and eventually you're done executing。

Okay so that's the thing you want to keep it mind。 The goal of the CPU schedule。

Essentially to decide of all the processes that are in that ready state。

 which one is actually going to execute next and you'll see that there's one process。Thereforefully。

 write about the running state is one process in a single processor machine that only one。

ing at any given timeOf course， in a multi processor system。

 multi code system therell be as many executing processes as the number of course。mean。

 that's a limit on the number。So our goal is to design in a multi program system a CPU schedule and multi programminggram again only means the ability to run multiple processes concurrently on your system。

 Uni program systems is you can only run one application at a time in addition to the OS multi programgram once you can run multiple。

So that's the definition ofグ。只能。Let's talk a little bit about how。

Scheduling works more broadly and then we talk about specifically processor schedule so in any OS and it depends on the flavor of the OSs there are two kinds of decisions being made one is called longter scheduling and the other is called short term longter scheduling is looking at how many processes can that system accommodate at any time for concurrent execution。

And the answer to that is going to depend on things like how much RA do you have that you cannot create unlimited number of processes and expect them to run eventually your system the run out of resources so the goal of the long term scheduler is to police the entry of processes into the system so you will see here that there is essentially here queue newly arriving jobs enter that queue the long term in this。

One part of the long term schedule here which is called the admission scheduler is checking have you run out of resources to admit yet another process in the system if so you are not going to let that process run if not you will basically let it actually become a real process and start executing。

This is another part of a long term scheduler which you don't see often as much every scheduler and its goal is maybe there you have matched out your system resources。

 you want to let another process in， the only way you're going to do that is you to take an existing process that's executing temporarily swap it out to disk。

That's what that memory schedulers is doing it's swapping entire processes in and out of memory just when you are run out of resource because the two collectively do long term scheduling decisions we basically decide how many processes are actually in。

execution案。メ。Using virtual memory how many are active processes in the system？

And then that short term scheduler is the one that you see at the top。

 that's called the CPU scheduler of all the processes that are currently active and ready to run。

 which one gets to execute next。So that's the goal of the and that is what we will call a CPU scheduler you won't actually use the term short term scheduling but well use the term CPU schedule Thats what I just said on the previous slide is just summarized here so I'm going to just skip。

So。Now when the short term scheduler okay， the short term scheduler or the CPU scheduler is essentially a core functional function of the OS kernel。

So it's going to get invo when one of a few different events actually occur then those are listed there saying if a process is。

The process is switching from running to reading， the process that's executing blocks。

The CPU becomes id。So the currently executing process blocked。

 so then you have the CPU carrier saying what next？

Then theres an interrupt same thing happens because an interrupt handler is going to run and then once the interrupt handler is done you have to say what should I run next should I assume the process that was running should I run another process。

 all of that is going to be decided like the sequenceQ schedule。

First a process is created or terminated you。But the see。All of those things happen。

And we will see that there is one more event that can occur vector trigger the CPU scheduler。

 but for that we need to define two terms non preemptive and preemptive scheduling。

Non preemptive scheduling says once the process starts executing on the CPU。

 you cannot actually preempt it。Which means that the scheduler cannot say。

That something else has to and it can run for as long as it works。Until it blocks or。

That's a non preemptive schedule okay most schedulers you see are not non preemptive they actually form in pre fall in the preemptive category and as the name suggests。

 a preemptive system is one where the CPU scheduler can interrupt that process or the OSs can interrupt that process。

And so this is of used in the context of your。What is called quantum based scheduling whenever a process runs is given a fixed time Qta and say that's the amount of time slice you have it can use this entire time slice at that point it is preempted and something else。

So in preempt the scheduling， in addition to those three things that cause the CPUQ scheduler to run。

 theres a4 EUN which is quantum expired and the quantum expired scheduler will also run and say what gets to run。

Is this clear？So now let's talk a little bit about some of these policies so before we do that it's good to understand what process behavior looks like so we can design policies that are designed for various kinds of process BH by and large when you run a process on your machine it will fall into one of two categories in either the CPU intensive or IO intensive。

At any given instant or the lifetime of that process it can switch from being CPU intensive at any point to IO intensives and back to CPU but at any given instant you have to can classify a processor as either being CPU bound or IO bound and as the name suggests CPU bound processes are ones that need a lot of computation cycles to execute IO bound processes spend most of their time doing IO okay those are the two things that are shown in the picture the X axis is time whenever you see a gray bar that means the process is actually executing and then anything in between that means it's not executing its block。

And you will see that for IO model processes， there are short bursts of computation and then long periods of IO。

And for CPU bound processes， it's the opposite， long burst of computation and maybe short bursts of fire。

And we'll come back to this when we think about what scheduling policies makes sense for scheduling processes that exhibit one or the other。

Any questions on thisす？そな。Let's talk a little bit about goals for scheduling as was what are we trying to achieve by scheduling processing so you can define various metrics and say the goal of the CPU scheduler is to optimize which could we mean maximize or minimize depending on the metric one or more of those metric and then there are several listed here CPU utilizations as a percentages at time CPU is busy。

Pput says the number of processes that finish per year at time serve around time says the time from start to the end of a process。

 waiting time says how much time is it waiting in the run queue。

 waiting for a ridicule excuse waiting for a turn to execute response time says how response is it to Iowa。

These are different metrics that you will see in the system。

NowYou might think these are all good metrics to optimizeim。

whyhy not try to optimize all of them as it turns out any scheduling policy can optimize some of them at the expense of others there's no policy that can actually optimize all of them together so you have to pick what makes sense。

If your machine is going to run lot of interactive jobs。

 which is a user sitting and interacting as a graphical user interface。

 you want to minimize response time so your system appears to be responsive。

If your machine is going to run a lot of bad jobs， maybe you are doing batch processing。

 machine learning computation， whatever it is， you want to maximize throughput。

 you want to maximize the number of jobs that are finishing per unit time。

So different metrics will require you to use different CPU scheduling policies。Yeah。都。

What I just said is actually summarize here， which essentially based that same point I said saying if you're a bad system。

 you want to essentially optimize these methods to put turnaround time CPU。

The interactive system we want。I' with this response time bushmatic here。the fighting what it says。

Expectation， you could have other kinds of systems， linear and time system。

 so these systems are maybe systems that are in your car。

an airplane that are controlling mission critical systems in those systems are completely different class of schedulers that try to meet deadline that give predictable guarantees that can guarantee that such the task can finish in a certain amount of time and things of that sort。

We are not going to look at realtime system scheduling。

 this entire class of scheduling algorithms and policies that are designed solely for that class of systems。

 but we will not look at that we are going to focus more on general purpose systems which fall into the batch and the interactive gap。

Yes question so the like the different types of schedulers in a three level one。

 So like do they have some sort of a hierarchy in terms of priority。

 which like one scheduler gets over the other like question is in the。4。60。

Policy where your long term and short term scheduling is there any priorities and things of so there are no priorities because they run and operate at different levels The long term scheduler is only looking at new processes that are starting。

It typically at least the wish schedule or not the memory scheduler and the CPU scheduler is only looking at processes that are active。

 It does not actually look at processes does time， So they are actually involvedked at different points in time。

That's what the most priority per se that' just doing two different things in the system。

They need to be sort of synchronized。Together so that the CPUU scheduler doesn't try to run an instruction of a process which already got swaped out or something like that。

Okay， so now the question is they need to be coordinated， so you cannot。

Runups process that is been swapped Okay so you will actually have data structures in the kernel。

 which is called the process table It will tell you the state of each process So if you swapped out a process it should not be on your run cube It should be in the weight cube。

Because it's waiting to be sorted back in so there are things you will do to make sure the cases that you are mentioning don't have。

し。So。Let us go through policies that CPU schedulers use。As I said。

 this is that part is India refresher。 So I'm going to present them and maybe see how。

When you remember them。And then we decide how much time to spend on so this I already mentioned。

 which essentially says a scheduler cannot optimize all the criteria together so youve got to pick depending on what system you are。

Okay， so as far as the scheduling policies， I'm going to present our it start simple。

It'Easier to understand， assume that each user has only one process。

 not true in practice the user gets that as。We also assume that processes are sequential。

 there have no threads one thread， which is a sequential process。not to practice。

P processes resume processes are independent， which means they don't interact with one another。

 That's also not true because processes can communicate and then they are not independent。

Then then you'll say single process or single quote， which most systems today are not。

But this is a set of simplifying assumption for us just to understand how the policies work。

 but in reality， none of those assumptions may be true。

 the policies have to deal with all of those issues。So let's start very simple with first one。

 which I think doesn't really need a lot of explanation and do first come first。hi is54。

 that's a very simple policy。You basically schedule processes in the order in which they have arrived。

Let's think about this and say， is this a preemptive or a non preemptive scaling？

It's a non preemp schedule。Essentially。As the name suggests。

 we essentially going to schedule that process for execution。

 it is going to run for as long as it will。One， which is an early one。

 says the job does not give up the CPU even if it is doing all。

So Ane is actually going to run all the way to completion and even may have a long burst of IO。

 which will ideal the CPU， but you're not going to schedule anything。

More modern variants don't do that okay they are not will preempt the process。

 but if the process relinquishs the CPU because it wants to do Iowa。

 its blocked on a lock or something like that than something else is。That maximizes CPU utilization。

 it doesn't id the CPU lit。Well that of CFS。There are some。Advantages， which is very simple。

 disadvantage is that the waiting times are highly variable in FCFS。

waitinging time essentially says how long are you waiting in the run queue to get a turn to execute on the seat？

Is it clear why there's more variance in waiting times？在没外。Okay，Pros levels are different。Okay。

 it's like you're driving on the highway and you're stuck there that time。

So there a long vehicle that is slowing everything The same thing is true here。

 if a long job runs before a short job， okay that job is going to make the short job wait for a long period because FfS says you cannot run the short job and in the long one is stuff Okay so depending on the arrival order。

 you might have high variance in if the short job at before just before the long job。

 everything would be reversed with the waiting time for that arrival sequence would be much lower。

But it depends on that I was ordered and be I。So here's a simple example which I'm not going to。

The just shows you CF if this works。point I say the first one is VCA。

The three processes that arrive they execute in arrival order。And the second one ABC right。

 and A is longer than B and C， as you will see， so in some sense。

 B and C are wait longer than in the previous sequence because。They essentially did BMC Sha。

The third example is just showing you what happens when you do I。

It basically says if A makes any blocking calls。Once it arrives。

 then it has to relinquiate the CPUP gets to run and then if iOS is done when be complete。

 it can resume it。So a basically just jumps to the back to the front of the。

And it jumps to the front of the queue。The question that's a good question question is if a has relinquied the CPU B runs and A is again done with its IO as a gets to run again is it at the front of the queue at the back of in FCFS since you're scheduling in arrival order what you do is you look at all the jobs that are ready to run you simply start them in arrival order so A has arrived first in the system the fact that it went off to do IO didn't change that it still arrive before C so it still gets to run。

one other question is， let's say so B。😔，If A's IO takes like one second。

But these run time is  five seconds。啊。Is the CPU gonna。

To work on B for the entirety of the five seconds。And then only afterwards， does it finish up？

The question is if A does a short IO and B is longer process and is executing， does a have to wait。

 remember this is a non preemptive scheduler。So once something runs。

 you don't interrupt it so these IO is done be arrived first but sorry A IO is done A arrived first that be is executing and' preempted until it finishes so it will actually have to wait so you will still see that。

That's true of any not pre interesting。Any other questionsで。Let's move。

 so the next one is also very straightforward， this is called roundrop in scheduling as the name suggests in this case you are executing jobs in some round dropping in order。

All right， so you are basically going to have a queue of jobs， you execute one。

 it goes back to the end of the queue once it's times slice expires。

 then you on the next one and so on。So is this preemptive or non3emp？

that has to be preemp because the ground robin is made non preemp to degenerate to FFs。

if it is essentially snow crop。No。 So yeah， every job is going to be given a time slice， also1。

There's a duration for which when it's scheduled for execution， it gets to run。

If it uses its entire time slice， it has to go back to the end。

If it blocks in the middle of its time slice。That's going to go to the weight queue。

Then when it's done with this IO， then it comes back and enjoys them。

So that's basically what is going to happen in this case， so that's simple roundrabin scheduling。呃，当。

One issue with the roundrobin schedulers is how large at times slice to pick？

That's the only parameter really that you have in order of its scheduling that you can play with。

And depending on the time slice that depict， you will get different properties。

Let's you pick a small times。Now you are rapidly cycling between processes because each of them gets to run for a short period of time you switch to the next one and next one。

 so every process gets to make some progress for a little bit of time and then they give up the seat。

So that's good because it allows every process to make some progress。

 but in this case there are a lot of context switches switching between processes。

The thing that you have to remember is when you switch from one process to another。

 there's some bookkeeping that the OS has to do， it has to save the state of that process。

load the state of the next process and that means essentially all the registers have to be saved。

 a stack point or frame point or all those have to be saved somewhere to load the next process registers and so all of that incurs some over it。

It may be small， but it's not zero。So the more context riches you have in your system。

 the higher that bookkeeping tax you are paying in that system。

So more responsive but higher overheads。Now on the other hand， if you pick a long time slice。

 everything is inverted so now you essentially have fewer context switches。By definition。

 because you have longer time noises。But。each process gets to run for longer periods of time。

 but each process allows has to wait for longer to get a turn。

Okay so you are going to have this overhead so then the question is what is the right？Balance。

Should it be。Aponness to jobs and the amount of overhead you pay。

 so typically those factors are determine wash times led are going for a certain system。

It's good to keep the overhead small， so typically don't know the overhead to be too high。

The quantum size is chosen so that the it is less than 1%。Ex love。被关住。

So many systems it have 10 to 100 millisecond quantum space。Some might have shorter。

 some might have a bit long further， that is still by and large operating system。Any questionsです。

So there is an example here， which I'm actually go to skip。咱那ぐラ部。是谁组是。look at。

Homework later on because I just shows how the two work and then what waiting times you see。

 the only thing I want to point out is if you take the same jobs and you schedule them using FCFS and using roundrobin。

You calculate the rate times youll see that the rate times are actually going to be different in this case that non droppingbin has higher rate times for this arrival pattern because remember F CFFS can be highly variable in terms of its wait time doesn't mean that F CFFS is better just says that all of the jobs finish more or less at the same time。

 the wait times end up being higher for。But that's something you ought to keep in mind。

It's more fair， but then in some cases the rate time goes。So we'll come to the next one。

 whichs a shortest job first。Does anyone remember what this is？Its Jeff。Just orders the。Some jobs。😔。

 so you order jaws by the length。And as the name suggests。

 you pick the shortest one for execution next。Preemptive or non preemptive。改B一的了去年。

So the non preemptive version is called SJf。Preemptive version is called shortest remaining times so you can essentially time slice and at the end of the time slice you can again pick the shortest job the one that you are executing has just become a little shorter because it executed for one time life but if a new job is around in that period thats even shorter it you get to。

you SJF， but definition is not preemptive， but SrTF， which is its preemptive variant。

 can actually use times。所以盖他一个。What is good about。JF and what is bad。事事前。

So one downside of shortest job first is that it requires knowledge of the job length。Okay。

 where is that though？Yesす。Yes。Okay， you go only ex。No point when you ever started a process。

For a browser in says， how long are you going to run。Users don't know anything about job length。

 always doesn't know anything about job so you can't really know what job plans are。

 only thing you can do as was pointed out is estimate you can use past existing when job run plan for this month。

 so I estimate that it might run but that's an estimate it not to。So it is。

 by definitions since job land are unknown， you cannot actually implement this in practice unless you have a way to estimate that length is anaccurate。

Otherwise it's not practical。So that's the downside。What's the comp？Doive job scandal。また？申します。

Mored number of processes can be done。没有说一要质证。More jaw， short jaws finish。 but what does that do？

There is only policy。Do he was all。The first a is this perfectlyly optimal waiting time is the only policy that actually minimizes waiting time across enfr。

No policy that can actually do any better。It's optimal in terms of eight times。

Because it's actually preferring short jobs and getting them out of the system as quickly as possible。

 the way times that jobs here are going to be as small as you can make。

But that's actually the only reason we've。We study this policy in。

Operating system textbook says it has that property which you want in a practical implementation you cannot implement as JF or any scheduler that you want to implement。

 we would like to have that password as good。No wait times is a good thing。这です。

What if in case of SrRTF， if the tri quantum is smaller than the smallest job。

Finish right before that， we go back。So what happens in SrRTf？えた？S quantum is smaller than。来道德。

All right so let's take an example， let's assume time quantum1 millity。连到再 jo辉 in你 second。

Another job comes as 10 minutes， two job，5 minutes second job，10 minutes。

You're going to pick the shorter job。We pick the first one。You run it for a millisecond。要把我。是的那个机会。

So after the job finish of this， four seconds left。Since about a shorter time。So in SRDF。

 if there are no new arrivals， it basically turns into SJF because the shorter job gets keep getting even shorter because it's executed for some time。

 it'll run again。Its not this is not doing round roing。

 it's not going at the end of the queue just looking at all jobs and say what is the shortest job。

 shortest remaining time， which is what is the job。The time left on this job。So it weren't very fun。

I there time for them in measure SJF is not lay pill， it does not have。Im but S IF。

which actually hasか。That brings here。Okay last thing that is bad about SJF is it can lead to starvation of long jobs。

There has low wait times because it's referring short jobs。

 but if there's a steady stream of short jobs arriving。

 there's a long job that arrive sometime where it will never get to run because short jobs are on this。

And that's something you don't want in a practice。So you want to do two things。

 you want to get the low optimal wait times or approximate it in the practical policy。

 but at the same time you don't want any starvation。

So those are the true properties we try to actually extract。

S GF and see how to get it in a different。Give the example。

You will see that the weight times are the lowest for the SGF。都住点。Example。

So what we now do is start looking at what actually most OSS do is start with priority scheduling and then will make that a little more complicated variant of priority。

So let's start with what is priority schedule， that picture is actually a good one to。

money in a priority scheduler， you essentially do。Round Rob in scheduling。

 but you have multiple priority levels or multiple cues。

You do round robin in each queue but you start always with the highest priority。

 you do round robin in that queue when that queue becomes empty。

 you go to the next highest priority queue that is not empty you have to keep doing round robin and so on and so。

So if these are the only jobs in the system， don't your jobs are right， youll essentially moving。

W is highest for everything you do。L up that priority4， eventually those jobs will finish。

Then that was empty and youll do round cropbin at priority three。

 Eventually those jobs will finish and then one next off。 Okay， of course， there will be。

So it's called priority scheduling。 Keep in mind that in a priority scheduling。

 there are a few things to keep in mind。 it can have star problems。

If you' are a low priority job and there's always a high priority queue that is gone empty。

 a low priority job will not help。Just as an SJf， the longer job dental， so it can face starvation。

Is that something you wanted to do？Second thing you want to ask is who's going to decide the priority level of jobs？

Where is that going to come from。咋吃的。Wcom whos giving priorities to。

Brosses manager process manager for the same priority。

There are only two entities that can you prioritize user or the OS。Russia doesn't decide its own。

 because it is。it turns out that you can actually have both of these users can assign priorities to jobs is definitely assign priorities to。

Whenever you start a process， it'll have a default process。

You can actually use some commerce to assign priorities to your own jobs。

Anyone know what that is in Mu？So nice is a command that allows you to change the price so if you say nice process I and given integer that's a priority level。

 the OS will actually choose that to be a prior。Typically as the command nice suggests。

 it was put in place so that you could lower the priority of your job to be nice to another use。

And of course， you can increase the probability of your job as well。

So that's so users can change priorities on jobs the OS by default gives priorities and you'll see in some schedulers。

 they can change the priority dynamic。And then of course there are really more important things in the system that you want to run at high priority okay that includes the kernel itself system processes and so on that device drivers who run all of those and high priorities that use our processes run at slightly lower price。

Well that's how you're going to send priorities to it。

 but keep in mind youll still have transmission if you're going to do this。Question zone。

So now let's go to what is。A variant of a priority scheduler that incorporates some of the features of multiple scheduling policies will talk。

Name of this policy multi level feels that your MlFQ。 You might remember some details from。

このか making合意とで。Again， because this is also the policy that mimic this only。First and foremost。

 MLlFQ is a priority strategy。Simple priority scale。There has multiple priority levels。

Within each level， you are going to do round Rob。First property of M。Any you want answer。啊，そや。黄贷。

So you're talking about a property that essentially allows you to avoid star。

So what MLF2 does is if up。Pros is stuck in a low priority queue for a long time and hasn't gone to execute it' is going to bump it up one priority level saying maybe this job is starving。

 let's just increase it up the priority a little bit so that it might get a shorter。

But youll come back to the starvation problem at the end that's just put in place to avoid starvation。

Let's talk about what is there in the policy。😔，Interesting。anymore it。

So MLlFQ prioritizes IO bond processes。That's true。How does it do it and why does it do？

Process to stopm。这对万。It keeps it at its。えっとすぞ。I'm using its full time。But if process uses its full？

我说。で。So yes， so let me explain the MLFQ rule。MlFQ uses a simple rule whenever you schedule a process for execution and give it a time quantum it says what happened when that process finished its time slice。

 did it use its entire time quantum or did it block before its time quantum expire if it uses its entire quantum you are going to reduce the priority of the job。

If it actually blocked in the middle of a time quantum， when it becomes runnable again。

 you're going to increase the priority of the job by one。但是在们 left you。

Which allows you to change the priorities of the job as they execute。But the question is。

 why does it do？What makes this a good rule？Why could I not have done something else？

It not changed but other these adults。说完的哎。Okay so that's a good point。

 So if you look at what this rule is going to actually do to this processes。

 remember I said at the beginning there are two types of processes CPU bound and i。

So you should ask the following question if I execute a CPU bound。

Ex I actually schedule a CPU bound process on the processor of。

 what's the probability you can use its entire time slice？Hi， not asking for a number。

It's going to be high because by definition it's E bond。 it needs a lot of cycles。

 so it will likely use up its entire time quantum execute And the opposite is true for I bond job if you schedule an I bond job。

 the chances that it gives up its。The process of the those times the next path is going to be high。

 That is the behavior you expect to see for CPU B and Iowa。Now。

 if you say bump up the priority of any job that does not use a time slice by definition you're going to start favoring IO Bo jobs because those are precisely the jobs that are not going to use their time slice。

So the priority levels of those jobs is all going to us。

And the opposite is true of CPU bound jobs because they finished their entire time slice， okay。

 their priority levels are going to drop。As a result， if you have， let's say a four level。

 a four priority MLlFQ scheduler here over time you should expect all the I bond jobs to be at。

An Augustugus C and the top being high priority risk。

 and Augustugus seat will bounce off today at the bottom， which means they have the lowest priority。

So we are basically MLFQ is favoring。I有 borrow jobs or c burn。And we should ask。

 is this a good thing， what does this give us？His experience。あ。Use was。给是一份。The the same。See。

So you will have more responsive this。😔，To some degree， that is true。

 but all we are saying is the I Bo job is going to go back during I。这是不是。Users interacting with just。

 but guess what you're saying is also it as an artifact of what。当时费用应该有。Yes。明くしから。Anization。

You are increasing di utilizationtilization， and you're also increasing CPU utilizationization into something。

So just using。いにす。use it， increasing the。Iio utilization as much as。Also， decrease your overall。插到冲。

承啊。So that's true， to get that behavior because you're failing Iowa。

But the other thing you should realize is because you are sharing IO Bo jobs over CPU bond jobs。

 MLlFQ is approximating shortest jobs。Because our Iloberg jobs are actually the shorter jobs in the system If you go back to that picture I showed you at the very beginning。

hereSo you will see in that picture that because ionbound jobs are short CPU bursts。

 they look like short jobs so we're only talking about when they execute on the CPU and CPU bound jobs look like long jobs。

So by if you just start varying IOal jobs， you're essentially going to start approximating shortest job cost without requiring any knowledge of the job length whatsoever。

 you're not asked what the job length is of simply saying I'm favoring shortest short jobs which are in this case Iobound。

And how do you know a job is iob bond， you don't ask for a label or you see if you want an iO bond to simply observe its behavior。

 did it finish its quantum or not if you didn't you are an IO bond job with height。

Probability is your take。And you receive going job。

So what MLFQ does essentially as a score is an approximating shortest job first without requiring any job knowledge。

And by just assuming that short jobs are also the same as I bond jobs and long jobs are essentially similar to CPU bond。

Yeah question this also a decrease in our。Will it decrease the number of contexts which is in some sense？

MlFQ has other properties which also decreases the number of content which I didn't get into。

I can show you along with the priority level being different。

 each queue is also assigned a different time slice length。

The highest priority you gets the shortest quantum。

 the lowest priority you gets the longest quantum and this is okay because typically you' are running iO bond job in the short quantum you don't need to give it a long quantum and block immediately short quantum is okay and CPU bond jobs are sitting at the bottom they need to run for long periods of time it's okay not to context which frequently in that case because you are maximizing CPU utilization。

So you are actually going to by having differentiated quantum durations across queues or also reducing the number of context switches。

Because if you had the same quantum duration， would have a lot more context， which is a CPU bound。

There are lots of properties thrown in。proxi shortest job first。

 shortest jobs are the same as IO bond jobs， change the priorities to actually。

 if for which one is an IO bond which one is a CPU bond job。

 use differentiated time slices to reduce context switches so many things come into play。

All that works and that the thing that was mentioned at the very beginning which is you also are throwing something to avoid starvation because are lots of iObound jobs that keep getting activated the CPU bond jobs are being sit at the bottom get no CPU time or so to do this if you sit in a queue and do not get scheduled for a certain period of time you automatically get bumped up。

So eventually， if you ask any jobs that are starring， they'll rise to the top。

 they at least get one shot at the C。That same thing might happen there result。We pictureた。これです。

So at the smallest priority level， the time quantum is larger， right？

At the smallest priority and small meaning high of compared the jobs Yes。

 the the highest the bound jobs are at the。I priority learned here at the quantum is this morning。

So at the lowest priority level， time quantum is larger。So initially。

 when I job comes you will go to lowest priority。So what do you do in the system is when a job arrives。

 you started at nice2。Not at the， just to give it some benefit on the。

 we don't know what kind of job it is。Ass a feel boundary for the topic。Okay all new jobs。

 so that's the one thing I didn't mention， all new jobs start at a highestpar level because you don't know anything about that job when it starts。

So， that's。Essentially， multile can impact you。And then I talked about how your existing priorities。

Some exercise general to skip。And then talk about some others。OkaySo this also a talked。

 which is how do you avoid。Because here's one policy， which is a randomized response。

As the last one we are going to talk about before we switch to。What Minex does。

 I you say myex essentially implements MLlF cube。Yeah I just my remember something。

Let me talk about one more before we。It just very hard please。Does anyone remember this。

So lottery scheduling is a randomized policy。Where every job is given some number of lottery tickets。

And to decide which process gets to go next， you essentially run a lottery to take all the lottery tickets from all runable jobs and then you pick a winning one and the job that go has the winning ticket gets to run next。

So let's say you give one ticket to each job。So if there are end run jobs。

 you will get chosen with probability 1 over8。So our entry is hopefully you get to run。

 It's completely random。 there's no guarantee that。Soけ。Once time is not every end time is not。

 but on average or long periods of time that。NowWhat is good about this policy。

 why do we want to do things in a randomized fashion looks like it's doing what rounddrobin was essentially to。

Parts on why we care about large risk eating。It'small like a weighted random choice like so like you based on number of tickets one gets like the random probability is like weighted。

Yes， but also kind of。都不在。Given enough time nobody said you have to give only one ticket to each process。

I just made that up as an example you can give as many tickets you want you meaning the user or the OS to each process。

 so what lottery scheduling does is it allows you to control the amount of CPU time each process is going to get over some larger periods。

So very simple example if you are two processes。And one process has two tickets or the second process is one ticket。

Essentially the second first process is going to get two third of the CPU time and the first was to get a third we did round dropping in order r equal。

 you can't control how many times slices you get here you actually control its randomized but you do control by controlling the number of tick。

So so if you want to give a lot of CPU time to a process you should give it lot more lottery tickets。

 it's like increasing the priorities in some sense lottery tickets are acting like priorities but not theyre not exactly quality which should increase the chances that that process wins。

And guest to learn more often。So， here the。The interesting thing is by controlling how many tickets each process gets carefully。

 you can also control what percentage of the CPU time actually runs on the processor。Yeah you。

Because it is randomized。Longer periods of time， it all ends up being fair and fair here means you should get CPU time in proportion to the number of lottery tickets。

 that's a definition of fare。Mar then the new process gets。That's not。I mean， it pro as SJF。

 so like don't you actually have to know which are the short running jobs to give them the most tickets so it's kind of just as unrealistic as SJF？

I mean if you could to implement this， then you could properly。S这样。

So you're asking a question about the public good here saying I could give more lot tickets to shorter jobs and then you would approximate S jail because they are get chosen and working with。

我真的 to。To do this， you dont need knowledge or whether it's a short job or IO job and so on。

 and without that knowledge you cannot accurately give the number。

 but sure if you knew that you could。それな。电双 buses to。But that's not only reason you want to edge。

 you can just say this there are two jobs。 I just need this job to run more because you can。名字。还多是。

more logic。Independent or whether you're IO bound or not， you want across， if you bond jobs。

 you can partitionition the CP。By across process。W's the one say 63， 66， 33？So， here is， essentially。

Examples which。けたでもか。Short jobs are being given 10 tickets。

 but you need to know what short jobs are I was pointed out。You do long jobs get one ticket。

 is one charge or one long job。A short job is going to essentially with them over 11 times。

L job guys speak one。That91年内。And then you can work out on。umb。

 you will see that by earning the number of audit three tickets。

 you can actually vary how much if on each job。Very similar question。や体がす。

The question is when thing normally。😔，A job， I never specified。If it's short long as a user。So。How。

How are you going to be able to give one ticket？That's a good question The question again is you don't know whether a job is a short job or a long job okay and then how do you decide based on if you didn't know how much it is do so that's a valid criticism of this policy but that's not how it actually gets used in practice you're not trying to say long jobs get more tickets and short jobs get fewer tickets。

Vice ver what you're actually doing is you're taking。Some jobs， they may be all similar jobs。

 not short or long and trying to say this job should get this much time and their other jobs should get this。

I guess when as a user you run a program， you don't even， I least I can't figure out the time。

Say give this process some warm priority。But it's one happened the system。So as a user。

 you're never asked to assign priorities to jobs， yes， in Uni there is nice， but nobody uses it。

Uly but same history of lottery scheduling， you are not expected as users to say。

 and I'll mention where actually things like this get used。

So they are actually used in many other kinds of cigarette， like virtualization is a good example。

If you create multiple virtual machines on one physical machine。

 you can use variants or lottery scheduling to say this virtual machine。Has more jobs running in it。

 I want to give it 60% of the total CPU cycle this one needs 30% so you can essentially partition your C This is not trying to distribute when IOCQ1 it's simply saying I want to give X percent of the CPU to this job How do I do that that makes sense so that's what it's actually used up this example is not really the way it gets used a job。

やてて欲しい。So there are deterministic versions of this which allow you to give something called a weight。

 weight is equal to equal into the number of lottery tickets and those deterministic versions actually guarantee that every time slots some fraction actually goes depending on the weight to a certain this is our randomized version is very easy to understand but then deter which is slightly harder to teach。

But they do exactly the same thing。 and that's basically what gets used in many。

Virtualization frame of they get using routers to allocate bandwidth that's another scenario。

 So if you are two users， one user needs more bandwidth ors pay for more bandwidth that's how you're actually going to get allocated if your a cable provider says you can pay for 50 megabits per second or 100 megabits per second they got to allocate that capacity to you。

Larger network， These are the kinds of techniques that。we' keep that aside for now。Go back to。

Scheduling and augment systems， so。In hall of what I just said。

You can now go and look at what is actually happening in。

So Linux is essentially implemented because it's meant for teaching purposes。

 it essentially does what you learn in a text it basically implements MLF everything I said about MLFQ and some other concept is actually what Linux does that's not true of more general purpose operating。

The nuts does not actually do anything close to what。Anything we learn here， it has its own thing。

Are there one constant time scheduling and things of that sort and when you the multiproces scheduling things get even more complicated if didn't talk about multiprocessors at all but Linux is come back and nice to understand what it simply does is MLL。

So as I said， when is the schedule removed？All of what I said earlier is still true in the process existss。

 you got invo scheduler and say what gets to them。Ain blocksx and Io， lox and lo， seapho。

 who are to invoke the skin。And then when a process。

 new process gets created when an interrupt occurs or when a quantum expires also the schedule。

Everything I said before still true。This is essentially a picture that shows you the scheduler in Min。

 it's a 16 level MLFQ schedule。16 priority levels。Priity delay go from 0 to 15。Zero is the highest。

 15 is the lowest， so higher numbers are actually lower priorities。It is opposite to how we think。

 but that's how Unix does it， so they're not directly to nice priority level。InN。

 you can say nice and， give it priority for。 it will go to the fourth。对。其他。说。You've been there。

 see 16 layers sating back。诶 some。Priority levels are used for。Scheduling over tasks。

 some are used for scheduling user processes。T tasks run at priority level zero。

 the only two things that run there。That's our system task and the clock task。

 and we come back to the micro kernel， youll see again there are two key components in there。

 it is a system task that essentially implements all system calls。

And there's a clock task that is implementing time and there's also some IPC that's happening。

 So all of that is in the system。So that's running at the highest priority。

You will see that device drivers and some of the system processes we talked about find server word process manager。

 virtual memory manager， device drivers that essentially run。A priority level one through4。

Still higher than all user processes。那 user bus the season。According to the book。

 there's started at7。We five and6 are used。ワば。So they start at seven and go all the way up to 14。

The I task runs at 15。The id task is essentially a task as an infinite loop when there' is nothing to schedule you will run the。

it's the lowest， it's always the lowest priority task that dash to run there nothing else to do because you can't really give the C。

Give this if in the market。这番。是多。总で。Well。With that in mind， all of what I said about。IO Bo job。

 CPU Bo job that's still true， but only for user level processes you are checking and you run for a quantum。

 did it finish third quantum did it not bump its priority level one up or one down based on。

The priority of the territory task is not going to change。It's always going to be at zero。

 it doesn't matter whether it uses just quantum or not， it is statically bound to priority zero。

 same issue of some system level processes。As far as what the book says。

 I will verify the code actually because sometimes there's discrepancy between most and the code。

 the book says that system processes are being differently from user level costs。

Which means they can be bumped up or down， but I believe that not all system processes are treated that but some are actually print to prop。

But some others might be actually floating up or down like any user process。

So that's the picture you want to keep in mind。As for many at some point you'll start mucking around on the schedule so you need to know that's how it actually looks victorious。

Yes my。You will see that each Q or each level is implemented essentially as a Q of task linked list。

2%。Harry essentially。Sly link， not a doubleubly link a single link list。

 and there's always two pointers1 pointing to the head of the Q1 pointing to the tailor。

I had all the queue what at the beginning to take a task there and then if you want to put it at hand end you have to assign it to something。

So they said priorities are assigned with nice。Since this is the first time so your heard of nice。

 go to any Linuxux machine or Mac and type nice or man nice and see what nice can do and change a priority of a task。

50 and the 15 system processes。刚个。是是。の。So。New三年さ。It's a good question。

 so this question is does nice in the priority or does it actually allow it to change？

Yeah this actually the parents on the horse。Because you are doing a male leftQ schedulecheduling。

If you noise it and stuck it at some level， you are not good。So what actually happens in most real。

This is also most general purpose operating systems is that as a concept of a priority。

 as's a concept of where you are in MLF to cu there two different things。The priority level kind of。

な女と性。How you start off and eventually you got allowed to drift up or。

I think that the lib of nice how collapses by any of this。Second globe。

a few more things I want to say is well the other thing you should know about Linux is this whole restart task。

 which is essentially the way your world in the CPU scheduler。

But the restart pass runs every time two different things happen there's an interrupt and there's a system problem and the quantum expires。

 you see that there's a flow charge that you can ignore from this point in time。

 but essentially many things essentially more saying restart restart new。5。6。start a new task。Ex。

 So eventually that task will invoke the CPU scheduler and say a system call has just finished or intrapre has just finished quantum measures expire。

 What should we do next Okay so that's the entry point of how the CPU scheduler essentially gets in。

So that's an implementation detail， but something you should know。Now。

 as far as the scheduler is concerned。The implementation， according to me。

 at least is not as clean as one would like， it is spread across multiple files and multiple components。

It's not hard to understand， but they didn't have a scheduled do C。

 which had everything you needed to remember about this。Heres a spread on multiple things。

The restart process is actually not process of starts is a main do seat。

And that main actually also has all of the cues that I was talking about。

 the heads and tails of all the cues of the MLF you scheduler can be found in life。咁系。

So the aqueuing and requeuing of processes is actually done in。被到C。这楚我也是。

then there is a function called SC which essentially decides which Q should a process be added to。

 that is where the priority levels are getting changed。

And then there is another function called peak process okay thats the one that's actually deciding。

 okay， this is the process that is going to go next essentially doing a priority scheduling at that point to take the I priority non emptyQ。

 take the head of their Q schedule that process。So it's kind of spread out a little bit。

 But once you get the hang of it is not。I the salary。是3个。

Is this happening in the curtain or the process my。

 some of this is actually happening in the process。

But not everything some other things that happening to。just sound to be changing。

You can implement some aspects of it in the process。😔，有的こし。

So that's the lay of the land as far as how the city。You'll come back with this in the next。就是在。

Implementation。And how maps are the resource。詳シぞです。Any questions on the。

Did you see the post I made about Sc？Lied laundry skin。什么情况在到。

So keep that in mind so you can essentially have you。まスクライフさんと。なだ。我国和新的人证。On Thursday。

 we talk about the process manager。大変し。