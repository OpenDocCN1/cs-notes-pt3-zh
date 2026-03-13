# LLVM开发者大会-US-｜-2025-Llvm-Developers-Meeting-p57-P56_轻量级故障隔离_LLVM对高效沙盒化的支持--BV1ejr5BAEja_p57-

![](img/59554453b33b448d176ecc94d35aa586_0.png)

Okay， now we wrap everybody here。 So today I'm going to be talking about lightweight fault isolation。

 which is a new feature for in process isolation that RF has been approved。

 We're working on bringing into LL VM。😊，嗯。And this is a capability for providing very efficient isolation in process of。

code that we're we about memory safety。 So third party and first party nativeative code。

Before I get started， I just want to give a shout out to like the whole community of people that have helped make this happen。

 probably most of all the Android team and like all the folks who have worked on LI there。

 they've done amazing work Sha Gilil for helping shepherd the RFC and yeah。

 colleagues at Texas and colleagues at Google and colleagues in the LLVM community who've given us really helpful feedback and kind of amazing code to work with。

 so thank you so much。So， so to start off， I think we sort of everyone agrees now that memory safety is a big problem。

 It's a big challenge we're facing。 and we need better tools to deal with us。And unfortunately。

 today， we have limited options for this。Stick close to mic。One option， of course。

 is kind of the unsound mitigations that we've relied on from stock cookies to you know CFI。 And。

 these are great because they work with existing code， everybody lives in mi mitigation。

 If you can just flip on a compiler flag。 They're like， yes， I'm in。

 The problem with these is they're often bypassed。 And it's very hard to reason about the benefits。

 You kind of ask people to go through this you know enable this or that thing in your system。

 and then they do and then they get popped again And they're like。

 but you just told me to do that thing and it was gonna be secure and I don't really know what I got for for that effort。

 And for the performance I paid。😊，The other challenge right is， so another possibility。

 right is rewriting code and safe languages。 I mean this is great because it actually gives us sound security。

 Like we know what we're getting when we do something like this。

 But the downsider is that there can be huge engineering costs associated with us。 This is， you know。

😊，And， you're building another system。 You have this code that was already， you know。

 maybe as battle tested。 Now， you have to go through that whole process again。

 And the other thing is that this doesn't always play nice with the open source community。 Right。

 often， there's groups of people out there who are doing their thing。You know， with their stuff。

 And like， we want to be able to use their code and benefit from their code and either not take over ownership or try to force them into a different way of doing things。

So we would like both these properties。 We'd like to have like sound security。

 but we'd also like something that works with existing code。So one option， of course。

 is process based sandboxing。 And if you work at a large company where people are willing to pay you to do this。

 this is actually like a viable thing。 But if you kind of look at the larger world。

 there's not much of this。So process sandboxing， of course。

 it does provide a sound security and it works with a existing code。

 but it has a lot of downsize to it in terms of the performance costs in terms of context switches。

 creation overheads And so this thing makes things difficult to scale and people can go through kind of amazing contors to put this into their system。

 which adds like lots and lots of complexity right keeping pools of processes around and all sorts of juggling associated with this。

The other bad thing is right， is end this kind of broken developer experience。

 Like all of a sudden now， you've gone from having you application where perf works。 GDB works。

 right， You know how to do your thing to like a distributed system， right， Like you， you。

 you had your way of doing concurrency。 You had your way of architecting things。

 And they've just like shoved a bunch of process in there and you're like， dude。

 what happened to my my architecture。So is there another option， right。

 Is there something else we can do。So I started looking at this back in。I don't know。

 I'm not gonna do math。 like 6 or seven years ago。 We were talking with our colleagues at and Mozilla and they're like。

 we have this problem， right we have these know dozens of thirdpart libraries that we use in the Firefox render for parsing content for decoding for spell checking for all these different things。

 And if they get popped， somebody owns the render。 So if I send you like an image to your Gmail。

 you open it up。 I pop your render Now I've got your Gmail credentials。

 Now I've actually got your credentials for Google do com because that's how site isolation works。

 And so I can you know do all sorts of terrible things as you。 And're like， this is bad。

 How can we fix this。 And so we ended up doing is building sandboxing of these individual libraries using webassembly。

 which at the time was like very cool and cutting edge。 I guess it's still cool and cutting edge。😊。

And Webassembly， it lets you get past a lot of these limitations you have with process sandboxing。

 So so it gives you this nice model of isolation that you can reason about input validation of those interfaces。

 but it doesn't in a way that where you get know1 thousand times faster context， which is you know。

 very， very fast startup time。 And you're thinking about basically isolation。

 but as a language construct as a compiler construct rather than as you know。

 getting the O S into your business。So this has been deployed in Firefox since 2021 on lots of different platforms。

 lots of different users。 So we know this approach is solid。So we did this work and we're like。

 this is amazing。 Like， how can we get this out there to more people。😊，And then we started， you know。

 trying things and like， you know burning through undergrads and grad students。 what we found out。

 he said Wasum has many limitations， right， theres there's a lot of code out there that you would like to sandbox that Wasum is not a good fit for because of a lot of the properties you know that or kind of like baked into its design。

 And this really limits your compatibility in terms of your ability to sandbox existing code and also limits performance。

 And I've spent I don't know。 years in the Wasom community working on standards working with folks like I have a lot of love for that world。

 And and Wasom is is solving a very particular problem。😊，Right， just Wasm is very good for the Web。

 right， It solves platform independence， and it it has managed to get through the Web standards process。

 so。Just in itself an amazing accomplishment， however。

 if you want something where you just want to sandbox things at a low level and you really want compatibility。

 performance， security and simplicity， low level sandboxing doing like low level rewrites close to the metal really has a lot of advantages。

😊，So。We've done this。 I was at Risk 5 summit。talkingal to one of another friend from the LVM community。

 And he's like， dude， you should talk to Nathan。 Nathan is here。 He's got this problem。

 He's trying to do this thing。 So it's like， Nathan。And Nathan's like， yeah， you know。

 we've got this codex。 And they're like， process sandboxing。 is like really hurting our performance。

 Like， we're trying to do this thing with like Web assemblymbly for like better part of year。

 And I'm like， no on， dude。 Don't do that。 I've doing it for the last three years。 Like。

 it super sucks。 Like， it's not gonna go well。So Android is really interested in this becauseuse like half of the Android open source project is like unsafe。

 third party code。😊，We're like， hey， try this thing。 So the nation's like， hey。

 I've got this decoder thing I work done Like one you guys sandbox this。

 And we came back two weeks later and I like here。 sandbox thing was David。 And it was like 4%。

 He' was like awesome。😊，So we started working with the Android guys。 And I think， you know。

 we've been kind of developing this vision of right， Eliliphi。 And again。

 Lfi is this low level isolation technology where again， you know， performance。嗯。

We're developing it so we can you know， fully exploit the architecture and compiler optimizations。

 Again， we're not like e in a format。 right tomorrow， when we figure out how to make it faster。

 like what the compiler spits out will change。It does provide us， know。

 like a really good compatibility。 And since we can work with Linux API， We can be A compatible。

Works we can work with our existing tool chains， right， I think we can。

 we can build something that basically looks like a normal library but is isolated。 Again。

 because we're at this low level， it's， it's much easier to do security。

 we can actually take the output from the compiler， we can verify it and you know。

 somebody even verified verifyifier against the arm spec with an ST solver。

 So if you want a verified verifier like， we can help you。😊，And and finally， again， again。

 it's this you know， a library is a library。 you can， you can you know， try to kind of get very。

 very like know asymptotically close to that normal developer experience。 So again。

 I don't see this as like of the answer for memory safety。

 But I think it's kind of another tool in our toolbox。

 along with things like F bound safety and these other kind of great capabilities that Alion provides。

 And we're hoping that will really be something that can benefit developers。

 we have this slated to roll out Android in 2026。 And we're working on getting this to other parts of Google。

 And。😊，I'm going to actually hand it over to to talk about how it works。Thanks， Tal， yeah。

 so now I'm gonna to talk about some of the like more technical details of Lfi。 So first。

 what the overall compiler architecture looks like。

 So we basically have a new target for a sub architectureitecture of A 64。 We also have some support。

 we have support for Act6， but I'll talk for the most part here about the A 64 version。

 So it's a sub architectureiture of A 64 and essentially what happens is there are some pattern rewrites that happen at the very end of the pipeline。

 basically in the asmbler at the MC Ins level， we're going to do some expansions to to basically make the instructions that get generated conform to a safe subset of the architecture。

And this is nice because it can handle things like handwritten assembly and line assembly as well as whatever gets generated from the IR。

 And other then just reserving a few registers， we just need to add this rewrite stage。

 And once you compile for the AR 64 LI target get you get an e binary out。

 which has been rewritten and you can run a static analysis verifier tool to make sure all the instructions conform to the subset of the architecture。

 and then that binary is going to be run inside of a certain Lfi runtime that's going to load load the sandbox and load the binary into there。

So the execution environment， once it's been loaded， looks kind of like this。

 we have a 4 GB region of the virtual addressure space that's going to be given to the sandbox。

 So that's gonna to be the untrusted code can access within that subset of the virtual addressger space and nowhere else。

 and that's divided into a code segment and a data segment。

 So the code is going to be not writeriable， the data is going to be not executable。

 And other than that it's essentially like a normal program And the way that we're going restrict accesses is using this idea of well。

 if we store the base somewhere in a register， then we're gonna to make sure all the loads and stores are going to be expressed as a 32 B offset from that base。

 which can be up to 4 gig away。So let me give you an example of that。

 And this this is now what a rewrite looks like。 So this is gonna to happen ahead of time in the compiler。

 We're gonna get know the normal A 64 backend is going generate some instructions。 for example。

 that use like just a normal load instruction targeting an arbitrary register。

 and that's a 64 bit value。 So it could be anywhere in the address base。 not necessarily。

 this is not a safe instruction for our L subset。 So the first stage is the compiler is gonna have a reserve register。

 X 27， for example， which is going store the base of this endbox。

 And so now our rewri when we're compiling is going to rewrite this this unsafe instruction into a safe equivalent where now it's expressed as a 32 B offset from our base register using the 32 B plus 64 B addressing mode that Ar provides。

Some instructions don't have this addressing mode。 So like a load pair， for example。

 doesn't have this。 And so we need to instead to handle this case。

 introduce an additional instruction。 And in fact， also an additional reserve register。

 So we're also going to reserve x 28， which is going to have some invariant that it always must contain a valid sandbox address。

 some valid address within the4 gigabte region。 And and now we can load we can load a value into it using our you know our sort of 32 bit plus 64 B masking instruction and and then a load from x 28 is always guaranteed to be safe because x 28 always has a value within the sandbox。

Right， so actually I'll talk a little bit more about the control flow in the next slide。

 So when we do indirect branches， we have a similar problem。

 like this is sort of in some ways a memory access。

 and so we're gonna to do a similar mask to keep keep the instruction keep the target inside the sandbox。

 And one thing that' that's nice about arm in particular is since every instruction is fixed with we just need to guarantee that each instruction individually is safe to guarantee that the overall program is safe and holds our sandbox guarantees。

 And that's because right you can't jump into the middle of an instruction on arm。

 the hardware will trap if you try to do that because of the fixed width encoding。

There's also for handling system call or other system instructions， So we have some rewrites。

 basically there's like a specific way of exiting the sandbox that uses a function entry points stored in a specific read only page and so we rewrite system call instructions to instead perform like a load from that page and then a branch to branch out into some runtime external code that can handle that system call on behalf of the sandbox and similar thing。

 for thread local storage。 We're not going clobber the actual host thread local storage。

re we're going to use a reserve register or maybe exit exit in the form of a runtime call。

And so talking about the runtime， this is the， this is some trusted code outside of the sandbox that's gonna handle。

 handle the system calls。 So we have it implementing sort of a subset of the Linux API for a lot of the libraries want a sandbox。

 There are not that many system calls that get used like decoders and stuff like that。 They。

 you know， just need to allocate some memory and have some buffers。

And so sticking to a subset of the Linux API keeps the simple and。

 and keeps it compatible with legacy code。So just as an example of sort of what this looks like when you put it all together。

 you know， you get your software， you can pile for the special target， and then you run it。

 you can run it at the command line with this LFI run tool or in practice for a library。

 you'd have some， you know， you link into your application。

 something that's gonna to load this inbox and run it。

So I have a few slides about X86 support just to give an idea of what we have to do there。

 So the main challenge on X86 is we have variable with instructions so you can jump into the middle of an instruction。

 And so one approach to prevent that is to use what's called bundledling So we're going force every instruction to be part of a 32 by bundle。

 and if it were if the instruction were to span bundle boundary。

 we're going to pad with some no ops to move that instruction to the next bundle。

 And then just before every indirect branch， we're going to zero out the bottom5 bits， for example。

 if its 32 by chunks or bundles， zero at the bottom5 bits to ensure that the indirect branch must always go to the beginning of a bundle。

For loads and stores on X 86， we don't have this 32 B plus 64 B addressing mode that exists in the arm。

 But what we do have， well you can sort of get away with that in the form of using the Gs segment register。

 So this is actually really nice optimization and makes the load and store sandboxing on X 86。

 much more performance where we can just stick the Gs segment prefix on memory accesses and then swap the register to the 32 B version rather than 64 B version。

 And this is much more performance than you may have to do if you have a separate instruction and you can't use Gs you'd have to do like a separate move to 0 out the bottom the top 32 Bs of your target address register。

 So this is called the seway optimization that's sort the overview of the the two main differences between the A 64 version and the X 86 version I'll now go through some performance numbers and some of our benchmarking and evaluation。

So on spec， you know， we ran a number of benchmarks and in a number of different configurations。

 So we've got full sandbox And this is with， you know， this is just your proper sandbox。

 And then you can also have a store only mode where you don't sandbox the loads。

 You allow your sandbox to your untrusted program to read outside of the4 gigte region But it can't store it can't write or corrupt outer memory。

 And so in some cases， maybe this is okay for your threat model。 And then just for sort of to。

To break down the components of the performance， we also have a version with the jump。

 so this doesn't sandbox lows or the stores。 And maybe this can be this is practical when used in combination with the hardware memory isolation mechanism like MP K on X86 or P O E on arm。



![](img/59554453b33b448d176ecc94d35aa586_2.png)

So the X66 version， we actually have similar performance for the full sandbox。

 But once you go down to stores and jumps， it's not quite as good as the arm version。

 And that's because you hit this floor of the control flow isolation being a much。

 much bigger problem on X66， having to do that bundling and having to not being able to use return instructions。

we're still working on maybe some optimizations to make this faster。

 but this is sort of what the performance looks like currently。Now， for Android in particular。

 we're interested in using this for audio decoders and other other sort of media decoding。

 So we have some more targeted benchmarks for， for example， Ous， the Opus audio decoder。

 and then also for sandbox and David， David is really like so it as an81 decoder。

 and it's really a stress test for Lfi because it has so much handwritten assembly in it。

 And so I think LI is really sort of unique in its ability to do in process isolation of these media decoders that have lots of handwritten assembly in them and do it with relatively little performance overhead。

 roughly like around 5%。Here's a micro benchmarkchmark for for the function invocation overhead。

 So one of the main benefits when you bring your your sandbox in process is now you don't have to pay a context which costs when you transition into the sandbox into the untrusted domain because you don't have a separate process anymore。

 And so we can get these these sandbox domain， switches much faster on the order of tens of cycles rather than。

Tands of thousands。So here I'll just have some， some additional ongoing work that I'll mention。

This is really interesting to be applied to existing forms of in process isolation that use Js。

 So in a browser， you've got a Jit engine that's gonna be compiling your javascript and your compiler is trusted in this case。

 But if we can if we can modify the Jit compiler so that it generates code that conforms to this L subset and then have a verifier that's dynamically running to make sure that all code that gets generated。

 actually passes verification， then we can really reduce the trusted code base by bringing the actual compiler logic outside of the trusted code base and just relying on the verifier to make sure that whatever the compiler is generated conforms this subset and the verifier。

 in fact， is quite simple， right， because it's just verifying that every instruction conforms to the subset。

 So way way less complicated than and optimizing Jit compiler。😊。

Another case where this is interesting is in the kernel because your programs there are a lot more restricted and。

 you can't use separate processes， for example， if you to if you want to isolate device drivers。

 and so aI we're sort of investigating that as a solution for reducing the amount of privilege escalation that that comes from。

Third party device drivers。So that brings me to the conclusion。 We have， you know。

 we have an RF online。 We're interested in hearing your advice， questions， comments， Con。

 So if this sounds， sounds cool to you， please come。

 come chat with us if you're interested in using it。 let us know， thanks。😊，If you have questions。

 we have mic on the right side， and I can also walk around。If you just raise your hand。Hi， nice work。

 So I probably miss this。 Who is going to specify the granularity of isolation。

 like the user should annotate the code。😊，How are you go to the same box。

 So there's no annotation or anything。 It's just when you compile your code。

 you compile for this target triple and the machine code that is compiled is gonna have these rewrites applied to enforce that the machine code that comes out is is within this know secure subset in the sense of the only instructions like generated or ones like can access that are restricted to the 4 GB region。

 So an application is going to be same box。 I thought like you're going to partition the application the library boundary。

 the library。 So that's what I'm going I see I you could certainly do something with annotations if you to partition your application like manually or even automatically。

 but libraries are just kind of this natural boundary especially get like par decoders libraries usually is a very clean interface。

So every library gets its own sandbox。 you choose or we could choose that。Yeah。

 we don't know evaluate to lose San B player libraries。Yeah， so to start， you know。

 you pick one library， for example， that you want to have in the sandbox and you're gonna to。

 you know， modify your application to do that。 and then maybe you'll put more and more in the sandbox as you。

You know， decide or you can have multiple sandboxes as well。 Okay， I we， we can chat later。

 But things， yeah。I like。So。So if， if you malloc something。

 does the runtime is it allocated in the 4 gigabbyte address space。

 and then the runtime just gives you like the offsetend into it。 Yeah。

 so you there's basically two allocators Now when you're using it from the host application。

 you have your normal host malloc， which could allocate anywhere。

 But there's also you can call the sandboxs malloc and that'll give you a buffer that's in the sandbox。

 And so if you need to give the sandbox and data or you know。

 you need to allocate a buffer where it can put its results。 You allocate the sandboxs allocator。

Yeah， thanks for the thanks for the talk。 It was pretty interesting。 I'm actually a little curious。

 The registers you guys were using as part of the sandbox here you're using X25 through x28 as your sort of reserve registers is that restriction only on the sandbox library is the process itself also restricted in those reserve registers。

 Yeah so that's only in the sandbox environment your host code is compiled natively without those reserve registers。

 but on the transition part of the additional overhead in the transition time is modifying saving restoring those registers or putting the correct values into those registers。

 so so I guess the big risk So the follow up would be so the big risk is those reserve registers can't be put on the stack realistically right if you're worried about corruption or anything like that。

 Yeah basically those reserve registers like the sandboxbased register can never be modified by any instruction in the sandboxes code。

 So that's one of the things the verifier is going enforce that there's no instructions that modify X 27。

Got it。 cool， Thank you。Very minor technical question。

 You always showed the base being at the bottom of the region。

 Will there be any architectures where you only have a assigned32 bit offset。

 it needs to be in the middle。I haven't come across that， but we've。

 we've only looked into Ar 64 x 86 in Ri 5。 Maybe there are some strange architectures。

 where this would be convenient。Any other questions。So for this， so for this to be secure。

 I guess do you have， do you have to like have two copies of say like the C library like in a process like the secure one and the insec。

 So essentially inside of the sandbox， everything all dependencies of your library or whatever you're putting in there has been compiled with the for the a target and statically linked。

 Does that include Lib C So you don't need a different。

 you don't really need a different Lib C like source code。

 but you do need to recompile it for the a target， Did you run out of curiosity。

 did you run any integrated problems。 There's a lot most C libraries assume like there。

 they only one。嗯。Well， yeah， So because the， because we have like we rewrite all the system calls and the TL S axises as well。

 Basically the Libpsy inside the sandbox has no idea about the external Liby and the external Lise also has no idea。

 know， it just looks like a memory mapped region to it。 So they don't actually interfere at all。

 And then the runtime is like gonna handle these system calls that come out of the sandbox Lib see。

 So they're not actually sharing， you know， any of the same system state because all that system state for TL S or things like that gets virtualized by the runtime。

' talking about also's no like symbol clashes or anything like that。No， I mean， for example。

 you compile your library as a static bb， and then it's going to be dynamically loaded and so。

That's all the symbols aren all the symbols are private。 Like the only thing you expose are like。

 you know， kind of the the trampones。The interface is like for library that get， okay， thanks。Yeah。

 I think that's all the questions。 If you have have any other question。

 you can meet talk to the T hotel outside outside， you know。Our next speaker。 Yeah， thanks。

