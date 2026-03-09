# 美国贝鲁特大学《GPU计算｜CMPS 297S396AA - GPU Computing - Spring 2021》（豆包翻译 - P7：-07-Lecture 07 - Profiling.zh_en - GPT中英字幕课程资源 - BV1bw4m1k7a1

![](img/cc887206d10388f4c86cf595f07a7960_0.png)

Hello， everyone and welcome to our  seventh lecture of。GPU computing。 Today。

 we're going to be talking about profiling。 In other words。

 how to profile our hda applications to see how well they're performing and where the bottlenecks。

So last time we spoke about DM banks。And we looked at how a DM bank is organized。

 We says we have these DM arrays that consists of DM cells and we we the address。

 the memory memory address is divided into a row address that accesses the DM array。

 and we read a whole row of the DM array。 And there's the slow process of， you know。

 going through the send splifiers and putting it on the column latch。

 we also have to write it back because when we read that we destroy it。

 So this a whole process slope。 But once we have that row in the column latch。

 the column address is used to select。Which part of the road that we read we want。

 And this is a relatively faster process。 And it turns out that if the next axis that comes along has the same row address。

 but a different column address， then we don't actually have to read the entire Dm array again we can simply change the column address on the mugs to read a different part of the whole row that we read and we call this and burst this whole row that we read from DM array。

 this is called the Dm burst， and if our aes land on the same D of consecutive axis land and the same Dm burst then they are faster。

 So the timeline looks like this， if we have aes the different Dm bursts。

 then we have we have all this time that we have to wait to read from the Dm and then we have the part where we read the part of the burst that we want。

 and then if the next axis to is to a different burst and we have to wait again until we read Dm array and then we read from the burst the part of the burst that we want。

 however， if aes land in the same burst。Then we can simply read from the DM and then we read part of the birth and then if the next axis is in the same burst。

 then we just read the next part of the birth that it's much faster。And because of this。

 what we like to do when we access when we when we access global memory is we like threads that are in the same war to access consecutive memory locations because when threads that are in the same war。

 access the same memory locations， they're going to issue load instructions that are likely at the same time that are most likely going to hit the same DM birth and what the hardware can do is that it can combine accesses you know combine accesses to nearby locations into a single access such that only one DM transactions is needed。

 and this is known as memory coales on the other hand。

 if threads in the same war at the same time access memory locations that are far away from each other。

 then each then these accesses cannot be combined and each access will require。

Its own load load operation and the roadorp will have to wait for all the load operations to complete。

 and this is known as memory divergent。We also saw how we usually have multiple Dran banks。

 You can't have gigabytes of DM all in one DM array。 So we usually have multiple DM banks。

 and we read from one of these banks at any point in time and what this does is that it gives us it gives us a way to hide the DM latency。

 So if if I'm reading from multiple Dran banks then then you know while'm while I'm waiting for one the DM array from one of the banks I can be reading from the bursts of the other bank。

 And then by the time I finish reading these births。

 then maybe the other bank is ready I can read those bursts and by that time maybe there's a third DM bank that I was reading from the DM array and now it's ready and I can read those births and by the time I'm done you know I go back and then the other DM bank is also ready for me to。

Read its first。 So for me to effectively utilize my DM。

 I want to have many memory aes at the same time going to different banks in order for me to hide the latency of the different banks so that I always have data in my memory system ready for me to consume。

 So we saw how having high occupancy in our Ss， not only helps us hide the latency in the course。

 but it also helps us hide it also helps us hide the latency in accessing our memory。

 we then looked at it at another optimization， which is threat coing and we said that threat couring is an optimization where so far we've been assigning threads to the smallest possible unit of parallelism but we saw how threat coing allow in the thread coing optimization we have a threat process more than one unit of parallelism and what this does is that it allows。

😊，Ca us to。Eliminate any redundant work across threads or any price that we pay for parallelism and an example we gave is with tile matrix multiplication we saw how you know you different thread blockss that are processing different output tiles might be loading the same input tile so here the thread block assigned to the dark orange output tile and the other thread block assigned to the light orange output tile both read the same blue input tile。

Now， if these two thread blockss are going to be running in parallel。

 then fine this redundancy is a price that we pay in order for us to get parallelism。 However。

 if these two threadlocks are actually going get serialized by the hardware because I have many more thread blocks in the hardware and simultaneously run。

 then maybe it's better for me to just have one thread log be responsible for these two output tiles and have this threadlock read this input tile and the green input tile and then compute this output and then before proceeding to the next the next tile of a it's simply keeps the same tile of a and goes to another time of B and processes and different output tile and by doing this what we've done is we've saved having to load a and then this time of a redundantly for both this output time and this output。

And with that， this was a summary of the different optimizations that we've covered so far。

 tuning resource usage to minimize occupancy， minimizing control divergence to get symptom efficiency。

 having uniform memory access patterns so that we have memory coalescing。

 using shared memory tiling to capture data reuse and then thread couring to basically eliminate the price of parallelism。

 that price of parallelism could be redundant data that we lower it could be redundant operations that we perform。

 or it could be something else like synchronization overhead that we will look at an example of later run。

And with that， we said that there exists a tension between these different optimizations。

 for example， when I maximize occupancy。😊，What I might end up doing is I might end up if I have the maximum of occupancy。

 the maximum number of threads on my SM that I can possibly have。

 if these threads act with a lot of data， these threads may end up starting to compete for the cache。

 for example。And they start evicting each other's data out and sometimes that's fine sometimes。

It's worth it for us to thrash our cash in order for us to maximize occupancy so that we can hide our latency。

But at other times， it might be the case that no， I prefer for my threads to I prefer to for me not to have too many threads。

 so not to operate at maximum occupancy in order for me to have better cash behavior so then this is an example of where having too much maximizing occupancy might actually hurt performance。

Another example is shared memory telling。 so when I have when I use shared memory piying every thread block needs to reserve as a certain amount of shared memory and if I use more shared memory。

😊，That allows me to have more data re， however， if I use too much shared memory I could end up in a situation where my occupancy is limited because for example。

 if my SM can take 2048 threads or so I create thread blockss that are 1024 that means my SM can take two thread blockss。

 however， if one thread block requests the maximum not shared memory on the SM。

 then because of the shared memory requirement the SM will only be able to have one thread block or 1024 threads running at the same time。

 even though theoretically it can have 2048 but the shared memory requests limits my occupancy so this is another example of where there's attention between these different optimization and we also saw how a thread coing when we course in when we have cosing it reduces our redundant work but threads when we co in every thread may require more resources which again may limit our occupancyup。

😊，And based on this observation of there being a tension between the different optimizations。

 what we said is that we need to find a sweet spot that achieves the best compromise between competing optimization and important part of finding that sweet spot is understanding what is actually limiting the performance of my kernel right is if the memory or is it divergence or is it you know is it something else to understand what is limited so basically you need to know your bottleneck so a bottleneck。

Is basically a constraint that limits the performance of an application， right。

 There's all kinds of different and different resources that we reuse when we execute on on a piece of hardware。

 And one of these resources runs out before the other。 Okay。

 so my may run out of bandwidth before I run out of flos or maybe I run out of flos and running out of bandwidth or maybe I run out of thread slots before I run out of shared memory or maybe I run of shared memory before I run of threat slots。

 So there's all kinds of different different。Resources that that may limit my performance and the resource that limits the performance is called the bottleneck。

And when we when we this bottleneck， it depends on the application right because different applications use different amounts of resources so the bottleneck is going to depend on the application。

 it also depends on the device because devices， different devices also have different amount resources。

 some devices have higher memory bandwidth than other devices。

 So the combination of the application and the device it dictates what the bottleneck is and the optimizations that we've seen so far。

 often trade off one resource for another。 Okay， so usually when I apply an optimization。

 I use more of one resource in order for me to use less of another resource。 So for example。

 when I apply shared memory tiling， I use more shared memory in order for me to use less of my global memory bandwidth。

So knowing what but for example， if my application is not limited by global memory bandwidth。

 it's limited by occupancy because of shared memory。

 then obviously a solution to my problem wouldn't be to use more shared memory。

 a solution to my problem or a solution for me to optimize forms further is maybe to reduce the amount of shared memory。

So， you know， this just highlights the importance of knowing what your bottleneck is。

Before going and applying an optimization because you don't want to be to apply to optimization that trades off the resource that is actually the resource that is bottlenecking your performance okay。

 so it's important for you to be able to properly diagnose what is the bottleneck of your application so that you don't optimize for the wrong resource。

O。😊，Any questions about what we covered last time？I know last time I kind of rushed the end because we ran out of time。

 I think we also had some some connection issues last time。

 and that's why we we were right out of time。 So does anybody have any questions about。

 you know what we covered last time before I move on。Okay， if there are no questions。

 then today what we' will be talking about is how to know your bottle line， Okay。

 so today we'll be talking about how to know your bottlenecks and the answer is through profiling so the couldda platform provides a pror that allows you to that allows you to know profiler application。

 see what's limiting your performance and analyze your bottlenecks in order for you to decide what is the best optimization tool it。

So we'll be doing doing kind of an example of profiling today。

 and we'll be referring to the vector edition application that we implemented in the second lecture of the course away back in the beginning of the。

😊，Okay， so let me switch to the terminal。

![](img/cc887206d10388f4c86cf595f07a7960_2.png)

Over here， I have my vector and kernel that we implemented last slide。

 I's take a look at it so here if you remember this was a vector edition kernel。

 there was basically a thread that was reading to output elements and writing to an input element。

Okay， there's two things that I changed in this file。

 The first thing I changed is I added this header file over here， Kuda profiler API。 And at the end。

 what I did。 So at the end of the main function。 I added this this call to Ka profiler stop。

 basically what this does is when if you're profiling your code。

 it just makes sure that before the application exits all the profiling information that was collected would be would be kind of saved before the application exit。

 So this is why I I added this call okay。Everything else is the same。

 we call like add on the GPU here we do our equipmentment copy。

 we call our kernel and then we do ament copy back and we do Ca free and then the kernel is also the same。

So let's get started， I'm going to compile this。Okay， and before you know。

 you we just we just run the vector edition and it runs and then it we had inserted certain commands in our in our code to print out the timing information。

 Okay， well， it turns out we didn't have to do that。

 because we could have actually let the profiler do it for us。 and here's how to do that。

 So the profiler that comes with the co SDK is called NV prompt。Okay， so envy Prof。

 the way you use it is there's different ways of using it。

 kind of the the simplest way is to write envy Prof and you provide your program your binary。 Okay。

 so you write en profit and you run by binary。So I run NV Prof and I run my binary。Okay， it runs。

And after it finishes running， what it does is that it outputs all this information for me。

So this is a table and the table basically has the different calls that we made Okay。

 so here its the time that we spent copying from device to host here。

 this is the time we spend doing a copy from most of the device This is my actual VA kernel。

 This is the co event copy API called notice here it separates things into GPU activities and then API calls These are API calls that we call from the CPU and these are things that happen on the GPU。

So we call put and copy on the CPU and then put and copy on the CPU performs the GP activity。

 which is copying from the device to host or from the host of device。 Okay。

 so what this is telling us is that for each of these activities。 So the MacA kernel， the web copy。

 device synchronized could a free K analog， all these different things that we do。

 a lot of these things are happening without you without you knowing that they're happening because they happen under the hood。

😊，What it tells you is for each of these things， what is the time that it takes？Okay。

 it also tells you for some of some of these things， how many times they're called。Okay。

 so here it has the time that it takes。If they're called multiple times， there's an average。

 there's a minimum， there's an maximum this tells you the total time that something takes and it also sort tells you what percentage of the total execution time it takes。

And what you'll notice is that the times are actually very similar to the times that we timed up here so here you can tell that copying from the device to the host it telling us it takes382。

82 milliseconds up here we timed it as 384。2 milliseconds The reason is that over here we're using a CPU timer So here there's a little bit of additional things that the CPU is doing wireless timing This is probably a more precise timing for how long how much time we're spending copying from device to host。

Okay， and it also tells you what percentage of the total application time is spent doing this。

 We spent 52% of our time copying from device to。Okay。

328 for copying from post the device are also similar here。 We have 329。

 Our kernel execution took 13 milliseconds at 1。8% of the total time。

 And that's also similar to what we found over。 Not that there are always slightly less because this measures a little bit more than。

呃，真的真的。Then you know， then just the pure time to takes the uptake on the GPU because there's a little bit of overhead from the timers that I'm using the CPU timers that I use。

Okay， so this is this is you know， this is very convenient because when you write the CDa application if you don't feel like inserting all this code。

 you saw how you know there's a lot of code dedicated to just be inserting and inserting timers and the reason I did that is because I didn't want to have to run the profile or every time we do a demo demo in class。

 but if you don't want to in yourku application have to insert all these timers everywhere you don't have to it's as easy as just calling M Prof with your application and it basically tells you how long everything is big。

😊，Somebody's asking how would N Prof work on the other machine that you guys are using。

 which requires you to submit jobs and batches， But what you could do is you could you could submit a job interactively if you would like to run a DProf and and you know with your on your application Okay and then we're also going to see today how we can use a DProf to also export more information about our code in order for us to analyze it using a visual profiler and we're actually going to do that do that next okay。



![](img/cc887206d10388f4c86cf595f07a7960_4.png)

So this is the command to run enV Prof on vector edition。

 this is an example of the output that we get。 These timings are a little bit different from the timings I'm showing you because I obtained them on different machines than thet I'm using for this lecture。

 but the trend， the trend should be should be similar。 Okay。

 don't worry about taking notes all the commands that I'm going write in in the command line I will have in the slides for you。

 So you can just sit back and enjoy the you know， the lecture and the commands will be in the slides。

 So you don't have to worry about taking notes of the command。😊，Did somebody have a question？Yes。

 I wanted to ask about what's happening under the hood with the profile。

 Is it like hardware counters？So it depends what you're profiling over here。

 you're just finding the execution time of every call that the GPU does so this doesn't really need hardware counters。

 you have this notion of a stream and we will talk about streams they on in the course but you have this notion of a stream that has these tasks taking place and they wait for each other so inside of these streams what every Pro does is that simply times how long each activity each activity takes okay so it's quite easy for you to imagine know that when you call put it that copy and of quantum copy when it starts and when it finishes there's the runtime system is somehow taken care of starting a timer when you start and then stopping a timer when you stop later on what we' see is we're actually gonna profile all kinds of things like a cache and occupancy and every bandwidth and all these things and these definitely use hardware counters and you'll see you'll see you actually。



![](img/cc887206d10388f4c86cf595f07a7960_6.png)

See kind of selfie going on that shows you that these hardware counters are being okay？

Okay us's do that， we're just about to do that。So let's say I wanted so here it prints these timing results for me at standard output。

 but let's say I wanted to export these values to a file so that I can I can analyze the more visual using a visual profiler well I can do that and the way to do that is like this so before what we did is we called enop we call envy Pro。

On our vector ad， our vector ad executable， If we want to export these timing results to some file。

 we can actually write dash code。And provide the name of the timeline file that we want。

 So here we can write something like timeline dot prof。 you don't have to say dot prof。

 You can name anything you want。 I just like to call call it dot prof to remind myself that this is a file that contains profiling information。

 okay。So I can run andVProf and provide it with and tell it that I want it to export all this information to a profiling file and it does that for me。

 so here I'm going to run it again and it runs and it's going to export the information。ok。Okay。

 and you see it tells us here， I generated a result file and that this result file is at this location。

Allright， now what this does it gives me timing information。

 but if I want other kinds of information related to things like occupancy。

 things like instruction count， things like memory bandwidth。

 I can actually also generate that information and to do that。

 there's a command which if I don't want the timing information I want other kinds of profiling metrics。

 I can actually write dash M。And I can specify one of the profiling metrics that I want here I'm just going to write all because because I wanted to export all the profiling metrics。

 but you don't have to write all what you can do is you can know you can look in the documentation。

 see what proing metrics are available and you can maybe maybe you're interested in a specific profiling metrics and you can just export。

Okay and and now what it's going to do when I write dashM all is that it's going to output not the timeline。

 not these timing results， but it's going to output these profiling metrics to the profiling file Now I don't want to overwrite my timeline profile so I'm going to call this something else for example I can just call it something like metrics。

Okay。😊，Now you notice that when I run this， these profiling metrics that we're about to collect about things like occupancy C。

 cash and delivery bandwidth， things like that， they use hardware counter and obviously there is an overhead to use a hardware counter。

Because when you use when when you start when you start profiling。

 you're interfering with the execution， the actual kernel， because profiling takes time。

 you're spending more time gathering all these statistics about the about the cash。

 all these statistics about， you know， occupancy and things like that。 so because。

We don't want to interfere too much with the the performance of our application as we profil it。

 because then our profiling is not going to be accurate。

 What M profit is going to do is that it's actually going to run our kernel multiple times。

 And each time it's going to collect a different set of profiling metrics。

 So you're going to see that happening right now。 So I run this， it says M profit is profiling right。

 And then the。So here use as this replaying kernel， replaying kernel， replaying kernel。

 and every time it collected a different different。Okay。

 and I notice how the overall time took longer， the reason is that this is actually running many money kernels is not just one。

 so the timing information we're getting to hear is not reliable。

 but the profiling information that we get is hopefully reliable because we ran a kernel many times and each time we collected a different set of profiling information。

Okay， so now we have our profiling our timeline and timeline。 Prof and our metrics and metrics。

 Prof now what we would like to do is we would like to you know take a look at Timeline。

 Pro and metrics。 Prof and see what information they give you。

And the best way to do that is using the individual visual profiler。

 There's also something called endight that comes as with different Is。

 If if you're using visual studio or eclipse， you can use use something called endsight that's that's。

 you know， also a very powerful profiling tool。 But for simplicity here。

 I'm just going to be using the Nvidia visual profiler。 And to write that。 Im very run and easy。😊。

So XZVP， now the Infinia visualual profiler uses a graphical user interface。

And since this is a command line， it doesn't display graphical user interfaces。

 I I'm connected to a remote machine via command line here。

 So what I've done is when I connect it to this machine。

 I actually enabled something called X forwarding that allows you to forward the graphical user interface that's running remotely on this machine to be displayed on your local machine So here NVVP is actually running on the server。

 but it's going to send me the graphical user interface so that I can display it on my computer in which I'm using to to teach the lecture Okay so I'm going to run NVVP okay。

😊。

![](img/cc887206d10388f4c86cf595f07a7960_8.png)

I'm going to put this at the a so that I can keep using my command line。

 This tells it This tells it to run it in the background so that doesn't so that I can keep using my command line after after I went。

The red V VP。It takes a while to run， it pending me the graphical user interface here tells me to specify where I want to put the temporary files that the profiler is using they is press okay。

And now it's launched the profiler， and this is what the profiler looks like。

So here you can create a new session and this you can create a profiling session where you can use the visual profiler itself to profile the application。

 or you can import profiling files that you you generated using enV Prof， which is what we did。

 So what I'm going to do is I'm going to click hit import。

 and I'm going to specify that them importing files that were generated by NV Prof。 I hit next。

 You can profile multiple processes。 We just have a single process。

 I'm just going keep in a single process the hit next。

And then here it asks me for the timeline file and also asks me for the mentoring file。

 So I'm going to browse to find the timeline file here， my timeline file is over here。Iline。 Prof。

 then I'm going to browse to find the metrics file and here the metrics file is metrics stop。Okay。

 we're going to hit finish。 And what this does is that let me maximize this。

 So now what it has done is it has。Put the timeline over here and then the metrics we can take a look at down here。

 let's take first let's take a look first at the timeline。

So here what the profiler does is that it has this timeline notice up here you have seconds and over here on the left you have the different activities that take place So we have things like Men copypy host a device。

 things like Mencopy device to host things like compute So here we have the VCD kernel that we executed and then you also have something like streams everything we'll look at streams later。

 but basically everything we're doing now。Is going into the default streams。

 We will see all of these things overlaid with each other and the default stream。 So over here。

 this is the good device synchized I execute at the very beginning。

 And then here you don't see anything over here because this is the time that the CPU was spending generating the data。

 So， and then later on， once the CPU was done generating the data over here。

 we can see our our actual。Our actual timeline， so you'll see what what's happening here is that you'll see the time that is spent doing KaM copy。

Okay， so it tells us it's doing QM copy here and then there's also a little bit of time over here if you can see it。

 this is the time that's done it' using to Kamal okay and then here you do KM copy and then over here you're doing another coM copy。

Here， remember， we copied two arrays， not just one array。And then over here。

 this is the time it took for the vector Ed terminal check。Yes， let me have you， if you guys。

So here notice how here it says could copy。 So this host a device。

 This is could have copy device to host。 So that's their corresponds to this。

 This over here is the vector edition kernel。 So that corresponds to this。

 And this here shows you a stream where everything's overlay。

 So you will see what the time and the time it' taking。

 So here tells you it spent this much time doing could have copy host device and this much time do get another couldnt copy host device this much time in the vector ad kernel and this too much time doing couldn have copy device。

And then this over here at the end is also doing the couta free stuff。Okay， notice down here。

 if you take a look at what's showing up over here， it'll show you that the test could are free。

And tells you to start end time safety over here， it'll show you that it's safe could amount。ok。😊。

Any questions about the timeline？So this is this is a prettier way of visualizing how what where time is being spent in your application compared to this you know oldcho way of using the profiler the NV Prof to just throw up throw out all these all these numbers and also you know these are these are for different purposes this is quicker over here you just get that numbers quickly okay。

 but this is if you want to do a more in depthth analysis and spend more time on it。Any questions？

So doctor， but this doesn't tell us if our application is memory bound or right we'll to that next so this is just the timeline and we're just about to look at the profiling the profiling and the profiling of the metric。

I just wanted to see if anybody has questions about the pipeline。

 I think it's fairly straightforward， right， I maybe how many people have questions。Okay， so next。

 let's now take a look at the profiling results。 I'm going to hide the timeline a little bit and here but we we can write something like examine GPU usage。

when the write example GP usage， it tells us you some high level information about the overall GPU usage of our application。

The whole application。And you notice that it tells us oh there's a lowM copy efficiency。

 there's low them copy an overlap， basically you can actually overlap multiple calls to them copy so just telling us that we're not doing that。

 we're not doing that and we are doing that because we haven't learned how to do that yet but later on hopefully we'll learn how to do these as。

😊，It tells us low kernel concurrency because， you know。

 it says the percentage of time when two kernels are being executed parallel is low。

 So we can actually call multiple kernels to run at the same time on the GP。

 But we also haven't seen how to do that。 So that's why it's telling us this。 And， you know。

 it tells us， you know， low compute utilization， etc cetera。 Now what we can do our program。

Could consist of multiple kernel。And what we can do is we can go and examine individual kernels now in our case we just have one kernel which is the vector industry kernel so we click on examine individual kernels here there's just one kernel。

 but if you run many kernels you would see many different kernel。So they click on this。

First it gives me some high level of information over here on the left。

 it tells me when the kernel started executing， when the kernel finished executing。

 it tells me the grid size the number the number of blocks in the kernel tells me the block size。

 the number of threads per block， it tells me the register usage so how many threads are used by how registers I used by each thread tells me how much shared memory is used by each block。

Okay， and here it also tells me stuff about occupancy。

 So it tells me how much occupancy is has been achieved by the kernel。 Okay。

 and this here tells me what is the the theoretical， the peak occupancy that my kernel can achieve。

 So in my case， when I call this vector edition kernel。 And the number of threats per block is 512。

 So that's usually large enough for me to not be limited by the block size。

When it comes to occupants。Also the number of registers for thread is low I'm not using any shared memory。

 so there isn't really anything that can limit my occupancy over here and that's why my theoretical achieved occupancy is 100% I can reach 100% occupancy in the way I've configure my kernel The actual achieved is 88。

1% and that just has to do you know you can never be 100% occupant there's always you know different things that happen that may result and you not always fully utilizing yourM that has to do with some runtime things that happen at runtime in the device and just basically have things are scheduled。

Okay， so now what we can do is we can go and look at more detail at the kernel。 Okay。

 so here we can write something like perform。A kernel analysis。

 so I can click perform kernel analysis。And the first thing that I get is the utilization and this utilization is divided into compute and memory。

 So it tells me how much am I utilizing my memory system。😊，And how much am I utilizing my course？

And from looking at this， does it look like this application is compute bound or is in memory bound？

Computer bound。他 to the来。RightSo I'm not utilizing my compute。 I'm fully utilizing my memory， right。

 So what is what is the what factor is limiting， is what factors is not being utilized and what factor is limiting you from utilizing the other factor。

It's firmly bound， because it's。I think a lot more memory than complete so。Right， you're right。

 It's memory bound。 So remember this is vector addition。

 right so we analyzed vector addition before and we observed that vector addition does very little operations per byte。

 So vector addition is memory bound。 and we can see this over here because we can see that the memory system is always busy。

😊，Right it's more than 80% busy the memory system and that's pretty high。

 right it's very hard for you to utilize the memory system 100% okay。

You're going to has to be perfect and run perfectly in order for it to utilize the nervous system 100%。

 so 80% is actually pretty high so your memory system is fully utilized。😊，Okay。

 the compute to the course are actually not not utilized that much。

RightSo I've only utilized my course a little bit more than 10% of the time。

What that means is that the remaining 80，80% to 90% of the time is the cores are not doing anything。

 they're idle。And so that shows you that I'm really underutizing my compute andm fully utilizing my memory。

 So obviously， my kernel is memory bound。And the profile is actually smart enough to tell you that。

 so if you read up here it says kernel performance is bound by memory bandwidth。

A kerneldle province is vow by memory Benmin。So a very quick way of figuring out if your kernel is every boundary compute mount。

 if you don't want to sit there and count all the loads and reason about them in your code is by profiling group。

Now， another nice thing is that over here when it tells me how the cores are utilized。你 train。

So here when it tells me how these cores are utilized。

 it actually tells me how when the cores are being utilized。

 how this utilization is really broken down。So what this is saying is that it's this dark purple is the amount of time it spends doing arithmetic operations。

 this steel color is the amount of time it spends doing control flow operations and the light purple is the amount of time it spends doing memory operations right because when we execute in our cores。

 we execute instruction Some of these instructions perform arithmetic。

 some of these instructions are prefer control flow like the if statements and things like that and some of these instructions are going to be load and store instructions。

😊，So here you can tell that most of the instruction most of the instructions executed by the core are memory instruction。

 there's a very little amount of control flow instruction and there's also a fair amount of arithmetic operation and this is not surprising right because every thread is doing one every thread is doing one if statement so it has a branch instruction and every thread is doing two loads at a store so and it's doing one edition and is doing two loads at a store so it's August that there's going to be more memory instructions than than arithmetic instructions and there's going to be a very little amount of control flow operation。

Okay， any questions about this， we'll go into more details now。

 but any questions about this plot over here。Okay， so since our there's three different kinds of analyses that we can perform。

 there's memory bandwidth analysis， compute analysis， and also latency analysis。

And since our kernel is limited by memory bandwidth。

 what the profiler does is that it recommends for us use to do the memory bandwidth analysis first it says the most likely bottleneck to performance is the kernel is memory bandwidth so you should first perform memory bandwidth analysis to determine how it is limiting performance and later on if we really feel like it we can also do compute analysis and weightency analysis okay。

let's start with memory bandwidth analysis， when we click on memory bandwidth analysis。

 what the profiler tells us is it tells us how much each part of the memory system is being utilized so here you'll notice that this table here is broken down into shared memory L2 cache there's something called a unified cache and then there's also the device memory which is the global memory and the system memory has to do with you know the CPUU memory。

So what you see over， you really knows。 So what is， what is what。

Part of our memory is fully utilized and what other parts of our memory are idle。

The device memory is utilized the shared the caches are not very utilized。 exactly。

 So here youll notice that our device memory is fully utilized， right， very high utilization。

 almost to the max。 Okay， it even tells us that every bandwidth that we are achieving。

 It tells us where we are achieving a every bandwidth of1 and 24 GB per second。Okay。

 and it also tells us that， you know， obviously， we're not using shared memory。Okay。

 our L2 cache is idle most of the time， it's not fully utilized。

Do we spent most of the time waiting on our device memory。Okay， add， etc cetera。

Another thing we can see is we can see this nice image that that tells us you know shows us the connections between all the different memories and it tells us on each of these connections。

 what the utilization， how many requests were made So here here reflects the vector edition kernel and it tells us this is shared memory。

 this is texture memory， local memory， global memory。And what you can see is all the requests。

So you know， shared memories， texture memory， local memory， or these are all zero。

 and all the actual requests are are to be global memory。Okay， so here at this moment area。

 it actually tells the number of requests。And then shows us how you know。

 go to unified cash L to cache and then the device that it tells us these you know how much each of these links is achieving。

Okay。😊，So this is not surprising right， we knew that vector edition was limited by global Larry bandwidth。

 but this kind of verifies what we expected and when you're writing very complex applications。

 it becomes harder and harder to reason about what's limiting your performance so profil becomes even more and more important。

ok。😊，Let's go now and take a look at computes so obviously obviously if we're profiling and in order to optimize our code。

 it's very obvious that what's limiting our bandwidth here is what's limiting our performance is global memory so we have to go and optimize that。

 but let's now take a look and what else what other kind of information we keep look getting so we could come back here and we can perform the compute now。

So here if I write perform computeute analysis， it gives me different kinds of information。

 It tells me things about functional unit utilization。

 So it tells me each of the functional units in my core how utilize are there so there's a load store unit。

 theres a unit for doing single precision arithmetic floating point arithmetic so this is what single says there's a unit for doing control flow right so this is this is what this says and you'll notice that we're utilizing them all pretty low and the reason obviously is that it's not a compute bound application it's a bandwidth it's bound by memory bandwidth。

This over here tells us the utilization。 This down here tells us。

The execution count the instruction count so it tells us how many FP32 instructions we have。

 how many integer instructions we have， how many control flow instructions we have。

 how many load store instructions we have etc okay so this is what this over here tells us and this count here tells us that types of floating point operations that we're performing so obviously here vector additions only doing F so it tells us that we're just performing F we're not doing FP mus for example。

 or FP mu add diffused multiply a Okay or any special instructions like sine and cosine and things like that。

So that is nice， it tells us you know what are the different instructions we're executing and how much utilization we're getting from our different functional units inside of the S okay。

 any questions about this？professorfeor， where do the integer instructions come from。



![](img/cc887206d10388f4c86cf595f07a7960_10.png)

Great question， so let's go back to our code。So over here。

 it's related to memory addresses and right exactly over this stuff。

 this index computation is all inger arithmetic。Right this comparison here， I less than n。

 this is an integer operation right the if the branch that branch is。

 if this condition is true is a control flow instruction。

 but i less than n itself is an arithmetic instruction and then as somebody was saying when you do Z of I what this does is this translates to several instructions that are're going to calculate the address because you're going to take the address in z and then you're going to add I to it before adding I you need to multiply by the size of the elements you're going to do I times4 because of floating point numbers for then you're going to add it to the base address of Z and then you're going to do the stored。

So each one of these memory aes involves several integer and arithmetic operations to calculate the address。

Okay。😊，Clear。

![](img/cc887206d10388f4c86cf595f07a7960_12.png)

Yes， thank you。Yeah， you're welcome。Okay， so now that we've seen the compute utilization。

 let's also go to our latency analysis so we can do latency analysis。And here with latency analysis。

 remember how we said that the most effective way of hiding latency is having high occupancy because when we have high occupancy。

 we're able to hide the latency of our applications by filling into these pipelines。

So here when we do mattency analysis， it tells us that occupancy is not limiting thermal performance Okay。

 so you don't have to worry about occupancy。Now we already saw here on the right that our occupancy was high。

But the nice thing here is that it us more information so it tells us the theoretical number of blockss we can achieve for SM and the device limits so we're under the device limit so we're not worried we can see that our number of active warps or a number of active threads are fully utilized and this is what we care about right so ultimately we care about having the maximum number of threads slash warps executing because the threads and the warps are behind behind blade。

And then here it tells us that our achieved occupancy is 88%， our theoretical occupancy is 100%。

 obviously the device limit is 100%。So we have nothing that's limiting occupants it also tells us you know the different resources so things like threats per block boards per block and none of these are kind of have reached their limit so we're safe in terms of occ down to here it has these nice plot that help you reason about oh if I change my block size。

 how will this affect occupancyccupants or if I change my shared member usage。

 how will this affect occupancycc。So here it basically tells you that if you increase the threats per block。

 if you vary the threats for block， you get this change in occupancy。

And notice how you have these intermediate values where the occupancy is lower than 100%。

 But then it goes back up。 These are basically the situations where your。

Total number of threads is not divisible by your threats per block。

 so here you would have full occupancy because of that lack of disability visibility remember we saw an example of this before。

ok。😊，One final thing we can do is we can do something called PC sampling and I think the device that I have doesn't actually support device that doesn't actually support PC sampling。

 however， in the slides I've included some profiling that I've done on a different device that shows you what information you get if you do but actually switch decides to show you that。

By the way， I have a screenshot of all the different things that we saw today in the slides if you guys would like to refer to it later on。

 you can also refer to the video。 This is what we would get when we do when we do the PC stamp。

 So what this tells us is it tells us the reasons behind the stove。Okay。

 so it tells us that if whenever we have latency， stall， whenever we have stalls in our。

It you know wars stalling。 and tell us the reasons why these wars stall。

 If you notice that for vector addition， the most common reason for a warmthp to stall as well。

 it's memory dependence。 it's basically waiting it's stalling because it's waiting for some sound memory operation to。

And this is obvious， right。 So vector edition， it's memory bound。 So there's not。

 the curls don't do much besides weight for for memory。 Okay， so so here， memory dependency is。

Is the most common source of stalls another one for example is execution dependency so this is probably because of the branch that we have we are doing the check right because we have the branch that compares that does the boundary check so we need to wait for the branch result to get resolved so because of this subors will stall until the branch gets resolved。

Okay， and these are other things that are just minor things that happen here and there and you know。

 depending on what your application is， one thing or the other may be big and that will help you reason about what's limiting your performance and what you should do。

Okay， any questions about this？嗯。Professor， why was there only。

 Why was there only four blocks active， And I couldn't we have used more。

 Is it because the size of the array we gave it is below。 Okay， so。

 the reason is that my block size is 512 threads。Okay， and my maximum number of threads is 2048。

 so 2048 divided by 512 is four blocks。So this is why I have four blocks active。

But the fact that I don't have the limit I don't reach the limit in the number of blocks is not really an issue right it's not an issue because what I care about time hide my latency is fully occupied having the maximum number of warbs sore threats。

So whether I achieve 2048 threads using four blocks that are 512 each。

Or if I achieve the maximum number of threads using eight blocks that are 256 each。

 doesn't really matter， it might matter for other performance metrics， but for the sake of occupancy。

 it doesn't really matter if I use four blocks or eight blocks that are smaller or 16 blocks that are even smaller。

Right。😊，Now， if I set my block size to 32， for example。

 and the maximum number of blocks I my allowed is 32。

 then my occupancy will be limited because then the block size will limit me before the maximumim threat count does and that's actually exactly what I was planning to do now。

As， let's go。Professor， yes question。Yeah， I just wanted to follow up。

 So since the number of active blocks is the number of active threads divided by。

The number of threads per block， it means we have not occupied all the Ss。

 like because if had we occupied all the Ss， then the blocks would have。Then oh。

 or can we have more than one block on MSM or not？Yes， yes。

 So we do can have more than one third block on NSM。 This information pertains to to NSM， right。

 It doesn， It doesn't mean were we， you know， you， we have many blocks。

 We have this many blocks up here。RightSo we have enough blocks to fully occupy all the them。

WhatWe care about when we talk about occupancy and hiding latency。

 we care about having achieving the maximum number of threats possible。Okay。

 but if if like we had filled all the Ss and still there were some blocks that had not been assigned to some Ss。

Right， so those blocks are simply going to wait until other blocks finish and then they will be assigned to a DS。

Okay， but would we see like eight active blocks per thread， they would it would still be four。

 but they were like it would take longer。this doesn't mean that only four blocks run the S run on an S for the entire execution。

 this means that four blocks at a time will run on the S。Okay， I see。 thank you。研nderwork。Do， yes。

significant part of the PC， like not the significant。

 but no A non negligible part of the PC sampling of the stall time was related to。

 to branches and the。I don't know what was， what was called exactly， but we we。

 we have no branch prediction， not even a simple one or speculative execution， Not at all。 So。

 so how much， you know， how much whether or not there is branch prediction and how statistical it is is something that is。

 is not necessarily public information。Oh okay， however， even if there was branch prediction。

 wouldnt it would definitely not be as complicated as that on the CPU。

Okay the reason being that you know the reason being that you know GPUs you care more about throughputency you don't care about the。

 it's fine if the branch takes a high amount of latency because you have many。

 many other wars that you can execute while waiting for the branch to get results。Okay。Okay。い合いわく。

Okay， let's take her with this a little bit。 Let's let's next with our profiler and let's see what happens if we set our thread block size to underutil the GPU。

 So here let's say so before I had set my thread block number fetch up to 512。



![](img/cc887206d10388f4c86cf595f07a7960_14.png)

Okay， now if I set my number of threats per block to 32， for exampleop。没有。落克 to闭。Okay。

 if I think my number says which is happening again？Okay。

 so if I set my number of threads per block to 32 for example。

 what we can expect here is we can expect to underutilize the GPU right because if I have 32 threads per block and I have a maximum of 32 blocks allowed that is I'm going to have a maximum of 2024 threads that I can schedule on the S but the S can support 2048 so here I'm expected to not reach for occupancy and let's verify that so I'm going to compile this。

Okay， I'm going to run my profiling commands again。 So I'm going to profile with the timeline here。

 I'm going to just write dash O to remember that this is the this is the。

The example where we were limit in occupancy。Okay， by the way。

 notice how our performance goes down right so before it was 13 millisecond now it's you know it's almost twice as slow why because our occupancy is half what it used to be。

So that's why it's twice as slow so your thread box size does really matter and then we'll also de generaterate the metrics。

Im also going to call this metrics dash arc。You notice how it runs many times They replace the kernel。

 Okay， and now we have generated these these。The the metrics and the timeline for the occupancycc。

 So let's go back to our profiler and let's let's import the these new files。 So we will go next。



![](img/cc887206d10388f4c86cf595f07a7960_16.png)

Thanks。This time， I'm going to get。Timeline dot or dash o that。Metrics， dashg。It hit finish。Okay。

 so now if we go and we examine GPU usage and then we examine individual kernels。

 we press on the kernel， now what you notice， you notice that we have actually I want to go back actually sorry I rush this So when I click on Ex GPU usage。

 okay， it tells us do the same thing when we write exam individual kernels。

 we press on the kernel okay what you'll notice is that over here on the right。

 it tells us that our block size is 32 and it tells us here that our occupancy at the achieved occupancy is 35% and it tells us that the theoretical maximum occupancy that we can achieve is 50%。

Okay， so it tells us that as long if this application launchs perfectly on the GPU。

 it won't be able to achieve more than 50% occupancy and it tells us that the factor that's limiting our occupancy is the block size。

 which is what we expect。And here if we run performform kernel analysis， again。

 the kernel is still limited by memory bandwidth as we expect。

 but if we run perform latency analysis， now it tells us it tells it gives us a different message up here。

 it says GP utilization may be limited by block size and notice here how the block limit is in red because the block limit now is。

It is higher than maximum， it tells us that the theoretical blocks that we can have is 32。

 and now it tells us that the active threads， the theoretical maximum number of active threads we can have is 1024。

 even though the device limit is 2048。Allright。Okay， so this tells us。

 this gives us some information about maximizing income。Okay。

 I notice here how it's highlighting our threads per block it points to 32 over here to showing us that。

 hey， look you're down here， if you change your thread block size a little bit。

 you can come up to a higher occupant。ok。😊，Is this clear to everyone any questions about this？

It's pretty neat right， the profiler it really helps with identifying what your bottlenecks are。

So this here is the you know。An example of occupancy analysis this here is an example of occupancy。

ok。😊，And that's all。 Does anybody have any final questions。



![](img/cc887206d10388f4c86cf595f07a7960_18.png)

Okay， well then， if you don't have any final question that is all for today and I will see you next time。

翻点位。

![](img/cc887206d10388f4c86cf595f07a7960_20.png)