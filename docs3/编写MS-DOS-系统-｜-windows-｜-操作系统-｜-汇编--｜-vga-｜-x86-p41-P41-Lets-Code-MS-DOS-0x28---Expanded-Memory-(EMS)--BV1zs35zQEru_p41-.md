# 编写MS-DOS-系统-｜-windows-｜-操作系统-｜-汇编--｜-vga-｜-x86-p41-P41-Lets-Code-MS-DOS-0x28---Expanded-Memory-(EMS)--BV1zs35zQEru_p41-

Hello， welcome and an excellent evening today we want to talk about exponed memory for MSTs。Well。

 the issue with the original PC was that the 8088 and also its slightly bigger brother the 8086 had 20 address lines which could address up to 2 to the power of 20 bytes that is exactly1 megabyte。

The upper 384 kB were used for Ro extensions， the Um and the bias at the top of the memory。

There was no way to address more memory using the CPU that changed with later CPUus， the 8286。

 and the 8386 enhanced this to 16 MB first and then to 4 GB。However。

 the old piecess were already hitting some of their limitations， basically。By。Yeah。

 having only 640K of usable Ram for programs。And that was an issue。

 And there was an issue that was addressed by certain companies， most。At the forefront was Lotus。

 who produced the Lotus 1，2，3。Software， which was basically the Excel of its day。

 one of the predecessors of Excel。 So a spreadsheet that was heavily used。

And Infill was also interested in getting more Ramm into these legacy systems and Microsoft as well。

 because they were also sending a lot of software。 So those three companies got together to produce the LI M standard for Lotus Intel and Microsoft。

Which defined a standard way to have so called expoundent memory。

Expent memory would normally be on an extra IA slot card in the original PC and X C。

And that count would come with up to multiple megabytes of Ram。

That would be bank switched into a certain frame in the upper parts of the memory， an unused segment。

 usually unused segment between D 0，0，0 hex and E 0，0，0 hex。

And you could talk to this card via a certain device driver as standardized API。

 which was accessible via the interruptrupt 67。There would be a lot of different sub functionss。

 depending on the standard and to query the size of the expansion memory card。Et cetera， et cetera。

 You could allocate memory， free memory， stuff like that。 And also， you could take the。

Single so called pages，16 k pages of the expand memory and bank switch them into this。

Page frame at S。 You would have four different pages and once visible inside of the normal memory。

 And if you wanted to see something else from the expanded memory， you would call the function 44。

 for example， map logical page into physical page window。

 and you could select one of the pages that you allocated and have it visible。So far so good。

 later versions of MSs Dos came with a so called expanded memory manager， EMM 386。

 which emulated these hardware cards and allowed legacy software to utilize the expanded memory。In。

Basically， software emulation。 If you had more than 1 MBby on your 386， the E M M 386 would。

Use the protected mode and the virtual 8086 mode to。

Simulate access to this hardware via other device driver and map。

Memory from the 4 GB of address space that the 36 had into this pay frame。

So why do we want to look at the Ems Well， because it's the expand memory that works on all systems down to the very first PC。

 so you can write MSO software with more than 640 kilobs of RA。Let's say even a couple of megabytes。

 for example， sound data or graphics data or level data， whatever， to have quicker load times。

 for example， because switching in bank switch memory is much faster than reloading from disk or。

Even floppy disk， maybe。So it's quite interesting to see that。

 And you can still stick with all the known stuff that we have。

 You don't need to deal with the protected mode switching back and forth between protected and real mode and stuff like that。

There's also a different standard， the extended member standard XMS。

 which we might take a look in a future episode， but today we want to stick with EMs， good old Ems。

And for that， we will have a look at the different functions that we have here。

I have taken the source code from the PC in turn。Booked by Databecker or in the US。

 I think it was Epicus。 And they have a chapter on E， M。 S and X M S。

 and I've taken the source code because there's really not that much to it。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_1.png)

And put it into an example program of my own。Wwhichch we use to plain animation that doesn't fit in normal memory and couldn't be decoded quickly enough。

 at least not with our very slow G decoder that we coded a couple of years back so I have a main loop here that loads all the G files into EMS memory and then copies them frame by frame into the VGA memory and we will fill out all these nice little functions to handle the EmS memory。

And I'll talk you through that。 It's no big deal。 It's just calling a couple of these interrupt 67 functions。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_3.png)

And that's actually it。 So let's get right to it。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_5.png)

First part of business is to see whether the expanded memory driver is actually installed。

And we can do this by checking at a certain memory location if there is a magic string。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_7.png)

This is actually also explained in the PC and turn book。

You basically fetch the segment address of the interrupt handler for interrupt 67 hexadeademal。

 which is the interrupt for the expanded memory manager。And if it's installed。

 then there will be a string， a magic string at memory location 10。

With this exact thing here with the0 at the end。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_9.png)

So， yeah， we can definitely check for that。So。Let's do it something like。That。Just we can。

 I think we can even use。Something like this。It should be possible。

 And we will have to get a couple of。Register unions， first of all。A reunion of registers， and some。

Segment registers that we can engage。As well。Let's call this S re。

And then we are going to use the interrupt。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_11.png)

The dots interrupt 21。Which we should have a documentation of here。

 and there is a function number 35。Exxiadeal and you put into A H， you put 35 xx。

 and then the interrupt recangle number， and you will get back in E S and B X。

 the point to the interrupt handler， which is。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_13.png)

The basically the API point for the EMM driver。So we say rex H dot Ah equals 0 x 35。

 This is a function that we're calling。And rex， dot H， dot A O。equals。EMS S endt。

 and I defined that up here that E S and0 x 67。 So you could also write that， of course。

And then theres a function called in dos x。Which lets you specify input and output registers。

 We can look that up in the header files。In dos do age， you will have in dos X。

 and there will be input registers， output registers and a bunch of segment registers that are not part of the union res。

 The union res only has the general purpose registers， basically in word and by sizes。Obviously。

 the word sizes being A X， B， X， E X， D X plus the index regis， the flags。The carry flag。

 I think that might be probably in the flags。And the bid registers will be the high and low parts of three journal purpose registers。

And the segment registerants are in the structure as res。Obviously。嗯。I think that should be it。Yeah。

 that looks good。 And then we just compare with Mecom。Creating a far pointer。Using the make FP macro。

From the return value as re is。And the address 10 as written here in the documentation at location starting at 10。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_15.png)

![](img/ce8475ab5dbd1304bea8baf2cdafce72_16.png)

This gives us the Power pointer looking right onto the place where there should be the E M string。

 and we compare with E M name。And。Yeah， we should use a string length here， I think。

That should hopefully， do the trick。See if this compiles， there will probably ton of warnings。

Because we never use this stuff。 But that should actually already。Function， just fine， I hope。

The E M S error function I just copied from piece in turn because that's just typing off a lot of error messages。

 There are different error codes that you can get back illegal hand， etc cea， etc cetera， etc cetera。

 More pages requested than physically present， etc cetera， so。You can read through that afterwards。

 but we are not quite that interested in that。However。

 it's good to know how to get how many pages the expansion board actually has or the E M86 driver provides because it is user configurable and how many are free because there might be some device drivers like Smartri that are already using those pages。

And where exactly in memory the segment is， because。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_18.png)

![](img/ce8475ab5dbd1304bea8baf2cdafce72_19.png)

It might not be at D000 but somewhere else if the user configured it as such。

 So there those are the things that we need to check。

 Let's go back to the functions here get page count。

 so this should be our function that we want to implement and the ways this works is always the same。

 We again need a union of registers。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_21.png)

![](img/ce8475ab5dbd1304bea8baf2cdafce72_22.png)

Then we fill up what was it。 Let's have look， Ah with 24 he。 So Ah equals the x42。And then we call。

The regular interrupt。With the input and output registers。And that's it。 And then we will compare。

The error code。 So this is our global error code that I defined up here。E MEEC。

Equals rex dot H dot ah。And we actually have to silence the warning。 So we cast this to an integer。

And。If that is the case， we return Emarrow。To signal the call that it should probably quit or at least print out the arrow。

Else， we have the。Actual number in。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_24.png)

Bx。And this is exactly what's written here， H equals0 on success， otherwise we have an error code。

Which we can translate with the error function above and B。

 X is number of unallocated or available pages。嗯。And actually， we should return D X， not Bx。

 but as you can already see。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_26.png)

The B， X is exactly what we need for the next function for the free pages。

So we can just copy this whole thing。And return B， X instead that very simple。

 And that's why there's not much use in reformulating this， because it's always the same thing。

 basically。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_28.png)

That is fine。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_30.png)

More interesting， perhaps is a little bit。 the next part， the frame segment。 but actually， we can。

 we can actually。Copy this as well。 let's see。Reactivate this。嗯。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_32.png)

OrSomething like this。So the frame segment， getting the frame segment， where does it say。

 get page frame base address。 So this is function 41 hex。

Same A H returns thearrow code and B access the segment of the page frame， so。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_34.png)

啊。It's again， copy and paste， a very simple， very straightforward。Allocating pages。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_36.png)

Let's see。Maological page get handle and allocate pages。 that is exactly what we want。 This is 43。

 And the idea here is you can do multiple allocations and it will return a handle to that particular allocation。

But you can also just go ahead and allocate。However much you wanna need。Or use in your program。

 you can just say， okay， I'm taking。Let's say1 megabyte or2 megabytes in one go and be done with it。

And since pages are， I think，16 kilobys in size， you can do some calculation。1024 kB in a。

Mgabyte divided by 16。 that would， for example， mean that you require 64 pages if you want to have one megaby of ES。

And try to do that。 Of course， you should。In advance， check if there are enough pages available。

 which I think we don't do in the program below。 so we might want to check that。

 but I think I'm checking for errors so there will be a useful error message for sure。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_38.png)

嗯。Nevertheless， we can。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_40.png)

Again， copy this stuff。Now we have function 43 if I remember correctly， and we will get back in E。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_42.png)

M Hand， which is basically just a number， like the ticket that I mentioned earlier。

Forgetting your code back， physically or。Your allocation and also to free the allocation。

 So that's very simple。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_44.png)

嗯。The mapping， mapping logical pages into the physical page window。

Here you will give the physical page number。 There are four in in the window， as you can see here，1。

2，3，1，2，3，4， or 0，1，2，32 B exact because it's 0 index。

And then the logical page number from your allocation。Identified by the handle。 So we need。

To fill up AH，L， BX and Dx， just like that。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_46.png)

So function number is 44。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_48.png)

And then。We have AO。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_50.png)

With the， oh， this is the allocation。 Yeah， okay， let's copy that down to the mapping。

 because we were。Talking about the mapping。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_52.png)

Was it， What was it before， What was it before。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_54.png)

43。O。So this is looking better。 So we have the handle that we go back from the allocation。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_56.png)

And we have the。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_58.png)

A physicalhys page number。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_60.png)

Hey l。And then we need the logical page number in Bx， x dot Bx。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_62.png)

![](img/ce8475ab5dbd1304bea8baf2cdafce72_63.png)

Is the logical page number。 And then in。D X， we put the handle。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_65.png)

So A H will return again， the success code or the error code， and which means。That we are actually。

Don't need。Any of that。 But we can shorten this to。A boion that I thought would be fine here。So， we。

Basically。Sa。In anarrow code。Is assigned。 And if that is。0。

 we will turn true because there was no error。 so we negated。And otherwise， we return。

Something not zero， which maps to pullole and true， basically。Which is fine。 So this is much simpler。

 so we can now。Free pages。 allocate pages。Map pages。Oh， no， we can query the free pages。

 We can query the number of pages。And of course， we also need to return the pages and here something very important is to be noted。

If。You do something like malloc。And then quit the program。

The memory will actually be returned upon quitting。 That is part of what。

And as those does for you when you quit the program。

There are ways to allocate memory and not have it returned， but that's usually not the case。

 When you quit a program， memory is returned to the operating system M does in this case。With E M S。

 that's not the case because the E M S driver doesn't know when your program quits。So。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_67.png)

You have to always call Em S free to release the memory pages that you allocated。

 or it will not be usable by the next program。That is being sudden。

 you will have basically memory leak。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_69.png)

So you do this with function 45。And it has the same structure as， for example， the E M S alloc。

 obviously， except that it's not。Oh， we forgot also to put the pages in here。

 we'll fix that real quick。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_71.png)

But first， let's do this。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_73.png)

Release handle and memory pages。 this just takes the handle， obviously。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_75.png)

So this is function 45。And。We will need in Dx or X， let's turn this off。And Dx the handle。

And then we'll call the function， and。The Eagle eyed viewers will have seen that the allocation。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_77.png)

![](img/ce8475ab5dbd1304bea8baf2cdafce72_78.png)

Needs in Bx， the number of logical pages to allocate。 So let's do that。

 And let's quickly check if we forgot anything else， so。

The number of three pages doesn't take anything。 number of pages， number of three pages。

 frame segment doesn't take anything。 So it's only As Aloc that we forgot。

That requires the number of pages that you want to have in BX。

The mapping we did correctly and the freeing as well。

And there's one more function that is of interest， because there are more functions that you could use。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_80.png)

嗯。Qurying certain things， I'm not sure this is even an older version， as you can see。

There is sometimes there's no version number up here in， in the function。But for example。

 if we say get page frame based address， this is only available in driver supporting E M S 3。

0 or higher。 Usually will see version 3。2， but there are new versions that are。Version 4。

And I'm thinking about which。For example， this year get expandedound memory hardware information。

 this is actually 4。0 or higher。We are sticking with 3。2 here， nothing that we're using is。

 I think in 3。2 reallocation of pages， for example。

 is a similar function that is only available for and higher and and for you can。

 I think even move around the exchange memory regions exactly。And you can change。

 You can move around the。Why do you have it， The M。

 S window so that it doesn't sit in the place that is given by the driver。

 but you can move it around。But this is something that we don't want to do here。

 So it's still a nice feature to get the version。Which is function 46， as you can see here。

 and it will return in A L D M M version as a binary coded decimal。

 which sounds fancier than it actually is。 The return value is stored as a B D。

 a binary coded decimal， which means that you have。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_82.png)

The2 digits of a two digit decimal number， like 10 or 99 or whatever。

 in the higher and lower nibble that is for bits of the by in A L。

So what we can do is we can mask out the lower。4our bits by doing logical end with0 X F or 15 decimal。

And we add to that， the。4 bits to the right shifted value。Which is the higher four bits。

And we have to take that and actually multiply that by 10， because that is。Basically， the tens。

And then you have a regular number stored in one B instead of the binary decimal。

The manual coded decimals were used quite often in the early days of computing。

 but are more or less obsolete， I would say。Next up are two functions in EMS and clear EMS。

Maybe the clear mess is actually simpler， so I'm going to do that first。Actually。

 we're going to call free Ems。On our。On our E M hand。Because we only have one allocation， and。

If you have more allocation， you would free them all。And compare that。 And for。

Suppressing the warnings we're doing cast to in here。And otherwise， if that doesn't work。

 we are just going to print out the error code right way。

Because this will be something more or less fatal because we can't feel the memory。嗯。

Then we have that okay， in Bm。We need to do a bunch of things， or we can do a bunch of things。

 I'm going to put in some stuff here that is not strictly necessary， but that's interesting to see。

So we're going to have。Some variables for the number of pages that are in the system。

The free pages and the version of the EmM driver。Then we're first gonna call the E。

 M S installed function。 And if that isn't even available， we will do。An error message。

Something like no E M S driver installer。Or detect it。Just like that。

 and we'll exit with an error code。And elses， we will print。MSs driver detector。Just like that。

 And we'll continue our work。We will read out the EMF driver version。Nm。Any quotes。EMS version。

 that is a function that we already coded。And we will see that this is。嗯。

If this is equal to the error code， -1。Then， we will。Print the error message that the driver gave us。

And return。What else？We got a print version number。US erosion。Percent D dot person D。

 And now we can use this binary code decimal that we converted to a regular format。

And we can get the first version part by dividing by 10。

And the second version part by doing modular 10， which gives us。The what tens and the ones。

 basically。And this will give us a very nice version number， indeed。嗯。Yeah， I think that's good。

There we can query the number of pages available。Something like that。And of numb pages。

Is not equal to the M  error code that we can print it actually out。Presentee， the mess pages。瞅瞅。

No pages。And no it'。We will print the error code。You see the principle here is always the same。

Same goes for three pages。 Let's just copy this。It is very similar。I I go here， Three pages。And also。

 check for that。Percent S pages。Free and we will also write how many bytes that is。Just。

To be very clear。嗯。NotNo pages， but free pages。We get the number of。

Free pages by multiplying by EMs page size。Which are defined above as 16384。And that's that。

And then we will also allocate the memory that we need。That will be M S hallloc。

Four times number of frames。 So the idea here being each of our VGA mode 13 frames is 60 exactly 64000 bytes。

And yet， four pages are a little bit more。 but for simplicity reasons， I said， well， let's take 60。

Fre 64 kiloBs， exactly。Of size for each frame。 So we have four times n frames。

 and we'll try to acquire that。In total， it will be slightly more than2 MBby。

 So you will be able to run this on any machine that has。At least 2。5 mebytes of expand memory。

 for example， every4 megabyte machine should be able to do that properly set up every 386 at least or 286 was a certain driver。

Do box out of the box will definitely run。 and usually has 8 MBby of E， M S memory available。

In the default conversion， I think。So that should be fine。Again， checking for errors here。

Just the usual printing out error code， which might， for example。

 here be that we try to acquire more pages than are available。And we also need to have the。

Page segment。Which we can also get here。And let's copy that too。

And that is our initialization routine， actually。Should be fine。 You can still try to boot。

 And there are a couple of errors where I forgot things。 There is a semicode on'm missing。

This year is complaining a little bit incorrect assignment， Yeah， but actually we want that。嗯。We can。

 probably。Avoid this。By doing some kind of。Let's perhaps cast this to Boa。Does this silence the。No。

 this were not silence。We probably have to。No， it definitely wants to have this in its own return code。

哎。Maybe we can do that。Yeah， let's just do that。Return， not E M M， E C， that should。

 that should silence this warning。 Yes， perfect。嗯。Here's a typo。And。Here's also the typo。

Out of rangeing comparison， there is another thing。 Let's see what we can do about this。

We need to do a little cast here。And that's okay。 The rest are the warnings。

That are due to not implemented yet。So during the load， let's go down here。The loading of the G。

 we are trying to load the give， and then we will copy the image data from the。

Current gi file into Em， M。 S memory。At physical， neuro logical。Logical page number， I guess。

Or physical H number。I times4 because we always need four pages。

 so it will copy to the next four consecutive pages。And do the me copy， basically。Of the palette。

 because we also need one palelleette per。Frame that will not be in the E M。 S。 actually。

 I have created。A large array for all the。Plls here， bite pells number frames times 768。

 We could put that into em M S as well。 That might be an optimization。

 but it's only a couple of kilobys。 So I didn't bother to do that。So how do we do the copy？

rather simple， we need an error code。 We need some iteration variable。

And then we will do for I equals n because n is the starting frame that we're copying from。2。

10 plus size divided by。Yes M page。Size plus one， for example， if we have 64000 bytes。

 64000 bytes divided by 16，384 will give us 3。9 or 3 in integer， so we need to add one more。

We will do plus plus I， and we will also increment the source pointer to be able to。Do the copying。

And we will nap。He single。Page。MM handle。Comma I comma0。 We will always take the。I。

Page and map to the。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_84.png)

Page number zero in the window， you could also map all four consecutive pages and do one mem copy。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_86.png)

That is a bit up to you。 you can do this optimization。Might be slightly faster， but。

Probably hardly measurable。We have to check for an  error。If there is an error。

 we will need to return to text mode， otherwise it will look very weird and then error out of the program。

However， if it works， we can do a。Mm copy by calling the Ems。Page macro4。The frame page。0。

 and the source is our source pointer， which gets incremented for every four copies。

By the actual page size。And that's also what we are doing。 Actually， the size here is incorrect。

 This needs to be M S page。Size。So， that should。Do the trick， I think。嗯。That should be fine。

And it's actually。Maybe a little bit。Too much。 maybe we should rather go by size。Let's， let's。

 let's do it like so。Let's introduce a variable K and K equals。Size divided by M S page size。Plus。

 one。So。That we it over I from。N to n plus k。And we increment by size， divided by。Key， because。

This will give us the actual 16000。Bys。So， we can。Do a much better。

Copy here without copying any extra bytes that we don't want to copy because we have a slight disagreement。

Our whole four frames， our whole four pages are 65536 or 64 kilobytes。

 but our data is actually only 64000。So that would be a slight optimization。

 Further optimization would be to map all four pages。

Because you have to call E S map four times anyway， and then do a mem copy。Of the whole size。

Which might actually be better， right？How would we do that， Maybe we'll do that right away。 We do。

 yeah， let's do， let's do that optimization as well。 So instead of that， we would go from。0，2， k。

Basically。And the source point， I would not be incremented。Instead， the。

Mm copy would go from E S page 0。Over the whole size， so it will write into pages1，2， and3 as well。

However。We would map。I plus。N， actually， the actual physical page a plus n into logic page I。

 So if we start off at page 10。Who had met。EMSS pages 10，11，12 and 13 into pages 0，1，2， and 3。

And that should actually be the most efficient way， because then we only have one mem copy call。

And 4 M S map chs。And K should be 4 because size divided by M page size plus one will be。

3 by 9 round down to3 plus  one gives us4。That should do it。 does it compile。

 No they have a couple of errors， expression syntax， Oh， because I mistyped。There's one more error。

3 E M。 S is not defined， which is a shame。And that is due to the fact that we either forgot it or it's called not。

Free m S but。Eam S free， obviously。So let's do that。 That's better。

 There are still a bunch of warnings， but those are from the uned copy from E M S。

 This is during the rendering loop。 we will copy the same stuff back。

 And the nice thing here is it is actually the very same function。Only with the。

Sos and destination point are reversed。So just like that。Where are done。So let's have a quick。

 very quick look on the MS page macro。Because that looks a bit weird。

 but it's actually rather simple。 It selects the。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_88.png)

Enth page where n can be between 0 and3 in the EM window。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_90.png)

And it will take。The Em M。 S frame segment that we acquired。And yeah。We should， actually。Don't make。

 we should make the call here。 We should use the page sec。Because that's much faster。

 We don't have to call this all the time。 So this is another optimization。

 This will save us quite a bit of time， not querying the E M S driver。嗯。

And we will make a far pointer with the M page segment。Plus， the。And。

Page basically shifted to the left by 10， because that's how far the segment segments are usually shifted in the word。

And the opposite will be 0， and this will create us a far pointer that we have to cast to。

To avoid Huntter to be able to use it for anything。And that should actually do the trick， hopefully。

Okay。Now comes the question， will it run First， let's quickly check our main function before we do that。

What we're actually doing first we should be seeing that we are clearing the screen。In it M S。

 which will print out a lot of information about the M S。 then it will。

Try to load the images and frames。 We can hit any key and it will abort after loading the next G file。

The G phone name will be in the subdirectory G。Netify MI IT dash and some number。

The load G function will actually print a little indicator。 I changed that from our previous version。

 I think that's in the next pixel function。 So if you check out the new code。

hair will be an indicator like a spinner， basically。

Which makes it more visible because the gift decoder is highly not optimizeimd。

So it's very slow and you will see how the progress is during the loading area， you will see it。

If the image loaded correctly， we will copy it to the E M S， exactly as we said to the。

It times fourth page。64000 bytes。 Then we will copy the palette。

 and then we will free the image because we need to make space for the next one。

 And this will continue in a loop。Then we'll go to graphics mode。

Weight for 7 frames so that we get 10 frames per second for 70 Hz refresh rate on the VJ。

Copy from E MS。The current frame to the VGA buffer and also set the pallet。

 this will lead to depending on how fast the copy can progress。

 this will lead to a little bit of arting in the palllets because the palllets will differ slightly between the G images。

We can only avoid this by going to mode X or mode Y and doing the palette setting in the vertical retrase。

You can do this as a homework basically， but you will have to adjust the ways that the images are put into memory by reshuffling the pixel so that you have it in the modX format。

 I didn't do that here， but you can try and do that for optimization purposes。

So let's try to see if it works。 There's an issue。 No E S driver detected。 So we have some error。

 So let's see what that error is。 Actually， very simple。 There was only three x。

 but it needs to be four x。 A thick that should work。 Yes it does。

 It says M S driver detected M S version 4。0。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_92.png)

1024 M S pages in total， and if forgot Himp extension and 944 E S pages free， which equates to 15。

4 MBby roughly。 And you can see it slowly loads using this nice indicator that you see that it's actually doing something。

And well just wait。 It will go to 35 to display the animation。Fast forward。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_94.png)

And there you go。We can now play an animation basically on any PC that has at least2。

 something megabytes of em or a do box that emulateates that without having to decode the data on the fly。

 we can preca this。 This is， of course， a not very useful example of this technology。

Probably you would rather use this for very large level sets or to swap in new graphics data for the current view of your game engine。

And maybe also for swapping in samples or music that are currently being used。

The nice thing here is that it runs on any PC that has eitherL a fitting card。

 an EMs card with an appropriate driver or on 286s。

 you can have emulators that use the extended memory to emulate EM or some chipets already support that and on 386s EMM386 is the default to do that。

 no need to switch to protected mode， which has different advantages。

 obviously but is also a little bit more difficult， perhaps to code for。

And especially it only runs on 386s and upwards， whereas this would run on any old PC。

Probably not with this performance， because the CPU would have a hard time pushing the 64 kB at 10 frames per second。

 probably not possible。 but you can imagine to use it anyway for large dataset sets and levels。

 etcter。So yeah， we can press escape here。To quickly recap。

 EMS has a so called page window usually at around D0，0，0 hex in the conventional memory。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_96.png)

It runs on any PC from the 888 onwards and uses a kind of bank switching。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_98.png)

And you can detect the driver by looking up the string EM for x and a0。

In the interop vectoror for interrupt 67 hex。You can query the number of pages and free pages。

 and there's also stuff for allocation， mapping and freeing。

And it always works in the same way by selecting the API function in the AH register。

 calling the interrupt and maybe passing around some parameters in the other general purpose registers。

 which you can look up in the specification basically。And other than that。

 it's very simple to map different。Pages from the EMs space into our conventional space into regular me copies。

You can， of course， also skip the M copypy if you don't need that， if you just need to look up stuff。

 you can directly use that。And yeah， it's actually a very simple mode of enhancing your。

Do programs with much more memory that you can probably ever use。

 but it's very useful for games for even for applications back in the day。

To store large amounts of data in a faster way than you could by using， for example， the。

Hart disk or the floppy， which were also very limited and expensive。So that's it for today。

 I think we can stop here gonna run the program again and。



![](img/ce8475ab5dbd1304bea8baf2cdafce72_100.png)

Shall like， subscribe to usual snuff。Everything else is in the video description linked to the source code so you can play with this program at home。

If you want to support me， there's also links to do that and other than that I want to say see in the next video and bye bye。

🎼Yeah。🎼。

![](img/ce8475ab5dbd1304bea8baf2cdafce72_102.png)

🎼，🎼The。🎼The。🎼，🎼，🎼。