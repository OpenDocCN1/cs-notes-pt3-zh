# 编写一个交互式C解释器--BV1RJhEzgEUL-

So guys， welcome to today's show。 So today， we are going code a an interactive C E interpreter。

And I'm going to show you what I mean by that。 We， we have those in different language。

s like Python and。Her scale。So in acal， for instance。Yeah。You can do something like。

Let X is equal to1 plus 2。And then you just press X， and you get the result。

Or you can do let SDR 1 is equal to fo。Let S R 2 equal the bar。And then， let result equal to。S T R1。

And this there too。So I want something similar to this。I want to be able to create variables。

 assign values and list the value。And Hascal also has something。

 You can type column T and then a variable， for example。Or any。Statement or expression。

And then you get back the data type of that。So I want to have that functionality as well。

And in order to create a really good interpreter， you actually need to create。A compiler， basically。

So， I'm not gonna do。That much of an ambitious project， I'm gonna create。

 at least version 1 will be an naive version。Where we use GCC and we produce temporary dot C files。

And。If everything works， maybe we can move on to more advanced stuff。So。I'm gonna， I， by the way。

 those are usually called rapples。It stands for Re Eval。Print loop。And that's basically what it is。

 So I'm going to call my C Reple。嗯。Because it's a repple for C。

And I'm gonna create it by using bash B， S。C。Reple。And。I'm gonna use C template。

 Go into the directory， Se it to my home。And when I use BPS， it just creates my basic structure。

And you can download that from the Ray from the reppo， if you want。Alright， so let's see。

Let's go into。The crple。Direory。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_1.png)

To open it up in VS code。And。And I use C to x here。If your compiler does not support that。

 you can just delete this SDD part。If you have a very new version of the compiler， which I do。

 you can even do C23 here。So I'm going to do that。嗯。And this is the basic structure。

 So basically just a couple of integers， burst jus， which you can also find in the rep bow。嗯。

And the sea file is pretty much empty。Alright， so how do we do this。Well， the API is going to look。

Something like。This， I'm gonna have two。Main functions。So， let's call them。Well。

 let's call one of them tie。And that will return a data type。Of type， type。So， this is type。

And it's going to take。Let's see。Let's start by letting it take a variable， at least。Yeah。

It maybe even a variable。Pointer。And it returns the data type。

And I also want to have some void function， which just prints that thing。So， let's say。Vvoid。

Show type。And this will take it in a tiethe。The parameter。So let's make this a pointer2。

And before we move on， let's define these different。Data types。So first all， we need to have a。Type。

对 the头。So， let's create Str S。台。😔，Or is it enough with an Eum。

Will this carry an additional information， I don't think it will。

 So maybe we can just make this a non pointer。And then we create an enum instead here。

So we'll have an E type。And let's say we support in and charge for now。And we will type def our。

And this should not bestruct。 By the way， it should be an e。So we'll T type def our in E type。To。😔。

Tie like this。Okay， let's see easy。So， let's define our structure。Shes a variable。

And what does a variable contain， Well， it has a type， right。So， let's say， data type。

And this needs to be。At time。台。Mmhm。It should also have an identifier。So， let's say。Yeah。

 let's do identify。Name like this。And then we can just type de。Char ever in the。To。Identifier。

So it has a name。 It has a type。only needs a value as well， right。So， let's see。AVal。

I guess we need to make this void。Value。Because it should be able to deal well。

Different types of values， right。Integers and。All that stuff。

So let's say we typed off ourstruct as variable。To very old。そ。Alright。

 so that's what we need at this point。Let's also create some constructors。

We don't really need one for the inum types。 Its since it's very easily easily constructed。

But our variable， we need 1，4。So it's gonna return a variable pointer。Mei。😔，Ver。

And it's going to take a type。Identifier。And。A value。Let's start defining this。We're gonna have a。

Constructor function， which returns variable。Make var。And it takes in。Tai。😔，嗯。Ddentifier。And。A value。

Let's see。Yeah。嗯。So， avoid。Value。And。All we're going to do is。Check that。 We have these things。So。😔。

By the way。Let's have a。Vvoid here， as well。Or actually， let's have a。Nothingh。

Because I want the nothing to have 0 as a value so we can complain if it's 0。

So if we don't have a type or we don't have an identifier or we don't have a value。That case。

 we will return a0 cast as a variable。Or it in a variable for the return。T。Let's call it P。And then。

We also need to have a size for this。Let's say size is equal to the size of a tract S。Variable。

P should be na look。And if we don't have a P， we can also return。Otherwise， we zero out the pain。

Using our0 function from the beach hotels。And we need to cast this to an integer。 I mean， to an in。

And now we just need to set the different fields。So P type will be type。PI。Difier。

What did we call it。Data type， name， value。And then， we return P。Simple呢。嗯。嗯。So。See。

Maybe we should create some。Some macros， which create different kinds of these。

So we allocate for the value。As well。And what do I mean by that， Well， let's say， for instance。

 we create something like a。And。So we call it。new。😔，Yin。And this will only take a value X。

And an identifier， why。Maybe we should call them better things。So， let's say。The name and the value。

So what are we gonna do when we call this macro。Well， first， we need to allocate for this value。

So let's do。Or。Can't really do。嗯。Maybe we can do this。So， we will have a。Pointer。

And we'll have a name。And will have the value。So， if we do it this way。We can。Create a do block。嗯。So。

 let's just do something like。Let's first create a temporary thing。Let's say。T N p。And。We wanna set。

TMP equal to。Mello。And。Size of in。Over。In 32， to be precise。

Because that is what we're going to support at this point。Let's make sure we have a TMP。If we don't。

We will set our return pointer equal to 0。Otherwise， we wna copy the value to this new thing。So。TN。😔。

Should be equal to。No， no like that。The dereence T。Should be equal to the value。And。

Know that we have the value we can create。The actual thing。So our P should be equal to。And then。

 we call this。Make la。And the type is going to be an integer。The identifier is going to be the name。

And the。Val。😔，Is going to be our T MP。And in case we don't have a P。Then we want a free hour TM。

And we'll do the wild， false trick。So we。So， this will not loot。But。This should been in 32。

 by the way， And we want to cast as in 32 as well。Because if we do it like this。

We can just call this。Newva。😔，And we take one additional。Prameter。Which is the data type。So then。

 we can do。This， I'm not sure if it works with the parentheses， but let's try。

Because if we do it this way。We can define。Newy。And just say， this isn an in 32。Yeah， I mean。

We take in the P And V， like above。But the only thing we do is we call new v within an in 32。

 and we pass on the P， the N and the V。It's good to have the parenthees here in case we want to provide an expression。

And now we can just make one more of these。And suddenly， we support chas as well。Strings， however。

Which I also wan to support。AndNes to be dealt with a little bit differently。SoLet's create。And you。

Dream。With a PM And V。And will'll do this similarly， but not exactly the same。So， we wanna have。

In8 star。体平。TP。We need to know the length of this thing。So let's also define。How should we call this。

Let's just do T and P 2。 This will be the size。So let's start with that。 T andP2 should be equal to。

Yeah。And now we need to have a string length function。

So let's say we have something which is called length。And we provide the value。

So we need to make sure we have a value。Or maybe our length function can return 0， in that case。

Let's say if TMP 2 is 0。Then we wanna set our destination pointer。0。Everyone wna break。ok。Otherwise。

 we know the length， which means we can allocate。So， TMP should be equal to。Mlow。T2。This is 0。

Forgot to。Break here。So if the MP is 0。In that case。P should0。And we should break。Otherwise。

 we should copy beer。Our value。Which means we also need to have a copy function。So， let's run。Or。

Drink个。So we want to copy in 2。Our brand new TMP。We wanna copy from。The value。

And we wanna copy TMP2 bys。No， we can create。Our thing。Which means we can set P。Equal to make v。

 And this should be a string。For the name。And TM P as the value。If we don't have a。Pin。😔，InThat case。

 we wanna free our value variable。And well only run this once。Okay， so now we can create。Variables。

Before we move on， we should probably test this。So。我子。We want to have a variable。Be。😔。

P should be equal to May。No new string。And it takes。Destination point。Alright。

 we don't do it like this。Give the pointer here。And then。We need a name for this new variable。

Let's say。STR。And we need to cast this into an。In date strain。And the third is the value。

Also in date string。 So let's say food bar。And if we don't have a P， let's print some error。

Otherwise。We can。Do something like。Ti。See。So this means that we w。Print a bikete， or maybe 16。

And then， the name。By the way， this should be present。Do。0，4。And then we have the name， and finally。

The value。So just like so。So the first is going to be the P。What did we call it data type。

Then he need。And value。So three to be and we wanna return 0。

But we also need to create those two string functions。 Let's do that。

The first is just a string length thing。 So let's say we have。I't know。 I need 16 string。

What do we call it string land。And this should take an in8。StR。We need to have an intent N。

 and an in。P。😔，For loop where we set n equal to。0。P equal to the string。

We iterate as long as we have a P， and。At each iteration， we increase n。And P。Then。

 we can just return。But we also wna check that we actually have an SDR。Otherwise， returns 0。嚟首。

And let's also create this copy function， which is pretty similar。So， we'll do voyage。It。

never remember what I call the functions。So， let's see， string copy and。Leng。😔。

Maybe we should call this copy then。So， this is。ling。This is copy。

So it's going to take a destination。Source。Size。So we need to have。A destination pointer， A sort。

Pointer。We also need to have an in 16 M。The follow。Snation pointer should be TST。

Source pointer should be。source。And should be size。And we want to go as long as we have an M。

At the iteration， and minus minus。D pointer， we increase and source pointer。We increase， as well。

And then we just wna set the destination pointer to the source pointer at every position。

And maybe add a zero by at the end。Yeah。😔，So。😔，We will。😔，Increase。The destination pointer。

And set that to 0。Think we can do this， right。T。😔，Let's also not forget to create these signatures for these string functions。

So we'll have an in 16 length that takes in a in star， and we will have a void copy。

Which takes an inate star， an inate star， and an in 16。

And now I think we have what we need to test our first thing。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_3.png)

Let's make this stuff。See where we error out。Type F in E type。嗯嗯。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_5.png)

knew something was wrong with this H file。 I couldn't put my finger on it。This needs to be。

Terminated。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_7.png)

Dollar1 undeclared。 Okay， I thought I had those。 I need to change the name。 I have the old standard。

 So this should be 1 B，2 B，4 B，8。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_9.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_10.png)

P type is equal date The type has no number。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_12.png)

Right， so this should be data type。 This should just be。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_14.png)

Yeah assignment to variable star from incompatible point in the a。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_16.png)

Mm。So let's see new string。The MP is an indeed star。嗯。me look this。Thats an indeed。Right。

This should not be。Dollar 1，0 should be variable。0。Well， here too， though。

cause this should always return variable。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_18.png)

Assignment variable。Froming a parallel type in。He。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_20.png)

For the sick。Same here。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_22.png)

And then， we just have。One more thing。Expect argument of type cha。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_24.png)

Alright。When you print this， we need to cast it into。小。And the data type we wanna have as。Inter your。

And the name。Should also be a chor。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_26.png)

And now， I believe it will compile。Yes， but will it work。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_28.png)

Yes。Let's also see if we can create other things。Like an integer。So instead of new string。

 this will be new in。Let's call this。系。And the value。Something like this。Okay。

 and when we print this thing。You need to print the value as D。So this should be an integer。

 and we need to do reference this stage。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_30.png)

Oh。TN P。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_32.png)

Unclared。Maybe this is not。We can do。😔。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_34.png)

We do not want an expression there anyway。 So this is actually better。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_36.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_37.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_38.png)

refer in。Vid point。Maybe we need to。And 32 star。This。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_40.png)

Something like this， perhaps。It's always tricky like this bullet point。 Okay， that work。Let's try。

And it works。P。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_42.png)

And if this work， the jar will work as well。Okay， so now we can create variable。嗯。

What else do we need to do。We need to have a。Well， this dot C file。Is what。

We will run as the actual interpreter program。But the code will run。I's going to be a separate file。

Which are dynamically created。But they will have a common structure， So some functions。

Which are common to them。So， let's。Let's define these。Let's go to the make file。

 And let's say we do have a。We wantna create a common of O。From common的。😔，By round C。

 with some flags。In file。Alzs file。Possibly some LED flags。No， no I leave flags。And dash see。

Lets say we have a command age， as well。And。Well do we want to link this against。Well。

 at least for testing purposes， we can link this to our main thing。

But we probably don't w to do that。When we are done with this。Right， so let's create。

Come on the edge。M。Common的 see。So， let's restructure a little bit。Make though。 We can close。

Let's say we have the C files to the left。Disorder。And。I defined those here， the。Type and show type。

Both of these， actually。Should be inside of here。And we do want to have。These。Well。

Maybe not all of these， by the way。At least this。嗯。These。We also。Well， we need to。These as well。

 or maybe not。The variable。But。Type， I suppose， we need。Or maybe not。

We will do that stuff a little bit differently here。Kve。And then here， we just wanna include。给。Okay。

 so let's create those functions。So， this should。Return the tie。Of a variable。Actually， I think。

I think I'm gonna do this differently。Let's not have a variable here。

 and let's not even have a function。 Actually， Lets instead create a macro。So， let's define type。

And this is going to take。A variable or an expression， perhaps。Let's say it's an expression。

And what do we want to do with this expression？ Well， I want this to be a generic function。And。😔。

I'm a little bit。I'm not entirely sure sure about the syntax here。Something like。This。And then。

 it's going to take。Different data types。Well， the input first。Wch is the E。And。

Then I think we do something like。If this is an。In 32， for instance。In that case。

 I want to return in 32 as a string。And if this is。Well， if this is a cha。Let's return jar。

And the string will be represented as in the8。Star。So， let's say that's a string。As， as I said。

 Im not entirely sure about the syntax here。But it's something along these lines。

Let's see if it works。Go to。This。And Louis。Clean out main， and we try out this。Fengshg。So basically。

 we just wanna print F something。And this something should be the。T。😔，哦。He。Where x isn't in 32 x。

Somethingh like this。And then we need to include this。 And I dont hope it will not。Clash。😔。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_44.png)

Expected。Identifier or blah before generic。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_46.png)

I'm not sure。Maybe we can just do this for now。And。And what if we were to add a regular in。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_48.png)

Will our expression work。In this case。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_50.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_51.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_52.png)

哼 cool。And what if you just put a regular string in here。This。Sa。😔，Hello， world。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_54.png)

Ch star。This is pretty cool， actually。So， now we can。At least。P the type of。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_56.png)

This stuff。We尔。😔，Do you see。Yeah。So。😔，Inside of this。Criple， we need to have some。Function which。

Reads from the standard input， because we need to have a shell， basically。And we will do this， gel。

 like。With arrow support and all that stuff。 but not in the beginning。It would be very simple。We do。

 however， need some kind of red line function。So， let's say we have something like。In a。Read line。

So we'll just read from standard in， and we need to remove the new line。At the end。😔，嗯。So that'起。

I think you wanna do it like this。He。Let's create a P， and a red。And the size。

And maybe some temporary buffer， as well。Let's say we read 1，28 bys。

So let's start by zeroing out this path。28。Then we want to set。Size equal to。You read from 0。

 which is standard inputs。You wantan to read into。Our buffer like this。And at maximum 1。27 by。

So let's say we read ABC。New line。Then a 0， at the end。In this case， it would say that we have。

4 bites。And if we add indices。This is 0，1，2。3。富尔。Like this。

So our size-1 is the index of the new line。Let's just do。Let's set P equal to。不。Plus， size，-1。

Then we set this to0。Maybe it's cleaner to do。This， actually。

 because we wna reuse this and we wna allocate。So。😔，I will return。Will be a melo。Of。Size bed。

And then we wanna copy this thing。 So we'll do copy。Into red。From。But。Size space。

And let's also clean out this first。 So red。Size。And then， we can return。Something like this， no。

So if we have an in8 command， for instance， command is equal to。Let's do something like print F。

See rebel。Flash。Then we set a command equal to read line。And then， we just print。That line。

F the command。And return。Maybe we can also do before allocating。Let's check， if。

The first bite of bath。This0。And in that case， we can just return0。Without allocating anything。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_58.png)

Okay。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_60.png)

I guess we should cast this。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_62.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_63.png)

Right， that works。オッケー。So let's create some kind of a main loo。Create the bullion。Continue。Yishg。

Let's have a sea point。For that。We will send。Contiation to true。

 meaning we should continue the main loop。And a continuation pointer。

Should be equal to the continuation。While。We have a continuation。We should do our main loop。

Willll pass our pointer。So， we can set that。A value of everyone。Quit。😔，So。😔，Vod mainlo。Will have the。

Boo sea pointer。Let's say。Pro。😔，And。So， if we have a command。If that command。Is。😔，Exit。

And we wanna set our。Continuation to false。Do like this。And now we just need the pro。And for now。

 I will just do this。Maybe we can have。A copyright symbol。Since this is the sea ripple。

A copyright symbol， A sea。Could be our logo or something。So we can have this C。

And use it as a prompt， maybe。And let's also create some signatures here。So， red line， we have。

We will also have the main loop。Which takes a Boolean pointer。And we have a void。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_65.png)

Which takes nothing。Unused variable C。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_67.png)

Right。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_69.png)

冬 need的什。😔。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_71.png)

This should be the address of this。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_73.png)

Okay， that didn't look。Really。😔。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_75.png)

It works。But why did it look so weird。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_77.png)

What if we put a space here。这是威儿的。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_79.png)

![](img/d6ef56e5ecb599ab2ac96745c7db818a_80.png)

Copy the thing。Px them。8 night。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_82.png)

Try doing。A 9， instead。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_84.png)

What do you look at that。Okay， so we have the general structure。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_86.png)

And the。Next thing will be to try to define variables。Yeah。😔。

And then we need to turn our variables into C code。So， we can dynamically generate。That thing。And。

And then we can show value would be able to show values as well as types。

 So I think this is going to work， actually。In some sense。But I think this will be all for today。

 If you like this project， don't forget to subscribe。EAnd hit the like button。 Just subscribe。And。

Also， click the bell if you want to be notified when I drop the next episode in this series and in all other cool series。

Like the。And it' a back door。Playlist。 And I have a lot of fun stuff。



![](img/d6ef56e5ecb599ab2ac96745c7db818a_88.png)

So thanks for watching。 Thanks for today。

![](img/d6ef56e5ecb599ab2ac96745c7db818a_90.png)