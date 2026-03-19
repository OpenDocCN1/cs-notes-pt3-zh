# 【密歇根大学】嵌入式系统设计导论-EECS-373-｜-Introduction-To-Embedded-System-Design-2025-p12-P13_课程12_SPI_I2C串行总线--BV1VTSNBoEem_p12-

Okay we can get started homework due tonight and there's office hours today I remind everybody that team registrations due Wednesday。



![](img/348c43aaec3cb5f1066981eae67c444c_1.png)

All rightAnd only one team is registered so far only one one good team I don't know about the rest of them then the other homeworks have already been released for the rest of the semester this is all that you have do as far as homework for the rest of the semester after you guys register for your teams actually on Wednesday we will release the project meeting schedule and you guys can go sign up your team will sign up for a slot you'll come to my office or mat's office or jam office for 30 minutes bring some basic slides and we'll review your project and give you feedback forgot was there homework in this there is no homework drop in this class。

You enjoyed fall break？13。It should be that date wrong， it should be like the 20th or something。

Let's go look， let's find out together。On Mondayonday the 20th， yeah， that would make sense。Very。

Yeah。So yeah， next week as Paul study breaks， we don't have， you don't technically have a lab do。

Right you can work on your lab if you want， your project proposals are due Wednesday。

 so I mean it's a little unfortunate actually I just need it 24 hour or I need it the night before your actual your meeting so you could do it on your meetings on Friday。

 you could do it Thursday night。Again you're going to bring slides Yeah。

 so there's going to be no formal class next week on Wednesday we're going to use that time for project reviews。

Any logistics questions？S think this is 20。I is 27， anything else？

If you guys are having trouble finding teammates， come see me after class。

We can spend a little bit of office hours doing some matchmaking。

 trying to get everybody into a team。All right。So we're going to move on to SPI。

 so it's a serial peripheral interface， this is another one of the communication buses。

Readings here so again guys should be at the point where you can read the manual。

 there's also this textbook gives a fairly good review。

 but serial SBI you are Ibergs here have been around for a long enough time you can find good tutorials online as well if you want a different take I would look at the major vendors like analog devices。

STM has tutorials， any vendor that makes chips typically has a tutorial for these things anyways。

 so you can guys look around and find other tutorials for this topics。I'll give you the basics here。

All right， so SPI stands for serial peripheral interface。

 common one of the most common communication protocols has four wires。Plus ground。

 you always have to remember that there is ground， if you don't connect ground between your devices。

 you will not get any data transfer through or you get very poor data transfer。

It's typically used for chip to chip， this is not USB where it's devices to device。

You have a single controller and multiple peripherals。It's fully duplex。

It's transmit and receive can you guys hold on for a second？呃。

So the controller can transmit and the peripheral can transmit at the same time。

 typically doesn't happen that way， but as possible and it's nice that it gets up to multi megabits per cycle。

 one of the challenges with SI it's this not official standard。

 like it's a de facto standard and that many chips and manufacturers follow it。

 but it's not like it's an IEE standard where they regulated every last little bit of this。

 so that means that there's a lot of freedom in here it's very basic protocol。

 but it also means that not every vendor is going to follow the same rules and we'll see some of the caveats as we go through here about how the standard has evolved over time。

So here's an example of wiring， so here we have a controller and three peripherals。

 they each share bus lines， so here we have SDO， so see。Controller out， controller in。

And then you have a common clock that goes to all of them and then to do the arbitration that's where you're telling the controller tells which one I want to talk to there's a little chip select so you have to have an extra on the controller an extra lines for each one of your peripheral so this is a lot like how advanced peripheral bus use had it controller and its peripheral would go through and select which ones it was going to interact with and remember there's different different registers inside of your advanced peripheral bus peripherals there's also different registers inside of here so you'll get a data sheet and it'll say oh there's n。

Registers in here and this is the way they'll tell you how to index them and how to send data in and out of those registers。

So serial data in， serial data out， system clock， maybe shouldn't say system clock。

 it's just the clock of the controller is using for that。And E select lines。

The control reflects flex peripherals by pulling it low。

Conter generates the clock and it shifts data out on the clock edges。Any questions？Okay。

This is calledchronous a synchronous protocol in the sense that the clock and the data are aligned。

 so there is a clock is fully duplexed in the sense that the idea of how this was originally developed is that there's a register here and a register here and that on each clock cycle data is being transmitted out is being shifted out。

 so basically let's see how do this here like this is shifted through that way。嗯。

And so here you can start seeing that typically like if your controller sending out data here。

 your peripheral isn't necessarily going to send out whatever it's here， it could。

 that's how it's designed， if it had a message to be sent out。

 but it has nothing known to send out all zeros for all ones， whatever is default fault statuses。

 but the idea here is these two shift registergis that that been put together。

 they're pushing data back and forth to each other。Packet sizes usually four to 16 bits。

 eight bit is typical， eight bits is just what ASCI characters are， it makes it life easier。

 that's usually the packet size to go between the two。There's no acknowledgements。

 there's no flow control bit so there's no parity bit like we saw and you are there's no start or stop bit it is just。

Send out clock edges， you're not always sending out clock edges。

 you only send out clock edges when you want to communicate。

 you're going to use chipI select peripheral， and then that's when data is being put out on the line。

Yeah，So all this does is swap data between。Yeah。How do you like write something new to one of the？

Especially the controller wants to send。啲个。All I see is like。

The only way that control it can change is if it reads in from the peripheral。

I mean this is the base format of how it works right so now you could have combinationlation logic over here that looks at this register and says。

 ah I've gotten a full new eight bits， I'm supposed to do something with it。

 like get my accelerometer data and send that back， but this is just the underlying mechanism。

Of how data it is transferred back and forth？And so the SI peripheral can choose not to send any data back when data is coming through if it has no data ready to send。

 so if it was all zeros， it wouldn't send anything。そよ。What do we know when all the bits are swapped。

 is that negative itself for？How do you know when all the bits are swapped so you have to agree beforehand you're going to look at the data sheet and say this peripheral of this device requires 8 bits or 16 bits or 12 bits whatever it is and then so you have to know a prior how that works and then you're going to ship out that many bits so it's not required there only an eight bit register this is typically how you would think about it I suppose it could be larger 14 bits that's why Im is there a counter to handle。

You would configure your serial peripheral device to be this many bits。

and you do multiple transactions over and over and over again so say yeah you're trying to read all three axis of an accelerometer。

 you'd say give me the X and then it would prepare a packet then you send out clock edges to get the eight bits for that and then you send another one that says give me Y and then it would get that thing get it ready and you send out more eight clock edges to receive it so you can only transmit data back when it's receiving clock edges。

Y。没很框。The controller。And it's sending the clock。All the peripherals。So here。

It sends it to everything。It's just the trick is only chip select for that peripheral is going to be enabled。

Just like the peripherals on the APB。What do you think about that？Believe it， believe it， okay。

 could you say I don't believe that that's horrible， okay？Yeah。

I control like I guess for the STM like I controller have like a finite amount of lot of there needs to be an able pin for each one you typically will reassign one of the GPO pins to act in that role and you have to tell your peripheral hey this is the pin that controls that it can be somewhat painful if it's like the STM I'm trying remember the STM STM does like have some predefined pins but if you wanted N like more than that then you have to kind of like push it into the protocol or sorry into your code。

What other questions you have？

![](img/348c43aaec3cb5f1066981eae67c444c_3.png)

呃。So as I want to go through this block diagram， I mean really the thing to take away from all of these serial protocols is really a shift register。

 why do we use shift registers as the core because that's the interface between the massively paralyzed world right。

 32 bits is your core。

![](img/348c43aaec3cb5f1066981eae67c444c_5.png)

![](img/348c43aaec3cb5f1066981eae67c444c_6.png)

Versus you've got this limitation so this is the controller， this would be your GPO pins。

 you have this limitation， you can't get 32 pins out， you only got four pins。

 a limited number of pins and so now you have to shift everything from the parallel world to the serial world and then you clock it in then you got the serial world back to the parallel world so it's really this whole protocol all the protocols of serial are based around this constraint of GPO pins。



![](img/348c43aaec3cb5f1066981eae67c444c_8.png)

![](img/348c43aaec3cb5f1066981eae67c444c_9.png)

![](img/348c43aaec3cb5f1066981eae67c444c_10.png)

![](img/348c43aaec3cb5f1066981eae67c444c_11.png)

And so in this little thing， trying to remember how it works here， we have some data up here。

 we have a load， we have a clock that's going through， let's see。

Is the clock not clocking I would just oh just， oh this is on the sequencer。

 so it just does eight clock cycles every so often， not continuously。



![](img/348c43aaec3cb5f1066981eae67c444c_13.png)

Make sense。And then let's say I'll select a device。You'll select that device。

 and then I can go and shift out。Data going to work。Oh， no， have to go this way。



![](img/348c43aaec3cb5f1066981eae67c444c_15.png)

That got a little bit off cycle， but now you can see that I'm shifting data out from here into there。

 and then you would just go， as I screw it up， go and select the other device and shift out data to the other side。



![](img/348c43aaec3cb5f1066981eae67c444c_17.png)

看到。And then as we get to the end of those eight clocks cycles， stop here。



![](img/348c43aaec3cb5f1066981eae67c444c_19.png)

You know you're going to have to have some logic internally it says okay。

 eight went past or whatever the number is and your data sheet。

 eight went past and now it's time for me to do something with this data right to take that data。

 the peripheral will do some action with that data。

 typicallyy it's getting prepared to send data back usually it's a request you're sending you send me some data and you get some data back。



![](img/348c43aaec3cb5f1066981eae67c444c_21.png)

![](img/348c43aaec3cb5f1066981eae67c444c_22.png)

![](img/348c43aaec3cb5f1066981eae67c444c_23.png)

Yeah。😊，I'm confused since the part where you say， oh， I screwed it up。

 I'm going to select them alternateative advice is it like sorry， say that all again。



![](img/348c43aaec3cb5f1066981eae67c444c_25.png)

So I'm a little lost after you said I screwed it out I'm going to go to select the other device。

 so I'm not really sure。

![](img/348c43aaec3cb5f1066981eae67c444c_27.png)

Well we have to have two device where it's just like an example， just an example。

 you know I need to have one advice， I just started clocking data out in the middle。

 I didn't load the data out of the。Controller shift register and theyre halfway through eight clock cycles I didn't align that so your my controller better be better at that than me and then I just readed the experiment by going to the other shift register or the other peripheral and usually it will be the programme programme' responsibility to make sure。

That we enable it。In the right timing or yeah， I mean you as a programmer are going to do that in conjunction with your SBI peripheral。

 so you have a whole peripheral on your device and typically what's going to be is you're going to send data in and you're going to send it tell it to go and then it will take care of the rest。

And you're going to have to set up and tell it what's the clock priority。

 the number of bits you're going to send out all that sort of stuff。

 you just load to register and then say go， that should be essentially what it is。



![](img/348c43aaec3cb5f1066981eae67c444c_29.png)

Any other questions？

![](img/348c43aaec3cb5f1066981eae67c444c_31.png)

うんふんうん。One of the nope， what is this SI，si squared C， that's not the right lecture。



![](img/348c43aaec3cb5f1066981eae67c444c_33.png)

![](img/348c43aaec3cb5f1066981eae67c444c_34.png)

One of the challenges is the timing of when you clock data in and how it's clocked in because there's no formal spec。

Or IE， everybody agreed on spec so it's kind of evolved over time。

 the most basic cases is here you have your clock， this is your control line。

 remember your control line or chip select goes low just select the chip。

It helps helps the peripheral know that there's anything connected right so if the pin isn't ever high。

 then the peripheral says well I'm not even collected to a bus right there's a little timeout in it。

 but here when it transitions from high to low you go and the chip says okay I'm about to be talked to then you have serial data out in serial data in so this is from out of the controller's point of view so it's out and then serial data in from the controller's point of view and so here's the bits that are possible to be clocked in and so a normal clocking regimen here。

Would be you're going to go in on say the rising edge you're going to clock in the data because the data is stable here。

 you don't want to clock on the negative edge in this particular case because the data is in transition so you're going to clock right in the middle of that i diagram so these are typically called i diagrams because of all the data that is going high。

 this is the highest part it's the lowest part and then you want to shrink the time to the point where it's the smallest possible such that you can transmit data through reliably if it's too small then you'll get corruption。

That's just the convention of how these diagrams are made。

 but this is not the only way that they can clock data in and out。

So they have a somewhat complicated at first set of options there's up to four different modes and so here we have clock clarity this row here is clock clarity1 this is clock clarity zero and basically are' saying is is the clock normally low or is the clock normally high so there's two different modalities here is rising here's rising here it starts low goes starts high goes low in so that's the two different clock clarity and then you have the phase what they're saying is where is data latched in and out so you can either latch here it's sampling edge here's the toggle edge so here toggle edge being when the data toggd sampling edge is on the first edge and heres sampling edges on the bottom so now you can imagine you have four different ways in which data can be clocked in and out and so you have to know what your peripheral does if you're doing something different than your peripheral it won't work and it used to be that not all microcontrollers would support these so I certainly had back in the。

this late 2000s， I had bought a ship， I think it was mode three actually。

 that was not compatible with my micro controllertroller for whatever reason it was insane， I'm like。

 how could this possibly be so I had to go and put like a little inverter just to invert the clock line to make it all work。

 made me insane。How do we feel about all the different clock edges？I can't tell y， one brave person。

toggling so sampling is when the data is sampled， toggle is when it's changing between states。

 so here this is when data is sampled， here's when data is toggling between the states。

So then the reality is you get some horrible complicated time diagram like this。

 which is trying to show you all the possible phases for one set of bits and so here we can say this is this is your clock。

 your is your polarity of your clock and this is your phase of the clocking so here we're positive。

And we're clocking it on the first edge， so this would be this one， zero0。

We can go down here and they just show that the data happens up all at the same time。

 which is a little bit confusing。But they're just advancing or slowing down the start of the clock just to make it all aligned in this diagram。

 and here you see the polarities inverted and the phases on the or on the second edge， so over here。

And so here you can see that here had a negative edge， started out positive， went down negative。

 so that would be inverted polarity， and then on the second part of that clock edge is when data is sampled in。

So you just have to keep track。What your device expects and be able to walk yourself through this diagram so that you know what you're expected to do。

So I'm looking at like the top and bottom one and then the two middle。

SoThose ones look almost identical to me except for the very beginning and the very end。

 can you explain why there are oh is clarity， clock clarity， this starts high， this started low。

OhYeah， it's subtle。But you can also this it's also in the nomenclature here， but yeah。

 they are very similar， you can get lost。嗯。Yeah， are there four different modes for this？

Because there you have two three parameters， so you can either be positive negative polarity or positive or negative phase。

So then that's just the logical combination of the two that answered the question。

I don't say how it would benefit oh why in the world would people do this？

That that's a whole nother story The problem is there's no standard so some manufacturers did it one way。

 some manufacturers did it another way， and now we're stuck with all of this thankfully your microcontroller supports all of them。

But yes， there is no， you could just choose one of these and it would have been fine。

 but that's not how we inherited this world。Yeah。对异。没。二。Plarity。

 think about clock clarity is what is the resting state of the clock？

When there's no clock signal going on， is it low？Or is it high？

That's what clarity is making you think about。if the clock is an higher low correct。

The phase that is， are we looking at the first or the second？Yeahep。All right。So De， let's see。

 am I trying to tell you here， I don't want the slide， I want the slide。

So here's an example of a typical transaction so here you're an idL the controller is an idL the controller is sending out clock edges here it happens to be I think we could figure out what mode this is maybe this is mode three it' saying that you're going to clock data in here and then it sent out some data as well so these two are generated at the same time by the controller in this case now you might say why is there nothing being transmitted back I thought this was that ship register thing well the peripheral has nothing to say yes that data is being shifted out technically。

But the peripheral has nothing to shift out， so it's just going to keep it all ones。

And then you can go line up here's what the data is that's being sent out so I said ask ES and then the typical case is that this is some command again you're going to read through the data sheet for your SI peripheral。

 this is some command and then the peripheral has to respond and you have to know what this timeout value in between is right so it can't respond immediately there's some point where this could be too short for the logic in here to respond so there's typically some timeout then you'd have to read through your spec typicallyy it's not big of a problem because your microcontroller。

It just has some built- in timeouts already in it so in anyways you're going to go out here and then you're going to send out another eightclock edges and this is the opportunity for the peripheral to send data back so the peripheral is pushing this out on serial data in from the controller's perspective and now it's sending asking back to the device。

Yeah。In the bottom right runner has a total dash on the chip slackck。Yeah。第 thatです。

After the last so you could keep this going if you wanted to keep a transaction keep this thing active or you could go back up to high if you're done having a transaction。

 this is a way to kind of tell the peripheral hey， you're expected to respond。

 but if this goes high and say you put say you send an s and s as a magical command that says I want to receive data and then you went high it's not going to send you anything back because you haven't shipped selected it even if you send edges out。

All right， that's a typical packet structure。SPI does not have a standard or a maximum data rate associated with it。

 it uses push pull CMmoOSs so it can actually go very quickly。

 it just depends on the drive strength of those output CMOSs devices so when you're looking through your data sheet you have to make sure that you're matched in terms of speed sometimes you can go much faster than other some devices can go much faster and you have to look at you know what is the spec for your particular device you need to read the data sheet for everything some standard specs standards in quote but you can get up here to。

You knowHundreds of kilobits to megabytes， there are some systems that go up to hundreds of megabytes cameras use a version of SBI called CSBI。

 I think， and those go particularly fast on the slide。when theyre doing the s。

Does the controller send the data and then the peripheral sends it backward is it having at the same time response like when it's getting input。

 is it also getting out the same time Yes， so it pushed out a one， it got a one back。

 it pushed out a one， it got a one back， it pushed out a zero， got a one back。

 it just had no information to set。So this idea of two shift registers they're shifting data back and forth that's like the foundational material of how these things were originally set up it's a good way to think about them now it just may be that it's not actually how your device manufacturer implemented it because there is no spec but this does allow for you could in some devices you can send out commands and receive data from the last command at the same time so you can do fully duplex sending data back and forth so you can increase your overall data rate。

嗯。Okay。So one challenge。With these devices is that there's no inherent way for the S peripheral to tell the controller I want to talk it's not part of the protocol just like with the A or APB peripherals there was no inherent way and that's a challenge for some devices so you take it like a gyro and accelerometer you know when laptops first came out they had spinning disk and it was all solid state and what they do is put a micro mems accelerometer in there and when the men's accelerometer or measured free fault right it's no longer a。

 no longer feels the a of earth gravity as measured by that canilevered capacitor then it would say oh no watch out。

 I need to pull the head of off the disk so that when it hit the ground the disc wouldn't ding the platter and and destroy some bits so you need oftentimes you need some way for your peripherals to actually。

Cause some action over here and so the way you have to do that is you kind of go out of spec well there's no real spec anyways。

 so they say you'll have oftentimes have interrupt prints so these interrupt pins will not be part of say your S peripheral STM doesn't know that they exist so that's not an option but you'd have some GPO pin you set it as an input interrupt you'd say rising edge or falling edge and then that will cause some interrupt on your device to go off under which condition you can go say read out the data and tell me what happened and then you can take the action to pull off the head off the platter。

So everybody you know what want to talk about with hard drives。

 does everybody know how hard drives are made， old disk ones？I get some shaking heads。

Back in my day they used to have metal discs with memory magnets on them that would spin all right。

 it's probably good just to know learn you know watch a you know two minute YouTube tutorial on how magnetic discs work they still use them today it's important stuff to kind of have in the back of your mind。

Yeah， so we talked a little bit about shifting stuff in and out， there's some extra features。

 there's different ways that this can be used and people have changed the protocol over or reused the protocol in different ways。

 so say we could go back up this example as a motivating example。So here the challenge here。

 I have to have what four， five， six wires to talk to all these things maybe you were。Wire limited。

So people will do things like have the serial data out from the microcontroller's perspective。

 send data into peripheral1 and then the out of peripheral1 goes to peripheral2 and so on so forth and so now I have only need to use four to talk to n chips now the challenge is that these chips have to be set up for this condition in the sense that you don't want each one of them reacting to the command but you can shift a command all the way through and then you could then you yeah could shift the command all the way through。

 so this is how dimmable or sorry LED strips that you can individually control each LED typically works you have some color code so say this is green this can be any color so you say you want this one green。

 blue and red and what you do is you shift that red all the way through you do it so fast that humans can't see the small color change that occurs when red was here and then red。

Then you know， shift red went here， then red， then red， and then when it stops。

 then you will see the correct colors， so that's a way in which to not have to have a chip select for every single LED on your thing。

 but you can go through and just push the data through。

 you just have to do it faster than humans can detect。Does that make sense。

 yeah does it have to be serial？You could do parallel。

But then you have a wire problem right so memory for instance。

 you want to do parallel so you might have a 32 bit bus to talk to a memory。

 but that's a high data rate scenario and you want it to be very quick so designers are willing to pay the penalty of all that wiring nonsense just to get that performance。

But here we're going to be in the world of ce where you're saying like a。

 we really care about pin out， we care about layout size， and we're slow。

 we're like our microcontroller is going to 120 megahertz， it's not gigahertz。

 so since we're so slow， we're just going to assume we're in the world where we're willing to pay the penalty for a slower data rates for the convenience of having less pins。

It's a good question any other。Yeah。Perrals need any extra hardware support to do daisy shading or can they do it with the standard hardware that they already have Tyically they can do it in the standard hardware configuration。

 but your peripheral has to be kind of set up for it。

And so there are peripherals that can be daisy changed。

 but some of them I've never expected that because there's no spec。

 so imagine you've written an S into one and you really want the next one to react to it。

 but the first one starts reacting。That would be a challenge。是没。Yeah。

 what is this telling us just that？In this particular case， the word for you2， which was here。

 starts off here， then transfers to u1， and then u1 transfers it to u2。

All right so you're on your STM 32， you have three spy modules， each module has its own IRQ lines。

 now you have a really beefy like 128 pin device on your dev kits。

 typically you don't have that many if it's much smaller yeah。I the previous slide yeah so。

A lot of the design constraints are surface area and then the clock speed on parking why is there like no big handsh parallel？

Why is there no big handhas cereal？I mean， they definitely exist for parallel。

In the world of microcontrollers and embedded systems， you typically don't have large parallel buses。

So we saw for the APP bus， that's a parallel bus， that's a 32 bit address， 32 bit data。

 they did have more handhaking things right you had like your P ready， your P andable， P select。

 all those lines。But here because we're IO limited， we're just not in that type of world。

 so typically there's this conceptual difference when you go from microcontrollers which is bare metal programming C free r task sort of world。

 then you go up to an application class processor so we're in the cortex M cortex R environment。

 you go up to cortex A so the application class then you're in embedded Linux and now it's much closer to a low- end desktop processor and then you start having things like parallel buses to go talk to memory external memory it's just we're not in that world yet。

That world also costs a lot of money。You know， if you want to dev in it。Okay。

So you have this big ginorous chip， but you have also have multiple SPI modules。

 each with your own external interrupts， you have DMA support which allows you to without the cores control or sorry without the controls。

 the core doing any tasks， data can be transferred from your SI bus to memory so you can imagine if you had some peripheral that was just going be streaming you lots of data。

 you didn't have to react on any one datate maybe you looked at like you know 64 data measurements and then you want to take the average or something。

 you could just have DMA push that directly into memory and then when your core gets the interrupt that goes。

 takes that data out of memory and does some tasks with it hardware CRC features。Really。

I't know I had I don't remember that CRC controller， it must be for very specific devices。

 I haven't remember any peripherals in the lab that actually use CRC I'm suppose there are some and your device has support for it again that's really dependent on if your peripheral uses that or not。

So the pros and cons， so straightforward wiring four wires。

3 plus n for the know n being the number of peripherals that you have because that's the chip select line。

 you also have to have ground， it's much faster than the asynchronous is faster than。

You are and there's no addressing right from the arbitration point of view， it is simple。

 you just tell which one you want， there's only one topology it's going to be a star topology。

 I guess you can do the daisy chain and those sorts of ones but they are more rare。

You knowChip select the cons are chip Select does not scale with a large number of peripheral so if you have many many so say 10 that's a lot of GPO pins to dedicate to that you might want to switch to a different protocol like I squared C which is address base we'll talk about that later there's no acknowledgement bit there's no flow control whatsoever so if the peripheral misses something then it's the controller's job to kind of try to figure out what happened why did the data get garbage garbled you don't really know what happens and then。

The controller has to initiate all communication。Yeah， this might be a stupid question。

 but for the like the peripherals not like scaling with a number of lines or whatever。

 is it feasible to have like one main controller and then have bunch of controllers go into oh yeah。

 yeah， and you find there's lots of workarounds for these sorts of things。

You this is a pretty easy doable configuration but sometimes what you have is you'll run out of pins over here or you're just a lot of devices you might have what they call a bridge whichll be an SPI bridge that will go from SPI and then it you will send commands into here which will break out into more SPI line so that you have more chip select pins a more common one is something like an I squared C extender or bridge where you talk i squared C and then you want to we'll talk about a minute。

 you have devices with conflicting addresses so then you have another device in between that changes the address so you talk to one address that's different from here and talk to the other one so there's all these extra helper chips to get around the limitations of these protocols typically when I see these problems you have to be like do I really need to solve it this way because it's usually out of headache but there are helper chips。

Other questions about SI？All right， we're going to move on to i squared C then。

 which is the last major。Gpher role that we talk about in this class。

The intratra integratedrated circuit。Nobody has ever called that that every year I forget what's called。

 it this called I square C or I2C。Um，U the。This too is， you know。Raised up a little bit but。

Not all the time but that's usually less's where the I squared C comes from。

 so there's some reading if you're interested， so what is I squared C？

So this was a standard that was vented by Phils in the early 200s because they wanted to be able to have a different serial communication protocol to talk to all the chips on television and now this is the de facto two wired communication standard if you only want to use two wired okay plus ground this is the standard that you need。

嗯。Now it's very common to have peripherals and used it for embeddedted devices like all the major manufacturers support it。

 it's just the trick is that each time that they want to，Oh， no， it's since 200 no licensing fee。

Oh wait， that's not true So every time that this Texas instrumentnstru or STM wants to make a peripheral that has a certain address associated with it you'll see and that address just has to be registered in at least a database so there's no overlapping addresses and you don't want to have two devices on chip with the same address as no to talk to。

So after 2006 they got away from the licensing requirement for， I think the mic controllertrolls。

 however there's still a fee-- oh so the licensing for the IP。

 the intellectual property of the design they got rid of。

 but you still need to acquire an IC peripheral， I guess is not an XP。

 which actually costs something。So if you want to make a new I squared C peripheral device。

 then you're going to have to register it and make sure this's an over conflict。

So this is the general topology here， you have a controller， you have device one， device two。

 there's only two lines， zero data line and zeroclock line。And now has these extra resistors up here。

Okay。So each device has a unique 7，10 or 16 bit address associated with it。

Zero is for broadcast it' not used that often， has external interrupt or external pull ups。

 and those are to return the line to high， so these things are open drain。

 which means they pull the line down， but they're not push pull so you cannot push the line high。

 is only returned by those resistors。Which means that the size of those resistors actually controlled。

 determine the speed of the bus。Does anybody know why a resistor would determine the speed of a communication bus？

Yeah， isn't it。we can return to the Lake Max voltage， yes， it is， and what's the defining factor？

Each pin has a capacitance so the resistance in the capacitance forms a time constant that determines the right time exactly I'll just repeat that so and we'll actually see a little example of this but here there's a bunch of little capacitors they call them parasitic capacitors parasitic in the sense that nobody designed them nobody wanted those capacitors there but they exist and so each GPL line has little capacitor effectively to ground it's generally the gates of your transistor CMm transistor make a capacitor to the ground plus your pins and everything and so that limits how fast it can charge back up because you have to charge this capacitor and these things are thing pointed up so now you're in the race with RC discharge RC charge about how fast your device can go which seems like a horrible design but they were actually smart enough there is a reason for it but now you're in the mode where you have to choose the correct resistor size to go certain speeds which is a wild idea。

So inside here are your open drain devices， so this is just a transistor gate。

 you may not be familiar here they put a diode here。

 so every NmoOSs and Pmoss there's an inherent diode built into it and these are also probably beefed up a little because they're supposed to be overvoltage and undervoltage protection from static discharge。

 but they're here。And now you have a device where say， here's your clock generator。

 is going to send out square waves here。And then it's going to pull the snow down and then it's going to let go and this resistor is going to pull it back up and that will be determined by your peripheral。

 and then both of these， the peripheral and controller both use the data line to send data back and forth。

 they just have to control and think about and coordinate about which ones going to talk when because they're both reusing this data line to talk。

Any questions so far。Yeah have to worry about the resistive thing for late by why don't we because that's push pull so that's a fully du or yeah it Nss Pmos pair so they can drive it high and drive it low but they also have different data lines here so they have a data line for transmit data line for receive so SDI SD here you don't have that so you don't want to get in a case where one's driving high one's driving low that would cause an error so this is the way to arbitrator across that from a hardware point of view。

we have resistors in the first place， like couldn't we just tie the line directly to VDD。

 but then if it's directly to VDD， then you cannot pull the line down because you can。

you it short out， you' would have to pull you know from a circuit diagram， infinite current。

 enough current that would brown out your system。So here's just an example of multiple devices would go got exactly why the slides here。

 but it's a great slide promise so here I really want to think about there's multiple devices and they only are going to they only have these two wire is connected up which is nice。

 the wiring's easy， these resistors can technically be anywhere on this line it doesn't really matter where they are if it was very long you might have to think about something but these resistors just have to be somewhere in fact if you remember on your microtwi they have internal resistors。

Remember your GPO peripheral had this option for resistors， well for this reason， STM is saying， hey。

 I'll put resistors in our device so that you buy our device instead of our competitors and it will save you two resistors on your PCB。

Is that a good deal？How much does a resistor cost？What how much， 10 cents。

 anybody lower or higher who's higher than 10 cents？Lower than 10 cents。All right， come on。

 give me another number0。1 point lower or higher than 0。1 cents。And volume in volume。Lower。

How about another number lower？で？1。01 that good I could even be less than that it could even be you know hundredth of a cent just because they you just make so many of them there's a machine that makes so many of them and you buy it you have to buy like 3000 or 100000 at of time but you can get those prices very low so it's not really a cost factor or they're saving STM isn't saving you a lot of money manufacturers don't really care about their cost of true resistors that much however it's space on the board that's what they're saving they're saving you space。

Okay。

![](img/348c43aaec3cb5f1066981eae67c444c_36.png)

All right， let's see if I have this one set up。Kind of look through how this peripheral will work。

All right。

![](img/348c43aaec3cb5f1066981eae67c444c_38.png)

And you said it。All right， so here we have an I squared C controller and a target。

 I have parasitic capacitance it's off right now it's not connected。

 and then we're just simulating here we have a clock that is driving it into an NOss transistor and this thing is just going up and down up and down up and down right and this thing is pulling it back up you can actually kind of see。



![](img/348c43aaec3cb5f1066981eae67c444c_40.png)

Advance the current a little bit。You guys can see it polls current down here， right？

When that data goes through。And then up here there's a register here and you imagine this is a register and we're going to put a bit out here and it'll get detected by these gates right here and this is just to convert the analog signal into digital and it'll show you the output and then we can send data back the other way so for example here I can go and send the low out here。



![](img/348c43aaec3cb5f1066981eae67c444c_42.png)

And so that low went all the way through and is registered as， oh sorry。

 I put a high out here and it's registered as a high over there。And if I go back the other way。

 I can send out a high。And。Oh weight it's got to be high， I can send out a low。

 I gave away the problem with this thing already。

![](img/348c43aaec3cb5f1066981eae67c444c_44.png)

All right， so one of the challenges here is in somewhere in here， I forgot where I did it。

 I sent data from this device to that device in here it sent device from back from here to here。

 so if you're looking on your network analyzer。

![](img/348c43aaec3cb5f1066981eae67c444c_46.png)

We' aslloscope and you see this data trace and you're like， well why doesn't my thing work。

 it's hard to even know which device was talking。

![](img/348c43aaec3cb5f1066981eae67c444c_48.png)

Bo， it a pain in the butt to try and debug these things。

The other problem that I felt victim to myself is that the natural state here is that the line is high so the controller can go through and send data。



![](img/348c43aaec3cb5f1066981eae67c444c_50.png)

Great， the receiver consent data or the peripheral consent data。

 but if the receiver is pulling the line low。And some other device gets on the line， see。

 I'm toggling this pin and the line's not going up。Right， because the。This peripheral has。

know an illegal thing is just pullinging the line low， so now this thing is hogging the line。

 I can't send any data back and forth as another error condition of this bus structure。



![](img/348c43aaec3cb5f1066981eae67c444c_52.png)

Now， the benefit we get is only two wires for end devices。

Nobody's raising their hand and saying this is horrible or I'm confused， so now I'm concerned。

So since the committee issues of。すで。youve done additional hardware or software。

 you have to there's an arbitration scheme where the controller needs to look at the line first。

 make sure it's high， pull it low， check to see if there was actually able to pull it low。

 and then it assumes it has control over the bus。But if it tries to pull it low and it doesn't go low or I think actually they pull it low and try to raise it back high on the first bit it tries to raise high。

 it's making sure that it actually goes high and somebody else could have controlled the bus yeah。

What's the bottom part doing and why is it not connected to the top this what's this this is the clock？

Is it the clock line， we're seeing it's wiggling over here？光形 to the。Yeah。

The target can't generate a clock， only the controller can generate a clock。

And then the controller or the peripheral， whichever I decide by clicking these buttons is sending data back。

What do you think about that？I said depending on who clicks on what button to send send to that's the problem。

 isn't it sounds horrible want。Sos like who decides that？

So it should be the controller this decides who's talking when right。

 so the controller is going to send out an address request that's going to send an address over here。

And then this thing says， okay， you want me to respond。

 then it'll send out clock signals for the send data back。

 but it could be that there's multiple in this particular protocol you can have multiple controllers and now the multiple controllers have to fight it out through this arbitration scheme about seeing if the bus is empty or being used or not to figure out which controller can use the bus。



![](img/348c43aaec3cb5f1066981eae67c444c_54.png)

But usually if it's just one controller and n peripherals， the controller is going to say， hey。

 I want you to talk， and then it's going to send out edges that only that thing should be talking back。

What if what if这。Target。Would want to like talk to each other at the same time then it will not work it doesn't nothing the thing doesn't blow up right so if I pull this thing low so i'm low and now all of a sudden the target wants to talk it just can't do it。

It's just not effective。I'm toggling it， but it cannot pull this line high。

 there's no way for the target to force that line to go high。You agree with that yes。

 okay so now we're this an error condition but the nothing blew up it's not like you have a short to ground or anything this is the only way that the the controller can be receptive to。

Be getting stuff as if they have their output rank high， correct？

And so now the controller has released the line， it's not sending any data。

 it's going to send over some clock edges， right usually I should have I don't have this particular device set up the best。

 usually it's only eight clock cycles at a time，88 or 14 or 1 is' not always sending out the clock。

 but now it' sending up the clock and then the peripheral。



![](img/348c43aaec3cb5f1066981eae67c444c_56.png)

![](img/348c43aaec3cb5f1066981eae67c444c_57.png)

And send data back as it sees fit。It sends out eight'clock eight cycles。

 there's data and now can be transmitted to the other side。



![](img/348c43aaec3cb5f1066981eae67c444c_59.png)

，If you have multiple controllers， how do you decide which one is？



![](img/348c43aaec3cb5f1066981eae67c444c_61.png)

And so they have to find it out， have multiple controllers。

 basically controller Asa wants to have access to the line。

 it looks to see if anybody has traffic on the line。

 it pulls it low and makes sure it is getting pulled low and then the first time it releases it has to make sure that it can be released if it's not being released then it has to back off because you're assuming some other controller came in there and try to do a task and so each controller has to have a little bit of logic to give up the line when no data is going through it。



![](img/348c43aaec3cb5f1066981eae67c444c_63.png)

![](img/348c43aaec3cb5f1066981eae67c444c_64.png)

Yeah， so when you're trying to send data and you're holding the line。

 you're only holding the line when you're when you're trying to send the zero correct。

 is that a problem or？And you're letting the line high when you want it to be a one。That's great。

 ones and zeros， we figured out how to send ones and zeros。Ones， zero。

It just happens to be that the mechanism for driving this line high isn't the controller because there's no pmosqui up here is's this pull up resistor over here。

 that's fine， logically it still works。Okay， if you're if you， if you have。

 you're trying to send a one， yep， and the other targets are trying to talk to you at the same time for whatever bad bad news bears。



![](img/348c43aaec3cb5f1066981eae67c444c_66.png)

But a target should only be talking when it's been told to talk。



![](img/348c43aaec3cb5f1066981eae67c444c_68.png)

And the part I'm not and how is it told to talk first， the controller says， hey， address， whatever。



![](img/348c43aaec3cb5f1066981eae67c444c_70.png)

Add Xxx， tell me the information stored in this register。

And then it will send that back on the next clock eightclock cycles。

 so the targets don't get to choose when they talk。

Only the masters are at the controller's control when the bus is activated。



![](img/348c43aaec3cb5f1066981eae67c444c_72.png)

Cho which address to tattoos through SDA。Theres the episode。There's no address line。

 this is the line， this is the only data line。Yeah， it sends all the data， address data， data， data。

 everything through the data line。So it's nice in the sense that， hey， I only have to have two wires。

It' just that you have to do a lot with those two wires， yeah。So you said。

 you said there's a problem if you have multiple controllers， yes。

 with this I mean it's they have to be the controllers have to be responsible to back off when they see the buses busy when it's not them acting on the bus。



![](img/348c43aaec3cb5f1066981eae67c444c_74.png)

There has to be extra logic built in。All right， so let's talk about these resistors。

 so these resistors here you know they make nice square waves。

 but the reality is that there is capacitance on these things and what did I put on here like this is like 500 nanofarets。

 that's pretty reasonable for the amount of capacitance that would be on a bus line。



![](img/348c43aaec3cb5f1066981eae67c444c_76.png)

![](img/348c43aaec3cb5f1066981eae67c444c_77.png)

And so you can actually start seeing that here， we start seeing this little arcing right。

 so this is the RC charge up now these clock look pretty good。



![](img/348c43aaec3cb5f1066981eae67c444c_79.png)

But and if I send data over。You can see how come on the go。



![](img/348c43aaec3cb5f1066981eae67c444c_81.png)

You can see it took a little RC charge up time， that's fine。 but if I start increasing my。



![](img/348c43aaec3cb5f1066981eae67c444c_83.png)

Capacitor size。What is it 700？ですかは？

![](img/348c43aaec3cb5f1066981eae67c444c_85.png)

I don't think I made them big enough， but you can start seeing that I've started increasing the capacitor size and now the RC charge was longer and longer and longer and you could imagine we could get to the case where the RC charge up time is so long there's so much capacitance I would miss my timing so let's just go here and I'll say this is 10。



![](img/348c43aaec3cb5f1066981eae67c444c_87.png)

![](img/348c43aaec3cb5f1066981eae67c444c_88.png)

And now I'm trying to get a clock， this clock period is trying to be this。

 it didn't even get wear VDD over two。

![](img/348c43aaec3cb5f1066981eae67c444c_90.png)

It's just not possible for the bus to go this fast， it cannot meet this timing requirement。

 but let's make it meet this timing requirement， so I'll go over to here。



![](img/348c43aaec3cb5f1066981eae67c444c_92.png)

And I'll increase the rate right it can't pull up， this resistor is not large enough to pull this line all the way up。

 so let's increase its power and I'll give it， let's say 500， oh no。0。5 k。Oh。

 it did a little bit better。These are just made up numbers right now Ill give it 100 ohs that would be a crazy amount but still here it works right here I'm able to get it all the way up and I'm able to meet I'm actually not even able to pull it down low enough because of this internal resistance but head made up numbers it doesn't really matter I'm really showing you hey if you have too much capacance decrease the size you resistor to cause it to come up fast enough there's this trade off you this is why you want to go to faster data rate on your bus well that's why on that previous slide we had different resistor values for different speeds。



![](img/348c43aaec3cb5f1066981eae67c444c_94.png)

![](img/348c43aaec3cb5f1066981eae67c444c_95.png)

![](img/348c43aaec3cb5f1066981eae67c444c_96.png)

No questions。Okay。Yeah。呃So the the stream data you。Start with a learning。

Because otherwise if you just like keep it high， you can't oversha it between like it being one on the first bit versus it just yeah。

 let let's look about the so this is just on bit signaling right now。

 let's go over to like the Mac layer， we'll do that next。Kind of see what that looks like。



![](img/348c43aaec3cb5f1066981eae67c444c_98.png)

![](img/348c43aaec3cb5f1066981eae67c444c_99.png)

All right， so the starting sequence here is that you have a clock， the clock is normally held high。

 I know in that last diagram we showed a clock going all the way through all the time normally is only clocking out for the bits it's trying to receive so as pulse is just like SBI。

 the starting sequence is SDI SDA is pulled low。Then the clock goes high。

 so this is starting to tell the peripherals， hey， look there's something's going to happen。

 this is the sga sequence they're looking for to make sure everything works。

Then this is the most wildest clocking scenario I think I've ever seen。

 and that is that the bit transition is not， is not clocked in or out on the rising or the falling edge。

 it's in the middle。So the clock actually occurs inside the data， both edges。

 the rising and falling edge happen to be inside the clock。Okay here， here， here， here。

 so that means you know， so here， for instance STA sending data out and then the clock is going inside so when the peripheral sending data back。

 it sets the data up， looks for the transition， and then waits a little period of time。

 clocks the data， makes the transition of the data down。So it happens on both sides。U。W。Yeah。

We talked about this one。So during data transition the controller is constantly checking to see if the SDA voltage matches what it's sent。

 so here SD is either going to be high or low， it's trying to check to see is that actually true because it could mean that some other peripheral or other issue happened。

 it's trying to take controller of the bus and if that happens it's supposed to end its communication that cancels that packet and then restarts waits for the controller to be available again。

So here' is an example of。嗯。A typical。Transaction， so here we have SDA and SEL。

 so we have a controller that's going to send out data it sends out address bits because the arbitration mechanism is that each device when its manufacturers has an address burned into it。

 it's not unique per device is unique per class of device so like all or ADM。

 not ADM say analog devices particular accelerometer。

 say whatever all of those any productsQ will have a unique address。

 but not every device has a unique address， there's some where you can control the last bits of the address by shorting or pulling a particular pin up to ground or up to VDD。

Anyways， we have our SART sequence， we're sending an address bitit out so this all this does is just say。

 hey， that device over there， this is the one I'm talking to but what do you want to say to it？

That's typically followed by the data Ro， so here address and then data and now we're sending out eight bits of data。

Now if you want the peripheral to talk back to you， you'd probably send it up， you send， hey。

 address this， get me some piece of information is contained in data。

 and then it will send out an address with blank data bins is send out edges and now it's the peripheral's job to fill in these data this data which goes back to。

The controller， so this way the controller is the one that's always sending out the address bits it's not the peripheral that's deciding where to send it。

 it's always the controller， so this is 90% of how arbitration is taken care of because first it's the address。

 but also control over the bus is defined by the controller not by the peripheral。

The other interesting thing here is in this packet that's being sent this address packet that's being sent from the controller to the peripheral。

 the peripheral actually responds inside this packet。

 the peripheral responds that it acknowledges this packet so this is an act or a bit sometimes we call it NAC not a knowledge and what happens is you don't know if that peripheral is actually on there so you send an address bit and then the so this is controller controller controller controller controller controller controller read write read write bit controller and then it's the peripheral a pulls that line down saying yes。

 in fact I've acknowledged this message because if it doesn't acknowledge this message there's no reason to send the data the data doesn't exist I mean there's nowhere for the data to go so oftentimes what students will do is they'll look at their data and they'll say every time I talk to my peripheral at NAX every single time this bit is high。

Why is it not responding， it could be miswired， the same thing happens if the device isn't even on the bus。

 it will naack because the pull up resistor is pulling it high。How feel about that。

guys give me the looks like this guy is this talking。

 and don't make any sense he's lying about how electronics work。

I was wondering given that this setup。后。其实。Ex expert regardless of M mode that we talked earlier。

 well， that's for a whole different protocol。As for a thing called SPI。

 we're talking about i squared C。Yeah。Wait， so is the second part of that diagram coming from the peripheral or is that also a controller？

So the clock lines are all coming from the controller。If it was a right bit here。

 then the data comes from the controller， if it's a read bit， then the controller wants to read data。

It's coming back。Does that act when it's reading？This act yeah。

 so this act says I acknowledge your address， I'm here I can do it this act says I'm done writing the data。

The controller acts to oh sorry yeah， sorry， the controller act says， yes， I have the data。

Is the other thing that acts Yeah could we explain again what happens when it's fact not connected so very？

Oh， when the device is not connected and the students are confused and I'm confius too when I was a student。

 so if we go back。To this， you guys can see that。

![](img/348c43aaec3cb5f1066981eae67c444c_101.png)

So the challenge here is。Let me un'do this。

![](img/348c43aaec3cb5f1066981eae67c444c_103.png)

Ron， so let's just say this thing is going to knack right， not knowledge or acknowledge no。

 I didn't receive this or it's not me for。What could NA else mean address not found， let's say。

So you could be writing， you can have you set up your hardware you say I'm writing the right address。

 I've looked at my logic analyzer， I'm sending out the right thing。

 I looked at my code I'm 100% guaranteed， I'm sending out the right address。

 why is this thing not naing well this thing pulling allowing this thing to rise high to send out a one is the exact same of this thing being disconnected by disconnected that line is still high。



![](img/348c43aaec3cb5f1066981eae67c444c_105.png)

![](img/348c43aaec3cb5f1066981eae67c444c_106.png)

Because the thing that pulls it high is that resistor， not this， this can only pull low。SheLike，Nope。

 I don't believe you。

![](img/348c43aaec3cb5f1066981eae67c444c_108.png)

So ask your question again。It's just generally lost in how it's going to work。Plays with this。

go home， play with false dadd， push the buttonts up and down， itll make more sense。Did you take 215？



![](img/348c43aaec3cb5f1066981eae67c444c_110.png)

You you got all the core that you need， you just the circuit，'s just going up and down， it's great。

Thank you。

![](img/348c43aaec3cb5f1066981eae67c444c_112.png)

Yeah。关音乐。Why do we need an act？I don't know these people at Phils forced us to have an app we have to deal with them why do we need an app maybe the question is what does it do for us。

 this tells us the controller right that the peripherals actually on the bus and is ready and available to do this next part。

 there's no reason for the controller to send data when there's nothing there to receive it。😡。



![](img/348c43aaec3cb5f1066981eae67c444c_114.png)

So it saves time， saves time， it ensures that when you're sending data out。

 there's actually a thing to receive it， it could be not on the device， it could be powered down。

 there could be a lot of reasons why the peripheral is not able to respond， it could be busy。

 you could have asked it to do a thing and it needs a certain timeout and it's just not ready。

To do a task。翻这。When you。You don't know why you need one because usually the controller's smart enough and capable enough to know that。

 hey， I was expecting data， I didn't get data， I can ask again。

 but this is just a feature of the protocol where it's saying here I'm done， I'm not done。

It's just an option。Okay。The对对对。Y不。This is what normal i squared C data looks like。

Celloscope plot here we see the start sequence where SDA was pulled low before the clock。

 there's a little bit of timeout here， a little bit of time now you see the clock pulses。

There's eight here there's nine， there's knife for the a bit sorry then there's eight here and then there's a little bit of this is between the packet so it's gone back high。

 it's released the bus essentially then it doest another start event and then you can see where each one of these clock pulses is in between those data and here you know obviously you can't see the transition but it was one to it was zero zero here you should be able to walk through yourself through this and decode this bus traffic and be able to come up with those as and as。

Yeah。我 is time傻。Why is the top stop Yeah it only yeah I confuse you with a false sta clock only sends out bits for data that's going to be clocked in。

 it's not sending out a clock， it's not sending out a clock for bits that don't exist。

Just like same with SI。아。Yep。Okayai， so you don't need a serialreal protocol。

handand shaake thing wherever you can just turn on the clock。Yeah。I mean， when you say handhaking。

 you mean there's no chip select， right？What do you mean by hand shaking？到一去。

Like you are like start with like a low bit Yeah， well there is that we have a stark condition where SD has to be pulled low before the clock is。

So you have to do start condition and it will just start when you throw the clock。Yeah。

 so here's the clock， here's a start condition so there is a start condition。

 there's a stop condition right， the clock is pulled up high and then SDA is pulled up so I mean there are some conditions it's not。

They're just different than an ice squ sea。BI you are sorry。When the peripheral is sending data back。

The microcontroll is anticipating land's ending back so it's going to drive the clock then， correct。

Does that defeat the purpose of like the peripheral wanting to talk to the controller on its own the peripheral cannot talk to the controller on its own？

Two controllers could be on the bus， rare condition， I highly encourage you don't do this。

 but you can。The protocol allows it， in that case， two controllers could try to be taking control of the bus and there's an arbitration scheme to kind of deal with that that's where he is trying to look at every bit is sending out and making sure that that bit is actually being sent out。

 but the peripheral cannot initiate conversation or have to have an external wire to do an interrupt。

Okay。Yeah， okay， talk about that。Yeah。But see okay so for your i squared C on your device you have four i squared C modules which seems insane to me again you have a really big chip but what it does allow is oftentimes you want to make say you want to have two of some chip and you want to have some distance sensor on your device but they both have the same I squared C address this is a challenge the challenge that comes up all the time because they are both say IR distance sensor from。

Miron or something。Miiccroron has only registered one address。So now you want to get two on there。

 well if you have put them both on the same data clock and data line then they're both going to try to respond it's going to be a mess and it won't work。

 so what you need to do is you could have a couple different solutions one is you could have multiple isqua C modules and then you put them on two different pins you have to use more pins for this。

 but now you can talk to both these devices that's kind of maybe the cleanest way if you have the pins。

 the other one is these device translators where you go right to them and either through hardware like a resistor or something you have a translator where you send an address and then the translator will turn it into the correct address and then from the peripheral's point of view or for the controllert's point of view there's two different two different addresses even though they go to identical devices over there so there's these hardware tricks you have to get around。

Anyways， and for your projects， you do not have to worry about that， probably。嗯。Yeah。

 so on the you have packet of air generation and it will validate that you've got NAs and ae when you were supposed to。

 which is nice， I think you can send interrupts based on that as well。So the pros and cons。

 so easy to wire only two wires plus brown， widely supported is very common now to get almost get every flavor of peripheral that you want in either I squared C or SI oftentimes are both baked into the same piece of silicon and there's this a toggle bit。

 some pin on the outside you have to raise high or low。

 the cons is this open collector which makes debugging challenging。

 speed there's a speed and power trade off， which is interesting。

 the max speed is defined by resistors， well let's just say resistors and your parasitic capacitance together。

Not by the performance of your chip， and there's no hardware arbitration and that really helps you solve that problem in the sense that there's no chip select line is all has to be done through the protocol。

So to review， let's see， we talked about i squared C or， oh man， we're not going out have of time。

Yeah， I will do it real quick， I'll make you， it's horrible， now I will do it。

We'll do it for next class it's fine I'll do the review now so for chip you are is chip to chip communication typically there's only one transmitter one receiver one device another device there's not multiple devices but now there's no idea of master controller here remember they both think that they're the transmitter they both think they're the receiver there's no mixture here。

 there's not the Tx doesn't go to TX you go the other way it's one of the oldest protocols and there's no clock so this is really good for say talking from your device to a USB peripheral so something will translate you are to USB or you are to wireless like XB or Bluetooth the other parts are there's no clock so these devices have to do clock recovery on their own The reality means that you probably aren't going to go as fast this is not going be the fastest protocol in the world but it's fairly easy to implement and only to to wires。

We talked about SI。So here you have serial data out。

 serial data in from the perspective of the controller， controller sending out a clock。

 and the controller is going to select which device to use。

 this is probably the most like the APB bus peripherals that we talked about in memory MaIio。啊。

And then I squared C， that cut out of order， open collectors and each device has unique address。

Zero for broadcast and the speed is defined by hardware。And we will end there。

And we'll have a worksheet when you guys come back on Wednesday。All right， thanks。



![](img/348c43aaec3cb5f1066981eae67c444c_116.png)

不行。