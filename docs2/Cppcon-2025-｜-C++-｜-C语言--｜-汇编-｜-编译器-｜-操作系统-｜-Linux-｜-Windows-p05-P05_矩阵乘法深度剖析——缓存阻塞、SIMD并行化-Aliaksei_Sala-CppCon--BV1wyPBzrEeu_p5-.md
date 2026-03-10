# Cppcon-2025-｜-C++-｜-C语言--｜-汇编-｜-编译器-｜-操作系统-｜-Linux-｜-Windows-p05-P05_矩阵乘法深度剖析——缓存阻塞、SIMD并行化-Aliaksei_Sala-CppCon--BV1wyPBzrEeu_p5-

![](img/507572f9fc54483e25786c793f65ea20_0.png)

And my name is Alexey Sal。 I am lead software engineer。I've been programming C++ over 10 years。



![](img/507572f9fc54483e25786c793f65ea20_2.png)

And one of the thing I love about C++ is how it gives me opportunities to work on huge range of different projects。

In my case， its creation of theters， chargers for electrical vehicles。Micro server for cloud systems。

And software for AI accelerators。In most of the projects。

We do care about performance as a S++ developers。But it's like high level optimization techniques。

 For instance， do not copy your objects if you can move them。

But I was always curious about low level optimization techniques。And we all know the principle。

 do not pay for what you do not use。Ive already paid for my CPU so I kind of must use it。

So I decided to dive into HPC high performance computing topic。



![](img/507572f9fc54483e25786c793f65ea20_4.png)

And share my journey with you。So I chose matrix multiplication。For this stock。

The application of the algorithm is really huge。But during the session， I would like。

To pick just one。Large language models。We are not going in the details how it works。

But I would like to emphasize that most transformer compute。

 about 7% to90% we spent on large matrix multiplication， basically。

In self attention and fit forward network。And if we take a look closely on the self attention。

We can notice how heavily we use matrix multiplication here。收。

It seems like reasonable to optimize matrix multiplication and understand how we can achieve the peak performance for that algorithm。

Why pick performance。Let me show you the table where we can see the。

AI breakthrough people made by past 10，150 years。And we can notice how we started with Alexnet。

 which required sweet teroflops of total compute and how the demand for the compute grows over the past 10 years。

 We goes from terraflps to petflps。Nowadays， it's exlos。 And the next， it's like azetalos。

 I've never thought that I'm gonna mention that So in the presentation。And。

Since we have this huge demand on the compute。I believe it's really important to achieve the big performance。

And according to open AI data， the compute， which is required to train a new model。

 double every four months。And I'm super excited to see what the next generation of model capable。

Capable of so。That' the reason why I believe that we need to understand more how to utilize hardware resources more efficiently。

So let me introduce the agenda for my talk today。啊。I start with the C+ class implementation。

 the na implementation where we can。Observe in different materials。Then I evaluate the performance。

 my focus will be on the execution time mostly， and also I'm going to show you the percentage of the big performance but for the specific implementation。

Then we proceed to the next optimized version of the matrix multiplication。

 where I apply one of the techniques。And we compare the implementation I show you。In the。

 for example， slide with all previous implementation and see how we are progressing from the na implementation to the most performant one。

For this particular talk。I used Google benchmarkchmark to run all of my benchmarks。

All tests on a Linux machine。 I used quite old CPU。

 It's Intel 60 I 5 with a household micro architecture。

And I compiled my matrix multiplication implementation with the following compile fluxs like03 fast mass with the specified architecture。

S ground context。So I assume that you are familiar with some hardware fundamentals like Simmed instruction。

 cache memory， stuff like that。 I'm going to mention briefly， but I'm not going to dive how it works。

In my particular case， matrix is basically is vector of double aligned on CPU cacheline。

 in my specific case at 64 bytes。Elements are stored to narrow major orders。

And I'm going to perform dense matrix multiplication of square mattresses with the fixed dimension。

And the size of the mattresses I choose to exceed at last level cache。So。

I would like to achieve peak performance。 So let me give you a definition for my presentation。

 What is the peak performance。So this is how I calculated for my CPU。I takes number， of course。

 multiply by the base frequency of my CPU and multiply by floating point App per cycles My CPU can execute。

And in my specific case， I。Have four core。I tested on the frequency，2。8 GBz。And。

To be able to understand how to calculate 1 floating aration per per cycle。

We basically can handle eight elements per instruction， using S instruction。

And multiplier2 comes from the instructions throughput。

 It basically means the CPU can execute two instructions a time。

And we got our peak performance around 180 GBs for this specific CPU。So。Let's。

Begin with our implementations and start with the na one。

So knife matrix multiplication looks really simple。

We need to take every row of matrixx A and multiply by every column of matrixx B。

And the result we are going to put into the element of Mar C。It's a pretty simple triple loop。

 And this implementation I haven seen in San Giharibos。People use。Let's measure the performance。

Execution time takes 100。52 seconds。In that table。We can see not just execution time。

 but I also show the relative speed up where I compare the next implementation with the previous one。

Absolute speed up is a comparison of the current implementation， business implementation。Gigalos。

 iss how many gigaplos this current implementation executes and the percent of peak performance。

 basically is a fraction of the peak performance I calculated on the previous slides。

So the first optimization is changing loop order。So in naV matrix multiplication implementation。

 we kind of go in an alphabetical order like over I J and K inices。

 but it's not the very efficient way for in terms of that access pattern。

So just changing the loop order to the IK and J， we can dramatically increase the performance of our algorithm。

Some reasoning behind that。So， if I。Take a look at naivematic multiplication imation。

 We can see that when we iterate over I J N K indices in that。Specific order。

We access an elements from matrix a sequentially， which is good。

But we access elements from matrixtri B with a huge stride， which has really bad special e col。

And some reasoning behind that is the following。 Then when we read an element。From the matrix。

 we don't read just one。 We read several elements to populate the whole cache line。

So when we're assessing the one element， we basically， let's imagine with four of them。

 And if we don't use all of them， we basically waste our cache memory。And the second reason。Sorry。

 the second reason why iteration with the huge stripe is bad is that it's dis hardware professor。

So it become much more harder for the professor to retrieve data from memory to the cache。

When we change the loop order to a IK J， now we can see that。When we iterate over matrix B。

 we have a sequential data access， which is good。Since matrix a。Does not depend on the J index。

 We just reuse the same element when we multiply the elements between A and V。

 which is alsocing good。And when we inter over elements ofmatic C。

 we also have sequential data access pattern。And when we measure the execution time。

 we see that speed up， It's like 12。6 x time faster than the na implementation。

But it's still relatively low。Compared to the percent of the peak performance we have。

The next optimization is styling。So。Let's multiply not elements by elements， but。

Divide matrix into the blocks。 And all of this square。 Let's imagine it's not an element anymore。

 It's a block of elements。收。For simplicity， our block can contain four elements。

And talent algorithm will calculate。Not just one element from my taxi， but the whole block。

And in that particular case。We reuse not just one element from matrix A， but the whole block。

 So we basically increase data re usageage。Using this optimization technique me。

Then we iteration over the whole row of matrix B elements to calculate the whole block of matrix C。

And。To be able to implement this optimization， we just need to add。frame猫菇。

So the most inner loop will iterate within the block or tile。

 and the outermost loop will iterate over blocks。Most inner loops。

 I'm going to put into the specific function， which I'm going to refer as kernel。

And this is our kernel for naive matrixx multiplication。If we measure the performance。

 we see that we triple。The performance compared to the previous implementation， using T optimization。

The next optimization is vectorization。Few words about it。So when， for example。

 we do the scar addition。And try to sum few elements from array A with few elements from array B。

We basically need to execute for operation。With Cinji， is not the case。

 We can load all these elements into special vector registers。

And apply only one operation to get the same results。

So this is what we' are going to do with our module multiification algorithm。

But before we start vectorctorizing our implementation。

 let's check the assembly we got from the compiler。

And we can see that compiler can't already use the same instruction for us。

 So it's kind of know what we're gonna do。And one of the interesting thing I noticed。

 then when I moved the most inner loop into the separate function。The assembly changed dramatically。

And that version actually is faster。So。Let's。Change our naive implementation with the viized one and compare after vectorization with manual vectorization。

And this is how Man Victorctorized kenal looks like。This implementation， actually。

 first time I saw in the article， what every programmer should know about memory。

H highlyigh recommend。 I really like it。But it's quite old。

 So the the Uri Dper used 128 B TMD instruction。My CPU support 256 B。

 So I just little bit updated this that implementation。Using the。Not the modern instructor said。

 but little bit more。More than the biggest one。And。Explanplaination how it works。

So we take the element from matrix a。We broadcast the value。To the whole register。

And put it into the register。 Let's call it a register。

Then we take the whole line from the matrixx B。Load this。 whats be four elements into B register。

Then we load elements from matrix C。Inter the vector register。And we apply the CMG instruction。

 which is calledfuse multiply at， which basically。To the two two operation at， at the same time。

 multiplication and addition。The result goes to the she register。

And then we basically store the result back into our matrix C。So， this is how。

Victorized cannel workss。And if you compare the assembly generated by the。Knel。

 which we implemented manually vectorization optimization。

 which is the kernel which compiler vectorized for us， we can see。

One particular thing that the compiler does not use all available registers。

 My CPU has compared to the manual implementation。 So in that particular case。

 it's like Y M M registers。 And we can see that compiler barely use。3 of four of them。

And in manual implementation， we managed to use all of them。 In my particular case。

 it's 16 registers。So if we measure the performance， we see that it's slightly better than the tar 1。

2 stream。So the next optimization is cash aware implementation。And before we jump into it。

 let me briefly review the memory hi Archy。So on the top level of this experiment。

 we have the most expensive。The most performant and the smallest memory。

On the bottom of the table table， papyyram， we have hard disk。Which is the biggest one。

 the slowest one， and the cheapest one。And to be able to explain how we can utilize memory hierarchy。

And apply it for our matrix multiplication algorithm。

 I'm going use the image created by Robert Juan dejean。

 who is a professor of a computer sciences at the University of Texas。So， let's。

Take a look at the first loop around microcarnel。We can see that when we multiply all elements from a row of matrix A to the column of matrixx B。

The first look around microcanll iterate all our roles of matrix A。

So that means that we are reus the tile or block of the matrix B all with all of these roles from matrix A。

Since we are reusing the。Be tile all the time。It's most frequently accessed data。

 So they highly likely will be in the L1 cache。This gives us information how to estimate the size for the tile of the B。

 So basically， the whole tile of the B must be fit into the L1 cache。

If we take a look in the second loop around micro kernelnel。Now we use the we。

 we use the whole block of the matrix A with multiple tiles of matrix B。

 So now we are reusing the whole block of matrix A。

 So this is will be like the next frequently accessed data。So applying the same logic。

 these kind of block will go into the L2 cache。 And now in the size of the L2 cache。

 we can estimate the block size for the。Marx 8。Following that logic depends on the memory hierarchy。

 we can estimate tile sizes for different blocks， for different hierarchy of of the memory。

How will it impact our implementation。So now， instead of three loops outer most loops。

 we have more to utilize all available memory hiarch。 instead of three， we have like five now。

The most outermost loop will iterate over blocks。 Then within the blocks， we iterate over tiles。

 and then over tiles， we basically do the matrix multiplication within the kernel。

And here I use N CM C and K K C to denote the size of the cache blocks and N R and M R to denote the size of the register blocks。

How how it affect our kernel implementation。We basically。

 instead of using the fixed size of the blocks， now we use。

The sizes we calculated based on the image with the memory hiarch came。And。

Let's check the output on the assembly。Now we can see when when we start using these talent techniques。

Applying the memory hierarchy assembly also changed。

 and now we are not utilizing all available registers anymore compared to the previous implementation。

And this is。The example of it。But if we measure at the performance， we still see some improvements。

1 point，16 times faster than previous implementation。But O， we know that we can do better。

 Let's give a hint。For compilers， how many CPU registers we have and try to utilize all of them。

So how we can do that。The way how I did it， I just manually created amount of C registers。

 B register and a registers。 So in my particular case， I have 16 registers total。

 So I allocated 12 registers for C elements， three registers for B elements and one register for A elements。

This number basically， I took from the previous implementation in assembly with saw。And。

Now we see much better picture。 Now our implementation。Use all available sp registers。

So how it impacts the performance。This is the example that we are using all available registers。

 and we see that we almost double the performance。Compared to the previous implementation。

The next obvious optimization is modest right。 And so we have multiple core。

 Why we don't kill them yet。For this particular CPU。

 I've tried different approaches to parallelize loops。

 I try to parallellyze multiple loops on a different level， like top level and asset loops。

 I pin specific thread to specific cores like different techniques。Everything。

I've tried to give me exactly almost the same results。 I didn't see any performance improvement， so。

For this particular。Case I decided to go with the simple one。

 I just split the matrix C over the I index。 I grow thises and every thread handle a couple fros from this mattress。

Ntrix。And。For my four corere CPU。It's triple the performance。Compared to the previous implementation。

The next optimization is tile matrix style layout。So if we take a look into our kernel。

 we can notice that we are itating our matrix A and B with the huge stride。

And we all know that it's not really good。Can we do that。Using just。It right equals to one。 And， yes。

 we can。How we can do that。In that picture。That image basically show us the data access button for matrix a。

So， what I did。Instead of accessing elements with these data access button within the kernel。

 I move this onto the higher level。Out outside of the kernel and copy the data using this data access button into the booth bathroom。

And then this buffer goes into our kernel。 So our kernel now don't need to do the strides when iteration over different elements。

 and that access will be sequential。And implementation slightly will be different Now。

 instead of these huge strides， we have。Stris， which is。Equal to the size of the register blocks。

 these numbers are pretty low for N R 12 for M 4。And compiler， compilers are happy to。

 all this looks for us。And we can see that we basically do not have this inner inner loopbes anymore。

 We just have one loop over K index。And this particular optimization。Gives us one point。

I see I have two rows，1，1。17 plus 1。10。Speed up。 I don't know why I didn't trim this one。搜。Same D。

 we already use。CMG instructions。But in C+ 26， we have still seen the library。

So I decided to see what will happen if I use this。

And this is how the kernel with CMG library looks like。And。The most amazing part， it just works。

 I just replaced all of these scary in functions， Use the same data type and used like a regular operation。

 like addition multiplication。😊，And it's like a zero over head abstraction。

 The performance remained the same and just works。 Really love it。

The next optimization is loop unrolling。So尾。Let's take a look at our channel implementation most in our loop。

And we've just seen that compiler unroll for us。But I would like to do that manually and see if it can impact the performance anyhow。

So on the left hand side， we see the。Original implementation on the right right hand side， we see。

Let's say top of the part of the unrolling。And when we do the manual loop onroll， just。

There is a problem with that we don't have this flexibility anymore to change our。

Amount of registers we have， for example， if I change the constant and R。

 which basically gives us information how many B registers we need to use。It's not flexible anymore。

 We cannot just change the constant and mathematical regenerate amount of B registers we're gonna use。

So we kind of need to generate a code based on this constant。And there is a way how we can。

Janu such a quote。And don't do the manual on running by like writing that got manually。And I use the。

My park from C plus plus fold expression and built in comma operator to generate。Unroll loop。

So how it works。Let's imagine we have a simple function print。

 and we would like to call it four times。What we can do， we can implement a new function。

 which is call call print and times。You啊。Viaic arguments， IDs。

 useful in expression to expand this whatever amount of times we need in our particular case。

 I passed four numbers for that。It's not really convenient。

 especially if you have not just four numbers， but like3itude， for example， or even more。

 So we can use some helpers from C plus plus standard library， like make index sequence， for example。

 which generate this sequence for us。Let's use this trick to generate the most inner loop for our kernel implementation。

So this is how compute kernel of function can looks like。So， we have。啊。Index bar， which I called I。

 which basically unrolled the loop over i indices。And parameter P J。

 which unrolled the loop over J indices。So in that particular case。

 we basically generate couple of numbers of registers for B。

 and then we generate couple of calls for computer function。And computer function。Also。

Use these techniques。And。Basically， do the matrix multiplication for us。

 multiplying elements from matrix A with elements from matrix B。This is how the API looks like。

 It's a little bit worthyy。We can simplify it a little bit by providing function over logging。And。

I skip this one and to use this computeken with make index sequence functions as an in implementation details。

And the final version of the function。Will look like that。 We just pass our register。

Tile sizes into the compute kernel size， compute kernel function。

 and it will generate unrolled kernel for us。And we are going to do the same trick with storing elements from Reg C to the matrix C。

We create a function store row， which basically execute load ink store function several times。

And we create a function store kernel， which executes store row several times。

And this is how the stockken function can be called。And the final implementation of the kernel。

 which do the loop and running manually for us， looks like that。

One of the benefits that we automatically support all all other types， it's easily customizable。

 We can generate different kernels with different parameters by passing different complete arguments。

And if we compare assembly generated by previous implementation with the one we just see when we did the manual and rolling。

They almost look the same， except one instruction。Broadcasts。after enrolling。

 this is the first instruction in the loop。With Man and， this is the fourth instruction in the loop。

Does it make any difference。Yes。It's slightly improved the performance， like 1。02。

But I still like to see the improvements。It's super hard to understand how compile do the。

Basically reored the instruction in assembly。 And it's even harder to impart that。 It's。

 it just like that I。Have this example。Okay， the next optimization is prefeing。This one。

 the most difficult to argue about。So， basically。Except hardware perfeure。

 we also have a way to execute the common， which prege data from the memory to cache。

I experimented a lot。 I got lots of different controversial results， but。

At least one thing I noticed that perfect elements from matrixtrix C gives slightly better performance。

And the final result gives me slightly better performance， like 1。07。

Compared to the previous implementation。And。I'm going to compare my result with the open bus implementation。

And when I execute the openlo implementationmentation。It's better than mine。 Like， it's even 1。

08% faster than。My implementationmentation。So there is a room for improvement。

When we reach the peak performance or near peak performance。

 it' become hard to reason about the performance itself。So couple of reason for that。Like。

 there is no point in in analog C plus plus code anymore。 So at the end， most of the time。

 I just check the output of the assembly language。Analyzing instruction for slowness doesn't lead to the same conclusion as we analyze。

Functions in C plus plus。 When we see that we have a bottleneck for one specific instructions。

 when do the computation。Sometimes， like。Fixes with changing data layout can help us not。

Not nothing we can do， for example， in that particular case。

 So we have a bottleneck in there with FMA instruction。 But the way how we improve the performance。

 we just applied like tile optimization technique。Instruction level parallel is。

 it's super difficult to utilize。 So like when I did like manual loop on rolling。

 we noticed that one instruction change the place in the our inner loop。

But how to give a hint for compiler to do the best instruction reordering， It's hard to understand。

Moreover。I've noticed one interesting case， where。We can see that。In that particular case。

 the change of the register you are using in your assembly can impact the performance。

And I believe this is the hardware bug where when you use R 6 register， the CPU cannot utilize。

Register， register renaming optimization technique。

 And when the guy changed the R C X instruction to E6， it gives like。

Slightly better performance than than the R C register usage。This kind of fixes we can do in C++。

Data analysis。 It's also not super straightforward。 So usually when I use a couple of tools。

 I use Perf。 I use Viune to analyze the performance。 This is the result from the Vune。

And on on the left hand side， we see the mime implementationation。And on the right hand side。

 open blast。 So most of the numbers are better for open blastom implementation。

 So we basically can conclude that open open blast implementation must be faster。But when I use Perf。

 for example， it's not so obvious anymore。Like when we compare the last level of cash misses。

I have better utilizationization than open blast。But when we， for example。

 compare the instruction per cycles， Uization， open glass does a better job。

So it's hard to say just watching this number， what implementation will do better。

In terms of execution time。Then， when we see。When we use Peronize instruction for slowness。

 like on the left hand side， we see lots of red instructions。

 Its basically our bottlenecks where we spend the most of the time。On the right hand。

 side the picture much better。 we don't have these red lines anymore。And what I did。

 I just unrolled K loop， which I didn't touch。It seems like it should be better， but actually。

 the performance remained the same。We just hide this， like picture from our eyes。

And the most controversial example I got is this。On the left hand side， we see the implementation。

Which have better characteristics compared to the implementation on the right hand side。

 And on the right hand side， is an open was implementation。So what did I。

 what did I use for the left hand side implementation。

You never believe It just seemed instruct seemed implementation。

 which utilizeizes 180 bit instructions。It's much， much slower than open blast。 but we soon show me。

Micro architecture usage and all of these numbers kind of better than open loss implementation。

 but actual result， like execution time， much better in open glass。So。This is what I got。

So how effective is C+ plus for matrix multiplication？When I study the subject。

 I learned a lot from different libraries。 We have， Cocos b。Also。

 learn a lot from different articles。When people implement matrix multi multiplication for GPUus。

I really love that we had the zero cost abstractions with templates， constant expert。

 and I will show you how actually benefit us a little bit later。😊，More power on the horizon。So。

 I demonstrated how same。Really good and tech。 like zero cost abstraction works perfectly good。😊。

I'm playing with M Sp right now。The thing I really love about it， that。Now。

 when I do this matrix matrix repacking， changing the layout。

 I can basically check the matrix dimension on a compile time。

 I really love it because when I implement the matrix multiplication。

 sometimes you like head blowing blowing and you start forgetting some stuff。

 you w to help from compiler。 and I'm just help me with that。😊，嗯。

Stoout Executor can help with the different strategy for multitra。

 I also will mention a little bit later。 And for those who don't want to implement matrixtrix multiplication。

 we will have stoodut linear algebra。And C plus plus， like parted by a strong and active community。

On last CPP con， I learned so， so many information， releaseful information。

 which helped me to prepare this talk。But。Allkenals I observed。

 They are written in assembly language。And kind of can understand why people do that。

 They probably don't want to struggle again the compiler。

 especially when you need to reor the instruction。They don't want to depend on specific compilers or version。

 because the。Let's say the performance depends on the compiler。

 And when I compile all of my implementation with G C and all of my implementation with Salang。

 I saw like a dramatic difference for sound implementation。

But the final implementation behaves the same for Cac and GCC。

 So this no difference with highly optimized version。And。

The bug with the hardware when you need to use instead of E6， you need to use R S X register。

 you just cannot do that in C++。So you need to use assembly for these kind of fixes。

And as I mentioned， like for some implementation， the performance vary by up to 40% for not optimized。

 fully optimized matrix multiplication。But they didn't answer the question how effective is C plus Pla matrix multiplication。

I recently bought a new desktop workst。It's I M D Z 5 micro architectureit。

So I decided to check how my implementation behave on the modern CPU。This is our peak performance。

Use the same formal I provided at the very beginning。And I got 2。9terfls of the peak performance。

But I read that CPU will down clock to 3。8 gig。If we are using Aviix 512 heavy workload。Therefore。

 the maximum performance， we can use like 3。8 gig to estimate our big performance for this particular case。

 and it will be 1。95terlos。And when I execute open blast implementation versus my implementation。

 I was really surprised。 My implementation actually beat open B for doubles。And I did slide。

What I did， I tweak tile sizes because mine， like new CPU has different cache sizes。

 different amount of registers。 So I must rec all of these parameters。

And I also change the multiing strategy。 So instead of splitting only by row。

 I start splitting like by blocks， and it will give some also improvements in terms of performance。

So in my particular system， such two threads。 So I split it the matrixs into 4 by 8 grid。Y probably。

Sit， okay， I will mention it。So sort to threads， but actually， CPUU has only 16 core。And I。

 this implementation still notized the。Think that every core has two separate threads。So。

 this implementation。Can be improved by utilizing that information。So。

All my previous experiments were with doubles。But we got flow support for free。Due to the templates。

And we can see that open blast implementation have the same performance like mine。 So here。

 here almost no difference。But。In C plus plus 23， we have B float 16。And since we get。

The type support for free， I decided to check how my matrix multiplication will will work with the new type D 16。

 which is frequently used。In large language models and on GPU computing。

So compiler cannot efficiently generate assembly when I use before 16。So。

We have like a special instruction set for this type of。Data。Which compiler didn't use。

 So I basically。Createated few specialization for my kernelnel， just to utilize these instructions。

And this basically template visualization can be removed when compiler。Can do that job in the future。

 So it's like a temporary solution。And unfortunately。

 I cannot compare with open blast because open blast does not support default 16 right now。So。

 I got3 point。You here are nine terlos of the performance。It's less than fl， but still。

 we basically got this for free。 I do nothing。 I just instead of double and float use B flow 16。So。

When I compared with the last。Not the last， but we then compared the matrix multiplication performance in then 5。

 I' noticed just that we kinda at the same level。 So I。

 I believe that C plus plus can deliver assembly class performance on matrix multiplication。😊。

And my implementation， I believe it's not the best one。 I still think that it can be better。

So this is all I have。 Thank you so much for your attention。 And now， if you have any questions。

 please feel free to ask。

![](img/507572f9fc54483e25786c793f65ea20_6.png)

Yes， we have a mic here。Perfect， thank you very much for the talk。 Mary， Very interesting。

 Very welcome， Truful。 So you have open blast， but you have also M K L to convert to。

 Did you compare it with M K L， the Intel M K L Library with M K L， Everybody asked me。

 But the problem is。😊，There is one more library， which is called Blis， E LIS。

I read the article with benchmarks there， and they showed that the performance of that library on AM M G CPU dramatically。

Like it's much worse than on Intel CPU。 So basically M K library behaves really good on Intel CPUs。

 but really bit M that but your hardware was Intel in one case。

 your hardware was intel the first case I didn't measure because I was focused on the okay Okay。

 so another note I'm developing a library for multi dimensional array that the goal is to provide all these abstracts that you had to put manually。

 I mean， in some sense， you are using M span now。 but idea is to give even more abstracts that M span can give you。

 And so we should talk later the。😊，嗯。Just like curiosity。

 I noticed you you said that the memory was aligned。 but in 26， I saw using store。And load unaligned。

 Yeah， exactly。啊。I believe I tried to use a instruction， and I didn't see any difference。I tried。认可。

That's just my my Thank you so much。Hi， a great talk。 Thanks so much。 Yeah。

 you would mention using M span。 I was wondering what， whether。

 what abstractions would make it easier to use M span for this case where you have a lot of compile time dimensions。

 Did you find that you needed to build more abstractions， Are there things that you would want to。😊。

Have in future versions of the C++ standard library。收。I still think about abstractions。

 I don't have answer yet。I， I'm going to try to because with M span， what I've already tried。

 like I remove all these pointers from matrix implementationation and use M span only。 That's good。

 like。Everything was in line， no performance in。 Then I tried to use。Customization point。

 which is layout and compiler。Cannot optimize that And performance much worse than I expected。 We。

 were you， Was it reducing to layout stride when you took slide。

 I created custom layout because I not just tried。If you remember。

 it's like I need to iterate over columns， then jump to the next element。 Yeah， therere also。

 it's like， it's not just a stripe。 It's like a Z pattern。 Yeah Yeah。

 So I I basically implemented that。Dot access button ist layout yet。

Do you think there's still room for that to be optimized in your custom layout or is there something that's missing in the standard。

 maybe。是是。So what I'm working right now。Multi， multi trading strategy， utilization of the。

Straight hardwares。And I didn't mention， but it's like when you have fixed dimension of marks。

 you don't need to handle tails。Right， so。I'm trying to address these issues first。

 get the full picture。 Okay， and then I believe it will be much more easier to see what the abstraction can works。

 Sure， well， feel free to reach out if you come a。 Thank you so much。 Thank you。😊。

Thank you for the nice talk。 See results we have shown more and implementation seems really good。

The question is， he that CPU was showing us was a mobile CPU。 that is not really。

Good for number crunching。 So what was the second CPU you compared with。Last tip I used Yes。

 it's A M D 99，50 x。99，50 x， but this is， this is the server CPU。 It's still a desktop CPU。

 desktop CPU。 Okay， good。 so two remarks here on HP PCC computing。

 the first thing they are doing is they disable hyperreading because that blocks your maximum performance report。

And when you on a desktop， you still have the goi and so on。

 So that also takes away a lot of computation power。

 So you should really test on a cluster Linux machine with no goi enabled at all。 Yes。

 that's the good common， but。Unfortunately， I tested not in a clean environment。

 So in the background， there were a lot of cleans processes。啊。In general， yes。

 I need to have the skin environment because other programs pollute your cache and so on。

 And that's what I also noticed when I use。Like highly optimized version。

 They don't have lots of impact from， for example， browser。 But na implementation， for example。

 the performance dramatically change when some process happens under the hood， but highly optimized。

 they don't jump in terms of performance too much。Okay， then jumping like， there is like a range。

 but。So so it didn't get us from the slides。 So your first thing got took 17 seconds。

So what was how much time you had for the last implementation？

Sorry yeah just have seen last overview that that's on there I said。

The overview of your performance results the last one。Would the tableYeah has the table one。Okay。

 it's so your execution time is now below1 second。 That gives you a jitter again。

 So that that's that's then maybe a perform measurement problem again。

Because the first execution time is quite long，152 seconds。 That's okay。 then you have such effects。

 So the last one is quite low and you should increase your test size。Test size。 Yes。

 for the last one， these size is too， too small。 I had such。 Yeah， I didn't provide。 but yeah。

 I increased the size of the mattresses to see if I have the same performance in terms of gigops。

 at least， yeah。So it for a long question markath on。Very good talk， good questions first。

 when you did underroll and prefge， your custom implementation。

 how did you assign the parameterss like by how much to enroll and also the prefage distance？

Pre distance。 So for preferred distance， my reasoning behind that， if I'm using the。The element。

 I would like to prefer the next cache line。This is the main reason， or for matrix C， for example。

 since I do not copy the elements from matrix C into the buffer。

 I need to iterate with the huge stride over the elements of matrix C。

 So here also I do the pre with the huge strip， which is equal of the dimension of the matrix。

So this is the two place where I have for the underroll， like by how much to underroll。

How much when did did you when you did the custom under？Like by I much to unroll the loop。

 How do you inside that。 you just fully underroll everything。

 Not everything just two inner loops over I and J index。 So over K。

 I try to enroll just to see if it has an impact。 It doesn't。 It just show me like a。

Beautiful per stas where there is no like in red instructions， but in terms of execution time。

 it remains the same。And then second question is， have you tried different versions of compilers and what the different performance all the time。

Especially for the last one， because I needed to use M G span。 I needed to use B 16。 I needed to use。

Smmed library， so you need to use different libraries。

 different components to satisfy all of this like right now。

 I believe I stay with GCC because GCC supports everything。But during the experimentation。

 I use different compilers and also checked like different version of of the compiler。

 if like any degradation or improvements。 I didn't want say。I see。

 but like quantitative was a difference in performance you saw between different compiles。yeah。

 so as I mentioned， some of the implementation， which is not optimal。

 GCC sometimes outperforms Silang significantly and vice ver for another implementation。

 Sil outperforms GCC significantly。 I don't know why。This in type number wise。

 like what the order of like significantly 70%，0%。 Okay， thank you。 You're welcome。

Really excellent talk， thank you just a conceptual question when you were talking about the tiling technique。

Reminded me of convolutions and image processing。 So do you think your progression of you know progressive optimization would it change if the case was different and you were dealing with images or how would you think about that？

So could you please repeat your question？ Yeah， just I guess the question is， if you were to。

Optimize just the tiling technique or starting point， because you're dealing with images。

 Would this change。How you thought about。Adding progressive optimizations if you were handling images。

Yeah， you're kind of stepping through different ways to， you mean。

 if you just pick one optimization technique and apply for your particular case， Yeah， Yeah。

 it should definitely help。Okay， yes。Okay， so actually， these orders。

I also kind of spent quite time to understand in which order to show you。

 because this is not the order I implemented much。 Yes。

 I see it's just like one of the random order I decided。

To demonstrate all of the optimization techniques， But you can reorder the way how you apply these optimization techniques。

 and you still will get the improvements。 Oh， okay， Yeah， thanks。 You're welcome。Actually。

 if I may add on to that a little bit， I mean。Convolutions work a lot like matrix multiplies。

 as you probably already know。 And so at least we think of it in in similar ways and apply similar sorts of optimizations。

 But there maybe the differences。The way that you translate it into a matrix multi like the outer。

The tiling for cache or the tiing for thread block is kind of the same approach。

 But maybe the way that you load in the tiles and store the tiles is a little different。

And our hardware has some support for convolution specifically， and other hardware may not。

 so you may have to think about how you're loading it。 and in particular。

 if you use the IM to call approach for convolutions。

 you're doing extra memory movement in order know like you're replicating data and so you have to think about。

How to deal with that。Mhm。😊，Thank you。

![](img/507572f9fc54483e25786c793f65ea20_8.png)

![](img/507572f9fc54483e25786c793f65ea20_9.png)