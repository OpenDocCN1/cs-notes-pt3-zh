# 【全集 附课件】慕尼黑工业大学 C++系统编程 中英字幕 1080P p13 Lecture 13 - C++多线程 -BV1QTzjBFER2_p13-

Welcome back everyone to another lecture of the systems programming and C++ practical course in which today we're going to talk about multithreading in C++ So of course we already had previous the previous lecture last week which talked about multithreading in general。

 how it's implemented on modern hardware， what kind of pitfalls there are what kind of specifics we have to keep in mind when talking about multithreading independent of any programming language and today we're going to take this knowledge and we're going to see how。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_1.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_2.png)

We can actually make use of the facilities that are provided by the CPU in C+ plus what are the language features to do this and so on。

So， of course， on a high level， there's nothing too surprising。 C plus plus， of course。

 allows us to run multiple threads simultaneously and of course。

These threads use the same shared memory， so we've seen this quite early during this lecture that we have this virtual address space of a process and all threads that we may start within such a process share this address space so they can of course access the same memory location and they will both see provided that we take some care。

 they will both see changes to this memory location that are made by the respectively other thread。

So this is the classic share memory model for multi threadreading N C++ allows us to make use of this。

Of course。Immediately after we are done being happy about this and we can start thinking about all the problems that come with this and the major cause of this problem is of course。

 that precisely multiple threads can access the same memory location。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_4.png)

So what is perfectly fine is when multiple threads read from the same memory location。

 Nothing exciting is going on there。 They're all going to see the same contents of our memory memory location and we're happy。

 But as soon as we start doing anything else， but reading from the same memory location。

 we get what is called a conflict in C plus plus So this means that any combination of one or multiple threads reading and some other threads writing the other way around someone writing and someone is reading or both or multiple threads writing to the same memory location are called conflicts。

😊。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_6.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_7.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_8.png)

And all of these conflicting operations are only allowed when the threads are synchronized in some way。

 So this means even if you have the situation that only one thread is writing to a memorial occasion and all other threads are reading。

 you'll still need some sort of synchronization。😊，To make this well defined behavior。Of course。

 and this is something that you may remember from last week's lecture。

 this synchronization can be done with mutual exclusion or atomic operations。

And we're going to see today how this is implemented in C plus， plus。

And just to stress this one more time， any unsynchronized access that has a conflict which is also called a data race。

 any deadlock or any other of the many potential issues that you can run into when using threats are undefined behavior in C++ and this once more means that any conflicting operation。

 anything that is not exclusively reading from a memory location has to be synchronized in some way。

So we cannot simply take our single thread at C++ code and slap some threads around that and then expect it to work。

 we have to do some additional work to achieve this synchronization that is required but of course today's lecture will spend a great deal of time talking about how exactly we can achieve this。

 but before we can talk about synchronization we have to talk about threads first so let's take a look at how we can start multiple threads and use those within C++。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_10.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_11.png)

So in this standard library we have the very useful thread header which defines the class STD thread and this class is our main way to use threads in C++ programs because this class is platform independent so the standard specifies how this class has to look and how it has to behave and then the underlying implementation of the C++ standard library can adapt to the different platforms that your code might run on but we always use STD thread and we don't have to worry about that。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_13.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_14.png)

But because threads are such an invasive feature， it's still possible that some additional compiler flags are required to actually enable this threading functionality and of course this once again depends on the actual underlying implementation of the standard library so here our recommendation is to use CMake to determine these flags in a platform independent way so that also on the build system side you don't have to worry about portability。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_16.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_17.png)

And just for completeness， if you're using GCC or clang on Linux。

 this flag will usually be the minus P thread flag， so just for those who are interested。

 this means that usually on Linux the threading functionality in C++ is implemented using the P threads library。

And for completeness。If you do want to include threats in your own project。

 there's a very brief C make code snippet down here that shows you how to do this。

Compilile a flag detection in CMake。 So all that we do is we call find package with the threads package at our executable as usual。

 and then we have to add to the target link libraries this threats target here。

 So for now you can just copy and paste this code snippet。 But of course。

 I think it's next week we're also going to talk about CMake in a little bit more detail and specifically we're also going to see what exactly these find package and target link libraries function calls in CMake do。

 But for now， as I said， just take the snippet， and it should work provided that we didn't include any typos in here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_19.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_20.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_21.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_22.png)

Now of course， getting the threats library to work is maybe the most uninteresting part of it。

 how can we actually use this STD thread class？

![](img/b4146116ad47eca7d2a49f6d5d93cb13_24.png)

So the constructor of this STD thread class。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_26.png)

Usually starts a new execution thread and the syntax of this constructor simply takes a function and a veryadatic list of arguments。

 so this is a little bit similar for example， to the syntax of and make unique where you also have this variableable list of arguments that are then simply forwarded to the constructor here in the case of threads and the arguments that you specify are simply going to be forwarded to the function that you pass here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_28.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_29.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_30.png)

AndThen this function here will be invoked in a new thread with the arguments that you provided。

 and then once your function F returns， through some means， the thread will terminate。In some cases。

 it's useful to not immediately start a thread once you construct an STD thread object and for this。

 you can simply use the default constructor， which will create an empty thread object。

 So a thread object that simply does not have an associated thread yet。Once we have started a thread。

 of course， and this thread will run for some time。

 do some useful work hopefully and eventually it will terminate。

At the end of your overall program execution， you have to call the member function join on this thread object to potentially wait for a thread to finish or simply make sure that the thread has already finished。

 So this is。Even if you know that your thread has already finished by the time that you call join。

 you still have to call join to explicitly merge these separate execution threads once again。

 so join must be called exactly once for each execution thread that you have started through the constructor of STD thread and this join call must happen before the STD thread object itself is destroyed because when the deor of an STD thread is called and the join function was not invoked previously。

 then your whole program is going to be terminated So this is a potential source of bugs。

 but luckily it's rather easy to spot these bugs because then your program will simply terminate if you forgot to call join。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_32.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_33.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_34.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_35.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_36.png)

So let's take a look at an example how this could actually look in code and what try to establish some intuition what's going on here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_38.png)

So first of all， let's take a look at the code snippet on the left here。

 So let's just assume we have some opaque function food that takes two arguments and does some kind of work and we don't really care about what this is for now。

 Of course we have to include the thread header to be able to use STD thread and then we construct two threads here using the constructor syntax from the previous slide。

 So first in the first version here we simply pass the function and then two arguments for the A and B parameters。

 But is also possible， of course， is to pass a lambda as the function and then because our La lambda here doesn't take any parameters we don't have to pass any parameters to the SDD thread constructor But of course within the lambda here we can then do essentially whatever we want。

 including calling our full function here with some different parameters。

 So this is just to illustrate that you can use both functions with arguments and lambdas as the arguments to the STD thread constructor。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_40.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_41.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_42.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_43.png)

And then once we have started these two threads， of course， the main function also runs in a thread。

 the main thread， and we could simply call fo with yet another set of parameters here。

 and then finally we call join as we've just learned that we have to before the main function exits here。

So what is going on here。 for that， let's take a look at this figure on the right here where we have our three threads。

 So the main thread that always runs that's implicitly instantiated and that executes the main function here So we start executing our main function and then we invoke the constructor of our SDD thread object T1 here。

 and at that moment that we invoke this non-deult constructor another thread is started。

 So at this instant in time T1 is started and it immediately begins executing whatever function we passed here。

 So in this case this is going to be full called with parameters 1 and 2。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_45.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_46.png)

So here in T1 fo is heavily executing away， but of course simultaneously this is the whole purpose of using threads。

 the main function also continues executing and the next statement in our main function here is constructing our thread T2 and here of course the same thing happens at the moment in time that T2 is constructed here。

 another thread starts which is going to execute our fu function with parameters 3 and 4 course this is very slightly inaccurate here because in reality this thread T2 here is not going to just execute the fu function。

 but of course the entire lambda function that we passed here。And then finally。

 once this constructor also returns in the main thread。

 we invoked our fu function with them  five and 6 as parameters。

 so this is also running in the main thread， then all the while simultaneously our threads T1 and T2 are also working on their invocation of the F function。

Now， at some point， our full function is going to return。 And at this point。

 the threat will the threads will terminate。 So this this can be seen for T1 here。 for example。

 where at this point in time。The execution of fo is complete， and then the thread terminates。

 the same happens for fo with a three and4 in our thread T2。 but also as we've learned。

 and this is indicated by these dash lines here， and we still have to called join on these threats and as long as we do that。

 the corresponding thread object is going to continue to exist in some very。

 very inaccurately in some kind of limbo state until we actually have called join and of course。

 these join calls here once again happen in the main thread。

 So those only occur after our execution of fo in the main thread has finished which is at this point in time and note that this is quite a bit later then then it happened in T1 and T2。

 So here T1 and T2 have already been inactive for some time before our fo invocation in the main threat terminated。

And then we finally call T2 point join， so at this point the thread is actually cleaned up and then subsequently the same for T1 here and the thread is cleaned up and then finally once these two join calls have finished。

 we are back at having one single main thread that continues executing， of course。

 until the main function returns and our entire program terminates here。

Are there any questions about this high level view of multi threading？I see some typing。

 so let's wait for what is presumably a question。Can a city thread be moved， Yes， it can。

 And we're going to see that in just a couple of slides。Any further questions。Looking good。 Alright。

 So then。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_48.png)

Let's move on just a very brief example to illustrate that we have to call join on a thread。

 So here we have some function that safely prints something to see out and we simply invoke this function in a thread T1 we call T1 dot join So everything is fine here we called T1 dot join before the thread object here went out of scope and was destroyed but subsequently we do we start another thread and then forget to call T2 dot join and at the time of destruction of T2。

 So when it goes out of scope here our program is going to be terminated because of course we forgot to call T2 dot join here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_50.png)

And returning to the question that we just had， SDD thread is in fact， movable。

 but it is not copyable， and， of course， this also makes sense。

 copying an SDD thread would almost always entail that we would have to copy a thread that has already started executing some kind of function。

 and the semantics of this would really be ill defined。

 So the only thing that we can do with SDD threads is move them。And when we do move an SD thread。

 this transfers。All resources associated with the running thread and then only the moved to thread can be joined and be moved from thread will become empty。

 so the move from thread will then be in the same state as a default constructed thread。

 which is simply not associated with any actual execution thread here。

And to give you an example here， once again using our Sa print function， we start a thread T1 here。

That is。That is I'm executing the safe print function here。

 We then move it into another thread object T2， and then finally call T 2 dot join here。

To make sure that the execution thread is joined and of course， we don't have to call T1。

 join because we just move from T1 and T1 is going to be empty。

Another question is whether joining an empty thread is a problem。

I am not 100% sure it might be there is a function thread dotted joinable。

 which tells you if you can invoke join on a thread object。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_52.png)

And I suspect that calling join on an empty thread might be undefined behavior。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_54.png)

But this is something that we would have to look up in the reference documentation to be certain。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_56.png)

Now， moving on。Something that's also quite useful is because STD thread is movable。

 we can use it in standard library containers and in particular we can use it in an SDD vector。

 which quite frequently is going to be rather useful if we want to set up some kind of thread pool with a varying number of threads。

 maybe the number of threads should be determined by the number of CPU cores in our system。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_58.png)

Then we can simply create an STD vector of STD threads and then push thread objects into this vector。

 have them do something。And then finally， of course。

 remember to invoke join on every one of these thread objects within our STD vector。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_60.png)

Finally。There is a number of useful functions within the thread library that you can of course use within your multithreaded programs。

 There are functions for stopping the current thread either for a given interval of time or until a specific point in time。

 there's the possibility to have the operating system schedule another thread by using the yield function and sometimes it's useful to to get the actual actual operating system specific underlying identifier of the current thread and for this we can use the get underscore ID function so just for reference on Linux if the threading implementation of C++ uses P threads this is going to be the identifier returned by the P threads library when the C++ implementation created the thread and of course we can then pass this identifier library functions of the P threads。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_62.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_63.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_64.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_65.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_66.png)

Library to use some platform specific functionality that may not be exposed in the C plus plus interface。

 Of course， always， as always， remember， if you do this and then you lose all the portability of using SD thread because once again。

 you have tied yourself to the P threads library in the implementation of3。So with this。

 our high level overview of。Threading and C plus plus is already complete。

 so we essentially can do everything that we need to do in order to be able to have multi threading within our programs。

 We can start threads。 We can have them do some kind of work。

 and we can then join several threads of execution again。 Of course。😊，At this point。

 we cannot really do a lot of useful things because we haven't talked about synchronization yet。

 so our threats cannot communicate with each other。

 And this is what we're going to talk about in the remainder of this lecture。 So at this point。

 I think it's a good opportunity for questions about the threading part。

 if there are any before we move on to the synchronization part。

No questions coming up So let's move on to how we can achieve synchronization between threads and the must straightforward way and this is also something that you may remember from last week's lecture。

 of course， is mutual exclusion where we define these critical sections that only one thread at a time is allowed to enter and in order to achieve this we have some sort of mutex object and every thread that intends to enter a critical section first has to acquire a lock on this muttex object and when the thread leaves a critical section we release our lock on this mutex object and of course when we try to acquire a lock on a muttex that is already locked then the thread has to wait until this lock was released。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_68.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_69.png)

So this is something that we already talked about last week。

 so just to reiterate here what the highle programming model would be。

 usually we have some kind of resource that we want to access from multiple threads simultaneously usually this resource is going to be a class and then this resource that requires protection from potential data races owns a Mutics object of the appropriate type and any thread that intends to access this resource has to acquire a suitable lock on the Mus before performing this axis and has to release this lock after completing the axis。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_71.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_72.png)

And usually to give a little bit more detail， locks are simply acquired and released in the member functions of the class that we intend to protect from data races here。

 so usually you see a class a mutix member and then within the member functions you see code to acquire and release locks on this mutticix object。

Of course， this is still very high level how does this actually look within C++ and for this we have several useful classes in the Mutex and the shared Mutex headers that are defined in the standard library。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_74.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_75.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_76.png)

So here we both have muts objects and some helpers to acquire and release locks on these muttics objects。

 so as far as the mutix objects are concerned we have the SDD Muts class which implements regular mutual exclusion without any added functionality and this is probably what most of the time is sufficient for synchronization。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_78.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_79.png)

We also have STD recursive Mutex which implements recursive mutual exclusion as the name array suggests。

 and we're going to see where this is useful in just a couple of slides。

 and then finally we also have STD share of Mutex， which implements mutual exclusion with sharedlock something that we also talked about last week already。

Now as we've seen on the previous slide we need two parts for our synchronization protocol。

 we need the Muticix object itself， which is implemented by one of these muttex classes in C++ and then we need some way to acquire and release locks on these mutts objects and for that。

 the standard di provides us with some resource acquisition is initialization wrappers for precisely for locking and unlocking muttexes。

 so we have the SDD unique lock wrapper which allows us to acquire an exclusive lock on a mutticix and we have the SDD shared wrapper which allows us to acquire shared locks on a mutticix provided that the Muix object actually supports shared locking of course。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_81.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_82.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_83.png)

And once again， similar in tone with our previous recommendations。

 we strongly advise you to always use these RAII wrappers for locking and unlocking mut Texas because it just makes bugs much more unlikely that could arise due to inconsistent locking and unlocking。

In some very rare cases， it might still be required to do manual locking and unlocking。

 but even then and this is a very very important recommendation。

 even then you should still use the RAII wrapas， they provide helper functions to do all of this manual locking and unlocking through this wrapper and still give you the benefit of having the RAII pattern。

 meaning that once your wrapper goes out of scope， it takes care of cleaning up anything that it has to。

 which in our case means unlocking the muts in case it was locked。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_85.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_86.png)

So once again to reiterate， even though these mutex objects have functions that look very useful and that can be used to lock and unlock them。

 those should be avoided at all costs， we should always use these RAII wrappers and for this reason we are also only going to talk about these RAII rappers in the following year。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_88.png)

And。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_90.png)

Taking that as a Q， let's start by taking a look at SDD unique lock。

 which can be used to lock a mutex object in exclusive mode。

 so how does this work works quite similar to any other RAII wrappers so in the constructor of SDD unique lock it acquires an exclusive lock on the muttex。

The syntax is simply the unique lock tiing of course the constructor here and then it takes a mutable reference to an arbitrary muix type as its parameter。

 and of course this is the whole point of mutual exclusion in case the mutix is already locked this constructor will block the current thread until the mutix becomes available and we could actually acquire our exclusive lock on the muts。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_92.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_93.png)

So once this constructor returns， we can be sure that our current thread now has a lock on the Mutix so we have entered a critical section and within this critical section we can be sure that only our current thread can execute whatever code we have written in there and of course here then we can do all of our potentially conflicting operations until finally at some point we are done our STD unique lock goes out of scope and then in the deor once again as usual for an RAII class STD unique log is going to release the lock that we have acquired on our Muix seal。

And of course， all Mutex implementations in the standard libraries support locking in exclusive mode。

 so STD and DL can be used with any of the Muex types that we've seen on the previous slide。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_95.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_96.png)

So to give you a very simple example， just to build some intuition here。

 let's take a look at how we could actually implement this safe print function that we've already seen on our slides。

 So the purpose here is that SDDC out of course is a global object and we can access it from anywhere from any thread and any operations on out are not synchronized by default。

 So if we want to do some multithread printing we have to make sure that only one thread at a time Accesses SDC out and this is what we implement in our safe print function here。

So in this case our resource that we intend to protect is a global object so of course here our mutex is not going to be a class member but also a global variable which we see here in our print muttex variable and then within our safe print function we want to make sure that only one thread at a time accesses STDC out and for this we acquire an unique lock on this print Mutex once this constructor returns we can be sure that we have acquired this lock we can then safely write something into STDC out and then once this unique lock goes out of scope。

 the lock on the Mutex is going to be released automatically in the deor of STD in lock。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_98.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_99.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_100.png)

Now， of course， something that you can also see in this example and this is something that's unfortunately unavoidable whenever you write multithreaded code is that you still rely on compliance by any involved party that your synchronization protocol is actually adhered to because no one is stopping some other developer within your project from simply writing to SDDC out unsynchronized。

 and of course this will then completely break your safe print functionality because this other person is not acquiring a unique lock on the corresponding mutex and then even though the safe print function has a lock on the Mutex。

 the other person doesn't and can still write into STDC out and once again then introducing a conflict between the safe print function and this other functionality that's not synchronized。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_102.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_103.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_104.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_105.png)

SoThis is just something that you always have to keep in mind。

 it's not sufficient to only synchronize accesses to shared resources。

 you also have to make sure that everyone that accesses these shared resources follows whatever synchronization protocol you have thought of within your project。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_107.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_108.png)

。到。Returning to our discussion of STD Uni lock what you see on this slide here is the vast majority of use cases for STD Uni lock so I would just off the top of my head sale upwards of 90% of the use cases of STD Uni lock will simply pass the mutex as the only constructor argument and then immediately acquire try to acquire the lock within the STD Uni lock constructor。

 nevertheless there are legitimate edge cases in which this is not precisely what you intend to do and for this STD Uni lock provides some additional constructors that can be used to fine tuneune the locking behavior of this RAII wrapper。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_110.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_111.png)

The first of these useful constructors is the。Constructor that still takes a Mutex as the first argument and then just an instance of the tag type STD defer lock T and this simply tells the constructor of SDD unique lock to not immediately lock the muttex but simply leave it unchanged in return immediately。

 of course if you use this constructor just keep in mind that afterwards nothing has happened yet you have not yet acquired a lock on the muttex here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_113.png)

Similarly， you can use the SDD try to lock T tag type here to try to acquire a lock on the Mut text。

 but not block when this cannot be done So here there are two possibilities it's possible that you have acquired a lock on the Muex but it's also possible that the mutex is currently locked and this was not possible immediately and of course you then have to write a little bit more manual code to actually do this locking and for this the SDD unique lock provides additional member functions such as lock try lock or unlock which is not listed here but probably should be that essentially have speaking names so lock of course manually locks the mutex and blocks the calling thread in case the mutt text is not available try lock does the same but does not block instead it returns false if the Mutex could not be acquired true if it。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_115.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_116.png)

Could be acquired。And then of course， in order to check whether a unique lock instance actually has a lock on the emutics。

 you can simply use the implicit conversion operator to Bo to check whether we have a lock on the emuttics。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_118.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_119.png)

So once again to illustrate， let's take a look at another example。

 which in this case is necessarily a little bit constructed because the usual use cases for manual locking are quite complex and we cannot fit them on a single slide。

 So here let's just assume that we have one of these use cases and we want to do a little bit more fine grained locking here。

 So what we do in our full function here is first。Construct an SD unique lock passing a Muex and the STD try to lock tag object here to tell that we only want to acquire the muttex if this doesn't involve blocking。

 we then check whether we we're actually successful by implicitly converting our STD unique lock to bo。

 if we then determine that we do not yet have a lock on the Muex。

 we can maybe do some useful unsynchronized work before we try again and then finally at some point we invoke the lock function to then force acquisition of the if necessary by blocking the current thread。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_121.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_122.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_123.png)

So at this point here after the if either we have manually called the lock function on our unique lock instance or the initial unlocking attempt was successful immediately。

 so at this point we know that we have a lock on the mus。

 we can then do some work that does require synchronization。

 then possibly release the lock early and continue to do some unynchronized work here。Of course。

 what you can also see in this example that even though some of these member functions are defined on the unique lock you can actually write code that never has to use them in our case here。

 this early rock lock release could also be achieved by simply wrapping the part of thecode where we want to have our unique lock in another scope so we could start a scope before this constructor here and close it after our view synchronized work call here and then of course the unique lock would go out of scope and in its destructure unlock our utex here with the same semantics SDcode that we manually route here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_125.png)

So in general， just as a guideline， try to avoid calling these functions。

 always try to simply rely on the RAII pattern because then your code will be cleaner and you don't have the potential issues of forgetting that maybe your STD unique log doesn't actually contain a log yet or maybe releasing it too early and then afterwards doing some work that in fact does require synchronization and so on。

Something that is quite useful about STD unique lock is that it is movable and when you move an STD unique lock and once again in the spirit of the RAII pattern。

 of course you transfer ownership of a specific lock on a utix to someone else。

And here there are legitimate and quite frequent use cases。

 One example would be if you intend to synchronize some sort of container。

 then you would have a mutex class member here and then when you want to iterate over this container of course iteration reads from the container you have to protect iteration from concurrent rights to the container。

 So here we would probably have to acquire a lock on the muttex in the begin function that returns an iterator。

 then compute whatever constructor arguments our itator needs this already reads from our container so it already requires synchronization and then we want to keep the lock for iteration and here of course。

We move our lock into the iterator to keep ownership of this lock alive here。

A question from the chat， what happens if a thread calls lock on a muttex that already owns this is a great question because precisely our next slide is going to talk about what happens then the answer is usually the code will deadlock because an SDD mutex can be locked exactly once regardless of whether the current thread already owns the muttex and this is something that can actually quite frequently lead to deadlocks especially when synchronizing some data structures or containers because here it is very easy to write code as is shown in this example where we have one mutex several functions that each require synchronization and therefore each have an SDD unique lock within them and then once we call one of these functions from the other you see that here in the full function we still have our unique lock on the mutex。

 we call bar and here we try once again to acquire a unique lock on the same muttex and here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_127.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_128.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_129.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_130.png)

Um this this constructor call here will block forever because the mutex is already locked and we also cannot unlock it because this would require continuing execution within our bar function。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_132.png)

Of course， this is a rather frequent。Case here。 and for this purpose。

 there is the SDD recursive Mus implementation。Which exactly implements what we intuitively would like to have here。

 which is called recursive ownership semantics。 so here on an SDD recursive mutex。

 the same thread can lock an SDD recursive muttex multiple times without blocking and other threads。

 of course， will still block SDD recursive muttex is currently locked。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_134.png)

So here we essentially just have to exchange our SDD mutex for an STD recursive muttex A apart from that we don't really have to change our code because SDD recursive muttex can be used with STD unique lock just like a regular muttex。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_136.png)

And exactly in these cases where we have several functions that each require a lock and that might call each other STD recursive Mutex is quite useful to avoid deadlocks in our system。

Does this answer your question， Let me know if not。 And in the meantime。

 I think there is another question coming up。 So let's pause for a second here。

Is there a price for using STD recursive mutics， Yes there is， as almost always。

 STD recursive mutics， of course， has to keep track of how many times it has been locked and also has to keep track of whether the current thread already owns a mutics a lock on the STD recursive mutics So here once again our recommendation would be to only use it if required。

In most other cases， you can get away with carefully writing your code and maybe passing around SDD Uni logs or。

 and this is what we are going to see next most of the time you can also get around this problem by using STD shared lock。

Which of course， allows a multiple shared locking attempts on the same muttics。And of course。

 just as a side note， if you are interested about the price of certain classes。

 you can always take a look at the reference documentation。

 which as I here for the recursive mutes is also linked on our slides。

Now I've already talked about shared locking， which is very useful once again if we for example。

 want to synchronize containers where reading is of course perfectly fine for multiple threads but writing has to have exclusive access to the data structure and for this we can use the SDD shared lock RAII wrapper。

 which on a high level can be used exactly like STD unique lock so the constructors and member functions are analogous to STD unique lock with the single difference that multiple threads can acquire a shared lock on the same mutex and only one thread can acquire a unique lock on the same muttex。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_138.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_139.png)

Of course， if we attempt to lock a Mutex in shared mode。

 this will also block if the Muex is currently locked in exclusive mode because we cannot have shared and exclusive locks at the same time and here of course the underlying mutt has to support shared locking and because of this STD shared lock can only be used in conjunction with STD shared muttex here。

Now， because we can acquire multiple shared locks on the same muttex。

 we have to be a little bit more careful when writing code that uses shared locks。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_141.png)

Because we could still write code that acquire a shared lock on the Muex and then do some writing。

 no one is syntactically preventing us from doing so。

 but here of course we would then just introduce another right right conflict because multiple threads could have a shared lock on the same mutex。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_143.png)

So usually shared mutetes should be used to implement read write locks where only read accesses are allowed when holding a shared lock and write accesses are only allowed when holding an exclusive lock。

Yeah。嗯。A small side note from the chat here that the CPP reference link appears to be broken on these slides。

 and thanks for the hint。 I'll write that down and fix it after this lecture here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_145.png)

Alright， so back to SDD shared lock， we've now seen that we want to use this mostly to implement read write log。

 so let's take a look at what this could mean by implementing a safe counter。

 So the semantics of our safe counter in this small example should be that we want to have a counter that we can read。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_147.png)

From multiple threads and that we can increment also from multiple threads。 And， of course。

Reading our counter from multiple threads simultaneously is perfectly fine。

 We simply have to make sure that no one is simultaneously incrementing our counter so that we do not get a read right conflict。

 And we also have to make sure that multiple threads do not attempt to increment the counter at the same time because here we would have a right。

 right conflict then。So one possible way to implement this is have our save counter class here which just wraps the actual counter value and contains an SDD shared mutex so that we can implement this readr locking functionality and then within get value function that reads our value。

 we simply acquire a shared block on the mutex so this can be done by multiple threads in parallel and we can then safely read our value but of course when we want to increment our counter we have to make sure that this is only done by one thread at a time so we acquire an SDD unique lock on the same mutex and then we can safely write to our value here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_149.png)

So this unique lock acquisition will block if there are any concurrent readers and this shared log acquisition here will block if there is any concurrent writer here。

Any questions regarding this example？I see some typings， so I'm assuming。Yes。Yeah。Yeah。

The question is whether the unique log access will be queued or is it possible that the riding thread will wait forever while reads keep occurring。

This is not specified by C++ itself as far as I know so this depends on the actual underlying implementation of the mutual exclusion functionality。

 it might be a fair implementation that makes sure that this does not happen。

 It might be an unfair implementation that always prefers readers over writers or also the other way around that always prefers writers over readers。

Just as a side note， so this is beyond the scope of this lecture。

 but it fits into this discussion here。You can implement your own muttex implementation。 Of course。

 you have to follow some interface specification that is given in the C plus plus standard。

 but there you could， in fact， implement any kind of these unfair muttes that prefers readers or prefers writers so。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_151.png)

If this is a problem， you will have to read， I suspect quite a bit of documentation to figure out what exactly is happening。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_153.png)

So on Linux， it's very well possible that locking attempts on muttexes actually involve the operating system so that you have to call kernel functions here。

 and then of course what happens depends on what the kernel does when it gets such a system call of whatever nature here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_155.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_156.png)

But in general， if you run into this situation that you have an extremely large number of concurrent accesses to your data structures。

 then you will probably run into scalability issues when using muttexes anyway。

 and you might want to switch your implementation to using atomic operations which we're also going to see in this lecture today。

 because those avoid some of these problems altogether。对。

So I hope this answers your question for now。And I see another question coming up。

 so let's pause once again。What does the keyword mutable again do here Good question we're going to see that on the next slide So in general what mutable does it it makes members modifiable even from const member functions so usually if we take a look at our get value function here its declared as cont so the this pointer is const and then accessing our mutex through the this pointer implicitly would give us a const reference to this mutex object and by declaring it mutable we get a mutable reference even though our member function is marked as const。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_158.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_159.png)

And this is something that you will see quite frequently when using muttexes within your own data structures because usually you will always have to make the mutexes mutable and this is simply because the RAII rapas that we use to lock these muttes require a mutable reference to the mutex and this also makes sense locking a muttex will have to change some of the muttex state。

 so it will have to modify the muttex object but our cont member functions such as the get value function here。

 most of the time will also need synchronization and they will also need to lock the muttex so our con member functions will have to usually modify the mutex and because of this we will have to make it mutable。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_161.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_162.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_163.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_164.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_165.png)

Now， something that shouldn't be a surprise to anyone after last week's lecture is that using muttexes without sufficient care can easily lead to deadlocks within our system。

 and this usually occurs when a threat tries to lock another mutex when it has already locked some other muttex。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_167.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_168.png)

So in some cases， this can be avoided by using STD recursive Mutex and if we were trying to lock the same muttex multiple times we've already seen this。

 but in other cases where this is not the case where it's actually two different mut textexes that we have to lock and then we have to follow some dedicated programming techniques to make sure that our system cannot deadlock。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_170.png)

So just to give you an example， this code here will lead to deadlock when thread A and thread B are called simultaneously。

And this is because thread A acquires locks on these three mu tes in a different order from the order in which thread B attempts to acquire locks on these mu tes。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_172.png)

So one scenario in which a deadlock will occur is if thread A starts executing and gets locks on Mutex 1 and Muex 2 and thread B starts executing and immediately gets a lock on Mutex 3 here then at that point thread A will wait for thread B to release the lock on M3 so that it can acquire its own lock on M3 and at the same time thread B will wait for thread A to release the lock on Muex 2 so that thread B can acquire its own lock on Muix 2 and of course both of the threads will then wait forever and we have a deadlock within our system。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_174.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_175.png)

So this example here can be fixed quite easily。 The usual strategy to avoid deadlocks in such cases is to always lock muttes in a globally consistent order。

 So this means that。You have to think of all the muttex objects within your program。

 and then you have to define a global order in which you acquire locks on these mutex objects。

This then of course， ensures that when threats try to acquire multiple locks that one thread will always win because we cannot have this situation here that both threats acquire part。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_177.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_178.png)

Of the locks and then wait for the remaining locks that are already locked within some other thread here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_180.png)

Of course， maintaining and actually just coming up with one such globally consistent locking order is quite a difficult problem。

 so it's difficult to come up with this global order at all， for example。

 if you have a non-contant number of mut in case objects come alive and go out of scope again and also it requires considerable discipline to always adhere to this one global locking order。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_182.png)

And in some cases， it may not be possible to have a globally consistent locking order at all。

 depending on the semantics of whatever domain you're working in your project。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_184.png)

So in these cases。There is the SDD scope block RAII wrapper。

 which can be used to safely lock any number of muttexes in any order。

 and this wrapper will internally employ a deadlock avoidance algorithm if this is required Well of course。

 deadlock avoidance algorithms or anything but trivial and of course。

 because of this the SDD scope block implementation will necessarily be quite inefficient in comparison to SDD unique lock or STD shared block。

 So with this in mind and we can easily deduce that STD scope block should only be used as a last resort if we really cannot figure out any other way to make our program work because there are some hard constraints that prevent us from having a globally consistent locking order and we cannot use any atomic operations to avoid muttes at all and so on so STD scope lock should really be used only when it's really necessary in this。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_186.png)

This doesn't happen too often in real world projects。Right， and I see some typing。

 So I'm assuming there is another question regarding。Deadlocks。

Why can't scope lock not just lock the mutexes in a consistent order like hash all of them with the same function and lock one after the other The problem is that it's not too easy to define an order on your muexes so in your example when you hash the mutexes and what do you do when you have hash collisions where two mutexes that are different objects get the same hash value then you still have to decide on some kind of order between these muttexes and this may not be possible。

Another comment is that you might be able to use the address in memory。This。Ma be true。

 And this might work。嗯。This is something that you would have to play around with and implement yourself if you're really interested。

For the purposes of the C plus plus library， SDD scope block does not implement a cheap way of deadlock avoidance。

 So here our recommendation still stands that SD scope block is expensive and。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_188.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_189.png)

We really do not want to use this。Having said that， this is not a big problem， usually because。

You usually want to avoid having a large number of muttices that you need to log simultaneously anyway。

 because this makes your code very complicated。 and usually you could even go so far as to say that。

code that has to lock a large number of muttes is bad code。

 So this is could be one instance of a code smell， usually， And this is from experience。

 you will have to lock at most one or two muttes at a time and。In most other cases。

 you will want to try to use atomic operations that are much cheaper than muttex anyway。Right。

Assuming that there are no further questions on deadlocks。

 let's move on to the final feature that is related to mutual exclusion。

 which are condition variables。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_191.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_192.png)

Now， a condition variable is closely related to mutual exclusion and adds some additional functionality to allow us to communicate a little bit more easily between different threads and more specifically what a condition variable allows us to do then it allows multiple threads to wait until an essentially arbitrary condition becomes true。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_194.png)

So a condition variable still requires us to use a mut text and we will see in another code snippet how precisely this works。

 and then threads can either wait on or notify the condition variable。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_196.png)

When a thread waits on the condition variable， it blocks until another thread notifies the condition variable。

 and then if a thread weighted on the condition variable and is notified。

 it also gets a lock on the associated mutex， so when a thread is woken up。

 we can be sure that it is in a critical section。And then once we have woken up。

 we need to recheck our condition if the condition is now true and we can do whatever we we waiting for if it is still false。

 we go to sleep again and we call weight again until we are woken up again。

 So this recheck is is necessary simply because spurious wake ups can occur that don't correspond to any notify call on the condition variable and this is just an artifact of the underlying implementation of condition variables here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_198.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_199.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_200.png)

So the high level programming model here is that we have a mutex and a condition variable。

 we lock our mutex， we then wait on the condition variable。

 this internally releases the mutex and we are then woken up at some point when some other thread invokes notify on the condition variable and we can then check whether our condition has become true。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_202.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_203.png)

And to implement this， the standard library defines the SDD condition variable type in the corresponding header。

 which has precisely these member functions that we have just talked about on a high level。

 So we have a weight function。On the condition variable that takes a reference to an SDD unique lock that already has to be locked。

 So this is what I previously said。 we first acquire a lock on a mutex and then call weight on our condition variable internally。

 weight then unlocks the mutex and waits on the condition variable。 So it waits until。

The naught5 function has been called。And then we have two versions of the notify function。

 so notify one notifies the single weighting thread， notify all notifies all waitinging threads。

 and then we can implement whatever kind of functionality we want to implement after this weight function here returns。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_205.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_206.png)

So this is quite involved to explain on a theoretical basis， so let's take a look at an example。

 which is in fact a very common example for condition variables which are worker queuees so we have some kind of queue where we can insert tasks and then we have worker threats that are notified to actually process this task so you could for example。

 think of a web server that takes incoming HTTP requests。

 pushes these into a work queue and then we have dedicated worker threats that actually process these HTTP requests and return a response to the call so that we can more easily scale our web server in case there are many concurrent accesses。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_208.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_209.png)

So how could we implement this So。A global scope， we have a mutex。

 a condition variable and our task queue， which in our case simply contains integers， but of course。

 could contain arbitrary C+ plus objects。We then have a function push that gets a task and pushes this task onto the task queue。

 Of course， we have to lock our muttics。To protect the STD vector from data races。

 and once we have this lock we can push something into our queue and then without holding the lock we can call notify one on the condition variable to wake up one of the worker threats that is waiting on the condition variable to actually start working on this thread here。

Within our worker thread function， which of course。

 we're going to probably pass to the constructor of STD thread， we also acquire a lock on the muttex。

嗯。If we have this lock and there is a task in the queue， while still holding the lock。

 we can take this task out of the queue， unlock the mut text so that simultaneously we can push new tasks into the task queue or another worker thread can pop another task off the queue。

Do whatever we need to do to process our task and then lock again。

So that we can either wait on the condition variable or continue working。 And here then of course。

 we invoke CV dot weight， which is going to put the current thread to sleep release the lock internally and then once we are woke up we start over again so we check was this a spurious wake up is there actually anything to do within our task queue if yes。

 take this task process it and subsequently go to sleep on the condition variable again。Any。

Questions regarding condition variables。Okay。What is the advantage of weight releasing the lock？

This is not just an advantage it's actually necessary for this whole model to work so what we have to keep in mind here the lock that we have is intended to protect our task queue from concurrent modifications and you see this here where we actually unlock the lock before we do our actual work of course the actual work might also require synchronization but this is not the purpose of the lock and the condition variable here and here if we were to not release our lock in the weight function here then our push work function would never be able to push any tasks into our task queue because for this we also need a unique lock on our mutecex so that the task queue is protected against data races。

So what we do here is in our worker threat， we go to sleep and release the lock if the task queue is empty。

 and then at some point our push work function can get the lock， push something into the queue。

 release the lock again and then notify our worker threat again。

 which then once again gets the lock so that the task queue cannot be modified concurrently and we can then safely check whether there is anything within our task queue here。

So I hope this answers your question， please let me know if anything remained unclear。Yeah。Allright。

 so with notify all every worker thread would still try to gain the lock and the question is does notify all then only make sense when the worker threads do a lot of work that can happen unsynchronized Yes。

 essentially this is correct。 So what will happen with notify all is that all of the threads are going to be woken up and they sequentially will get the unique lock and then they can check whether something is in the task queue and then they have to unlock this lock before the next thread that was woken up by notify all can get this unique lock So notify all in this example here would for example。

 make sense when we would have another version of the push work function that's say pushes 20 tasks onto the task queue at the same time。

 then we could invoke CV do notify all to wake up all our worker threads。

And have them start working on all of these threads in parallel right away， of course。

 as you correctly pointed out this only really makes sense if the actual work part here takes sufficiently long so that the same worker threat will be occupied for longer than it takes for the other worker threads to also get their individual tasks off the task queue here。

And of course， in this probing model， you would also have to make sure to adjust our worker threat implementation to not immediately go to sleep again。

 but'm continue checking the task queue for available task because then we don't have this one to one mapping between notify one and one task being popped off the task queue anymore。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_211.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_212.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_213.png)

Any further questions。After calling wait， when does the worker get the lock back。

 the worker gets the lock back immediately before the weight function actually returns。

 so the weight function blocks the current thread So execution will stall here until someone calls notify one or notify all on the condition variable and then once this function returns and our execution in the worker thread continues。

 we will already have the lock back。 So all of this this waiting for the lock to become available in case we invoke notify all is going to be performed internally by the weight function and once it returns。

 you can be sure that you have the lock back。그。Do notifications get buffered。No， they do not。

 so I'm assuming that you mean when you call notify one twice that two threads exactly are going to be woken up。

 this is not guaranteed， and this is what I meant previously when I said that once we start I using notify all here。

 we would have to adjust our implementation to essentially do this buffering ourselves。그。

So if no thread is waiting on a condition variable and you invoke notify one。

 then nothing will happen。 So this is something that you have to keep in mind。And in general。

 because our discussion of condition variables here is necessarily a bit short。

 you can also take a look as always at the reference documentation which explains in much more detail how exactly these functions work and there are also a number of quite good examples in the reference documentation that illustrates some more of the corona cases in which you might find yourself using condition variables。

So follow our question on the buffering part， isn't this a problem in our current example here？

You're right， it may be a problem if our worker threat takes longer to process the actual work than it takes the push work function here to push stuff onto the queue。

 So you're right in that we would probably already in this example need to implement our own。

Our own form of buffering here。 So in， in our example here， this。

This should usually be a very minor change simply because we can have this while loop run as long as the task queue is not empty and only wait on the condition variable if the task queue is empty。

 then we would avoid this problem without any without too much additional code。

 but still you are completely correct in that our code is not 100% correct and I will adjust the example after this lecture here。

Yeah。So as you can already see from the number of questions and also the nature of questions。

 condition variables are not the easiest construct and C++ to use。

 but they are quite useful because they give you an easy way for this interthread communication that otherwise you would have to implement。

Yourself， which would also be quite a difficult undertaking。Now。In the interest of time。

 let's move on if there are any further questions， of course， you can still let me know。

 But in the meantime， let's move on to the second large part of synchronization in C plus plus and that is。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_215.png)

That are atomic operations。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_217.png)

So after now， we've always talked about mutual exclusion， but mutual exclusion。

 And this we've already hinted at this a couple of times may be quite inefficient for synchronization。

 And the reasons for this are there are various reasons for this。 So， of course。

 mutual exclusion is rather coarse grained。 You always have these critical sections that are can be quite large and。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_219.png)

Essentially， no parallelism is allowed in these critical sections。

And also something that I've briefly hinted at is that Muuttes may require communication with the operating system。

 which would then of course always involve context switches， whatever system call is required。

 which can also be quite inefficient。Sometimes of course we cannot avoid mutual exclusion。

 but sometimes in fact we can， because modern hardware also supports atomic operations for synchronization。

 which in many cases can give us the same outcome at a much smaller cost。So。

And this is once again something that you have talked about in detail last week。

 the memory order of a CPU determines how nonatomic memory operations are allowed to be reordered to each other。

 so by reordering we always mean here how they become visible to different threads in which order。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_221.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_222.png)

Something that we've also seen in the beginning of this lecture is that in C++ any nonatomic conflicting operations are undefined behavior。

 even if the memory order of the underlying CPU will allow it。So even if you are， for example。

 on an Intel CPU that has a strong memory model that allows you to write unsynchronized to memory under some constraints and have a welldefined outcome。

 this would still be undefined behavior in C++ with one major exception and this exception are special atomic functions that are defined by the C++ standard。

 which are allowed to have conflicts and where the C++ standard。

 then precisely defines what the outcome of these conflicting atomic operations are going to be。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_224.png)

Something that's also useful to keep in mind is that these special atomic functions are essentially syntactic sugar because the C++ compiler will usually know your CPU and it will generate real atomic instructions only when they are necessary。

 so even when you use these special atomic functions to make C++ happy most of the time or actually if you take a little bit of care always the compiler will generate code that is just as efficient as code thatt that would use non-atomic conflicting operations right away。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_226.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_227.png)

For these special atomic functions， C++ provides the atomic operations library in the atomic header。

 and this essentially defines one type that can be used for all of these atomic operations which is the STD atomic template。

 which just represents an atomic version of whatever type you pass as the template parameter here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_229.png)

And then this atomic version of this type can be used almost interchangeably with the original type T。

 so in particular it has the same size and the same alignment as the original type T。

 but with the added benefits that you can write code that has conflicting operations， So。

 for example， a readrite conflict or a right right conflict on these STD atomic objects。

 So this is the only exception to the rule that conflicting operations are undefined behavior。

 they are only defined behavior if they occur between STD atomic objects。

 So even if you have a conflict between an STD atomic object and a non-atomic object。

 this would still be undefined behavior， the only conflicts that are allowed are conflicts between STD atomics。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_231.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_232.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_233.png)

Something that's also extremely important to keep in mind that SDD atomic on its own does not provide any synchronization at all。

 It simply makes conflicting operations possible and defined behavior。

 but it does not make them deterministic。 You can still observe non deterministic。Effects。

 if you have conflicting operations on STD atomics within your code。

 its SD atomics simply exposes the guarantees of these of specific memory models to you as the programmer。

 And of course， you can achieve synchronization with this。 But for this。

 you have to follow some suitable programme models that exploit these guarantees of a specific memory model。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_235.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_236.png)

And then use this to achieve proper synchronization， for example， for a custom data structure here。

 So SD atomic on its own simply allows you to have conflicting operations and the outcome is well defined。

 but not necessarily deterministic。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_238.png)

Now to go into a little bit more detail about atomic operations。

 the main member functions that you can use to have to write code with such conflicts are the load store and exchange member functions。

 where the load function simply loads the value of your atomic so where you simply use for example。

 an unsigned variable in regular code， you would use an STD atomic with template parameter unsign and then use the load value to get the actual unsigned value that's currently stored in this atomic value。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_240.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_241.png)

The same goes for the store function， so where you usually would have an assignment to an unsigned。

 you now use the store function on an STD atomic to store an unsigned value within your atomic object and you can also instead use the exchange function which does the same thing。

 but in addition returns the old value， so whatever you exchange them by the new value from this function here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_243.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_244.png)

If your type T is an integral type， then in addition to these load store and exchange functions。

 you also have a number of arithmetic operations such as fetchdge add， fetchdge sub and so on。

 the semantics of these are always that in case of the add function here。

 the argument is added to the value that's stored in the atomic and the old value that was replaced is returned from this fetchdge addd function here and of course the same goes for all the other operations that are listed here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_246.png)

Now， to give you a brief example before we go into even more detail。

 let's take a look at an example that does not use atomics and has conflicting operations。

 So of course， because of this it does involve undefined behavior。 So here what we do in our example。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_248.png)

We simply have an unsigned that's initialized to0， we then have a single thread that increments this value 10 times and then terminates。

 and we also increment this value 10 times within the main thread and then join our thread T here。

So of course， this incrementing here is a read Mo write operation。

 so it involves both reading and writing to the value。

 and because there is a right involved and we do this in parallel in two threads。

 we have a data race here which is undefined behavior。And。

The usual outcome of such an ill formed program is that after we have joined our T here。

 value will simply contain garbage because some of these reads or rightss are where maybe toent rights。

 maybe it also contains a meaningful value in case the underlying CPU instructions happen to。

H to be arranged in such a way that the CPU can still guarantee a valid outcome。 But regardless。

 this is undefined behavior。 so we cannot write code like this。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_250.png)

The correct way to write the same code would be to use atomics of course。

 so if we compare our examples here we see that we have a plane unsigned in our correct example we have an SDD atomic with template parameter unsign and instead of using the pre increment operator we use the fetch add function to safely add one to our value here and the same in the main thread and here this program is well formed and the outcome is in fact deterministic in that value will always contain 20 after we have joined our thread T here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_252.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_253.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_254.png)

Note and this also illustrates some of the pitfalls when using atomics quite well note that the eventual outcome here is deterministic because we know that the increment value exactly 20 times overall。

 the order in which these increments happen and which values each of these thread actually sees when incrementing are entirely nondeterministic。

 so it's possible that t increments from0 to 10 and the main thread increments from 10 to 20。

But it's also possible that T increments for all the even values of value and the main thread increments for all the odd values or any other combination that you can think of。

 So no explicit order or anything is guaranteed by the atomic only that these increments are defined behavior。

 and of course， our final outcome in this case here is also going to be deterministic。

Any questions up to this point？Nothing yet。 All right， then let's move on。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_256.png)

What are the semantics of atomic operations we've of course seen this a little bit already in our example。

 but let's take a look at this in more detail。 So the first thing that's important to keep in mind is that SDD atomic guarantees you that conflicting operations are atomic so they are either seen not at all by other threats or in their entirety and that they are welldefined behavior。

But at the same time， SDD atomic can be used with any trivially copyable type。 and in particular。

 also for types that are much larger than one cache line。

 And if you think back to last week's lecture， atomic operations are only defined。If at all。

 by on objects at most one catchline wide， and in those cases where you use STD atomic with an arbitrary truly copyable type。

 the compiler is allowed to fall back to mutex to guarantee atomity of the operations that you perform on this STD atomic。

Of course， for most of the use cases， you will simply use an STD atomic on the fundamental types that are already defined in C+ and there。

 but once again still depending on the underlying CPU。

 the compiler will usually generate true atomic assembly code。Once you have an SD atomic and。

Don't care anymore more about how it's actually implemented。

 You still get the precise semantic guarantees that the C+ plus standard defines for atomic operations。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_258.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_259.png)

And those are essentially related to the order in which modifications on an atomic object can become visible to other threads that read from the same atomic value。

And。There are several technical terms that are related to this。

 The first is that every atomic object has a totally ordered modification order。

 So even when an atomic object is modified from multiple threats。

 there is a single global total order in which these modifications are going to be applied。

 This order is not necessarily deterministic， but in every for every run trace of your program。

 there will be one totally ordered global modification order。That being said。

 if you read from such an atomic object， reads on the same atomic object， of course。

 will adhere will be consistent with this total global modification order。

 but reads on different atomic operations may be reordered。

 so they may become visible in different orders in different threads。

So this is once again a result of the memory order that is used by the underlying CPU for most purposes。

 the memory orders that C++ defines do map quite precisely to the underlying memory orders defined by a CPU but just keep in mind that this is not necessarily so so the C++ memory orders may differ slightly from the memory orders that your specific CPU supports。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_261.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_262.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_263.png)

So。What does this mean for us if we have a single atomic object。

 then modifications of this atomic object are total the order and this is called the modification order of the object。

 and for a single atomic object all threads are guaranteed to observe modifications of the object in this order。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_265.png)

If we talk about different atomic objects。Modifications on different atomic objects may be unordered with respect to each other。

 which means that different threads may observe modifications of multiple atomic objects in a different order from each other and how precisely this can happen in which which types of reorderings are allowed here is once again specified by the C plus+ memory order that is used for the atomic operation here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_267.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_268.png)

So。Of course， this is something that's quite complex and quite difficult to wrap one's head around。

 so let's take a look at a couple of examples that may help to illustrate this problem of modification order。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_270.png)

So。In our example here， we have two atomic variables， we have an atomic variable I。

 and we have an atomic variable J。Now， what we do in a worker thread here is we first increment I by one atomically and then we decreement I atomically by one again。

 and then subsequently we increment J by one also atomically。

 So what we have here is we have two modifications on the same atomic object。

 So these are modifications A and B here， and then we have one modification on a different atomic object which is named C here。

And if you now have a reader thread， some quite unexpected things can happen here so。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_272.png)

One thing that is a result of the total global modification order for a single atomic is that reader threads will never see B happening before a because these happen on the same atomic object and these are ordered A before B。

 so any reader thread will always see a happening before B and because of this we will never see I when we I so the value that we load from our atomic here to be negative one because this addition of one will always happen before the subtraction of one。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_274.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_275.png)

But what is possible let the effects of our modification C here。

 which are on a different atomic object happen at any point before between or after A and B。

 So of course， depending on the memory orderura， reader threads may see any of ABC， AB or C A B here。

 and this is the key reason why we actually need memory ors。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_277.png)

To be able to still reason about programs that use atomic operations on multiple atomics and write useful code with this so depending on the underlying memory order it's actually not possible that we observe some of these modification ors and then of course once we know that we can write code that actually relies on this fact that maybe we always observe C happening after A and B。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_279.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_280.png)

There is quite a large number of memory orderss that is defined in the C++ Atomic operations library。

 and all of these memory orders can be passed as an optional last parameter to the atomic function。

 so for example， the fetch add function， the store or the load function。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_282.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_283.png)

Most of the time it's sufficient to use either SDD memory order relaxed or STD memory order sequentially consistent by default sequentially consistent memory ordering is used and also this is a quite s default because usually this is the strongest memory order so it gives you the most guarantees and most of the time it works just fine。

 so you should only move away from using this default memory order。

 if you have profiled your application and noticed a single atomic operation to be a performance bottleneck then you can start thinking about using a less restrictive memory ordering。

 but of course this is always a very complicated undertaking because you have to make absolutely sure that the weaker guarantees by a weaker memory ordering are still sufficient for your program to work as intended。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_285.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_286.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_287.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_288.png)

So just to give you an example of how this could look， so we have our same atomic variable I here。

 we just call fetch add this will internally use sequentially consistent memory order by default。

 but we can also pass a second argument here and specify what memory order we want to use ourselves here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_290.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_291.png)

Now， of course this doesn't really help us a lot we have to actually understand what these memory orders do。

 so let's take a look at the two that we determine to be most useful。

 so first of all STD memory order relaxed roughly maps to a CPU with weak memory order so it behaves as a CPU with weak memory ordering would behave。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_293.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_294.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_295.png)

And here， the only guarantee that you get is that a single atomic variable has this totally ordered global modification order。

 Atomic operations on different objects may be reordered arbitrarily with respect to each other。

 So no guarantees at all are made here。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_297.png)

So what this means is if we have the same code as before， where we add and subtract M I。

And then also add one to J， but here instead of having sequentially consistent memory ordering in our route use relaxed memory ordering。

 thread B may observe a modification order ABC and thread C may observe C happening before A and B。

 Not that A and B， of course， are still going to be ordered because those are on the same atomic variable here。

So a relaxed memory order is quite useful， for example。

 if you have a counter that you want to increment， maybe you have a multi threadreaded program or you just want to count maybe iterations within each thread。

 then the order in which these increments happen doesn't really matter。

 and you can use relaxed memory ordering。In most of the other cases。

 and this goes back to our recommendation， Re memory order ordering will probably introduce bugs into your code once you start using atomic operations for actual synchronization。

 where you need stronger guarantees and in particular you need more information about the order in which modifications can be observed by different threads。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_299.png)

And for this， usually it's fine to stick with sequentially consistent memory ordering。

 which roughly maps in terms of behavior to a CPU with strong memory orderura。

 and this guarantees that all threads see all atomic operations in one globally consistent orderura。

Note that this still does not mean that your program behaves deterministically。

 but it only means that all threads see one in the same order of modifications。So in our example。

 which is the same example as in the previous slide， just with a different memory ordering。

 this means that if thread B observes a modification order as CA AB。

 then thread C and all other threads in the system will also observe the modification or as CA AB。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_301.png)

And of course， once we have this guarantee， we can actually start writing useful code that makes use of atomic operations to synchronize entire data structures。

 but before we take a look at that， are there any questions up to this point？



![](img/b4146116ad47eca7d2a49f6d5d93cb13_303.png)

No questions so far。 So then let's move on to the final part of this lecture。

 I am going to go over time a little bit apologies for that， but there's not too much content left。

 so please bear with me。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_305.png)

So most of the time what you' are going to use when you use atomics for synchronization is the comparison swap operation。

 once again something that you saw in a high level last week today we're going to take a look at how this is implemented in C++。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_307.png)

So the signature in C++ is yet another member function on atomic objects。

 it's called Compare Exchange Week， it takes a reference as its first argument and a value as its second argument。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_309.png)

The semantics of this compare exchange operation are that。

The current value of the atomic is compared to whatever you pass in this expected reference here。

 If the current value of the atomic is the same as in whatever you pass as the expected value here。

 then the current value of the atomic is replaced atomically by what you pass as desired here。

 and the compare exchange function returns true。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_311.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_312.png)

If the current value of the atomic is not the same as what you passed as the expected value here。

 then this expected reference is updated to contain the current value of the atomic object and the compare exchange function itself returns false。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_314.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_315.png)

So this function is often the main building block to synchronize data structures without mutt。

 of course it's not always possible， but it is possible quite frequently and the reason why this is the main building block is that this compare exchange function here allows us to check that no modifications occurred to an atomic variable over some time period in particular we can read the current value of an atomic then do some useful work and then use the compare exchange weak function to validate that no one else modified the atomic value in the meantime and by this we can instead of enforcing mutual exclusion by using muttes。

 we can validate that mutual exclusion actually happened after the fact。

So with this somewhat informally， we can use this compare exchange function to implement implicit mutual exclusions。

 So as I said， where we don't enforce mutual exclusion from the beginning。

 but we simply validate that no conflicts occurred in the meantime。

Of course we have to be very careful when we do this because as you've seen once again last week。

 this validation is not always reliable and can suffer from subtle problems such as the AVA problem that you saw in the example of using atomics to implement a lock free stack last week。

A question from the chat， the otherwise in the fourth bullet point is unclear， so this is。

 I presume this bullet point here。So this otherwise refers to this previous bullet point here。

 so if the atomic compare contains the same value as what you passed is expected。

 then the current value is exchanged and compare exchange fault returns true。

 if the atomic does not contain the expected value。

 then this expected reference is updated to contain the current value and compare exchange returns falses。

All right， this seems to be cleared up。 Any further questions。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_317.png)

Alright， so let's take a look at at one example， how we can actually implement。嗯。

Thread safe data structures without muixes。 And the canonical example here is to implement a thread safe。

 Sly linked list， which only supports insertion。 This is sometimes quite useful。Of course。

 our singlely linked list has on a high level exactly the same structure as any other singlely linked list and we have an entry which stores a value of some unspecified type T here and a next pointer to the next value。

We then have the head pointer to the first element within our list。

 which is an atomic so we can atomically change this the value of this pointer。

 and in particular we can also use the compare and swap function on this pointer。

We need some way to allocate entries， this is left unimplemented here because it does' not matter for the purposes of our example。

 all that this does is give us a pointer to some entry that already contains the value that we passed to our allocate entry function here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_319.png)

So excuse me so what we now want to do before we start looking at the implementation is and when we call our insert function with a value。

 we want this to be callable from multiple threads simultaneously。

 and we want to prepen a new note containing this value to our list here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_321.png)

And。As is usual when using atomic operations， we do not really care about the order in which multiple such notes are prepened to our list。

 The only thing that we want to guarantee is that once the insert function returns。U。😊。

The value is certainly inserted somewhere within our list。And one way to implement this。

 and this is a pattern that you see quite frequently when when inspecting Lofr data structures is as follows。

 so first of all， we simply allocate an entry， we assume here that maybe allocate entry called Maoc internally。

 which is threadsafe or we synchronize allocation ourselves in some way the important thing being that allocate entry here is TsSafe and we get a pointer to an entry Now this entry of course is currently unlinked from our list and we now have to make this entry。

 the new head of our list。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_323.png)

And the way to do this is to first get the current head pointer here。

 which maybe null pointer it may contain an already existing node of our list here。

We then set the next pointer of our new entry to this current head。

 So this is analogous to how insertion into a link singlely linked list always happens。

 And then the key line of our code here is the compare exchange week call。 So what is happening here。

Note that we have， remember that we have loaded the current value of our head pointer here。

 and now we try to exchange the current head pointer with the pointer to our newly allocated entry here so that our new entry becomes the new head of the list and the next pointer of our entry points to the previous head of the list。

So what we do here is we invoke Compare exchange week on this atomic pointer。

 the expected value that we expect to be in this pointer is the current head pointer that we loaded here and that we store in the next pointer of our entry。

 and the desired value， what we want to store in our head pointer is our newly allocated entry here。

So if no one else change the head pointer in the meantime。

 then it will still contain the value that we loaded here。

 And then our compare exchange week call will succeed。

 So the current head of the list is going to be replaced with our entry pointer。

 and this compare exchange week call will return。Will return true and we will break out of our loop here。

If someone else modified the head pointer here in the meantime。

 then this compare exchange weak function will notice this the current value of head is not the expected value。

And then two things will happen and both of these things are very important。

 the first thing that happens is once that Comp Exchange week notices that the current value has changed。

 it will change the value of current hedge to this new current value。

 so compare exchange week will modify its first argument here to contain the new new current value of the atomic in case it has changed。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_325.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_326.png)

And the second thing that will happen is that compare exchange week will return false because this compare operation was not。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_328.png)

Successful， so subsequently， we will run into another iteration of our loop。

 Our current head will now have changed。 It will contain the new head that was set by someone else in the meantime。

 and then we will try simply try again， we will once again set our next pointer to the now current head and we will once again try to exchange the current head by our new entry。

 This， if someone else manage to squeeze in and add yet another element to our list in the meantime。

 will then probably fail again。 in which case we simply try get another iteration。

 until at some point， we actually manage to replace the current head of the list with our newly allocated entry here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_330.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_331.png)

Allright， and I saw some questions in the chat which hopefully got cleared up in the meantime。

 so the key here is that Compare exchange week will update its first argument in case and the current value of the atomic change。

So we do not in fact need to reload the current head within this loop here， and in fact。

 this would be a little bit of unnecessary overhead because this is already done by the Comp exchange week function。

Any further questions。Allright， no typing， then I'm assuming not if there are in fact， any questions。

 do let me know。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_333.png)

So some final closing slides on compare and swap。 So in fact。

 there are two compare swap versions on SD atomic that have the same signature。

 There is compare exchange weak and compare exchange strong， which。Can both be used interchangeably。

 So they have the same semantics with the only minor difference that the weak version is allowed to return falses。

 even when no other thread modified the value of the atomic。

 So this is then called a spurious failure。 And as opposed， the compare exchange。

 Str function will never return these。

![](img/b4146116ad47eca7d2a49f6d5d93cb13_335.png)

These falses negative。 So if compare exchange strong returns falses。

 then you can be sure that a modification has happened in case of compare exchange week。

 no modification may have happened and you might might have run into a spurious failure。Internally。

 the strong version can use a loop to avoid this so then it would essentially implement this same loop here internally to give you this guarantee and because of this as a general rule of thumb if you yourself use a compare swap operation in a loop always use the weak version because then spurious failures do not really impact your code only when compare exchange strong could be used in your code to avoid such a loop。

 then it makes sense to actually use this compare exchange strong version of the operation。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_337.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_338.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_339.png)

Now， the final。Thing that we briefly need to touch on is a new addition in C plus plus 20。

 which is the SDD atomic wrapper， which essentially implements an SDD atomic reference。

 So SDD atomic itself can be a little bit tricky to use because it is neither movable nor copyable。

Which， of course， is a little bit annoying in particular because you cannot use SDD atomic and standard library containers seeing that it is neither movable or copyable and with SDD atomic ref and we can work around this problem because SDD atomic ref allows us to apply atomic operations to objects that are not stored as SDD atomics so the constructor simply takes a reference to an arbitrary object of type T and this referenced object is then created as an atomic object during the lifetime of STD atomic ref so all of the member functions that you have on STD atomic are also defined on STD atomic ref。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_341.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_342.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_343.png)

With the difference that SDD atomic rep can be used with a reference to some object of type T。

 whereas SDD atomic stores such an object itself。Just to keep this in mind。

 any data races between accesses through STD atomic ref and nonatomic accesses are still undefined behavior。

 so if you use STD atomic ref， you have to make sure that all potentially conflicting accesses to an object occur through an STD atomic ref for your program to be well formed。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_345.png)

![](img/b4146116ad47eca7d2a49f6d5d93cb13_346.png)

And on our final slide， our final example here， just a brief example where we want to have a vector of integers that are modified by multiple threads so as SDD atomic is not movable or copyable。

 we can directly store SDD atomics here in our vector so instead within our threads here we construct an SDD atomic ref to one of these integers and then use the fetch add function in our example here on this atomic ref and end up with a well definedfined function here。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_348.png)

对。All right， so that's it for today。 Are there any concluding questions on today's lecture？All right。

 no questions so far。 so then thank you for your attention and see you this Friday， goodbye。



![](img/b4146116ad47eca7d2a49f6d5d93cb13_350.png)