# 中英-•-C++和C语言ACCU大会2024｜人工智能｜架构｜函数编程｜静态分析｜安全｜编译器｜开发者｜垃圾回收｜链接器｜代码生成｜cmake-p28-P30-C++-Linkers-and-the-One-Definition-Rule---Roger-Orr--BV1pNotYYELk_p28-

![](img/98029beef01d55c3107916ed8455d3ff_0.png)

Well， welcome all。 Thank you for coming。 Link is in the one definition rule。 Now。

 he was in this room for the previous talk。😊，Okay， there'll be a little bit of asem， not as much。

 And I won't be talking quite as fast。Because it's getting later in the day and your brain might be about to catch fire。

Typically， we compile and link C plus plus programs。 in my experience。

 most people at least have got a vague idea of what they think a compiler does。

 Anyone feel they've got a vague idea of what a compiler does。And。

 and probably a rather less good idea about what the linker does。

 who Who thinks they know what a linker does。Okay， yeah。

So I'm going to cover it with examples from Windows and Linux because those are the ones I know best if you're on a different platform or not Linux on the。

A and D 64， then some of what I say won't necessarily be true on your platform。

 but hopefully because I'm talking about two different platforms。

 it will still give an idea of the sort of things that happened。

And then I'll also talk about the one definition rule， the ODR。

 and what's that got to do with the linker， and hopefully we'll find out when we get there。So。

 first off， who needs a linker。Can't we just throw the link around and use a compiler。

Or even not even bother with a compiler。So as the old joke has it back in the day。

 you wrote programs by copying from con to A or out， just cat type in the hex。

Anyone ever written a program like that？1 at the back。Yeah， and。Theres actually co file format in。

 in the old days of Doss。 Who remembers Dos。 Yeah， Oh， yes， you are my age。 Some of you。

 And you had the X file format， which had a file header。 It was quite a simple file header。

 But the Com file was just load these bytes into memory and start at the first byte。😊。

Nice and simple。 And we actually used that， as I say on the slide in an example。

 we were doing an installation program for remember floppy disks， you know。

 the incantation of the save icon in 3D。 And wed filled the floppy disk 1。

44 with all the binaries we wanted to install and the install script。

 And then we realized we needed to reboot the machine at the end of the install process。

 We didn't have enough disk space to even put one more program on the floppy disk。

 So we worked out that we could put a few more bytes at the end of the install script。

 We could echo C S backlash P， which we took a while to find a sequence of printable characters that causes a triple fault on X 86。

 and then execute B dot com and the machine rebooted。😊。

Something I never questioned was whether any of the people who'd used this install disk ever idly wondered what this B dot co on the route of C disk and tried it。

 but we never got an error report， so maybe we were okay。But this is。The simplest possible program。

 It doesn't do anything that involves anything external。 There's no， there's no linking。

 There's no compiling it。 just is a sequence of bytes。

 And that's what we're ending up with at the end of the day。

 When we write a complicated C plus plus program and compile it down。

 We eventually end up at some point with a sequence of bytes in memory that get executed。

So it could go a little bit more complicated。 Still back in the old days of Doss。

 things are nice and simple。 We have a little header。Which I'm hiding in our main， we just go print。

 Hello world Co return， line feed Do is， this is the end of the string。And， then me exit。

And in the doss header， we have some in line assembly that generates the appropriate interrupt calls。

And she's also seemed horribly familiar to some of you and you thought you'd long passed these days。

But it means that you can actually compile this in a single pass。And you don't need a link stage。

 You just write out to the output， the， the instructions。And that could be done very， very simply。

 And in fact， one of my very early jobs， we had a single past thoughtran compiler。

That turned For trans source code into executable in in one pass。It was。

wish I could ask questions of my former self because I now looking back。

 I I've got questions about that compiler， but it it worked really， really fast。So in this case。

 what we can end up with is。Just a few instructions。So we load these this program into into memory。

 We get the effective address in this D X register of where the text is Ho world。Issue an interrupt。

 that goes into the operating system， comes back， we put the return code in。

 we issue another interrupt job done。Nice and simple。However， it doesn't really scale very well。

We've got no， no function calls in there。 Everything is just linear。 Start at the top。

 Get down to the bottom。 However， it is。Functional。It works。

And we've converted our single source file into an executable program。

How many of you are working on projects now that are a single source file。I'm not seeing any hands。

 Yeah， I can't think why。So let's go a bit more modern。 We'll， we'll get into the sort of this。

 at least millennium。Hash includes some headers， ink Maine， yield stood printf。😊。

I said C plus plus printf。Yeah， still C plus plus。 Also。

 it makes the examples a lot easier because otherwise you get into a whole bunch of stuff that Io stream pulls in and makes it much harder to see the kind of wood for the trees in the talkrque I'm doing。

😊，So。This is actually done known in two stages。 The first thing is that we compile to generate an object file。

And then we put the object file together with the standard library and generate are executable。Now。

 sometimes you don't actually see the object file because the compiler affected。

It doesnn't bother to write it to disk。 or if it does， it throws away afterwards。

 you can appear to go。Straight through to the executable。 But under the covers。

 it's nearly always doing it this way。And there's also some metadata， not just the raw bikecode。

 but additional information that will be used by the linker and later on to kind of tie everything together properly。

And you can see what's happening by looking at the asar output。

Or you can use Matt Godbalt's wonderful tool。 He does this amazing job at taking hundreds of lines of a sender output and producing the three or four that you really care about。

 who's， who uses Godbalt to look at code。 Yeah， it's great， isn't it？

 So I was very impressed with this one because。😊，On the left， that's what you see from the output。

 There's 2382 lines in the asem output。 And he manages to display just those。8，10 lines。

MSDC produces far fewer lines， and he ends up with more lines on the screen。 but hey， whatever。

 I think he started out with GCC and has managed to strip things out。

 So what we're seeing in the object file here， a few things are of importance。

 The first is we can see the string， Ho world。And it's got a label attached to it。

And then we've got the actual code。Pushes and moves and another move。 and then a call to a function。

The first thing you might be puzzled by on the left， we call puts。In the source code， I had printf。

Oh。That's nice。 A compiler has liberty to do this。 Printf is part of the standard。

 and it's defined in terms of， of put that it can replace the call to printf with the call to puts。

Saavs a little bit of work。 MSTC doesn't do that。But of course。

 we don't have put S or printf in our object file that comes from the runtime library。

So in the linking stage， we take the object library that Ob  Fives just generated and the runtime library and glue them together。

And the external references in this case to puts or printf get resolved against what's in the library。

And the resultant binary may still still contain some unresolved references because of the way that runtime loading goes。

 but for now， we'll just quietly ignore that。And what happens in these stages is the linker is editing up the references。

So that in the object module， we're calling this symbol， don't know where it is。

And when we link it together， we now know where it is， and we can put the address into the binary。

Hand waving slightly， Its not quite that simple。And certainly。

I won't say how many years ago I worked on a linker， and it was called the linkage editor。

 because that's basically what it did。Modern linkers do lots of other clever things like optimization and stuff and generate debug symbols。

Wonderful things， which I'm not going to cover in this talk because we'd be here till after the lightning talks。

 but they are getting quite complicated， but the basic principle is linking together these object modules and resolving these undetermined unknown references。

Things get bigger。So the GCC， the output file Hallellot O is 1592 B and。嗯。

You link it together and you get something even bigger， you get 8，3，4，4 B。 Now。

 if you fiddle with the linker options and the compiler options， you can change the size a bit。

 but it's。80 times bigger than the original source code。Which is slightly scary。

And it's got three dependencies on Lib C。😊，The shared library on Linux， Lipsy start Maine。

Exit and put S。 Now we know about exit and put S because that's in our code。

 The other bit is magic that gets the C plus plus runtime up and going and starts your， your main。😊。

On MSVC， the object module is slightly bigger。😡，2 and a half thousand bys。 Well， you know。

 he's counting。 And again， if you fiddle with the options on the compiler。

 you can get that number to up and down a bit。 And the binary is about the same sort of size as GCC。

 slightly larger。But it's got a dependency on two DLLs。TheCoel 32。

 which is providing the W 32 API and VC runtime 140 DLL， which is the C plus plus runtime library。

And also five dummy A API set DLLs that don't really exist， I won't cover now。

 and it needs 43 symbols to be resolved from these DLLs。That's quite a few。Including exit。

Which we called and also underscore， underscore stood I O， underscore common， underscore V F printf。

With the particular symbols I was doing， what's happening is we've got printf is the unresolved symbol。

 When it goes to the runtime library， it finds part of the implementation of printf。

 actually in the library。As object code pulls that into the executable。

 and the only unresolved bit is this call to the common V F printf function。

So you learn things when you're writing a presentation that you didn't know。And as an aside。

 when you actually run the resultant binary on Linux I ran it with Stra and I got 28 calls who's used Stra on Linux quite useful。

 the low levell operating system interface and it demangles some of the things so the open call tells you the name of the file that's opening and it opens this shared library the load is doing that maps it in。

😊，We can also see the call to write that the printf call is making or the puts S call is making。

 Windows doesn't really have quite the same direct equivalent。

 I've got a tool I wrote called N T trace。 Other tracing tools are available， which tracks the。Again。

 operating system interface。 and we get 284 calls on Windows。 Wow， it's a lot more。

 Startups more complicated and5 DLs get loaded。Starting out with N T DLL。

 which actually contains the operating system interface itself。

 also including kernelonel 32 and the sea runtime。And in the middle of that。

 we can see our call to N T right file the。Operating system level call to write the data out。

So let's split our example up from one source file into two source files。As long as I need really。

3 important numbers in computing。 Theres there's no one and more than one。

 So you can generalize two source files to how many source files are on your project。在那。

So in our main dot CPP， we call an external helper function。She's voidd。In Ma。

 we put out how I want to in Ma， call the helper function， and in helper do CPP， we print out。Hello。

 world。ok。Probably one of the simplest example programs you're likely to see this week。

And when we compile main dot CPP， we've now got an unresolved reference to the helper function。

 It's not there。 It's somewhere else。And if we try to create a binary from。Main or main object。

 It doesn't work。So we get an undefined reference on GCC to help her。

And MSVC is slightly less helpful， it tells us。And question mark helper at Y A X X Z gives us the mangled name。

 but it also gives us the original symbol as well。 D mangles that For us and tells us that they're using the Sea decal callinging convention。

 which happens to be the default。These mangled names。

 whenever you're looking at low level stuff with linkers， you tend to come across them。

So what happens is when you have a program source code。

 you've got the function with a name and various types of the arguments， return type， etc。

 and they're usually encoded by the compiler to include。

Bits of or an encoding of the argument types into the mangled name。And there's two reasons for that。

 The first is it makes sure that。Everything lines up。So if in my other function。

 I implemented helper and expected an hint argument。

The mangled name would have int in it and wouldn't match what main was expecting。But conversely。

 it supports overloading。 I can have several functions that differ in the argument type。

 and they've all got different names。So in the source code， they've all got the same name。

 but the compiler can work out which you one you want， and given the different mangled name。

 the linker can work out which one you want to call。

MSV and GCC use completely different encoding schemes for the names。

 So if you get to recognize it in one environment， it won't help you much with recognizing in the other environment。

So as we see here， MS seeing codes with question mark helper at app， etc cetera。

 and GCC underscore Z6 helper V。U。Fortunately， there are tools that let you turn this mangled name into a readable name that looks like what you've got in your source code。

 Some of the tools do it for you。 So you don't have to worry about it because as we've seen when you get these unresolved references。

 it tells you what the sort of C plus plus name is。 But if it doesn't。

You can use anddecorate it with under name in MSV land or with C+ plus Fil in the Gcc world and it will tell you what the name is。

If you  type it in and your typing is as good as mine is。

 you tend to get nothing back because you've mistyped one of the letters or put it in the wrong order。

 Copy post is definitely a good thing to do。 And also。

 sometimes it's not entirely clear where the name ends。

So sometimes you end up with something with a prefix on the name or a postfix。

 And if you put the whole thing in， it doesn't understand it。 So you sometimes have to show it down。

 You get used after a while to， to kind of decoding it a little bit in your head。

 So you can often do this。And you can also do both of those programmatically if you're doing luckyy stuff where you need to convert the mangled name into a readable name at runtime。

 but few people need to do that。So when we provide the object code from the helper function as well。

 as main links together because the linker can。Liick link the two together and put the relative address of helper in the place in Maine that calls it。

嗯。So looking inside the built binaries in both cases。

 obviously they're going to be different in many regards。

 but the basic principle is the same in both cases。So what we've got is conceptually。

 we take the code。😊，Which is called dot text， normally。And we， we put the main text first。Probably。

 and then follow it by the code from the helper function。And while we're putting this together。

 the linker remembers。What the address is。Does that help a function。So where is it in？The resulting。

Combined text section。And then it chucks the data on the end for Maine and helper。And again。

 it remembers what's that address relative to the other sections in the code and what's that address。

And then it uses those addresses to fix up the code。So in Maine， I'm calling help her， well。

 help her， I'm here and I'm calling how many bites further on。

So it could just replace the undefined reference to helper with an where helper is it's 48 bys that way。

In reality， there's much more going on than just text and data。

But that's the most important parts of the program normally。

And you can look at the complexity with a couple of tools and again they're different on the two environments so with MSVC there's a tool called Dump bin for D binary and it takes a range of different options and one of them is headers which just links shows out all the headers in the executable and in Ar the case there are 16 directories shown for Windows executable and our simple case only six of them have anything in。

The other 10 are empty， theyre use for things that we don't use in this example。

And of the section headers， we've got dot text for for the code。

 dot R data for read only data and dot data for read write data and a few others。

Corspondingly on the GT world， you've got readellf and there are other programs as well。

 But that's the why I tend to use a lot。 readellf minus L with hellello dot out。 And again。

 that lists us in this case，13 segments And with mapping from segments， sections to segments。

 And again， we've got here dot text is one of the things in03 R O data similar to our data is one of the things in 04。

 And data is one of the things in05。So it's quite a complicated structure and supports lots of additional things that I won't have time to cover today。

Now。When you run a program。What happens。And the answer is， of course。

 it depends In some environments， the program gets loaded a fixed address。

And so that makes the job of the linker very easy because it says， well。

 I know where everything is going to be when this program runs。

 so I can actually put hardwired addresses into into the binary。On。A lot of modern environments。

 programs load wherever。How many of you are working on environments where programs load？

Always at a fixed address。Any。How of you've got no idea whether it loads at a fixed dress or not。

 Yeah， mostly who cares。嗯。So。Back in the day， a lot of programs used to load at a fixed virtual address。

 And then all the malware people got busy。 And it's really easy if you've got a program always loads at the fixed address。

To do a buffer overrun。 And you know what addresses everything else is at。

 And you can disassemble the code on your own machine and say， I could put in a call。

Here to this address， and it all。Do what I want now rather than what the program author wanted。

 So they added in this address space layout randomization so that programs load at different addresses。

 Sometimes on some operating systems every single time you load a program it runs a different address and other operating environments。

's after every reboot programs load at a different address。

 But it means you can't guarantee your program is going to be at the same address。

So you can't put fixed addresses in the program as easily。But that's okay。 what， what is an address。

 Well， it ends up。 I need to address。This bite in memory。

 but one of the things that the computer knows or the thread executing knows is， well。

 I know where I am。So I can just do a relative address from where I am to where the target is。

And this。For most address， there's two ways of of accessing them。 One is a relative。To where you are。

 another one is the absolute address。 And most of the time。

 you don't care remotely what the absolute address is。 You just want to know。

 how do I get from there， to there from here。And quite a few of the instructions that the X 86 and obviously many other instructions sets operate work on either an absolute address or a relative address。

Now with X 86， you can do a jump or a call to a relative address。

 and actually you can do a jump to a one byte offset。

Which recognizes the fact that lots of jumps are very small。 So if in your high level language。

 you go， if condition something else， condition something else。When that gets compiled down。

 it typically is a test and a jump。And then。When the if branch finishes。

 there's another jump around the else branch。 And again。

 typically the body of the F and the body of the L is quite small， so it fits into only a few bytes。

 So a one by offset is enough。So I did a quick。 I took Che and disassembled it and then look for jumps。

 and half the jumps in the binary were of this size that1 B jumps。

So it was a good optimization for the chip makers to come up with。

The second sort of relative jump you can do is with a 32 bit offset。This is in X64， right？

So you're right to do a relative jump as long as it's within two gig。

How many people are working on a binary， single binary that's more than two gig in size。Yeah。

So you got some problems with this。 and it means that the compilers got to do some more complicated stuff to get from one end of your single executable。

To the other。Most binaries are small enough that you don't need to worry about that。

 And so within the single executable or shared library， jumping within it and calling within it。

 you can do with a 302it relative offset。And also means because it's relative。

 you don't care where a memory it is。 It can be a low memory address， high memory address。

 Everything's relative。 Once you've started， it just runs， jumping relatively。😊。

If you want to jump to a 64 B address， you've got to do a bit more work。

So there's an additional cost in terms of space and additional cost in terms of execution time now。

 obviously when they put together the X 64 instruction set。

 they could have said let's make relative jumps 64 B relative address。

But that would have meant that all relative calls were twice the length。Now， instruction cache size。

 you're going to fill it with things that are。6 zeros。 And a small number。Again。

 they could have decided to have 32 B relative offsets and 64 bit relative offsets。

For all the instruction to do calls and jumps。 But then again。

 you're running out of bits in your instruction set。For other things it might be more useful。

 So I guess they just did someone sort of heuristic and decided 32 B relative offsets are good。

 Anything more， you have to do something slightly more complicated。

So if I take the output of mainine or exie and I dump in， another option to dump in is slash disasm。

 disassemble， and cut out the bit I care about， Maine starts here。And。We fiddle with a stack。We load。

R C X with an address， it's a。64 bit address。 But the actual instruction only has。Small。

4 by number for where the address is It relative address。 It's。

 it's the current address of where we are plus 1，6，3，1，5，0 D。And then we call。Priinf。Which is oh。

 it's a cool instruction， and it's 70 by from where we are now。And then we call helper， which is。

0 b bys from where we are now。And that will be the same sequence of bys， actually in memory。

When you run the program。Nothing needs to change in the code segment when Mainda X gets loaded because all the instructions in the code segment in this example are all relative。

It doesn't matter quite as much for a binary file。 but as we'll see later on。

 look at shared libraries。 Well， the hints in the name。

How many programs might be using a shared library when you hope more than one。

And so if the code segment doesn't have to change。When you load the shared library。

 multiple programs on the same box can share the same actual pages of memory because they're the same。

And even more cleverly， if you're running on a virtual environment and the virtual environment is smart enough。

 it can actually share code segment pages between multiple virtual environments because they're not changing。

So you get far more use out of your memory。The equivalent the GCC uses ObsDump。

And it's much the same。 slightly different format for the assemler listing。

Things are the other way around， but it's basically equally andcomprehensible to most of you I'm sure as the previous slide。

But the key bits are， again， we'， we're doing a call。 and it's a relative address。

 This one's a negative address。So wherever they've put this thing。

 it's further up the binary and helper is it's setting bikes on。And in fact。

 you'll see that if you count，1，2，3，4，5，6，7， it's 7 bys from the end of the cool instruction。

I don't know enough about hardware to know why that was a good choice。

 but presumably they've got something that already has worked out where the next instruction is because they've had to decode the current instruction and that can be a variable length。

 So they they've already got the next instruction。 So why not make it relative to that。

 I'm guessing it's something like that。 But it does mean if you're trying to read this sort of thing manually。

 you need to know when it's a relative address， I it this instruction or the next instruction。

And again。The X codes that are there on the left hand end are what appear in memory when you run it。

And away you go。Now this just shows two examples， two source files being linked together。

 but of course in general you've got more than that and you can build programs by just linking together object modules。

 lots and lots and lots of them this rapidly gets unwieldy anyone worked on a project where you link together lots of object modules manually yeah anyone discover that you've added ones in that you didn't need。

Yeah， and what happens then？You got possibly ODR， you get coblloat。

 You get a bigger program than you won。 Or conversely， if you miss one out， what happens。

Doesn't link linker error。Hopefully， a link error。 If you're unlucky， it might find something else。

 but hopefully a link error。 And either way round， it's， it's quite a manual process。

 and it doesn't scale very well。 And my program uses these 16 object modules。

 And when you write your program that uses the same basic functionality。

 You've made slightly different choices about what to use and you don't need the same 16 object files。

 you need a different set of 14。 and it all gets very difficult。Which is why libraries。

So you glue a whole bunch of object files together in a single file and call it a library。

 and this gives quite a few advantages。 So the first saw is a static library。So you。

 you bundle together these object files into particular file format。

 and very often it has a little bit of metadata。 So， for example。

 here are all the symbols that are defined in this library and。

 and which object module they're defined in。So it makes it much quicker for the linker to find things because it's already got the pre builtt table of where everything is。

 and secondly， it only bothers to include the things it needs。So I can now ship a big。

 shared a big static library with lots of object modules in。

 and your binary only needs one of the object files。

 So you only get the code from that one object file。So we can do that in our case， again。

 a bit silly for a toy example to turn a single file into a library， but you know， generalized。

 so we compile the source code unchanged。But this time we added in a new step。

 so on GCC we use the librarian archiva to create a Libheler。 A， again bike convention。

 libraries tend to start Lib and then the name and then dot A for static libraries。On MSVC。

 we do the same again， we use LibB with the out being the helper and there's not the same convention with the Lib prefix。

 partly because the Lib goes in the extension。You probably don't that often write that yourself because it's probably your build system that does that。

 And you just wave some magic saying， create me a static library。

 and here are the things to go in it。 And under the covers， it's doing this sort of thing for you。嗯。

Anyone use Le and AR from the command line themselves。Yeah， occasionally。You're in the right place。

And you can examine what's in the library again using different tools。 so with GCC。

 you can use NM to this A file and it tells you。This is one of the object files that's in it。

 And inside that， there's this。Remember that scrambled name from before？Or of course。

 you can pipe NN through C plus plus Fil， or you can provide NM minus capital C to give you the dmangled name。

With MSVC again， is' Din， the one we've seen before， this time with a Lincolner member。

And there's an option here for what sort of style of output you want。 And again， it tells you。

 hope that should be do。Dot Lib tells you the public symbols and the name and some sort of offset。

Which again， you don't care about the 104， but the linker will because it will use that to simplify linking things together。

And then at link time， you provide the main object file and the library and let the linker do the worst。

So we call GC plus plus with our output file dot O file for main， and we pass。

This is the directory to look in。And that's the file to look for。So。Toolth chain adds。Lip helper。

And it looks for dot A。If it finds it， it will use it。 It also looks for dot S O， which will come to。

Very soon。On MSV， we again use CL， we give it the object file and we just give it helper dotlib。

 same file name as we had before， and we tell it the add build into the lid path。

Build is where I put the the library。Now you can do definitely。

 you can provide the actual path to the library。 You don't necessarily have to do it this way。

 but it's very common to split things up into a directory path and a list of files。

 because often you may have more than one library in the in that path。And in a simple case with。

Just one object file in the library。 The output is unchanged。In the Linux case。

 you get exactly the same binary。Which I was quite surprised actually。

 I thought bound would be some difference。 But no， if I di my main dot out that was comprised of main dot O and help with the O and I di that against main Lib out。

 I get。No difference in the binary at all。MSVC， it's slightly more complicated because they put timests into their executables。

 So unless you're a really fast typist。You're going to get a small difference in the output。

 So here I've got B 5， A5，5 D5 V， Oh B5， A 5，5 D5 V。

 So obviously the timetamp is appearing twice in my executable。Also。

 I have no idea why it's capitalized the second argument to D， but F， but。It works。

And the main difference is start to appear once you've got a proper library with multiple object files in。

So if you provide multiple files in the library and you need access symbols on one of them。

 then you only pull in。What you need。 So if I create。An extra。

Source file and compile that and drop that in my。Main Ay。

I now find that main do out and main actually are out are different sizes。And they， they differ。

 because the。Compilr and Lier pulled in all the code from extra dot O into my excutable。

 even though I don't use it or need it。Again， there are ways of。

Configuring the linker so that you can throw things away that you don't need。 But in general。

 you end up with extra craft in your binary that you don't need or want。With a library。

 if I create a lid extra that's got the two binary object files in helper and extra。

 and then I compile a link against the extra library。 I get once again， the identical。Bike for by。

 identical output file。So the linker has said， okay， main。

O has got an unresolved reference to helper， helpers in this library， it's in， oh， it's in helper。

O pull the code out， stick it in， extra to O never gets referenced。😊，Okay。

 any questions about static libraries。Is that all like really well known to you or Have you learn something。

You will awake。Good， yeah， I've got if not， I've got a glass of cold water here， so。

Now you can also have a shared or dynamic library who's used or built shared libraries。Yeah。

 who's had a completely trouble free existence with shared libraries。Yeah， okay。

So the idea shared libraries came from a time when。Computers were very expensive。

 memory was very expensive， it was quite nice if you could share things like code and reduce the memory pressure on your PC or whatever computer you had。

We're not actually in that world now。Quite the same way， most people for code。

 So some of the benefits of shared libraries are are less important。

 but there are still some definite advantages。 But I suspect a lot of people still write shared libraries when maybe they don't actually need to。

 but we shall see。So what you can do is write a shared library be usable by multiple applications。

And now what you have is effectively logically an extra step that goes on because when we load the program。

 we've now got to resolve the reference to the shared library。So with a static library。

 everything can be done。Hand waving slightly。 Everything can be done at link time。

With the shared library， you've got to have a reference to the shared library when you run the program。

 you've got to find the shared library， you've got to load the shared library and you've got to resolve references so linking actually takes place in two stages。

Once at link time and once at load time。And at runtime， the loader goes off and does all this。

And as I said earlier， if you're sharing the same shared library across multiple processes。

 you may find that some of the pages are already in memory。

 so actually simplifies the job of the loader because it goes off to load the shared library it's already there and the memory is already hot。

And on I was surprised to find playing around on。My laptop here with with the WSL 2 and bash and GCC。

 you can actually do a lot of this stuff with shared libraries without making any changes to the compilation stage at all。

Which is quite nice。At you can on GCC on older versions of GCC and some of the platforms。

 depending on how they're configured， you need to wave flags at the compiler to tell it to generate position independent code。

 But for the purposes of this talk， I've basically ignored that because it's one more thing I'd have to cover。

On Windows， though， you do need to make a change normally。

This is because the Windows model of shared libraries and the Linux model of shared libraries diverge in one particular。

Difference， which is that by default on Windows， anything that's inside the shared library isn't shared。

You've got to say what bits of your shared library actually are visible outside。

And if you say nothing， you get nothing。It's evil and I shared library that has no。

 it's like a sort of black sphere。 You know， there's nothing， nothing to see here， nothing to call。

So if you try naively compiling your code， checking into shared library。

 and then you try to load and do something with a shared library， and bad things happen。

 doesn't work。So you need to mark the functions that you're exporting。 There's two ways of doing it。

 One way is is to write a linker definition file and the other way is to mark them with this double underscore dec spec。

So you mark the functions you want to export as exported。And then conversely。

 when you're calling them， you may mark them as imported。

You can sometimes get away without bothering it that bit。😔，It does slightly change what happens。

 but it works。You can also export data， the talk would be too long。It's like you shouldn't do that。

 right？So in our example， we can take our static library， make it into a shared library。

 and link against that。😊，In my case， I was able to create the shared library compiling exactly as before。

This time， I create a shared。Library rather than the default static library and the convention is do SO。

With Microsoft。I put in the。LD， I think it was。 And in this case。

 I started out giving it a definition file。Now， in the GCC world， you just get an S O。

In the Microsoft world， you get the DLL， which you expected。

 and you also get a couple of other files。 You get a helper dot lib and a helper dot X。

Few people ever need the X file。But most people need the lid file。Again。

 as with the static libraries， you probably don't do this yourself。

 but you probably just w the appropriate flags over your build system and it goes off and builds a shared library rather than a static library。

And as before， you can look at what's in the shared library using the similar sort of tools。

 So if I do N minus capital C on the S O， you can see it's got。Helper functioning inside。

And if I use dump bin with another flag exports on my DLL。

 you can see that our good friend question why helper at， whatever is exported from the DLL。

That's it。 Nothing else is exported from this DL。So although there are dot dots above and below。

 that's for all the other craft that the output generates， not for other symbols。

 whereas in the GCC case， there are loads of other symbols exported or visible inside the shared library。

And if you look inside the Lib file that's generated in MSVC， you can see again， the same function。

 So it's in this static。Library file。So， when you're。Linking your program together in GCC。

 you point it。At the Helper Library， and he goes and finds libhelper。soO。

 which is going to be the shared library you actually run against at runtime。

And it finds a reference in the helppo SO and puts it into the binary in MSVC。

 you give it this lib file。and the lid file。Tells the linker that the symbol you want is available。

 It's in a shared library called helpper。t DLL。And in both cases。

 end up be a result in binary that doesn't work on its own。

If you try running it without the shared library available， bad things happened。So in the GCC case。

 you get a message Lib help or the SO can't open shared object file， no such file directory。And。

Windows MSVC， you get a dialog box which says code execution cannot proceed because helpDLL was not found reinsalling the program may help this problem。

So I just built it。But in general， that is probably a good advice。So that's the first。

Important difference in in usability with a shared library。

 You've got to make sure that the program can find it。 Otherwise， you get a runtime problem。 Now。

 if you get things wrong with the static library， it won't link。

And so you've got to fix that problem before you end up the program in the first place。

 but with a shared library solution， you can end up with a program that links fine and you ship it and it doesn't run。

Because you've missed out or haven't given the instructions so that the loader can find the shared library。

And。Life is complicated On both windows and Linux are multiple ways of telling the loader where to go and find the shared library。

So in Linux， you might put it in a known directory。

So you might install it somewhere in a well defined list that that particular installation of Linux knows where to look for the shared library。

You might actually you can embed the path in the application。People vary。

 some people think that's brilliant， some people think that's terrible， and you should never do it。

But you can do it。 And the other thing you can do is there's an environment variable L D library path。

 and you can set that up to a list of paths to look in。 And again， people vary。

 Some people think that's a great way of running things。 And other people say never do it。

 The strengths and weaknesses of each and。😊，Briefly cover a bit of a minute later on。 Alan。

 you got a comment or question。めくさいます。good reason。Good reasons for and against。 Yeah。

 and additionally， particularly with L library path。

 you can put in a relative path or an absolute path。

And interesting things can happen if you try relative paths， well that can happen。

 is there absolute paths as well。 Windows has got similar list。 You can put it in a known directory。

You can put it in the application directory， so by default on Windows。

 it knows where it loaded the XI from and it has a look to see whether the DLL is in the same directory。

By default。Or you can add now there's not a separate environment variable on Windows。 It's the path。

 which is the same place you look for executables， as well as shared libraries。Good decision。

 bad decision。 It was a decision。It's got strengths and weaknesses。

But you just throw people flipping back and forth between the two。

 it's quite easy to forget and to set the wrong environment variable and wonder why your shared library isn't found。

So， for example， I can export L library path as current directory slash build。

 and now my program runs。Because the loader has a look in standard places and then in the build directory and finds the shared library on MSVC。

 I set the path to current path and I put current directory build on the end。And again。

 the program now runs。In both these cases， of course。

 I'm just changing the path or the LD Library path for the current command prompt。

So you can potentially update it in the settings for that user on that machine。

 but then of course it doesn't scale very well if you want to do that for 27 different applications and you end up with an LD library path like this or a path of similar length on Windows。

So what happens？Behind the scenes is inside mainine Under Lib or out。

 there's a reference to the shared library。In the， in the metadata in the binary， Livehelp dot S O。

 which is how it knows。That it needs to find that library and how it knows what name to tell you when it can't find it。

It's also got an undefined reference to helper。Now， in our case， the hints in the name， Lib helper。

 helper， they probably go together somehow， but in the general case。

 you've got no idea which of the libraries。You're expecting to find the missing symbol from。

They're not tied together。So during startup， the loader。Start sliding the executable。

Finds it needs a reference to Lib helper loads up。 Lib helper looks for its symbol table。

 chucks all its symbol tables into its collection of symbols。

And then tries to resolve references to this undefined，' what the you undefined helper。

 And blame me down， it's got a reference to it that it loaded from the helper。

 and it knows where it is。So it can put the virtual address for the function into the memory for the program and there's a question from the back Before we go any further Roger。

 I think I missed the point at which helper stopped being mangled on Linux。

hIt depends how you dump out。The name， if I actually。If I did N M without the minus C option。

 good point， it would still be mangled。 Yeah，s that's a good point。

 I should probably change that for future reference。

 So we we find the symbol in the global symbol table for the executable。Now。

 what happens normally is on x 64， the jumpstone indirectly because where the executable is in memory and where the shared library ends up may be miles apart。

It's unlikely to fit within the two gig range， so it can't use a 32 bit offset。

 So what it does instead。Is a little bit complicated。 So in Maine。We have a call。😡，2。

Our function was at P LT， at the end。Procedure linkage table。In the PLT， we have a jump。

To an offset of the instruction pointer。 So it's a relative offset。 So it says。

 go and find that address relative to the instruction pointer and trust me。

 you'll find a 64 bit number there That is the real place you're supposed to go to。

So we've got a call to helper that goes via a call via indirect jump。Vre a 64 bit address。

And this address。Some address，5，5，5，5，5，5， whatever。 And this address，7， F， F， F 7。

 theyre a long way apart。So the offset here is。2， A， A， A， etc cea。

 Well beyond the 32 B relative address。 it， it's a huge， a huge jump。嗯。It's a little bit expensive。

 So the other thing you might be thinking about is。In the earlier example。

When I had a static library， it was called current instruction plus 7。Okay。

 it was a five by instruction。In this case， we've got。An indirect call and then a jump。

 And then we've got some data It's got the 64 bit addressing。

So you're paying a bit of cost for the flexibility of a shared library。And the other thing is。

 as I said， there's nothing obvious linking the name of the symbol that you're calling with the name of the shared library it's in。

Which is both good and bad。The second thing， though， is that you can also do this resolution lazily。

So， we've got this call to。PLT entry。 and in there it does an indirect jump to something in the data segment。

 Now， what we can put in here is some code that resolves where the function is at runtime。

So now you don't actually need to resolve all the addresses when you load the program。

 you can do them on the first call。Is that good or bad？Yes， yes。We'll come back to that in a minute。

And the other thing is the only bytes， again that change in the executable program are the bytes in the global offset table。

 which is where it stuffs in the 64 bit addresses of all the targets。

 So all the other bits of data in your executable don't change the code doesn't change know the read only data doesn't change just this global offset table。

On Windows， it's similar but different。It also contains a reference in the metadata in the executable to help adopt DL。

😊，Or clear so far。 it also contains a reference to their function。 Help avoid again。

 the demangled name。 It actually has the， the fully mangled name， but that's。Unhelpful。

Jing starts out。The loader loads the shared library Helper and looks for its sported symbols for the helper function。

 because。It's actually tied the helper function to the shared library， helper dot DLL。

 It will only find it in that one shared library。Which makes life。Easier in some regard。

 because it means if you fail to find a symbol， you know which D LL it is。

You were expecting to find it。As above， it gets to virtualr Je the Helper。

 it puts in some data section in the code and the call does something very similar。So。

 we end up with。Calling that。 And that's a jump to an indirect pointer。 And again。

 the data for that is the actual 64 bit address of the target。And as a relative call， this one is。

 well， it's only a few bits bigger than 32 bits， but it still wouldn't fit in a 32 B relative offset。

So， just to kind of。High level summary。 I I quite like the way winners does it because you have the clear indication of which symbols in the excutable come from which library。

So if you get a problem， you know which library to look in with the GCC model。

 if you get a missing symbol at startup。You've got to work out which of the 27 shared libraries you were expecting to find it in。

Which can be quite painful。 Also， you're much less likely to get a conflict。

Because you've got to get two symbols of the same name in the same shared library with the Windows model。

In both cases， the resulting in code ends up very similar， some sort of jump， an indirect call。

So one of the problems with the Linux models， which fortunately we can work around。

 is simple table from the shared library includes loads of things。

 some of which are not expecting anyone to call。Sometimes you definitely don't want people to call outside your shared library so we want a way of restricting that set and the second thing is that if we're not careful calls to local symbols aren't optimized because we're going to put the same logic in for any call。

So we've got a call to a local symbol， it's only seven bytes further on。

But we do all this jump of doing an indirect call and a 64 bit jump for no purpose。

So GCC since 424 has supported a visibility attribute who's come across visibility attribute？

That's good。It comes under the category of strongly recommended， which is。

Not that many attributes that I've seen strongly recommended by GCC。 So what you do is you。

Mark the things that you want to share as attribute， visibility default。

And he mark the things that you want to hide。Unsurprisingly， as hidden。

Don't actually often do this bit， because what you can do is set the default visibility to hidden。

 So everything is hidden by default。嗯。That's the way I tend to use it。

 Other people do it differently。So what you typically do is you set the default visibility attribute on the interface to your shared library。

And you compile everything with everything by default being hidden。

 and now when you link your shared library together。

 you only get a very small number of symbols exported。

Whi is good from a point of view of avoiding conflicts。

 good from a point of view of reducing the size of things。

 good from the point of view of reducing the cost of starting up because you've got much smaller symbol tables to look through。

And also， it means that the compiler and linker know that the symbol you're calling can only be within the shared library so it can make the code do。

Short jumps， short calls and optimize a whole lot of stuff out。

And if you're doing code that's compileilable on Windows and Linux。

 which is getting remarkably common， you typically have something a bit like this in a header file somewhere。

 so you say if you're on Windows， then define export and import as the appropriate magical keywords for Windows。

 otherwise if you're on Linux， define import and export as default visibility and math。

Nothing special for import。 And if you're on something else， then。I don't know what that is。

 don't do anything。And then you mark the。Again， in， in a specific header for your。Helper。

 some attribute header， which is either export， import or blank。

 in the case where you're compiling as a share static library rather than。Shared library。

 And then you put that。Thing a macro on the front of your function。

And then we just pass the appropriate definitions in when we build。And use the code。啊。

I forget what the second example was supposed to show its using it。 the import head helper。

So if you mark a code as DLL import on Windows， you get slightly different code changes because it knows if it's marked DL import in the header。

 that it must come from a shared library。So， it just puts in the。Into the object module。

 the indirect call straight away via a 64 bit address。So it cuts out the jump。Which can be helpful。

It it makes this instruction is one by longer， but you're saving the trampoline。

 and if you've got instruction cash pressure， that's one more bit of code that doesn't need to be in the instruction cache。

Right， one definition rule， who's heard of that？😊，Who loves it？Yeah， who hates it。

 probably the same hands。For any definable item D with definitions in multiple translation units。

 if D is a non in line non templated function or variable。

 or if the definitions in different translation units do not satisfy the following requirements。

 dot dot dot dot dot， the program is ill formed。But sadly。

 a diagnostic is only required if the definable item is attached。Conditions。

So you get these nondiaaggnosable。ODR violations， which can cause life to be interesting。Now。

 there's multiple things that are definable items。 Funs is just one of them。

 I really thought I'd cover functions and classes。 And looking at the time， I， there wasn't。

 wasn't time。 I did write an article for Seaview in 2015 about using the。

LTO optr and WODR on GCC to find some of the problems with classes that have got different definitions of different translation units so if you're interested in the class side you can have a look at that if you've got an old copy of Cview floating around or if you're a member of AQ you can look at it on the web or if you're not a member of AQ you can join Acu or you can follow the article link which will be on the slides。

So a simple example of ODR。 I， I declare a function F， which says I'm F in main。嗯。그고。In Ma I call F。

 I then go call helper and then in another function in another source file。

 I declare F as F in helper。 CPP and I've got two functions with the same name in the same namespace。

 different contents， it's ODR violation。Okay， that's bad。 We all agree。 What will happen in practice。

It will complain。Maybe。Yeah， so static， static linking。

We try to make one executable from helpper dot CPP and main dot CPP。And it's ill formed。

 standard guarantees it's ill formed in theory。Given the stuff in the standard wording。

 you could just say it's a form， but I'm not going to tell you。

You'll find out when you try running it。Or not。 But， in fact， both environments。

 you get a link failure。Because in both cases you've defined something and it's seeing both of them at the same time in two different object files。

 it just says you can't do that that's illegal and you get a link of failure so and this one actually tells you you know first you find here and I can't find it here and that also says already defined in main org so you know。

Where you are and where else it's defined。 And then you can look at the source code and decide， okay。

 which of these is right， Which one do I want to keep。Or do I need to just make some changes。

 put one in a name space， whatever？And if we put it in a static library。

 we typically get the same error。If I think statically。

 I get a complaint out of the I created a simple static library with it in， and I get a complaint。

 multiple definition。 And again， on Windows with a static library， I again get an already different。

Defined error out， so。In this simple case， it's great。 It， It doesn't link。Which， which is nice。 but。

Dynamic libraries， shared libraries。 they're fun， aren't they。

So if we link dynamically against Libhelper or SO where I've got the same function F。

 I don't get any errors or warnings， it just links。Great。😊，What do I get at runtime？Any guesses。

The one call from helper is called from Helper。Ones call for Maine call for Maine。 That's one option。

 They're both there and the resultant excutable that the。

 the F implementation is present in Maine and the F implementation in helper is present in the shared library。

 Which one gets called in other ones。It depends random it depends random， Yeah， it can well depend。

What I did when I tried it。Was I that。F in Maine called， and then in helper I get F in Ma called。

This may surprise you。What happens here is。The loader starts。 It loads the main。

 It starts building up a symbol table。 The symbol table contains F。 It loads the shared library。

 It finds a reference to F。 It says， I've got one of those already。 Oh， well。Ignores it。

 And now the symbol table just contains the F in main。Now， the shared library loads are。

 and we haven't done anything about visibility。 So it looks。When it loads the shared library。

 where's this F function of which you speak。Oh， it's over here in Maine。So it calls the one in Ma。😊。

Do you think that was what you wanted。Possibly not， because you've now called in your shared library。

 which a different team or different person completely could have written。

 You've now called a function in the main program。But if the main program didn't have an F。

 you'd call the one back in the shared library。 That's fun， isn't it。So。

You set up with visibility as I looked at before and on Windows again。

 by default things are hidden so now the shared library looks within the shared library for F and the main program looks within the main program for F and we get what we would hope probably in Maine。

 we call the F in Maine in helper， we get the F in helper。Except， of course。

 now we do actually have an ODR violation。We've called the same function in the same namespace with the same name and the same arguments and got two completely different outputs。

So is that a step forward？带概。And。It's quite valid from a C+ plus point of view that you could end up just the program could terminate。

 could just say you're being bad。I don't know of any implementations is that do that。

 but there's no reason why they couldn't。And then you have the ODR and templates。 Now。

 function templates a great fine。 mean， they're normally designed to go in a header。

 and you instantiate them when they're needed。And you've got a header that's shared by 6 or7 source files。

 and they all instantiate the same template instantiation from the same definition。

 So everything's cool。 But it means each object modules got a definition of that template function。

So they get marked as。Just pick one。And the compiler sort of trusts you to make sure they're all the same。

那。Well， sometimes they are。This make it rather hard to detect ODR violations。 Now， in Syria。

 compiler could be very clever， and it could keep a reference of exactly what the function looks like。

Whatever that means I'm not quite sure and then say。

 well I've got six object modules with the same functioning。

 does the content look the same and all they're not the same raising an ODR violation。

 I'm not aware of any compilers that do that there may be， but I've not ever used them。

So you've got to be a little bit careful with function templates if you end up with somehow getting a different definition of the function template。

 and then you instantiate it in two translation units and it will link without any errors。

 and it will pick one of them。Which one？The one。So here's an example， we start out。

 we've made our F into a function template with a defaulted argument。

Just to mean the rest of the code can stay the same and again。

 our other function has exactly the same defaulted argument and different contents。

 so we've got an ODR violation all and what happens now is we can compile and link without any problems whatsoever。

😊，Nobody complains， we just get main dot CPP， main dot CPP。

And what is happening is the linker is picking one of them。 And in the cases I've tried。

 it's picked the one from main do CPP。 And I think what happens is I put main on the line first。

And it loads that in， and then it gets to help her and it picks it all， he says。

 I've seen that template staiation， don't bother about it because if I swap the order around。

 I get a different output。Which。If you're using a build system that generates the list of object modules。

Sort of make time。And it's not alphabetically sorted， but sorted by something else。

 It means you might get different behavior between different invocations of your build system。

So this is a bit unhappy。So yeah， that's what I got when I changed the order。

Now if I compilely with optimization， 01。😊，I nowga， Effin May， Effin helper。

Because the compiler has inline。The function template。Into the actual function that's calling it。

And there is nothing for the linker to do。So you've now got two separate instantis of F of end。

 but they're in line， they're not actually a single function。

And you can then surface its problems if you assume that the definition is available。

 So if you have written code that knows that something in your system calls the function with the template instant staiation in。

 and then somewhere else you call it without having the definition available， it will probably work。

Until you start optimizing， and then the compiler throws away the actual function definition because all the uses of it are in line。

 and now you get an undefined reference。So。What I can do is in Maine。

 I can take out the implementation and just rely on finding it somewhere else。Which is fine。

And I compile it with no optimization and links on GCC and MSV， and even with high optimization。

 links on MSVC， and then I try it with01 on GCC， and I get an undefined reference to void F event。

Because I need to explicitly instantiate the template with。One is the appropriate syntaaxxies。

I think we'll skip over to that one and we'll get down to ODR and template to shared libraries because that's even more fun。

So I put the helper。cPP for the previous example into a shared library。

Now we get some slightly different behavior。😊，Again， without optimization and without any visibility。

 I get F in Maine， F in Maine from both so again the shared library is finding the template instantiation in Maine at load time。

And if I change it to hidden visibility or compile it a link with MSVC， I get。F in Maine。

 because that's the one that Maine can find。 And in helper， I find the F in helper。

So a bit like the example with the the free function。And again。

 it's because the instantiation is found and resolved purely locally within the shared library when the visibility is set。

Now we have fun， when we。Have both inlining and。Functions。So， I now。

Use FN as a alias for a function returning void， and I set P F to be F of template function。

 and I print out calling the function and Ill give it the address of the function I'm calling。

And then I call the function through。PF， okay？We're not optimizing。And linking statically。

 we get what we expect EffI Ma calling a function at some address， E in Ma， same function。

 E Ma calling function at same address。F in name。Yay， we're good。As before。

 it's just because there are two instantis of the function template and the link is pick one。

In this particular case， you have to go to02 or above or an MSVC， just01。 And now I get in main。

 F in main， calling the function of this address， F in main in the helper， F in helper。

 calling the function at all the same address。 and want to actually call the function through the function pointer。

I get the one in helper。That's clever， isn't it？What's happening is the compiler is very clever。

 and it says， you've got a function pointer。That you've set up and initialized。Just going back to it。

 Only my mouth seems to have decided not to。Want to do that。

You've set up a function pointer here to F。 It， it's a local variable on the stack。

 And then you've called through point to function。 I know which F you mean。 I can inline that call。

So it actually replaces the call to the function pointer。With the inlined template。

That it found further up in the source code， but this one actually has to go and find a genuine function。

 and it finds the function in in main。Which means if you're trying to debug these sort of problems and you start printing out the function addresses。

 it doesn't always help。So you have to be a little bit cleverer。Confuse the optimizer。By。

 for example， I just passed in a flag。And so it now says， well。

 I don't actually know whether you're going to call F or G。So， I won't optimize it。Well。

 not this week。 Of course， a cleverer optimizer could say if the flag is set， then call the function。

 otherwise inline it。So I still might be hoed because in liing。I'll skip the delayed loading。Hi。

 Jacking。Once you've got shared libraries， symbols are resolved when you run the program。

So you might get something other than you expected。Possibly for good reasons。Possibly not。

With great power comes great responsibility。So just to be aware， this is an option。

 So on both platforms， you can replace one shared library with another shared library of the same name。

Obviously， it's just a file。Withs a completely different implementation。

And that mostly is quite a good thing， means you can update your shared library and everyone using that shared library now gets the bug fix。

 or you can have a debug version with extra purchasing it。It also means of course。

 that somebody else。Can put a shared library。In your path somewhere with the same name。

 and you'll now load that one rather than yours and who knows what that does。

You can often do this without actually touching anything on the file system。

But just putting it somewhere and then fiddling with these environment variabless， I mentioned。

 path and L library path。 So now suddenly， your program goes off loads some other piece of。

But malicious code， rather than the shared library you're expecting。

And both windows and Linux have got a variety of ways of preventing this in various more secure environments。

😊，If you need to worry about that sort of security。

 you need to know a little bit about how that works。And Linux programs， as I said。

 use this shared symbol map， so you can also just load anything。

That happens to define a symbol early enough in the process。

 and it will take over hijack the symbol that you were expecting to use。

And there's an environment variable LD preload that's actually defined。 just let you do this。

So the loader starts out by loading anything in LD preload and， and populates the symbol table。

 And then it does the rest of the things you want。 So if I create a little function helper。

It says hi， Jack，Couldpart that as a shared library。And drop it in。With LD preload。

 I go into mainine and rather than printing out Ho world， I print out hijack。哎。嗯。That can be really。

 really useful。Also can be really， really scary depending on who wrote the injected shared library。

 So if you've got a program where you let other people define environment variables。

 this is one you might want to not let them define or at least be a little bit careful about what they put in LD preload。

You can also wrap the function。Which is what you typically do when you're using this for for kind of good purposes。

 So I've got my helper function， and I want to do something around it。 It doesn't work correctly。

 I want to add extra diagnostics or something like that。 So what I can do is I can use the。

Dynamic library runtime call， D L S， saying， find me the next definition of this symbol。

 I've got to use the unmangled name here after after mine。And it will give me back the address of。

The next instance of helper。 And now I can。Call the original function。

So if I use this wrapper function with L preload， I can see wrapping coming out from here。

 followed by the original call to Hello world。嗯。発生も？Yes， in general， you'd obviously you'd cash this。

 etc cetera。 I mean， it's expensive to call this every single time。yeah。

I could have made that static， I suppose。And this also gives you the option that if you don't find another symbol。

 you can do something else。Rather than just falling out of the sky。

So my kind of conclusion is that the basic process of taking source code。

 compiling it to object files， putting them into libraries， whether static or shared。

 and linking the whole thing together and running it on Windows and Linux。

 they've got a lot of similarities。But there are one or two differences that become。

 can become quite important。 and it's useful to know about this sort of stuff。

It's also useful to know about making symbols hidden。

With the visibility flag on GCC and also to think about ODR violations and making sure that things are properly hidden away。

 So using anonymous namespaces， putting things inside other namespaces is a really useful technique It's very common I've found with people write tests they write helper functions for the tests。

 they don't think about it very carefully， they use some sort of helper template and lo and behold。

 when you link all the programs together， you discover that this one helper function is being instantiated in three or four different tests and one of them is being used。

And where things happen。And ODR violations are sadly， quite hard to track down。

So the compiler and Lier tries to help you， but as we've seen with tick shared libraries。

 it's really tricky for them and for us to resolve them。Okay。

We got that five minutes to go for any questions or comments。啱。👏谢。



![](img/98029beef01d55c3107916ed8455d3ff_2.png)