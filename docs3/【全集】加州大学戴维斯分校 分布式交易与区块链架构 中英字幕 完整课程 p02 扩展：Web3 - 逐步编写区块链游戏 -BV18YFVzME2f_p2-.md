# 【全集】加州大学戴维斯分校 分布式交易与区块链架构 中英字幕 完整课程 p02 扩展：Web3 - 逐步编写区块链游戏 -BV18YFVzME2f_p2-

Todayy I'm going show you how to create your own blockchain game and I'm super excited because this is the first time I've ever done a gaming tutorial on my channel but right now is the perfect time because blockchain gaming is really starting to take off and I'm gonna show you how to jump on that trend and create your own game today I'll show you everything step by step how to createthereum smart contracts the programming language how to write tests for them put them on a and also how to create a clientside app that will let users play the game and interact with your smart contracts but don't worry you don't have to be an experienced programmer or really know anything about blockchain to get started today I'll show you everything step by step So before we get into that if you're around herey I'm Gregory and on this channel I turn you into a master So if that's something that you're interested smash the like button below YouTube and subscribe and if you want to learn how to master step by from start to finish and heading over toyverse cant to get started today Here's a demo of the app that we're gonna build today This is a blockchainbased memory game where you try to find match。



![](img/84667de9984b90e1ba962183151f4b9e_1.png)

And as soon as you find the matches， you get to keep them forever on the blockchain That's because each of these tiles is represented by a blockchainbased token。

 So whenever you find the tokens and you match them。

 you get to keep them in your wallet and then these tokens can be transferred outside of the game because they live forever on the blockchain and you can sell them on a marketplace keep them as collectibles whatever this app is inspired by a tutorial by Anyao who's another ja to YouTube so full credit to her for originally making this tutorial I'll put a link to her channel down in the description below but I've taken this and adapted it for blockchain and also for modern web development with react JS Here's a quick diagram of how the application is going work we're gonna build first and foremost we're going use our web browser and talk to a client side website This is where most of the logic for the memory game is going live we're going write this game in ja and we're gonna do it and react JS and then when we match the tokens in the memory game we actually create new tokens on the blockchain that's where the tokens are going get saved。

Whenever we find them and these tokens are powered by Ethereum smart contracts。

 which is going to act like the business logic for transferring the tokens and you governing the token ownership and then the ledger of people who own the tokens are going live on the blockchain as well It's gonna to act like our backend database in this tutorial and then of course once that are on the public ledger of the blockchain they can be sent to any other blockchain wallet sold at a marketplace etc etc really quickly let's talk about the tokens in this tutorial So the kind of token that we're gonna build step by step is not a money it's it's different called a nonfungible token so you might have heard about this with digital collectibles like crypto kitties for example this is a really popular topic in the blockchain space right now so that's what the tokens are going to be in our tutorial that can mean memory tokens that are collectibles that we win by playing this blockchainbased game and then we can hold on these tokens collect them sell them whatever let me further explain this difference so that it makes sense So the token we're creating as a nonfunggible token and that's different from a fungible token。

So you might think of fungible tokens like cryptocurrencies。

 so these are examples of you know tokens that represent money， so let's take a token， for example。

 let's just see like the uni swap token uni。Every uni token is worth the same as every other uni token。

 you can swap one uni token for a different uni token and it's worth the exact same that's what a fungible token is。

And this works really well for money so nonfunggible tokens mean that tokens aren't necessarily worth the same so each token is unique these tokens are not unique these tokens are unique that's why they work as collectibles so for an example you know one token might become rare and therefore worth more than another token and that's an example of nonfungible tokens and that's exactly the type of token that were going to create this video so we're going to use the ERRC721 standard you might have heard of the ERRC20 standard for Ethereum based tokens that's what these are these are all ERRC 20 tokens well ERRC 721 is just the standard for non-fungible tokens so it basically just describes the types of functions and events that a token must implement again this is just an Ethereum smart contract written in the programming language and this is the description of you know the types of solidity functions have to exist like balance of to see how many tokens the individual owns the owner of each token。



![](img/84667de9984b90e1ba962183151f4b9e_3.png)

![](img/84667de9984b90e1ba962183151f4b9e_4.png)

The ability to send tokens like transfer from the ability to approve tokens for other people to send them we're gonna get into all those details in this video。

 but that's a really quick overview of what the ERRC 721 standard is because that's what we're going to build in this video Now let's install the dependencies beneath for this tutorial The first dependency is node Js This is gonna allow us to install all the packages on our computer as well as run our client side application so you can see if we have node already install by going to your terminal and typing nodev so I'm using node 9。

10。0 I would recommend using the exact same version for best results during the tutorial but you can probably use the latest version if you really want to and you know what you're doing so you can download node directly from the website or you can use a command line tool like Homebw a package manager to install it that way The next dependency is the truffle framework This is a framework for creating Ethereum smart contracts we can write Ethereum smart contracts with the solidity programming language write tests against them and deploy them to a blockchain with truffle as well as many other things which we'll see。



![](img/84667de9984b90e1ba962183151f4b9e_6.png)

![](img/84667de9984b90e1ba962183151f4b9e_7.png)

![](img/84667de9984b90e1ba962183151f4b9e_8.png)

utial you can install truffle from your command line like this。

 say NPpm install a G truffle at version 5。1。39 The next dependency is theganache personal blockchain This is a blockchain that run on our computer we can simply download it and run transactions in the blockchain deploy smart contracts to it without having to pay any real money so go ahead and download Gash can just click the version for your operating system here and whenever it's finished downloading you can open it and you'll see that you have a brand new blockchain running in a computer just like this you'll see lots of different accounts funded with 100 fake ether and don't get too excited because this isn't actually worth anything The last dependency is the metamask extension for Google Chrome Most modern web browsers won't connect to the blockchain out of the box and so we need to install a special browser extension to do that that's exactly what metamask does it's an Ethereum wallet that turns our browser into a blockchain browser so go to the Google Chrome web store find metamask and click install and。



![](img/84667de9984b90e1ba962183151f4b9e_10.png)

Once you have it installed， you should see a f icon in the top right hand corner and just walk through the setup steps to get that started。

 All right now let's start building the project So instead of building out everything from scratch in the beginning I'm going help us get started fast so I've put a link down in the description below to a Github repository this is gonna let us get the starter code for the app so we can get moving so type this into your terminal say get cloneer this is a specific branch on this repository here's repository link Githubdi block game and finally put a space after that and call the folder blockchain under short game so don't worry if you understand everything about this I'll put this command done in the description below。



![](img/84667de9984b90e1ba962183151f4b9e_12.png)

But just click enter and you'll see what happens， all right。

So I'll enter into the newly created directory like this， say CD blockchain game。

Allright and you'll see the branch starter code so if you want to change to the master branch you can。

 but I'll just start in the starter code branch like this So next we want to install all the dependencies we'll just say NPpm install wait for that to finish。

All right so it's done and you might see some warnings here don't worry about that as long as your package is actually installed。

 that's all we really care about this point。 it's not ideal。

 but that's just the state of things So let's clear that out and then I'm going to open this in a new tab here okay so I've got two tabs in my terminal and the second one I'm going to start the server we'll do it like this let's saympm Run start This is just a server for the client side application again the rest of it's going to be on the blockchain So this is my old version let's just see if this loads up here。



![](img/84667de9984b90e1ba962183151f4b9e_14.png)

Al right， there we go。 That's what you should see。 So here's the basic template for the app again。

 you can see that it just says edit this in appjs so we're gonna fill this out in the tutorial so there's no game here but this just has some basic UI ready for so we have to build this stuff from scratch has a nav bar up here with this memory tokens title nice little icon and then a place for our Ethereum address here and then this is where we'll actually build the game all the interactivity and we'll collect the tokens at the bottom and we'll do that later in the tutorial So I just wanted to run the server really quickly to make sure that everything was set up properly so let's just continue on with that let's just set the project up so that we can build it out for real。

😊，So the next thing we want to do is startganache。So this is our local blockchain and we want this running so that we can you know deploy smart contracts to it and all that kind of stuff before we start building everything out。

 So we'll just create a smoke test to ensure that everything work so let's go ahead and open this project in our text editor so I'm going open mine sublime text you can use whatever text editor you want to people ask me about that a lot what does that subbble dot command mean well basically that's just how I open my projects in sublime text it's a quick shortcut from my terminal don't worry if you can't do that you can always just navigate to your file browser and open it manually that way if you want to so we can see inside of here that。



![](img/84667de9984b90e1ba962183151f4b9e_16.png)

![](img/84667de9984b90e1ba962183151f4b9e_17.png)

We have a truffle dash config file， this is what configures our project to talk to the blockchain。

 so here's our connection to Gaache right here。And then if you've used shffle before you might notice that I set my projects up a little bit differently。

 I put the contracts in a different directory so they can be exposed to react JS for these tutorials so that's the configuration here if you're brand new don't worry about that but if you've been around truffle for a while that's why I do this okay and so let's keep looking at the project here。

So next let's just look at the source directory， all right。

 there's lots of different files in here and directories， so the first is the contract directory。

This is where the smart contracts will go， so we already have a memory token。

 smart contract set up for us， this is where we'll write all the code for the token。

 and we'll build this out here in a minute。We have a test directory where we're going write tests for this smart contract and we already have a basic test skeleton set up here as well we'll out the code for this in the tutorial and then last but not least you know we have the client side directory so this is where the components go。

For react Js again reacts the componentbased library we'll dig into all of that in this tutorial。

 but we have the basic you know markup for the front end that you see inside of here and of course we'll fill out this code in the tutorial and also create a lot more in here as well so let's start off with the token all right so this is where we're gonna create the ERRC 721 token for you know the memory tokens that we're gonna to collect during this game So we'll build this out you know in the tutorial but first let's just create a basic test to ensure that we can deploy the smart contract to the blockchain that everything's set up properly and so let's do a couple things here so first I want to take out this right so this is you know part of this different smart contract that we're going inherit from later in the tutorial don't worry about that just yet just know that we don't want to deploy it with that on there yet。

So basicallyically we want to say we gonna to give a contract a name this is the second thing So we'll say string public name equals memory token right so what we've just done here is created a variable inside the smart contract this is called a state variable which basically means that it belongs to the entire smart contract not just a function and it is stored on the blockchain so it's gonna be in im mutable variable value means the variable value can't change because on the blockchain and it's with a smart contract so it's just going be a string name memory token and so that's what this means here because validity is a statically typed programming language which means that whenever you declare the data type you must do it like this and then it can't change it can't be something else it's also public which means we can read this value outside the smart contract which we'll see in a minute and then it just has this name here so we'll just save that and we'll deploy it to the blockchain and we'll try to read the value So the next thing we need to do is tell truffle how to put this on the。

blockchain so we'll open this migration file so go to the migrations directory look at migration number two。

 This is called deploy contracts So this is just gonna be a file that tells truffle how to move the contract onto the blockchain that's what a migration is so you might be familiar with migration from another programming background if you're a program already maybe like a web developer or a mobile developer anything that works with the database you know you have to migrate a database you basically are changing it that's what a migration is and moves it from one state to another or maybe you're moving data from one place to another you can think about a migration that way as well that's what this does so we can put the smart contract in the blockchain like this we'll go to this initial migrations file will just copy this。

paste it inside of here and instead of deploy migrations we'll deploy memory token so that's what this is here。

 This is just importing the memory token artifact into this file the artifacts what truffle uses whenever it you know compiles the smart contract it creates an artifact so that it knows how to work with it in ja we'll see that in action more later so we just do deploy deploy memory token to save that and then also while I'm here I'll note that the migrations are numbered so that truffle knows what orders run to run them in so the initial migration is number one and then deploy contracts is number two because they must be run in that order right so let's go to the terminal and deploy this we'll say truffle。

Migrate dash dash reset。All right， I'm going to do reset for now in case you have any other smart contracts that exist in your build directory。

 I pretty much always do the reset flag for local development like this。

Basically understand that smart contracts are immutable。

 like they can't change and so if you update the code to them when you're developing them。

 you have to put new copies on the blockchain and that's what I do whenever I do the reset flag。

So we'll run truffle migrate dash dash reset to put this on the blockchain and let's just see if it works let's compiling all right all right and boom there we go it's put memory token on the blockchain so now let's open the truffle console to interact with it all right we'll say truffle console。

So now we have a JavaScript console where we can interact with the blockchain directly。

 which is pretty cool okay。So I can actually fetch the smart contract with JavaScript inside this console and we can read that variable value name。

 so I'll say like hm'll say name or so contract or token， token equals weight， memory token。

Dot deployed， all right。So I'm using a weight here because this is an asynchronous function I talked about that a lot in my other tutorials but basically you know the interactions with the blockchain are asynchronous and so if you want to get the value of this you must use the await keyword because like you know just token if you did this then it would only return the promise not the actual token itself it's kind of confusing if you want a deeper explanation that just go look up how promises work in JavaScript and also how aso weight works so anyways you'll see token here it'll say undefined that's just the logged value that's not the return value so you can say token all right boom and there it is boom all right so token address all right so it was deployedport the blockchain boom done and then token name so we'll say name equals a await token。

 name and then call the function with the parentheses。All right， and so it'll say undefined again。

 that's just the logged value， it's not the actual return value， click name and then boom。

 there we go， memory token， awesome。So we have successfully put a smart contract on the blockchain It is a very simple smart contract that doesn't do very much but now you have you know do you guarantee that everything works properly you've set up a blockchain you've put a smart contract on it you've written a little bit of solidity programming language so you know you've taken some concrete steps to becoming a blockchain developer and building your blockchain game so congratulations that's really the first step so let's continue on that Alex the console like this to say dot exit clear this out and we want to keep building out the smart contract but we're gonna to do is actually write some tests for it so we don't want to boot up the console every single time to see if our code is correct we want to use test drivenn development and not really test driven development we want to write test along with the code I think test drivens probably too hard for most people who are just starting out programming and just like learning blockchain we want some sort of test coverage though to make sure that actually works so we won to be hardcore test driven but we will write some。

right it will make things more efficient and speed things up So what we're gonna do is we're not gonna write actually too much solidity code in this tutorial because we can get a lot of this for free by using the open Zeeppelin library let me explain why So let me just pull it up here say open Zeepellin ERRC 721 So a lot of these tokens are basically like solved problems So for example if you want to create an ERRC 721 token there's no need to really reinvent the wheel Now that being said if you're just learning programming from the very first it can be helpful to like reinvent the wheel to learn things and I actually teach you how to do that and some of my other tutorials I teach you like how to build a cryptocurrency from scratch I teach that inside the blockchain boot camp because sometimes like when you're just starting out it really helps to build things from scratch to get a deeper understanding even if you are reinventing the wheel sometimes that can be helpful for。



![](img/84667de9984b90e1ba962183151f4b9e_19.png)

But the scope of this tutorial is really just to show you how to make a game and how to use tokens so you if you want to build tokens step by step。

 you can check out those other tutorials to do that deeply。

 but for this tutorial we're going to use a template from ER sorry from Open Zeeppeplan because they have a standard interface and implementation for writing ERRC 721 tokens these are the collectible tokens on their Gitthub so basically。

We can just use this， see ERRC 721。And they basically have a lot of the functions created already because remember it's just a standard token it works supposed to work the same way for pretty much everybody here's the specification here and they basically already implemented the standard for us all we have to do is inherit from it in our smart contract and we get all that functionality for free so I've already included the ERRC721 full standard inside of here so I did this because I didn't want any conflicts with the open Zepellin version I wanted you to be able to follow tutorial pretty easily I didn't want to import it from the NPM package or anything like that I wanted to just put it in our project so you had easy access so it's already wired up for you all you need to do now is you know put this line back in there。



![](img/84667de9984b90e1ba962183151f4b9e_21.png)

So basically we say memory token is ERRC721 full so this is how you do inheritance and solidity。

 this is the smart contract we're going inherit from this is the ERRC 721 full here all right and of course this inherits from every other you know contract inside of here so and then we import you know the file right here say dot is the current directory and then here's the file name and then we inherit here all right so let's just take this out and start over。

And we can actually set the name a different way， so you can see that this ERRC721 has a constructor here。

 so this constructor is just the function that gets run whenever the smart contract is created or put on the blockchain。

And it has some values we can pass in， so it actually takes a name。

 so string memory name and then string memory symbol because u tokens all have names and symbols so they can be traded on you know marketplaces so that。

 you know while's understand how they work。So we can implement this constructor into our smart contract like this。

 okay， we just say constructor keyword， constructor。

And then this is how we tell it that we want to give the ERRC 721 full arguments。

 and I'm just going copy this and paste it here， and then we give it this name and symbol that's required here。

 so names a string and symbols a string。And we just say memory token。And then we say memory。Nanmo。

 that way the symbol， okay？And this constructor must be public all right。

 and then it's just going to be an empty function， we don't actually have to implement any logic inside the constructor。

 we just have to implement the constructor for this ERRC 721 full here。Okay。

 so let's just start off with that it's a really basic implementation we've given it a name and a symbol a lot like this state variable name here that we read out in the console we just assigned the name this way because that's what the。

The template asks for and if you want to browse this you know you can look for name so you can see this is the name function here inside of the ERRC720 metadata it actually implements a variable here a private variable actually called name and a private variable book called symbol but they expose public functions that read these values okay yeah that's that's how it works but we're gonna write a test for this so tests are just automated test that allow us to check the behavior of the smart contract it's like what we did in the console but it does it automatically。

Inside JavaScript with trule， so go to your test directory and find this memory token。t。

js file and this is where we'll write all the code for the test so of course I have cleared out a lot of this stuff but。

You know， I have some boilerplate code in here so that you don't have to buy all this yourself。

Basically what it does is it uses memory token， right it imports it just like we did the migration。

 it creates some configuration for the test， and then it uses this contract function to create the test suite。



![](img/84667de9984b90e1ba962183151f4b9e_23.png)

So really quickly， we're going to use the MoOCA testing framework and the ChaHI assertion library。

So MoOcha testing framework comes bundled with truffle okay so it's a JavaScript testing framework where we can write tests for the smart contracts。

 MoOCA is a pretty popular framework， like I said comes a truffle and then we're also going to use the ChaI assertion library so ChaI basically just can allow us to have these matches in our tests like should you know expect assert all that kind of stuff so those are the two main things that we're going to use to write the tests and you'll see that in action as we go along here。



![](img/84667de9984b90e1ba962183151f4b9e_25.png)

![](img/84667de9984b90e1ba962183151f4b9e_26.png)

![](img/84667de9984b90e1ba962183151f4b9e_27.png)

![](img/84667de9984b90e1ba962183151f4b9e_28.png)

![](img/84667de9984b90e1ba962183151f4b9e_29.png)

So inside the test， the first thing we want to do is let's just create the basic one， right？

Let's just say， let's why I test example like this because they describe。Deployment， all right。

 and then I'm going to use an async function。All right， and then inside of fear， we'll say it。

Deploys successfully。And then we'll say async。So again。

 I'm using these async functions because we're going to be using the blockchain and we want to use the await weight keyword to fetch things。

So the first thing I want to do is basically like declare the token here say let token。All right。

 this is just going to be a variable that we can assign the token to when we fetch it back from the blockchain just like we did in the console okay。

 and then I'm going to write this exact same code that we did in the console so let's say like say token equals oh wait memory token deployed again this is just what we did a few minutes ago in the console so we store the value here。

And then we want to check the address all right， this is we also do this in the console。

 let's just see this。All right， Con address equals token address。

 and then we would just want to make sure that it exists and that's not blank so we'll do this。

 all right。So say assert。That's what we do to check the validity in the test to say assert do not equalal you know address。

 we don't want to be the blank address， we don't want it to be an empty string。

 we don't want it to be null， we don't want it to be undefined that's because we want to check that it's present but we don't know what the address is going to be because you know every time we put a new smart contract in the blockchain the address changes so we just want to make sure it exists right。

So let's run to test like this if it tru tests and this will， yeah。

'll it'll put it on the network and then check the address， right， make sure it runs。

Hopefully this have errors and boom there we go it passes awesome So if you've never written a test before。

 that's what it does。 you just see this output here and you can see the name of our test。

 know contractors memory token this is the deployment and we say that yes it deploy successfully based upon the rules that we described in here we say assert that's saying you know ensure or know make sure that this happens。

 make sure that the address is not equal this， make sure the address is not equal this， cea， ettera。

 you could change this something else and watch it fail and you could make it turn green the whole testing philosophy is like red green refactor it's not exactly what we're doing here but we are adding test coverage next let's check for the name but first let's。

Do this so we want to fetch this memory token before we write more tests well let me just show you we can add a new test for the name like this。

 we can say like you know it。Has a name。All right， and then we say async。

Like this and say Kant's name equals08 token。 name all right， and then we can say assert equal。

 yeah name and then say memory token。Just like we'd created in the contract but。

It's not going to know what the token is because we defined token here inside this test。

 so we want the token to be， you know， let me just show you a better way to do this it's not necessarily true for this one。

 whatever we write more tests it's not going to know。So let's do this。

 let's say before aync basically were going create a before block where we can fetch the token before every test instead of doing it here right so basically I'm taking this line away and I'm moving it in here so this is part of the testing framework we have a special function called before all right and we can。

Ftch the token from the blockchain first and then do all this stuff because that makes sense because you don't want to just do it inside of here。

We want to do it before we do everything。So we check the name like this。

And then we can also check it symbol like this。All right。

 boom has a symbol and that's just like the name test， but it's， you know。

 we just check for the symbol， so symbol equals token do symbol。All right， and then if you want to。

 you know pause this part of the video and then check your test before werun it。

 you can do that or you can also check the code solution。Provided in the GitHub link down below。

 all right。So let's run the test。And let's see if it passes。All right， there we go， boom。

Deploy successfully， has a name and has a symbol。So great， we're making good progress。All right。

 so those are the basic attributes to the token Now next what we want to do is test we want to build up the token so that it can be minted all right yeah so that it can be minted and so that it can be distributed to other people so the whole idea is that whenever you are creating the token。

You want it to start from zero like whenever the token is created there are no tokens in existence and then we want people to collect them so again we're gonna to have this memory token game here and it's it's not there anymore but again we're gonna you know match squares like in a memory game and whenever we match the squares a new token is going to get created for us and we'll see that in action okay so we want to write the logic to create the tokens。

 we'll have a mint function right that's that's what it is you know you mint the token that's what it means to create one。



![](img/84667de9984b90e1ba962183151f4b9e_31.png)

![](img/84667de9984b90e1ba962183151f4b9e_32.png)

So we'll create a new function like this， I would say function。Mt， all right， let's say address to。

 and then string memory， token UI and say public returns bo all right。

 and so let me explain what this token what this mint function does。So it accepts two arguments。

 of course is the function， so we start with the function keyword and we give it a name mint。

 all right， and it has two arguments， argument one， and then argument  two。

So the first argument is the address or the username basically of the person on the blockchain that we're going to give the token to that's what this address data type is here all right so it's an Ethereum address just like you'd have in Memask so this is the person two is the variable name and that we just underscore as just a convention here。

And then we use a string for the token Uri So what do I mean by that basically like you know these tokens have images associated with them so you can see like this is this cat has a cat image all this cat has a cat image all these tokens have pictures so these pictures are stored somewhere you know they can be stored on a web server somewhere if you want to get more decentralized you can store the images on a distributed file system like IPFS for example okay so that's what these images are okay so basically we need a place to reference the image for each token and that's what the Uri is so that the two will be the owner and the token Uri will be the location of the of the image that's stored so we're gonna override one of the functions inside of the ERRC 721 file here so。



![](img/84667de9984b90e1ba962183151f4b9e_34.png)

![](img/84667de9984b90e1ba962183151f4b9e_35.png)

Meant with。see here。呃。Actually， we're going to create our own。So we'll just say。Do like this。

Let'll say。You went yeah， well over the mint function， sorry， I got a little confused。

 so see here mint。All right， you can see this function inside of here。It's an internal function。

 that's why it uses this underscore。All right， and so we want to create our own min function that implements this。

 but we want to do it a little bit differently， all right？Soum。

How this works is it wants to use a token ID， okay？So you can give an arbitrary token ID。

 but we want to actually create a token ID， so first of all， let's just do the mint function。

 say mint and we'll pass in you know two value here。

 this is how we implement the mint function that we've inherited from okay underscore mint。

Let's say token IDing。All right， now we need to set the token ID， so we'll say youent。

Let'll say token ID and then we'll we'll say equals。Total supply， and then we'll say add。1。Okay。

 so let me explain this。The ERRC721 standard， or at least this particular smart contract that we're inheriting from。

Has a total supply function， so what this does is it returns the number of tokens that already exist。

 so we have an all tokens array。Whi basically keeps track of all the tokens as you might suspect and we just read the length all right so we can just see how many tokens exist in this array and that will give us the total supply or the total number so we're going to use that as the ID okay？

And so whenever we want to create a new token， we'll go ahead and increment that ID manually inside the function so that we can't accidentally override an ID。

So we'll just get the total supply， we'll add one to it just like this all right。

 to get the new token ID。And we'll call this mint function， all right。

 so this calls the mint function inside of the ERRC 721 contract here。And then boom。

 that will be the first step。 So the next step is that we want to。Set this token UI， okay？

So there's a function for that inside of your two， set token， UI， okay？

So basically this just takes the token ID， which we just created and then the UI。

 and then it sets the UI for the token so that we can see this image right here okay。

 and this is exactly we'll do for a memory token。So we'll do that like this。Say set token UI。

And it'll pass in the token ID， and it'll pass in the token UI。Allright。

 we use a semico and then finally we'll just return true all right and then boom there we go all right hopefully all this code works we'll check it out our tests but if it does then this is our complete smart contract and now it's it's pretty simple right this is not an in-depth flex solidity coding tutorial because we're just using a library and customizing it again we've got lots of other tutorials on my channel if you want to check those out for more in depthepth solid coding Of course the blockchain boot camp goes way more in depth in those tutorials as well you can check that out in the link down below。

But yeah， this is。This is it all we need is a smart contract with a couple variable values and then a special mint function and we're ready to go and that really highlights how easy it is to use the ERRC 721。

Standard use the token templates from open Zeeppelin to get started really fast creating own token。

Let's go ahead and write the test for this with this kind of quick。I'll go to the test here。

We'll create a new test like this。She's going to paste this in。

 I'll clear it out and then we'll write the code manually again。So I'll clear that out。

And so we're going to create a new test unit that describes a token distribution， all right。

 so this is just like deployments， the two main concepts here are deployment and then token distribution。

 all right。So I'm going to。This up so you can see it。We want to talk about how it mins tokens。

 so first of all we declare this variable value here let result。And then we want to say， basically。

 we're going to call the mint function and then inspect the results。So we can say you know。

 a await token。 mint。All right， were just going to call this mint function just like this。 All right。

 boom， we're going to do it in our test instead of the console。And then we could say， you know。

 accounts。Zero。So if you look at the top of our test here。

 we have this accounts in variable that's injected by shuffle， okay， and so count zero。

It's going to be the first account in that array， and that's the two value。

 that's the person that we're creating the token for here on the two。And then next we want to。

Do the token UI， okay？So we'll just say like you know HDDPS， calling for slash www。

 you know tokenuri。com slash nft right so this is just a really basic example。An arbitrary URL。

 this could be anything you want it to， I'm just going to do that for now to make sure that works good。

So we can make the first thing we want to do is make sure that it actually increments the total supply。

 okay， so do that like this。It should increase the total supply。

We just call the total supply function that's exposed by， you know this smart contract like this。

 we say you result， which we defined here。Equals a weight， token， total supply， right。

 we just read it back。And then we want to make sure that the total supply is one because you know now we have created just one token。

So we do that like this boom， all right？And then next we want to ensure that the owner balance is increased。

 all right， so this person who we went to the token for。

 we want to make sure that they have just one token。All right， so we can do that like this boom。

So we can say increments to owner balance， your result equals a weight。

 token balance of accounts zero， all right， that's the first account and we say this is equal to one。

 right？So next， we want to make sure that the token belongs to the owner。

 so we'll use a special function for that。Oh like this bone。So token should belong to the owner。

 so we just say token do owner of ID number one all right and we just want to make sure that the owner of token number one belong to the account that we minted it for okay that's how you do this account zero to string owner is correct okay and then let's do this。

Next， we want to see that we can actually。See all the tokens of the owner。

So you can get that just like this， we need to see how many tokens the account has first we'll call this balance of function just like this。

 okay。We want to see how many tokens they have and then we want to loop through all of the tokens inside of JavaScript。

To fetch out each individual token that the person holds， okay。Basically。

 what we'll do is write a four loop in JavaScript like this boom。To fetch out each token。

 so if you're brand into programming， let's just look at like four loop JavaScript。



![](img/84667de9984b90e1ba962183151f4b9e_37.png)

So。U me just pull it up like in JavaScript， you have these four loops。

So basically you can just write this code that keeps executing over and over again for all these conditions。

 so here not this a little the context switch but basically like this says for I which is a variable value that you declared here so I is zero and then we're going to loop through each。

 we're going to keep like incrementing I by one until you get the length of this car's array okay。

And then that's how long the loop will execute for so if you want to you know learn more about how these loops work。

 definitely go check out W3 schools they're do a good job of teaching the basics okay so we write this four loop that basically loops through all of the tokens that the person has so we start at zero and then we go all the way to the balance of which is one so it's gonna be one token if they had a bunch of tokens it would loop through all of them。



![](img/84667de9984b90e1ba962183151f4b9e_39.png)

And then we just increment it one by one and so for each of those。

We want to fetch all the IDs that belong to this owner， so we say token token of owner by index。

 all right？That's what this function does is a special function provided with this smart contract。

And we say， you know， pass in this account and then we want this basically is going to return all the tokens from this account。

The first one， the second one， et cetera， et cetera。

 and then for each of those we push them into this array here okay？

And now because this person only has one token it just going to return one token inside that array。

 which will look like this， so this is the expected result。

 it's going to be just this simple array with one you know if they had more tokens。

 it could be like you know two。You know， three， et cetera， et cetera， but it's not。

 they just have one token in this case so。What we want to do is basically just assert that this array is correct。

 so we'll say token IDs two strings is equal to expected two strings。

 sorry token IDs is the array that we created here。

And then expected is this array that we created here。Okay。

 and so the last thing is we just want to make sure that the token UI。

For a token we created is correct， so let's say token。Your eye， correct？

And we'll just paste it in like this boom。So token your eye equals a weight， token dot。

 token your eye。For the first token and we want to make sure it's equal to this same URI that we created here at the top。

 okay， so boom。All right， so that's all the tests we need for now because we don't need to do test coverage for all this stuff because it's already tested inside the library that we're borrowing from。

But we do want to write test coverage for the stuff that we implement right and that's what this does and we also wanted this basic test to you know see that our settings are correct and that you know it deploys properly okay。

And the last thing I want to mention this， I don't think I said this at the beginning of this part is that it's really important to test smart contracts。

 you know it's important to test all smart all software well it tests often are very important in software but that way。

 they're extra important for smart contracts， okay， because smart contract code isn' immutable。

You know， developing blockchain applications is very different from developing regular applications。

Because like once you put on the blockchain， you can't change it， really。

And so you want to write tests the check for things extra before you deploy it for real okay。

 so that's what we're doing here All right so let's just save it and let's run the test and say trovol test and hopefully it passes how many problems here we'll just see if fingers crossed。

All right， we'll wait， we'll wait， come on， come on， come on。

boom there we go So it mins tokens properly awesome So everything on our tests passed just fine So at this point。

 if you want to play around this， you could write more tests if you wanted to or you could like you know change these values to watch the tests fail and then make them pass just so that you see what that's like but from this point we're gonna move on and go ahead and start building out the client side portion All right so now let's start building out the client side portion of the application So I'm gonna go back to my web browser here and make sure I still have this open Okay so again this is our web server is running here in the separate terminal tab make sure you start your web server if you haven't already thismpm run start and I'm running it in a separate tab so I can still execute my other commands here。



![](img/84667de9984b90e1ba962183151f4b9e_41.png)

![](img/84667de9984b90e1ba962183151f4b9e_42.png)

Let's make sure that， you know Gaanasha is running， okay， this is the blockchain。And then finally。

 this is your truffle， migrate， dash dash reset tube， sorry， you would say reset。

To put our smart contracts on the blockchain。Make sure theyre things there our tests are passing but we want to put the smart contracts there so the first thing we want to do is make sure that Metamask is set up so again you know Metamask is how we connect our web browser to the blockchain we're going connect it to this particular blockchain that we just booted up here with Kaache and so we first do that by you know going to Metamask here。



![](img/84667de9984b90e1ba962183151f4b9e_44.png)

And typing in basically say choose the network， okay， and you'll see the main Ethereum network。

 you'll see these other test networks， but you want to create a custom RPC。

 probably I just called mineganache， okayganache， and then I type in the RPC URL。

Whi is just this right here， you can see RPC server boom， all right， so I've already done it。

 so it's going to say it's already in the list， but thats that's how I do it I just canosh and then boom and then click save。

And then you want to connect to it， all right？And so once you've done that。

 your web browser will be talking to this specific test blockchain that you're running。Okay。

 so again， these are all the accounts on the blockchain so it's got 10 accounts that already have they are premind with 100 fake ether again this is an Ethereum blockchain's it's a fake Ethereum blockchain that's the blockchain we're working with in tutorial basically。

This e isn't worth than anything on the real Ethereum networks that don't get excited。

 but you need to use this Ethereum to pay the gas fees or the transactions whenever we claim the tokens on the network because anytime you put new information on the Ethereum you have to pay gas。

 that's what it's for and yeah so I've already paid some gas for deploying the smart contracts that's why the gas has gone down here okay normally start with 100 but this is the account that truffle uses to deploy the smart contracts is the first account list anyways I'm kind of going off a tangent here but I just want to explain that but。

Anyways， we want to import this account into Kache so we can expose the private key right here。

 click show keys and you'll see the private key all right so never use this account in production because everyone who's watched this tutorial has seen this private key and they could steal your money if you decide to put any real cryptocurrency on here right anyways。

 you want to click a copy。And then you want to go to Gaache okay， and then on the accounts。

 you want to go to import account， you can click you know。

 import account here and then select private key paste and then click import。

 I've already done this Okay， so it's not going to import that same thing again。

 but to click import it'll work and then you know I've named my account you know Gadaache number one。

You can do the same thing by changing the account name that just reminds me that it's the first account provided by Gsh okay so again don't use these in the real world this mnemonic is used to rebuild wallets and anybody who's seen this tutorial could steal your money if you you know use this for real so don't do that but it's okay to use it in development right？

And that's how we're doing that。So now you've got Metass set。

 web browser is connected to the blockchain。But the first thing we want to do is connect our app to the blockchain。

 actually this memory tokens app， we want to wire up a connection。



![](img/84667de9984b90e1ba962183151f4b9e_46.png)

We'll do that that's the first task okay， but there's a little bit of work to be done in order to make that happen all right so let's go to the source director。

 go to components and look at this app dot JS file okay so this is the main file or write all the client side code okay this is a react JS component so Re is a framework for building JavaScript interfaces or user interfaces in JavaScript okay。



![](img/84667de9984b90e1ba962183151f4b9e_48.png)

It's a very popular modern web development framework。

 very popular for blockchain developers that's one of the main reasons that I use it in my tutorials。

 lots of other web developers already no react and yeah that's one of the reasons I use it in my tutorials okay so it's a component based library which basically means that all the code is。

Is contained instead of react components。Which is just these class based components that have a name all right。

 and they inherit all this behavior from react component， all right？And you know。

 it mixes HTML and JavaScript all inside the same files。

 so instead of like having a file for HTML code and then a file for your JavaScript code。

 it puts it all the same place and you can even see like a mixture of HTML and JavaScript on the same line。

That's what this like evaluation here is so don't worry if you're like not a react developer already if you're not much a developer。

 you can just follow along with what I'm doing here and pick it up pretty quickly like I think you'll get the hang of it as long as you just watch what I do。

So that's what react components are the other big。Thing to know about react。

Is it has a state object with a bunch of special functions under the hood， Okay。

 so the state object stores。Like the state of the application。

 that's a terrible explanation because I just used the same word to define the word。

 but let me just illustrate what that looks like and I think it'll make sense。

They give you this example here that talks about the to do list。

 so if you're on a to do list and you say like you know item one。All right。

And then you click like add item one， and then you say item two。All right。

So your website now knows about item one and item two。Well。

 how does it know where it is Well it basically has a database kind of。

Inside the website that keeps track of these two items on the to do list。

 that's what the state is okay， so you can see this right here。

 this dot state equals this and then has this items right here this items array well there's an array under the hood that stores each of these items that we just added inside this text box okay that's the state object is。

It basically gives us a way to。Handle like a small database on our client that application。

And so we have all these special， you know。Functions and things like that that help us interact3 react state。

You'll see those in action as we build out this game， okay？



![](img/84667de9984b90e1ba962183151f4b9e_50.png)

So let me go back to the code here and introduce you to this， right。

 so this looks familiar from that react。Documentation， so we have a component here called app。

 all right， we have a constructor function here， which just initializes the component。

 looks a lot like this all right this constructor right here。

And then we have this render function right here that lays out all the HTML code， all right。

 I'll expand that。

![](img/84667de9984b90e1ba962183151f4b9e_52.png)

And you can see it here all right， this looks just like the documentation。

 here's their render function that lays out the HTML code。

 you know they put some JavaScript and some HTML inside of here and we will do the same thing as we code this example out okay。

So， you know， we can see that here， boom， here we go。



![](img/84667de9984b90e1ba962183151f4b9e_54.png)

Inside of our layout， we have you know a nav bar， that's what this is， all right？



![](img/84667de9984b90e1ba962183151f4b9e_56.png)

So as this this black navigation menu up here with the memory tokens， you can see this here。



![](img/84667de9984b90e1ba962183151f4b9e_58.png)

All right， memory tokens and then this brain， right。

 this is an image right that I've already imported at the top of the file。And then， yeah。

I've already got some basic CSS imported into the app and then one thing to notice too is that we're using bootstrap here so bootstrap so bootsottrap is a UI framework for building you know user interfaces so you don't have to write a bunch of HTML and CSS yourself that's what we've got here that's why this styling looks nice without writing much and that's why you have all these extra class names inside the markup and some people don't like bootstrap because it clutters up the markup but this tutorial is really about teaching you how blockchain works and how react JS works it's not so much about teaching you how CSS works so that's why like using bootstrap for these types of things All right so let's make our app talk to the blockchain a few minutes ago that's what I said our first task was and we got a little sidetrack explaining how react works how bootstrap works but if you're brand new then you definitely need to understand those thing before continuing so let's just create let's just connect。



![](img/84667de9984b90e1ba962183151f4b9e_60.png)

![](img/84667de9984b90e1ba962183151f4b9e_61.png)

![](img/84667de9984b90e1ba962183151f4b9e_62.png)

![](img/84667de9984b90e1ba962183151f4b9e_63.png)

App the blockchain。

![](img/84667de9984b90e1ba962183151f4b9e_65.png)

So in order to do that we're going to use a library called Web 3 JS。

 so this is the main JavaScript library for interacting with the Ethereum blockchain again Ethereum is a protocol that we're going to use in the tutorial and so you know we've connected our。



![](img/84667de9984b90e1ba962183151f4b9e_67.png)

![](img/84667de9984b90e1ba962183151f4b9e_68.png)

Our web browsers are the blockchain with Metamask， but now we need to connect our web app to the blockchain。

 we're going to use Web 3 JS to do that， right？

![](img/84667de9984b90e1ba962183151f4b9e_70.png)

I're sorry， this one right here。So we're going to see Web3 in action for sure in the tutorial。

 but first we need to import it at the top of the file， that's what I did here。



![](img/84667de9984b90e1ba962183151f4b9e_72.png)

All right， but now we need to actually。Create a function that loads web3 in the app and so I'm really just going to copy and paste this and that's okay because you don't have to code this out by hand I don't personally code this out by hand I just import it into my other projects because there's no reason to code it out by hand it's the same code every time so boom。

We're going to create this function called load Webb3， all right？

And this code right here is literally given to us by Metamask like that's another reason I'm not making you code this out by hand MetaMask even tells us in this blog post like hey。

 here's how you connect your web application to web3 so I basically have taken Metaask's own recommendations here。



![](img/84667de9984b90e1ba962183151f4b9e_74.png)

![](img/84667de9984b90e1ba962183151f4b9e_75.png)

And sified it for this react app and create this load web3 function， okay。

So we've just defined it and we've connected it to the browser。

 but the next thing we want to do is actually。We want to call this function。

 so we'll get a new function here called component will mount。

And this is a JavaScript function or sorry a react lifecycle method so you know you can read more about those react lifecycle methods in their documentation if they want to like to see will so they don't let's they don't show any here but you can just Google it like component will mount for react you can read more about those so basically the whole idea is that like while the component is being rendered。

 there's a special point in its lifecycle where this will be true we'll say component will mount and whenever that's true。



![](img/84667de9984b90e1ba962183151f4b9e_77.png)

![](img/84667de9984b90e1ba962183151f4b9e_78.png)

![](img/84667de9984b90e1ba962183151f4b9e_79.png)

![](img/84667de9984b90e1ba962183151f4b9e_80.png)

We want to execute this code， so in this case you want to say oh wait。

 we'll say load or thist load web3。Okay， and we'll call this function。



![](img/84667de9984b90e1ba962183151f4b9e_82.png)

Okay， so let's check our app and let's open the console。If you want to know how I did that， you can。

 I think it's option command I or you can just do right click and say inspect and then click Con here。

 okay。And then we don't see anything yet。That's okay。



![](img/84667de9984b90e1ba962183151f4b9e_84.png)

Let's perform a task to ensure that Web3 is connected into our app。

 so we'll create a new function down here。We'll call it load blockchain data。All right。

 so you like this boom。And then we'll call that function here。

 so low blockchain data we're going to define it here， and then we're going to call it here。

 so you'll say oh wait this low blockchain data。And then the first thing where you're doing inside of here is just。

Stash the Web3 value， all right。Cot Web 3 equals Windows。 web 3。

And then the first thing we want to do is just fetch the account that we're connected to with Metamask and log it out to the page。

So to that like this， we'll say Con。Accounts。Equals a weight， web3。😔，t east。ge。Accounts。All right。

 and then we'll say console。The log。Say account。And then we'll say accounts。Zero。All right。

 so this is the Web3 function for fetching the accounts and then this is the account all right so let's just refresh the page and then boom there we go so here is the account that we're connected with。



![](img/84667de9984b90e1ba962183151f4b9e_86.png)

Meta maskask， you can see it here boom all right to AEC and then to AEC awesome so we are rockinger Mo。

 we have connected our application to the blockchain。

 we have Memask connected that's a huge first step right our react app is working it's talking the blockchain checkmark number one okay。



![](img/84667de9984b90e1ba962183151f4b9e_88.png)

So next we can instead of logging this out to the console， it's actually display on the page up here。



![](img/84667de9984b90e1ba962183151f4b9e_90.png)

![](img/84667de9984b90e1ba962183151f4b9e_91.png)

Inside this nav bar so we've already got this wired up inside the nav bar you can see this right here。

 so this is how react implements JavaScript inside of HTML okay so we've got this render function that lays out the content on the page we've got a bunch of HTML but then inside this HTML we can use these curly brackets to evaluate JavaScript so we're using that react state object which I talked about a minute ago right this thing right here。



![](img/84667de9984b90e1ba962183151f4b9e_93.png)

![](img/84667de9984b90e1ba962183151f4b9e_94.png)

All right， the state object to store the current address right and right now we just said it as a default value of0 x0。

 okay？And。Inside this account here， we've just said hey read this dostate do account。

 that's how you read information from the react state object it's super simple。

 which is this dotstate dot account will return this value right here okay and that's what you're seeing。



![](img/84667de9984b90e1ba962183151f4b9e_96.png)

![](img/84667de9984b90e1ba962183151f4b9e_97.png)

Right。Here， okay。So now after we have。Gotten the real account for Web3JS。

 instead of logging it at the console， let's say this set state。

And then we'll pass in the account here， let's say accounts。Zero， all right， boom。



![](img/84667de9984b90e1ba962183151f4b9e_99.png)

And then refresh and there we go awesome now we can see the actual account that we're connected with from Meta maskask inside of this project Okay boom there we go awesome all right so that's the big next step So now what we want to do is we want to actually connect the smart contract。



![](img/84667de9984b90e1ba962183151f4b9e_101.png)

From the blockchain。And bring it into the app as well so this is the token that we just created in the last section。

 we want to bring it into our app and load up that information and put it in the state object as well okay。

So we'll do that like this。First of all we have imported the token at the top of the file already right this is just the AB files if you go to the ABs source As you can see the memory token right here so this is the truffle artifact it's not actually an A this is not the best name for this directory but you know this is contains the A which is basically just a JSsonN object or an array that describes like the functions on the smart contract it describes the interface basically so that we know like what the functions what functions we can call inside our app and things like that so we're gonna create a JavaScriptscript version of the smart contract just like we did in the console just like we did in the test suite inside our clientside application and we need two pieces of information to do that we need this AB okay。

And we also need the address， so I'll show you that inside web3。

 let's just look at three E contract whenever we create a JavaScript version of the contract。

 we need this decide how do it right here。

![](img/84667de9984b90e1ba962183151f4b9e_103.png)

New web3 Eth contract， let me pass in the JSON interface。

 which is the A that I just showed you and then also the address that's the location of the smart contract on the blockchain so this file in Hyif here for the memory token it contains the A。



![](img/84667de9984b90e1ba962183151f4b9e_105.png)

And then it also contains the address down here at the bottom， okay， let's just sign。

Let's look for networks， networks， yeah boom， there we go， so networks， it contains the address。

 let's see those are the events。The address boom right here for the smart contracts and the A is the top and then the address of the smart contract is here。

All that information lives inside if you're inside this JSON file。

 so we need to pull it out and then create a JavaScript version like this okay。



![](img/84667de9984b90e1ba962183151f4b9e_107.png)

![](img/84667de9984b90e1ba962183151f4b9e_108.png)

So the first thing we want to do is determine the network we're connected to with Gache because that's going to tell us the specific location of the address。

 all right？Because the address could change depending on what network we're connected to so that's the first thing we want to do we want to get the network ID all like this。

So we'll say boom， so let's say load smart contract。So network ID is going to be Web3 E get Ne ID。

 in which console log that， okay？

![](img/84667de9984b90e1ba962183151f4b9e_110.png)

And so we'll go back to Gash here and see 57， 77， all right。



![](img/84667de9984b90e1ba962183151f4b9e_112.png)

So that's the same thing that we see here， which is what we expect because we have Mesasks connected to Gache。

 if we were connected like the main Ethereum network， it would be one。

 but inside here it's 5777 that's just the name of Gash and you can also see that here， 5777。



![](img/84667de9984b90e1ba962183151f4b9e_114.png)

![](img/84667de9984b90e1ba962183151f4b9e_115.png)

So now you want to fetch into this file and fetch the address on network 5777。

So we'll do that like this， we'll say， you know network data。All right。

 this is going to be the memory token Network key network ID， so we're going to do this networks。

 then we pass in the network ID 57， 77。And then we want to fetch the address。

 but only if it's deployed to the network， we say if network data。All right。

 then we'll you know store the address like this。We'll say， you know。

 address is network data dot address， Okay， all right， so that will set the address like this okay。

 and then we'll say， you know if。If it's not， if we don't see network data， like I'll say。

 tries to get into that file and it doesn't see that。

 then we'll just say the smart contract is not deployed to the network。

 we'll just alert that to the window okay。All right。Like that boom done so again。

 in order to create the JavaScript version and smart contract， we need the AB。

 I we also need the address， we have the address， we can get the A like this。

 say constant AB equals memory token。ab because that's on the top level。

 okay it's not in the network data right it right here。

ABI ABI is always the same regardlesss the network， but when the network changes。

 the address changes， that's why we fetch the network data address， okay？

So now we can create a JavaScript version of the smart contract we'll call it tokens like token equals new web3 Eth contract ABI address it's just like we saw in the documentation here okay。

 new web3 Eth contract AB address okay， so we fetch both those pieces of information just like that so now we want to do is add it to our state object so we'll say you know like token let's do it empty。



![](img/84667de9984b90e1ba962183151f4b9e_117.png)

![](img/84667de9984b90e1ba962183151f4b9e_118.png)

Object here and we'll say。You know just like we did here this set state account。

 we can say this set state token right， so this is a shortcut in ES6 for saying this。

 so this is the exact same thing。But we can abbreviate this since ES6 by doing this， okay， all right。

So next， so we fetch the token smart contract， it's done。

 and then now we want to do is fetch the total supply， okay？So we'll do this。

 we'll say constant total supply equals a weight， token。 methodss。toal supply all right。

 and now with web 3， you can't just call the function you have to also say call all right。

 so like with Web3 JS， basically like let's just see here。



![](img/84667de9984b90e1ba962183151f4b9e_120.png)

You may find the documentation， yeah， call methods or when you read data from the blockchains。

 basically you have to do the function name and then say， you know， call at the end， okay。

 because if you don't do call it won't actually run the function， it'll just return the function。

So send methods， which we'll see later are when you actually like trigger transactions on the blockchain。

 and you have to call sendend at then end of those functions as well。



![](img/84667de9984b90e1ba962183151f4b9e_122.png)

But in this case， we're just reading the total supply， so we do call here。All right。

 and then we're going to store that to the state as well， all right。

 just like we did with the other things， so set state total supply。

And then we're going to update the default value in our state like this， so we'll do this。

And the while way're here， instead of doing token is an empty object， I'm going to say no， okay。

That's probably better。U so that's the next thing and then we're going to， uh， let's just see here。

Now we want to load all the tokens so we did that into the tests right this can be very similar we did in the test where you can see we loaded all the users tokens with this for loop so I don't want to go through and explain all this stuff over and over again because we already did this in the testing section so I'm just gonna paste in the modified version inside of here because I don't want to like you know just reex all that stuff you can go back and watch that section if you want to but we're gonna to load the tokens like this so just say boom soll load the tokens。

So this will say balance of a weight token methods， balance of accounts to zero。

 that's the count we're connected with， what you call and then we write this for loop to go through the entire balance and we just say you know get the token of owner by index。

 fetch the UI and then we set the state， the token Us。

 that's going to be all the URLs for the tokens， we update the state like this okay so we'll also do a default state here。

We'll do an empty array as default for the token your eyes and there we go us so that's it。

 that's loaded up all the blockchain data into our app so again if you want to understand how this works。

 go back and watch the testing section because this is almost identical code。

We're just calling it again inside our client that application to load up all the tokens on behalf of the users so let's just go back to our browser make sure everything loads properly and yeah boom there we go so nothing has really changed that's okay we't shouldn't see any visible changes on the page because basically yeah we we just wired up stuff under the hood okay so let's just see here next let's go ahead and fill out the rest of the state object so i'm gonna to payeten and values here you can just get these from the final tutorial code if you want to all right so there is gonna be some more values that we need so we need a cards array this is going to basically。



![](img/84667de9984b90e1ba962183151f4b9e_124.png)

![](img/84667de9984b90e1ba962183151f4b9e_125.png)

List all the cards on the page， the cards chosen， and then the card's chosen ID and the cards one。

 you'll see all these implemented as we go through the story okay。So first of all。

 yeah first what we want to do now is actually like build out the game we've wired this up to the blockchain。

 we have you know loaded the smart contract now we want to create the game so the first thing we're gonna do is just show you how we're gonna to do all the cards so in the project already if you have the public directory you could do these images and you can see like the tiles for the memory game okay and then also like the actual you know the the images for them okay whenever you flip them over so first thing we want to do is create an array that manage all this stuff so actually before I do that let me explain these are in the public folder because we don't want them to be in our react source code because whenever we mint the tokens whenever we create these we're gonna to reference these full URLs from the public folder so that's why I'm doing that in case same watching that wondering why the images are there that's what。



![](img/84667de9984b90e1ba962183151f4b9e_127.png)

![](img/84667de9984b90e1ba962183151f4b9e_128.png)

If you're a total beginner， don't worry about。So I'm going to create a constant。

Inside of here that references all the images， it's like this， I'm going to paste this in。

 you can get this from the final code solution if you want to。

 but basically we're going create this constant called card array。

That just keeps track of the name of each card and then the image location， so the image， you know。

 the fries， the cheeseburger， the ice cream， the hot dog， etctera， etc， okay？

That's going to just get stored in this constant here， right？And that you know。

 that's going to reference all these images in the public folder for each tile， okay？

And so now what we can do is load all that content on the page。So first。I will scroll down here。

And we want to。Put all that here and this code goes here section。

So what we want to do is create a we want to look at this card array。And yeah。

 basically we want to create the card array first。So inside the component wheel mount function。

 we're going to go inside of there and sort the cards because we were to randomize them before we put them on the page all right。

 so we want to go at the very last line of this before after low blockchain data and do this。

So let' say thist set state card array， right， that's this right here。

And then we want to take this card array right here。And then we want to sort it。

All right and we say 0。5 minus math dot random so that just gives it a random order and then yeah。

 it just randomizes the cards for the memory game and that way it'll be sort of an unpredictable order anytime it lays it on the page right so that's the first thing is randomize the cards and then now all those cards are loaded up in this cards array state variable here and now we can load them out on the page like this so we'll just map over them so map is a function in JavaScript where we can iterate over each item in the array all right we'll say this do state do card array。

Okay， so I'm just going to paste this in here， you can get this from the code solution if you want to。

 but I'll explain it。So say this state a card right map and then we'll say the card and the key so here's the key the key is basically just something that react needs to know about whenever we implement multiple items with the same HTML element on the page and we'll say the source is equal to this choose image will implement this function momentarily all right it not does not implemented yet but then we'll get each element and ID of the key。

And then we'll create this on click event so basically whenever our car is clicked， it will get the。

Function and will'll actually implement the card， so let's not do this part yet。Let's do that。

 let's just do choose image right and get some quick feedback。

We'll create a choose image function like this。All right， so I'm going to paste this in。

 I'll code it out step by step here in a second， so we'll do it right below load blockchain data。

Let's has to do below the low blockchain data， okay。So choose image， all right？So basically。

 we'll just say we'll start here。We'll say this if state actually it's do。Let's just start like this。

 let's just do choose image and then we'll start off like this。

This will be the basic surrounding points that choose image。All right。

So basically this is just going to return all the blank cards， right？



![](img/84667de9984b90e1ba962183151f4b9e_130.png)

And there we go， boom， awesome， so doesn't do anything yet。

 we just see the board laid out on the page。

![](img/84667de9984b90e1ba962183151f4b9e_132.png)

And yeah， that's the first feedback。So what we want to do is actually create the logic to start flipping over the cards so we can check the matching。

 right？So that's what this part of the function does。

 so I'm going to add this back in there again this is in the final code solution。

 so we want to create this on click handler， so basically anytime we click one of these cars we want a certain function to fire。



![](img/84667de9984b90e1ba962183151f4b9e_134.png)

![](img/84667de9984b90e1ba962183151f4b9e_135.png)

All right， so say on click and then event， or I would say let the card ID。

 we're going to get this data ID right here， event target， get attributes data ID。

 and that's this right here。And then we say basically this state cards one includes card ID two string thats that's basically going to say like if you've already won the card then don't flip it。

 but if you haven't then flip the card over so we're going implement this flip card function and we're going to update this you know choose image so let's just。

Scroll up here and implement that flip card function。So we'll do that like this。

 we'll say choose image and then flip card。It's going to be an async function and we'll just pass in the card ID okay。

 and then so inside of here's where we I'll lo it to do it。So what we do is basically。

We just say if the card's already chosen。So basically we say thist state chosen cars length， right？

And we see if there's we just check the link to that。All right。And then。

We basically say this set state and we actually update the chosen card， so card's chosen。

 this state card's chosen， this state。 cards array， card ID names。

 so basically that just updates the chosen card to include this particular card that we've passed in again。

And then also we implement the IDs， so we have cards chosen and then the cardss chosen ID。

 which is a specific ID that we passed in。So this can be a little complex to understand there's a few different arrays going on here。

 but I think if you just take a step back and look at this and then look at the different arrays that are in play here。

Then that will make sense， okay。So there's that and then basically what we want to do is say if the already chosen is equal to one。

 all right？Basically， if it already has been chosen， then we want to check for a match。

 we're not going to do that just yet， we'll just leave that all right。

So that's the first step all right so next we want to do is actually implement the logic for showing different cards on the page all right so whenever we flip the card like we want to you know show different image okay。

So we want to go back up to the function I forgot the name is call， let's see here。

 it's choose image， all right？So we want to go to the choose image function and update that。

So right now we're always doing the same image， but now we want to do some conditions and say like we got the card ID right。

 I want to say if the card ID includes，Um， basically， if if this is in the cards chosen already。

 then we want to show the card on the page right， and if not that we want to do that default image。

 right？So that's that's what this does here so this state card's chosen ID includes this card ID right then we want to put it。

 you know， turn the card over basically because we're dynamically choosing the image right here right it'll change the source automatically and if not we want to do the default okay。



![](img/84667de9984b90e1ba962183151f4b9e_137.png)

So let's do that and then there we go， boom。So of course it's， you know， still。

 we can turn over everyone so that's not totally working yet and it's not actually checking for matches。

 but that's the idea， okay？

![](img/84667de9984b90e1ba962183151f4b9e_139.png)

So now we just wanted to turn over two。Cards at a time， right。

 so that's when we go back to this line right here， we say if it's already chosen。All right。

 basically if you've already chosen， then we want to go ahead and check for a match。

So that's the whole idea here is this， if the chosen cards already has one card in it and we're calling this function for a set second time。

That means it's you know it's one already exists， we're calling this function the second time then we want to check for a match okay so that's going to be our next function and we'll just say this check for match function be a little complicated so we'll just we'll just do really basic starting point here we'll say check。

For match。All right， and then just pass this in here， I this async。やませ。

Alert let's say checking for match so you'll see how that works right right so boom and then boom so checking for match all right doesn't do anything yet。

 it just puts the alert up on the page like this all right。



![](img/84667de9984b90e1ba962183151f4b9e_141.png)

But that's the idea。All right。

![](img/84667de9984b90e1ba962183151f4b9e_143.png)

And then we'll go back in here and we'll say we'll code this out more so first we want to do is keep track of each option that we have checked for right so the first is option one so this will be state cards chosen zero it will be option one ID state cards chosen one will be option two ID right so basically like if it's the same image then we wish want to say hey you just clicked on the same image。

And then。Next， if a。It's the same if you've actually found a match you want to tell you。

 so you say else if the card's chosen zero is equal to card chosen one。

 basically if the card ID is the same， then we'll say， hey， you found a match， all right？

And then yeah， and then we'll basically say， you know， this set state， you know。

 cards one and we'll put in the cards， okay？And they'll put in the token your eyes as well。

 so let's not do the token your eyes yet， let's just keep that out。

And then if you didn't get anything， right， if it wasn't a match， then we'll just say， you know。

 sorry， try again right， and then we'll basically just say。This set state。

We' reset everything in the bottom， this state card's chosen card IDD， all right。

 so we'll reset those after you've checked for a match and then basically if you've found them all。

 then we'll give you an alert that says hey， you found them all okay。

So this is the basic functionality for checking the matching。

We'll add the blockchain part in a minute to collect the tokens。

 but last thing we want to do is update the choose image function， okay。

 so whenever we dynamically choose the image like if we find a match。

 we want to show a blank white square okay？So I'm just going to overr the choose image function like this boom。

So basically we just add a new condition， so basically if the card one includes the card ID。

 so if you've won it， you've collected the token， then we want to show this blank white square。

 if not， you know show the card image and if that's not even true you didn't even find a match。

 then show the blank image， right？So that should be the basic logic， I believe。For the game。🤢。



![](img/84667de9984b90e1ba962183151f4b9e_145.png)

Um， so let's do that。And then boom。All right， so let's。

Try to actually find a match here there we go boom。

 found a match so click OK and then awesome so they go away。

 we found the match it checked it out correctly so that's the basic game functionality down so there's two last things to do before you finish up this tutorial。

Now what we want to do is actually。You know， collect the tokens。So when we find two hamburgers？

We want to create a new hamburger token， all right。

 and then we'll do that like this and we also want to we will list them out on the page whenever you find them okay。



![](img/84667de9984b90e1ba962183151f4b9e_147.png)

So we're going to add the blockchain part like this so down here。Inside of。Inside of this。

 like if we actually found a match and we say you' found a match。

 we want to change this code to look like this， and I'm just going to paste this in here but I will explain what it does so boom。

So basically， we do this。So we're going to call this function on the token， so this dostate。token。

 methodss。 mint， all right， this is the mint function and it is just like we did in the tests all right as you go back to the test。

 you can see this mint function here。All right， we're doing the same min function but with Web3JS。

 so it takes an account and then a UI， so do the account。

 which is the account we're connected to the blockchain。

 then we give it the token Uri which is basically just you know the current location。

 local host 3000 plus the image right here， so like you know this image is。pizza。pG。

So basically just build a URL right here for the U。



![](img/84667de9984b90e1ba962183151f4b9e_149.png)

And then remember with Web 3 Js， we're actually triggering a transaction on the blockchain。

 so we must call send all right， so my method。Send right so my contract methods。

 my method send right because we can't just call it like this。

 we tell who we're sending it from so we say from thisstate。 account。



![](img/84667de9984b90e1ba962183151f4b9e_151.png)

And then we wait for a transaction hash to come back from the blockchain and whenever that's done。

 we're going to update the state with the cards one， all right。

We're also going to update the card Us so this is gonna to be all the Us of the tokens we've actually collected。

 which is going to allow us to reload the page and play multiple times and save our cards or our tokens forever on the blockchain so let'll save that go back here and show you on the page so click refresh and let's give it a shot let's see if it works so let's try to find a match maybe all right you found a match awesome so' click okay and now you should see this meta maskask confirmation pop up that allows you to claim your token whenever you find a match right so click confirm and then boom there we go so I just got a confirmation on my other monitor that said the transaction was confirmed so we've collected that token。



![](img/84667de9984b90e1ba962183151f4b9e_153.png)

So now what we want to do is actually like display that token down on the page whenever we have collected it。

 okay， so let's go back to the code and implement that because we going to show all our tokens once you collected it at the bottom of the page okay？



![](img/84667de9984b90e1ba962183151f4b9e_155.png)

So what we're going to do is replace this code right here。At the bottom， right？

We'll replace this code and loop through this with with the map function。

 we'll say this state token your eyes map and passing token on of your key and we'll just show the tokens at the bottom all right。

 it's pretty simple， just like we did up here， but even simpler。And then we'll add some text to say。

 you know how many tokens you've collected right here。So tokens collected is equal to this state。

 tokenurris length， all right so all the token Us we've collected， we'll show the count right here。

And then finally， we'll just add that last little bit of copy text at the top that says， you know。

 start collecting or start matching now， all right。We'll just we'll just change that text okay。

 so now this should be a complete application， let's let's test it out here all right let's click save。



![](img/84667de9984b90e1ba962183151f4b9e_157.png)

Go back to yeah， and there we go， boom， so I'm going to close the terminal here or start on the terminal with the console Josh console。

And yeah there we go you can see our ice cream token was saved from the last time we played the game and we actually invented that token on the blockchain so let's do some more see if we can find any more in action all right。

 so it might take me a second to find a match here oh perfect if I on the match cook okay。

See a meta mass confirmation pop up， click confirm and then boom， there we go。

 we see our second hamburger， you know， token on the blockchain show on our page。

So if find another one， all right， so let's try this， oops， sorry，All right， found a match。

 awesome another meta mask confirmation。Pop up and then boom there we go so you get the idea here you know you can play this over and over again keep collecting tokens and so congratulations you know this is a complete blockchain game so especially if this is the first time for you building a blockchain based application you know really congratulate yours either way congratulate yourself you know you've seen I implement this this is actually the first time I built a game on my channel so you know hope you liked this tutorial but that's how it works。

So you know what you can do from here， you know， these tokens are now yours on the blockchain。

 you can take them out of the game， you can keep them in your Ethereum wallet。

 you can send them to other people and you know you can sell them on a marketplace， for example。

 these are digital collectibles that are yours to keep and you know you can keep playing this game over and over again to collect more tokens。

 you know what I mean it's just like you could just you could basically earn tokens that way by playing this game over and over again。

Like maybe there's some crazy advance incentive that you get people for playing your game and whenever they play it they get tokens that's kind of the future of blockchain gaming in my opinion that'ss where I think this whole space is headed you can create these games that don't fully run the blockchain but they have some sort of blockchain based rewards so you can take out of the game that exists you know outside their control so if you like this video you know where can you go from here know you can always take this and build more features on of it on top of it yourself I'd love to find out what you build again you can follow me on Twitter and just you know show me your project there and of course if you like this tutorial you want to hit the next step well first of all of course always smash the like button down below subscribe to this channel you haven't already and if you like this tutorial want hit the next step learn how to build a realworl blockchain application like more than just tutorial so that you can land a high paying job become a freelancer build your own real world project whatever right。

Just click this link here， heading over to DAPiversity。

com s bootcamp I can show you how to build that real worldd app step by step from start to finish right so again。

 hope you like this video love to see what you guys build subscribe to channel smash that like button and until next time thanks for watching DAPivers。



![](img/84667de9984b90e1ba962183151f4b9e_159.png)