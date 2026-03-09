# 美国贝鲁特大学《GPU计算｜CMPS 297S396AA - GPU Computing - Spring 2021》（豆包翻译 - P5：-05-Lecture 05 - Memory and Tiling.zh_en - GPT中英字幕课程资源 - BV1bw4m1k7a1

![](img/2700d7d129b2fd03a595532953820cdb_0.png)

Hello everyone and welcome to lecture 5 of GPU computing Today we're going to be talking about memory。

 the memory how the memory in the GPU is organized and how memory in the Cuta programming model is accessible。

 and then we will also talk about an important optimization related to memory and that is highly。

Some of you might already be familiar with Tyling if you've taken a GPU course where you've spoken about how to optimize cache accesses on a CPU。

 sorry if you've taken an advanced architecture course and you've spoken about how to optimize cash accesses on a CPU。

 so the Tling we'll be talking about about today is very similar to that actually。Before that。

 let me review last time， what we talked about last time。

 last time we talked about the GPU architecture， we said that GP is organized into SMs or stream multiprocessors。

 each SM having its own set of cores that share some control logic and also share some memory and that they all have access to a global memory。

 which is the same global memory that we were copying data to and from in previous lectures。

We said that blocks are assigned threads are assigned to as on a block by block basis at block granularity。

 which means that all the threads in the same block will be assigned to the same S now obviously since an as has a limited amount of resources you can only have a limited number of blocks running on an S at the same time so if your grid has more blocks than all your Ss can fit simultaneously then those blocks will simply wait until some block on some S has finished before the next block can have its turn we also said that threads within the same block can collaborate in ways the threads of different blocks cannot hence the benefit of having them scheduled on the same S we said that they can synchronize using barrier synchronization which means they all wait for each other at some point in the code before they keep going and we also said that they can have access to a fast shared memory that only threads in the same block can access and we'll actually talk about these two。

Thanks they all can also col in other ways which we haven't talked about yet。

And we said that for threads scheduling when blocks are scheduled on Ss。

 they're divided into units of warps and they're scheduled units of wars and we said what's special about warps is that they are executed。

 they are executed following the SD model so a warp is consists of 32 threads and every 32 threads are executed on an S following the single instruction multiple data model which means that we fetch one instruction and we execute it for all the threads in the warp at the same time Now if we are in a situation where these threads that are in the same war have take divergent execution paths we have to do is we have to do multiple passes through the code。

 in other words， if I have this warp these 32 threads that executed this code is3 indexex dox is less than 24 do a then else do B and then do C we cannot。

Have threads 0 to 23。 execute A。 And then at the same time， threads 24 to 31， execute B in parallel。

 They cannot do that because the threads that are in the same morp are bound to the same instruction。

 So what happens is threads 0 to 23 are gonna execute A while threads 24 to 31 are inactive。

 And then we're gonna have the second pass where threads 0 to 23 are inactive while threads 24 to 31 are executing B。

And this obviously is a source of inefficiency because here when these threads are inactive。

 they're still reserving cores， but they're just not using them。

 so here we have underutilization of the processing units on our GPU so obviously we'd like to avoid situations like this。

 we'd like to avoid cases where threads in the same war are doing different things are taking divergent path in the code and we will see later on in the course how we can optimize our code to avoid things like this another example is where is if we have a loop for example。

 and different threads have a different loop bound in this case。

 the threads may initially all be active but then some threads finish the loop iterations。

 but others keep going and basically the threads that have the longest number of loopiterations will hold all the other threads in the war hostage because those other threads are going to remain inactive until the last thread in the war is done with this loop iteration。

After talking about convergence， we spoke about latency hiding and we said that the way that these warps are scheduled on the SM is that we get a warp and we execute it on the course in the SM and then once this warp encounters a long latency operation we put it aside and we bring in another warp to fill in those cycles until this other warp is done and then if that warp and cast long latency operation。

 we bring in another warp until finally in this first warp and completes this long latency operation and is ready to execute again and in this case we bring that warp again and we start executing it and by doing this。

 you know whenever one warp is not ready to execute the next instruction。

 bring in another warp and use that warp to execute we minimize the number of stalls that we have in our pipeline where we minimize number of empty slots that we have in our pipeline and that results in us being able to tolerate the latency or hide thelatency of some wars。

By executing other words。And because we would like to hide this latency。

 we saw that it is desirable for us to have as many wars as possible scheduled on the as in order for us to high hide latency as much as possible。

 And this run us on the topic of occupancy。 where we said that there's a certain maximum number of threads that's allowed to be on the S at the same time。

 but depending on how we write and configure our kernel。

 it might be the case that this maximum is not achieved。

 So the ratio of the actual number of threads running on the S to the maximum that is possible is called the occupancy。

 and ideally we would like to have an occupancy of one。

 meaning we'd like to have as many threads running as as there are maximum allowed however。

 it might be the case that this doesn't happen and and for that， we looked at。

What are the various things that may constrain occupancy we said that depending on the architecture there might be a maximum number of threads that connect execute on the Sm andvol of you 100s 248。

 but there's also maximum number of blocks and a maximum number of threads per block。

 there's also a maximum number of registers and a maximum amount of shared memory per S and we'll talk about shared memory today。

 but basically the observation was that if I， for example。

 can figure my thread block to have 32 threads， then the maximum number of blocks that I can have as 32。

 So 32 blocks， that's 32 threads is 1024 threads。 So if my block and the size of my block is 32 threads。

 then I will only be able to have 124 threads running on my S which which is less than the 2048 threads。

 which is the maximum that is allowed。 So that was an example of how we may we may have you know a low occupancy because of the way that we can。

Figuring the maximum number of blocks。It also also depend on the number of registers， for example。

 if we have too many registers per thread， we might run out of registers before we run out of threat slots and that also may lead to us underutil our SM so this was a quick overview we covered last time。

 any questions。Everything weirdd， everyone。ok。So today。

 what we're going to do is we're going to talk about memory in the GPU architecture。

 So last time we focused on cores， we focused on ors。 We focused on。

 you know a lot of the execution units。 Today， we're going to look at the memory part。

 So we're look at the memory in the GPU architecture。

 We're going to look at memory and the cota programming model。 In other words。

 how can we manage the memory in the GPU architecture。

 What is the cota programming model give us access to We're going to look at how to optimize memory accesses and we're going have a running example throughout the lecture。

 which is， again， matrix matrix multiplication with this time with some more optimizations added。

 Simply the tiling optimization okay。So before I talk about every energy I'd like to first discuss performance metrics so when a processor designer designs a processor。

 they usually give give us some information about the capabilities of this processor okay so processor designers inform users about the processor's performance through various metrics and the most notable metrics that you've probably heard here and there are one the flops rate so the flops rate of a processor is the number of floating point operations per second that the processor can execute and what this refers to is how many computations the processor's scores can do pretty even time。

 how many floating point operations can execute for even time of course assuming that everything else is perfect okay I may not achieve this rate but this is basically the maximum rate that I can achieve if everything else is perfect。

Similarly， we are also told about the very bandwidth of a processor， or in other words。

 the number of bytes per second that a processor's memory can supply to the cause of this processor。

Again， this memory bandwidth， if pro designer tells you that the bandwidth of my memory is bytes per second。

 this may not necessarily to me that you will get this many bytes per second。

 it means that if everything else is perfect， then the memory is able to give you this many bytes per second。

And these rates vary across processors and they vary across across generations of the same processor because they depend on。

 know how many Aluus， for example， floster depends on how many Alus I have in my processor。

 maybe the frequency of my processor， the memory bandwidth depends on the memory technology how many you know how many how much how much parallelism I have in my in the memory architecture。

 So if you look at different generations of GPUus recently。

 you can see how the peak flops rate has changed。 obviously there's been quite an increase and you can see how the peak memory bandwidth has changed。

 So also there's quite an increase。 So the V100 GPU。

Wwhich is the one you've been using in the cluster， it has 14。

028 gigabflps or close to 14 terof flops and what that means is that it can perform 14 giga is billion so you can form around 14 billion floating point operations per second and it also has sorry 14000 billion so 14 trillion floating point operations per second and the bandwidth has 900 gigabytes per second so you can load 900 billion bytes the memory can supply us to 900 billion bytes every second。

And now again， these metrics are not a guarantee。So if you write a program。

 if you write a kernel and you run it on the GPU， you're not guaranteed that this kernel is going to perform 14teraflos and you're not guaranteed that this kernel is going to receive 900 mebytes per second。

These are the limit。 This is not a guarantee that you will you will reach these these peak values。

 and most often you will not。 What this tells you is that it is physically impossible for you to to execute more than 14 bigger flops per second。

Because if you execute a floating point operation at every single core for every single cycle。

 then you will get this kind of fl rate。Similarly， if you load every single bike in the in the in the memory interface on every single cycle。

 So if have perfect utilization of your memory bandwidth， this is what you will get。 Okay。

 so it's not a guarantee you will get these， but it's basically the maximum possible that you can get。

 but they do serve as good proxies for how powerful a processor is。

 And they also serve as good reference for you to compare the performance of your code to see whether you've reached close to these peaks or if you're very far away from them。

 And that usually gives you an idea on on on where you stand in terms of the potential performance that your code can get。

😊，ok。😊，Any questions about these two metrics， are they clear？Doctor Bu question。

 bandwidth and throughput。 throughput is the actual bandwidth。 bandwidth is the theoretical。Okay。

 so here I think I will try to be clear， so you know you know different people who may use different terms or different things I will try to be clear throughout the lectures when I say bandwidth what I mean so you have here I'm writing the peak memory bandwidth and the peak flops rate okay and then when we when we mean achieved we'll usually say like achieved memory bandwidth or achieved flops rate okay。

So there is really a fixed convention what we mean by when we say throughput versus bandwidth。

 usually the word throughput， we usually usually the flops rate。

 we refer to instruction throughput or you know floating point throughput。

But for the distinction between peak versus at， I'll try to be clear so that you don't have that confusion。

Okay， thank you。Okay， so performance sounds。More on performance bounds， an application。

 it runs on the GPU or when it runs on any processor， it can be compute bound。

 And what that means what it means for an application to be compute bound is that it's limited by the flops rate。

 Okay， in other words， our processors scores are always fully utilized。

 They always have something to do。 So what's what's preventing an application from getting more performance is that the processor's scores I don't have more core to do more work or the processor of course cannot work any faster。

In this case， an application would be computed done。

An application is memory bound when the performance of that application is limited by the memory bandwidth。

 and in this case， the processor scores may be id at different points of time because they're just sitting there waiting for memory。

So in this case， the memory is what's limiting my performance。

 The memory is preventing my course from working faster because the memory cannot provide the course with data fast enough。

😊，Okay， so an application is compute bound when it's limited by how fast the course can go in this case。

 the course can be fully utilized and my memory is you know sitting there and happy。

 it doesn't have much to do because the cores that' have enough data to fully to fully utilize themselves or it can be memory bound where the cores are sitting there and waiting for the memory to give them the data。

 but the memory is the bottleneck The memory is what's preventing me from going any fast。Okay。

 now if we look at these very， these different GPUs that we that we just saw。

 youll notice that the fps rate。Tends to be higher than the memory bandwidth， right， For example。

 in the fourth of your 100， we can execute 14000 giga flops，14028 giga flops per second。

But we can only provide the cores with 900 gig per second。Okay。

 and what that means is this brings us to kind of this metric of the。

Desired compute the global memory access ratio for short， I'm just starting compute to memory ratio。

 So here I mean， compute the global memory access ratio。 And here by peak memory bandwidth。

 I mean the peak global memory bandwidth。So this desired compute to global memory access ratio is the ratio of the flops。

To the memory bandwidth。Okay， and it's basically the number of times that I bike that I load has to be reused in order to advertise the memory access。

 in other words。If I can only provide my my cores with 900 gig per second， But my cores can do 14028。

Fps per second。 But for me to be able to fully utilize my core。

 for me to be able to do 14028 mega flops per second， I need to be doing 15。6 operations per bike。

 on average。So for every bitete that I load， I need to do 15。6 floating point operations。Okay。

 and remember， a floating point value is if its single precision is not one by， it's 4 bys。

 So here we're looking at 15 times 4， which is about 60。

Floating point operations current floating point value that we load from memory。

 So if I really want to reach the peak flos rate， I need to be doing at least 0 60 floating point operations for every floating point value that I load from memory。

Now， of course this is a very high number。 There aren't many applications that do60 operations for every value that they load。

What we're going to be looking at today is what is the typical number of operations per life that obligation do and what we can do in order for us to improve to bridge this disparity between the Fb Street and the peak memory bandwidth？

Let's， let's do an example。So vector addition， if we look at our vector edition example。

 we saw that every thread in the vector addition was doing z of I is equal to x of I plus y of I。

Okay， so just by looking at this code， what is the expected compute to global memory access ratio that you think we can get from this vector from the vector edition kernel。

 Okay， and let's ignore story operations for now， let's only focus on loads， Okay。

 so what is the what is the ratio of operations to bytes loaded by the vector edition kernel。

One operation every two bytes。Asuming x and y are 1 byte。So we do one operation every two bytes。

 but remember this is a floating point value one byte。No。

 but can like what's the floating point with。32 bits，64 bits。

 usually we've been dealing with floats so far。 So 32 bits。

 usually when you say floating point without saying anything。

 we need 32 bit by 32 bits floating point number。Okay， so one operation every 8 B， Right， exactly。

 which is 0。125。 So we do one floating point add for every two floating point values。

 which is 8 B that we load。What that means is that the vector addition kernel performs 0。

125 operations per byte。Okay， now this is very， very far away from the desired 15。

6 operations provided that we want in order to fully utilize our course。

 So you can expect that vector addition will be what compute Bo or memory now。Memory bound。Right。

 our our vector edition kernel is going to be me rebound， right， because how we。

So little operations for every bike that we load。 So most likely the GPU is going to be the cores are going to be sitting there most of the time and waiting for the memory operations Okay。

 so vector addition is highly memory bound。Okay， the the operation operational intensity or the the floating point to global limit access ratio is very。

 very low。 Okay， and this is why we did not see a significant speed up。

Because of a massive number of AUs okay we didn't see a significant speedup between a vector addition for vector addition between GPU and CPU because this massive number of AU that we got was idle most of the time okay we have this massive number of ALU that we added but the applications limited by the global memory bandwidth so these Alus are not doing useful work most of the time So this is why if we remember when we saw how much performance improvement we got from vector edition and then we looked at other computations。

 we saw that these other computations were actually giving us more speedup。

And this is the explanation for that vector tradition is memory bound。

 so throwing more compute at it is going to give you only a little bit of improvement。Okay。

 and and the sadder part here is that there's not much we can do。Okay， here with vector audit。

 there's not many， there aren't many optimizations that you can do to make it go faster。Right。

 it's such a simple kernel。 And this low ratio of operations to bys accessed is is inherent in the application itself。

Okay， now let's look at a different application。 Let's now look at。Mattrix， matrix multiplication。

So the matrix multiplication that we wrote earlier， every thread was doing this。

Okay had a loop and it was doing this。 So what is the for this particular code of matrix matrix multiplication。

 what is the， what is the what is the the operations provide the compute to global memory access ratio。

It depends on N， no。Depends on what。And。😊，The width， it doesn't depend on that。

It doesn't depend on it。At least not for this particular code。So how many floating point up。

 So some of you are asking if if integer operations count， No， let's ignore integer operations。

 So let's ignore these address computations。Right， integer is usually faster than floating point。

And ultimately， the useful stuff is to us it floating point， right。

 these editorgers are just kind of supporting operations for the real operations that we care about。

 which are the floating point operation。Okay， so how floating point operations are we doing， right。

 we're doing two floating point operations， this multiply over here and this addd over here for every loop iteration。

And how many bytes do we load8 right， So we do two floating point operations for every8 bys Our floating our compute global access ratio is 0。

25 operations per byte。 It's a little bit better than vector addition。But this is still pretty low。

Okay， this is still pretty low。ok。However， unlike vector edition。

Mattrix matrix multiplication actually has a very high potential for data reviews。Okay。

 so here we thought how， how the the specific kernel that we implemented。

How many operations it does compared to how many global memorytaes that it does？

But let's look at the potential for data reuse， okay。Let's look at how much it actually does。

 Let's look at how much it needs to do。 So what is the total number of。

Floating point operations that matrix matrix multiplication needs to do。

I have an N by N T N by N matrix giving me an n by N matrix。

 where is the total number of floating point operations that need to be done？It's not n。

 and it's not n squared。Thank you， right。N cubed and then we have and for these n cubed operations。

 there's a multiply and there's an add。 Okay， so we have actually two N cubed Okay so matrix matrix multiplication has high potential for data reviews for n by n matrix。

Okay， like you guys said， we have two un cubed operations。 What about the data that we need to load。

Okay， assuming we load every piece of data that we need to load only once。

How much data does matrix matrix multiplication use？I have two input matrices。Okay。

 and each of these input matrices has n squared values， and each of these values has four bys。Okay。

 so on total I have8 n squared bytes that I need to load。Assuming I don't load any of them redundly。

And I have N square dot product。 Each dot product is N ads plus n multiplications。

 We have two N cubed operations。So if I divide to nq by 8 n squared。

 the potential compute ratio that I can achieve is actually 0。25 n。Os per bite。Okay。

 this is this is the kind of the maximum compute dimension ratio that I can achieve。

 This is not necessarily what I will achieve。But if I， if I。

If I kind of rewrite my code in a way where somehow I can reuse the data that I access。

They access from global memory rather than having to load it from global memory every time， Okay。

 then maybe somehow I can have something that higher than this and closer to this。Okay。

 and let's see how we can do that。 But what this indicates。

 what this indicates is that matrix matrix multiplication has the potential has high potential for data reuse。

 In other words， it has high potential for having a high computer memory ratio。

Let's take a look at where this comes from。So a reuse in matrix matrix multiplication。

 every element in my input matrix introduces matrix matrix multiplication。

Is used for computing an entire row。But here， this element in blue is used for computing all these elements in orange。

Okay， so in the way that I've been paralyzing it。The threads that have been assigned to all these elements in orange are all loading the same data。

They all go to global memory and close this data。Similarly， every element in the matrix B。

Ass used for computing an entire column。So every element the threads that are computing the elements in these columns。

 every thread is accessing the same value over here redundantly from some global memory。Okay。

 and what this， what this reflects is that we have an opportunity to optimize the memory accesses in the kernel so that we can reuse the input data that we load from global memory as much as possible。

 So basically other rather than me having to load this data from global memory for each one of these output elements。

😊，Okay， maybe there is some way for me to load this data somewhere and then have maybe only some threads load this data and then other threads be able to access this data without having to go to global memory。

And what this would do is it would reduce the number of global memories。

 this would reduce the number of global memory。Acticses that we have and ultimately improve performance。

ok。So let's see how to do this， but before we see how to do this。

 let me now jump having you know given this motivation。

 let me just talking about memory in the GPU architecture。So before we saw that an SM。

Has streaming processors， and it has the chair control logic。

 and that all these Sms share access to global memory。O。Now。

 this access to this global memory typically takes of the order of 500 sites。ok。So obviously。

 going to global memoryory is not something that I particularly like to do。Now。

 the Ss also have registers。Okay， you guys are familiar with registers and a register usually takes one cycle to access right not not even that because I can the same instruction that does the arithmetic operation is going to reach from the register file and right to the register file So we access registers for free。

 You know， we get them in the same cycle that we execute our。Our instruction。Okay。

We also have an L1 cache， so an SM。Has an L1 cache。 And what， and you know。

 those of you who are familiar with computer architecture。 You know what L1 cache is。 Basically。

 when you load data from global memory， there's a cache that keeps that data there in case you access it again。

And that way， frequently access data tends to stay in the cache rather than having to go get it from Google every every time。

And there's also a shared memory and the shared memory also the L1 cache typically takes five cycles to access。

 and this shared memory is similar to the L1 cache， but it is managed by the program。So here。

 when you get something from global memory and you're frequently accessing it。

 the L1 cache kind of automatically puts that data here for you。Okay。

 but shared memory is not managed by the hardware， it's managed by the programmer。

So what the programmer can do is they can take data from global memory and put it in shared memory。

 and then they can start accessing it from shared memory and we'll take a look at how to do that。

And then finally， well， not finally， but we have another kind of on memory。

 which has the constant cache。And we're not going to talk about that today。

 we're going to talk about it later， so as the name says constant cache will hold some kind of constant data。

 also similar access time to the LM cache and shared memory。And then finally， we have an L2 cache。

And the L2 cache is on chip here。 The global memory is Dam。 It's not on the same chip as the ass。

The L2 cache is on the same chip as the Ss and all the Ss have access to the same L2 cache。

 so L2 cache is basically just a cash for global memory that's on chip。Okay。

 so this is how memory the memory memory， this is the memory architecture of a GPU。Now。

 let's look at the memory model in Kuta in the Kuta programming model。

 we saw before that gridits are divided into blocks and blocks consist of multiple threads。

 while each thread。Has access to its own private registers。

And then each of the threads in the same thread block。Have access to the same shared memory。

 so all the thread of say all can access the same data and shared memory。

 they cannot access the data in shared memory of other blocks。诶。😊。

All the threads in the grid have access to the same global memory。几。😊。

And they also all have access to the same constant memory。

 So anything in global memory or constant memory is accessible to all threads in a grid。

But the registers are private to a thread and shared memory is private to a block。

 but it's shared across all the threads in them book。Okay。😊，So someone's asking shared memory。

 constant cash and L1 cash are physically unified， right。

That that's a micro architecture detail and for example。

 in some architectures they let you configure how much L1 cache versus how much shared memory you want so you can have a kind of a tradeoff between shared memory and L1 cache so you can say I want more L1 cache less shared memory or less L1 cache and more shared memory so in that sense they're somehow unified。

Det memory is a little different。Okay， so I was asking， what about L1 cash， Well。

 is the L1 cache part of the programming model。Good question。

I guess the developer doesn't have a say in it。 The programmer doesn't right exactly。

 So the reason over here， you don't see L1 cache and L2 cash is because over here。

 I'm illustrating the programming model。And the L cache and the out cache are managed by the hardware。

 so they're there in the hardware， but we don't see them in the programming model。

 We don't have access to them。 The programmer can't manage them。O。

So but the nice thing is that we can manage the shared memory。And we can manage our registers。

 and we've already seen we've already seen how managed global memory。

 Registers are usually these local variables that the compiler manages。

 But the nice thing here is we have this constant memory that we'll talk about next time and the shared memory that we'll talk about today that that the programmer can manage and we can use。

 take advantage of shared memory in order for us to reduce how much we need to go to global memory。

 Okay， let's see how we can use this shared memory。 So it could。😊。

Gives us these various qualifiers to help the programmer specify where they want particular data to reside。

Okay， so we've already seen that Kuda Maloc allocates in global memory from the host。

 we actually have another way to allocate global memory statically。

 Kudamaloc allocates global memory dynamically， but we can actually just declare a variable and precede it with this keyword underscore underscore device underscore underscore。

 and and this has to be this global variable will go in global memory。

And the scope of the global variable will be the entire grid。

 What I mean by the scope will be the entire grid means that we have the same copy of the global variable accessible to all the threads of the grid。

So all the threads that they grid access the same copy of this global variable。😡。

At the lifetime of this global variable is the entire application， I can launch grid after grid。

 and all these grids will see the same copy of this global variable。

 And if a previous grid rises to a global variable， a later grid can access this global variable。😊。

Okay， and obviously， this global variable will have to be declared outside of the kernel。

 you can declare it inside a kernel。Okay， we also have constant data。

 so constant data is placed in constant memory， however similar to global variables。

 their scope is an entire grid， meaning all have access to the same value and their lifetime is the whole application。

And then we， if we proceed our declaration with device and shared。

 then this is how we declare a shared variable and this shared variable is going to go in shared memory。

 And now for this variable。😊，Every block is going to have a unique copy of this third。

Okay and the lifetime of the variable will be in the block only， so once the block is done。

 other blocks cannot see the shared variable of one block。Okay。So when I declare something like this。

 if I write share device shared， I don't have to write device optional。

 if I write shared and something inside of my kernel， this shared variable。

 there's going to be a copy of this variable for every different block。

 but then threads in the same block have share the same copy of this variable。

And then I have local variables。 So if I write something like int local var right and we've been using this all the time we've be declaring these local variables。

 this will go in a register and here the scope is the thread。

 meaning every thread has a unique copy of this。Okay。

 so if I write something likeentt I equals something。

 every thread is going to happen a a by and the lifetime of this eye is the thread。 when is gone。

 that eye is gone。And then finally， we have local arrays。

 so these local arrays are similar to local variables in that their scope and lifetime is the thread。

 but they're different in that they go in global memory。

So we'll and these are actually not frequently used these local arrays they're not frequent to use they are future C so in support of the C standards they're supported。

 but they're not actually frequently used by programmers Okay so we'll talk about constant memory allocation and initialization for today what we're going to focus on is shared memory or another word for the scratch patterns so today we're going to focus on this shared memory over。

So somebody's asking if we need to access shared variables， we need to synchronize。

 you're absolutely right and we'll look at how to do that today。Okay， so having introduced this。

 let's go back to。sharedhar matrix matrix multiplication。

 so previously what we did is we divided when we wanted to paralyze our matrix matrix multiplication。

 we divided our output matrix into tiles or blocks and we assigned a thread block for each tile and we assigned threads to each element in that tile。

So what you'll notice here is that the threads that compute each these four output elements all load the same row。

 they all access the same data。And similarly， the threads that compute and the four threads that are assigned to these four outputlet elements in this block are all going to load the same in a column of B。

So what can we do here， knowing now that threads in the same block can manage this have access to the same shared memory and if shared memory is fast to access。

 What can we do。Right， we can share。 We can share the input So rather than having all four of the threads processing these four elements each load。

This element from global memory， and this element from global memory。

 and this element from global memory， et cetera。What we can do is we can have the threads that are in the same block。

 somehow collaborate。To share， to load elements from global memory into to shared memory and then reuse them from shared memory。

Okay。So here's what we're going to do。Oh before I say。

 so the fact that these four threads load these same for these same column elements and if these four threads all run on the same S means that if we are。

Right， the threads might find the data in the L1 cache。

 Okay so when I load when multiple threads are loadeding the save data from global memory。

 if they load close enough in time， they might find that data in the L1 cache。 So if we're lucky。

 we can find it in the L1 cache because and recently some other thread loaded。Okay。

 but if we are not lucky， so sometimes you're not lucky， the data might get evicted from the L cache。

😡，Okay， before the thread is a the next thread that needs it is tries to add this。And on GPU。

 it's actually quite frequent for data to get evicted El and Ca， why。

Why is it more likely on the GPU for something to get evicted from the El cashment on the？

Because things can execute out of order。我呢边。Like there's no temporal locality to things。

 maybe except is there is locality。 If I， if I have two threads and these two threads are executing on the GP and they're sharing the same data。

 Okay， so there's temporal locality， but across threads， Okay， so collectively。

 they have temporal locality， right？ Why would why， why， why is it， you know。

 less likely for the the thread to find its data in the I cache than， for example， in a CPU。

 if I have two threads that are access the same data。While Sler point out L1 cache is smaller， fine。

 so caches are smaller on the GPU is another reason。

So the other reason is that I have many more threads。

Right so if I have two threads on the CPU and they're accessing nearby data。

Right so then then they're very likely to find that data in the cache。But on the GPU。

 if I have 2048 threads running on the GPU， if two of those threads are sharing data。

 while there's so many other threads that are not。😡，Okay。

 so the probability of getting your data evicted is very high。And for that， you know， if you know。

 sometimes we might want to rely on the L1 cache， but for some things， but for some things。

 where where we know that the data we use is extremely high like matrix matrix multiplication。

 it's probably better for us not to rely on the L1 cache。

 but to try and do the caching ourselves using shared memory So the solution here is to let the threads work together to load part of the data。

And ensure that all the threads that need to use access it before we load more data。

 And we're going to use shared memory to ensure that the data stays close by。

 And this optimization is， is called piling because we divide our input into tiles of data and we load those tile to shared memory and let all the threads access them and then load the next file。

 etc ceter。 So let me show you what tiling for matrix matrix obligation。 So here if I have a these。

 if I， if I am。If I have this matrix that I I divided it to tiles and I signed a thread block for each tile。

 So here， the thread block that's assigned to this center tile over here has a thread processing each of these input elements。

Okay， what I can do is I can divide my input matrices as well into tiles。

And then rather than having each of these threads load all the elements they need from Google memory themselves。

 I can have this block of threads。Load the blue tile of a into shared memory and the blue tile of B into shared memory。

Okay， so now I have So the step one is to load the first tile of each input matrix into the shared memory。

And then I will have the threads that are assigned to this output tile of the matrix access shared memory to do the partial dot product。

Okay， so each thread is going to do a partial dot product on these tiles of shared numbers。

 so the thread for this first element。We'll go through shade memory and access this row。

 as well as this column。The thread responsible for the second element will add thiscer row from sharedd memory and this column。

 etc cetera。Okay。😊，And then all these threads finished wait for each other to finish accessing this shared memory。

 Okay， and when they're done， I can go back to my local memory and bring back and bring in my next style。

 So then these threads。😊，Go the next time from sharedd memory。Okay， and then the next step。

 until we are done。Now what do you notice here， what you notice is that this thread that was responsible for loading for processing this element。

Before it was loading all the points of the rowve。Now， it's only going to load one。2。

Three elements from A。The other elements are going to be loaded by the other threads into shared memory。

 and this thread is going to be able to access them from shared memory。Okay， is a spirit to everyone？

Any last appointment。So before。In my original matrix matrix multiplication code。

 every thread was loading an entire row of A and an entire column of B。Okay， now every thread。

 so now what happens when I go to T。Is that these four by four threads。

I they load is 4 by four tiles。 threadread is every thread in a site。

And my thread block is going to load to one element in this time。Oposed loop， urgently。

 in this thread was not load 1，2，3，4 elements。From this tile。

 But now it's only going to load one element from this title。

 The other elements will be loaded by the other threads。

 and then this thread will exit from shared memory。Okay。

 so for every thread is going to do a global memory load once per tile as opposed to once per element。

 okay。So every thread loads once。And they all access from shared memory four times。Okay。

 and rather than loading four times， and then again。

 every thread will load once instead of four times， but the access from shared memory four times。

 and then again， every thread will load once and then access from shared memory four times。

Okay so in general， if I have a tile widths by tile width tile size。

 then every thread will reduce its number of global memory aes by the tile widths because rather than loading the entire row。

 they do one load for every tile width elements， and then they access tile width elements from the shared memory。

Okay。😊，Clear。😊，All right， let let's write a code example to make this more concrete。



![](img/2700d7d129b2fd03a595532953820cdb_2.png)

I'm going to switch now to my code。Oops， I got disconnected once second。Okay so here。

 this is the previous matrix matrix multiplication code that we wrote。

Here you see we have row column。 We initialize a sum。 We loop over the entire。

 we loop over the entire dot product， and then we do we accumulate the sum to the sum and then we store the result。

 Okay， so let's compile this code and remember what how it performed。 Okay。

 so here this is the performance of my CPU code and my GP code。

 So it was 2 milliseconds on the GP for the kernel itself。

 The whole with the copy time it takes around4 milliseconds。

 So now let's go and try and implement this optimize we talked about where rather than doing things this way。

We use tiling， can remember tiling， okay？So I'm going to get rid of this code。😊，Okay。

 I still have every thread responsible for a specific chrom and a specific column。



![](img/2700d7d129b2fd03a595532953820cdb_4.png)

But this what I'm going to do is rather than having the thread loop through the entire row。

 what I'm going to do is I'm going to loop through the tiles。

So the thread blocks in the the threads in the same block are together in a loop through the tiles。

 Okay， so how many tiles do I have。

![](img/2700d7d129b2fd03a595532953820cdb_6.png)

Well， I find here a variable tile dim， So tile dim is 32。

 so my tiles here are going to be 32 by 32 and my block size is also going to be along the lines of my tile。

 So my block size is also be 32 by 32 because I have I have one thread per block for every one for every element in my output tile Okay so so the number of and the number of tiles that I have is going to be n over the tilewin。

 So if my block is 332， then the number of tiles is going to be n over 32 Okay so here the first thing that I'm going to do。



![](img/2700d7d129b2fd03a595532953820cdb_8.png)

![](img/2700d7d129b2fd03a595532953820cdb_9.png)

As I want to。Loop over。Tile， so I'm gonna to callm uns end tile equals 0。Child is less than and over。

Ted them。N plus， plus type。So this is my first step。



![](img/2700d7d129b2fd03a595532953820cdb_11.png)

Now， when I loop over this tile， what do I want to do So for every tile。

 you know now tile first tile is going to be0， then my file index is going to be one。

 then my how and it's going to be two， etc ceter。 Okay， so now that I'm working on a specific tile。

 What do I want to do。 Well， I want to load this tile into shared memory。

 and I also want to load the corresponding B tile into shared memory。Okay。😊。

Now guyss asking me how I chose TLD， I'm going to talk about a little bit about that later， Okay。

 so hold on to that question， but for now I'm just going to set T in to be 32 by 32。



![](img/2700d7d129b2fd03a595532953820cdb_13.png)

![](img/2700d7d129b2fd03a595532953820cdb_14.png)

That2 by 32。So now what I want to do is load this data into shared memory and to do that I need to declare a arrays in shared memory。

 so what I'm going to need is I'm going to need two dimensional array shared memory that's T widths by T widths to store a and another two dimensional array shared memory to store Tle widths by T widths。

 tile of B。

![](img/2700d7d129b2fd03a595532953820cdb_16.png)

Okay， and the way I declare that is as follows。 I'm going to write。Remember。

 we have the shared quaifier， sorry right underscore underscore， share underscore underscore， okay。

 and then float。And then A and a convention that you don't have to follow。

 but that I sometimes follow is underscore S whenever underscore S that's just to remind me that this is a shared memory variable。

Okay， and this two dimensional array is going to be tile width by tile width in size。

 so I'm going to have tile width。By T with shared memory array for a。

 and I also want a T by T shared memory array for B。 Okay。

 so I'm also going to declare a T width by T width shared memory array for B。Okay。

 now what do I do Now that I have this shared memory arrays Now what I want to do is to load I want。

 I want each thread to load one element。

![](img/2700d7d129b2fd03a595532953820cdb_18.png)

Okay， of the global memory tile and put it in the shared memory tile Okay。

 and that of course comes to what happens here， I want each thread to load a global memory tile and load it into a shared memory tile。

Okay， let's do that。So here， the thread over here is thread over here at row is going to be and column is going to be responsible for loading this element over here of a。

 so same row。Okay， but it's but but then it has to use the tile to somehow find the column。



![](img/2700d7d129b2fd03a595532953820cdb_20.png)

Okay， let's how to do that。So what we need to do is we need to load into a of S。Okay。

 I'm going to give a thumb index。And in some other index， I'm going to load a。

And then a when it access to a， I'm going to give it some index times the width of a， which is n。



![](img/2700d7d129b2fd03a595532953820cdb_22.png)

![](img/2700d7d129b2fd03a595532953820cdb_23.png)

Plus。😊，Com index。Okay， and then similar these for。To load into B of S at some index， some index。

From B of sum index times n plus sum index， so now we need to figure out these indices。O。Now。

 let's first start at where we're loading from a。 So if a thread thread that's responsible for row and call。



![](img/2700d7d129b2fd03a595532953820cdb_25.png)

Okay， the thread responsible for this element is going to load this element。 Well。

 what is the index of the what is the row index of this element。

 Well it's going to be the index of the tile。Okay， times the size of the tile。

 actually let me go to the next just to make us more clear。

 So here for this thread wants to load this element。

 So this the index of this element is going to be the index of the tile。 Okay。

 times the size of the tile， which is tiled in and then plus well。

 thread the thread that has thread index do y 0 is going to load。Actually， I let me focus on A。

 not on B first。 So here I'm going to load tile。Times the the tile index here is one。

 times the tile width， which is4 in this illustration is going to be 32 in my code。 Okay。

 and then plus the thread that has thread index dot x is going to load tile times T width plus plus 0。

 So the thread with3 x that x 0 is going to load tile times T width plus 0。

The thread with thread index that x equals1 is going to load tile times tile width plus1。

 The thread that has the index that x equals 2 is going to load tile times tile width plus 2。

 etctera So in general。

![](img/2700d7d129b2fd03a595532953820cdb_27.png)

Okay， I'm going to load from the same row。嗯。Sa row。



![](img/2700d7d129b2fd03a595532953820cdb_29.png)

Okay。Times n to get here。 And then the offset from here to the element that I want is going to be the tile index times the tile width。



![](img/2700d7d129b2fd03a595532953820cdb_31.png)

The trial times。

![](img/2700d7d129b2fd03a595532953820cdb_33.png)

Filed in。And then plus， over here， the， like we said。

 it's the thread index dot x equals 0 will load just the element at point at right offset 0。

 The one with one will load element offset 1， et cetera。 So it's going to。



![](img/2700d7d129b2fd03a595532953820cdb_35.png)

Thdinex dot。

![](img/2700d7d129b2fd03a595532953820cdb_37.png)

Okay， and then where do I put this result， well， if we go back to this illustration here。

 when this thread loaded this element from here， regardless of what tile this element was in and always put it at element zero so the thread that loaded the element at index 00 in the tile is going to put the in this tile is going to put the element at00 in the shared memory tile。



![](img/2700d7d129b2fd03a595532953820cdb_39.png)

ok， so。This the shared memory， we're going to use the threat index to store the results。

 It's going to be threat。Inex dot Y， and。Treat index index index。Okay， in other words。

 the thread responsible for this output element will load into this element。

 the thread responsible for this output element will load into this element， et cetera。

 so that the thread index within the block is going to be the index into the shared memory tile that we used。



![](img/2700d7d129b2fd03a595532953820cdb_41.png)

![](img/2700d7d129b2fd03a595532953820cdb_42.png)

喂。😊，Now， same thing for block index dot X for block indexd dot x。



![](img/2700d7d129b2fd03a595532953820cdb_44.png)

If we if we， if we look at block index x， for example， sorry for BS。 So for BS。

 where we want to load from the tile of B。Okay， so it's going to have same column index。

 So this thread is going to load this element。 This thread is going to load this element。

 This thread is going to load this element。 This thread is going to load this element。 Okay。

 so the column index is going to be the same as the thread itself。



![](img/2700d7d129b2fd03a595532953820cdb_46.png)

ok。

![](img/2700d7d129b2fd03a595532953820cdb_48.png)

This is going to differ。The row index is going to be a tile index。

Times the size of the dimension of the tile that brings us to the beginning of the tile so here。



![](img/2700d7d129b2fd03a595532953820cdb_50.png)

My row index is going to be tile times。Ted then。

![](img/2700d7d129b2fd03a595532953820cdb_52.png)

Okay plus。The thread responsible， the thread that has thread index dot y is 0 responsible for this element。

 and it's going to load this element。 So there's no offset。

 The thread with thread index dot y is one is responsible for this element and it's going to load this element in the time。

 Okay， so the index is going to be thread index dot Y。



![](img/2700d7d129b2fd03a595532953820cdb_54.png)

ok。Where is this result going to go， Well， again， you know this style is going to be loaded into a shared memory array that just has this value over here。



![](img/2700d7d129b2fd03a595532953820cdb_56.png)

Okay， so if we go back to this illustration here， the thread is going to use its own local index to store to the tile。

Okay， context where the was。Sorry。Can you repeat why it's thread dot wildil。

 and it was lagging muchmal。

![](img/2700d7d129b2fd03a595532953820cdb_58.png)

Oh， you mean over here。Yes。Yes， me let me let me repeat that。



![](img/2700d7d129b2fd03a595532953820cdb_60.png)

Over here this thread is responsible for loading this element。

 this thread is responsible for loading this element， et cetera。

 so how do I get to this element well it's going to be the number of elements in the previous styles which is tile times the dimension of the tile plus the position of the thread in the thread block。

Right so the threads this thread， the thread 0，0 in the thread block is going to load element 0。

0 within the tile。Okay， that's why we use the thread in index dot y to figure out which element to load。

可。

![](img/2700d7d129b2fd03a595532953820cdb_62.png)

好。All right， so here similarly， we're going to use。Fd index why。And。Get index index。嗯。

So now what we have done is we've loaded the this tile。



![](img/2700d7d129b2fd03a595532953820cdb_64.png)

Of B and this tile of a into shared memory。 Okay， now what we want to do is we want to compute with them。

 Okay， so we're going to loop over the shared memory tiles and do the dot product of this partial row with this partial column。

 for example。Okay， how do we do that？

![](img/2700d7d129b2fd03a595532953820cdb_66.png)

What we do， what we simply move what we do four。I and。系。Is equal to 0。 I is less than what。 Well。

 here is looping through an individual tile。 So partial partial row an individual tile。

 So I'm going to I is less than tile dim。

![](img/2700d7d129b2fd03a595532953820cdb_68.png)

![](img/2700d7d129b2fd03a595532953820cdb_69.png)

And then plus plus I。ok。And now I'm looping through a specific a specific title。

 Let me actually show you a different illustration for this。

 So here now I have these tile in shared memory and I' want to loop through them。 Okay。

 this thread is going to loop through this this partial row and this partial row。😊。



![](img/2700d7d129b2fd03a595532953820cdb_71.png)

Okay， and it wants to accumulate them。Into a part I want to do a partial dot product。

 so that's why it goes from Michaels zero to tile them。Okay。

 and then I want to declare a variable to do the accumulation。 So I'm going to clear it out here。

 I'm going to right float。

![](img/2700d7d129b2fd03a595532953820cdb_73.png)

三。0。0 F。Okay， and now here I do the accumulations。 I do some plus equals。 And this time。

 I want to look elements from my tile。

![](img/2700d7d129b2fd03a595532953820cdb_75.png)

Okay， so what am I going to do if I have this thread over here with this thread index and thread index do X and this thread do y。

 I'm going to load from the A tile at the same thread index do y。Okay。

 but'm going to but it going to be iterating through these elements。



![](img/2700d7d129b2fd03a595532953820cdb_77.png)

Okay， I'm going to load from a underscore S of current index the dot y。And then I， okay， times。

 and then this thread over here is is going to have the same column index。

 which is going to be thread indexded dot x。

![](img/2700d7d129b2fd03a595532953820cdb_79.png)

But then I is going to be iterating through the rows。 So here I'm going to use the underscore S of I。



![](img/2700d7d129b2fd03a595532953820cdb_81.png)

啱啱。Treread index dot X。ok。So I learned these tile from shared memorymin。

And then I compute using the tiles in。

![](img/2700d7d129b2fd03a595532953820cdb_83.png)

Okay， what am I missing here？So after I load these tiles I compute with them on the next iteration what happens and'm going to load the next tiles and I'm going to compute with the next styles and the next iteration I'm going to load the next tiles and compute the next tiles Okay and yes。

 you're absolutely right what I'm missing here is synchronization So here I have different threads they're working together to load these tiles and they're working together to compute these tiles。

 but I might end up in a situation where if I just run this code the way it is。

 I might have in a situation where these threads load the tiles。



![](img/2700d7d129b2fd03a595532953820cdb_85.png)

几。😊，Threads finished loading the tiles and start computing before the other threads have loaded finished loading the tile。

 Okay， so maybe this thread， Okay， loads this element and this element， and it starts computing。



![](img/2700d7d129b2fd03a595532953820cdb_87.png)

But， but this this thread over here hasn't finished loading this element over here。

So if the first thread over here reads this element over here before the second thread over here has finished loading it。

 we have a problem， so when the threads load the data from the tiles they have to wait for each other to finish。

Before they proceed to compute。

![](img/2700d7d129b2fd03a595532953820cdb_89.png)

Okay， so what I need here is I need a。Think。😊，And then also， but adds compute。



![](img/2700d7d129b2fd03a595532953820cdb_91.png)

Okay， when these threads compute， if a thread finishes computing。

 So if this thread over here finishes computing and it goes and starts loading the next element of a。

 but this thread over here at the end hasn't finished computing yet。

 It might load the wrong element of a right this first one finishes computing and loads a new value of a。

 but then this one hasn't hasn't used the old value of a。 We have a problem。

 So the threads need to need to all finish computing before they proceed to load the next tile。

 So we also need a sync threads at the end over here。



![](img/2700d7d129b2fd03a595532953820cdb_93.png)

ok。😊，And then finally， once we're done with this， we've accumulated our sum across the tiles。

 we can go and we can store the result back。To C。 So here's C of row times n plus call equals some。

Okay， somebodys asked， where does some reside while some is here there's going to be a register。

It's probably going to go in and register。All right， any questions， this is clear to everyone。

The professor had made the tile to be as big as as a。



![](img/2700d7d129b2fd03a595532953820cdb_95.png)

Swarm or warp could we have guaranteed synchronization without the synchronized function？



![](img/2700d7d129b2fd03a595532953820cdb_97.png)

Well， if we make the tile as big as the war， we have several issues。

 which is our our blocks are going to be small okay， but then the other thing is no。

 there's no guarantee that tiles there's no guarantee you should not assume that that。

Threads in the work are executed。even though they do。

 you should not assume it because the compiler might make an optimization where it reorders things and that assumption goes there and what you're assuming goes away。

Oh okay， so no， don't don't assume that threads in a war execute synchronously for correctness purposes。

 but you can assume it's for optimization purposes。Okay。So， for example。

 if you don't put the sink threads over here。And you don't put the same threads over here。

 you know maybe the compiler detects that something is reused， your sorry something in shared memory。

 and then you're loading it the same thing again，t so it just accesses an old variable or recomputees it rather than loading it again from shared memory or something like that。

Okay， you should not， you should not make that assumption。All right。

 so let's having written this shared child code， lets and see how it performs link。

And I'm move to run。Okay， and。This is our new performance， now。Which is quite an improvement。

 so we're little more than two times faster because of shared memory time。Okay。



![](img/2700d7d129b2fd03a595532953820cdb_99.png)

And that is because we were able to reuse data and reduce the amount of global memory ades that we are making。

This is the code that we wrote。Now， a few things to be careful about when we are repeat this kind of code is boundary conditions。

 we always come and look at boundary conditions。So one thing to be careful about with boundary conditions here in the previous。

In the previous application that we implemented， we simply deactivated all the threads that were not computing any output elements。

 and we didnt the whole computation。That's what we did。 But here we have to be careful。

 Why let's say we have a thread block that's responsible for these elements over here。

 And youll notice because of boundary conditions， some of these output elements are out of bounds。

 So some of the threads in the thread block assigned to this output file are not going to be computing any output element。

诶。However， let's say this over here， this thread this here represents the threads that are active during the computation。

😡，When I'm processing this output tile， okay， for the first tile， I'm going to load this input。Okay。

 so these are the threads that are going to be active that need to be active when I' loading the input tile。

Okay， when I load this input tile over here， okay， these are the threads in the block that will be active when I'm loading the second input tile。

And then when I compute the output element and store it。

 these are the threads going to be active when performing the dot products and storing the result。

And what that means is that we have different primary conditionss for loading the input tile。

 loading the output tile and computing and scoring the results。

 So this is something you should be careful about。 you can just simply guard the whole kernel with if row is less than n and column is less than n。

Okay， because if you do that， you might deactivate these threads。

 but these threads are going to be needed and loading input tile or loading from the other input tile。

 even though they're not needed in the actual computation。

 So sometimes some threads are just used for loading loading tiles。

 but they're not used for computation。ok。And of course。

 another thing to be careful about is that you will have an assignment and in the assignment you'll have to deal with matrices with different dimensions。

 so I could have an M by K matrix and a K by N matrix and an M that produce an M by N matrix and these boundary conditions make things further complicated when you're implementing。

A tile matrix matrix multiplication， okay？Is that clear to everyone？Okay， somebodys asking。

 why do we need the。

![](img/2700d7d129b2fd03a595532953820cdb_101.png)

The thing。The reason we need the second thing is that some threads might finish the computation and proceed to load the next style。

 but the other threads that are still doing the computation are accessing data from these tiles。

 so a thread might load the developers of the next style before the other threads are done using the old values of the tile。

是。

![](img/2700d7d129b2fd03a595532953820cdb_103.png)

O。Okay， so it turns out that we can actually also do time on the CPU。Okay。

 so Tling also works for the CPU and now on the CPU， there's no scratch pad memory。However。

 Tling is frequently applied on the CPU and it relies on the caches。 Why is it on the CPU。

 I can rely on the caches。There are less caches， less threats， Right， exactly。

 So the cache is sufficiently reliable on the on the CPUU because there are fewer threats running So there's and the cache is larger。

quickly show you how to apply Tling on the CPU。By the way， I hate going over class time。

 but this is really interesting to me， you don't have to stick around if you don't want to do this。

 I think we're done with the important material for today so you don't have to stick around。

 but if you're interested in seeing how to do tiling on the CPU feel free to stick around and and you can get to see what it looks like。



![](img/2700d7d129b2fd03a595532953820cdb_105.png)

Here， let me go and look at the CPU code。 So remember。

 our CPU time was around in the order of 200 milliseconds。 Okay。

 so now let me open the CPU code and let's see what Tling would look like on the CPU。So here。

 rather than looping through the row and the column and also loop through the elements of the dot product。

 what we can do is we can loop over row tiles and then column tiles Okay。

 so what we can see to you sequentially following。

![](img/2700d7d129b2fd03a595532953820cdb_107.png)

嗯。We can sequentially go through our our files， our input tile。

And then go through sequentially our output tiles。 And then for every output tile input combination。

 we can sequentially go through our output elements。 Okay。

 and for every one of these output elements we can go go through them and do the dot product。 Okay。

 so the way that our C code is going to look like is as follows， we're going to do for every。😊。

Rrow tile for every column tile。 for every input tile。And then for every row and within the tile。

 for every column within the tile。 And then we're going to do the dot product。Yes， let's see。

What that look。

![](img/2700d7d129b2fd03a595532953820cdb_109.png)

诶。😊，So I'm going to take this and actually， let me just get rid of this and start from scratch。

So I want to loop over every row tile， Okay so I'm going to do four unsed and row tile is equal to zero。

And how many row tiles do I have Well the number of tiles that I have is n over the tile there。

 So I'm going to do。Protile is less than end over。And then plus plus row tile。Right。😊。

And then I'm going to do a little more of my column tasks。

 I'm going to do four unsigned and column tile is equal to0 column tile。

Is less than an over piled in。Qu plus。Colum tile。Okay， and I'm going to loop over my input tile。

 because I'm going to do four unsigned and I tile is equal to 0。 I tile is less than。

And over tiled in， and a plus plus I tile。ok。😊，And then now what do I do？

 Now I'm going to go through the elements within the tile。Okay， so I'm gonna do。 So I have。

 I have tiled in by tiled in tile。 And I'm gonna to do the element。 Go to the elements with the tile。

 I'm going do four。Unsigned end， my row is going to start at the beginning of the tile。

 which is going to be the row tile。Times the tile then。The role is equal to。

Row tile times tile them Okay， so zero， so if Im in the if I'm in the you know。

 if I'm in some row tile， if I'm in row tile 0， the row is going to be 0。 If I'm in row tile 1。

 the row is going to be the first row is going to be 32 and then row tile2。

 the first row is going to be 64， etctera。And then I'm going to do row is less than。

Rotile plus one times。And styled them。Okay， I'm gonna do plus plus row。

And then I'm going to loop over the columns within the tile side before unsine n call is equal to zero。

 sorry， call is equal to call tile times。Ted them。Call is less than。Call tile plus 1。

thenAnd un request plus column tile。Okay， and then now here I'm going to do the dark product within the tile。

Okay， so I'm going to declare some float。Some is equal to 0。0 F。

And then I'm going to loop over the elements within the tile。

 So the way I do that is as follows as I'm going to do four。Unsed and I is equal to。

 and then similar to the row in the column， the I is going to start at I tile。Times filed in。

And it's going to end at。呃。嗯。5 tile plus one。Times。Tll them。And we're going to increment。系。Okay。

 and now what I'm doing is I'm loop over the elements within the tile。

 So now just suppose it's going to look just like the other code。

 I'm gonna have some plus equals a of row。嗯。And plus column。Oh sorry， plus I。Okay。

 times B of I times N。好。Okay， and then finally， I need to write the result back。Okay case。

 I write C of row times n plus column。Is equal to sum。

 But here I actually have to be careful because the I， I can come back in later tiles and write some。

 So here， So here， because I'm sequential， all the different elements within an output tile are sharing the same sum register。

😊，Okay， so what I need to do is for the first tile， I'm going to write out the sum。

 but for the remaining tiles， I need to accumulate this。I'm going to do F， I。Pile is equal to0。

Then I write out the thumb。Otherwise， for the later input tile， I'm going to。AHumulate。ok。

So this is what the tiled CPU version looks like and if you look at it closely you can see that this over here corresponds to the different thread blocks in the y dimension。

 this over here corresponds to the different thread blocks in the X dimension。

 this over here corresponds to the tile loop in our kernel。

 this over here corresponds to the different threads within our block in the y dimension。

 this loop here corresponds to different threads within our block and the x dimension。

 and then this here corresponds to the inner loop in our kernel。

 you can see a nice correspondence between the sequential version and the parallel version。Okay。

 and if you compile this。And we run it。It doesn't finish because we have a mistake somewhere。嗯。

Let me see figuresers。Oh， there's no mistake。Should be post plus column， not post plus。Okay。

 let's compile this。And run it。And you'll see that the CPU time is also almost twice as fast because of tiling。

 The ti is also beneficial on the。

![](img/2700d7d129b2fd03a595532953820cdb_111.png)

ok。😊，So this is the code shared using shared memory also has an impact on occupants。

 so you' noticed that before just like just like you know we have a maximum amount of threads a maximum amount of blocks that we can have that we can have in the As。

 we also have a maximum amount of registers and a maximum amount of shared memory that we can have。

So the Vol， we can have 60。Some threadreads in an time and 96 kilobytes of shared memory。

 So if we use too many registers or too much shared memory we could we could run out of register or shared memory before we run out of threads。

 So this is another thing that one needs to be careful about when using shared memory。

 you can't use too much shared memory and you can't use too many register。几。😊。

And then the final point is that we can dynamically allocate shared memory so far in our shared memory code over here。

 we've been kind of statically allocating the shared memory。

 so here the shared memory is always a 32 by 32 array but in some cases you might want to dynamically allocate shared memory and the code allows you to do that so shared memory can be dynamically allocate it and the way to do that is by declaring it like this X shared a underscore S and then you can provide actually a third configuration to the kernel where you're specify the size of the shared memory array that you okay。



![](img/2700d7d129b2fd03a595532953820cdb_113.png)

![](img/2700d7d129b2fd03a595532953820cdb_114.png)

And with that said。Read more about what we covered today in chapter four of the textbook and that's all for today and I will see you next time。

8月份。

![](img/2700d7d129b2fd03a595532953820cdb_116.png)

Perfect。