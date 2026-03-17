# 【全集】加州大学戴维斯分校 分布式交易与区块链架构 中英字幕 完整课程 p04 扩展：Web3 - 用区块链编写DROPBOX复刻版 -BV18YFVzME2f_p4-

Gys， I am back with another blockchain tutorial。 I'm super excited to share it with you today。

 So I'm gonna show you how to create a blockchainbased file storage website just like Dropbox。

 And as always， I'm gonna show you the hottest skills and technologies that you can use in order to land a high payinging job。

 become a freelancer whatever you want to do We're gonna use the Ethereum blockchain and also IF these are two really inde technologies。

 But don't worry， you don't have to be a programmer right now or know anything about blockchain to get started today。

 I'm gonna show you everything step by step。 I'll show you how to create the Ethereum smart contracts the solidity programming language。

 put them on a blockchain and then also create an app that you can show your friends and also use for your portfolio if you're trying to get hired。

 So before you get it all that。 if you're new around here。

y I'm Gregory and on this channel I turn you into a blockchain master So that's something that you're interested in I bet you are because you're watching this video smash that like button down below and subscriber this channel and if you like this tutorial and you want to take the next step or each want to pause this video take a massive shortcut entirely then head over to deput。

😊。

![](img/42765643d30b926b61467dd8d1f5adec_1.png)

co4 bootc I can show you how to build a step by step blockchain application a prole application that goes way beyond this tutorial Just click the link down below to sign up today that being said let's jump in and get's demo of the application we're gonna build together in this tutorial This is a decentralized dropbox that runs the and also the interplanetary this will allow us to files in a decentralized way and also share with others in a trustlessship resistant fashions take a how this application will work So here's a quick diagram of how a traditional web application work let's dropbox example so when you use the dropropbox website you get on your web browser。

And you talk to a server and this is where all the code and the data and all of the files for Dropbox lives know on the central server So all of the backend logic is inside of an application like this all the codes in a database and all the files also live here too and when you store files in the cloud in this way is a very centralized models。

 So any of your files can be sensored at any time and you also have to pay to store files here for a long-term basis but by contrast。

 here's how the application that we're going build together today will work so instead of talking to a web server a centralized version of Dropbox we're going to build a decentralized version where you use your web browser and you connect with a blockchain wallet to the blockchain。

And this is where we will store all the code for application inside of smart contracts。

 We're going to use Ethereum for this tutorial so we'll write Ethereum smart contracts to store the location of the files and then we'll store these files on the interplanetary file system So IFS this will work a lot like a blockchain but it's a different way of storing files also decentralized and this will allow us to store these files here for free for the long term and then also they'll be censorship resistant。

 no central party can take them down and here is a technical diagram of how this application will work So these are all the technologies that we'll use to build this application So we'll see these here in a minute we install the dependencies and also as we build the project but basically a user will interact with the application that we build and react JS and this application will talk to the blockchain so we're going talk to Ethereum in this tutorial and we'll use a blockchain called the Gache which is a development version of Ethereum and our react application will also talk to IFS the interplanetary。

File system whenever we upload these files so we'll upload to IFs we'll develop smart contracts that store the location of these files。

 we'll put them onganache and then this will allow the user to view and download files from this reactact application as well as upload and store them So here's an even more technical diagram this is from the D creator's perspective where they will connect this application through the development lifecycle with a truffle framework So if you want to study this more in I highly recommend pausing this video and looking over this Now let's install the dependencies beneath for this tutorial the first dependency is node js。

 This is gonna allow us to install all the packages on our computer as well as run our client side application。

 So you can see if we have node already installed by going to your terminal andtyping node so I'm using node 910。

0 I would recommend using the exact same version for best results during this tutorial but you can probably use the latest version if you really want to and you know what you're doing so you can download node directly from the website or you can use a command line tool like Homebrew。



![](img/42765643d30b926b61467dd8d1f5adec_3.png)

![](img/42765643d30b926b61467dd8d1f5adec_4.png)

![](img/42765643d30b926b61467dd8d1f5adec_5.png)

![](img/42765643d30b926b61467dd8d1f5adec_6.png)

ackage manager to install it that way The next dependency is the truffle framework This is a framework for creating Ethereum smart contracts。

 We can write Ethereum smart contracts with the solidity programming language tests against them and deploy them to a blockchain with truffle as well as many other things which you'll see in the tutorial you can install truffle from your command line like this say n install truffle version513 The next dependency is theganache personal blockchain This is a blockchain that run on our computer we can simply download it and run transactions in the blockchain deploy smart contracts to it without having to pay any real money so go ahead and download can just click the version for your operating system here and whenever it's download you can open it and you'll see that you have a brand new blockchain running computer just like this you'll see lots of different accounts funded with100 fake ether and don't get too excited because this isn't actually worth anything The last dependency is the metamask extension for Google Chrome。



![](img/42765643d30b926b61467dd8d1f5adec_8.png)

Most modern web browsers won't connect to the blockchain out of the box and so we need to install a special browser extension to do that。

 That's exactly what Memass does。 It's an Ethereum wallet that turns our browser into a blockchain browser so go to the Google Chrome Web store find Memask and click install and once you have it installed you should see a Fox icon in the top right hand corner and just walk through the setup steps to get that started Now let's start coding the project so heading over your terminal and clone this repository from GiHub so I'll put a link down in the description below this is just the D University Github repository or Github organization and this Dtorage repository is where all the final source code is for the application we're going to build again as well as this diagram here don't we saw a minute ago。

So， you know， if you want to ever check your progress with the final code solution and this tutorial。

 then you can just look at this repository and you can download it。

 but what I'm going to do is actually。Cone a starter branch so we can get it started fast on to build everything from scratch。

 you can see this you know starter code branch here。

 that's the one that we're going to download right now so you can switch to that and you know click the download button here right。

Download a zip file if you want to， but I'm going to do it with git， so I'll do it like this。

 we'll just copy this URL here and go to our terminal。😊，Say get clone。Dash B is a specific branch。

 So starter code。All right， and then paste in the URL here。

 and then I'm going to call this what we call it you know D storage。All right。So it looks like sorry。

 I got to change this URL here， make sure you just go back here， I did the master branch。

 so don't do that， just copy this。Replace that one more time。All right， try this boom， there we go。

 awesome， so now we'll enter that newly created directly like this， we'll say CDD storage。All right。

 and now we will install all the project dependencies like this with node， say MPm install。

And then wait for that to finish。All right， now that's finished let's go ahead and test out the starter code。

 let's go ahead and start the server for the web application。

 so I'm going to open a new terminal tab here and I'm going to say MPm。Run， start。

And this will start up the front end application for us in a new window here and here you can see the starter code for the you know application so we'll come back and edit this later al right we're going to code this tutorial out in two sections we're going to start with the backend the blockchain part we'll code the smart contracts put them on a blockchain as their final version and then we'll come back and you know wire up this clientside application that you see here to actually talk to the smart contracts and build out the you know build out the user interface so I'm going to leave my web server running here for now we will revisit this like I said。



![](img/42765643d30b926b61467dd8d1f5adec_10.png)

So let's go ahead and start coding at the back end so the first thing we need to do is make sure that Gaache is running all right so go find Gaache wherever you download it and open it and whenever you have this running。

 you'll have a development blockchain running you'll have 10 different accounts with 100 fake ether in it this is know athereum cryptocurrency it's now worth anything in the real world don't get excited but we need this running in order to code out the smart contracts that will put on this that will create this tutorial。

So I'm going to go ahead and open this in my text editor， I mean in some blindme text。

 you can use whatever text editor you'd like。

![](img/42765643d30b926b61467dd8d1f5adec_12.png)

But we'll go ahead and take a quick tour of the project。

All right so I'm going to look at the truffle D config file first and foremost。

 this is how we configure the truffle project to talk to the blockchain you can see there's some kind of advanced configuration in here。

 but the most important part that you need to understand is this this is how we talk to Gash so this is the development network configurationguration for local host sorry local host port 7545 and this is the blockchain that we're going to use if you want to use a test network later you can always use Robton because it's preconfired for you。

But we're going to use Gaache in this tutorial All right， so next is the source directory。

 this is where the front end and the back end part of the application will live。

The components directories here， this is for all the client side code for react AS we'll come back to this later。

 but the important part that we're going to focus on now is this contract directory。

 this is where all the Ethereum smart contracts written in solidity will go for the project。

In this case， we have the migration contract which comes standard with every truffle project because we're using truffle to develop this。

 that's what you see that's all those code is， but we're going to create a。

Our own smart contract here called D storage， okay， and so you can see that here。

So we've got some basic code in this file already， we basically have the skeleton of the smart contract with a bunch of instructions here on how to create it。

So we're using this starter template so that we don't have to create everything from scratch so we can make the tutorial faster。

And so that you can sort of see the important parts without you know having to do everything step by step。

 and so we'll use this as a starting point right so。I'll explain this file At the very top。

 we have the Soity programming language version， just pragma solidity version 0。 5 to 0。

 And the next we have the。Beginning of the smart contract code so contract D storage that's what the app's going to be called This is just the name of the smart contract and we put all the code for it inside of these curly braces here all right so we can see that we have you know several different。

You know， comments here with some instructions， so we'll just go through these one by one。

 we'll start off with。The basics we'll just start off with the basic variable all right so inside of solidity you know it's a fullb programming language it's it's a tu complete language looks a lot like JavaScript if you ever coded JavaScript before you might this might look somewhat familiar all right kind of user friendly it has variables。

 it has loops， it has data structures like arrays， strings， functions all that kind of stuff okay。

We're going to see lots of examples of those inside this okay。

So this smart contract today is going to be pretty simple， let me tell you what it's going to do。

 go back to our diagram here。

![](img/42765643d30b926b61467dd8d1f5adec_14.png)

So whenever we access the application， you know we're going to talk to the blockchain and also IPFS。

 so how the user flow is going to go is like this basically someone's going to talk to the reactact application。

 they're going to upload their Dropbox like file to IPFS and then IPFS is going to return a hash。

 okay。So you can see what an IPFS hash looks like right here。

Here's an example of an IPFS based website all right， here's what a hash looks like， okay。

 so IPFS hash looks like this。Let me change the font size here。Okay。

 so it's going to return something looks like this， okay？

And this is really just the ID or the location of the file on the IPFS network。And then。

Once we get that hashback， we will store it on the smart contract right here that we code out on Gash and that's what we're going to do right now So this smart contract holds all of the hashes in one place。

And puts them on the blockchain so basically the dropropbox is going to be sorry the smart contract will be like on our database that tells us where all the files are and the hash of the file IPFS will be the location of the actual file and then we can retrieve it from IPFS once we know that location okay it's kind of like the address basically。

So this contract needs to do a few things， let me just pull the code here。



![](img/42765643d30b926b61467dd8d1f5adec_16.png)

Yeah， we're basically it's just going to be a we're going to use the blockchain as a database to store the location these files and the smart contracts going to facilitate all that so we'll go through all that one by one okay。

So we'll start off with the basic tests， let's just give this a variable name here。

So we'll say string public name equals D storage， okay so this is。Basically how we create a。

A variable in solidity and this is a state variable called name and it's a string okay so that's why we tell it string here because solidity is a statically typed language we have to tell it what data type the variable is before we create one okay and then it can't change after that and we call it D storage and then we call it public so that we can access this variable outside the smart contract so that's different from a local variable which we'll see later when we start building out these functions。

Um， but here's the basic name， Okay， so let's let's wait is this in action？

Let's go to our terminal here and let's open this in our console。So first。

 we're going to say truffle migrate。Okay， and we're going to put this you know work in progress copy of the smart contract on the blockchain and we're going to interact with it in our truffle console to see this behavior in action Okay so before we do that we need to make sure we have a migration file so we can go to this migrations directory and we can see this deploy contracts file。

So we want to do is update this all right， so every trouble project comes with this initial migrations file。

 okay， but we want to add a migration here that puts the smart contract in the blockchain so we can use this as a starter code so we'll just copy this and then all right。

 so well just say。I would just say like this cause D storage equal to artifacts require D storage okay。

 that just pulls the smart contract into our file here and then we're going to deploy it like this。

 so just deploy deploy D storage all right it's pretty simple。

So now I can put it on the blockchain like this， I tru and migrate。

 I'm going to go ahead and use the reset flag here in case there's any。呃。

Old code inside of here I recommend you do the same I typically do it in development just as a easy practice I'll explain this more later but。

Okay， awesome， so now it's on the blockchain and let's open it in the terminal like this in the truffle console。

 say truffle console。Oops， sorry， tyypo。And then we can fetch a copy of the smart contract in this JavaScriptscript runtime environment here。

 So inside the T console， we're interacting with a smart contract which is written the solidity programming language。

 but here inside the T console will we'll write JavaScript commands to。Interact the blockchain。

 interact with the smart contract， all that kind of stuff， so I'll show what that looks like。

 we'll say you know D storage equals a weight D storage do deployed。Allright。

 this will get a copy of the smart contract from the blockchain and then I can say decent name equals well here we go。

 some people get confused because this says undefined All right， that's just the。

This is the console log value， it's not the actual return value if I can say de storage just call the variable again and then boom it appears on the screen so here's a JavaScript copy of the smart contract okay。

So now we can read this name variable value from the code like this。

 I can say name equals 0 weight D storage lowercase D。 name， all？They'll say undefined。

 but we call the name variable again and then boom， there we go。Awesome so。

That's how we can you know talk to the blockchain with the trouble Con。

 talk to the smart contract with T Con， and this just really make sure that we've got everything set up properly that we can talk to this smart contract that this name variable was set correctly you get a basic idea of how you can create variables and sensitivity。

 that's the basic smoke test just to make sure that we're on the right track right？So。

With that being confirmed， let's go ahead and code out the rest of this smart contract。

So like I said， we're going to use a smart contract to store these。



![](img/42765643d30b926b61467dd8d1f5adec_18.png)

Hashs of files on IPFS okay， and so we want to do is code out a basic database like behavior so we can do that with something called the mapping inside Soity。



![](img/42765643d30b926b61467dd8d1f5adec_20.png)

So that looks like this so mapping is a key value store。

 so basically like you give it a key and it returns a value so like you know key equals one。And then。



![](img/42765643d30b926b61467dd8d1f5adec_22.png)

The value equals。You know， like some IPFs hash， all right， and then like， you know， key。



![](img/42765643d30b926b61467dd8d1f5adec_24.png)

K equals two and then the value equals。You know， like some different hash like Kb， one，4， five， six。

 blah， blah， bh bh， blah， and like that， like these be different files and so。

That's how a database would work where you say you know file number one， the value is this。

 file number two， the value is this， you know file number 3， etc cetera， etc cea， etc ceter。

 and as you add more files， these numbers increase and then you know it maps to the special hash for the file and IPF that's what a regular database will do and that's exactly what we can do with the blockchain with the smart contract we're going to program this thing called the mapping to do this it's basically going to give us an ID key value pair relationship just like that So we'll say mapping。

And so what we do here is give it you know the key and then the value， okay。

 and that's how we create the mapping and we give it a name， you know， files， okay。

We also call it public we can well anyways， we'll get there a second。

 so the key is going to be we have to give it the data type for the key and the data type for the value。

So the key is going to be an unsigned integer so youent so this is basically just a number without a minus sign in front of it that's hence you know not signed unsigned。

 so it can't be negative and then the value is actually going to be a file okay and then we're going to call this public。

So that we can access this with a function outside of the smart contract just like this， all right？

So the data type for the ID is an non sign integer just we saw a second ago， you know，1，2，3，4， 5，6，7。

89，10， etc cetera， et cetera， onto you know， a very large number。

And then the return does to be a file okay so but what is this file。

 where does it come from Well we're gonna create it al right and we do that with something called astruct inside a Soity So astruct solidity allows us to create our own data types so you can see data types like you know string mapping array all that kind of stuff these are standard data types。

 but now we can create our own like this， we can saystruct file。All right。

 and this is basically going give us， you know， somewhat like a database object kind of kind of like a database object that gets returned whenever we you know read it from the blockchain。

So this allows us to store all the files， all the attributes of the file that we need for Dropbox。

 okay， so we can define the data type and then you know， give it a bunch of attributes like this。

 okay？So we can say， you know， it has a file ID if that's an unsign integer。

 it has a file hash for IPFS， that's a string， it has a file size， file type， name， file description。

 upload time， and then the uploader， okay。So that's's what the filestruct looks like。

 so going back to our mapping， we have this unsign integer。

 the ID and then the file and then this is all the attributes of the file from this customstruct that we create okay。

So now we want to actually create a function that uploads files and stores them， okay？U。

 so we need a way to add new files and then a way to fetch files， okay。

So we'll create an upload file function like this， we'll basically just say you know function upload file。

 okay。And then we'll write all the code for that inside of here so we can copy this。

And then put it inside here， these can be our notes for what needs to happen in here。All right。So。

Yeah， we'll call upload file， this would be the function that we create and it's going to create a new one of these files and put it inside this mapping so that we can read it later from the blockchain。

Soum。We can add a new file like this。 we want first when I create a new file struck， so let's just。

 I'm going to do it at the top of this file so we don't。Get too confused here。

 we'll say you know file。And then we want to add all these， you know。

 attributes so like file ID might be one， you know， file hash might be like ABC， 1，2，3， you know。

 the unsign integer might file size might be， you know， 10，24。You know， name might be fubar。

Description， food， bar， bath。And then upload time might be some like timestamp。

 and then the uploader might be 0 x0， right？So that's that's how you would create a new file。

 so you're basically you' creating a new you're instantiating a new filestruct like this。

And then with an idea of one， these are hard codeed values， will change this。

 but this is just an example of how it work， okay？And then you could add it to the files mapping this thing right here。

 files like this， you could say files， all right， and then you'd say you know one equals this and that would be like we're going to create a new file here。

 boom， and then in the same line we assign it to the new files mapping like this ID1 okay。Soum。

You know you could just hard code this function and that's what I would do create a new file every single time the ID of one okay。

 so let's get more dynamic， let's not hard code this okay。

So the first thing we'll do is actually replace these values。 We want to get the file Id。

 the file hash。 So we're gonna pass those inside of a function。 So we'll say。

 we'll add some arguments like this。 We'll say a string memory。File hash okay。

 and then that could replace this。Okay， boom。All right。

And then also we'll do the same thing for these other arguments， you know， file size。

 all that kind of stuff， okay。So I'm sure to replace all these here。Like this boom， all right。

 so file hash， file size， file type， file name， file description。And then also while I'm here。

 I'm going to call this public so that we can call this function outside the smart contract just like we did here。

 all right and here。Okay， and so now what we want to do is replace all these so after the ID。

 we'll say this file hash， file size， file type， file name， file description okay。😊。

And then next you want to replace the timestamp， what's really cool is we can generate a timestamp it littleitude like this。

 we can just say now， that's pretty cool， and it will store the current time from the blockchain into this right here。

And so next we want to determine the person who's calling this function right so the cool thing about solidity is it has a global variable that allows us to find that information there's a global variable called message。

 so MSG。And we just say message。ser。And that will give us the address of the person who's calling the function and that way we can just save that as the uploader here so there there's a couple two little pieces of magic。

 the upload time， we can just use the now timestamp and then message。

ser will give us access to the person who's uploading it so essentially the uploader and that allows us to save the uploader here okay。

All right， so now。That gets most of the。Dynamic behavior in place。

The next thing we want to do is replace this one here so if we were going to leave this code as is basically we would overwrite this every single time and you would just create a new file with ID of one。

 but we dont want to do that we want a new ID every time we call this function so the first time we call it this will be file number one the next time we want file number two etca。

 etca， etc。So we're going to do something called a counterc all right， so we'll create a new。

We'll create a new variable inside of solidity like this， we'll say boom， so file count。

 so unent public a file count， we' going start at zero and then basically what's going to happen is we'll use this file count as an ID management system it's a countercache。

So before we get to this line， we want it to be one the first time we call the function。

 so it's currently zero。So we'll say， you know， file count。Equals。😔，File count plus one。All right。

And then we'll use file count here for the ID okay。Then that will give us a， you know。

 a complete function guy that I'll give us how the basic。Behavior we need for the function。

 this is how we'll create new IDs every time this function is called。

And that's really the core functionality， but we want to make this a little better。

 we want to say we can write this as a shortcut instead of saying file count equals file count plus one。

 we can just add one every time this function is called like this and just say file count plus plus okay。

 and then boom that will actually increment file count by one every time this function is called it's a nice shortcut。

It's very common in other programming languages as well。All right， so yeah。

 that's the basic functionality for this upload file function okay， so it'll work just like this。

 we wouldn't really have to do anything else if we wanted sort of a minimum viable product。

 but we want to make it a little better all right。We want to first。

Add some requirements here to make sure that they don't。

Don't break their app doesn't break whenever people to try to use it， okay。

 so we can do that like this， we can use something in solidity called the require so require function。

So we use a function looks like this。And this function， what it does is it。

It makes sure that something is true before it continues execution so we can pass in a special value here or an expression like。

 you know true。Or false。Allright， or an expression that evaluates true or false。

 I'll show that a second， but basically if whatever's passing require is true。

 then this function will continue executing and then it'll actually get to this line and we'll see file count increment and we'll see the files added to this。

 but if this evaluates false then this will blow up and exception will be thrown and these lines here will not execute okay。

So。Yeah， that's the basic idea， but we can， you know。

We can we can create expressions inside if you rather than just hard coding true or false。

 So we could say like you know one plus one equals two that would evaluate to true。

 and then this case require would。This requirement would be fulfilled and this would execute。

 but if we said two plus2 equals three or4 right here right。

 then this would of course evaluate false and then these lines would not run okay。

So we're going to basically do this several times。 so what we want to do is basically make sure that the。

File hash exists。 So like somebody passes in a file hash， right， So we can do is say require。

By we can require the file hash length is greater than zero。

 So first we convert this to bytes right and then we call length and if it's longer than zero。

 then we know that the hash exists and it will satisfy this requirement and。Then， oops， sorry， then。

 yeah， this will work。So same thing for file type。All right。Okay。

 and then we'll do it for the description the name and the name right。

' very same thing over and over and over。We'll just do it for all these things， all right。

So next we want to make sure that the uploader address exists， okay， so do they like this。All right。

 so basically we say message sender， which is， you know， what we used here。

 we want to say it's not equal to the zero address okay。And then last。

 we're going to make sure the file size is is this all right， so it's bigger than zero all right。

So that adds some requirements so the app won't break when people try to use it the wrong way。

 essentially。All right so next what we want to do is actually trigger an event。

 so Soity allows you to have events that can be subscribed to by external consumers。

 namely our client that application， and we want to trigger this event down here so that we can know any time that a file is uploaded all right。

So we'll just create a new event like this， sort of like astruct， would you say event file uploaded。

Okay， and then we can add all little arguments inside of here for the application or sorry for the file upload。

 it'll look almost exactly like the file， but we'll just do like this， right？

So it's basically the exact same arguments， looks almost the exact same， all right。

 except we use commas here instead of you know， semicoons。All right， in the very bottom of the file。

 we'll do this， we'll just say you can trigger the events like this。

 say emitm you know file uploaded。All right， that's how we trigger the event。😊。

And then we're just going to pass in all of the same variables that we passed in here okay。

 so we'll just do that here， right？So boom， there we go。 That is our complete smart contract。 Okay。

 so let's go ahead and finish it off。 Let's go to our terminal and。Clear this out。

 I'm gonna say truffle， migrate， dash， dash reset。 Okay， so this will compile it。

 make sure we didn't have any coding errors first。 right， that'll be the first step。

 So it says compileiling contracts。 Alright， so we got a little issue here。 So let's see here。

Ex this， but got constructor Okay， so I see what the problem is， let me just fix it really fast。

 okay？We forgot to add a semicolon here after the event all right。

 so the the correct code solution is in the GitHub repository if you have any issues like this。

You know you can just check your code solution so that's good the compiler is doing its job。

 but now it's compiled properly so you can see the first step is compilation this basically just checks for any coding errors there are no coding errors so it migrates the contract to the network okay。

So one thing I want to note here is that we use truffle migrate with the reset flag and I did this at the beginning of the video。

 but and explain what this is， so smart contract code isn immutable， that's the whole idea。

Once you create a smart contract and put it in the blockchain， it can't change， okay。

So if you want to create， you know， if you want to update your code inside of truffle。

 like we did here， you know， we started off and just had a basic smart contract that had the name variable。

 but then we added a bunch of code。The only thing you can do is deploy a new copy of it to the blockchain。

 okay？And that's what we do with the reset flag here okay。

 so it puts a new copy on the blockchain and then updates truffle to know the address of the new smart contract okay。

So now that's done。We want to go ahead and continue on by building on the client side portion of the application。

I'm going to make a quick note here， a little short on time for the video today。

Some of my other tutorials， you know， I like to write tests for these projects。

 but I've gone ahead and included the tests inside of this you know code solution here I'm not going have and I have time today to route the test step by step。

 but if you want to get and you want to see an example of what testing looks like for these smart contracts So you can you can just run these tests like this to check your code a truff old tests。

All right if you want to learn how to do testing， you can of course check out those other tutorials on my channel where I do testing and of course we do testing quite extensively inside the blockchain boot camp and I highly recommend that if you want an advanced testing example all right so we run the tests like trouble test like this and all the test pass so our code works。

And then now what we want to do is go ahead and revisit the clientab portion of the application and start building that out Now let's start coding the client side project so go back to your terminal and make sure that your server is running so again I've started a new server here you used to do NPm run start okay make sure you've installed your node modules and this will start the application and a new in a new window here and you can see the starter template we've got a UI framework here this is bootstrap we've got some starter code for us with the Dtorage name here a place for our address and then a blank canvas to put the body code with a little bit of text here so we can see where to edit this。



![](img/42765643d30b926b61467dd8d1f5adec_26.png)

So make sure that's running we're also going to do a few more setup steps the first thing we need to do is set up Metamask to talk to Gaache okay and so find Gaache wherever you installed it and make sure it's running it should be running already if you put the smart contract on there but anyways take this URL here there's RPC server URL this is the URL to talk to Gaache then go to Metamask and you want to change the network so。

Do custom R PC down here and pasteing the URL So I've already done this it's going to tell me。

 you know one already exists， you could give it a name Gache here if you wanted to click save all right and then go change to that network。

 so I'm click on Gache right。Allright， so make sure you're connected to Gash and you need to see your account balance listed here if you've imported your account so the next step is to do that go to Gaache。

 show your private key so you know don't do this for real in the real world don't show this to anybody else don't use this private key in the real world because anybody who uses it could still your funds so copy this go to metamask and then go to import account and then paste your private key here。

 click import so I've already done it it's gonna tell me it the duplicate so you should be able to click import all right。

And then moving there you go， you should see your account balance here。

 you have an account that's connected to the blockchain that's the whole purpose of Metamask is to turn our web browser into a blockchain browser and that's exactly what you've done。

So we're going to open up the client side application and connect it to the blockchain first。

 so that's the first step is connect your web browser into a blockchain browser and then next we're going to connect we want to convert this application into a blockchain application。

 right？

![](img/42765643d30b926b61467dd8d1f5adec_28.png)

So let's go to the client side code， I'll be the first task it's connected to the blockchain。

 I've go got to source components， all right， this is where the website lives， go to app。js。

 all right。And this is where we will connect。This is where we'll write all the code for the application and connect it to the blockchain。

So this is a react JS application， we'll get back to that in a minute。

 but the first task here is going to be to connect it to Ethereum with Web3 JS。

 so if MetaMasask connects our web browser to the blockchain。

 then web 3JS connects our application to the blockchain， so there's two steps。

 connect your browser to the blockchain and then connect your application to the blockchain。



![](img/42765643d30b926b61467dd8d1f5adec_30.png)

So there is。A very standard way of doing this， I'm going to paste in the code and show you how to do it。

 and then we'll explain everything。All right， I'm going to go to let's see here。

Let me see inside of app。js， we're going to take this configuration and put it in there。



![](img/42765643d30b926b61467dd8d1f5adec_32.png)

Okay， so we've got a bunch of we got a bunch of starter code in here that we step through a minute。

 but I'm going to go ahead and wire up the。Web3 code so we have this function called Lo web 3 this is the JavaScriptscript library for interactive Ethereum This basically just takes our connection from Madamask and puts into the application don't worry if you don't understand all this code This is literally the instructions that Madamask gives us so there's no point encoding this out step by step you can literally just copy and paste their example that's what we've done here。

And then next， we would just want to make sure that。You know， we can talk to Web3。All right。

And then we'll just console log。That log， web 3。

![](img/42765643d30b926b61467dd8d1f5adec_34.png)

All right， so save that， go back to our application， open up the console like this。

 and then boom there we go， so here's the Web3 connection all right boom done。😊。

So I just wanted to go through those steps really quickly to make sure that Meask is set up properly to make sure that our app is running and then it talks to the blockchain now let's explain some of the concepts here and some of more the codes that you can understand what's going on after you've seen this works okay。



![](img/42765643d30b926b61467dd8d1f5adec_36.png)

So here in the source directory， all the components。

 this components folder contains all the client's side code。

 so these components are react JS components。

![](img/42765643d30b926b61467dd8d1f5adec_38.png)

So we're using react to build this。Clients our website。

C reactact is just a JavaScript library for building user interfaces。



![](img/42765643d30b926b61467dd8d1f5adec_40.png)

And you can see。That it's component based so basically you organize all your code into these react components where you can mix JavaScript and HTML in the same file。

 so you can see this know class hello message is written in JavaScript but then it has some HTML code in here for you know like hello world basically and how this render function it is a very similar thing in our project you know we have an app extends component and then we have a render function down here that lay all the content out on the page you know of course with some more JavaScript inside of it。



![](img/42765643d30b926b61467dd8d1f5adec_42.png)

![](img/42765643d30b926b61467dd8d1f5adec_43.png)

We have something called react state。All right and state basically just gives us a database of sorts on our client that application。

 so here's a good example like this to do list， so if you're going to add a to do list and have like item one item2。

U all item two， you know， where are these items stored， like how did this content get updated？

We'll react has something called the state object that handles that。

 it has an array inside of here that holds all the items， you can see that right here。

And that items array is what， you know， allows us to list these items out of the page。

 and it acts like acts like a database in that sense。 Okay， so that's where。

Yeah that's what we need that's what that's what the state object does and we'll do the same thing in our application。

 basically the state object will be like the front end database for all the blockchain data inside the app okay。

So。Yeah， those the main features of reactor we're going to use are the components and the state Okay。

 so those's the main things to explain and you can see you know we've got this state object here inside our project already。

 this constructor function this is just the。

![](img/42765643d30b926b61467dd8d1f5adec_45.png)

Function that runs are other components created all right， and you can see this state in action。

 so we'll create this again。So we got a few more things。 we got a few more components here。

 We have a navbar component， which you can see here and then a main component。

 which also you know has the content for the page will fill these。

We'll fill these out as well okay so let's go back to the app and you can see the flow here basically whenever this app whenever this component loads。

 we'll have this component will mount function so this is just a lifecycle callback inside of react okay basically whenever the component is going to get added to the DOm or added to the page basically this function is going to run okay there's a special function this is a magic function from react and so we call two functions inside of here the first is load web 3 that's what this does it connects the app to the blockchain。

😊，And the second function is load blockchain data right， and that's where we did this inside of here。

 we just got the Web3 connection and lo the console。

So now we're actually going to add some more blockchain data to the page。

 we're going to get the account， we're going to get the smart contract and all that kind of stuff okay。

 so I'll load the account like this， we're going to use the Web 3 get accountscount method so let's do like this say con accounts equals let's see here。

Web3 get accounts and Wisconsin log that。All right。



![](img/42765643d30b926b61467dd8d1f5adec_47.png)

Say that go back to page and see that here。 So here's the accounts boom。 Allright。

 so now let's actually do something with this data。 let's put it on the page。

 We're going to use that react state object that I talked about a minute ago and save the account to the state so that we can fetch it back out to the page right。

😊。

![](img/42765643d30b926b61467dd8d1f5adec_49.png)

So we add the account to the state like this， we just say well instead of cons locking it。

 we say this dot set state， that's how we add new items to the three state and then we give it an object again。

 we say account equals accounts0 so remember accounts was an array here so we can just access the first account from the list with zero right this would be the account from Meask。



![](img/42765643d30b926b61467dd8d1f5adec_51.png)

And then we want to put this account here， all right？



![](img/42765643d30b926b61467dd8d1f5adec_53.png)

So we're going to do is pass it down to this navbar component all， so that's how we do right here。

 account equals this dot state the account。All right， that's and so then inside the nav bar。

 what we do is say this。That props account， okay？

![](img/42765643d30b926b61467dd8d1f5adec_55.png)

And then boom， there we go， all right。

![](img/42765643d30b926b61467dd8d1f5adec_57.png)

So now it's on the page。And yeah， so it's important to know we use this dostate dot account to assign the account all right。

 but this is something called props So if you want to pass data down to a new react component。

 we use this syntax here， this account here is called a prop。

 okay or property basically and then we can reference those properties inside of this new component navbar like this。

 so this dopros account， not this dostate account out here， it's this doprops。 account。

Because we're not using the say object， okay？

![](img/42765643d30b926b61467dd8d1f5adec_59.png)

So now we can see that on the page， that's good progress， all right。



![](img/42765643d30b926b61467dd8d1f5adec_61.png)

Excuse me。Now the next thing we want to do is configure this a little more allright we want to add a special icon to the navbar so I'm just going to copy this from the final code solution instead of coding it out step by step because it's kind of long but basically we're going use this Idents library here inside the package I JSO file to automatically generate a special user avatar for each user based on their Ethereum address it'll just do it programmatically okay。

So we'll do that with cons like this boom。So see this new idon， all right。

 which is going to create a cool picture for us。

![](img/42765643d30b926b61467dd8d1f5adec_63.png)

Which we can see here。Al right， so we yeah well issue let me just。Fix this allright。

 so its telling it can't read substream of unde definedfin。

 that's because we haven't implemented the loader yet， I believe。So I'll try ahead and fix that。

Basically， we want to create a way for our app to load， all right。So basically like u。The app。

 we won't know when the app is loading and when it's when it's actually you know。



![](img/42765643d30b926b61467dd8d1f5adec_65.png)

We want to keep track of whether it's loading and if it is loading， then we want to， u， you know。

Do certain things And if if it's not loading， then we don't learn to do certain things so you can see that already wired up。

 you could say this do state dot loading if it is loading， then show the loader if not。

 then you never to the page so let's fix that all right so say。呃。Loading goes false。Okay。

 so let's see if that fixes it， I think it might not actually or actually loading is true。ok。

And then whenever this is done。Sre。

![](img/42765643d30b926b61467dd8d1f5adec_67.png)

Let's try this。All right， so I let didn't fix it so let me let me just fix it real fast I think I think it's something else actually all right。

 it looks like this little issue here so I'm going to fix this say this do prop do count。



![](img/42765643d30b926b61467dd8d1f5adec_69.png)

We'll use this and we'll see if it exists， then we'll do this and if not， then we'll do this。



![](img/42765643d30b926b61467dd8d1f5adec_71.png)

just save the x0。So you see if that fixes it。

![](img/42765643d30b926b61467dd8d1f5adec_73.png)

All right， so let's look at a problem here。Let's try like this。Oops， someone。

So this is not the best way to write this， of course， but this will fix the problem。All right。

 so let's just save that for now。

![](img/42765643d30b926b61467dd8d1f5adec_75.png)

All right， boom there we go， so this is nice。It abbreviates the。

Abbreviates to the address as't look really big on the page like that All right。

 so that should fix the problem， al right。

![](img/42765643d30b926b61467dd8d1f5adec_77.png)

So now let's go back and continue on coding out the application， all right。

 so let's go back to AptI JS and continue filling this out。😊。

So next thing we want going to do is actually get a copy of the smart contract that we just created from the blockchain and we want to。

Added to the project like this。I'm going to go over。

 I'm just going to do the code from the final code solution so don't save some time here and I'll explain it。

 so we'll just go ahead and fill the rest of this out like this。Basically do this。Take this in here。

 okay。Because I want to get to the IPFS park， that's the really important part of the tutorial。

So what we do here is first get the network ID all right so every Ethereum based network has an ID Gaache here has an ID of 5777 right and so we want to do is basically create a JavaScript version of the D stward smart contract that we created in the previous section okay so with web 3 we can do like this web 3 Eth contract okay and so we can create a new web3 contract like this we say a new web3 Eth contract and we need two pieces of information information piece number one is the JSON interface so this is the ABI it' basically just a JSON description of how the smart contract works。

 the functions it has and all that kind of stuff the next is the address。

 the location of the smart contract in the blockchain。



![](img/42765643d30b926b61467dd8d1f5adec_79.png)

![](img/42765643d30b926b61467dd8d1f5adec_80.png)

![](img/42765643d30b926b61467dd8d1f5adec_81.png)

![](img/42765643d30b926b61467dd8d1f5adec_82.png)

We get that information like this so we see a new Web3 Eth contract so the D storage AB comes from this file。

 so if you go to source ABs D storage， you can see it right here， all right。

 so that's piece number one， it goes here and the next is the network data the address okay。

 so you can see the address here 5777。Okay， let me just find it。You can see the address here， okay。

 boom， there it is。One important thing to note is that this smart contract could be deployed to multiple networks。

 it could be deployed to Gash， the Ethereum mainnet， a test network， etc cetera， etc ce。

 and the address will probably change every time that happens So Truffle stores these addresses under each individual network ID so here's Gaash 5777 here's the specific address forganache and so that's what we do here Basically we fetch the network ID that we're connected to inside Meammask we get the network ID or sorry right here。

We had38 get an NI all right and then we basically get this network data right here。

 okay that's what networks is。D storage networks and then we pass in this network ID57 77 from Gash and then basically if that exists。

 then we create a new JavaScript version of the smart contract like this and if it doesn't exist it'll say hey。

 you know this smart contract doesn't live on this network so here's an example we can just go to metaaskask and。



![](img/42765643d30b926b61467dd8d1f5adec_84.png)

![](img/42765643d30b926b61467dd8d1f5adec_85.png)

Change networks， but first it looks like D storage isn't imported， so at the top of the file。

 make sure you import like this， boom， import D storage okay。



![](img/42765643d30b926b61467dd8d1f5adec_87.png)

So here we go， and then we can meta a mask， we can go to。Lets just go to like mainnet。

Refresh the page and it'll say boom， D storage contract not deployed to detect a network okay。



![](img/42765643d30b926b61467dd8d1f5adec_89.png)

So we can see that here， you know， it didn't have this network data， so it gave us this alert。

 all right。

![](img/42765643d30b926b61467dd8d1f5adec_91.png)

And so that's working and now we can just change back to or sorry， change back to Gache okay。



![](img/42765643d30b926b61467dd8d1f5adec_93.png)

So boom， there we go。Alright。So then we set that to the state。

 so let's go ahead and update the state object as well we can just basically。

Update this date from the final code solution like this。Okay。And then。Yeah that's how it'll work。

 and then we can say we get the files counts， this is the number of files that runs up the app al right。

 we say D storage。 methods file count， it's how we interact it in JavaScript we say call to get it back more with the GS。

And then say this states at files count。And then now we want to load all of the files from the smart countries like this。

 we use a for loop in JavaScript。We basically get the files count。We start with that。

And then we count backwards， so we start off with the latest ID and then subtract each one。

 all right。And then we just get all the files。And then set the file like this， okay？



![](img/42765643d30b926b61467dd8d1f5adec_95.png)

So I'll save that， go back to the page， make sure everything works properly， and boom， there we go。

 we're good。

![](img/42765643d30b926b61467dd8d1f5adec_97.png)

All right。So now。We want to。Actually wire up the application to store files onto IPFS so that'll be the next step because remember。

 you know we do this， it's a multistep process， we add the file to IBFS then once we get it back we get this hash and then we add that to the smart contract here。



![](img/42765643d30b926b61467dd8d1f5adec_99.png)

![](img/42765643d30b926b61467dd8d1f5adec_100.png)

Okay， so。We're going to create a we need to first create a connection to IPFs like this。

 so I'll put this at the top of the file it's pretty simple。

 we use the IPFS client from our package JSO file all right。

 and then we connect it to a free infea client like this the host is IPFS。 Fuda IO， we use Portf 01。

 we use the HTTP protocol。sorrytTPS has protocol。😊。

So now we have an IPFS object instead our app that we can call， we can say like upload， you know。

 add， all that kind of stuff， you know， you know， read so。I'll show you how that works momentarily。

So let's go ahead and create a way to upload files。

So we're going to do this inside the main component， all right， so inside of main。js。

 we'll modify this all right。So inside of here。We will use a basic form that allow us to upload a file know from from our computer and then put an IFS and that's what we'll do right here。

 So I'm going to take the form from the final code solution and put it here So this D storagege starter code we're going to take this out and then take out these two commented lines Okay。

 so like boom take this out and then add this boom allright， so here's the div allright。

 that's going to contain the form。So everything inside of here is going to be the form for uploading the files we can save that and go back to our page and see it boom all right。

 so here's the share file section， you know we it's going to basically allow us to choose a file。

 add a description， like in a food bar。

![](img/42765643d30b926b61467dd8d1f5adec_102.png)

And then upload it for our Dropbox， okay， so let's go ahead and do that。



![](img/42765643d30b926b61467dd8d1f5adec_104.png)

Well we can't do it yet， because don I haven't wired up， let's wire up the part that lets us do that。



![](img/42765643d30b926b61467dd8d1f5adec_106.png)

So let's look at what this does。 So uploading of files may be to， is's really a three step process。

 Okay， so I'm going put those steps down here。So step one。Pros file。Or you can say prepare file。

For upload。Step 2。Upload。File to IPFS。And step three will be。Let's say store on blockchain。

We've already kind of talked about step two and three where we publish the file IPFS。

 we get back this hash and then we store this hash on the blockchain so we can read it later， but。

Basically u。There's a preliminary step， which is that we prepare the file and convert it to a very specific file format so that it can be actually uploaded to IPFS so that's what we want to do here。



![](img/42765643d30b926b61467dd8d1f5adec_108.png)

You can see this line here， So input， this is the file form input。 we have this onchan handler。

 So this is called this props capture file， So this is going be a function that we're going to code out here in a second。

 What this is going to do is convert the file to something called a buffer that will allow it to be uploaded to IFS。

 So we'll do that inside the main appjs file right here。So。That's's what we'll do in capture file。

 okay？So instead of capture file， we'll do this， all right。So。I'll show you。

So first we prevent the default behavior of the form。

 we don't to submit and refresh the page or anything like that。

 so we first say con file that we basically are going to get the file from the form field okay。

And then we use the native file reader from the JavaScript window object。

And then we convert it to a buffer all right， so you can see what that looks like right here all right we capture file we pass it down here and then basically whenever we upload a file。

 it's going to capture it and convert it to this buffer object and log it to the console so you'll see what that looks like。



![](img/42765643d30b926b61467dd8d1f5adec_110.png)

So I'm going to actually upload a file screen， I don't want to reveal my file contents here so I'll it off screen。

Let me just find a quick file。I'm going to yeah， let's do this， this works。

This is a screenshot of my tutorial right now。So here's the file and you can see once I've uploaded it。

 you can see this log to the cons here。 This is this a buffer array。 Okay。

 and basically this is just how this is the format that we need the file in ja in order to put an IFS。

 So that's what this first step is is it processes the it processes the files。

 that's this prepare file for upload， we just did that。 So basically whenever we。



![](img/42765643d30b926b61467dd8d1f5adec_112.png)

Upload a file wherever we add a file with this file field， it calls on change。

 which calls this capture file and then this capture file does this code to convert it to a buffer right and we loggged into the console。



![](img/42765643d30b926b61467dd8d1f5adec_114.png)

So now we want to do the next step， which is upload to IPFS。



![](img/42765643d30b926b61467dd8d1f5adec_116.png)

All right， so we're going to do that on the form submission mission。Okay。

 so you can see the on submits handler， I'm sorry it' the na bar。On submit handler。

 so form on submitm， we say Prevent default， we capture the file description and then we upload the file with this props the upload file function。

 all right。So that's going to be this right here。This special function that we're going to code out step by step。

 which is also passed in here， all right？So， you know， step one。Or step  two， I guess。

 step one of this section， but step two overall is now take this file that we've captured in upload IFS。

 so we'll do it like this。

![](img/42765643d30b926b61467dd8d1f5adec_118.png)

![](img/42765643d30b926b61467dd8d1f5adec_119.png)

Well， first stay。Smitting F to IPFS and then we take our IPFS connection from up here all right。

 and then we just call。IPF to add。And say this， that state， that buffer， which we created here。

 right， and then we say， you know， error。Results。And then you can say console。 log。呃。Let's see here。

 IPFs。Results。Say results。Size， okay？

![](img/42765643d30b926b61467dd8d1f5adec_121.png)

All right， so let's log this up to the console here， I'll go back to the terminal or sorry。

 the window and I'm going to upload this off screen。😊，Choose file。

 I'm going to do is just a screenshot of my whiteboard here。And then， you know。

 we can see that it was it was converted to an array buffer here， click upload， okay。

 let's do a description， let's say food bar。Upload。We can say it submitting F IFS。

 and then here's IFS results。 So it worked， but it looks like we didn't actually。



![](img/42765643d30b926b61467dd8d1f5adec_123.png)

It's like we didn't properly return this， let's just make sure。Oops。LetJust make sure this was right。

So we don't actually want to do result size， want to do results， sorry。



![](img/42765643d30b926b61467dd8d1f5adec_125.png)

Start again， Ubar， choose a file of screens， that that code was wrong。Fix it。All right。

 let's try this， click upload。Somethinging I pross all right， boom， there we go。 Here's our result。

 Alright， yeah， we can see it。 Yeah， here we go。 Here's the path。 Al right， here's the hash。 A。

 alright， so you can see it worked。 And here's the hash on IF S so。😊，Like I said here， step once。

 prepare the file next is upload to IPFS and we get a hashback just like this。

 so here's our actual IPFS hash that we got， take out the quotation marks。

 you know we can go view this on in our web browser。So I can say， like， you know， if you're an IPFS。

Let me just actually get the URL。Let me look here。嗯。Let's see here。We can preview it in our browser。

So I can go here and in my URL bar do this and you know IPFs I'm here to IO forward slash IPFs and then paste in the hash。

And then the moment of truth boom there we go there's our file that I just uploaded so you know here's the hash that we got back and then we can just use the IPFS gateway to view it and I just took a screenshot on my whiteboard and you know saved it so I could upload it and there it is awesome。

So that's step one and two， step one is to prepare the file for upload。

 step two is to upload it to IPFS， which we've done now step three so store it on the blockchain。

 all right。So。Inside of the。

![](img/42765643d30b926b61467dd8d1f5adec_127.png)

You know， at JS file， we're going to do that next step。

 which is put on the blockchain we're going to use。呃。Well， first， we'll do a little more code。Um。

 basically if there's any， it's just some error handling if there's any errors here。

We're going to return。Um， if there is， uh， we'll make sures there's loading。

 we want say loading to true。And then next。We want to set the file type here。Alright。

I it the file type like this。Okay。And then next， we're actually going to upload it to the blockchain。

U。With Web 3 like this。Se a bone。So this would be this stateD storage method so upload file。

 this is the bulk of step three， so we get the hashback from myFS， we give it the size of the file。

 the type， all right， the name， the description call send from this state。 account all right。

 and then whenever that's finished on transaction hash， we set the loading state to false all right。

 all that kind of stuff so save that。Clear out all this code。Go back to the application here。



![](img/42765643d30b926b61467dd8d1f5adec_129.png)

Let's find it， I think mine actually disappeared。So I'll put it back here。I refresh。

upload my file off screen and we'll just call it my screenshot all right I'll click upload and submit it to IBFS and boom here we go so now we have to actually you know sign this transaction to put it on the blockchain so we pay for this pay this small fee inside Metamas to store it you know with Ethereum click confirm。

All right， and then we've got an error， so let's just fix that。So。

I got a little issue my metatamass you know failed so let's just do this I'm going reset my account metatamass and sometimes this happens sometimes if you get you see this error and you just need to reset your account like you restart a notch or something I actually want to leave this on screen so you guys can see how this works。

So basically let me just remember how it works to count details。

 actually it's the settings I believe so if you go to your account icon up here and then go to let's see your settings。

 you can go to advanced。And then reset account， All right。

 so this won't mess up anything and it'll just reset your transaction history on metaask click reset。

All right， so that's done， let's refresh the page and we' going to try to upload one more time。😊。

So we'll say here's a screenshot。Same my screenshot。All right， pull this back over here。

Click upload and let's see if it works， confirm。And boom， there we go， awesome success。

So now it worked， it's submitted to the blockchain。

 but we can't see any of our files on the page that's going to be the last step we want to list out all the files。

You know， from from the smart contract onto the page。

 so we've already loaded all the files into the app like this load files and sort by the newest right here。

 here's this step all right， let we save them to this right here。



![](img/42765643d30b926b61467dd8d1f5adec_131.png)

So last thing I'm going to do is put them inside here。

 we're going to do with a table and we're going to map over all the items in that table and put them on the page。

 so we've also patch the files down here so this files is here so we can just access you know Vta props inside of here So basically what I'm going to do is just take out this table。

I'm going to add the code from the final solution like this。So we just collapsed this。All right。

 put it in here， opens of table。So this is an HTML table all right。

 and then we have table header and table rows， so basically we just have the ID， the name。

 the description type size date， you know uploader viewer and then the IPFS hash and we do is take this do prop do files we map over each of them and we have the file and the key and we create a new table row for each file so we just you know load loop through all these and then give give the data so here's here's each row for those okay。

So let's click save and take a look。

![](img/42765643d30b926b61467dd8d1f5adec_133.png)

All right boom there we go all right so here is our here's our file okay and so we can click on this and this would be like the share link so its how Dropbox works you know you can see you can store your files here and you can see the file name。

 you can see the description you know the type size so you can build an entire file store system like this and the whole idea is a social app a sharing app so you can say you know hey I want to send you a file over a text message or something like that。



![](img/42765643d30b926b61467dd8d1f5adec_135.png)

Then you can click that share URL， you could just copy this link and then send it to somebody of our text message over an email if you have some sort of decentralized chat system or maybe like an encrypted chat network like telegram。

 for example， like a secret chat， you know you could have no trace of your communication and you know store。

 you know send a IPFS file like that， it's pretty cool。



![](img/42765643d30b926b61467dd8d1f5adec_137.png)

So we can just， you know， battle test this and add some more files。

 I'm going to choose another one here。 Let me see if see if back can picks like。U。Let's do this。Okay。

 did another image。So we'll see like。Juicy swap， is a this is an app that I built， all right？

It's a picture of an app that I built。Click save and then boom there we go。

 automatically as of the page and we can see the hash here。Okay。All right， boom， very cool， awesome。

Yeah all right there you go so there's your completed application this is your Dropbox clone with blockchain so congratulations especially if this is your first time you know building a decentralized application。

 you've come a long way， you know've you've used the blockchain。

 you've created a smart contract you've created a react based application that uses IPFS to create this you know unstoppable censorship resistant DAP right for storing files so you can go you can take this application and and build on it。

You can make add more features to it。So yeah， I hope you like this video again the final code solution is always here on Github so if you want to check any of those。

something doesn't work for you in the tutorial you can go check this link and if you like this video and you want to take the next step。

 you know what should you do well first you should smash the like button down below subscribe this channel that really helps these videos out so that more people can find them you spend a lot of time making these tutorials for you all that's always appreciated and then of course if if you like this。

 you want to take the next step， learn how to build a realworld blockchaincha application decentralized cryryptocurrency exchange so that you can land a high paying job。

 become a freelancer build your own project then you can I can show you to do that over at Dyversionion。

com bootc， just click the link right here。Sign up today and I'll show you how to do that step by step right。

 so that's all I've got for today until next time， thanks for watching Dappy diversity。



![](img/42765643d30b926b61467dd8d1f5adec_139.png)