# 2025LLVM欧洲开发者大会-p55-P55-LLVM_ENABLE_RUNTIMES=flang-rt--BV1EoE9zUEbG_p55-

![](img/9ad5d6c7edc4e953486b0f7c60db432c_0.png)

So my talk is about my experience on making the fl one time compilable or buildable as as a one time。

 So it in the title， My first thing is about what's actually the difference between L enable projects and L enable one times。

 So if you use enable everyone has probably here used that already L projects uses the compiler that CMake shows。

 that could be， for instance， Gcc by default， in a lot of cases and is building then usually for the host architecture but you could alter theoretical cross compiler compiler itself。

 on contrast to that L enable one times is using the Kang built previously in the L enabled projects。

One to build the one time itself and that's then meant to build one times which is used by compiled code that a compiled clang itself。

 which is not necessarily also the same platform where Kang is compiled from but you could have a one time for cross compilation from X86 to A 64 for instance。

 So how does it work if you have L enabled projects is used just standard CMake facilities like recurs into the projects with at subdirecty if you use L enabled one time。

 it does something different it just does some some artificial targets studio targets and for each of these targets it does this L external project at which internally one CMake within a directory of your。

Mas builtil directory itself。 So in concretely， it's this directory one times one times bins usually within your own built directory。

 So it's an entire new built wheel there。If you then compile it for norm projects just CMake and Nja handling all the dependencies。

 if you one time with the entire system， first ensures that all the dependency are built before you build the one time。

 so this includes for of course claim itself but also utilities like file check not and so on。

 it also when this build it actually once the CMake command。

 so it does not do it during the configuration step。

 it does it during the the build step itself and then inside the build step after configuration builds the one time you would like。

There are some， some options you may not know about because they are not really advertise。

 not even in C make。 So you can， for instance， pass your own options to the one times build within your build directory。

 So this is done with a one times C make as。 this example here you can have this from the V outta projects。

 So if you use Kang G， for instance， it would be F maxax errors。

 If you use for the one times build it uses Kang。 It's this flag with the same effect is not F maxax errors。

 it's F error limit， something that always bother me somehow。

 if you want to do have a one time for cross compilation targets。

 you can specify it and than one time targets。 And then you have addition different flexs where you can specify what options you want to have it compiled to this in this case。

 optimized for a specific。Process zone。You also have the possibility to do a standalone build in that case you can actually use any other compiler。

 including GCC to compile your one times， in that case you specify a different top level director in the source3 it's one times。

 specify one times built and you choose GCC， for instance。

 C makes decisions which compiler to use and then can build it as usual。So why， what's new here。

 So what did flang you before。 So they also two were two build types。

 First used the normal entry build， how it was called。

 which just in goes into the subdirecty in built。 It with the same compiler which flang itself as built。

 But you also have a standalone build。 In that one case。

 you would use a different top level directory。 You would tell it where to find the LL VM clang and MI files。

And and compiled there special there is actually you needs a second one as well because the decimal library is used by the fl runtime as well as the compiler itself。

 it's the same binary， which have the strange consequence that if you would compile it with kuda support。

 Qa for one。 and it uses the flang uses the decimal， which then also compiled with kuda support。

 your flying executable has a dependency on ka on yours system。

 So that's one of the less nice consequences of that one and that one to solve。

 it might be already one thing reason to change is already because all the other1 runtime to it。

 And the flying runtime would just stand out。 But there are although a different reason。

Like for AMD specifically， we want to compile for your AMD GPU targets just as any other targets。

 So if youve used naively， you would have for AMD GPP。

 you need to compile it for your host X 86 again if your host is power PC again when it has your host is A 64 and do it it's as a normal costcompilling targets。

 Sa to do that。 It's also a problem I showed also the lip decimal， which is shared code。

 which comes as problems。 there are different requirements for what you compile the one time with and you compiler compile the compiler itself with for instance。

 you can't LT is not supported with one time at the moment。

 it should not have anything to do with with。How a flag and the compiler the one time is compiled。

 but at the moment it does had to use the same flag。So what are the changes。 So as you may expect it。

 is just yeah， use the existing system for use for 11 enable one times。

 just add enable one times flang at。 That's one built way to build it in which case uses， of course。

 claimang。 just build claimang to compile the one time。

But you can also the standalone build is still supported in which case you do again。

 use the one times as the top level CMake directory。

 but then you also need to tell it where the compiled LVM is for all the tools and the Kang library and you need to specify the For compiler you want to use one special is if you probably may not have seen it yet CMake photo compiler works is because we don't have a one time yet。

 and CMake twice out whether the compiler is able to build and link executable and that doesn't work with without a one time。

 So we just tell CMake， please ignore it just assume the compiler works that's done for clang as well in the bootstling build by the way。

There are specific things thats a bit strange。 I need to continue working。 For instance。

 there is a support for 128 B floating point， which is dependent on whether the。

 the host actually support it， whether you compile it。 One possibility is using G C slip quamar。嗯。

But the， the thing is that it's tested on the host platform where you compile your fl on。

 It does not necessarily to do have to do anything for where you actually want your executable that more one might or might not have the slip cloth available that。

That kind of thing should be avoid to make the compiler dependent on the， the environment。

Or where it's being compiled。There are also two kinds of unit testing frameworks。

 So there there is a G test that all of L uses， but there's some。

 some custom called non G test testing framework as well。

 which that's be a bit complexity because it's used by test for the compiler as well as test for the one time。

 Windows is always its own topic。 and there's experimental， this Qa support that I already mentioned。

 which actually compiles the one time using NVCC or can be built with NVCC， which is yeah。

 bit unusual。So one of the first things we agreed on in an RFC is to rename the libraries。

 So on the left you see the previous names and we got them renamed to new names。

 which is more follows the the convention that is used for compile RT compile I T libraries are called lip Kang R T dot component。

You may notice there's no decimal anymore。 This has been integrated into the one time。 I。

 I strongly think that if you use the one time， you should not care about what's the internal structure on。

 on what libraries， what sourceco are shared within compiler and and one time is。 But for cases here。

 I mentioned the not support， but also if you want to have Qar。

 these are different just different components in this case。And at some point。

 there had to be a big move of all the source files。 For me。

 it was important to have like some clear separation because there were cases where I do in header file which included both things that you only could use in the one time and only use things that in the compiler and I really tried to to get them split apart。

 there were some compromises， but in total it got off。

 There are some complexity where the library actually is。 I'm running out of time。

 So I have to skip thing share library is also something more consistent with the way you used with with the other one time。

And there's some things left that complex complex。 So I still want to make the the41 modules as well use the one time system。

 or because C make has support for41， Why not use it。 But all other things that are too complex。

 even for me that this one is multilip support where you basically need to know all the the support environments at the same time。

 And I， I just can't do that。So， thank you。

![](img/9ad5d6c7edc4e953486b0f7c60db432c_2.png)

![](img/9ad5d6c7edc4e953486b0f7c60db432c_3.png)