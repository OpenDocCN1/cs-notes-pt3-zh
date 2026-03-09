# 美国贝鲁特大学《GPU计算｜CMPS 297S396AA - GPU Computing - Spring 2021》（豆包翻译 - P23：-23-Lecture 23 - Potpourri.zh_en - GPT中英字幕课程资源 - BV1bw4m1k7a1

Hello， everyone and welcome to lecture 23 of GPU computing Today will be our final lecture and unfortunately。

 because we have a limited time in the course， there is there was a limited set of topics that we could cover So there's plenty of other topics that we haven't covered a lot of patterns that we could have covered that we didn't covered and also some advanced features of GPUs or other kind of useful things that we didn't cover So what I will do today is I will just go through a potry of some of the remaining features that we haven't covered so that you guys are aware of it in case you you ever want to use features like that or in case you have a C code that's using these features so that you know what they are。

 but we're not going to go into any details about each of them so we're going just going to kind of go through a potry of remaining topics that we haven't covered and conclude with that Okay so this is a kind of list of topics that I'm going to briefly。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_1.png)

![](img/54013e81b522e1ea7638796f7d982f26_2.png)

![](img/54013e81b522e1ea7638796f7d982f26_3.png)

![](img/54013e81b522e1ea7638796f7d982f26_4.png)

![](img/54013e81b522e1ea7638796f7d982f26_5.png)

Touch on today and so well get started with we'll go through these in orders。

 we'll get started with multi GPU programming。

![](img/54013e81b522e1ea7638796f7d982f26_7.png)

So multi GPU programming， we can have multiple GPUs on the same note okay so so far the model that we've been dealing with is where we have a CPU and a GPU and then the CPU offers work to the GPU but in fact we can actually have a CPUU connected to multiple GPUs and if we have a CPUU connected to multiple GPUs。

 the CPU will need to somehow tell each GPU want to do and orchestrate the work across the GPUs。



![](img/54013e81b522e1ea7638796f7d982f26_9.png)

![](img/54013e81b522e1ea7638796f7d982f26_10.png)

So there is support for doing this inside of Kuda。 you can figure out how many GPUs you have on the node using something like KUa get device count。

 So this API call this API call tells you how many GPUs you have and then you can use Puda set device to select one of them so you can have different devices if you want to for example。

 launch a kernel on this on GPU 0， you can set a device to0 and then launch the kernel if you want to launch the kernel or call the kernel to launch a grid on GPU1。

 then you can do Kuda set device for GPU1 and then launch the grid on GPU1。



![](img/54013e81b522e1ea7638796f7d982f26_12.png)

![](img/54013e81b522e1ea7638796f7d982f26_13.png)

Now， typically when we use multiple GPUs and a single CPU。

 we also use multiple CPU threads and we have the CPU thread。

 each CPU thread being responsible for operating one of the GPUs or calling kernels or copies or whatever for one of the GPUs and for multithreading。

 we usually use something like Openmp or there is other multithing libraries that you could also use。

 so you can use multiple CPU threads of each CPU thread would select one of the GPs and operate one of the GPUs。

 and then you can also synchronize across the different GPUs using the CPU or as we'll see later。

 we can also use shared memory across the GPU。😊。

![](img/54013e81b522e1ea7638796f7d982f26_15.png)

![](img/54013e81b522e1ea7638796f7d982f26_16.png)

ok。😊，Now this is one way to synchronize one form of multi GPU programming is where we have multiple GPUs attached to one CPU。

 but we can also have multiple GPUs on multiple different nodes in a network so we can have multiple CPUs connected via a network。

 and then each of these CPUs could have multiple GPUs and in this case I would want to coordinate work not only across multiple GPs that are connected to a CPU。

 but I also have multiple GPUs connected to different CPUs on a network。



![](img/54013e81b522e1ea7638796f7d982f26_18.png)

![](img/54013e81b522e1ea7638796f7d982f26_19.png)

![](img/54013e81b522e1ea7638796f7d982f26_20.png)

![](img/54013e81b522e1ea7638796f7d982f26_21.png)

![](img/54013e81b522e1ea7638796f7d982f26_22.png)

![](img/54013e81b522e1ea7638796f7d982f26_23.png)

And in this case， we typically use something like MPI， which is the message Pass Interface library。

 or MPI allows us to be able to program multiple CPUs connected over a network and we can have an MPI we have something called a rank so an MPI rank is like different threads on the CPU but a rank would be running on different CPUUs and we can have each MPI rank we can also have multiple ranks on the same CPU。

 so each one of these would correspond to a process that's running on the same CPU and we can have each rank interacting with one of the GPUs。



![](img/54013e81b522e1ea7638796f7d982f26_25.png)

![](img/54013e81b522e1ea7638796f7d982f26_26.png)

![](img/54013e81b522e1ea7638796f7d982f26_27.png)

![](img/54013e81b522e1ea7638796f7d982f26_28.png)

![](img/54013e81b522e1ea7638796f7d982f26_29.png)

![](img/54013e81b522e1ea7638796f7d982f26_30.png)

Now， one important consideration when we do multi multi GPU programming on a network is that so when。

 when we're using。

![](img/54013e81b522e1ea7638796f7d982f26_32.png)

![](img/54013e81b522e1ea7638796f7d982f26_33.png)

When we're programminging multiple GPUs on a CPU， these GPUs。

 if I want to kind of share data across them， I can do it through the CPU memory or I can do it directly across the GPs depending on how my system is configured。

 but oftentimes I can copy data from one GPU to another GPU using the CPU and that's。



![](img/54013e81b522e1ea7638796f7d982f26_35.png)

![](img/54013e81b522e1ea7638796f7d982f26_36.png)

![](img/54013e81b522e1ea7638796f7d982f26_37.png)

![](img/54013e81b522e1ea7638796f7d982f26_38.png)

Fast relative to if I want to copy data across the network。

 so if I want to share data from a GPU on one side of the network and one CPU on the network and a GPU another CPU in the network what I would need to do is I would not I cannot just copy from one GPU directly to another GPU I would need to copy the data from the GP memory to the CPU memory then over the network to the other CPU memory and then over the network to the other GPU and and this takes a lot of time if you want to communicate across the GPU and attached to one CPU and a GP potential noise CPU going over the network takes a lot of time So one of the important considerations when we are paralyzing across multiple GPs is how to overlap the communication across the network with the computation on the GP。



![](img/54013e81b522e1ea7638796f7d982f26_40.png)

![](img/54013e81b522e1ea7638796f7d982f26_41.png)

![](img/54013e81b522e1ea7638796f7d982f26_42.png)

![](img/54013e81b522e1ea7638796f7d982f26_43.png)

![](img/54013e81b522e1ea7638796f7d982f26_44.png)

![](img/54013e81b522e1ea7638796f7d982f26_45.png)

![](img/54013e81b522e1ea7638796f7d982f26_46.png)

![](img/54013e81b522e1ea7638796f7d982f26_47.png)

And one example of this， for example is if we have some kind of stencil computation and we divide the space that we're doing the stencil computation on across multiple GPUs and each GPU does in a portion of the space well we have to share the halo elements across the different GPUus so one thing people usually do is they will compute the elements at the boundary and then while they're computing the internal elements they would do the communication of the boundary elements across the network so this is one example of how we can overlap the communication across the GPUs with the execution of kernels on the GP。



![](img/54013e81b522e1ea7638796f7d982f26_49.png)

![](img/54013e81b522e1ea7638796f7d982f26_50.png)

![](img/54013e81b522e1ea7638796f7d982f26_51.png)

![](img/54013e81b522e1ea7638796f7d982f26_52.png)

![](img/54013e81b522e1ea7638796f7d982f26_53.png)

Okay， so this just second at how we program multi multiple GPUs and some of the challenges that we face when we do that。



![](img/54013e81b522e1ea7638796f7d982f26_55.png)

![](img/54013e81b522e1ea7638796f7d982f26_56.png)

Another topic that we haven't really delved much into is interconnect。

 So when we have when we have a CPU that's connected to the multiple GPs。

 how are they connected Well they're connected via an interconnect and one common interconnect that is used is PCIe。

 So PCIe is a type of interconnect that's used in many systems to connect CPUs and GPs together。😊。



![](img/54013e81b522e1ea7638796f7d982f26_58.png)

![](img/54013e81b522e1ea7638796f7d982f26_59.png)

![](img/54013e81b522e1ea7638796f7d982f26_60.png)

![](img/54013e81b522e1ea7638796f7d982f26_61.png)

![](img/54013e81b522e1ea7638796f7d982f26_62.png)

And CPIE is a very kind of general kind of interconnect， we use it to connect CPUUs to GPUs。

 but we can also use it to connect CPUUs to other kinds of devices like FPGAs， for example。

 and because PCE PCIE is general， it's commonly used in many systems but there's also other kinds of interconnect like NVlink for example。

 and NVlink actually provides faster interconnect and we can use it to connect multiple GPUs together or we can use it to even to connect a GPU to some kinds of CUs that support the NVlink interconnect PCIE is very widely supported so most CPUUs would support PCIE。

 most GPUs would support PCIE， however something like NVlink。

 only some CUs support NVlink and only some GPUs particularly certain generations of Nvidia GPUs if have a later generations of NVD GPUs。



![](img/54013e81b522e1ea7638796f7d982f26_64.png)

![](img/54013e81b522e1ea7638796f7d982f26_65.png)

![](img/54013e81b522e1ea7638796f7d982f26_66.png)

![](img/54013e81b522e1ea7638796f7d982f26_67.png)

![](img/54013e81b522e1ea7638796f7d982f26_68.png)

![](img/54013e81b522e1ea7638796f7d982f26_69.png)

EnVi link so PCIE is the general one EnVlink is more specific to NviA GPUs and later generations of them and is always supported by some CPUs and give you faster and it's a faster interconnect so we can get higher bandwidth when we are copying data between GPUs or between CPUU and GPU howevers not it cannot be used for anything so if I want kind of something general that works for any CPU and GPU then PCIE is usually the general interconnected people use。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_71.png)

![](img/54013e81b522e1ea7638796f7d982f26_72.png)

![](img/54013e81b522e1ea7638796f7d982f26_73.png)

![](img/54013e81b522e1ea7638796f7d982f26_74.png)

Okay， any questions so far， multi GPU or interconnect？Okay。

 another topic is unified virtual addressing。 So what is unified virtual addressing， Well， so far。

 what we've been doing is we've had a CPU。

![](img/54013e81b522e1ea7638796f7d982f26_76.png)

![](img/54013e81b522e1ea7638796f7d982f26_77.png)

That had access to its main memory and we've had a GPU that had access to global its own global memory and we've been treating each of these as if it were its own address space so the main memory is an independent address space from the global memory on the GPU。

 So if I have a pointer that points to an address that pointer we've been assuming could point to you know that pointer value is going to be used here in main memory or it's going to be some global memory and this would be its own virtual address space and this would be its own virtual address space so the pointer would point to different things if I used it here or if I used it here。

 but in fact， what later GPU systems or invi GPU systems did is they have something called a unified virtual address space。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_79.png)

![](img/54013e81b522e1ea7638796f7d982f26_80.png)

![](img/54013e81b522e1ea7638796f7d982f26_81.png)

![](img/54013e81b522e1ea7638796f7d982f26_82.png)

![](img/54013e81b522e1ea7638796f7d982f26_83.png)

Where we have a single virtual address space， we still have two separate physical memories。

 the main memory of the CPU and the global memory of the GPU or the device memory of the GPU。

 we select separate physical address space， but we have a unified virtual address space where the same virtual so we have the same virtual address space that is used across the hosts and devices and what that means is that an address。

 a memory address that points inside of the range of addresses that's supported by the main memory of the CPUU is mutually exclusive from the range of addresseses that's supported by the GPU so the same memory address cannot be valid in both places it's either valid in the CPU or valid on the GPU。



![](img/54013e81b522e1ea7638796f7d982f26_85.png)

![](img/54013e81b522e1ea7638796f7d982f26_86.png)

![](img/54013e81b522e1ea7638796f7d982f26_87.png)

![](img/54013e81b522e1ea7638796f7d982f26_88.png)

Of course， even when we didn't have a unified virtual memory。

 it's probably not a good idea to use the same memory address here and here because if I allocated some memory on the GPU and it incidentally pointed to validate on the GPU。

 that doesn't mean I should be using that， okay。Using the memory however。

 because the only reason that a pointer would be valid in the other address space is if I accidentally had two things mapping to the same address location。

 but that's not even a concern in when we have unified virtual address spaces and the reason is that the address ranges are mutually exclusive now what's the advantage of having a pointer having a unified virtual address space across CPUUs and GPUs in other words。

 having the address ranges mutually exclusive that such that pointers I can't all use pointers across。

😊，Well， the advantage is that。When I know that the CPUU is going to use a separate virtual address range from the GPU。



![](img/54013e81b522e1ea7638796f7d982f26_90.png)

Then I know I can tell the where a pointer points to。

 whether it points to a CT memory or GP memory from the value of the pointer itself okay so the data location is known from the pointer value so if I have a pointer。

 I can look at the value of this pointer and I can say oh。



![](img/54013e81b522e1ea7638796f7d982f26_92.png)

![](img/54013e81b522e1ea7638796f7d982f26_93.png)

![](img/54013e81b522e1ea7638796f7d982f26_94.png)

This range of adveracsses is the CPU memory， this range of addressesdveracies is the GPU memory。

 so by simply looking at the value of the pointer I can tell if this pointer points to the CPU or the GP。



![](img/54013e81b522e1ea7638796f7d982f26_96.png)

![](img/54013e81b522e1ea7638796f7d982f26_97.png)

![](img/54013e81b522e1ea7638796f7d982f26_98.png)

And the advantage of that is that when I do QM copy， remember when we did QM copy。

 we had to specify whether we want to copy from host the device or we're copying from device to host or maybe there was device to device or host to host well with unified virtual addressing we actually with a unified virtual address space we don't need to tell the runtime system whether whether a pointer points to the device or points to the host because the runtime system can tell from the value of the pointer。

 whether the pointer points to the device or the host So if we are using unified virtual address space then when our Q ofM copies。

 we would not need to specify device to host or host the device。

 we can simply write QM copypy default and from the value of the pointer。



![](img/54013e81b522e1ea7638796f7d982f26_100.png)

![](img/54013e81b522e1ea7638796f7d982f26_101.png)

![](img/54013e81b522e1ea7638796f7d982f26_102.png)

![](img/54013e81b522e1ea7638796f7d982f26_103.png)

![](img/54013e81b522e1ea7638796f7d982f26_104.png)

![](img/54013e81b522e1ea7638796f7d982f26_105.png)

![](img/54013e81b522e1ea7638796f7d982f26_106.png)

The runtime can figure out whether this points or points to the device or the phone。



![](img/54013e81b522e1ea7638796f7d982f26_108.png)

So this is the advantage of having a unified。

![](img/54013e81b522e1ea7638796f7d982f26_110.png)

Puol address space across GPU and GPU， where the main memory of the CPUU uses a certain address range and the virtual address space and then the GPU。

 the device memory and the GPU uses a separate address range in the virtual address。



![](img/54013e81b522e1ea7638796f7d982f26_112.png)

![](img/54013e81b522e1ea7638796f7d982f26_113.png)

ok。😊，Is it clear to everyone any questions？Now there's another advantage of unified virtual addressing。

 which I will show you， I will also show you， but let me first introduce another topic which is liberal copy memory。



![](img/54013e81b522e1ea7638796f7d982f26_115.png)

![](img/54013e81b522e1ea7638796f7d982f26_116.png)

So what is zero copy memory， zero copy memory enables to have threads running on the GPP use。

 the device threads directly access the host memory。



![](img/54013e81b522e1ea7638796f7d982f26_118.png)

![](img/54013e81b522e1ea7638796f7d982f26_119.png)

Okay， what does that mean I have before so far， we've been saying that threads on the GPU cannot access data that that's in the main number of the C P。

 I have to copy the data from the CPU to the GP。

![](img/54013e81b522e1ea7638796f7d982f26_121.png)

Well， it turns out that we can use something called zero copy memory。

 And what that does is that here，0 copy refers to the fact that we don't have to do any K and end copies。

 Instead， what we can do is we can have。A thread that is running on the GP。Access data directly。

 access data that is in the CPU memory。What happens when we do something like that is that when a thread running on the GPU。

Tries to access a memory address range， a memory address that points to data that is on the CPU。

 the runtime system on demand will copy that data from the CPU memory to the GP memory and serve it to that thread。

So rather than us having to do a co and copy explicitly， we can just。

Alllocate the data then and then of course there's a special way to do it。

 we can just use the regular P mal， but we can the idea is that we can allocate the data and then not copy it。

 but instead have the CPU thread once it accesses that data。

 the runtime system will copy that data from the CPU to the GP on demand。



![](img/54013e81b522e1ea7638796f7d982f26_123.png)

![](img/54013e81b522e1ea7638796f7d982f26_124.png)

Okay， now an important thing here is that if if the CPU thread is going to access data。

 that is going to access data that is on sorry if if a GP thread is going to access data that is in the CPU memory。

And that data is going to be copied on demand。That means I'm going to be using a DMA to copy that data right so what does that tell me about the data that's in the CPU memory that I'm accessing。

 where does it have to be？Inpend the memory。And pin memory exactly so the memory for zero copy memory to work the data that I want to be able to access from the GP the data that I want to be able to access from a GPU thread in the CPU memory should be allocated penned memory。



![](img/54013e81b522e1ea7638796f7d982f26_126.png)

Okay， and the way we do that is using an API call that is Ka Ho hour。



![](img/54013e81b522e1ea7638796f7d982f26_128.png)

Okay， kuda host A， so this command kuda host Alloc， when we use it to allocate memory。

 what happens is that it gives us a certain memory range in the GPU that in the CPUU that is pinned and not only is it pinned。

 but also if I try to access this data from the GPU。

 the runtime system will automatically copy this data for me from the CPUU to the GPU。



![](img/54013e81b522e1ea7638796f7d982f26_130.png)

![](img/54013e81b522e1ea7638796f7d982f26_131.png)

![](img/54013e81b522e1ea7638796f7d982f26_132.png)

Now， without unified virtual memory， what we need to do is we need to get the data that we want to access in in the CPU memory。

 we need to have it also map to the address space of the GPU。

So what we can do is we can use a command called Kudahost Gett device pointer that takes a pointer that was allocated using Kahost Allc that points to a pinned memory on the CPUU and gets a corresponding pointer on the GPU that the GPU can use to access this data。



![](img/54013e81b522e1ea7638796f7d982f26_134.png)

![](img/54013e81b522e1ea7638796f7d982f26_135.png)

![](img/54013e81b522e1ea7638796f7d982f26_136.png)

![](img/54013e81b522e1ea7638796f7d982f26_137.png)

However， this over here is unnecessary if we our system supports unified virtual address。



![](img/54013e81b522e1ea7638796f7d982f26_139.png)

So if I have unified virtual addressing， that means the pointers on the CPU and the GP are mutually exclusive。



![](img/54013e81b522e1ea7638796f7d982f26_141.png)

Okay so the pointer that I get from KudDa hostst ac。

 I can simply give that to the GPU and when the GPU dereferences this pointer the GPU knows from the value of the pointer that this memory is actually in the CPUU。

 not in the GPU， so it knows that it has to go to the CPU and fetch that data on demand however。

 if I did not support unified virtual addressing， then the GPU would not be able to know from the value of the pointer。

 whether this to CPUU memory or GPU memory， so this is why we would need to use something like Kuda host Kuda hosts get device pointer to translate the pointer that points the CPU memory into something into a pointer that's usable on the GPU that the GPU can use to figure out that it has to go to the CPUU to get that memory。



![](img/54013e81b522e1ea7638796f7d982f26_143.png)

![](img/54013e81b522e1ea7638796f7d982f26_144.png)

![](img/54013e81b522e1ea7638796f7d982f26_145.png)

![](img/54013e81b522e1ea7638796f7d982f26_146.png)

![](img/54013e81b522e1ea7638796f7d982f26_147.png)

![](img/54013e81b522e1ea7638796f7d982f26_148.png)

ok。😊，Is this clear any questions about zero copy memory？A professor。Yeah。

 would this give us some kind of like automatic pipelining of some sort or not really？



![](img/54013e81b522e1ea7638796f7d982f26_150.png)

So the。

![](img/54013e81b522e1ea7638796f7d982f26_152.png)

The combination of zero copy memory andified virtual address unified virtual addresses。

 the combination of these two things enables you， it gives you the feeling that the CPU and the GPU are accessing the same memory location。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_154.png)

![](img/54013e81b522e1ea7638796f7d982f26_155.png)

![](img/54013e81b522e1ea7638796f7d982f26_156.png)

Right， you don't have to。 You don't have to worry about copying back and forth。Now。

 your point is very is a very good point。 Does this give us automatic pipeing。 And it kind of does。

 because what happens is since I'm not copying and the copying happens on demand。

 Then what happens is when， when some threads get scheduled on the GP and they start accessing the CPU memory。

 what's gonna happen is that that CPU memory is gonna get copied， when those threads execute。

 when those threads are requested。 So here， because you have this。



![](img/54013e81b522e1ea7638796f7d982f26_158.png)

![](img/54013e81b522e1ea7638796f7d982f26_159.png)

![](img/54013e81b522e1ea7638796f7d982f26_160.png)

This kernel that's running and this memory is being copied on demand some threads they will make a request that request will be served and as soon as that request that data is copied from GPU from the CPUU to the GPU those threads can start executing without waiting for all the other threads data to get served and then the other threads will then later on come and make request and their data will start getting served so and what that means is that we're not no longer waiting for all the copy to happen all the input to get copied before any of the threads start working the copying the copies will happen on demand when the threads request。



![](img/54013e81b522e1ea7638796f7d982f26_162.png)

![](img/54013e81b522e1ea7638796f7d982f26_163.png)

![](img/54013e81b522e1ea7638796f7d982f26_164.png)

![](img/54013e81b522e1ea7638796f7d982f26_165.png)

So the threads that request them earlier， the data will be copied earlier and then the threads that come and request later。

 their data will be copied later while the earlier threads are doing their computation So yes。

 you are right and that this gives us the feeling this somehow does some of the pipelineing for us now whether。



![](img/54013e81b522e1ea7638796f7d982f26_167.png)

![](img/54013e81b522e1ea7638796f7d982f26_168.png)

This will be as efficient as as doing the pipelineing yourself where you're you have more control over what's getting overlap with what。

 That's something that you would need to try and see whether you can。



![](img/54013e81b522e1ea7638796f7d982f26_170.png)

![](img/54013e81b522e1ea7638796f7d982f26_171.png)

![](img/54013e81b522e1ea7638796f7d982f26_172.png)

You can whether using zero copy number and unified virtual addressing will give you as much of a benefit as doing something like doing the manual pipelining yourself。

 but it is a very good observation that we do get some kind of pipelining when we use zero copy member and unified virtual address。

Okay， thank you。Yeah， it was。Profesor。Yes。😊，When we we use zero copy memory。

 do we get better performance than if we had copied everything ourselves to the GPU。

 like are we guaranteed almost an improvement？So it really depends。

 it really depends on the situation。Right， is if you have a。

 if you have a case where you have this huge data set and you're you're only going to use。

A small portion of this data set， but you don't really know ahead of time which portion of the data set you're going to use that's going to depend on some runtime information。



![](img/54013e81b522e1ea7638796f7d982f26_174.png)

So in this case， using zero copy memory is useful because you're going to be copying at runtime。

 so you end up copying only the data that you actually need as opposed to having to copy everything and then only use some。



![](img/54013e81b522e1ea7638796f7d982f26_176.png)

Also you get this automatic pipeing that somebody else pointed love where you have this automatic pipeline that's taking place and you get more overlap between computation and copying by using them。

However， you have the trade off in that when， when you use Put and copy。

Right you're doing the copy in bulk， so there's some overhead that the system can amortize across the copy when you're doing this copy in bulk。

😡，whereasas having to do the copy， know， in pieces and pieces at a time。

 maybe each of those individual pieces will be faster。

 but there's going to be kind of a price that you're going to pay every time you need to copy a piece。

Okay， so you have less amortization of that pick。So it really depends on the situation。

 whether you know， doing the copy in bulk and then computing is faster or doing the copy on demand as best。



![](img/54013e81b522e1ea7638796f7d982f26_178.png)

Okay and that relates to how many portions of your data what percentage of your data set do you need or youre going to be using all of it or you're going to be using only a small part of it。

 but you don't know ahead of time and also how important is overlapping copying with computing。I see。

 So for something like matrix multi matrix matrix multiplication， it's hard to say from the start。

 whether the bulk copying compensates for the。

![](img/54013e81b522e1ea7638796f7d982f26_180.png)

Like。For having to copy into the GPU in the first place， right？Right， so for matrix multiplication。

 the coman copy takes a very small fraction of time compared to the actual computation。😊。



![](img/54013e81b522e1ea7638796f7d982f26_182.png)

RightBecause the data you copy is uns squared but the computation is un cubeed， however。

 if youre going if you're going to use zero copy memory it means you're going to incur this copy every time you want to access this matrix or maybe it gets cached。

 however， it's hard to reason about you would need to try it out。

 but it's hard reason about whether you would actually get benefit from using zero copy of memory there just because the copy doesn't really take much time compared to the actual computation。

I see。 Okay。 thank you。Yeah， you're welcome。 So One benefit， though。

 from doing this is that it makes the host code much easier， right。

 You don't have to worry about doing all these food in them copies back and forth。 You just。

Alllocate data on the CPUU then you go use it on the GPU and you come back and use it on the CPU then you go back and use it on the GPU and the system is taking care of doing the copies back and forth for you whenever you need to So in terms of the ease of programming it makes your application much simpler if you use unified virtual memory and in practice unified virtual memory or unified virtual address and zero copy memory used is used very widely and a lot of times people consider that if it was going to have a performance penalty that performance penalty would be small enough that the benefit you get from making your code simpler is worth it so this is actually used very commonly the reason we don't teach it to you at the beginning of this semester is because we want you to be aware of what's going on underneath we want you to be aware of the low-level details and that's why we teach。



![](img/54013e81b522e1ea7638796f7d982f26_184.png)

![](img/54013e81b522e1ea7638796f7d982f26_185.png)

![](img/54013e81b522e1ea7638796f7d982f26_186.png)

Youlude themM copy in the course however， in realel applications。

 unified virtual address and zero copy memory together are used very frequently for people to simplify their code and also in some cases maybe even get good perfect。

Okay。😊，We。Okay， thank you。你我。

![](img/54013e81b522e1ea7638796f7d982f26_188.png)

Okay another topic is events so so far in all the code that we've been writing。

 we've been synchronizing after every copy and kernel called in order for us to collect timing information and I've been doing this just to keep the code simple because I didn't want to introduce the events from the very beginning because I would have had to introduce streams at the very beginning and I didn't want you guys to worry about streams from the very beginning。

 So we've been we've been synchronizing after every copy and or kernel call in order for us to collect the timing information but in practice this this approach interferes with the execution and closed close things down。

 I really don't want to synchronize across across you know every time I have。😊。



![](img/54013e81b522e1ea7638796f7d982f26_190.png)

![](img/54013e81b522e1ea7638796f7d982f26_191.png)

![](img/54013e81b522e1ea7638796f7d982f26_192.png)

![](img/54013e81b522e1ea7638796f7d982f26_193.png)

![](img/54013e81b522e1ea7638796f7d982f26_194.png)

![](img/54013e81b522e1ea7638796f7d982f26_195.png)

![](img/54013e81b522e1ea7638796f7d982f26_196.png)

Every every time I do a copy or a kernel call， especially if I'm using multiple streams and these kernels are supposed to be executed in parallel with each other or the copies are supposed to be executed in parallel with each other so the way that we can collect timing information without having to do a something like akua device synchronize is using events and events can be used to collect timing information without synchronizing by simply you know you know adding the events to streams in order for us to collect timestamps whenever something in that stream starts or finish it so the way we can use events like this we can write couda event create for example。

 to create an event we can write coa event record to record an event and we provide the stream we want to record into okay so here we can。



![](img/54013e81b522e1ea7638796f7d982f26_198.png)

![](img/54013e81b522e1ea7638796f7d982f26_199.png)

If we add an event to a stream， what we do is the event will simply capture the time when it the events turn in the stream。

 and then we can do something like Ka events synchronize。 So wait for some event to happen。

 So if I have multiple things inside of if I put multiple things in a stream。

 And then I put an event。 And then I put multiple things after the event。 But I and then later on。

 I want to wait for the event to finish。 But I don't care about waiting for the things after the event to finish。

 I can do something like kuda event synchronize， which waits for a particular particular event in the stream to to finish without waiting for the things that are after the。

And and this is better than just could device synchronize。

 which basically wait for everything that passed to finish。

 So maybe I want to wait for certain things in the past to finish without other things in the past to finish。

 and I can use events to do that rather than having to wait for every。

We can also get the elase time between events so we can reduce coa event elaps time to get the time in between two events so for example。

 if I want to get the time between if I want to take time how long it takes to do a certain kluomm copy but I don't want to synchronize after that coudm copy it could be an asynchronous com copy and I don't want to synchronize the time it I just want to take time how long it takes without having to synchronize before it or after it what I could do is I could record an event before the before the com copy and record an event after the com copy and then get the eappsse time between these two events and this tells me how long that com copy took without me having to synchronize it and interfere with the asynchronous behavior that I'm trying to。



![](img/54013e81b522e1ea7638796f7d982f26_201.png)

![](img/54013e81b522e1ea7638796f7d982f26_202.png)

![](img/54013e81b522e1ea7638796f7d982f26_203.png)

And of course， I can use Kuta event destroy to destroy an event that I previously created。Now。

 a lot of this， we can also， a lot of this information we can also collect in the profilers。

 So the profiler also tells us how long kernels take to run or how long。



![](img/54013e81b522e1ea7638796f7d982f26_205.png)

Mm copies take to run。 so this information it can be collected use in the profiler。

 But if for whatever reason， I would also like to collect this information in the code itself。

 maybe I want to use it to make some kind of decision in the code。 I could use events。



![](img/54013e81b522e1ea7638796f7d982f26_207.png)

![](img/54013e81b522e1ea7638796f7d982f26_208.png)

诶。😊，Is it clear any questions about events， do guys see where they're useful？



![](img/54013e81b522e1ea7638796f7d982f26_210.png)

Okay， another topic is tensor cores。 so tensor cores were introduced with the volt of U 100 architecture and tensor cores are basically programmable matrix multiply and accumulate units inside of our Ss。

 So each SM has tensor cores that can be used to do a small matrix。

 multiply and accumulate operation in one instruction。 And the reason tensor cores are so important。

 Tensor cores were especially important when。😊。

![](img/54013e81b522e1ea7638796f7d982f26_212.png)

![](img/54013e81b522e1ea7638796f7d982f26_213.png)

![](img/54013e81b522e1ea7638796f7d982f26_214.png)

![](img/54013e81b522e1ea7638796f7d982f26_215.png)

When deep learning took off， it was very important for accelerating deep neural network workloads。

 And the reason is that a lot of these deep learning workloads are just doing matrix multiplication。

Okay， and you know we've saw much how good GPUs are at performing matrix matrix multiplication。

 but in fact， we can do even better by using Tensor course。

 which are the specialized hardware that does you know a matrix matrix。

 a small matrix multi and accumulate in one instruction rather than having to execute multiple load and multiple add and multiply instruction to do the operation。



![](img/54013e81b522e1ea7638796f7d982f26_217.png)

![](img/54013e81b522e1ea7638796f7d982f26_218.png)

![](img/54013e81b522e1ea7638796f7d982f26_219.png)

So the tensor cores give us a lot of speedup when we use matrix multiplication。

 but we have to use them explicitly using a certain API so in the Volta U100 architecture we have 640 tensor cores since we have 8SMs there's actually eight tensor cores per SM and each one of these eight tensor cores is capable of doing a four by four matrix multiplied so it can do a D equals a times B plus d operation。



![](img/54013e81b522e1ea7638796f7d982f26_221.png)

![](img/54013e81b522e1ea7638796f7d982f26_222.png)

ok。😊，Here， D A B， P are all4 by form。Any questions about this？Okay。😊。



![](img/54013e81b522e1ea7638796f7d982f26_224.png)

The next topic we didn't get a chance to talk about is libraries。

 so there's many libraries that are part of KUuda or that are popularly used with KUuda that have common parallel primitive。

A lot of the primitives that we actually use in the course are provided in libraries。 So。

 for example， there's a library called Thr。That contains primitives like reductions， scan， filter。

 and stored。Okay a lot of we implemented a lot of these manually in the course。

 and that was an important exercise because we wanted to teach you how how these different primitives work。

 where they're performant， where they're not a performant and just the principles that go behind optimizing them。

 but in practice， if you are writing an application。

 you probably wouldn't write a reduction or a scan or a sort operation your self manually as part of your application。

 you can just call a library like thrust or there's also a cub which which thrust uses the cu is another one。

You can call one of these libraries like thrust or Cb and and they would they would just do the reduction or the scan or the sort or the filter operation for you you wouldn't have to do it manually yourself so a lot of times some of the primitives that we're implementing in the course you wouldn't have to worry about implementing them yourself and in a full-fledged application you would just call some of these libraries to do it for you but you know the course wasn't about teaching you libraries it was about teaching you concepts behind reasoning about how to paralyse code and that's why we went and we implemented these ourselves。

ok。😊，Another one is CU BS， so CUBLS is used for basic dense linear algebra like vector addition matrix vector multiplication。

 matrix matrix multiplication， a lot of these operations again。

 we implemented matrix matrix multiplication in class and the purpose of that was to teach you about some of the some of the decisions and the challenges that go into paralyzing something like that。

 but in practice if you're using matrix matrix multiplication or matrix vector multiplication in your application。

 you would probably not implemented from scratch you would probably use a library like2BLs that already has a lot of very highly optimized implementations of these basic dense linear your algebra root。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_226.png)

![](img/54013e81b522e1ea7638796f7d982f26_227.png)

![](img/54013e81b522e1ea7638796f7d982f26_228.png)

![](img/54013e81b522e1ea7638796f7d982f26_229.png)

![](img/54013e81b522e1ea7638796f7d982f26_230.png)

![](img/54013e81b522e1ea7638796f7d982f26_231.png)

![](img/54013e81b522e1ea7638796f7d982f26_232.png)

![](img/54013e81b522e1ea7638796f7d982f26_233.png)

![](img/54013e81b522e1ea7638796f7d982f26_234.png)

There's also NVBLAS， which is a multi GPU library that can do these pencilline algebra operations on multiple GPUs。

 and this is implemented on top up。

![](img/54013e81b522e1ea7638796f7d982f26_236.png)

Another one is to use sparse to see if sparse does sparse does linear algebra so again we looked at very in the course we looked at how to do SPnB and we looked at different sparse matrix storage formats and it turns out that we actually have a library that does all kinds of sparse and linear algebra routines for us so in practice if you have an application that has sparse matrix operations that you need to perform you could just use these built and functions to create these matrices and to operate on them instead of implementing them yourself from scratch but again the reason we taught to you about them is so that you can appreciate the kind of the kind of kind of process that you need to go through when you're optimizing these kinds of workloads and these principles are also useful in other kinds of workloads that that you would want to paralyze that may not necessarily。



![](img/54013e81b522e1ea7638796f7d982f26_238.png)

![](img/54013e81b522e1ea7638796f7d982f26_239.png)

![](img/54013e81b522e1ea7638796f7d982f26_240.png)

![](img/54013e81b522e1ea7638796f7d982f26_241.png)

Involved forly。Another one is CU solver， so CU solver is useful for factorization and solve routine if're doing matrix factorization and CU solver is actually built on top of COU BLs and CO sparse another one is COUDNN and COUDNN is popular in deep is used in deep neural networks it implements a lot of routines that are useful for deep neural networks and as a matter of fact a lot of the frameworks that some of you are probably familiar with if if you've worked with deep learning before so a lot of these frameworks like CAfe MXnet Tenorflow plytorch these frameworks a lot of them give you the option of running on the GPU。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_243.png)

![](img/54013e81b522e1ea7638796f7d982f26_244.png)

![](img/54013e81b522e1ea7638796f7d982f26_245.png)

![](img/54013e81b522e1ea7638796f7d982f26_246.png)

![](img/54013e81b522e1ea7638796f7d982f26_247.png)

![](img/54013e81b522e1ea7638796f7d982f26_248.png)

![](img/54013e81b522e1ea7638796f7d982f26_249.png)

![](img/54013e81b522e1ea7638796f7d982f26_250.png)

And the way that these frameworks are able to take your models and run them on the GPU is that underneath what they do is they call CDNN。

 So a lot of these frameworks for deep learning that are popular and that they use GPU to make your different networks much faster。

 they simply use CDNN to。

![](img/54013e81b522e1ea7638796f7d982f26_252.png)

To accelerate your code CDNN is actually a very popular library used indirectly by these framework and CDNN itself also uses something like C blue。



![](img/54013e81b522e1ea7638796f7d982f26_254.png)

![](img/54013e81b522e1ea7638796f7d982f26_255.png)

because the Ds themselves do all kinds of density or algebra and other operations。停。😊。

Another one is NV graph NV graph is useful for graph processing it gives you different representations of graphs and operations you can do on graphs there's CUFFT for the Fast Fourier transform if you're interested interested in doing any operations that involve FFTs and there's also NPP so NPP is useful for all kinds of signal image and video processing。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_257.png)

![](img/54013e81b522e1ea7638796f7d982f26_258.png)

![](img/54013e81b522e1ea7638796f7d982f26_259.png)

So all of these libraries are very useful and very widely used and whenever you're writing GPU applications。

 a lot of the parallel letters that we covered in this course are actually implemented within these libraries。

 So a lot of times you would not need to implement these parallel patterns from scratch。

 you would be able to just use these libraries to do these operations for you and building an application involves composing together a lot of the functions that you can find in these different libraries。

 But again， the reason we went through all these parallel patterns is。😊。



![](img/54013e81b522e1ea7638796f7d982f26_261.png)

![](img/54013e81b522e1ea7638796f7d982f26_262.png)

![](img/54013e81b522e1ea7638796f7d982f26_263.png)

![](img/54013e81b522e1ea7638796f7d982f26_264.png)

![](img/54013e81b522e1ea7638796f7d982f26_265.png)

So that you guys can learn about what are the challenges that we face and world the optimizations that we can apply when optimizing GPU code in general。

 and these principles that you learn are also useful for you if you want to implement some other custom application that is not necessarily built into any of these libraries。



![](img/54013e81b522e1ea7638796f7d982f26_267.png)

ok。😊，Any questions about these libraries。

![](img/54013e81b522e1ea7638796f7d982f26_269.png)

Okay， the next topic is about other programming interfaces。 So in the course。

 we've been focusing on Kuda。 However， Kuda is not the only interface for programming GPus。

 There are other programming interfaces out there as well。 One of them is open C。

 Open C is similar to Kuda， however， it is open sourced and also it's more portable across non Nvidia GPUus。

 So if youre there are other hardware vendors out there， there are other GPUs besides Nvidia GPUus。

 I will talk about those on the next slide。 However。

 if you're interested in targeting GPus that are if you're interested having one the same code to be able to run on Nvidia GPUs as well as noninvidia GPUus。

 Open C presents a more portable portable。😊。

![](img/54013e81b522e1ea7638796f7d982f26_271.png)

![](img/54013e81b522e1ea7638796f7d982f26_272.png)

![](img/54013e81b522e1ea7638796f7d982f26_273.png)

![](img/54013e81b522e1ea7638796f7d982f26_274.png)

![](img/54013e81b522e1ea7638796f7d982f26_275.png)

![](img/54013e81b522e1ea7638796f7d982f26_276.png)

![](img/54013e81b522e1ea7638796f7d982f26_277.png)

![](img/54013e81b522e1ea7638796f7d982f26_278.png)

Programming interface， whereas Kuda is very specific to Nvidia GPus。 In fact。

 open C code is not just portable across different GPus。 It's also portable across different devices。

 So they're actually compilers out there that compile open C to CPUus and there's also compile high level synthesis tools that compile open C to FGs。

 So if you're interested if you're interested if you're only interested in running on Nvidia GPus。

 maybea Kuda gives you is a little simpler than open C。

 So if you're interested in just running onvi GPus， maybe kuda is enough。

 But if you want your code to be portable across different kinds of GPus and also you want to also be portable across GP and other hardware like FGs and Cus。

 then open C is a popular interface programming interface to use。😊。



![](img/54013e81b522e1ea7638796f7d982f26_280.png)

![](img/54013e81b522e1ea7638796f7d982f26_281.png)

![](img/54013e81b522e1ea7638796f7d982f26_282.png)

![](img/54013e81b522e1ea7638796f7d982f26_283.png)

![](img/54013e81b522e1ea7638796f7d982f26_284.png)

![](img/54013e81b522e1ea7638796f7d982f26_285.png)

![](img/54013e81b522e1ea7638796f7d982f26_286.png)

![](img/54013e81b522e1ea7638796f7d982f26_287.png)

Okay another interface is open ACC and openacCC is a directivebased GPU programming interface so here directive my directivebased I mean something similar to openM where you just take your regular sequential code that has a bunch of loops and you can annotate these loops in a certain way similar to the way you annotate them for paralyzing and on is using OpenM and by simply annotating your loops in the right way using openAC the open AC compiler takes care of automatically taking your sequential code and paralyzing it to run on the GPU of course assuming that the loops you're annotating are paralyzable in everything。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_289.png)

![](img/54013e81b522e1ea7638796f7d982f26_290.png)

![](img/54013e81b522e1ea7638796f7d982f26_291.png)

![](img/54013e81b522e1ea7638796f7d982f26_292.png)

ok。😊，So directivebased programming is very popular in parallel programming， it's popular on CPUs。

 people use OpenM all the time to paralyze work on CPUUs rather than using lower level threading libraries like PTs and then similarly。

 if you don't want to have to worry about allocating memory and calling it kernel and dividing the work across the box and all these things。

 you can use open ACC to annotate loops in your sequential code in order for you to a paralyzed to have that code automatically ported to run on the G。



![](img/54013e81b522e1ea7638796f7d982f26_294.png)

![](img/54013e81b522e1ea7638796f7d982f26_295.png)

![](img/54013e81b522e1ea7638796f7d982f26_296.png)

![](img/54013e81b522e1ea7638796f7d982f26_297.png)

ok。😊。

![](img/54013e81b522e1ea7638796f7d982f26_299.png)

Another library， yet another library is D++ Amp and C++ Amp is a library where you can use that you can use to implement GPU programs inside of C++ so you can in your side of C++ code。

 you can use Lambda functions and things like that and certain specialist syntax in order for you to implement code that would run on the GPU directly in D++ without having all these KUD extension。



![](img/54013e81b522e1ea7638796f7d982f26_301.png)

![](img/54013e81b522e1ea7638796f7d982f26_302.png)

Okay， so that's any questions about programming interfaces？



![](img/54013e81b522e1ea7638796f7d982f26_304.png)

Okay， the next topic is other GPU hardware， so in the course。

 we've been focusing on Kuda and we've also been focusing on discrete NviDdia GPUs NviDdia GPs meaning the GPUs that are manufactured by NviIDdia which is a popular GP manufacturing company and by discrete what I mean is GPUs that are not kind of integrated with the CPU on the same chip you have a GP that is a chip that is separate from the CPU that's what I mean by discrete。



![](img/54013e81b522e1ea7638796f7d982f26_306.png)

![](img/54013e81b522e1ea7638796f7d982f26_307.png)

![](img/54013e81b522e1ea7638796f7d982f26_308.png)

The GPU is its own independent chip， but in fact， we have other GPU hardware beside NviIDdia GPUs。

 AMD manufacturers GPUs， if you might be familiar with radian GPUs。

 these are manufactured by AMD and these are also very popular for Nvi GPUs are popular for gaming and they're popular also for for high performance computing and AMD GPUs are also popular for gaming and they're also popular for high performance。



![](img/54013e81b522e1ea7638796f7d982f26_310.png)

![](img/54013e81b522e1ea7638796f7d982f26_311.png)

![](img/54013e81b522e1ea7638796f7d982f26_312.png)

Arm manufacturers GPUs， you might have heard of Mali GPUs and arm， some of these GPUs are used。

 you know arm is very popular in mobile devices， so some of these GPUs and mobile devices will are manufactured by well theyre GPUs。

 sorry I shouldn't say the manufacture by arm there's many different companies that manufacture arm processors。

 but the GPUs use are kind of follow the arm architect。



![](img/54013e81b522e1ea7638796f7d982f26_314.png)

![](img/54013e81b522e1ea7638796f7d982f26_315.png)

And then also， there is Intel GPU。 So Intel actually manufactures GPUs as well。

Even though Intel is very known for CPUUs， but Intel also manufactures its own GPUs。

 a lot of these actually come integrated within your machine。

 so you probably if you have an Intel processor， you probably also have an Intel GPU in your system that's used for controlling some of the graphics on your screen。



![](img/54013e81b522e1ea7638796f7d982f26_317.png)

![](img/54013e81b522e1ea7638796f7d982f26_318.png)

Besides beside other GPU hardware， like I said， we've been focusing on discrete GPUs。

 but they are actually integrated GPUs where you can have CPUU and GPU on the same chip and in this case the CPUU on the GPU would share the same physical memory and the advantage of this is that we don't have any data transfer over PPIE you actually can share you can access the same physical memory from both the CPUU and the GPU because they are on the same chip。



![](img/54013e81b522e1ea7638796f7d982f26_320.png)

![](img/54013e81b522e1ea7638796f7d982f26_321.png)

![](img/54013e81b522e1ea7638796f7d982f26_322.png)

![](img/54013e81b522e1ea7638796f7d982f26_323.png)

![](img/54013e81b522e1ea7638796f7d982f26_324.png)

Okay， and arm arm， I mean， sorry， AMD is kind of one of the pioneers in manufacturing design。ok。😊。

Any questions about this？Okay， and then the last thing I would like to mention is a disclaimer about all all the comparisons I've been doing with CPU throughout the course so so far in the course what I've been doing is we've been comparing GPU with CPUU but we've been using a single threaded nonveized CPU code and what this does is it exaggerates the GPU speed up that've we've been。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_326.png)

![](img/54013e81b522e1ea7638796f7d982f26_327.png)

![](img/54013e81b522e1ea7638796f7d982f26_328.png)

We've been seeing and you know for the purpose of this course， maybe that's okay。

 but in general this practice is frowned upon if you're publishing a paper， for example。

 on where you're reporting your speedup between CPU and GP if you we really want to do a fair comparison than between GPUs and CPUUs。

 it would be more fair to compare our GPU implementation to a parallel CPUU implementation that uses vectorized CPUU code because it's just like a GPU can run many thread blocks and parallel。



![](img/54013e81b522e1ea7638796f7d982f26_330.png)

![](img/54013e81b522e1ea7638796f7d982f26_331.png)

![](img/54013e81b522e1ea7638796f7d982f26_332.png)

![](img/54013e81b522e1ea7638796f7d982f26_333.png)

or many warps in parallel a CPUU can run many threads in parallel and also a every CPU core for many CPUs every CPU core has a vector unit where we can vectorize the CPU code rather than just having having kind of a single thread running on the core so we did not do this in the course and the reason we not do this in the course is because the objective of the course is not to focus on CPU parallellyization it's to focus on GPU parallellyzization so I didn't want to trouble you with parallel computing on the CPU as well this is something that you can cover in another course。

 perhaps you've taken a course on this before this course or you might take a course on after this course however。

 I want to say this because I just wanted to take the comparisons that we've been doing with CPU with a grain of salt because in fact just like we've been paralyzing and vectorizing on the G。



![](img/54013e81b522e1ea7638796f7d982f26_335.png)

![](img/54013e81b522e1ea7638796f7d982f26_336.png)

![](img/54013e81b522e1ea7638796f7d982f26_337.png)

![](img/54013e81b522e1ea7638796f7d982f26_338.png)

![](img/54013e81b522e1ea7638796f7d982f26_339.png)

![](img/54013e81b522e1ea7638796f7d982f26_340.png)

![](img/54013e81b522e1ea7638796f7d982f26_341.png)

We can also do the same on the CPU， so a more fair comparison which CPUU would have been to compare to parallel CPU code that uses vectorization。

Okay。😊，So with that said， I've reached the end of the course。

 I'm sorry that I had to rush through all these topics today and we didn't get the chance to look at them with more depth。

 but unfortunately this is the number of lectures that we have in the course and we've run out on time so does anybody have any final questions before we conclude？

😊。

![](img/54013e81b522e1ea7638796f7d982f26_343.png)

![](img/54013e81b522e1ea7638796f7d982f26_344.png)

![](img/54013e81b522e1ea7638796f7d982f26_345.png)

Okay， well， there are no final questions then thank you guys for attending and it was a pleasure having guys in this course and I look forward to seeing you in other courses or perhaps other research projects。

😊。

![](img/54013e81b522e1ea7638796f7d982f26_347.png)

![](img/54013e81b522e1ea7638796f7d982f26_348.png)

Viron。

![](img/54013e81b522e1ea7638796f7d982f26_350.png)