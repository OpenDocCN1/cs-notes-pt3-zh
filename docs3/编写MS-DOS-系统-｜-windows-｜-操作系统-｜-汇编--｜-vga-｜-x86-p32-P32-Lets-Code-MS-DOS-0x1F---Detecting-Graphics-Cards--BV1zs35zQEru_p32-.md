# 编写MS-DOS-系统-｜-windows-｜-操作系统-｜-汇编--｜-vga-｜-x86-p32-P32-Lets-Code-MS-DOS-0x1F---Detecting-Graphics-Cards--BV1zs35zQEru_p32-

🎼。Hello， welcome and a very good evening and today on the Let's code and starss episode。

I want to talk a little bit about video cards or graphics cards。

And how to determine which graphics card is actually in the machine that you're currently coding for。

Because you have to know that the original IBM PC and everything that came after that， up until。

Perhaps the mid 90s。Or some other systems that I will talk very。Briefly about。

Didn't have any way to identify hardware， basically。

All the cards that you would put into the IBM PC or XD or 80 were actually pretty dumb compared to。

 for example， machines that came a little bit later， such as the Amiga。Namely。

 the mega 2000 and similar things。Which used a bus that had。

Cards that would alter identify them similar the PS2 line of computers， the successor to the PC。

 basically by IBM。Or boughts， I think with Ia E I S A slots。

 I think those also supported something more clever。 And only when the PC I bus arrived in， I think。

1993， but it became only widespread in 1995， roughly thereabout。

The cards gained so much intelligence that they would announce themselves to the system and be identified。

 resources would be allocated for them like memory ranges， interrupts。

 DMA channels and stuff like that。But this year， this is the CGA Redux。

Color graphics adapter clone board。It's super dumb。 Basically， there are only a few。

Buss transceives and buffer chips on here that basically connect the whole cart directly to the I A bus down here。

And the port that， for example， the Motorola 68，45 appears on the bus is hard coded in these chips。

And there's a bit of Ram that's also hardwired into a certain memory location in the memory space of the PC。

 as well as the character room。I'm not even sure that this is exposed to the bus。

 but it's definitely visible from the 6845。So。😊，How would you then determine that theres a C J count your system。

 And similarly， we have a Hercules monochrome display card clone， which was an enhancement。

Over IBM's monorome display adapter， which was similar to the CJ。 And these two once look。

A little bit similar because both are based on the Motorola 6845。

And the IBM MA card could only display text， high resolution text， nonetheless。

And the Hercules count， which we have here。Or a clone of that basically added a high risk monochrome graphics mode on top of that。

So we you had two cards and you could even drive them at the same time， one color card。

 one monochrome card， both based on the same chip。And the question would be。

 how do you determine that either of those is installed in the system？Because this is itself。

Wouldn't be able to tell you because there was no API。And then along came the IBM EJ， in this case。

 there is a little bit later version made by paradise or a clone board again。

 which came with its own bioossro， so executable code because it had to run also in the original IBM PC or X D。

 which didn't even know about the EJA card because it didn't exist Penglan。

 so it would announce itself at least by other bioos。

Which would appear in the space memory space for the option rooms。

 and the regular buyers would execute this。And。Or the other way around， Imur。

 maybe this would be executed first and then the normal biasro would run。 but either way。

 there was a mechanism to execute Xoms， which the AGA card utilized。Again。

 how would you tell that an EJ card is in there？Existence of this realm is one of the methods that you could do that。

 But we'll， we'll see that in a short while。And even later came the VGA standard。 In this case。

 we have a saying E T 4000 super VGA card。 Again， it has some rum chips here。

Which work similarly as the EGA ro， and they would be executed right after the boot up initialize the card。

And yeah， but both the VGA and the EJA card would be backwards compatible with the CGA card in a matter of sense。

 and how would you be able to tell all these different cards apart？And this had to be done。

 because people would have。Any of those cards。 and you could combine always one monochrome card that is mostly an MDA card or hecules card with one of the color cards。

 CG， E G or VJ。For actual for dual monitor use， for example。

 playing games on the color monitor while doing business stuff and do stuff on the monochrome。

 or maybe even what I did back in the day develop some stuff on the color monitor and the ToboC or something IDE would run on the monochrome monitor。

Even underdoth way you don't have any multitasking at all。

 but that way you could basically debuok a graphics application on the color card。Very fancy indeed。

 And games like Zac Mac K orman Man would auto detect which card was installed and choose the appropriate video mode。

 which is sort of like magic。 Other games like Space Que Kings Que from Sierra would have an install program where I had to choose manually which card to use。

😊，But we will learn now that they are actually relatively decent ways to automatically identify which cards are installed in the system also if there are two cards in the system。

 and yeah I'll show you how to do that。One note， we will be using the emulator 86 EMU。

Because it is a very， very accurate PC emulator where you can choose from a wide variety of PC motherboards。

 CPU types and bios types。 and it's very accurate。 And I will pick this over the usual dos box。

 which I will still use for coding because dos box actually is。A rather fast emulator。

 and it doesn't emulate the hardware very well。 For example， the 6，8。

45 chip on the Hercules or CG A card are not 100% and properly emulated so that we will get some issues there and yeah。

 our method of detecting this relies on the 6845 being there physically or very accurate。

Emulation mode and dos box can't supply that。 So the actual code has to run on real PC or on the 86 E U。

 and Dos box will fail somewhat if you set it to emulate CGA or Hercules only。 Also。

 I think the regular dos box can't emulate dual screen color and monochrome。

In case I didn't get it to work。But 86 E U can do that without problem。

You will rarely want to run Dos box in CGA or Hercules mode anyway。

 except if you have a program that needs Hercules， but then you don't need this automatic detection thing anyway。

 So yeah， I think this is still very interesting because if you want to code for MSs Dos and want to automatically detect and choose video modes。

 you will learn how to do that today。 So let's have a look at how this works in program code。

I have set up a little framework already here so that we don't spend too much time on the boring details。

 the program contains。Two files， one is the Dosviideo。 C file。

 which contains the actual detection code， and the other one is called Dosviideo。t H。

 and it has a few strings so we get a human readable answer。

 which displays we have in the system plus a few helper variables in a helper function to convert some return values into the strings。

That we have up here。 So will ignore this for the time being。But it's there。

If you want to have a look， I will put everything up on GitthHub and put a link in the video description。

And the main program basically looks like this。 we have a primary card and a secondary card。

 Those are just strings which are initialized with unknown and no display because for the primary card we just don't know what's in there and we assume that there's probably no display。

On the secondary card。Then we clear the screen， which works in TobyC like that and other C dialects won't have that function。

 This is specific to TobyC。And then we say to the screen we are probing first of all the VGA then EGA。

 CG and the H GC card， HGC being Hercules and MDA cards。

 and we will differentiate between both of these。And why are we doing it like that Because we are going from the new standard to the oldest。

 because actually the new standards like VGA have functions to determine which card science installed in the system and let's have a quick look on help PC library there is the graphics interrupt which is the interrupt 10 and its sub function 1A is called the video display combination。



![](img/b40b5f9afaa8c465d97b7773ada977a4_1.png)

And you put。0，0 in A L and 1 a into A H。 and this will give you the video display combination。

 You can also set the video display combination but that doesn't make much sense as you can do that during runtime while the computer is up。

And then you will get these codes here。In B L andPH for the active and inactive display。

 that is what we are calling the primary and the secondary display。



![](img/b40b5f9afaa8c465d97b7773ada977a4_3.png)

And this will be the codes that we are also seeing here， for example。

 VGA with analog monochrome or color display。

![](img/b40b5f9afaa8c465d97b7773ada977a4_5.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_6.png)

This is what you most likely will get is 08， and you can see here it's the same case 0 x08 is display VJ analog color and which translates to this string here。

 which are basically just copied from this file here。



![](img/b40b5f9afaa8c465d97b7773ada977a4_8.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_9.png)

So all we have to do is call the interrupt and we already know how to do that more or less we are setting up a union of registers。

 this is how you do that in Tousy if you don't remember that it's also in earlier let's code episodes。

This is basically a structure collection of all the registers that the CPU has。

And we can write to them like this。 Rex X gives us all the60 bit registers。

 and we are writing to the A x register value 0 x 1， a 0，0。

 which is exactly the function that we are seeing here。 We could have alternatively written。



![](img/b40b5f9afaa8c465d97b7773ada977a4_11.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_12.png)

It like this， Regstart H。

![](img/b40b5f9afaa8c465d97b7773ada977a4_14.png)

A H equals0 x1 a and rex dot H dot A equals 0 x 00。



![](img/b40b5f9afaa8c465d97b7773ada977a4_16.png)

Which is exactly the same， but the line above is only one line and this takes two lines so I'm inclined to write it like this because this is the AH register and this is the AL register inside of the accumulator register AX。

Okay， so and that's that。And while doing this， we can already call the interrupt。

 which is done by calling the function in 86。And you pass on the interrupt。

 which is the graphics interrupt0 x 10。And you pass the pointer to the register structure。

Called res for the input and output values。We can use the same structure here as we don't care about preserving what's there。



![](img/b40b5f9afaa8c465d97b7773ada977a4_18.png)

And now if on return， we actually get the same value back。

It says here AL contains 1A if a valid function was requested in Ah。



![](img/b40b5f9afaa8c465d97b7773ada977a4_20.png)

Otherwise， this will be actually be reset， so we can test that if res HL。Equals 0 x 1 a。

 That means the bias did work， and it did execute the function。 so we can。Basically。

 just take our primary。Card and set it to。Whatever we got back and we feed this to through the VGA2 string function that you can see here on the right and the value for the primary card。

 we remember here will be in VL， so this is ragsdoth。tbll。



![](img/b40b5f9afaa8c465d97b7773ada977a4_22.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_23.png)

And the same thing we can do with the secondary card。Secondary card。 But this time。

 it will be in B H。So anyway， once we have the primary and secondary card from the VGA card。

 we actually don't need to check any other cards， So we have these variables here that are set to one in this header file here to notify that we still need to test for that and we can actually set。

Everything to0， now。Because the VA card actually can tell us。What cards are in the system。

 So that is pretty simple。 One thing to note is if the active and inactive display that we get back。



![](img/b40b5f9afaa8c465d97b7773ada977a4_25.png)

Was reported as the MA with monochrome display。 It could still be the Hercules card。

 which means we test now if the。

![](img/b40b5f9afaa8c465d97b7773ada977a4_27.png)

哦。B L Reg。Equals。1 or the。B， H。 So one of the。Cards that are in the system。

Is potentially an MA card because the VGA won't test for any or can't can't signal to us if it's a Hercules card。

 We will still do the。

![](img/b40b5f9afaa8c465d97b7773ada977a4_29.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_30.png)

Herriccules test。This will give us a distinction between the MBA card and the Hercules card。Yeah。

For the remainder of the tests， we will also rewire the pointer that we're using here。

Which is this one here to point to the secondary card string。This is just so for the CGA card。

 we don't know or for the 6845 base cards， we don't know if we're on the primary secondary card and I'm using this pointer here。

So I can swap around now with the EJ card， everything is actually rather similar to the VJ card。

 but there is a different function that we want to call。

And that is the function 12 heodal the video subsystem configuration。



![](img/b40b5f9afaa8c465d97b7773ada977a4_32.png)

And here we need to call the sub function10 hexismmal。Don't be confused by the missing H here。

 Thiss actually the Exodional value。 So Rex dot H dot。



![](img/b40b5f9afaa8c465d97b7773ada977a4_34.png)

A H needs to be。12 hexeromal， according to this and Rex。th dot BL needs to be 10 hexsMmal。

And then we can call function as usual。For interrupt 10 exit SML and the input and output registers。



![](img/b40b5f9afaa8c465d97b7773ada977a4_36.png)

Now， if there is no EGA card， the inter tool just return and PBL will be loaded with the same thing that we put in there。

 So if Rex dot H dot BL is still 0 x10， then we know we can't have an EGA card。



![](img/b40b5f9afaa8c465d97b7773ada977a4_38.png)

And we will set EG， the test variable for EG to0。And simply return。 That's it。Otherwise。

 it is possible that oh， it's definitely the case that EJA has been found， and we just need to check。



![](img/b40b5f9afaa8c465d97b7773ada977a4_40.png)

What the settings are basically， if it's a monochrome card or not， because if it's a monochrome card。

An eG card on a monochrome display。 We can't have another monochrome card in the system。

 as you remember， because monochrome cards will always use the same memory， basically。

And the interesting part here， the C L registerar contains the actual switch settings on the EJ card。

 if it has dip switches or otherwise if it's wire up via a driver or setup program I showed you the paradise EJA card before and it had those switch settings。

 and one of them is for actually。

![](img/b40b5f9afaa8c465d97b7773ada977a4_42.png)

Setting the card to。Mono mode， basically。 So we're gonna introduce a new variable here called dips。

And the dip switch setting will be the C Reg shifted to the right by one bit。And very simply。Put。

 you can。Look up the switch settings on one of the many websites that describe the EG switch settings。

 but if the dip settings。Exactly equal 5， which I think in binary。Should be， there should be one。

 This is the two。 This is the。4 and the8。 I think this should be this pattern。Yeah。

 if this is the case。Then we actually are in the mono mode。

 and we will set display EGA mono to the primary card。

And then we can actually skip the test for the Heculus graphic start。

 but there could still be an E CGA card in there， so we will still test that。Um， elsese？If。

The dip switch settings equals 3。Which in binary should be the case if you have these switch settings。

I think then the color card its color color basically。Primary card equals。

Display EGA color on a CgaA monitor， actually。嗯。And there can't be any more CGA cards。

 Hercules or MA could still be there， so we leave that。And if none of those are the case。

 everything else should， in theory， be the。DGA on a high risk monitor？

And which means there can't be another color card in there， so CGA again。

 is being set to zero so we don't test it。Hercules， etc， are still possible。

And now the same goes here because we don't， we have to know for the 6845 based cards， So H GC。

 MA and CGA。That we are now on the secondary regard we put。The pointer again， to this thing。

 It's just for storing the correct information in the correct variable， basically。Okay， that's that。

嗯。Now， I've already prepared。3 functions C， one is called a test CJ，1 is called test H TC。

 and both will be using the test 6845 function， which tests for the existence of a 6845 Motorola CRD C on a certain port。

And how we do we do that basically。We will need a bunch of。嗯。Variables。

 which we'll introduce shortly。But the very first thing that we have to do is we have to know a little bit about the CRTC registers and most of the registers that we can try to identify。

Are a bit tricky and could distort the image on the screen。 But there's one particular。

A register on the CR TC will namely register number 15 or Hx SMl F， which is the cursor low register。

 which。Thing sets the size of the cursor。Which we can simply write to without destroying too much。

Things on on the screen we can also reset it without any grade。Disturbance， if there is a 6， a，4，5。

 it will take this value and also give it back to us when reading from that port。

 So we are gonna to do that。 And the way this works is。We can write to the part in question。

The number of the rear that we want to read al right， which is F hexadeimal here。

And then on the next port， one up basically is the actual data port。

Where we can read and write the actual register basically here you set the internal register address and you go incremental the address of this register。

 for example， on the CGA card， it's 3D4 and on 3D5 you can read and write the port then the registers actually。

So we're doing that and we are storing the old value that we had in here。

So we can restore it after our experiments， basically。 and then we gonna。Again。Right。

 some arbitrary value。Here are the。Vue could be anything we're taking this one here。

And then we wait for a little while。 and topC doesn't have a proper function to do that。

 So we are just gonna wait for a few microseconds by counting 2000。Especially in a slow machine。

 this will work quite fine。 And let's be honest， any fast machine probably won't have a CJA or alas card inside inside。

Yeah， and then we read out the new value。By reading into from this port。嗯。And。

Then we are gonna set a good idea what I did here。 Basically， I need to do that。That's better。

 And then we're restoring the value that we had。 Oh， sorry。Poor， but。Port。Od value。

And we return true， if the new value。That we have read back exactly equals the sort of arbitrary value that we wrote into there。

And we need a bunch of。Variables here。 So we need some iteration variable， the old value。

 the new value。 and yeah， that's it。 I think， yes。Let you do it。So basically。

 select the register for the cursor Lo increment port， read that register。

Sts an arbitrary value read back after short while this new value。

 hopefully then restore the value and compare with the arbitrary value。

 and that gives us if the information if at that port， theres actually a 68，45。So， for a。

CD a account。 The test looks pretty simple if test。6845 at port number 3D4。

 because that's where CGA cars always are and nowhere else basically in the system。

Then we can say primary card equals。Can display C GA color。

sorryrry because the C j can only be the primary card。And card equals。Secondary regard for the H TC。

 Actually， I think we should have a test here。 I think it could also be。

 let's do a little bit differently。嗯。Let's do if can't。Let's take。Card equals。The address of。

Secondary card。Then we don't need to do that， says does it make sense， no， it doesn't make sense。

Basically， what we can do， I think， is just this year。I would say。Let's strike like this。

 I think this should be more less safe。Because we could have an EJA mono card and CJ is a secondary。

 I think I don't think I can configure it in EmUS 86。

 but yeah maybe those are the test case that we can't really do。But never mind。

The Hercules card is a tiny bit more difficult。And I made one mistake here。 It， of course。

 has to be asterisk card， because we need to write into whatever card currently points to。

 And I think that should be fine。Okay， Hercules count is a little bit more difficult。😊，However。

 the basic test is actually the same if test 6845， no it's not 3D4 but 0 x3 B4 for the MA and the Hercules card。

Then we already know that whatever card we have is at least。And MDA monochrome graphics card， okay？

However。This way， we can't actually distinguish between MD and Hercules。

 The Hercules has one feature that the M A doesn't have。 There is a status port at 3 B A， Exosmo。

So basically， we will need to do something like import。From0 x 3 B。



![](img/b40b5f9afaa8c465d97b7773ada977a4_44.png)

Okay， here we have the information page for the 6845 CRTC controller and at 3BA or 3D area of the status register。

And if we go to this one here， status bit 7 is unused on the M。

 but it will actually toggle during certain retraes。

 I think it might be the horizontal retrase instead of the vertical retrace。on the。

Hercules card on the M card， it's not used on the Hercules card。 It is used。 so we need to check。

If this bit actually is toggling， and this is only the case if we are on a Hercules card。

 So what we're doing now here is。

![](img/b40b5f9afaa8c465d97b7773ada977a4_46.png)

Take。Some kind of status value on this port。And then， we'll do a。

Very long for loop as long as we can get with the 16 bit integer。So something like 32767。

It's a very long loop。On a slow machine， at least。And we'll read。Again， the byte。

Here from the status and we will mask out the seventh bit。This is basically。Something like this。

So this is the seventh bit that we're asking out。And if the value that we then get。Actually。

 we also need to do the same thing here。If the value that we then get is not equal to the status value from above。

 then we know we have got the Hercules graphic start so basically we can say okay。Card is。Display。

HtC mono， and we can return。That's it。So。To recap。 and we will very quickly test this out。

 The VJA card can tell us exactly what's in the system via the interrupt 10 and the subrout 1 a。

 The EJA card can tell us that it's an EJ card and with the subrout。10 hexademal of the function 12。

Exadadeimal of the interrupt 10。It can tell us the dip switch settings。

 and it will tell us if it's mono or color or height resolution color card。

And the CJ and Hercules and MDA cards we can test by testing for different pods。

On different ports for the existence of a 6，8 for 5 CTC controller by using。

The fact that it has certain registers on certain ports。And the Hercules card。

 we can distinguish from the MDA card by testing for this toggling of the seventh bit in the status register。

 which doesn't happen on MDA cards， which is a peculiar peculiarity， basically。 Okay。

 let's fire up M U 60 86 and testers。

![](img/b40b5f9afaa8c465d97b7773ada977a4_48.png)

Okay， and the application is actually called 86 box， I can totally recommend this。



![](img/b40b5f9afaa8c465d97b7773ada977a4_50.png)

Currently we are set up for 386 DX with primary card CGA and secondary card Hercules。

 which you can see here on the left is the CGA and here's the Hercules card。

 I'm not sure if I can enlarge the second one seems to be a bug。



![](img/b40b5f9afaa8c465d97b7773ada977a4_52.png)

But it doesn't matter we don't want to display anything on there anyway。

 and I copied the file onto drive a。And we can just call those video。Here。

 and it will be probing all the things。 and we'll say primary card is CGA with color display and secondary card Hercules with monochrome display。

 which is exactly correct。 let's quickly rebo the machine and set it to VGA and Hercules as an example。

 and we will also do only one display basically yeah the。



![](img/b40b5f9afaa8c465d97b7773ada977a4_54.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_55.png)

Bios will complain about this。 We will have to。Save the buy information again， because。

80s will store if it's a color or monochrome display or VGA or CGA。

 and they will complain if it's not correct， So again running Do video。And again。

 it works primary count VJ with analog color display in Hercules with monochme display。



![](img/b40b5f9afaa8c465d97b7773ada977a4_57.png)

We're just pretty nice。 Let's turn off the。AHercules card here and let's say switch to EGA。

 we haven't seen that yet， we are taking a vanilla EGA card from IBM。



![](img/b40b5f9afaa8c465d97b7773ada977a4_59.png)

the machine will reboot。The second monitor will be empty。

And it will not complain this time because EG and VGA are treated similarly by the biasers。

And then running those video should hopefully give us E G A with color display。 Oh。

 there's still the monochrome display。 I didn't turn that off。 It seems。 Yeah， let's try。

 let's try and see if we can do that。 We can even change the， I think。



![](img/b40b5f9afaa8c465d97b7773ada977a4_61.png)

Let's quickly check。 Let's go out here。 It says EG with color display。 So nomly not a EGA color。

 high color， high resolution color display。 Let's switch to that so we can configure here。

 enhance color。

![](img/b40b5f9afaa8c465d97b7773ada977a4_63.png)

![](img/b40b5f9afaa8c465d97b7773ada977a4_64.png)

🎼Oh， I think that's。Enhanced mode probably， yeah， that should be enhanced mode。

 This should be the high。

![](img/b40b5f9afaa8c465d97b7773ada977a4_66.png)

And then we are doing none on the second video card， just to make sure。And yeah。

 this is already looking more higher。 This is not CGA resolution running。

The thing now should interpret the dip switches correctly primary card EGA with higher color display。

 there I have it。 And this is basically how back in the day with IBM PCs， you could identify which。

Cards are basically graphics cards， especially are in your system。

 and how all the andfo programs did it。There are， of course， caveats。

 if something is not 100% compatible or maybe some Hercules card doesn't implement this status bit 7。

 then you might misidentify things。 So it's always a good option to give the user the option to override the video settings。

 or， for example， some people might want to play。In C GA or E J mode。

 even if they have a VJ account for whatever reasons。But that's it， I think for today。

 check out 86 box。 It's a very nice， very accurate IBM PCC and compatible emulator。



![](img/b40b5f9afaa8c465d97b7773ada977a4_68.png)

I will put up the code on Gitthub and link to it in the video description。As always， like。

 share and subscribe， please leave a comment down below and Im very grateful if you can support me in some fashion。

Links to Patreon and all the other stuff are in the video description。 And if you can' do that。

 that's all to find。 I hope to see you in the next video。 Have a nice evening。



![](img/b40b5f9afaa8c465d97b7773ada977a4_70.png)

🎼Yeah。