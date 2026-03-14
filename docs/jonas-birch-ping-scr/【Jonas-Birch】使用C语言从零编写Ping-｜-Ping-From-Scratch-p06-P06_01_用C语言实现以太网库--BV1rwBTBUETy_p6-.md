# 【Jonas-Birch】使用C语言从零编写Ping-｜-Ping-From-Scratch-p06-P06_01_用C语言实现以太网库--BV1rwBTBUETy_p6-

![](img/71193a65bb6b908f70e6c24891d2d8d3_0.png)

So， guys， welcome to today's show。So today， we're gonna begin implementing Ethernet。

So we are going lower level than I。And I'm going to talk a little bit about that。

 but first I'm going to talk about another project because I'm going to use that as a base when I implement this。

And that project is called Ping from scratch。Where I coded a p utility using raw sockets。

And this code is quite good to use， for this purpose。



![](img/71193a65bb6b908f70e6c24891d2d8d3_2.png)

I have a function for receiving an IP packet， and I'm going to rewrite that entirely。

 but some other stuff is quite good， and that is the constructor function which creates an IP data structure。

And when we have one of those with the I addresses and whatnot。We can run Eal I P。

 which turns this into a format that can be sent over the network。

 And I have the same for the ICM as well， which is the protocol involved in Ping。

 So I want to do something similar with the ethernet。So we will have an a construct function。

 which creates an ethernet data structure， which contains the stuff that we are interested in。

 So if we look at the header file， we have two data structures of each。

 So we have an I data structure， which only contains interesting stuff like the kind。

 the source and destination IP addresses and so on and so forth。

But in order to send it over the network， we need to have a more involved data structure with more fields。

 so。Some of them can calculate it。 and some of them， we just juice default stuff。

And then the eval function turns this into this。 And I want to do the same for the ethernet。

 And then I want to turn it into a simple library that we can use to send any protocol and receive any protocol by reading a writing directly to the network card。

 basically。So that's the general idea。 So let's get to it。

 I'm going to begin by just making a copy of the entire project folder。



![](img/71193a65bb6b908f70e6c24891d2d8d3_4.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_5.png)

And since this is going to be based on Ethernet， primarily other protocols as well。

 I'm going to call this new project Esther。So I'm gonna to copy the entire ping folder。

Into the asster folder。Clean up a little bit。And let's。Change ping dot C into Ping into。Ether。

Let's see。And pinged of H。Into Ether dot8。

![](img/71193a65bb6b908f70e6c24891d2d8d3_7.png)

And then I'm gonna open up this。Project folder inside of V code。

And I'm using this sociopath SP client in order to code remotely since I'm using a Linux server。

Alright， so let's start。But， just。Changing the make file。 So it reflects our new names or stuff。So。

 pinking is going to be Ether。Same here。Sorry for the background noise。It's probably my。

Brothers wake up。Larn block。Alright， something like that。 And if you're running an older GCC version。

 remove this。Yeah。C 23 think。 And by the way。

![](img/71193a65bb6b908f70e6c24891d2d8d3_9.png)

You can download these ping files from briefbodobirch dot com。



![](img/71193a65bb6b908f70e6c24891d2d8d3_11.png)

Okay。So， let's open up these files。Let's just。えと？Fi names here， as well。And maybe we should do。This。

 instead。And then， we can take。Dash I dot。 So we use the current directory as a。

Include directory so we can use these。This syntax。Okay。

So I'm gonna start by just deleting this receive I P。Function。

 because we're gonna use a different one。HKP shall I P and。team check some。Think the rest is。

Probably fine。And we can remove these main functions as well， because。And this sand ping。

 we can also remove。I guess。对。Okay， so now it's a little bit cleaner。

And we need to remove the functions， signatures， as well。So。This we can keep。Copy check some setup。

Something remote。Send I P， receive I。We can keep the ICP stuff。I'm not sure if we're going to use it。

 but it's good to have。Alright， so let's begin by designing。Our data structure。

So we're gonna have astruct S Etherna。And what do we want to keep in here。

 We want to have some kind of type variable here， as well。So that's basically。

 that says what the network layer protocol is。 So if it's I P or。Possibly something else。嗯。

And then we wanna have Mac addresses。So let's say we have some data type， which is called math。

And then we want to have a source address。The destination address。We need to have a payload。做咩。

And indeed。ray。Without a size。 So it's variable size。嗯。And maybe we can have。Some kind of。

What's called。PD U type or。嗯。Frame type， I think。So maybe we can change this type into。Protoical。

And we can have。Some kind of。Frame type。T。Is that。And we want this to be packed。

 so we don't have a lot of these。S rose in between。And let's type that。St。S ethernet。

 and this is going to be ethernet。Maybe we can just call it Ether。Like so。Okay。

 so we need to define what a frame type is and what a Mac address is。So， let's say。

Frame type is an enum。Yi。Frame tag。AndAnd there's a couple of frame types。

Let's say we have a an unet。 if we haven't set this yet。And。Then we have Uniicast。

Which is when we send a frame to a specific。destination。We have broadcast。

Which is when we send it to the entire local network。And then， there's。Muldcast。Yeah。

That's when we turned it to a groove。Of。嗯。Hosts。And there's also something called unknown。

 which basically behaves like broadcast。 It's just。嗯。When it doesn't know。

The Mac address I didn't want to send it to basically。嗯。

We're probably only gonna use Unicast and broadcast， but let's keep those two here， just in case。

Let's make this packed and we'll type def Eum E frame type。To frame type。

And how are we going to represent a Mac address， So a Mac address。For those who don't know。

 looks something like this。So。In Windows， it's usually represented as six numbers with a colon in between。

And each number。Is。1 by the H。Mhm。😊，And that's often represented by two hexadeimmal digits like this。

嗯。And this is the hardware address， So every network card。And every computer and。

Different devices have its own Mac address， which is globally unique。And that is。对。

Every vendor of hardware。A is assigned。These three first fields。



![](img/71193a65bb6b908f70e6c24891d2d8d3_13.png)

嗯。From Iana， I think。Internet design， the numbers and addresses or something like this。And those。

Three fields they can decide on their own。However， I won't represent it in this way instead。

So it's the same numbers， but no columns。And I group them as two bys each instead。

 with a dot in between。And this is the Cisco style。Of representing them。

 And I think it's a little bit cleaner and easier to read。But， that doesn't matter。

When we think of it。In a low level， how we going to represent it in our code。It's still six buts。

And we don't。 And， that means 48 bits。And we have integers that are 32 bits and 64 bits。

 but we don't have any 48 bits。In theger。So how do you represent this thing。

I think we're gonna create a structure。

![](img/71193a65bb6b908f70e6c24891d2d8d3_15.png)

Yeah。Let's create as strategy as Mac。Yes你咩。And inside of this， we have an in 6464 B integer now in。

What do I call these things， Yes， in 64。And。And in 64， by the way， is an unsigned， long， long inn。

This is the address， but I only wan to use 48 bits。AndThis is the whole structure。

It willll make it packed so we don't fill it up with zeros。And then， we type F。Struck。

As Mike to Mike。来首。And I want to start with creating a show function for the Mac， which。Is going to。

Print out。A Mac address。

![](img/71193a65bb6b908f70e6c24891d2d8d3_17.png)

Yin。This format， because that will make stuff a little bit easier for us。And this is 1，2，3，4，5，6，7，8。

9，10111213，14 bys long。

![](img/71193a65bb6b908f70e6c24891d2d8d3_19.png)

Let's say， we have。in the。So。Ether。And it's going to take。A Mac pointer， maybe。Yes。

 it should be called Xo Mai。So， basically。We give this。A mac data structure。 and it returns a string。

That we can print if we want to， or using， any other。O。Alright， so let's start there。

So we want to have an in a。小门。AndIt's going to take。In my address。嗯。And let's。嗯。Let's see here。If we。

Don't have a Mac。Well just return an error。So0。We're going to need an in8 pointer。嗯。

We need variables for the different types with different parts of the Mac address。

So let's say the Mac address is A A。B bc。CCDDE。FF。We're gonna have an in8th， A，B，C， D。Yes。

And let's also copy the。In 64 to a local variable to make things a little bit easier。嗯。

So let's say this is the integer version。So。Integer is going to be equal to。嗯。Let's see here。So。

 we take the address。Address。And we end it to。 Let's see here。So， one。2。😔，3。For。5ve。6 beds。And。

ACo of zeros。The beginning， so this is8。So， this will take。Only the 48 bits， in case。

There's something else。There。I don't think this is strictly necessary。

 but let's do it just for the sake of it。And now we need to break out each part。So， let's start。Yeah。

We take the integer， and we end it with。F。And， that's it。And to take the E， we added to。F F。0，0。

 which means we take the next bite。And we also need to push it。8 Bs to the right。Because。

At this point， we take these two bites。Which means it's going to return。生定你。诶。Yy。0，0。

And we need to get rid of these zeros。So， we're just。Wsh these8 a bits to the right。

 And those two zeros will fall off the edge。So something like this。And then we continue on。 So the。

It's going to be the same， but we add two zeros here。因为。呃，对。He， dear。

AndThen we keep on doing the same thing。So，32。And finally， we take the a。Shes。Yeah。40。8。Well。

 we'll see won。So let's say we have broken out all of this stuff here。

Now we need to create create a string out of it。So let's say， we take。The P， and we。明咩了。😔，16 by。Sir。

 that we have a P。And then we zero out that pe。And then we can use S and print S。

To put something inside of this pe。Maximum 15 B。Okay， so we wanna have hexadeadeimmal digs。2。Y。😔。

This is going to be an H， H X， which is an8 bit。Number。

And then we're going to have one more of these。And then。And do。Pulous thing。I never do that， try。And。

😔，Once again。So we have the first two， then a dot。Then， we have the。Second2。And a。And then two more。

And we wanna have them in the order of。I guess it would be the reverse， right。So， F E。Dc。B。

And then we return P。Something like this。 but we also need to have a constructor function so we can create one of these Mac addresses。

So that will basically be all of this in reverse， right？Because we want to give it a Mac address in。

The string form， don't we。吹的 short儿。😔，But， let's do it like that。So。😔，We have this showm function。

And let's say， we have a read Mac function。Because it's not。

We don't really know if we w to have this only as a string。Input。

Maybe we can do some kind of magic here。A little bit of。What's it called。Polymorphism。

That could be kind of cool。So let's create two functions instead。So， let's say we have one。

Which is called。Well it's going turn了呗。Let let's say the first。Is a read。M。String。

In this stage string parameter。And we'll also have one， which is read me。Yin。And this。Takes。6。😔。

Or I guess。And then， we can have。诶。So。It's not going to be a function， but we will have a macro。

Which we just call make me。And this can take an argument X， which is either a。A string like this。

 or an integer。And。It will call the right function， depending on the input。

So a little bit like well function overloading。 I think the correct term is。But first。

 we need to have something which。Does this。 So let's start with an int， which is rather easy。什咩。Read。

Ying。😔，In 64 address。Have a Mac structure。そです。嗯P。And this output。Mmhm。

And let's allocate for one of these。 So let's say we have an。16 size。And make is equal too。

The Mac dress casted malllo。And we take the size。First， we need to calculate the size。

 and it's just the size of astruct S max。We sir that we havet met。And now， we can just set。The们。

Addres。No。😔，We called it。Something else dealing。Out to put。

So the output address is equal to the input， and we do the same thing。We end it with。晚安。え。Double 0。

 and then1，2。3。4，5。6。return。Output。Okay， so this was rather easy。And。

The other function will be a little bit more involved。So this is going to be a readmer from a string。

Then， we have an end a。Uposed。Still haven a map。Outper。And beside size。But this time， we need to do。

Similar to what we did up there。But the other way around。So let's say we still have in 64。

In the rear。And we need to have a different parts。あです。In， ABC。异议啊。We don't have。Yper。😔，In return。😔。

Aro。And I didn't do this check up here， because an int。ItCan be 0， and that will create a0 map。

But if we don't even have pointer， we can't really do anything。Alright， so let's see here。

So now we have a string input。And we need to passse that string。Let's say we have。Pointer。Bye。And。

The nice way would be to do this inside of a loop， but。I will be a little bit lazy， you know。

So let's set P equal to the input。😔，We need to parse the hexismmal digits， as well。

So let's say we have some X and Y。So if we have isolated， let's say the A's。We wantna break each。

Character into x and y。So this would be the bite。And then we'll have X and a Y。嗯。

So let our bite be equal to the current。Pocision of P。 but that's not entirely true， is it。没有。

X will be equal to the current position of P。Then we can increase this。Then we can set y equal to。

And at this point。The next， maybe I should type it in the correct format。

Ca we want it in this format， right。So。So now we have read the A's here。😔，So at this point。

 P shouldn't be。0， because if it's 0。Well， it can。Let's see。No， it cannot be。

So if we don't have a P at this point。😔，We can return an error。Let's we say， we also have an。

Ex primeme。And the why prime。Because， currently。And。The x is going to be equal to an A like this。

And why。In this case。Wellson A， but it's。It's a ASci character A。

 We need to turn this into exodadecimal digit a。Let's say we have some function for that。

So x prime is going to be equal to the hex value of x。

And why crime is going to be equal to the hex value of y。And now we need to assemble it together。

So the byte is going to be equal to。So， we take the。W prime。And， we push it left。For bit。And then。

 we add。The X prime。I think that is right。Yeah， something like this。And then we can set。 So。

 let's see。Then we can set A equal to the by。And then we need to repeat that。

 We also need to make sure that the next character is。Well， we'll do the same once again。

 but then we want to check that it's a dot。So maybe we should have some kind of parry to bit。

SoLet's start by setting the parity to folds。And when we are done here。YouGoity。Equal to。Well。

 it's going to be。X or equal to。True with。So this should toggle it back and forth。

Because if parrot is false。So，0。If we x or。Sro with one。 we get one， which is true。

But if it's already true。We ex or 1 and1 and get0 or false。 I think this would be right。

And before we do that， we check if we have。The pary by set to true。That means we have done this。

Twice。Which means we want to check that we have it。At door。走 if。If P plus， plus。It's not equal。

To个 little的。Then we return an error。This function became a little bit more involved than I。

Anticipated， well。Never morning。Alright。So， then。😔，We will take this and turn it into a。Macro。

 so we can repeat it。Without。Affecting our dryness。Well。Let's do that now。Basically。

 we're gonna have something like。Dfinine。😔，Let's call this parse。没。Takes in。This we need to do first。

And the only thing it's going to take。Is the output。



![](img/71193a65bb6b908f70e6c24891d2d8d3_21.png)

诶。And let's continue after the break。Did you learn anything useful today day。

 And you want to support this channel。Go to Doctor Birrch dot com flashlash support。

 You can also click the button， Be a member。 Thank you for your support。



![](img/71193a65bb6b908f70e6c24891d2d8d3_23.png)

All right guys， welcome back。So where were we。We were coding the conversion functions。

Where we go from a string or an integer into a Mac dress。And。I created the code here。For a parsing。

Wen。😔，Let's see， one hex digigit。No， one bite。So if we have a Mac address like this。😔。

We are currently。Able to。Parts one by。So， those A's here。嗯。And if。We are。On an even number。

Which we're not。 We're on B number one。嗯。We check if。The next character is a dot。And if it's not。

We exit with an error。So first， we passse the A's。 Then we check if were。EAt the right parody。

Which were not so we will continue on paring the bees。And then were on the correct par。

 which means we will gonna。Check that。 We have this dot。And then we will continue doing this。嗯。Well。

 six times。So let's create a macro so we don't have to repeat the code。😔。

And we're only going to take one argument。 That is the output。

 because the code will be the same each iteration。 The only thing that is going to change is this A here。

This would be a B and a C and a D and so on and so forth。But the rest will be the same。

So let's do the good old wild trick。So， the wild true。Will do do。

Let's not forget all of these back slashes。Maybe I should make some vim script or something。

That lets me add those。Backlashes。If I。Select a block of code。That would be kind of if。

 maybe it's some。嗯。He is code extension， result。Right。So， at the end here。We are going to say。

While false。Which means we are not going to repeat this stuff more than once。So。😔。

Let's take this code look and put it inside of our age。Among our our other function based macros。

We're going to change this A here。To the output。Yeah。Prameter。That should be it， I think。So。

Let's see。 P is equal to N。 Yes， we start with that。Then we're going to do this thing。

 and this is called parse Mac。So， we're gonna parsem。For the a。1，2，3，4，5，6。

And then we're going to do the B and the C and so on and so forth。And hopefully， by the end of this。

 we will have all of these variables filled out。And we are going to return。one。Let's see here。Well。

 we're gonna put it inside of an integer first。So our integer is going to be。

 and let's remove this stuff here。I need to look at this while I do it。うう。

So our integer is going to be。Well， we're gonna start with the a。And we need to push this 48th bits。

And then we're going to end it。😔，With a B。Which we push。呃。SoLet's see here。40。😔，Its。

And the C is going to be 32。The D is going to be 24。He is。No， this is wrong。

You need to go one step lower。 So this is 40。This is 32。 This is 24。16。诶。And at the end here。

 we will just。Do the F without pushing it anywhere。 We can， just to。Show our intent。Push it。

 zero steps。And when we have the integer， we can simply return。 So let's see we don't need。

This outputs variable。Because we already have。This thread here。Which takes。

An antiger Mac address and produces a Mac。Data type。So we can simply return that function。

 read Mac in。And we provide our integer。That's it。All right。

It'll be very interesting to see if this works。Look at this code。It's kind of beautiful， in a sense。

 right。And。Al right， so how do we do this。Let's say we have a main function。We have a Mac address。M。

嗯。AndWe have a string。And here we can put it in so。do。😔，3。Like this。嗯。And then we can set M equal to。

Well， we're going have macro， which selects the right one。 So we should only be able to do make Mac。

Let put the string here。It's also created in 64。So we can print this first。This is going to be。So。M。

Let's also print the inte。0 x。Person。😔，朗狼。哎。So guess。😔，Exend。Serious。And this will simply be the。

Addres。And then we want to set our N equal to。And address。Let's also create。M prime。

So let's see if we can go back as well。So M prime is going to be make Mac。

 but this time we don't provide the string， we provide the integer。Then we do the same。But。

 we provide。This instead， and this instead。And we leak a little bit of memory here。

 but I don't care since we exit the。Program right after。By the way， I remember。 we forgot to。

Do one thing or a couple of things， actually。First of all， the show function needs to。

Have support for our new stuff。So if we want to show a me。We provide the show。嗯。Right。

 we don't have this first thing。 We can add that later， or perhaps。So。We wan to have。M dress， okay。

来 so。And。E well， we haven't done yet。But we want to do something similar for that。different。

Pse function。 So what did we call those。Redm string and redm in。We wna have one。

 which is called make Mac。Takes in an X。 and we want to do a generic。Of x。And if we provide。

And in 64。You wantan to call。F。Mei。No。Readman。So read Macck int in this case。😔，嗯。Ca this tune in 64。

And if we have a string。We do read Markck string。Let's not forget the back slashes。Like so。

And we need to do one more thing。 This hex thing。We need to be able to turn a character。

So a hex value inside of a character。 ask a character。Into a regular hex character。

And I guess we can do that inside of a macro。So let's say we have an hex which takes in an X。😔，嗯。If。

De。Let's see here。If the x is less than or equal to。No。😔，It's more un equal to the character A。😔，沃尔。

If X。Is。Less than。Or equal to the character after F。In that case。We wna return。

What do we want to return。Well， we want to return a0 xa。Minus。mh。The character a。Minus。

The heckx character。Let's see here。

![](img/71193a65bb6b908f70e6c24891d2d8d3_25.png)

Think you need to do this。Here。So。What is the character。诶。61。And we want to turn this into a ta。

So what is 0 x 61-0 x 10。81。And the hex version of 81 is 51。So if we remove 50 w。From our ex。

We will get the right thing。

![](img/71193a65bb6b908f70e6c24891d2d8d3_27.png)

X。Linus。0 x，51。That's the result in case we are between the range A to F。Otherwise。We want to take。

Our x， but this time， minus。A zero as an askky character。Yeah， I think that's right。All right。

 a lot of moving parts here。 Let's see if it。

![](img/71193a65bb6b908f70e6c24891d2d8d3_29.png)

Compar。

![](img/71193a65bb6b908f70e6c24891d2d8d3_31.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_32.png)

Quite many errors， but probably most of these will be removed once we fix。Singularulator。う。X minus。

This。Expected a parentheesis。

![](img/71193a65bb6b908f70e6c24891d2d8d3_34.png)

Right， we forgot backslashes as usual。

![](img/71193a65bb6b908f70e6c24891d2d8d3_36.png)

Exed。

![](img/71193a65bb6b908f70e6c24891d2d8d3_38.png)

We need a comma here。

![](img/71193a65bb6b908f70e6c24891d2d8d3_40.png)

If。

![](img/71193a65bb6b908f70e6c24891d2d8d3_42.png)

Well，3，12。This should be。

![](img/71193a65bb6b908f70e6c24891d2d8d3_44.png)

Dress。Fing to targets and passing， blah， blah， blah，3，2，6。



![](img/71193a65bb6b908f70e6c24891d2d8d3_46.png)

We need to cast this into a。Character。

![](img/71193a65bb6b908f70e6c24891d2d8d3_48.png)

Warning left shift。Cown。Moral equal to。The width。Of the tie。



![](img/71193a65bb6b908f70e6c24891d2d8d3_50.png)

3，66。Maybe we need to do。Something like this。Or no。This， I guess。I need to add in 64。Same here。

I love the dog。Function。

![](img/71193a65bb6b908f70e6c24891d2d8d3_52.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_53.png)

We need to。Have the cast around the a。So like this。



![](img/71193a65bb6b908f70e6c24891d2d8d3_55.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_56.png)

Right， unjust variable 3，4，6。

![](img/71193a65bb6b908f70e6c24891d2d8d3_58.png)

We down to about one page。

![](img/71193a65bb6b908f70e6c24891d2d8d3_60.png)

Conflicting types for main。

![](img/71193a65bb6b908f70e6c24891d2d8d3_62.png)

嗯。

![](img/71193a65bb6b908f70e6c24891d2d8d3_64.png)

Blah， blah， blah， blah， blah，3，77。I guess we need to do this。



![](img/71193a65bb6b908f70e6c24891d2d8d3_66.png)

Cas from pointer to integer of different size。嗯。呃次了没同意。And this was a little bit funny。

 The format expect type， long， long， uned int。But it has long， long unsigned in of 48， O。



![](img/71193a65bb6b908f70e6c24891d2d8d3_68.png)

So let's fix that first。

![](img/71193a65bb6b908f70e6c24891d2d8d3_70.png)

Something like that。

![](img/71193a65bb6b908f70e6c24891d2d8d3_72.png)

Return with no value。That is true。

![](img/71193a65bb6b908f70e6c24891d2d8d3_74.png)

来呀。Okay， so we're done to a couple of warnings。 and I'm not really sure why it complains。



![](img/71193a65bb6b908f70e6c24891d2d8d3_76.png)

Becauseuse the whole point of the generic is to。Let us do what it's complaining about。

But it does not complain with the old stuff we had so stiff。The parenthees。Here it will。嗯。Swe weird。

 what's different。Readed mark in。It 64 of x。And x is an N 64。

What if we weren't casting and just saying X here。Make a difference。



![](img/71193a65bb6b908f70e6c24891d2d8d3_78.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_79.png)

Maybe we can ignore that warning。

![](img/71193a65bb6b908f70e6c24891d2d8d3_81.png)

I'm not sure why it's there。Alright， let's try this out。Okay。And it equal to know。



![](img/71193a65bb6b908f70e6c24891d2d8d3_83.png)

So， it fails。Ping。And what if we weren't starting with a string？

But if we just put in 64 here instead。😔，是。0ro。0ero one。38。FB。99。诶诶。So something like this。



![](img/71193a65bb6b908f70e6c24891d2d8d3_85.png)

Okay， no， something happened。This work。We get the right thing。你 here。😔，And here， so it's just。

 it's just string parsing that。

![](img/71193a65bb6b908f70e6c24891d2d8d3_87.png)

Fail somehow。And why is that？So let's do something like this。 We put this。Right side of the screen。

So we can look through this macro。So。Is that P equal to input。And then we parse the A。

The output is going to be a。And the parity is false。So， we make sure that we。Get。The two characters。

Maybe this is the problem。一个是。ItHas to end some time， right。

 but we should be able to parse all the way to F。No， it at F。It's going to be。A zero here。

So how do we perform this check。Let's remove it， for now。



![](img/71193a65bb6b908f70e6c24891d2d8d3_89.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_90.png)

其的那。这样匙。😔，Allright， so。Ex pointss。To the F。To the first a。In this to the secular。那会说。😔。

For the right value。we order them together。To get them by。The output is equal to that。And if parity。

 which it's not at this point。And here we set it to one to true。So， we have passed the a。

Then we do the B， which is going to be the same thing。Only this time。We have parity。Let we check。

That the current position is a do。If it's not， we return ir， it must be this， right。

That's the only place where wed return this era。So we have a string like this。 A， A， A， A， no， A， A。

 B，B，CC，TD， and so on。We start here。Then we increase and increase。Then we don't check for the dots。

It will increase， increase。Then we do check for the dots。Maybe we can do a temporary thing here。

Let's print。Kurren。😔，Oession。So。😔，You can like this。



![](img/71193a65bb6b908f70e6c24891d2d8d3_92.png)

Then we can see what's going on。对。Do。Nothing。

![](img/71193a65bb6b908f70e6c24891d2d8d3_94.png)

嗯。Okay， so when we have par the F。It's going to be nothing。So， we need to check first。We have a pay。

Something like this。

![](img/71193a65bb6b908f70e6c24891d2d8d3_96.png)

And now it works。

![](img/71193a65bb6b908f70e6c24891d2d8d3_98.png)

Beautiful。

![](img/71193a65bb6b908f70e6c24891d2d8d3_100.png)

But。It doesn't look quite dry。Doess it。I think we need to look through the math。

 but the actual parsing seems pretty O。 It's probably the hex function。

 which doesn't work as intended。So after the break， we take a look at that。1月了边。All right， you guys。

 welcome back， so before the break we managed to successfully or almost successfully parse。



![](img/71193a65bb6b908f70e6c24891d2d8d3_102.png)

This thing。And I think the hecks。Macro is the culprit， but I'm not the 00% sure。

 so let's test it out。😔，Let's just add something like， no， this is wrong。 Let's go to the main。嗯。

And let's say， this is Maine。切。嗯。明天。And the regular man will just return。Main too。Or rather。

 this is main one。And now we're going to create a main two。

 This makes it a little bit easier for us to。Tobug and such things， test different versions。

So in here， I will just have a single print。And what I want to print。Is。2 hex characters。So。😔。

Pcent 0，2， H， H， X。same thing， once again。Where the first one。Is。Character A。Second one。Character 5。

 let's say。And I guess we need to cast this。72。Something like this。By the end of this。Thing。

And add some。Signatures for the other main functions。 So we have in main one。Void。Into main to void。

And I'm going to put a space in。Before these wounds you indicate that they are temporary。Thanks。



![](img/71193a65bb6b908f70e6c24891d2d8d3_104.png)

10。😔，4。

![](img/71193a65bb6b908f70e6c24891d2d8d3_106.png)

Hm。

![](img/71193a65bb6b908f70e6c24891d2d8d3_108.png)

If服 even。

![](img/71193a65bb6b908f70e6c24891d2d8d3_110.png)

So I did those calculations wrong， I guess。If x is。Is more or equal to。The character， a。

So this is true in the first case。So then we take x minus 51。



![](img/71193a65bb6b908f70e6c24891d2d8d3_112.png)

嗯。And if we。Prince。And hes them。So that is 61。So， we have 0 x 61。Minus。0 x 51。Which is 16。6。😔。

We want this to be 10， not 16。So。😔，What we really want is 51 plus 16。That's 97 or in He。😔，61。

That's not ride， either。We would。Don want is to be 16。 We're 6 of。Plus10 to this。Hey。0 x 91。5 B。



![](img/71193a65bb6b908f70e6c24891d2d8d3_114.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_115.png)

嗯哼。We're still off。Li。😔，Plus。普洱。

![](img/71193a65bb6b908f70e6c24891d2d8d3_117.png)

Soello。😔，1。😔，2。😔，3。

![](img/71193a65bb6b908f70e6c24891d2d8d3_119.png)

布尔。

![](img/71193a65bb6b908f70e6c24891d2d8d3_121.png)

Two， we go the wrong direction。And so where will， where will it be。So， one。2，3。服。



![](img/71193a65bb6b908f70e6c24891d2d8d3_123.png)

There we go。And what about this second case？嗯。

![](img/71193a65bb6b908f70e6c24891d2d8d3_125.png)

诶。Minus。0al。Do we have the five。

![](img/71193a65bb6b908f70e6c24891d2d8d3_127.png)

And a 5。Translates to。35。And the 0。30。We have 35 minus。30。



![](img/71193a65bb6b908f70e6c24891d2d8d3_129.png)

Which is five。嗯，我的什大腿。-0。

![](img/71193a65bb6b908f70e6c24891d2d8d3_131.png)

35。ter。

![](img/71193a65bb6b908f70e6c24891d2d8d3_133.png)

I if we play。Should' make a difference， right。Oh， wait the minute。Yeah。

This should be an and not an oar。

![](img/71193a65bb6b908f70e6c24891d2d8d3_135.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_136.png)

There we go。All right。So if we go back to May number one。



![](img/71193a65bb6b908f70e6c24891d2d8d3_138.png)

This time， I believe everything should work as intended。Almost。



![](img/71193a65bb6b908f70e6c24891d2d8d3_140.png)

嗯。So let's say we start out with this。

![](img/71193a65bb6b908f70e6c24891d2d8d3_142.png)

A， a，9，9， A a， okay。So we have the right values， but in the wrong order。



![](img/71193a65bb6b908f70e6c24891d2d8d3_144.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_145.png)

Still doesn't look quite dry。Okay， so we have swapped the individual bites as well。



![](img/71193a65bb6b908f70e6c24891d2d8d3_147.png)

So I guess we should take the X here。

![](img/71193a65bb6b908f70e6c24891d2d8d3_149.png)

AndThe why here。

![](img/71193a65bb6b908f70e6c24891d2d8d3_151.png)

F B 99，0。F been at9。

![](img/71193a65bb6b908f70e6c24891d2d8d3_153.png)

Almost the last one。Didn't become the right thing， but everything else。



![](img/71193a65bb6b908f70e6c24891d2d8d3_155.png)

So why is that must have to do something with。Yes。

![](img/71193a65bb6b908f70e6c24891d2d8d3_157.png)

Everything is right， except the last one。

![](img/71193a65bb6b908f70e6c24891d2d8d3_159.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_160.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_161.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_162.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_163.png)

Okay A becomes 0。

![](img/71193a65bb6b908f70e6c24891d2d8d3_165.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_166.png)

mm。A is the first thing we are。Weird。Maybe it's not the string barsing function。 That is the problem。

Maybe it's the show function or something。Yes， this should be 40。



![](img/71193a65bb6b908f70e6c24891d2d8d3_168.png)

那出来。😔。

![](img/71193a65bb6b908f70e6c24891d2d8d3_170.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_171.png)

And there we go。

![](img/71193a65bb6b908f70e6c24891d2d8d3_173.png)

Alright， so now we can successfully parse the stuff and print it and stuff like this。

 So now we can actually start coding the inner workings of the。Ethernet implementation。

So what we need to do is we need to take a look at。The protocol。So let's search for Ethernet weki。乐器。

Give me the English page， please。

![](img/71193a65bb6b908f70e6c24891d2d8d3_175.png)

So let's see if we find a packet format， or frame format。嗯。



![](img/71193a65bb6b908f70e6c24891d2d8d3_177.png)

Can we just guess that。Frame format。

![](img/71193a65bb6b908f70e6c24891d2d8d3_179.png)

Okay， here we go。The weird。Presentation。Usually， we don't。

See the preamble and that stuff inside of this， I think。But okay， let's。Let's do that。嗯。

So let's create a structure。Based on this thing。

![](img/71193a65bb6b908f70e6c24891d2d8d3_181.png)

So。We are going to。 We already have our own ethernet。Stuc， but this is going to be the raw thing。So。

若。Eithther。😔。

![](img/71193a65bb6b908f70e6c24891d2d8d3_183.png)

嗯。7 myths of preamble。And we need to consider。A network byte to order here here as well。 So。

 for instance， here we have a byte。But。We need to put this before the preamble。AndHere。😔。

It's a little bit tricky。Tmining the order。 So here we have 12。Plus 4 is 16。 So this is an in 16。In。

 and we need to reverse this order。 So it's a little bit。Tricky here。

 But I think we're gonna figure out。So let's start with this preamble thing。



![](img/71193a65bb6b908f70e6c24891d2d8d3_185.png)

It's going to be an in。Preamble。Pre。😔，Emble。With 7 bits。



![](img/71193a65bb6b908f70e6c24891d2d8d3_187.png)

And then， we need to place this。S，FD， before the other thing。



![](img/71193a65bb6b908f70e6c24891d2d8d3_189.png)

Which means that this is going to be a bull。

![](img/71193a65bb6b908f70e6c24891d2d8d3_191.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_192.png)

S，F1。

![](img/71193a65bb6b908f70e6c24891d2d8d3_194.png)

So， this is one bite。Then we take。The 16 bit thing of this one。Starting with it。え。Vent tag。😔。

原来 wonder者。😔，This is optional。 but what happens if we omit it。Let's。Keep this for now。

 We might be able。Need to change this later on。

![](img/71193a65bb6b908f70e6c24891d2d8d3_196.png)

4 bits of El。So this is going to be N 16。Mian。😔，4。

![](img/71193a65bb6b908f70e6c24891d2d8d3_198.png)

And then we go backwards。 So we have that。Source。And then， the destination。



![](img/71193a65bb6b908f70e6c24891d2d8d3_200.png)

系。This is the。

![](img/71193a65bb6b908f70e6c24891d2d8d3_202.png)

Let's see here。No， I'm thinking I'm doing this wrong。Because these are 6 Bs， not 6 B。It makes things。

Trickier but。

![](img/71193a65bb6b908f70e6c24891d2d8d3_204.png)

Also。Nicer。

![](img/71193a65bb6b908f70e6c24891d2d8d3_206.png)

Let's do this again。Alright， so now we can take it in order， at least。



![](img/71193a65bb6b908f70e6c24891d2d8d3_208.png)

Start with a preamble。

![](img/71193a65bb6b908f70e6c24891d2d8d3_210.png)

So， we need 7。Bs for that。

![](img/71193a65bb6b908f70e6c24891d2d8d3_212.png)

The7 bys。In 32 is 4。And in 64 is 8 bys。 so we can think the same way as before， only。



![](img/71193a65bb6b908f70e6c24891d2d8d3_214.png)

Using it in 64， instead。

![](img/71193a65bb6b908f70e6c24891d2d8d3_216.png)

So we start with S50。This is 8 bit。And then we have the rest of this N 64。Which is the pre。Amble。

And this is 8 times 7。 So it's 56 bit。

![](img/71193a65bb6b908f70e6c24891d2d8d3_218.png)

All right。And then we have our two met。Address structures。



![](img/71193a65bb6b908f70e6c24891d2d8d3_220.png)

Actually， I think we should have them in disorder。So we have this destination and the source。



![](img/71193a65bb6b908f70e6c24891d2d8d3_222.png)

嚟首。Then we have the optional vant tag。Which is 4 by。



![](img/71193a65bb6b908f70e6c24891d2d8d3_224.png)

So that's真。😔。

![](img/71193a65bb6b908f70e6c24891d2d8d3_226.png)

In 32， then。Is it really four bys in size。怎么啦。😔，And then， we have the tie。



![](img/71193a65bb6b908f70e6c24891d2d8d3_228.png)

Which is said in 16。

![](img/71193a65bb6b908f70e6c24891d2d8d3_230.png)

And then， we had the actual。Packet。Which is variable size。



![](img/71193a65bb6b908f70e6c24891d2d8d3_232.png)

And that is general in IPPC。And that's。The only thing will support， I guess。

So this will be a raw IP packet right here where a pointer to it。😔，No， the real thing。

But it includes is， its。Payload， as well。So let's say we have a strict S。Rule。Hy。Payload。

Then4 by of CC CC。

![](img/71193a65bb6b908f70e6c24891d2d8d3_234.png)

An inter packeted gap。It seems like this stuff here and here is not what。Things that were going to。

Have to tell it， because I think the network card should handle that stuff， but。



![](img/71193a65bb6b908f70e6c24891d2d8d3_236.png)

I'm not entirely sure。 I haven't really done。This type of packet before。

 because we're not doing raw sockets any longer。 We are doing something called。



![](img/71193a65bb6b908f70e6c24891d2d8d3_238.png)

It's see。Ro of guest。But。M need to check。小说。😔，哦。I think it mentions。Time somewhere here。

I think it's called。嗯嗯。So锅。😔，This is probably AF package。Neeththannet dot h。Maybe别的。Shows。The syntax。

 how much of the actual packet we need to use。The user include I C。嗯。I 3。嗯。还有一个。Ether Heer。

The destination， host， source host type。 That's all。The rest is handled by the network card。



![](img/71193a65bb6b908f70e6c24891d2d8d3_240.png)

Yeah， it's busy。So we can clean out all of this stuff here。

 So we have the destination and the source in that order， right。😔。



![](img/71193a65bb6b908f70e6c24891d2d8d3_242.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_243.png)

Yes。No we learn the type we keep， the payload we need to keep。Let's see。

 How do we do the other protocols。For I MP P， we had this day at the field at the end。We I。

We didn't have any of this。So the CRC， we don't have to bother with E either。

Maybe we should make this easy on ourselves。And just do something like this。

We need this to be packed， though。When we evaluate this thing。We are going to turn。This。Structure。

Into this。So actual rowab bites。And then， we can just assemble。All of this stuff。

 So we take one of these and then one of the IP。 and then we need to create something similar for TCP and。

Udp。And then we can basically deal with adding new practical。So后。😔，How did we do。Let's see here。EIP。

So we fill in all the different stuff。And this was a little bit more involved than what we have to do。

Right here。And we also deal with the payload here。So maybe we should do that， after all。And then。

 we just return。In end date， so they row abouts。Okayay。是。We're gonna have an in8 Eval I P。 no E。

Ether， then this takes an ether pointer。Maybe we don't need to deal with。う。Theicular。Alright。

 let's see if we can write this function。 Shouldn't be too difficult。

So we're gonna return an in8 point there。This is going to be called evil， E Ether。

Go to take an ether。咦了车。😔，嗯。We need to have point there。 We need to have。Something for the size。

You need to have astruct S。R。Eer， Ether。R。And if we don't have an E。We gonna return。Sirah。

We can start by。Clearing out our row packet。Ne the size of it， first。Size of strap。Yes。Raw。😔，Eer。

Maybe we can make this a pointer， actually。And we can set P equal to。系咯。Size beds。We can assert that。

 We have a pain。And we can。0 out that P。Size beds。And when we have the room for this。Structure。

We can set our raw。Equal to this。J。Yes。Raw either。O屁。And I will not just need to fill in the blacks。

So。😔，The P destination， no。The roa destination。It's going to be。有异。Destination。

I think we can do it like this。Let's try， anyway。And the raw source is going to be the E source。

And the raw tie。

![](img/71193a65bb6b908f70e6c24891d2d8d3_245.png)

Is going to be。

![](img/71193a65bb6b908f70e6c24891d2d8d3_247.png)

We do want to support our。

![](img/71193a65bb6b908f70e6c24891d2d8d3_249.png)

To though。😔，So， we need to have some。我也有。😔，Distinguishing。So we have the frame type type。

 Maybe we should just have。An Ether type type。

![](img/71193a65bb6b908f70e6c24891d2d8d3_251.png)

Where we have。

![](img/71193a65bb6b908f70e6c24891d2d8d3_253.png)

T。😔，Ortype I。And that is 800。

![](img/71193a65bb6b908f70e6c24891d2d8d3_255.png)

And type R。Yes， itll see。

![](img/71193a65bb6b908f70e6c24891d2d8d3_257.png)

And maybe well have some tea other， as well。好了。That's not。So now we can just set the type to E。Tai。

Or ether。No， what do you call。We called it type。But， we need to。Rename these things。

So this is now an either E Ether type。Same here。Ether type， eitherther type， like so。

And now we should just be able to get this as。系。And these are the only three things we need to fill in。

Well， let's start there。 we can deal with the payloads a little bit later。For now。

 let's just return this thing。So， now we can evaluate。あのデスタ。

And we need to create a construct function for this， as well。Oh wait a second。Proractical。

 that's probably what。This is。Referring to so we can remove this protocol。We can change this。

Have the source destination， and possibly some data。And how does the function for make I P look。Okay。

 so we take all of this， these different things。But， no payload。Okay， so we create an empty payload。

 and then we can add it manually。And here we don't。 We only support ICMP。

 but we are going to add more there。So， we can just do。IP。He look。

So let's create this constructive function。So， it's gonna return。An ether。Make。😔，Eer。

And it's going to take。A destination。Source。And then， eitherther。系i。Something like this。So。

 make either。And we have an ether type。T。😔，Tai。Have a market destination。So。If we don't have a。

Mac or。source for a destination。Return error。So the size is going to be equal to the size of astruct S ether。

E is going to be。Ma look。With his thanks。We're going to zero out。嗯。This。The size。

Then we're going start filling in the fields。So， the E。Protocol。It's going to be equal to time。

The E destination。And this is。Well it's going to be equal to this， right。

And the E source equal to this。那个这。Well， we're gonna to set the payload。To0 for now。

Then what is your name。

![](img/71193a65bb6b908f70e6c24891d2d8d3_259.png)

嗯。That's a couple of arrows。Unknown type name， I P。84。



![](img/71193a65bb6b908f70e6c24891d2d8d3_261.png)

Think we have a little bit of。我日。Ordering problem here。So， let's take this thing。With down enough。

Here， perhaps。

![](img/71193a65bb6b908f70e6c24891d2d8d3_263.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_264.png)

Or0，3。嗯。

![](img/71193a65bb6b908f70e6c24891d2d8d3_266.png)

嗯嗯嗯。Raw is equal to stroke。S Rother。

![](img/71193a65bb6b908f70e6c24891d2d8d3_268.png)

よし。Well， it's going to be a point or shouldn't it be。



![](img/71193a65bb6b908f70e6c24891d2d8d3_270.png)

So now we're back at those warnings that we had before。But everything compiles。



![](img/71193a65bb6b908f70e6c24891d2d8d3_272.png)

Alright， so now we have successfully。Taking care of the parsing of the back addresses。And。

Some of the show functions。Convering back and forth。

And also a construct function for our ethernet data structure。And the raw version。

 which we can send over the wire。呃。Which we get by evaluating。Ethernet data structure。

So we have all a solid foundation here。And in the next episode。

 we are going to take care of the sand function for actually as sendinging one of these things。

I hope you liked this episode and that you want to continue watching this series。

 please like and subscribe。And thanks for watching。 Thanks for today。



![](img/71193a65bb6b908f70e6c24891d2d8d3_274.png)

![](img/71193a65bb6b908f70e6c24891d2d8d3_275.png)