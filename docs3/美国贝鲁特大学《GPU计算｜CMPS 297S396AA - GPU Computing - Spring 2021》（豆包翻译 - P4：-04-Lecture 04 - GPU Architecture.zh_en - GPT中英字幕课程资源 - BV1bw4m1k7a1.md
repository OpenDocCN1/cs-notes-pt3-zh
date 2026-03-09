# 美国贝鲁特大学《GPU计算｜CMPS 297S396AA - GPU Computing - Spring 2021》（豆包翻译 - P4：-04-Lecture 04 - GPU Architecture.zh_en - GPT中英字幕课程资源 - BV1bw4m1k7a1

![](img/dc7eda33d312150061530193033d07dd_0.png)

Hello everyone and welcome to our fourth lecture of GPU computing Today we're going to take a little bit of a break from writing code and we're going to talk about the GPU architecture。

So before that a quick overview of your last time， last time we looked at how to create multidimensal grid。

How to store and access multidimensional data， and we did three examples throughout the lecture of writing data parallel code that manipulated two dimensionional data。

 Our first example was converting an RGB image to a grayscale image and we said that straightforward parallellyization approach was to assign one thread for every pixel in the image to be responsible for generating that pixel from the corresponding RGb pixel and we saw from this example that we can we can create twodial grids So a grid with with you know an X and y number of blocks and each block itself could be twodial array of threads and we saw how the block index and thread index and the grid them and the block 10 variables all have X。

 Y and z components that we can use。We also saw that our data。When we， when we can really allocate。

A two dynamically allocate a two dimensional array and pass it to a coa kernel so if we want to dynamically allocate data to two multidimensional data。

 we actually have to lay it out as as a one dimensional array and the convention for storing multidimensional data and one dimension in C is the row major order this contrasts with fortran。

 for example where the convention is column major。So the conency is to store data in row major order what that means is that you store all you store all the elements of the first row fold by all the elements of the second row。

 et ceter。 We also looked at how we have to worry about boundary conditions。

 And since this is a multidimensional grid。 when we do our boundary checks。

 we have to do our boundary check across multiple dimensions。

 So this was the RGB to gray kernel that we wrote we saw how to use the DX and the Y variables to get a multidimensional index for the thread and how to do a multidimensional boundary check and also how to do access a linearized multidimensional array。

At our second example which was image blur and that was very similar。

 the boundary check was a little bit more complicated because the boundary check on the input was different from the boundary check on the output so there was a little bit more complexity with this example and then finally we looked at matrix matrix multiplication as our third example last time and we said that a straightforward parallellyzization approach here was to assign a thread for every element in the output matrix and that thread would sequentially loop over the corresponding row in the matrix A and the column in the matrix B。

So these were the three examples that we covered last time。

 any questions about multidimensional arrays or data before we continue to talk about architecture today？

🤧Yeah， I have a question。 So in the first lecture， you told us。

You told us that 1024 is the maximum thread per block。was like a 1D area。

What if it was a 2D or a 3D already Okay， excellent question。 So yes。

1024 is not a limit on the dimension。 It's a limit on the total number of。

So if I have a multidimensional thread block， then the total number of threads cannot be more than 1024 so for example I can have a 32 by 32 thread block that will be 1024 I can't have 1024 by 1024 thread block so the limit is on the total number of threads not on the dimension there's also a limit on the dimension of a grid but that's fairly large and you can always look those look those things up。

Okay， thank you。 But where does the limitation come from， Just a curious question。We。

 we'll talk about that today。Okay， thank you。 Yeah， you're welcome。ok。Alright， great。

 any other questions。Alright， let's move on。 So today we're going to be talking about the GPU architecture。

 So to start off， a GPU consists of multiple streaming multiprocess。Okay， we call or for sure。

 we just say Ss。Every stringing multiprocessor consists of multiple cores。And these are you know。

 by course， we mean these units that can execute execute arithmetic operations。Okay。

 and the cores in the S M share some kind of control。 Okay。

 so by mean the different kinds of control logic the processors usually have。To execute instructions。

And they also share some kind of memory Okay， so the GP is broken down into many Ss。

 Each S has many cores and these cores share control logic and they also have a shared memory Okay。

 and then of course， all the Ss have access to the same global memory。

This is the same global memory that we discussed in in the first lecture。

 We said we copy from the CPU memory to the GPU's global memory。

 So this is the GPU's global memory that we copy that we copied。

 So all the Ss can access this global memory and HSM has a bunch of cores。

 some control logic and some memory inside of it that could use for various purposes。

 There's actually different types of of memory on the S that we will look at。As a typical example。

 the volt of U 100 GPU， which is the GPU that is available in the servers that you are using in the course。

 a  Volt of U 100 GPU has ATSMs。😊，And each of these Ss has 64 cores， so you have ATSMs。

 each SM has 64 cores， so this is a total of 5120 cores Okay， so this is how how much processing。

 how many processing cores a vol of your 100 GPU has。

Now the question is how do we the code that we wrote right so when we wrote code we we configured these grids and these grids had were divided into blocks and these blocks were divided into threads so the question is how do we take these blocks and grid these threads and run them on a GPU。

Well， the way it works is that threads are assigned to a sense at a block granularity。

 And what I mean by a block granularity is that every thread block。Is going to be assigned to an As。

All the threads in the same block will be assigned to the same S。Now we can have multiple threads。

Sorry， multiple thread blocks assigned to the same S。 That's okay。 So this this illustration here。

 each of them has three thread blocks assigned to it。 However。

 we cannot have the threads inside of a thread block。

 some of them assigned to one S and some of them assigned to another S。Okay。

 all of them have to be assigned to the same as。Now， these threads， when they run on these SMs。

 they require resources right so every thread requires resources， so they need things like registers。

 maybe they reserve some memory there's also some slot for some thread specific thread specific you know control data。

 So threads and the thread blocks， they require resources to execute。

 So the FM can only a limited number of threads per block at once。

 Okay so hopefully this answers the question earlier about you know why is there a limited number of threads in the block。

 Well， well， part of the reason is that all these threads in the block need to run on this SM。

 but thisM has a finite amount of hardware so it can support a finite amount of threads at the same time。

Okay， so。Because the SM each S has a limit that can support a limited number of threads at the same time。

Okay， we can only have a limited number of thread blocks running。On the entire GPU at once。

And because we can only have a limited number of blockss on writing on the entire GP at once。

 if we launch a br。That has more blocks than we can run simultaneously。

 What happens is the remaining thread blocks are going to sit there in some。

Q and wait for their turn。 Okay， this is not an actual。

 Its kind of maybe it could be closer to a counter if Q may。So。

There is going to be these threads are logically going to be waiting until the thread blockss that are executing on these Ss finish their execution so that these new thread blockss can come and start executing。

Okay， so we have SMs， we have threat blockss， all the threads in the block need to be on the same as。

 the S can support multiple blocks and a grid can have many more blocks then the number of blocks that can execute simultaneously on the entire GPU so if we have if we have extra if we have more blocks then these blocks will wait until one block is done so that they can come and execute in a split Any questions。

Yes， doctor， when you say the block is assigned to an SMM， is it assigned。

Then the block itself is assigned to one core of the SMM or are the threads divided over the course。

No， the thread block is assigned to the SM， how these threads execute on the course is something I will talk about shortly。

Okay， but for now what you need to know is that this thread blocklock is assigned to an SM and what that means is that each of these threads in the thread block is going to reserve resources like registers for itself on the S。

O。Other questions？Allright， so so this brings me to an important point to which is synchronization。

 So these threads because the threads in the in the same block are assigned to the same ascent。

 they can collaborate in ways that threads in different blocks cannot Okay。

 and this is previously you guys asked me， you know。

 what is what is this the purpose of dividing grids into blocks。

 Why can't we just have a grid of threads。 Well， the reason is that threads in the same block can collaborate with each other in ways that threads that are in different thread blocks cannot。

😊，One of these ways is barrier synchronization so threads in the same block can execute a call this function or execute instruction sync threads and what sync threads does is it allows threads that are in the same block to wait for each other at a certain point in the code before they can all proceed。

😊，Okay and barrier synchronization is common in parallel programming。

 we're not going to look at an example of how to use barrier synchronization today。

 we will look at one later， but for now I just want you to be aware that threads in the same block can you communicate with each other and one of the ways they can communicate with each other is by waiting for each other so executing some kind of code one thread they can execute this barrier and what the barrier says is that all the threads need to arrive at this barrier before any of them can proceed and this helps them coordinate work coordinate work for each other across each other。

O。呃。Another way that threads in the same block can collaborate is using some kind of shared memory。

 so there's this shared memory on the aN that threads in a same block can access that threads in different blocks cannot access。

And this is another way of collaborating and this is also something we will take a look at how to use later on。

 and there are also other ways that will we will not discuss today， but we will discuss later。Okay。

 but the idea is that threads in the same block can collaborate because the threads of different blocks cannot。

And this is the motivation for assignings to assigning threats to a on a block where。

So when we assign threads in the same block to the same S。

 this makes it easier for us to support collaboration between these threads efficient。

Right when the thirds in the same block are on the same as that means when they need to synchronize with each other when they need to wait for each other。

 they don't have to communicate across ass with each other because they're all in the same as。

 so it makes that kind of collaboration between them more efficient to support。Another important。

All the threads in the block are assigned to an SM simultaneously In other words。

 if I have 1024 threads in my block， I cannot assign 512 threads and if I have 124 threads in my block and there's an SM that has 512 thread slots free I cannot assign 512 threads of my block to that SM and then wait for them to finish and then assigned the next 512 the block cannot be assigned to the SM until it secures enough resources for all of its threads to execute okay so if I have 124 blocks。

 that means if I find an SM with 124 thread slots free。

 I can assign my threads to that SM if I don't I have to wait okay now why do you think that is why do you think that I cannot I have to assign all。

Threads in the block to the As at the same time。They might be collaborating to solve that problem。

exactly and if I don't assign them all the same time， and they try to collaborate， what happens。

Did you get the there。啊。They will be late。It will be late。啊What do you mean by。So for example。

 if you have three processing steps and you need to communicate at the second step。

If one of them is at step one， when the others at。Step two， then you're going to break the program。

Well， if they're synchronizing with each other， then they shouldn't the others shouldn't go to step two before the others are done with step one。

 so somebody's saying deadlock， you're right， why could there be a deadlock if I only some of the threads and dons and the rest？

Sas the threads that are already in the course that are working on the course are waiting for the ones that are not and the ones that are not are waiting the ones that are to run。

Right， exactly。认真。If I'm over here ands say have my threads are 1000 I have a block that has 1024 threadss and then all of a sudden there's 512 thread slots that free up on this S if I take 512 threads and have them run on the S。

And then the remaining of5 and 12 are sitting here and waiting。

What could happen is that I could end up in a situation where these if these threats try to synchronize。

Well try to wait for each other at a barrier， for example。

 what could happen is the 512 threads that are executing here would be waiting for these 512 threads to reach the barrier。

But then the 512 threads that haven't been scheduled yet are waiting for the512 threads that have been scheduled to finish executing so that they can take their place。

Okay， so that is why I cannot have some threads assigned to the SM and other threads not assigned to the SM and waiting for resources to free up so that they can be assigned to them。

Okay。Yes， is the assignment also parallel or does it happen？And know does it do it okay。

 this this one will take this one， this one will take this one， this one will take this one Okay。

 so by assignment， what I mean is that these threads have reserved resources to execute on the SM that doesn't mean they're actually exit。

You know what I mean is is there one unit that kind of for the schedule？Yeah。

 so there's there's a hardware unit that takes care of assigning threadblock to ass and scheduling with threads on the assembly Okay。

 and obviously there's going to be parallelism in there so that you can have scable。Okay。Okay。

 so is that other if we don't assign all threads to DS SM at the same time then some threads may reach the barrier and others cannot execute so the system would that。

Yes， somebody had a question。Yes， couldn the same， like， even if we load all of them on the。

On the SM M， if some of them are already in the course。

 is there a way we can get them out and get others in， like do multi threading inside the G。 yes。

 yes， there is。 And we will talk about that。Okay。Okay。

 but the idea is that in order for them to be able to run the course。

 they need to reserve execution resources like registers and threat slots and other things and for them to be able to and we need to make sure that all of them have the execution resources they need before we let any of them start executing on the course。

 that once they start executing on the course， we can ensure that they can all eventually execute and reach a barrier if they try to think but yes。

 they can do things like multithreading and we will。Okay， thank。 Yeah， you're welcome。

 Another point I'd like to make is about transparency capability。

 So we saw that threads in the same block can synchronize with each other。 In contrast。

 threads in different blocks do not synchronize with each other。Okay， so threads in the same block。

 they can collaborate threads in different blocks do not collaborate with each other。

 and the nice thing about the KUDa programming model not allowing threads in different blocks to collaborate with each other is that this makes these blocks independent from each other。

And what I mean and the blocks being independent from each other， not talking to each other。

 not collaborating with each other means that these blocks can execute in any order。Okay。

 so it doesn't matter what we to execute these blocks in， and more importantly。

 these blocks can execute in parallel。😡，Or they can execute sequentially with respect to each other。

Okay， so if I have， you know， 128 block threat blocks in my grid， I can execute them from0 to27。

 or I can execute them from3 1227 to block 227 to block  zero。

Or I can execute them in any random order that I want。

 and I can execute them all in parallel or I can execute some of them and then execute the others。

 the order in which I execute them doesn't matter。And the reason this is important is because this enables something called transparent scalability。

And what we mean by transparent scalability is that the same code。

Can run on different devices that have different amounts of hardware parallelism。

So if I have a device that has a small number of SMs。

 I can execute these blocks sequentially on that device。

And if I later on get a device that has more SMs， then I can take the same code and execute it on that device that has more SMs and these blocks that were executing sequentially on the first device will execute in parallel on the second device。

Okay， so say the blocks execute sequentially， I mean that I don't mean that the threads within the block execute sequentially。

 I mean that the different blocks execute one after the other on the same。Question。

So you have to be careful when you select which trends go to which block depending。じゃああ。If you're。

Right， exactly。 You have to be careful。 So programmers should not write code that tries to synchronize across blocks。

 Now， Kuda doesn't give you that。 So Kuda gives you sync threads。

 which lets you synchronize across threads in the same block。

 But Kuda doesn't explicitly give you some operation that lets you synchronize across threads in different blocks。

 Now， people could try to do that by having some kind of， you know， by trying to。

 you have these threads access， maybe the same memory and wait for each other using， you know。

 using spin locking and loops and things like that。 But programmers should not do that。 Okay。

 Why shouldn't programmers write code where they try to synchronize between threads across blocks。

Because it will not scale well with different machines。It will not scale well。

What could happen given what you know about the way that thread blocks are scheduled。

 given what we know about that blocks can be executed parallel or sequentially？

What could happen if a programmer tries to communicate across threads in different blocks？

They don't know the order of what。To avoid that abuse。To avoid what data races data races。 No。

 it's not about data races worse than that。We're not even sure the blocks are in the have the access to the same。

Sm or memory range。Not even that。 know， they could have access to in global memory。

Why are we not sure about， So it's written up here。If I try to communicate across different blocks。

Maybe it's not even going。Different order actually。

 so at the end of the block I'm trying to synchronize where is' not even running what would happen in that case。

We wait for it。 We would have sequential execution， instead of parallelism， and slower。I mean。

 that hurts performance， but there's something that's even worse。Deadlock， right。

 So somebody answered the chat deadlock again。 So if I。

 if I try to communicate across different thread blockss。And， and the。

 and what happens is that the hardware， you know， we don't have， we have more blocks than we have Ss。

 So the hardware is going to schedule some of these blocks and and is going to put other blocks and have them wait until the blocks that are scheduled。

 they're done。 If I come and try and synchronize across all the blocks。

 While some blocks are running， but some blocks are waiting。So what happens？

The blocks that are running are waiting for the blocks that haven't started running yet to synchronize with them。

 but the blocks that haven't started running yet are waiting for the blocks that are running in order for them to start to finish in order for them to start running。

 Is that clear。So nothing will run， let me go back to my art figure， not this one。嗯。So here。

 if I try to communicate between the blocks that are running on these ass。That are， that are waiting。

Fer， I say I want all these blocks to wait for each other at some point in the code。😡。

What's going to happen？While the blocks that are running are going to wait for the box that are down here waiting。

Reach the synchronization point， but that the blocks that are down here waiting are going to be waiting for these blocks that are starting to finish so that they can come and start running on the essence。

Okay， so that is why is that point clear to everyone？But can't you sold that at a hardware level。

How would you hardware level， you could， but it's very expensive， but go ahead。

 how would you solve at a hardware level？I'm not sure you would see that something needs something else to start running。

 so you put it I guess， into cash and you bring something else。Okay so what you're saying is。

 maybe we can take this thread block and remove it。P a threadlock in its place， and when it is done。

 we can bring this one back。So kind of like context switching on a CPU， right？也是。

So so that's what we do on the right in the CPU we don't have this problem because threads just context switch so when a thread is waiting for another thread we remove that thread from the from the CPU and we bring in the other thread to execute So here why do you think that we don't we why don't we think the hardware the GPU hardware does that right so why do you think the GP hardware does not want to have to remove this block and bring in another block to execute。

It's probably most expensive to take and reen it。Why， why is it expensive。

 Why do you think context switch to threat blocks is expensive， Oh because you need a lot of cash。

 That's why you know。right， you need a lot of space。Why do you need a lot of space？

Because you have 5000。You have a lot of threads， right？

So a thread running on a CPU might be using 32 register。So when you contact switchhep。

 you have to save 32 registers somewhere in memory。A thread block running on the CPU view。

 I'd have 1024 thread and each of these 1024 threads might be using。So how much do you have to save。

 you have to give around 32 kilobytes of memory to context。That takes space， but worse that space。

 that takes time。😡，It takes time for you to have to take all this context and store it to memory so that you can bring in a new book。

Okay， so it's really not scalable for you to support context switching between them。

So that is why the hardware， when a threat log fits on ann， it executes until the threat log is done。

And when the thread block is done， the new thread block is come in and paper。

And because of this restriction， we do not have cameras。

Should not write code to tries to synchronize across blocks because if they do。

 then deadlock will occur if the blocks that they're trying to synchronize between are not scheduled final。

Okay， clear， any questions about this？Okay。So now that we've seen how reschedule blocks on different SM。

So then on one SM， and see how threads are scheduled on that So threads are assigned to an SM run on that SM concurrent。

And what。What I mean by concurrently is that they I don't mean that they are all running in parallel at the same time。

 but they one concurrently that there's a scheduler that manages their execution and schedule thumb threads sometimestime than other threads thats it。

诶。😊，Now when the blocks assigned are scheduled on the， they are further divideded into units called4。

Wps are the unit of scheduling on the so these thread blockss。

 when I come out and I assign these threads to execute on these scores I schedule them in units of warps。

 the thread block is further broken down into warp。And these warbs are the unit of link on I。嗯。

This shows how each thread block is broken down into warps and these warps are the unit of scheduling on the SM。

So let's talk a little bit about what these wars are。 like I said。

 wars are the unit of scheduling in an asN and the size of warps is device specific。 but to date。

 it has always been 32 threads。 Okay， so if I take a if I create a thread block that is 1024 threads。

 these thousand24 threads are going to be grouped into 32 warps that are 32 threads each。

 if I if my thread block has 64 threads and these 64 threads are going to be grouped into two warps that have 32 threads each。

 Now， what's so special about these wars。 Well， what's special about these wars is that threads in the same warp are schedule together following the Cindy models。

 So who here knows what Cdy is。😊，S with instruction multiple data。Right， single instruction。

 multiple data， what does that mean？You have different data。

 but you run the same instruction on them。Right， exactly。 So single instruction。

 multiple data means when when threads are bound to each other by the Cindy model。

 the single instruction， multiple data model， what that means is that we one instruction for all these threads and all these threads will execute the same instruction。

 but implicitly somehow these threads will all be executed the instruction on different data。

 So one instruction is fetched and executed by all the threads in the warp。

 but each of them is going to be processing different data Okay。

 now what's the advantage of doing this。 So what's the advantage of saying that all these 32 threads will execute the same instruction on different data。

 What's the advantage of Cindy。Only one fetch instruction need to be sent。Right。

 only one fetch instruction needs needs only one instruction needs to be fetched。

 so what's the advantage of that。Our instruction cache is much smaller。

Our instruction cache is much smaller， Well， I mean。

 even if they were even if I was executing a different instruction for each thread。

 most likely they'll be going through code right so they will have a good amount of locality but there's something more important than saving on the memory footprint of fetching the instruction。

You save time you save time and complexity of getting the data where it needs to go。

We need an interconnect that's very elaborate to wire each instruction to its core or ALU。Okay。

 what I think you're saying interconnect， but I think you mean something else。

 you mean the hardware logic that you need to fetch a different instruction for each thread， right？

I met interconnect。 but yeah， so is it because it's wrong。

 So the war will finish once and all all the third and the work will finish at the same time。I mean。

 that's the result of thread， the war having Cdy， but the benefit of it is that and somebody you wrote in the chat。

 you're absolutely right， we decode it once right so remember when we there's the there's fetching and instruction。

 it's not just about the memory footprint to fetching， but when we fetch an instruction。

 we have to decode it。Right and decoding that instruction requires some kind of controller。

That is looking at the fields of the instruction， figuring out what this instruction is and telling the different units what to do with this instruction。

RightSo if I have a separate instruction decode for every single one of these 1024 threads。

 I'm going to need a lot of control logic。But the advantage of executing the same instruction across across many different threads is that I only need one unit for fetching and executing these instructions and I amortize the cost of that unit across multiple multiple threads。

 so this is the advantage of Cindy， this is why people use Cindy so the advantage of Cindy is that we share the same instruction fetch slash dispatch unit across multiple execution units or which are cores in this case and what this does is that it amortizes the cost of control。

 it amortizes the cost of the control units across more execution units。Okay。

 so someone is asking what if there is a branch and that is an excellent question。

 And we'll talk about that。 Okay， and that is that is the disadvantage of Cd。

 But before I talk about the disadvantage of C D， let me first demonstrate this advantage of C。

 So so far， I've been this cartoon Ss with these cartoon cartoon course。

 And I wanted to show you you know， a more a more complex picture of what an F7 looks like。

 So this is this is from the white paper on the Tesla V 100 GPU， which was released in 2017。

 Of course， there are newer GPUs now， But in using the V 100。

 because that's the one you're working on in the。😊，And estimates so this is an example。

 this is the S， this is the architecture of one S and the test in the V 100 GPU。

 we said that the V 100 has 80 S Okay so the of 100 has 80 of these Ss。

 the SMM itself has 64 FP 32 cores so it has 64 cores。

 when I'm talking about these cores I'm referring to the floating point cores because a lot of times with what we care about is the floating point operation。

So it has 64 floating FP32 cores， it also has 64 integer cores， 32 bit integer cores。

But these 64 cores are actually organized into four processing blocks Okay so here you'll see that you have these FB 32 cores。

 you also have these integer cores， you also have these FB 64 cores。

 we have things called tensor cores which which you know we'll talk about much later in the course but these 64 cores are organized into four processing blocks where each processing blocks has 16 cores。

Each of these processing block in the SN has 16 cores， and each of these 16 cores。

In addition to the 16 integer cores and the tensor core and all of these share one instruction dispatch。

And one register file。Okay， and what that means is that we this patch unit is going to fetch one instruction and execute it on all 16 of these scores now obviously a thread a warp is more than that a warp is 32 threads so these 32 threads are going to be taking turns on these 16。

Okay， so a warp is going to be executed by one of these processing blocks。

 and the processing block has one dispatch unit that's shared across all 16 cores in the processing。

Okay so this is in more detail what the architecture of an SM looks like looks like and by the way。

 this varies across architectures so for example， the pastcal architecture had also had 64 cores per SM but those 64 cores were divided into two processing blocks and each processing block had 32 cores。

 so different architectures have different configurations。

 this is the configuration of the Volta architecture。

So somebody is asking what is the difference between float and integer cores while float cores are execute the floating point operations and integer cores execute the integer operations Okay so if you remember from 255。

 we said how we have in the CPU there's the integer pipeline and then there's also this floating point coproor where you can think of these integer cores as containing the ALUs that do integer operations and the floating point cores containing the ALUs that do the floating point operation。

Doctor， have a question。 If we said that one one warp is executed for each by each processing block。

And can you get like multiple warps running on the same block and on the same core。Yes， yes。

 And you actually should do that。 And I'll talk about that later。 But yes。

 So I said a warp is executed by one processing block。

 I don't mean only one warp is executed by one processing block。

 So where each each processing block is going to execute multiple warbs。Okay， but you know。

 but the warp is what I mean by this is that one warp is not going to execute on multiple different processing blocks。

The warp is going to be fetched， we're going to fetch one instruction for that warb and execute it for all threads in that work。

Okay， and and that's why that's why I have the L0 instruction cache for each score。 right， Yes。

 exactly。 So there's there's as you know， as you observe， there's an L zero instruction cache。

 So these processing blockss has its own instruction cache。 they all share an L1 instruction cache。

And they also all share a data cache and shared memory， which we will look at later on。

 they also share texture memory， which we'll also look at later on。Okay。

 here you have this war scheduler and this war schedule。

It's actually responsible for selecting because as we were saying since we opened the topic。

 because we can have multiple wars running on the same processing block。

 the workp scheduler will be responsible for selecting which work to execute at any point。

Can they execute out of order and are they dispatch an order or like what's the specific specific No。

 these are1 order not out of order So remember out of order we said you know the first lecture that out of order execution this is to optimize or for latency but these but these GPUs they're optimized for throughput at the expense latency and what that means is we don't want to invest hardware for into out of order execution we prefer to take。

And invested into adding more course， so these are all in order of course。Okay。

 but what if we get like different ver that for example， if it floating。32， floating。32。

 then we get integer the if if all the floating。32 executioners are busy。

We will be doing nothing when we can do the integer operations， but I guess the see William。

 you're talking about taking interlieving instructions from different works。

Yeah I will talk about that。Yeah， but within a warp。

 the instructions are going to execute in in an in order manner， these are in order pipelines。

 not out of order pipeline。Professor， what's the difference between L1 and L 0。

 Is it the same thing just closer to L0 is private to each of this processing works L1 is shared across。

Okay， but same technology。Yeah， yeah this is all EM。O。哎。Other questions？Okay。

 so we saw the advantage of MD that we can amortize the cost of the dispat unit across many cores so that we can invest more hardware to perform actual operations and less hardware and control logic。

So that's the advantage of S。 What's the disadvantage of S。Somebody had already mentioned it。Advans。

Right， exactly branches。 So the disadvantage of Findi is。Different head may take different paths。

 And this results in something called controlled divergence。

So we said that we're going to fetch one instruction and execute the same instruction on all the threads of the same warp。

 but what happens if different threads in the warp want to take different execution paths。

 what happens if I reach an if statement and some threads in the warp want to go to the then part and some threads of the warp want to go to the L？

So in this case， we have something called control divergence when different thread want to take different control paths and what the warp does in this situation is it has to do a pass over each unique execution path。

And when it does these passes， all the instructions have to stay together and what that means is that in each path pass the threads taken the path that will execute and the others are disabled。

So some threat， so when I take the then， for example， if I reach an if L statement。

And some threads take the true branch and some threads take the false branch。

 what happens is all the threads are going to go together to the true branch。

 but only some of them will execute， and then they will all go together to the false branch and only the others will execute。

And what that means is that at some point during this divergence。

 only some threads will be active while others will be inactive and percentage of threads or core that are going to be active or enabled during C execution。

 this is something called CD efficiency。 CD efficiency is the percentage of my cores that I am actually utilize because because there are some core that I may not utilize due to control divergence。

 Let me do an example to make this。So let's say I have threads that take different branches of a conditional。

 so if I have code like this。When I have if thread index dot x is less than 24， then execute code A。

 else execute code B， and then after if statement I execute code。Okay。

 so if I am I am the first warp and the block。So that refers to threads 0 to 31。

What's going to happen in this case， thread 0 to 23 when I execute a。

Whereas threads 24 to 31 want to execute the。Okay， however， these threads are bound to each other。

 They all execute the same instructions。 So I can't have some of them go execute one instruction and the others go execute another instruction。

So what happens in this case is that at the beginning， all the threads execute the same condition。

But then later on， what I'm going to do is I'm first going to go to a， some threads will execute A。

 the ones that were for whom the condition was true。

 and the ones for whom the condition was false will be inactive。

And then I'm going to do a pass through B， and then in this case。

 the other threads are going to execute B while the remaining threads are going to be inactive。

And remember that you know when I execute this instruction for all threats。

 that means that these cores。These cores are reserved for those threads。

 so these threads that are inactive are actually reserving these cores， but they're not doing any。😡。

Okay so I can't use the course for anything else because all the cores execute the same instruction。

So all these course， their either execute table structure or they'll do nothing。

So then this is what happens in this case and then finally。

 these threads will then reconverge and all of them will execute together。😊，So obviously。

 there's an inefficiency here because I have these cores that are wasted because of these inactive threats。

I can't do anything else with these scores because these scores are down to the cores that are executing these other threads by the same instruction dispatch unit Is this clear to everyone。

I just， yes。Are there techniques to improve like compiling techniques to improve the warp dispatching or scheduling in order to minimize those？

In active times。So a lot of time a lot of so these are not inactive times I mean these are executing at the same time as this。

 so there is not much the compiler can do a lot of times this divergence is dependent on the code that the programmer provides you。

So if you want to minimize this control divergence。

 what you want to do is you want to somehow rearrange your threads so that some threads so that all the threads that are in the same more take the same path。

 but usually this is something that the programmer is able to do it is difficult for the compiler to detect this and transform your code to minimize this divergence That said。

 there is research on you know some people have proposed maybe compiler optimizations where they try to minimize the divergence that is there in the code。

 but I don't think I'm not sure but I don't think that the NviA compiler actually adopts any optimizations where they rearrange the threads in order to minimize divergence。

So basically， the worst thing you can do is LCF， LCF， LCF， LCF。Yes， because if I have LSif， Lif， Lif。

 I' a lot of different diversion path。😊，Okay， another example is maybe this is possibly even worse than the LCL。

Is is a loop。So threads that execute a different number of loop iterations。 So for example。

 I can have code like this n equals a of thread dot X。

 and then I execute a loop for I equals 0 is and n plus plus size。And then I execute some code A。

 So in this case， the value of n。Depends on the thread index。

 And what that means is that different threads may have different values of and。

And what the is is that different threads they execute a different number of loot iterations。

But because these threads are bound to each other by sdy。

I cannot have the threads that finish the loop， keep going and the threads that haven't finished the loop say and execute the loop。

They all have to wait for each other to finish them。So in this case。

 if I have zero transs0 to 31 in the same warp and if each of these threads has a different value of n。

 some of them might be eight， some of them six， some of them seven。

 some of them four so here the smallest value of four so the first four iterations all of them are going to execute are going to be active。

 but then once I get to iteration 5， this thread over here is going to drop out。

And then when I get to iteration 6， these other threads are going to drop out。 However。

 they can't go and do something else， right， they they're bound by these other threads because of ST。

And then later on， you know， some more threads drop out and then finally， some more threads drop out。

 And then when the， if the largest iteration is 8， then once I'm done with all it iterations。

 then all threads can continue together。And you know this can get， you know。

 this can really hurt you if you're not careful， you know。

 if you have some kind of code where if you have some kind of application where one of these threads executes thousands of iterations and all the other threads are executing like five or six iterations。

 then that one thread that's executing thousands of iterations is going to hold all the other threads hostage。

 all these other threads are going to sit there and they're going be waiting for that one thread to finish executing its iteration。

ProIn that case， shouldn there be a way for maybe the compiler or the dispatcher to click blocks。

 like allow tinkering with the blocks and have all those with block index 1 to be together and so on。

 Like theres going be a lot of differences between the actual here but here A the the loop the loop bound is data dependent。

 The compiler has no idea what this a is going what this value n is going to。Okay， I misread it。

 Yeah。 Thank you。 Now， now， but there the programmer can do things about this。

 and we will look later on in the course about all kinds of optimizations what we can do to minimize control divergence。

 So now we're not going talk about the optimizations。 We're just talking about the problems。

 but we will talk about optimizations later。 one one optimization that the programmer can do is if somehow it is possible to sort a。

If our computation allows us to somehow sort a， then what we could do is we can sort a such that threads。

 you know some warbs will have large values of a of n， and some warbs。

 the threads and some warbs will all have small values of n。

So this helps a little bit reduce the control divergence and this is something that is commonly done in applications that suffer with this kind of code。

 and we will look at an example of this kind of optimization much later in the course。Professor， yes。

I understood the problem， but aren't they going to think later on anyway。

love need to they need to reconverge later。 So basically， at the end of this loop。

 they all reconverge and continue executing together。But I mean， later on。Okay。

 what about later they'd have to wait for each other to finish， right？Okay。

 so there's a difference between threads in the same block。

 executing sink threats to wait for each other and threads in the same warp being forced to stay together。

So here threads in the same war are forced to stay together。

 and the reason they're forced to stay together is because they don't have the independence of executing different instruction。

Okay， they must all execute the same instruction。So if one thread is done with with the loop。

 but the others are still executing， this thread cannot go and execute different code。

Because all these threads are using are they have to execute the same instruction at any point in time。

So a thread can either execute the instruction that all the other threads are executing。

Or it can be inact。Is that clear？Yes， yes。 it is。 but I was thinking that。

All these works would be in the same block later on。 So， so the。

Can can go and execute different code。 So basically over here。

 if I'm going to have multiple works executing this code， if one wordb finishes this code。

 that word can continue。 It doesn't have to wait for the other ver。And later on。

 if I have a sink threads， then that's where all the warps in the tongue will wait for each other。

So yes， multiple wars， one warp can keep going whereas the other warp stays here。

But for threads in the same warp， they all have to stay together。Does that answer your question， Yes。

 yes， so the thinking would be with all the works later on if there is a thinking exactly。感觉。对见。

Other questions about control divergence。Okay， so another topic that's related to warps and scheduling is latency hiding。

So no work needs to wait for a high latency operation。Another war that is ready。

 selected and scheduled for execution。 Okay， so， for example， if I have this S M。

Back to my cartoon S。 And if this S M has these three different warps scheduled on the S。 Okay now。

 obviously S M has multiple processing blocks， each block can has have set of warps。

 Warps are 32 threads not four threads。 So this this is this diagram means here just for simplicity。

Okay， so here， if I have。AMip works scheduled on the SM。

These cores are going to be executing threads this from one of these wars。

 so let's say this first warp gets executed and executes， you know it executes。

 it goes on for a few cycles and then later it find it encounters a long latency operation。

So this could be it loaded data from memory， it did not find that data in the cache。

 so it had to wait for the next level cache or for DrM to serve that data。So in this case。

 the warp can cannot cannot continue executing instructions。

 that warp needs to sit there and wait for the previous instruction to finish。

 This could also be something like maybe the thread executed some arithmetic operation that takes many cycles to complete。

 maybe it's executing some kind of multiplication。or some floating point operation and it needs it takes multiple cycles to finish this operation so and the next instruction depends on this previous instruction so the thread sit there and stall the warp has to sit there and stall until the previous instruction is done。

 So in this case I don't want my warp when it encounters a long latency operation like a complex arithmetic operation or a memory access I don't want it to sit there and wait inside of my pipeline until this operation finishes。

So what I'm going to do is I'm going to， oh， once this warp reaches a point where it doesn't have a next instruction to execute。

 I'm going to remove it from the course and I'm going to bring in some other warp that's ready to execute and I'm going to execute that war so in this case I take out this warp and I bring in this warp。

And I'll keep executing this warp until maybe this warp encounters a long latency operation。

 and when that happens， I'm going to take out this warp。

 I'm going to go and find if another warp is ready。

 maybe this warp is ready instead of bringing in this other warp。

And then maybe this warp finds a long latency operation， so I'm going to remove this warp。

 and by this time it's possible that this first warp that was executing has finished its long latency operation。

 so maybe the memory has arrived。Right or maybe the long arithmetic operation has finished executing so I can bring back this warp and I execute this warp。

 and then I found a long latency operation， I remove this warp。

 this third war is maybe this middle warp is not ready yet。

 but this one is ready so I can bring this one back and so on。Okay。

 so those of you who are familiar with multi threading on CPU are， you know。

 probably recognized what's going on here。 This is exactly multi threading。Okay。

 but it's it's happening at the war level。 Okay， so what we're doing here is we're multi threading these wharves so so that。

We don't have any stalls in our pipeline。 The minute award needs to stall rather than letting it stall in the pipeline。

 we remove it and we bring in another work that is ready。 And by doing this。

 we make sure that our pipeline is always doing something。 It's always busy with work。给。Professor。

 doctor。The question， generally， if you want to have an high outputput。Processor。

 don't you want to optimize all operations to be one clock cycle exactly？Absolutely not。

 that is if you want to have a low latency。So if you want your processor to have low latency。

 you optimize how long operations take， but if you want your processor type through high throughput。

 then what you do is you have a lot of cores even though these cores have longer latency and you tolerate that latency or you hide that latency by having many。

 many threads executing together。Okay， thank you。Doctor， but doesn't this also involve。

What did you call not thus migration。It's similar to test migration when you。The switch。

 Does it also involve。 So we're not we're multi threadreading here。 We're not context switching。

 So when I refer was referring to context switching。

 what I meant is removing blocks or threads from the S M。

 saving their context to memory and then bringing in other blocks。 We're not doing this。

 all these threads that are executing all these threads that are assigned to the S M。

 they all have registers reserved for them。 and they all have memory reserved for them。 Okay。

 but they don't all have but， but they don't all executed on the course at the same time。Okay。

 in other words， and brings me to my next point in order for us over here， in order for this to work。

 in order for this multithreading to work， for me to make sure that I use every single on my apply plan and don't waste any of them。

 it's in my best interest to have many， many warps scheduled on my SM then I have courses， okay。

 because if I have many more warps。Assigned to the SM。

 then I have cores in the SM that this ensures that I will always find a warp that is ready to execute。

Okay， if I only have two wars， but I execute one warp， it finds a long latency operation。

 I execute another war， it finds a long latency operation。

 and then now both of them are waiting to finish their long latency operation and I'm going to have skulls。

So to maximize the probability that I will find a warp that is ready to execute when a previous warp encounters a long latency operation。

 I want to have many more warps than I have a course so many many I want to have many more warps than the number of warps that I can execute at the same time。

 or in other words， I want to have many more threads assigned to the SMM than the threads that I can execute at the same time。

Okay， so we need many warps are needed so that there is a sufficient work available to hide long waitency operation。

 In other words， there's a high chance of findingening a warp that is ready to execute。

And because of this， an SMM typically supports many more threads than the number of cores that it has Okay。

 so an SMM has enough registers and enough memory and enough thread slots to support many more threads than the number of actual cores in the SM and let's take a look at some numbers here。

So here if we take a look at。The resources of one estimate。

 depending on the different micro architectureits。You'll notice that。

Here there are different kinds of resource you the number of SMs。

 number of course per S number of threats per S the blocks perM maximum number of threats per S we'll talk about some of these later for now I want to focus on these two things so here you'll notice that for all the different architectures they usually support many more threads than they actually have cores on the SM。

And if you look at the  Voltta U100 architecture， it can support 2048 threads being assembled to the SM at the same time。

 even though it has only 64 cores。What that means is that we have 32 times more threads assigned to the SM than we have cores on the SM。

😡，And you can imagine that you know what this does is that these when one of these warps reaches 208 threads is 64 warps。

Okay， so when one of these warps encounters a long latency operation， I have many。

 many other warps that I can choose from to execute。A this Korea。Yes， but isn't  32 times like 2048。

 2008 a lot， like wont some thread star， for example。No， no。

 they won't startve because because I mean there's a scheduler that's responsible for scheduling these threads and obviously the scheduler is going to go and try and find is going to go and try and find which warp is ready to execute and it will execute it。

 but if there are multiple warps ready to execute， then obviously the the scheduler is going to have some other kind of way to decide between the different wars that are ready that prevents warps from getting started。

How many threads per core can we execute？So here the ratio of threats to cores is 32。

 a single core can only execute one thread at any point in time。

Right we learned about the multi thread aspect。Because for example， on on X 86， you can do。

2 threads on the same core。 exactlyactly， That's excellent observation。 I'm glad you mentioned that。

 I was going to mention that。 So when we compare this to GP CPUs， for example， in a CPU。

 when we do multi threadreading we usually have two threads running on the core here。

 when we're doing multi threading， you saw that the ratio of threads to cores is。32， as opposed to。

 you know， when we have an eighth core CPU， we usually have 16 threads running on it right so the ratio of cores of threats to cores on a CPU is 2 here it's 32。

 So why do you think there's that big of a difference in the ratio。Because of longgraency operations。

Right， a CPU is latent oriented processor， so CPU the CPU is designed such that we don't have a lot of pipeline stalls that we need to fill。

Okay， we're doing all kinds of things like out of order execution， you know， multiple， you know。

 you know， we we we fetch， you know， we have a， we have， you know， wide issue。 We have large caches。

 We have all these kinds of things to make sure that our operations have as low latency as possible。

 So we don't have that many cycles to fill when we're running on a CPU。

 And that is why we don't need to have many more threads than we have， of course。Okay。

 on the other side， On the other hand， the。On the GPU， because we have these long latency operations。

 that is why we need to have many， many more threads than we haveb of course。Cl。

Someone's saying that the GPU executes faster， the GPU executes faster because it has higher throughput。

 but it doesn't have lower latency。😡，So for example， if I wanted to add one element to in an array。

 the CPU is going to be able to add that one element in an array faster than the GPU。

But when I want to add millions of elements， a arrays of millions of elements。

 that is when the GPU becomes faster。Okay， so the individual operations take longer latency on the CPU。

 but the whole computation can finish faster because the GPU has higher throughput because it has so many more core。

Why did they go down with the K40 the V100 is newer than the K40 no。Yes。

 so here you notice that there's a trend where they reduced the number of cores per SN。

And what this does is that it allows you to have more S。Okay。

 and it allows you to have more multi threading on each of stem so that it can hide frequency。Okay。

 and there's probably all kinds of good reasons why Nvis think that it does that their hardware experts know that we may or may not may not know。

 but you know one intuition here is that over here you're increasing your ratio of threat forces in order for you to be able to highlight。

Okay， so with that said， let's this brings me to another topic， which is Occants。

So we said that we want to have many more threads than we have scoress in an SM。 So here。

2048 is the maximum number of threads that I can assign to the SM。

But that doesn't mean that any program I write will have a maximum of 2048 threat on the As。

 And this speak to the topic of O。So the occupancy of an SM refers to the ratio of the warps or threads that are active on the SM。

Compared to the maximum that is allowed。Okay， and here by active， I mean assigned to the S。

 not the ones that are actually。So the SMM supports 2048 threads。

But maybe I because of how I wrote my code， my， my hardware will not be able to schedule more than 1024 thread to assign more than 1024 threads on that of。

 So in this case， my occupants do a be 50 person。Now， in general， I like to maximize my occupancy。

 right， I'd like to， I'd like to have the maximum the number of threads I'd like to have scheduled my S is the maximum allowed because the more threads I have on the S。

 the better I am at hiding late I have more threads， more instruction， more warbs to choose from。

This is the common case， however， it is possible that we might have cases where having high occup of my third performance。

 so in some cases lower occupancy is desirable， but in the common case I would like to maximize my o。

Now， how can I maximize my occupancy？ Well， to maximize， I need to think about some of these other。

So here we've seen cores per SM and we've seen max threats per SM， but we also have these other loop。

 which are the maximum number of blocks per S。An maximum number of threats for。

There's also registers press them， also shared to shared them for them。So how I choose my block size。

Okay， impact my occupants。So here the SM can support the， for example， view 100。

 the SM can support 2048 threads。But also， it can support only 32 blocks。

We're up to 30 locations I should say only because that's quite a big number。

 but I can support up to 32 blocks， I can't have more than 32 blocks on my。

Now what does that mean take？V 100， if I can， if let's my max for for blocks 1024。

My maximum threats per S is 2048， and my maximum blocks for S is 32。If I select a block size of 256。

 so if I configure my kernel to have 256 threads per block。

 then in this case my occupancy is maximized because if I'm 256 threads per block。

 then to fully utilize the 2048 spreads in the SM， I need8 block， who has 48 divided between 6 is8。

ok。😊，So with eight blocks it's less than 32 blocks。Okay， and with that and therefore。

 I can fully utilize mass I'm not limited by the number of。However。

 if I set my number of threads per block。To 32， for example。I'm allowed to do that。

 But let's see what happens If I say that I want 32 threads for blog。

Then if I have 2048 threads in the SM。And I have 32 threads per block to fully utilize the 2048 threads。

 I need 64 blocks。2048， divided by 32，6。However， my SM can only support 32 blocks。

So if I set my number of threads to 32。😡，I cannot have 64 blocks I can only have 32 blocks so I'm only going to have 32 blocks times 32 threads that's 1024 threads I will not fully utilize the 2048 threads of the SMM so in this case my occupancy will be limited I will not have a full occupancy on my SMM。

And because I will not for occupancy， my ability to hide latency is going to be even it's going to be worse。

ok。😊，If I choose something like 768 threads per SM， in this case。

 I have a problem which is that 2048 is not deisible by 768。

So 2048 is going to be divided by 768 is going to be two blocks。

 and then there's going to be a remainder of 512 threads that cannot be used because I cannot use these 512 to execute 768 block。

 768 threads， why， because I need to make sure that I have enough resources for all the 768 threads before I scheduled we talked about this at the weekend number。

So in this case， I'm going to have 500 fs on you so here when we pick the number of threads per block。

 we need to make sure that this number of threads per block is able to fully utilize V SM by making sure that my blocks per SM is not exceeded and also by making sure that my threads per SM is divisible by my block size。

So yes， this is you know， some of you observed before you had asked me how do we choose how many threats block we want。

 Well， this is one of the considerations that goes into choosing that number。

Okay now we saw that different GPUs have different numbers for these。

 So if you're running on a particular GPU， how do you know how many threads per assembly。

 how many blocks per asem GPU supports well coUDa actually gives you an interface for doing that So there there's an interface called coUDa device coulda get property there's API I call called Ka to get device properties that allows you to query the device and figure out what are the different properties of the device like how many threads for asmb support how many blocks for as support what is the maximum number of threats per block。

Okay， and this here is example code on how to do this， I' going to get into it。

 but you're welcome to review it on your own。For example， here。

 we can query the max threats per b and we can query the max threats per multi processorcessor multi processorcesor needs。

诶。😊，And with that said。You can read more about what we covered today in chapter of textbook and that's all for today。

 anybody have any final questions？Can you go back to the latest C hiding slide。Yes。

I didn't understand the。How do you switch？So shall on the warps that are running if you have a long latency operation。

So there are these core， right， and these scores are pipelined。Okay。

 and you know how when you studied pipelining in a basic computer architecture class。

 you saw how when an instruction reached the point where the next instruction cannot execute before this instruction needs to wait to do something。

 we added its stalls into our pipeline。Yes。So basically， instead of adding stalls into our pipeline。

 what we do here is we remove。The threads。And we bring in another thread where the instructions of that thread are independent of the other thread that's executed。

But what do we do with the threadreads that we removed， where do we store them？

I mean the registers for that thread is still there。

 the program counter is there there's a scheduler basically that says。

 okay you know you're not going be you don't have any instructions ready so you're going to set aside your instructions I'm going to remember what your program counter is and I'm going to bring in this other word okay and then when you're ready。

 I'm going to come and I'm going to bring you back and'm going to return restore your program counter so you can continue executing from where you left up。

And how is that different from context switching？So with context switching， okay。

 so here the registers for the thread that we are removing from execution。

 these registers are still reserved on the S。Okay， okay， but with context switching。

 we take these registers on the CPU and a CPU does context switch。

 so the CPU has two threads running at the same time， it has registers for both of these threads。

At the same time。But when you context switch a thread on a CPU。

 you take all its registers and you store them to memory in order to bring in another thread and restore its registers from them。

That's the difference between multi trading and context。Thank you。 Yeah， you're welcome。肯定要这个申。

Thus you mentioned at the same slide that long late inency operation might be an aromathmetic operation。

Yes。😊，But how would removing it from the course？So remember， these are pipelines， right。

 I could have my my A pipeline。Okay， okay okay， right so so the arithmetic instruction is still going to be executing a later stage of the pipeline of the pipeline AOU while the instruction from another warp can come andfuse an earlier pipeline of the AOU。

Okay， okay， I was thinking of the core being。Like really simple or basic。 Yeah， no。

 there's there's there's a lot of pipeline。 These are very deeply pipeline for。Okay， okay。

 oh concerning my previous question。About the words。

And no I if I have to think the works S for the blocks。

 no would it be beneficial to to try to optimize the control diversions is Annabel S in Im。

I'm thinking all the words in the block。嗯。😊，I'm not getting why would it be beneficial to optimize the control diversion？

And end they all are going to be think。 Well， M Damon the warbs in all the the block will be sync。

So these are two separate things the problem with control divergence is I have a percentage of my course and I execute that are not being utilized。

Okay， the thing would be in the same as， I would have a lot of more than。

More than wars from different blocks。Yeah， I could have warps for different blocks in the same S。

 yes。Okay， okay。I'm not sure if I answered your question。no。Okay， okay， good other questions。Do。

 W can repeat best the definition of occupancy and know if you can go back to slide of the examples about occupancy。

So after the example of the ratio。Of thwarorps or threads that are active on the SM to the maximum allowed。

 So if we go back to our previous slide we said over here that the maximum threats allowed for SM is 2048。

 even though the number of course for SM is 64。So ideally。

 I want to always have 2048 threads for my SM and my SM but if I if for summary。

 if I configure my block incorrectly， for example， or maybe I am forced to not be able to have 2048 threads for SMM。

Then in this case， I will have fewer threads in the SM and it will not have fluoc， so for example。

 if I set my number of threads to 32，And my maximum blocks is 32。

 then the maximum blocks is going to limit me to 1024 threads in my SMM。

So even though I can have 2040 interests with DSM， I won't have it because I'm limited by the number of logs I only't gonna have 1024 so in this case my occupancy is going to be 50% it's going to be the number of threads actually assigned to SM which is 1024 over the total threads the maximum threats that can possibly will be assigned with which is 2004。

没要。Okay。Yeah。There be by the way， there could be other reasons why I limited my occupancy。

 so for example， if I write a kernel where every thread needs the the longest amount of registers。

 then I might run out of register registers before I've reached 2048 thread。Okay。

 so if every thread needs  64 registers， for example。

Then the maximum I'll be able and I have 64K registers。

 then the maximum3s I'll be able to have is 1024 so I'm going to be limited by my registers before I reach the maximum number of three。

这是在哪个？Where I want I have high occupancy。So there's a way for you to figure out how many registers your threads are using to be able to figure out whether you will reach high occupancyup。

And if you find out that your thread， your code is using too many registers。

 maybe you can rewrite your code in order for you to use fewer registers。

 or maybe you can pass a compiler flag that tells the compiler or maybe some annotation that tells the compiler。

 hey compiler， don't use more than this menu registers for this kernel。

 if you need more registers do some kind of registers building or。Okay， thank you。Okay。😊。

Other questions。Just a small one， so for example， an F statement it' something that we use quite often。

So why don't they choose to do something like two instructions， multiple data？

So you're having some you're proposing some kind of hybrid SMD where you can have two different instructions running at the same time。

呃，一样。Okay， I'd be interesting know to maybe discuss offline what that would look like。

 but you know that starts going into you know the idea of C is that you amortize the cost of an instruction dispatch over over you 32 different threads in the warp so now if you want to have threads being able to do two instruction then you now somehow need to have two different instruction dispatch units and somehow need to say which scores are going to go for which instruction dispatch unit and to get a little bit complicated。

Okay， see but if you want to explore that idea， we can definitely talk about it offline。O。All right。

 well， if there are no more questions， then that is all for today and I will see you next time。第一部分。

Ma， thank you。

![](img/dc7eda33d312150061530193033d07dd_2.png)