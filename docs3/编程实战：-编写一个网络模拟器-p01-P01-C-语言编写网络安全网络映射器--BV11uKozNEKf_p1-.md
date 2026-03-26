# 编程实战：-编写一个网络模拟器-p01-P01-C-语言编写网络安全网络映射器--BV11uKozNEKf_p1-

![](img/d2acdde8394d43c332a2e6f3f3cf9289_0.png)

Hello， everyone。 Welcome to today's show。え。This is the first episode that I am releasing for a while。

 I had been taking a little bit of vacation。I'm glad that you are still sticking with me and from now on。

 I will release a new episode。Every four days as usual。

And today we're going to talk a little bit about a network mapper。I'm going to create the tool。

 which I'm going to call Nema。And it'll be a network map， so what is a network map？

There is something called a port scanner。Which is basically the same。

 but the poor scanner is like a black hat hacking tool。

This is a security tool that we're going to create today。

So port scanners are primarily used by hackers to map a network and find out what ports are open。

 like TCP ports most often。And。A network mapper is used by ci admins and。

Se people to check the network if there are any ports open that shouldn't be。

 and perhaps you are new at your job or you're taking over the network that you need to learn。

Then it's a good way to map it using a network mapper。

 So you know what servers are up and what services they are running and so forth。So， basically。

We're going to code something that works。Something like this。 You run a net map， and you give it a。

Starting IP P address。Like this。As an ending I address。Something like it。です。And then a port number。

 for example， 22。So this means that itll。Start with this IP。

 and then it will take the IP with a 2 and3 and all the way up to 200。

And it will make connections to each and every one of them at TCP422， which is the SSH。

If it's unable to connect， the port is not open or its firewall or the server is down。

Or theres snow server with that IP address。 and then it'll do nothing。

 but if the port is open and the connection succeeds。Then it will log that。So basically。

 it will connect to that and。一ょエファイクネう。Local host at work。19 in this case。

 the regular port for SSH is 22， but I'm using 19 on my server primarily to don't show up on network mapping for port 22。

Okay， I'm not chasinging that I pe。 Let's see。Let's connect directly to the external IP address。Okay。

 I think I'm binding it to this 10 address，10，1，2，3。10，1，2。美ち？Oh， port 18。Right。There we go。

 So when I do， when I use Telnet， I basically create a。TP connection。

And this is what the server is sending to us when we connect on that port。

 So it basically says what S isH version it's running。And we want that information。

 so we're going to log that the port is open。And if we are able to get。The version of the SS running。

 we want to log that as well。And we are going to create several versions of this network mapper。

 The first will be a very naive version。 So version 1， naive。 it's going to have a。No threads。

And it's going to use。Block game。Sockets。So what are blocking and non blocking sockets？Well。

 when you this far， if you have watched my earlier videos about H P connections。

 we have always basically always used blocking sockets。That means that there is no concurrency。

 so we use connect to connect and itll wait until the connection is established and then it will continue the program flow。

And when we read data， we use read and it will wait until there is data to read。

 and then it will terminate。And same with right。 It will write。The data and then terminate。

And that is the default behaviour。 And it's very easy to code using that technique because you don't have to worry about concurrency and stuff。

In many cases， this is what we want， but for。Network mapper， no， not really。

 because it will be very slow。 We have to wait possibly minutes per I address if it's unable to connect。

But it's good to create the most naive version first so we can see what we can improve。

The second version。Will be。😔，Like the naive， but with non blockings of。So still no thread。

But where the non looking stock is。So that's basically， if you know jascript。

 like using a single weight， you can。Do concurrent stuff with non blocking sockets。

 So when you do connect， for example， it will terminate instantly， even if it hasn't connected yet。

Same with read。It willIf there is no data to read， it won't read anything。

 it will just terminate and if there is data to read， it will read it。And basically saying right。

 So we need to。Develop a system that will。Check all the open。 It is P connections。そ。Basically。

 we do a lot of connect。Two different Is and these calls will terminate instantly。

Then we want to use the select this。Basically， to。Watch all these open connections。

 So select wheel wait。And when there is。A actionction on any of these socket file descriptors。

Then it will term it， and we can use a macro to check which sockets are。Well。

That's something is happening to。 And the only thing it can happen is basically two things。

 it can fail and it can succeed。So， if we have。Any action on the socket， then we can do the connect。

And。Or then the connect will succeed and we have an open TP connection。

And then we can just select to check for the open sockets as well。And when there is data to read。

 select which terminate， we can check with a macro。

 and then we can call read on the sockets which have data to read。So this will make it much faster。嗯。

And the third version。Then we'll use the real concurrency with threads。

 And I think we are going to use my library， needleto。Great。So this time。

 well have breads and we're gonna have nonbing sockets。

Which basically means that when we have connected successfully to the。To the servers。

Then we can create the thread。Which will wait。For the actual data。And that would make it。

Even more faster， plus， it will make things easier for us because we don't have to worry too much about reading every。

Open socket with select。Only the initial correction will be that way。

And perhaps we will even do a fourth version some time。And then we can do maybe a scene scanner。

That's basically when we use。Ro sockets。So we can send we can alter the IP packets in any way we want and edit the headers and stuff so we can basically send a lot of itTP seen requests to the different ports。

And then collect the synac responses from it， and this would make it incredibly faster。

But we will focus on the first task today， creating a very naive。Easy to write。Network mapper。

Which will be very， very slow， but it will work。And。This first version shouldn't be a problem。

 even for beginners to write。Those will be a little bit more advanced。

 but we'll worry about that when we get to that point。So，We're gonna。

I'm also going to be a little bit structureized because today I'm going to need to write a function。

To convert between I addresses and。Well， basically， it will use this for。

And turns into a number so we can work with it with the sockets and。The other way around。

 and I have written that function twice already， I think。

So this would be the third and last time I'm going to create something which I' going to call birch uts。

Which basically would be my library for utility functions。So。

Each time I would write the utility function that I might have used for in other。

Situations in other projects。I will add that utility function to the library instead。

And we will build on that library and add stuff。All along。

 And then we can be very effective when we have all the utility functions written and in one place。

And this is an idea that I recommend to all of you because you are probably like me that you are rewriting a lot of functions。

 perhaps your copy pasting， I'm not very fond of that， but。You can do that as well。

 but I recommend create your own library。😊，And add all your utility functions to that library。

So I'm going to create a new screen and I'm going to go into my code。And then let create Vi you this。

嗯。I'm going to set my home to。Diiry。And I have already in this code opened the network Ma file through Sociopath directly connected to the server。

But。One nifty feature is， you can。Go into another directorate。 So I'm currently working。

Against the net map directory。But if I go to my code and I go to Brchio Tis and I open this in editor。

Then it's going to。Connect， and it will。Create a new window like this for this bertuo directory。

But one nifty thing with。VS code is you can take this directory and put it here。

And then you click add folder to workspace。So I can close this one down。

 and now I have both my directories。In the same place and when I create files or edit stuff。

 Sociopath SUP will update all files for me。Okay， so let's。Begin with the make files。

I will begin with a virtue to make fun。This make that。And what do I need here。It's kinda big。

I hope this will work for you。😔，え。Let's see。 We want some flags。And I'm going to juice。Oh，3。

 for optimizations。 I'm going to use wall。And I'm gonna use the C standard C2 a。Like this。

Perhaps we're gonna have an LD flags as well。 I leave that， as is。And what are we going to do here。

 we're gonna have a。Let's see。We're gonna want to create a。O file first。

 So this will be birch us dot O， which depends on biirch us dot C。And then no， let's see。

And order to compile list。 We're gonna run C，With some。来。And that see。Are we gonna take。Source spell。

Like this。When we have an O file， we can create our library file， which is SO。

Which depend on the births dot O。And in here， we're going to run CC with the flags。

And we're gonna take the source file。And compile it to the target file。Like so。I also want to have。

Let's see。The onena have。Clean。Thank you。Which will remove。Birch you。Oh。そ。And all will be。First。

 clean， and then birch。ゆうてす。そう。Likeそ。This will work， I believe。

We do need a couple of additional flags because we're creating a library。

 and I always seem to forget。Those flags。 So let's see。 Let's go into the。Filees and directory。

And our library。And live are worth making。So these wool if epicpic share， aeleele and new source。

And as you see， the make file has been uploaded。Auttoomaically。So let's add that to the flags。

 like so。And now we have a make file。 So if we do create this。Let's see。

I want to have a birchdu tous。8。And I wanna have a birch， youtius。The see。And。I need to save。

See my very。Because it uploads every time it saved。 Okay， so if I run Mac。It will create our file。

 like this。Okay， so that's the burst of tools。We're not gonna worry about that， for now。In。

It'll be when we are dealing with IP addresses。So let's do the same for this network mapper thing。

In this case， I will create netmap。 Let's see how were gonna name this。AndLet's call it。Ne map。

 And then which version it is。So， next。Nive。どつ？Like so。

And the H file will be common for all the different versions。 So let's just call this Nema。お？

Like some。Ened that update。As well。I。And we need a make file for this as well。

And this would be a little bit bigger since we are dealing with several different versions。

 but not much。Its very。B。Okay， so let's do the same。 We begin with the flags。 I want 03。 I want wall。

 I want standard。 I'm going to speed through this a little bit。Standard C2 x。And leaf flags。

 perhaps we're going to use those。By the way， I almost forgot I didn't use the LD flag with my2 to do that。

So， let's add those。So we don't forget it。Perhaps， we should。Move this part。Yeah， I think so。

We make L flags out of this。Swes。O。In this case， we're not going to have any leafx to begin with。

 we're going to link in our Bir Ju library， of course， but thatll be later。For now， let's just。

Start with the。And then。Nve do O， which will depend on an。Nive， let's see。And we're gonna run C。

 with some flags。And we're gonna run dash C and this source file。When we have an O。

 we can create the N。The Eve binary。Which will depend on the N M。Ned of O。

And we're going to run CC with some flags。And then we're gonna take the source。File。

 and we're going to produce the target file。And use our L flags， as well。

And our all we use clean and then and not E。And we also need to。Create。きの。

And I will just simply remove all the old files and Nm。じいい。That ought to do it， I think。Yes。

 it comps， but it can't link because we don't have a main。As expected。Okay。

 that was information and preparation。In the next section。

 we're going to start the actual coding of our tool。Alright， so。Let's see where we were。

We have our make file。 We don't have to worry about that anymore。

 and we can close this town as well to get some more space。😔，Okay， so first of all。

 we need a couple of includess， and as usual， I'm going to take the standard ones that I use in almost every project。

And if we want later on， we can prove off if we don't use them。It's a better way， as I usually say。

 than to add one at a time when needed， it takes。Longer。And we need S lid as well。

 And let's also use。Third。呃你你。Our number as well。 I also want to have SD pool dot H。

And we need to define。嗯。Source， I think we did that in the。The make file。

 but let's do it here as well so we can use our。A3 p error。

And I'm also going to create some data types， as I usually do， and then do a type depth for。

un signeded Sha。 And this would be an in a。I'm going to type the。Unsigned。Short in。In 16。

And I'm gonna type if unsigned。え？In。2832。Like so。Right。So， let's。

Let's also create the function declarations。We're going to have a main， and we're going to use。

argumentsguments。So， let's do it like this。嗯。It made with dark， and。小指。And if O C is less than。

 let's see。 we need three arguments。 So it's， if it's less。Then。5。Let me think if this is right。

 So if we have one argument， this should be a2。Okay，4 them。If it's less than 4。You should err。

But we want to write the usage to the screen。So if pre def standard error。ジセ。best。And。Let's see。

We want to have the port， first and foremost。So。That should be compulsory。And then。

 we want to have a。Start I P address。And。Whatち do like thisす。And we also want to have。And。

And as you see， I have those in。Those kind of brackets， which means that those are。え？

Not necessary to use。So let's change this to two。Because the port is the only thing we need。

 So if we supply a start I address。Let me show you。Here， instead。So， if we run。P run network map。

Again port 22， And we give。An I P address， like。This。The start IP address。

 but we don't give any ending IP address。Then， it will default。To the last possible。I P address。うん。

If we do give them。Arrange。Like this。It will follow this range。へ。And， of course。

 this ladder needs to be bigger than this。Or at least。As big。

And we can also do something like this when we only supply the port。

And then as you might have guessed， it will read the I addresses from the standard input instead。

 So you can basically do something like this where we have an。Add file。

 the T C that we put into this。Or another way would be simply to do something like。呃 cat。

Address file dot T C and pipe bit。The that matter。So。We want the tool to be。

Useer friendly and adding those functions is quite easy。And it'll。Make for a better user experience。

 so I think it's important。Let's do new line here， and also。You need to send the ugly。

So this first argument or argue will be the name of the binary that we're executing。And then。

We will simply return-1 like this。Otherwise words。Return 0。Something like that。 Does it compile。

Let's see， oh， what happened there。Oh， I forgot to。Include our own H5。So， include。

What did you call it that map dot age。And now it compiles us fine。 If we run it like this。

 it will give us the usage。 And if we give the port， it will not。Alright。Noice。

So how are we going to structure。All of this。We do need have a function， which will。

Calculate this range。And we also need to somehow generate。The P addresses。So。

And that should be one of our utility functions。So basically， that would be in our Brch U library。So。

Yeah。In order to go from this kind of format。The regular Actpi was four months like this。

To the numbered format that we're gonna need when we connect。

There is already a function in the study library， which is called the E address。

So we'll use that one， but the other way。Then we want to go back。

Then we need to create our own function。But perhaps we should wait a little bit with that and focus on the actual range first。

So let's create some function， which will。Let's see。Should we。嗯。

I think we're going to make it a little bit easy for us。 I'm not very fond of global variables。

 as you all know， but we are using C。😔，Procedural language。

 and we are allowed to have global variables。So let's at least have one for the current。IP address。

And which format is that。In。Let's see if we run this， I note address。本庭。What does it return。Okay。

 an in address T。And in a tea。Is the structure。嗯呢。😔，Mei。😔，Addres。無て。

Have you ever seen this format before， So you just struck it。In address。

And then a function is there some kind of constructor function for structures。I need to Google that。

C。对。Construct。now， this is the regular stuff。The图。😔，O。😔，你。Compound later。

I it supposed to declare an inline function with the same name as structure。

Stt my EM A in line struck。Maai。😔，My。And a。Return。St。😔，He。It really is。

A constructor function for structures in sea。How can I have missed this。

I think I'm going to make an episode about this later on when I have experimented a little bit with it。

But it looks really cool， doesn't it。Sometimes you just stumble upon heaven。Cool things like this。

Allright， so that's basically how this is done and they have an ionnetmic address。

 which is a constructor function which generates those ion in addresses。

But this is what I was looking for in address T will be our return tag for the IP addresses。

Which makes it suitable as a type for our。Global， variable。So。Let's create an。

What is it called in address key。Was it。Yeah。And let's call this。Oh we。Let's call this current。

So this will hold the current value of the IP address and we will just simply increase this by one each time we want a new IP address。

So I would create a generator function。For that purpose。We do， however， also need a。An ending。

do we really need to have a global variable for that。😔，No。

 I think I'm going to pass that as a argument instead。But then， we need to。

Ju that in barrel in many different places。It's a bad habit， I think。

 that I'm getting used to using all these global variables， but。Let's do it。Okay。

 so we have a current and we haven't。Ending。And。Let's see。We will create our generator function。

 and that will be of the same type in address T。You know it。🤧Sorry。And we don't need to have any。

Arguments done， since were using the global variables。And what we do here， Well。

 we take the current and we add one to it。And if。Current。More equal to。本0。Let's see。No。

Then we will skip the last one。First， we will check this。And if。Current is。At the last IP address。

 then we want to return。In。T of 0。Otherwise。Will increase current。

And I know the else isn't necessary here， but I think the structure looks a little bit better。

And then， we return parents。Like so。This makes our lives a little bit easier。We should not forget to。

Initialize those variables， as well。So， let me see the return。嗯。This。Et address。 What if it。

What if it fails， How does it。Tell me。😔，Standard tri。Otion。😔，Where is the return value。Okay。

 if it returns 0。都在死ね。If the input is invalid， in none will be returned， usually-1， usually。

Well well。Let's use this then。So if it fails， then it will return in address none。See。We will set。

Current。First， we need to find out if we even have。Toes。So， if O C equals。Let's see。2，3，4。

 Then we have。Both。我 maybe should do。If they。It's more。2， then we at least have one I P address。

So let's make a block out of this。So in this case， we at least have the first。I P address。

So we will set current equal to I address。第ぎ。2。Like soon。And if。Org C is more than three。

Then we have an ending address， as well。So then we can set ending equal to I address。呃的。3。Ex so。

And if we don't。Then we'll set ending equal to。かいね。Let's do this a little bit cleaner。Ending equals。

 okay， so。If A C is more than 3。Then we will return the e of a 3。と。え。And if we don't have that。

We will return the island address of。2，5，5，2，5，5，2，5，5，2，5，5。Like so。All right。

Let's also do some sanity checking。Like。If。It did this。If。嗯。If current。Is equal to。This thing。我。IfN0。

Yes cool。To this thing。我。If。En the。Ening is smaller。Concur。Then we'll do this again。

And you return right as well。So。Looks okay。😔，By the way， the E address。

 do we need any include for that， Yes， couple。So， let's put it inside of our。See for 1，2， No， it's。

嗯嗯。Okay。Let's see if it compiles。We can add some temporary stuff， by the way。

 So we see a little bit more what's happening。So if it succeeds， we can print out。Precent D。And。And。

这先。We're gonna send。And。Perhaps we can just put it here without any casting。确认。If we can't。

It will tell us。Most， definitely。Although semicolons。There go。Allright， compiles。

And if we just give it a port。Then we don't have any start and end。If we give it a start。

 I P address， lie。不用。No no。Didn't quite like that， the thing。What if we give it an ending as well。

Okay， then it works。So these are the numeric versions of this， basically。But it did not work。

When we didn't give it。😔，An ending， it should default to this 2，5，5 fella。Wai a second。This。

This I net address none。 It defaults to -1 and 2，5，5，2，5，5，2，5，5，2，5，5。 What is that， Well， it's -1。

Okay。That's not。Too good。Let's check where does the multicast addresses begin。Maybe， we should。

Only used real I addresses。Let's see。I it。😔，1，92， something。 That's the IP P address glasses。没有没有。土？

嗯。Private address range。Okay， so this is the list。😔，I P address before the multi cast addresses。

And this is private type address。 But perhaps you do want to。A scan， private addresses。

 so we need to handle that。So let's see it 2，1，2。你是。😔，Wait。😔，First us advice range from 1，92 to 22，3。

Okay。😔，So， this is basically。The last one。Yeah。All right。So instead of doing these， this 2，5，5 thing。

Let's use。2，2，3，2， the，5，2， the，5。0。It's weird that it ends in a0。I think I'm going to do2，5。For。

2 by5 instead。Okay， so now it works。 If we just give it an IP address。

 it will scan all the way up to。The last。Real I P。Uniccast address。Perfect。Perfect， perfect， perfect。

Kay。So now we have a little basic structure。😔，Let's create。The generator。 And that is。

We don't need to do anything more with the。We do， however。

 want to remember to add that to our list of functions。So， we will have an。In address T。Of。Genrate。

Vid。エきそう？So， now we have the port。Perhaps we should save the port somewhere。😔，As well。Yeah。

Let's do that。So what format do we want to port and let's。メクエセキスティのた。And。Po。Let's do it。で。

P right here。And before that， we will do。Port is equal to the N 16。哦。L。嗯。Like so。Okay， guys。

 that's all for today。And。If you like this episode， please like and subscribe。

 I will begin recording the next episode today， probably。But before we end for today。

 I'm going to show you one thing。We do have a chat server。Now。

So if you go to chat doctor or Birch dot com。Por 9000。You can connect to our chat。

 so you put your nickname here。And you can have the same user name。At this real name field。

 you put your。YouTe。name is my is Dr。 Jonas。对对。And then you just click connect and you will be connected to our server and you can send the messages to me and to the other subscribers and members。

And if I don't reply directly， I might be doing something else like recording an episode。

 but I will check the chat every now and then the upcoming days。

 so please stay there and we are having a competition currently So Sha the topic inside of the channel and you can win fine prizes。

Okay， thank you guys for today。 and take care， everyone。



![](img/d2acdde8394d43c332a2e6f3f3cf9289_2.png)