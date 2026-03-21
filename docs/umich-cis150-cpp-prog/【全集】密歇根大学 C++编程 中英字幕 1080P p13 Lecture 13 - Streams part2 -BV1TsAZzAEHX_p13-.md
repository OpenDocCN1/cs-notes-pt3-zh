# 【全集】密歇根大学 C++编程 中英字幕 1080P p13 Lecture 13 - Streams part2 -BV1TsAZzAEHX_p13-

All right， there we go。

![](img/d2cadc6e5c62aff90d8f828238d53841_1.png)

是。All right， we're going to move on to new stuff this week， finally。

 Ho you're super excited we' talk about streams， which is a fancy way of talking about files。

 I don't know why they named it this way。We'll get there it's okay so this is chapter6 in Zybooks hopefully you're following along keeping up I'm not going to check to the end because it's just a lot of work to check all the time and to enter a bunch of things all the time so do try and keep up though those Z labs especially do add up so if you've not gotten through the first five chapters with all the exercises and the Z labs and all the good stuff make sure you work on that it's a lot of work which is good because。

It'll feel a little bit annoying but the more you practice the better you get at it like anything else so lots of practice there for a reason so we'll get into streams next week Monday we'll do the midterm review and then talk about the solution to project two and then next week Wednesday we will have time for the midterm。

I know not everyone's a morning person， I'm especially not a morning person and I still count 11 is the morning so my plan for the midterm is that it will open at 11 am and then you'll have any time that you want to sit and take it for your hour 15 block up until 1030。

So whatever's good for you， you find a time that。Five days right between 1025 and 1030 when you've got an hour 15 that you feel good and you can click start Okay I'm going to assume you guys will not work with other people we can all agree that this will be our individual effort it is open book open notes open internet but it's an hour 15 so if you don't have any of it in your head or even nowhere to go look it's going to take you a lot longer right so the idea is。

Kow where to go find the information you don't have to memorize anything okay like no one gets paid to memorize stuff in software no one's ever told me on the job that I have to do something off the top of my head because that'd be stupid we're gonna use our tools it's perfectly fine to use your tools use your resources but you have to know where to go look so everything should be coming out of the Zybooks and our lecture stuff that was our main source of here's the stuff we're talking about so we'll have half the quiz it'll be true false questions essentially I don't really like multiple choice I might have like short answer like I fill in the blank style short answer style so I'll give you last year's midterm on Monday or maybe even on Wednesday because then we can talk about the answers on Monday I'll do that so on Wednesday remind me I'll post last year's when I did the midterm here I'll post that one for you so you can see what the questions look like kind of get a feel for how they're formatted and then it'll be three short long answer style programming questions right。

So one on functions， one on loops， one on streams。Right so hey it'll be a short little thing again the goal is that takes you maybe 15 minutes or less or 20 minutes or less so if you did three of them that' be about an hour or so and maybe you 15 minutes for the true false fill the blank style questions at about a minute each that's sort of the goal so you I'll give you the practice one should feel pretty good anytime between 1025。

 11 a。 and 1030 11 a。 take it when it's good for you you will just agree that you will not work with other people and I'll trust you okay because。

Yes， and if you guys do work together it roads up for everybody right and then I can't do this anymore so we'll just agree not to because it'd be a big sad to have that happen for everyone so。

All right， and then after that week， we get into the last couple new topics， chapter 7。

 eight and nine。And we're done。So we're like looking near the end of the semester already。

 believe it or not。After we hit midterm week and come back to a couple new new topics here。

 we've got December set aside for you to work on the final project。

 I'd love for you folks to do it in Paris it's not required in this class to do group work I think working with someone else usually get a better product。

It does add a little bit of effort which is interesting like working with someone actually makes it take more work because you have to do all that coordination stuff and you have to work together。

 pick out who's do and what and talk together so it's the same project whether or not you do it individually or with a partner because it's about the same amount of work even if you're trying to divide it up between two people you still have the extra collaboration work there and then instead of your final exam on 1211 you guys just get to present your projects so your turn to get up in front and hit run show us your project will maybe ask a couple questions about the code。

Pretty quick maybe five10 minutes stops we'll get through it it's not too bad I promise I don't know where that is yet at least probably in the regular room but they've assigned those separately so that's always fun。

But ideally， if you can get it done by 126。Then you've got nothing to worry about for finals week so we'll have some time there we're going to start at 1115 or so so you have about a month to work on that one and again the final project takes is the bulk of your grade here in the class right that makes up 40% of your overall score so this is a significant portion here the idea is if you don't do this you don't pass the class。

This is the summation of all the things we've done in the class in one final little package。

It won't be anything super amazing because this is our first class but itll be something interesting。

 I would like to imagine。And should be fun by the end， okay。

 so it's sort of the plan working towards the end of the semester here we you visual studio。

I love streams and files because this is the first time we get to work with data that I don't have to just sit at the console and type in。

When I hit run， I can actually go read a file and get information out of a file or I can write information to a file。

So that I have the data somewhere when the program stops running right everything we've done so far has been working off of data in memory and it's stored in RA and it is only there while the program runs。

Which is nice。 And we do a lot of things with inmemory data， But we can't use anything pre-existing。

 and we can't keep it around when we're done。So being able to use files sort of sort of solves this problem for us to make a new project here。

 this is chapter6。

![](img/d2cadc6e5c62aff90d8f828238d53841_3.png)

Six streams。All right， let me grab the sidebook as well here。去。Yeah。

I don't know why they don't know the return， it makes me a little sad， but that's okay。

We'll add our name space。

![](img/d2cadc6e5c62aff90d8f828238d53841_5.png)

2。Yeah。You go， oh， that's wrong one。

![](img/d2cadc6e5c62aff90d8f828238d53841_7.png)

Too may looks。嗯。は。All right。So input and output streams。

 we've been using the output stream this whole time with this insertion operator。

seemsms really funny because it feels like we're outputting things what we call insert。

You're essentially inserting something into the stream the stream being what shows up in the console here so what I did see out that's our standard output stream happy Monday。



![](img/d2cadc6e5c62aff90d8f828238d53841_9.png)

We're inserting this。So this is the insertion operator。Inserted into the seaout。

 that's our standard output here。That's an old stream。

So this is our output streams where we're inserting into the output stream and this stuff will show up in the output。

So just the wording there is a little funny。

![](img/d2cadc6e5c62aff90d8f828238d53841_11.png)

And let me grab spring so we can also see in right， we've used the extraction operator。To get text。

 to get input from the user， you' would see in it extract from the input stream。



![](img/d2cadc6e5c62aff90d8f828238d53841_13.png)

是。Number and then we can see in number right， extract the value。 So this is our input stream。

And this is our output stream。

![](img/d2cadc6e5c62aff90d8f828238d53841_15.png)

Just put some names to what we're doing here， right it's sort of a magic before that。

So this one's nothing super new and interesting is just putting names to what's happening in these input and output streams for。

Formmatting that's all fine， you can go back and figure that all out after nothing very interesting。

If you want。You can input off of a string， so when we've done。😡。



![](img/d2cadc6e5c62aff90d8f828238d53841_17.png)

Inputs before we said there were two ways we could get the line to get a line of input and where we could see in we got when we did get line wed get everything including spaces up to when they hit enter if we did C we would just get the value up until they found a space so like trying to get someone's whole name would be tricky right so if we said enter your name name little safe name。

And I had a string for name。And I tried to see in on name， it's not going to get it in here。

boots string here。嗯。And I can see how I' made。Nothing new here。



![](img/d2cadc6e5c62aff90d8f828238d53841_19.png)

I got to do a number first， don't I？Tski。

![](img/d2cadc6e5c62aff90d8f828238d53841_21.png)

Weorre only to do the air right because there was a space there So if we wanted the whole thing。

 we could use giline instead so we could do Gitline and Giline says okay。Now this looks crazy here。

 this all these different functions here， but what is the input stream we're using。

 so I'm going to use the CN input stream and where do we want to put it。

 we want to put it in the name variable。Right， so this gets。The whole line standard input。

Up until enter key right and now I can get everything including spaces。



![](img/d2cadc6e5c62aff90d8f828238d53841_23.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_24.png)

Oops，Yep， mixing and matching these is us ugly， you see it was kind of skipped all of a sudden so when I said one and I hit enter。

It ran to the end and this is why I recommended not mixing matching just causes all sorts of headaches when you see in a value it goes until it sees with white space but it doesn't grab that white space so the enter key is white space the space is white space a tab is white space right so grabbed the one but then the enter key that I hit the hit enter it was still there on the input stream so when I called git line Git line says oh I see an enter key here's your line but it was blank。

So it gets to be a little messy here， so to do that。

 you sort of just need to get a line and just trash it here so I CNN in and I don't spring for throw away。

We'll add it to throw away。This gets the enter key。Let's rest。

Now the next time I call Gili it'll sit and wait and say okay。

 I haven't seen an enter key yet because this one got the enter key。

 we didn't spend a whole lot of time on this earlier because I said just avoid it that's the lazy way。



![](img/d2cadc6e5c62aff90d8f828238d53841_26.png)

All right so now I hit one， now I can get my full name here。And it's good to go。



![](img/d2cadc6e5c62aff90d8f828238d53841_28.png)

Because we got the enter key off the input stream。

![](img/d2cadc6e5c62aff90d8f828238d53841_30.png)

That part makes sense cool so not only can we。Get values this way， but we can take a string itself。

And you can input off of that string because a string。Is an input。

 you can use an input string stream。

![](img/d2cadc6e5c62aff90d8f828238d53841_32.png)

Which is super funny sounding so if say I were to read a file and get a one big line of data out of the file here let's count what name here so maybe we had something about like a car because vehicle of fun so we might have an string for vehicle info。

Is what we have like the make you have the model usually a year or is it a year first people say and like when you describe your car。

 you say the year first and then they're making the model right。

 so who's got a car they want to to offer up here 2011 Ford fiesta and that's a party right there。W。

Thats a joke right Okay， thank you thank you for lettingping my tear of the jokes I guess sure so if I want to turn all of this into individual pieces of information now I can use the input string stream so an I string I string stream goodness this is my vehicle。

😊，Itll info string string and you can call these anything you want I think one if they often use here they usually say in SS and I hate that I hate in SS but sure it's your strange truth it's not hard to type this but okay sure。



![](img/d2cadc6e5c62aff90d8f828238d53841_34.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_35.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_36.png)

So to assign that right we say， okay， in the parentheses here。

 we're going to give it the string we're going to convert or use in this string string so I give it my vehicle info string。



![](img/d2cadc6e5c62aff90d8f828238d53841_38.png)

It will turn this into these string stream， I was upset now。



![](img/d2cadc6e5c62aff90d8f828238d53841_40.png)

Initializer。No。No initializer。Oh， I didn't do my stream S stream there we go。

 include my string streams too。

![](img/d2cadc6e5c62aff90d8f828238d53841_42.png)

Io streams， string streams and strength。I feel like it's the Dr Zeus's book here and talk about this here so now it's happier that red line went away I did not get the suggestion for importing the S stream。

Sometimes it's not perfect right you're not always going to get the right light bulb here so right now we got our string string string so I can use that then and I can have something like here's my string for the year here's my string for the make and here's my string for the model。

And I can see in I'm sorry， not off of the scene， I can off of my vehicle string stream。

 I can grab the year and then I can take my vehicle string stream and I can grab the make I can take my vehicle string stream and grab the model。

We can see in off of the inputs。

![](img/d2cadc6e5c62aff90d8f828238d53841_44.png)

Strings dreams here。

![](img/d2cadc6e5c62aff90d8f828238d53841_46.png)

To do that same thing now this doesn't seem very interesting now but we're going to use this in combination when we read out files because we can read out lines at a time and piece apart take apart those lines if we want to as we go and then you here's your。

Our vehicle is a。Year space。W。Space。And a model model。

And then mine so it should get those three pieces that we took part individually and we'll spit the back out here because it's not very interesting we're not doing a whole lot with them here。

 but maybe eventually we could do something fun with them。



![](img/d2cadc6e5c62aff90d8f828238d53841_48.png)

2011 fort Fiesta。

![](img/d2cadc6e5c62aff90d8f828238d53841_50.png)

Fantastic。So we were able to take apart a string and then use those parts however we want it to here。

So以。This will get a single line here。As well， right so we can ask for。Then to type something in。

 right the first name， last name age on a line。And then exit as long as we were not done here。

 we'll get the line。Clear is what we are going to use if you're reusing your string stream here。

Clears it out and then resets it essentially so instead of making new ones of these every time this is a slightly more proper。

 say hey， clear it out and then set the string to this。

It's just slightly more proper here it's more memory efficient instead of trying to make new ones of these every time we'll just clear it out and set it clear it out and set it so it just like kind of says。

 hey point to this one please。Look over here for your input string stream here。😡。

And if we exit sure we're done， and then we can grab values， output the values。

 and then we're good to go。So not super interesting here。

 but we can go through getting one line at the time and this is generally easier for users to enter one line instead of something enter something enter something enter something enter right if they just type it all out of one line。

 it's a little easier for them so。It's slightly more natural。

 although you probably don't see very many users typing stuff in in the black box anymore。



![](img/d2cadc6e5c62aff90d8f828238d53841_52.png)

Invent programs， so again， all of this leaning towards using files， if I can get a file full of data。

 it's easy to get the line out of the file and do something with that line。



![](img/d2cadc6e5c62aff90d8f828238d53841_54.png)

RightNot necessarily as much users are going to type something in here。

 but builds up into using files here。All right， no， excuse me。We might not know。

When we're out of data。So you can say， hey， while I can extract data。

You can do that right so whether or not we've reached the end of the file this EOF end of file。

 I don't know whether they didn't just spell it out， but your end of file。

 it more alphabet soup you can keep in your head， will be a true or false。

 whether or not there's more information to read out of the string here。

So we're just going to output whatever here， as much as they want to enter。

 we're going to go and grab their individual name now in just getting individual names here is not super interesting or exciting。

😡，But it's a way to go through all of the data that was entered and do something with it right it's a way for us to process it and we don't know how long it's going to be eventually we'll get to the end here so if they maybe like entered the list of scores。

 this is much more interesting。enterter some numbers， just space separate rather than number， enter。

 number， enter， number， enter， number enter， number， enter， eventually hit a negative one。

It's kind of annoying it's not the end of the world， but you know。

 as we like prompted users to enter values until they were done。Sure， we could just say， hey。

 just enter a list separate my spaces。So like a little more friendly input style here。

 we can go through that way。Phone number formats， sure。Oh。So clear out your string stream。

 set it here。If it's good。So this one's interesting when you ask if something is good or not。

 it was figuring out whether or not the stream。Is it an error state or not？As we try and read things。

 we get into an error state。And then if we don't， it no longer returns good。对不起。Interesting。

 so you can input multiple things all at once here。😡，So it's trying to get the dummy character。

 it's trying to get the office code， the dummy character and the station number。Sure， because。

Office code is the。First， the second set of three digits， we have the area code。

 we have the office code， we have the station number。Doess everybody really how phone numbers work？

Especially someone really old， this is older than I am， none this makes any sense。Oh。

But we read in the area code as a number， right because my area code is an integer。

 so it's going to try and read in an integer。😊，If it can't read in the integer， this good is not set。

It's failed the extraction here and we no longer have this good flag set they'll say no。

 something wrong happened， hey， you didn't enter something right here。Right。

 so maybe they gave me some parentheses first so I can get the dummy character being the parenthesy。

 then I can get the area code numbers， then I can get the next parenthesesis。😊，RightAnd so okay。

 is it good did that work and I demmy character are parentheses here？Sure， so we can validate our。

Piece of information here。All right， and then standardize it here。

This gets to be a little more more interesting this is a little bit more complex。

 but dealing with varied input is actually rather difficult how are all the different ways people might enter values here and have a new account for that gets to be a lot of fun。

That was a fun example。All right。Outputting to a string stream。Instead of this screen。

 you can output to the O string stream。Here。So eventually I'll turn everything into a nice string at the end。

Here。So we can say hey， take this output string stream。

 put it all together now this is useful because not everything we're going to do will go to the console right not every time when we need to work with data are we going to spit it out in this little black box here。



![](img/d2cadc6e5c62aff90d8f828238d53841_56.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_57.png)

Because this is not the whole of the world， right， not everything gets spit out as a prompt。

So if we need to build a string together for us to write to a file later， maybe perhaps。

Because we're going to write to a file then I can build that string out using the output string string and do all the things like I would before with my other outputs right say hey take this one then add in this one and add in this one and just put it all together here eventually we get the string version say hey output string stream give me the string I just built and then we can do something with it again this example just outputs it here so it's a little silly。



![](img/d2cadc6e5c62aff90d8f828238d53841_59.png)

But if we were to write this to a file， now I have one single string I can write to the file and it starts to be useful here。

可。So working with these is a lot of fun。So。Depending on how we want to format our data。

 we'll do a lot of these again using the S stream， string stream include here when we start building these out。

All right， savings， that's a big stream here， that's fine。This one's fun， look at this。

You can figure out how much money you're going to save。Because you guys have square money， I'm sure。

 as Bro College students。Yeah， go for it。I'm sorry。

 I'm not making fun of you I'm trying to sympathize with you because I know what that's like。

 you'll get there though， you'll get there and。People on Twitter are just jerked sometimes。

 which is really weird， but there's like a whole debate going on whether or not you should get into software engineering for the money or you should get into software engineering because you like it。

And the jerks are like， no， you can only do this if you have a passion for it and you love it。

 and you have to code inside your job and outside your job。

 and you have to do nothing but write code。 And most of the same people online are like， no。

 your job you do for a living。 have hobbies。 please don't write code all day long。 If you like it。

 go for it。If you want to do other fun things， do other fun things， so it to be a little weird。

So that's okay that has a question yeah so for the。

They put string string yeah it inputs all the information stores it and then the output out output string string it outputs the information from the input string input in so you can build an output string string just like you would do see outs so you can turn whatever you would say normally we've been outputting everything here with these insertion operators you can build a string with that instead so I can kind of piece it together here's here's a hard go to string here's a variable here's this here's a variable to build a string and that string we can do something with later so we're going to see we can use those strings all right those strings to files so it gives you a nice way to format it as we're building here one line at the time essentially。



![](img/d2cadc6e5c62aff90d8f828238d53841_61.png)

But you don't need to use inputs and outputs at the same time this is or independent from each yeah。

 yeah， they're independent from each other。

![](img/d2cadc6e5c62aff90d8f828238d53841_63.png)

。All right。So eventually they just spit this out here this produce savings table function。

 remember we don't get get rid of things here so here's our function produce savings table starting them amount annual percentage rate I don't know why they didn't write this out here APR because not everyone knows what APR means and then the number of years like this is not hard people okay。

They've got some constants right their output string stream they know what their interest is they know what their balance is and then we start adding to the balance so they're doing some of the formatting that I skipped over formatting is great right I just don't want to spend the time on i'm sure you guys can figure that part out reading the Zy bookss it'll give you lots of practice don't worry。

And when you start。Adding the interest to the balances。

 right your monthly percentage rate here that we divided by 12。

And it's a little awkward here but sure， and we add that interest and then we tell you hey what it is and then only if we've hit 12 months。

 do we now we add this to the output string stream。

So we add 12 month worth of interest now this does make a difference right this is compounding monthly。

 not compounding annually。You want to you want to compound as often as possible because it increases your possible returns right if you just get 5% back at the end of the year。

 that's much different than getting 5% or a 12 of that every month right because then you're losing the monthly interest you would have earned。

It's not a ton， but as money starts you start to have more money， this starts to matter more here。

Right well we can look at the difference later if you're curious。

 but this one is a lot of fun let's just shamelessly steal this because why not here let's take his whole。



![](img/d2cadc6e5c62aff90d8f828238d53841_65.png)

This one here because this is fun。Com we'll put this function up here。

And I'll even grab the URL for you here because why not？Look at that。

 I cited my source for that function。I need some more includes， don't I？



![](img/d2cadc6e5c62aff90d8f828238d53841_67.png)

Ioman。Iio manipulation。

![](img/d2cadc6e5c62aff90d8f828238d53841_69.png)

Ging input output manipulations， we get all those steps here， okay。



![](img/d2cadc6e5c62aff90d8f828238d53841_71.png)

So that one's fine。If we could even ask the user right， we could say， hey， what's your balance right。

 starting out and your percentage rate number of years， see out the table。



![](img/d2cadc6e5c62aff90d8f828238d53841_73.png)

Scrb all these here。Nope， I didn't hit copy， copy。There it goes。



![](img/d2cadc6e5c62aff90d8f828238d53841_75.png)

All right， starting up， so if we just start with $1000。

Annual percentage rate what's an annual average？

![](img/d2cadc6e5c62aff90d8f828238d53841_77.png)

Thank you。Sur race。嗯。5。355。35 first merchant that's an ad though， that's not even an ad， is it？算。05%。

 that's a little bit different than 5%。

![](img/d2cadc6e5c62aff90d8f828238d53841_79.png)

We're going with 5%， though right。That's a little happier so five number of years。

I'm sorry30 so if you're around age 20 or so。For 30 years， I put you at 50。

Probably going to sit around longer than that right because by the time you actually retire the Social Security minimum Medicare minimum will likely be 70 if not even higher than that so that gives you 50 years right from age 20 to age 70 or so。

 so let's put 50 years here because that's fun so 1000 if we don't touch it and earn 5% a year。

It's up to。12l000。That's not terrible right from 100 to 12，000， so it's doubled right。

 so it doubles here and then it hits 4000， it doubles here and then 8000 it doubles here or so。Right。

Okay， that's fun if you like numbers and those sorts of things people say the rule of 72 take your percentage rate divide divided by7 or 72 divided by your percentage rate that's how long it'll take to double essentially so 72 divide by five I can't do that math that I had hear it it's about 14 years or so for it to double I think that checked out right you' 14 we doubled and then。

We doubled again year 28 and then 42 we doubled again right we double about that rate here and that's putting 1000 in and letting it sit never touching you and never adding anything to it either so we can make this more interesting right so let's go。



![](img/d2cadc6e5c62aff90d8f828238d53841_81.png)

And see if we can add make this more interesting， so let's say we need a int for。

Monthly inquiry monthly ad I don't know monthly。Savings sure come about monthly savings so each month we' add to the balance here as we go right not only we add the interest we're also going to add the monthly savings。

Right？So if you add $100 a month， right， we'll add that every loop here for every month。

Right as we go。So let's ask then for see out。How much will you save each month？是。

And then we can see in we need them like a for monthly savings。嗯。Monthly savings。All。

 and we'll add this one in here monthly savings， and then we'll add this into our function monthly savings。

Okay， so now if we start with $1000， oh， let's just start with the start with zero。

 so we've got no money here and we'll add at 5%。

![](img/d2cadc6e5c62aff90d8f828238d53841_83.png)

We'll add for this is for 50 years， right， we'll add$100 each month。

So $100 a month for 50 years right is 100 times 12 times 50， that's $60，000 over 50 years。

How much do you think we're going to end up with if we can get a 5% rate of return over 50 years？

It's going to be a lot more than 60，000， right？Anyone take a guess？Thank。Half a million。

 anyone else want to guess？300，00 okay， less than half a million， anyone else。我 what。How much more？

100，000120，000， anything think just doubled？Okay， and else want to guess。More than how much。

 more than half a million， definitely more than half a million， yeah。Definitely， all you ready。

 it's super exciting here。Oh266，000。From 100 from 60，000。Plus， this is4， four times doubled。Or no。

 double， I guess double twice， right， but four times as much as the original savings。So 268，000。

 that's just 100 bucks a month here。It's not too bad。Now the sad part of this though。

 is inflation because your future spending power will decrease thanks to inflation because that's the fun thing you want to talk about in class。

 so inflation。It's crazy right now it was pretty stable before and the Federal Reserve has the target of about 2% per year inflation like they actually want inflation。

 which is a whole other story here you can get into that in an economics class but if we were to able to hit the target 2% per year right so it's 1。

02。We went to the 50th here means that something that costs a dollar now at 2% inflation for 50 years will cost $2。

69 in 50 years so that is not even a gallon of milk anymore how about loaf bread can you even get a loaf of bread for a dollar I don't think so。

When do we get for a dollar？Candy bar， you can't even get a candy bar for dollar， right？呃。天你个自打回事。

Yeah dollar starts moving up， but this means that that 266，000 really has a spending power。

 let's copy this here。S。Divided by 2。65， it's really only worth 100，000 in terms of spending power。

 so it'll buy you $100，000 worth of today's goods in 50 years。So you're still better than the 60。

000 we had， all right？If you just put 100 a month in cash away and this is only a 5% return。

 so ideally you can do better than a 5% rate of return。



![](img/d2cadc6e5c62aff90d8f828238d53841_85.png)

This is what the average stock market。Now， average is a really bad number here because this is not how math works。



![](img/d2cadc6e5c62aff90d8f828238d53841_87.png)

Okay， the average is how math works， but this is not how the stock market actually behaves right the actual rate of return varies wildly。

 it will go down， youll lose money in the stock market some years you gain 30% it's all crazy it's a bit of a ponzi scheme as well because there's federal incentives for having to invest in the stock market so it increases demand artificially that's another story so if you can get 10% per year right unless rerun this here for fund so0 $10% rate of return for 50 years at 100 bucks a month。



![](img/d2cadc6e5c62aff90d8f828238d53841_89.png)

Now we're at， oh， we ran out of room here， that's a good thing。Right1。7。1。

7 million know what that number is？1。7 million so。Change in our rate of return significantly changes this number we went from 260 right to 1。

7 million。So that's the compounding that's the doubling here right at 10% the power the rule of 72 says every seven years or so we're going to double。

The more you can double， the better off you are。This was super fun。

 this was just using their coding example here， and this is a retirement savings calculator。

And again， you know， divided by 2。65， you get a lot less spending power out of this after 50 years from now。

 but that's not。

![](img/d2cadc6e5c62aff90d8f828238d53841_91.png)

Not necessarily anything we need to worry about right now it will impact you in 50 years and that's if we can get down to 2% inflation target it's going to be worse now so。

Anyway， was that fun。That was lots of fun， so building out this string here。

 this output string stream here。So that I don't need to see out everything。

 this table here I can do something with that doesn't always have to show up on this black box console。

Right。These sorts of things， if I could save it as a file。

 it' would be much cooler right because then I could take this file and have it around。

Or I could email it to people and be like， hey， look， look at all this really interesting data。

 you should start saving 100 bucks a month。Because you can scrape together 100 bucks a month right now。

 maybe later in the future， right that sort of thing。So。

 and that is why the federal government tax incentivizes retirement savings because earlier you can save the more time it has to compound the better off you are。

 and ideally in your career you start making more money later in life as you get more experience。

 you're generally more valuable， you can make more money so maybe you can put away more than $100 a month or so。

 but that's another story there。

![](img/d2cadc6e5c62aff90d8f828238d53841_93.png)

All right， where were we？All of that from the savings calculator， there we go。Yeah。

 now files we finally get to files， so opening and reading from a file super fun here。

 so when you work with files you always do three things。

 you open the file and read orite the file and then you close the file。😡，Opening is very important。

 closing is very important and you probably want to read read from it or write to it the thing you want it for。

 but we always need to open and close those are always going to happen as we work with our file so we're going to open the file here with our input file stream or our F stream for file streams here。

😡，Then eventually when we're done with it， we're going to close it here that tells the operating system hey。

 we're done with it and it's not going to keep it locked or keep it open and let other things interact with it here now when your program stops。

 it'll automatically get closed but that's a really bad habit you don't want to be in the habit of just letting it close when your program stops it's just bad form。

😡，So we to try and be better than that okay， so to open a file。

 we just call open and you give it the name of the file it's super cool so hey open this file。



![](img/d2cadc6e5c62aff90d8f828238d53841_95.png)

Let's try it so let's go and let's see let's comment out a lot of this。

 we don't need to do a lot that we'll start it at the the top so we'll include our F streams here for file streams。

ASt， okay？

![](img/d2cadc6e5c62aff90d8f828238d53841_97.png)

H。So。We need an input file stream here， and then we're going to try and open a name of a file here now text files are really easy because we can open them up we can edit them and we can put whatever we want in them ourselves because text is pretty easy here so we can input file stream input file stream。



![](img/d2cadc6e5c62aff90d8f828238d53841_99.png)

And then we're going to try open。So my input file stream do open and let's， I don't know。

 test dot Txt。And then we want to， I don't know， read something out of it here。

 so we need an int for number。And then I can take my input file stream and I can extract the number。



![](img/d2cadc6e5c62aff90d8f828238d53841_101.png)

No。couple other things we wanted to check here， right， so it's checking， hey， if it's not open。

Something happened and we finally see something that's not a return zero。this return one。

Something bad happened right if I can't open the file probably should quit because it's not going to work and I can give them a nice little error message here so this is pretty handy here to say hey。

 if it doesn't open。

![](img/d2cadc6e5c62aff90d8f828238d53841_103.png)

Let's bail out early before I try and get that number here， so if it fails to open。Oops。

 just outline。If it's not， is opened。They not so we're inverting that if it's not open。

 could not open test Txt return one。Anything other than zero really indicates an error。

 I guess non zero。It means an error indicates an error， it indicates is that a more proper word here。

That's what they had indicates in error。Okay， so we try and run this here。Olps build air。

 what did I do， as' my aist。No。Where's mays。Why what it。Aha hint number， there we go， all right。

 we don't need hint number down here then。We already have a number， all right， let's try that。



![](img/d2cadc6e5c62aff90d8f828238d53841_105.png)

Finally got there could not open file test。 Txt Now there is no file name test Txt we didn't make a file so I think this makes sense there is nothing for it to open here。

 so for us to go in open files， this is where it gets to be a little weird The file has to exist where our program can go find it。



![](img/d2cadc6e5c62aff90d8f828238d53841_107.png)

So I'm going to go and add a new item。I want all templates here want。呃。

Text file you can find in the list here， it's under utility I don't know why this is my shortcut here。

 we'll call it test。tTXT。是。I've added a file test。txt， I wanted to add a number here， right。

 so let's add 42。Make our file is safe。 So now I have a test file here and if I open this up in file Explorer。

I can see here's my CPP file。 Here's my text file。 test dot T Xt。 you know， I don't have the。

I did not change my new options here yet you want to view don't hide extensions for known file types。

 this is the most annoying option here that Windows does is really annoying for programmers and we do want to show hidden files and folders there we go so now you can see it's test。

Txt。Before it hit the dot TxT is I' like you don't need to know what's the text file。

 all' just Windows knows it's the text file， I want to know what's the text file。All right。

 now let's see if we can get a number。It didn't crash， so it must have gotten number。

So let's go so we can find the test file here when we run our program。嗯。

So if I leave run one more time here， do I get， where's all that output here。Here it goes。

It's actually running or executable from over here and go and find a file right it puts us in this x64 debug folder。

That's x64 debug。Where can my executable go， it's not in there， so not there。

Thought it left it in there。 They clear it up。You got rid of it for me。Well。

 did have it there for a minute。Let's it clear that。Good。

So if I were to put this test file somewhere else reading it would be a little trickier right so let me move it let's go back to test TxT。

 I'm just going to move it up a folder here to the same folder as my solution file here。

I now I hit run。

![](img/d2cadc6e5c62aff90d8f828238d53841_109.png)

And it couldn't open the file。Couldn't that， oh， I was in the wrong folder， that's where I was。

 so here we go。This x64 folder。Dog， hey， there it is， okay。

 there's our executable that I was looking for。So I just run this here。

 right you can double click your files。Now notice it just closes right away。

 it only stays open here because it's doing this debug thing right automatically closed。

 you can set this option our program stops because it wasn't expecting any input to hit that error and crashed。

Right so running it here it's crashing so let me take the text file put it back in here when I've got it next to my CPP file here。

 I can run it in debug mode and we're good it runs without crashing。

 but if I go find that executable。And I run it here。It's crashing。

So it doesn't know where the test file is， so if I copy the test file in here。

I going to make a copy of it here， we'll have more than one copy of going。😊。

If I put it next to the executable but in the same folder is executable now when I run my executable it runs and it doesn't crash so when you ask for the name of a file。

 when you ask to open a file where it looks is where it's running in this case when I double click it it's running in this folder。

😡。

![](img/d2cadc6e5c62aff90d8f828238d53841_111.png)

Right so if it doesn't have another file in this folder， it's going to crash when I hit debug here。

 it actually runs at the project folder， which is kind of weird。

So it's a little bit different on where the files exist and where it tries to read them here。

 is that question？So once suppose with。And then the any and cur disappear that's。

I've not seen that before， I off to look at your computer in a minute that should should this let you tight？

I don'tt know exactly what happened， I'm sorry。So right， we can look in a little bit。

So when I put this file in the project here I've clicked on my project right a solution has one or more projects we've only done one project at a time and that's all we're going to do because we're not that fancy right now we'll get to more advanced stuff later you want it at the project level because that's where it runs when you run your program in Viual Studio。

Okay if you want to specify the full path of a file and say hey it's specifically in this location you can do that so if I were to take my file here let's pull it out of this one here and let's make sure it is not here i'm going to pull it out of this one I'm going to go all the way up let's go just to a C drive here so I'm going to add a new folder here so a new folder so see test。

😊，Test TXt generally， you don't want to put files right in your C drive。

 at least in Windows land it likes to protect that location， so make a folder first。

 so this is C colon slash test slash test do TXt， right that's the full path to the file here。

In Windows land。So if I want to open that file specifically， now notice the back slashes here。

Are escaped right the backslash normally means this is an escape character because Windows is fun like that。

 so you can do backslash backslash to say， please escape the next character of a backslash I really want a backslash。

That's the Windows pathway goes。Paaskt。Sscape。Escape the。Exlash character。

Right we talked about this way back when right you can do your back slash N for new line back slash T for tab all sorts of fun characters like that Sure so I should be able to open it from this location here if it does not exist in my project I got to open this one up to get here right open。

It does not exist here。

![](img/d2cadc6e5c62aff90d8f828238d53841_113.png)

So now when I run。It reads the file。

![](img/d2cadc6e5c62aff90d8f828238d53841_115.png)

ど？😮，So now when I go to my debug directory。It's that debug version here that's built x 64 debug。

 When I run this one here。

![](img/d2cadc6e5c62aff90d8f828238d53841_117.png)

It also runs。It's not looking relative to where it's running。 It's looking at an absolute path。

 Se colonlon test slash test， so you can give relative paths or absolute paths。



![](img/d2cadc6e5c62aff90d8f828238d53841_119.png)

So this is an absolute path。Now， absolute paths get a little screwy， though。

 because if I were to give this executable to someone else。

 and that's sort of the idea when we write software that other people can run it。

It's all well and good and fun for us to run our own software。

 but if I wanted someone else to run this， it won't work unless they have a folder called test and a file called test on their computer。

She is maybe not so great， right， because it like starts to cause some trouble。

So absolute paths are great for us。Gets to be really weird。

 especially if you start putting stuff like absolute paths in these folders here。 you're like， hey。

 I really want to find it in this location here。Well， it's in the users's Eric C folder。

 how many people do you think have in users's E C folder？Not very many of us in the world， right。

 unless you're also Eric C。はい。So actually I do have a class with another Eric C and it's the weirdest thing when I get emails from them because it comes from Eric C and like what and it's like have to take a second I wonder why I'm either emailing myself it's even C like their life names pretty close to mine which is creepy but an absolute path to something like this is just terrible it's not going to work so most of the time what we want to do is relative paths so I just say a relative path。

Path， so let's let's forget the absolute path here and just go back to our test Txt。Test up TXt。

This most of the time works pretty well rights is that finally even in the right spot？When to folder。

 okay， neat， you put it back， but I double clicked it， it created again and even put the 42 back in。



![](img/d2cadc6e5c62aff90d8f828238d53841_121.png)

That's really neat。So most of the time， relative is what we want here。



![](img/d2cadc6e5c62aff90d8f828238d53841_123.png)

And when you send someone software， it gets all packaged up， you don't just email around executables。

 usually it install it， all sorts of other fun things or zipped up and you can send files along with it and if you put it all in the same folder。

 it has a relative path it will just work。It can just open the file and can be good to go so this looks in the same。

Holdderware the。XC is running。I think it to be kind of fun。Okay。

 so one more time let to make sure that's running here， it runs there。

 it does not run from my debug folder。Yeah。file Explorer。I want this one here solution。

This one crashes on us here now one last thing we're going to do real quick here I'm going to find it in here so this is OneDrive documents GiHub see 150 nope I'm not typing this fast I'm hitting tab eventually you'll get to using the terminal it's lots of fun I promise here when you hit tab it will autocomplete and say hey I started the G what other folder matches a G right so I'm not actually typing stuff really fast here it's just showing up for me fall 2023 and then chapter6。



![](img/d2cadc6e5c62aff90d8f828238d53841_125.png)

Streams， right， And then from here。I can go find my debug folder here's my solution file right I'm looking at what's in this folder here from terminal next semester you spend a little bit of time here。

 which is a lot of fun especially in Uni land because we teach multiple operating systems for our accreditation process which is fun so from here if I wanted to go run that executable and' say hey let's go find or I could go into that folder so the x64 folder and then what's the next the debug folder here and I can call chapter 6 oops。

Streams， EXE。And it says， hey， could not open file test on TXT， can't open it。

But now i'm in terminal so there's nothing for it to close so I just get the output here right so if I want to go back a little bit here and if I go into that directory and run it I don't have my file here he and we go into chapter six streams。

So this folder has the test file right I'm in the chapterer6 streamams project folder inside the chapterer 6 streams solution folder。

Right we're just doing this at text here so if I want to go from here upper a level and then go into the debug directory。

Heバ。No。Oh no， I want it up a little。啊不干。Come on， go back。It's not working for me here。Oh， it's x64。

 that's one of this， that's why Bbug chapter six streams。

If I run the executable from this folder here。😡，I said， hey。

 go' find the executable that's in up a folder in X64 in Dbug in chapter 6 streams EXE。

It finds the testTxt file because where I'm running it from here。

 I'm running it from the project folder， the file is relative。😡。

And that's what Visual Studio is doing when I hit run here， he runs it from the project folder。😡。

It doesn't actually run it from the debug folder here， right， It's not in the。

Xe4 debug folder when it runs because then I wouldn't be able to find the file。

All this to say relative file paths right and we'll spend more time with this。

 we'll practice with it's a lot of fun I promise running stuff in terminal it's really exciting。

I know you love typing in black boxes， so lots of fun。

Does any of that make sense that I'd lose you a little while ago， that's okay if I lost you。

 we'll come back to it。

![](img/d2cadc6e5c62aff90d8f828238d53841_127.png)

Ok。All right， so relative files。😊。

![](img/d2cadc6e5c62aff90d8f828238d53841_129.png)

So that's reading files from relative paths。RightAgain。

 checking to see if it was open or oh I didn't close it， I'm showing a terrible example here。

 so if it's not open， we read it here and then we close our file quote。



![](img/d2cadc6e5c62aff90d8f828238d53841_131.png)

Close the file when we're done， so I got the number out here and I could see out。Red number。

Super exciting right we read the number here， it is， oh goodness， gracious。Oh， it can't。

Open it for so I think one or two of you have had this error before here I left the program running so when it tries to build for running in debu mode it says I can't edit this file I can't change this file I can't write this file because it's in use so I need to cancel my run over here control C will kill that now I should be able to run it here so if you leave the debugger open and then try and stop and run it again here sometimes it gets confused。



![](img/d2cadc6e5c62aff90d8f828238d53841_133.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_134.png)

I didn't that time， but sometimes it does， it can get confused easy。All right。



![](img/d2cadc6e5c62aff90d8f828238d53841_136.png)

So we were able to read a number out， right， I think we read the number 42， super exciting。



![](img/d2cadc6e5c62aff90d8f828238d53841_138.png)

Now again。That's just one one number， what if we wanted to have a list of numbers here。

 what if this was like our cash register receipts here we could have a bunch of numbers here。

 77 and 23 and9 and15， I don't know a bunch of numbers here right industry。

Type numbers in the silver For， okay？Probably that one here。

 so it'd be much more interesting right if we did some sort of loo。

That idea as long as we can read data， let's keep on reading data。

 so instead of reading one number here， let's read a bunch of numbers。

 so we go ahead it for the total here starts off at zero and while my input stream reads number here。

Yes will。Loop。So it can't read anymore。Reaches end of file。The file right。

 we're to take the total plus equals the number。And just for fun。

 I'm going to see out the number just so we can see what number we're reading here right。

 this is just for our purposes to see it here。And then we'll close the file total。Little red。

And I'll output put the total。嗯。

![](img/d2cadc6e5c62aff90d8f828238d53841_140.png)

So now we should be able to get all the numbers out， right？Up to the 246。

 right that was the last number， I think that was the last one here， right 246， yep。

 so it read all of the numbers here。

![](img/d2cadc6e5c62aff90d8f828238d53841_142.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_143.png)

And total them up for so now all of a sudden it feels a little bit more useful I can give it a file with who knows how much data in it be able go and read it all out and do something for me we could calculate an average we could calculate a standard deviation whatever sort of fun things you wanted to do here right but now I can base it off of a file input I don't have to have the user type this stuff in。

😊，Which is so much nicer， right， because computers are faster that sort of thing。 Hey。

 just read the cash register file。Don't have the user look through every single receipt and have to type stuff in because I don't about you。

 but the more often I have to do something， the more likely I have to screw it up So if I'mtyping in receipts。

 I'm probably going type one of them and then my cash register won't balance and then they'll be pissed off on me。

So I tell you the funny story about food service workers and cashiers and like people in I。

 it's not actually all that funny， but turns out if your cash register short。

A lot of times your manager gets pissed off and they want you to pay for the difference。Like， hey。

 your customers is $5 short， you got to pay that。Like kind of jerks and do that。

 but this is how we treat our food service workers or people in cashiers all around the world in IT。

 it's not common， but it happens where people make mistakes that cost， you know。

 tens of thousands of dollars because you did the wrong thing and took the system down or deleted the wrong thing and took something offline and。

The general response to that is。Oh， okay， let's make sure it doesn't happen again。

 And you learn something， right， We're like， this is like tens of thousands of dollars mistake。

 not $5 we're like， that's okay。 Just learn from it。Which is the right response。 right， Not， Oh。

 you have to pay the difference on your paycheck。Like we treat people so differently here it's crazy there's there's a whole Twitter thread Twitter's a fun place sometimes like most costly mistakes people ever made in IT。

It's a little bit painful to read， but also kind of interesting to read。

 like all the terrible things people did。If you remember was it last year。

 I want to say like most of the internet went down。

Because Amazon someone at Amazon clicked the wrong button or typed the wrong thing and hit enter。

I don't know if I don't remember that was huge outage because it this。



![](img/d2cadc6e5c62aff90d8f828238d53841_145.png)

基本上。😔，嗯。Well last three out of each， what was it here？嗯。This is here。I think it was this one oh no。

 that's 2008， that wasn't it。IFeel like it was 2022， right？I think it was 2022。All right。

 they had a good article about it here， but I'll see if I can find it later for you。

This one now that was 40 minutes， I don't know， they press the wrong button and they're like， oh。

 we need to make sure that you can't press the wrong button in the future。



![](img/d2cadc6e5c62aff90d8f828238d53841_147.png)

Which is good we'll fix our processes so that's sort of sort of thing all right so work with files right open it read it write it。

 close it we're good to go。

![](img/d2cadc6e5c62aff90d8f828238d53841_149.png)

Read to the end of the file like we just did， right we read and so you can also say until it doesn't fail。

So remember we said if it's good or not， you can say if it doesn't fail and then check whether or not you actually got to the end of the file。

 this is sort of nice because if someone throws something stupid in your input file。

It might end unexpectedly。Right， honest， so we can check this is kind of nice to make sure we are properly reading things as expected and then when we do stop this while loop。

We can check， hey did we get to the end of the file or not， so if we just stopped because it's bad。

 we didn't get to the end of the file。And tell the user， hey， something went wrong here。

 you need to fix your file versus our program here if I throw some garbage in here。



![](img/d2cadc6e5c62aff90d8f828238d53841_151.png)

Is just going to stop so if I throw in like the 10 here。



![](img/d2cadc6e5c62aff90d8f828238d53841_153.png)

Right， and then we run it。哼。

![](img/d2cadc6e5c62aff90d8f828238d53841_155.png)

They just stopped reading。Right because we said， hey， as long as we can read。Well。

 you can't take the number the word 10。Extracted as number， so while loop stopped。

Right so it's nice to have that check， hey， if my input file streamed end of file if。

Not the end of file here。See out。Something bad happened。While reading the data。对的。

Right some sort of message here so we can find out， hey， something bad went wrong。

 something bad went wrong， Yes that's good English here something bad happened while reading the data So my totals probably not right again or maybe even just completely skip this piece here so working with file input bad stuff can happen just like we work with user input but if it's completely automated we're not going to notice here unless we go and look for it so you have to be a little bit more careful because we might not even know that we didn't reach the end of the file here or sometimes if we just instead of 10 here if we just have like a blank line let's see I think this might work 246 the blank line works it just keeps on reading past it here that's okay the way that we extract here but I think if I have a space here。



![](img/d2cadc6e5c62aff90d8f828238d53841_157.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_158.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_159.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_160.png)

![](img/d2cadc6e5c62aff90d8f828238d53841_161.png)

I think the space will it on nope， the space is fine， Okay。

 that's it because we're doing CN so we'll be able to get it here。



![](img/d2cadc6e5c62aff90d8f828238d53841_163.png)

So you can work with it。All right。Couning yeah， counting words here。

 that's all sorts of fun business reviews sure input stream errors right it's a good bit。

 the endde file bit， failed bit， bad bit， a couple different things you can check for。

All right we're about out of time so why don't we hold off on output files for Wednesday so in lab today we can work all with input files and be reading data out of files and then next week for lab we can do the output files because we've got lab next week when we're just doing midterm review nothing new so we'll do the midterm review and then the lab will be on。

Output files and we kind of split it up that way。Does makes sense。 All right， fantastic。

 So we pause this， any other thoughts， questions， concerns before we break。😊。



![](img/d2cadc6e5c62aff90d8f828238d53841_165.png)

All right， awesome。

![](img/d2cadc6e5c62aff90d8f828238d53841_167.png)