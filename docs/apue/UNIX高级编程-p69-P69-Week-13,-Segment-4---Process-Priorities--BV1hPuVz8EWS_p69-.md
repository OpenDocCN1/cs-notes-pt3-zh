# UNIX高级编程-p69-P69-Week-13,-Segment-4---Process-Priorities--BV1hPuVz8EWS_p69-

Hello and welcome back to CS631 Advanced programming in the UniX environmentvironment。

This is our fourth video segment on the larger topic of how to restrict processes。In our last video。

 we looked at restricted shells， shrus and jails。In this video。

 we'll go back to a more process centric view。Even though we are able to restrict with fine granularity。

 which users may execute which commands and by way of file system permissions extended or otherwise。

 or even through the use of a ch or jail， which filess may be accessed or which processes may be viewed。

 we are still facing a number of problems。We are still using the same resources。

 All software contains bug and humans tend to misconfigure things。

 thereby oftentimes allowing a process to do things that they shouldn't be able to or to interfere with the normal operations of the system。



![](img/d692eeebd2915e618af745931c87fafe_1.png)

All processes， even those running in jails， effectively compete for these same resources and may continue to run forever or consume certain resources to a degree that would rather it not。

We've discussed some ways to restrict the given process research utilization in week 6 segment 5。

 where we looked at the getar limit， setar limits this course， and the U limit shall build in。

The use of resource limits brings us back to a significant and important concept， self restriction。

That is， the process can voluntarily restrict its own usage。

 such that it itself cannot later regain the privileges it previously had。

This applies equally to any children this process may create thereby by allowing you to create more confined processes or process groups。

One of the limitations we had observed here was the total CPU time and seconds。 That is。

 you may not want to allow certain jobs to keep hogging the CPU， but。If we didn't have this U limit。

 would the process just sit there and not let any other processes get the CPU。

To better understand how processes may compete for CPU cycles。

 let's briefly take a look at how the scheduler works when placing processes on the CPU。



![](img/d692eeebd2915e618af745931c87fafe_3.png)

You've probably seen similar illustrations from your basic operating systems class。

 but to clarify our understanding of the resource limitations we discuss here and still useful to rehash this topic real quick。

In an naive roundundrobin Schr， you have a run queue of processes and are waiting for CPU time。

And the scheduler picks off the next job from the run queue and places it on the CPU。

But a job may not necessarily run to completion and instead request some I O。

 As you mentioned before， this is very slow in computer terms。 And so while we're blocked for I O。

 The scheduler may move for a job into the weight queue。



![](img/d692eeebd2915e618af745931c87fafe_5.png)

This free up the CPU to handle another job and so。The scheduler picks the next job of the run queue。

Pit 2，2，3，4， in this case。 And lets that job have the CPU for a bit。But even if Pit 2 to3。

4 does not request I owe or otherwise ends up being blocked， It might still or run to completion。

If we simply let any job get the CPU and keep it until it's done， then it block all other jobs。

So instead， the scheduler preemps the job after some period of time and places it back into the run queue。

 giving the next job a chance to run。Now with process 8723 on the CPU。Process 1，2，3。

4 may have finally completed the IO it was blocked on， so it gets back into the run queue。

But now it's all the way at the end of the queue and we'll have to wait until all the other jobs ahead of it got their slice of CPU time before it gets a chance to do some work again。

This trivial round dropping approach also assumes that all jobs have equal importance and should always get the same amount of CPU time。

 But in reality， we sometimes have some jobs that would like to be preferred over others。

Certain system jobs or kernel tasks， critical for the OS to run smoothly should probably not be preempted for unimportant long running processes initiated by normal users。



![](img/d692eeebd2915e618af745931c87fafe_7.png)

So let's try again this time， in addition to our run queue， we let each process have a priority。

If all jobs have equal priority， then the scheduler can pick the first job of the one queue just like before。

But let's suppose different jobs have different priorities。In that case。

 the scheduler will pick the job with the highest priority of the run queue and place it on the CPU。

In this case， there would be process 8，7，2，3 with a priority of 15。With process 8，8，3。

3 being up next。Note that as we placed process 8723 onto the CPU。

 we are increasing the priority of all waiting processes。

This ensures that any process that waits for a long time will eventually have a high enough priority to get picked up。

Now， if process 8，7 to 3 gets blocked， waiting on IO， for example。



![](img/d692eeebd2915e618af745931c87fafe_9.png)

Then it gets placed into the W queue while the next job process 8833， gets the CPU。

 and the other jobs in the run queue have the priority incremented again。After some time。

 process 8833 gets preempted， but note that when it gets placed back into the run queue。

 it has its priorities slightly lowered since it just had the CPU。And process 1 to 3。

4 now gets the CPU。If process 8，7，23 now completes its Io。

 it will then get placed back into the run queue， but has kept its priority the entire time since it never got a full cycle on the CPU。

So this way， the job that was blocked by I O now has the highest priority。 And when process 1，2， 3。

4 gets preempted。It gets the CPU。Now， this is a very simplified view of dynamic priority scheduling。

 but I think you get the idea by allowing for priorities。

 we can ensure jobs are scheduled according to their needs and by dynamically adjusting the priority based on CPU cycles used。

 for example， we can avoid starvation of even a low priority job。Now。

 there are many other scheduling algorithms， but for us。

 this is a good enough approximation to now take a look at how process priorities are adjusted。



![](img/d692eeebd2915e618af745931c87fafe_11.png)

For that， we have the get priority and set priority system calls。By default。

 every process gets a priority of zero， neutral。Which specifies whether you are interested in the process priority。

 the priority of a process group or that of all users processes。For multiple processes。

 get priority will then return the highest priority of any of those processes。

The default priority of0 is neutral， numerically lower priority values cause more favorable scheduling。

 higher values imply less favorable scheduling。This is a bit confusing。

 since normally we might consider a higher priority to lead to more favorable scheduling。

 which is why we differentiate between the actual kernel priority and the process niceness。

As we will see in a few minutes， we can adjust the priority of a process using the nice utility and the logic mapping here makes a bit more sense。

 The nicer a process is， The more it is willing to let other processes have the CPU。😊。

So a higher number means you're being nicer， so receive a lower kernel scheduling priority。

The value you can set here ranges from negative 20 to positive 20， although on some Uni versions。

 you can only be nice up to a level of 19。A value of 19 or 20 will schedule a process only when nothing at priority less than or equal to 0 is running。

Similarly to how we handle U limits， our process is only able to raise its niceness and can never lower it unless you're the super user。

We'll see examples of this， in a second。Finally， note that if our nice value can range from negative 20 to positive 20。

 the negative 1 is a valid return value for get priority。

 meaning we can't just rely on the return value to identify and error。For this reason。

 we need to explicitly set Erno before and then check Erno after we call get priority。

Let's see all of this in action。

![](img/d692eeebd2915e618af745931c87fafe_13.png)

When we run up time， we will see not only how long the host has been up。

 but it also includes the load averages and three numbers。



![](img/d692eeebd2915e618af745931c87fafe_15.png)

These three numbers show the load average across the last1，5 and 15 minutes。

 with the load average being defined as the number of processes in the run queue averaged over that interval。



![](img/d692eeebd2915e618af745931c87fafe_17.png)

Here is a trivial programme to print just the load averages。



![](img/d692eeebd2915e618af745931c87fafe_19.png)

The three numbers printed by our program roughly matched will uptime report as the averages are calculated in real time。

Okay， so now let's try to generate some busy work。

![](img/d692eeebd2915e618af745931c87fafe_21.png)

A silly little script that will keep our CPU busy for a bit。Here， were simply looping around。

 subtracting numbers round and round。If we run this。

And then take a look at the output of top in another window。

Then we see our busy job up here as the process ID 1361 with a kernel priority of 28 and the niceness of 0。

When our runnable jobs decrement。We will find that this script completed。Okay。

 now let's run a few instances of the script in parallel to observe how our CPU priorities are assigned。



![](img/d692eeebd2915e618af745931c87fafe_23.png)

I just run four instances in succession， waiting for a bit in between。



![](img/d692eeebd2915e618af745931c87fafe_25.png)

We then expect these four jobs to complete in the same order they were started， A， B， C。



![](img/d692eeebd2915e618af745931c87fafe_27.png)

And then the。

![](img/d692eeebd2915e618af745931c87fafe_29.png)

Now， in our other window， we should see these jobs show up one by one。

 with each having the same nice level and approximately the same kernelnal priority adjusted on each update as they get on the CPU and are preempted。

As they complete， we will see the order we had expected。First， A， then B， then C， and then D。

So now let's try to alter their priorities after we kicked off the jobs。



![](img/d692eeebd2915e618af745931c87fafe_31.png)

![](img/d692eeebd2915e618af745931c87fafe_32.png)

We can use the nice command to specify an initial priority。

Or we can use the re nice command to adjust the priority of an already running process。



![](img/d692eeebd2915e618af745931c87fafe_34.png)

So let's use Reise。

![](img/d692eeebd2915e618af745931c87fafe_36.png)

But for that， we need the process ideas of our jobs。So let's print those out when we start them。



![](img/d692eeebd2915e618af745931c87fafe_38.png)

![](img/d692eeebd2915e618af745931c87fafe_39.png)

![](img/d692eeebd2915e618af745931c87fafe_40.png)

Okay， now we have job A with process ID 2，1，9，7， B with 1，8，6，9 and so on。



![](img/d692eeebd2915e618af745931c87fafe_42.png)

Let's adjust the priorities so that we give process A the highest nice level to any。



![](img/d692eeebd2915e618af745931c87fafe_44.png)

Process D， a nice level of 15。Process B， a nice level of 5。



![](img/d692eeebd2915e618af745931c87fafe_46.png)

En leave Pro C at the default。Now we can observe our jobs over here again。

We see the nice level reflected here and the current priorities adjusted accordingly。

As the jobs complete， we should find another order of termination。Now， C was first to complete。

Then B。Then D and A was the last。This reflects the nice levels we assign to each process。

 showing that the higher priority drops did indeed get the CPU more and were thus able to complete faster。

Allright， now let's take a quick look at how nice might set the priority。



![](img/d692eeebd2915e618af745931c87fafe_48.png)

Here we have a program that prints its current priority。Then tri has had its own priority。

To the value provided on the command line。Then， print out its new priority。

And then tries to set priority to that， which had had a program startup。Finally。

 it again reports its current priority and exits。Let's run it and request a nice level of5。

We start out with a default， nice level 0。We're able to set the new nice level since we're raising our niceness。

 lowering our priority， or being nice。😊，After that， we try to set our priority back to 0。

 but that fails。And so our priority remains5 throughout。

If we run the same command with super user privileges。

Then we are able to lower our niceness again from 5 back to our initial 0。

What happens if we start out being really nice？ Let's try。Our initialized level is now 10。

 So trying to sell it to 5 will fails， and that would be lowering our niceness。But we can， of course。

 still be even nicer and lower our priority further。Can we start out being not nice at all？

 Our default value is 0。 Let's try out with negative 5。That fails。

We can't lower on nice level below 0， but note that nice lets us still run the program now with a default priority。

 While， of course， the super user can start out with a lower nice value and then adjust as they like。



![](img/d692eeebd2915e618af745931c87fafe_50.png)

Okay， let's take a break here and summarize。

![](img/d692eeebd2915e618af745931c87fafe_52.png)

As mentioned before， a process is able to voluntarily self restrict the resource utilization。

This applies to U limit resource limitations just as it does to CPU scheduling priority。

We can adjust our CPU priority， our niceness using the set priority system call。

Or using the command on utilities， nice and re nice。

This can be done for individual processes or process groups。Unlike in the human world。

 once you're nice， you can't decide to be naughty again。

This follows the principle that we can lower our privileges。

 but not raise them again once lowered with the intent to allow a process to intentionally shed some privileges so that it or its children cannot abuse them at a later point。

Finally， while we can control to some degree how often we get CPU cycles by being nice。

 this is no direct effect on which CPU we are scheduled if the system has multiple CPUus。

And stands to reason that on a multi CPU system， you might want to keep one CPU for system processes。

 for example， and farm out all the other jobs to the other CPUus。

We'll talk about how to accomplish that， in our next video。Until then， thanks for watching。



![](img/d692eeebd2915e618af745931c87fafe_54.png)

Yes。