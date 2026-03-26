# 终极React-Native课程---在-2025-年构建你的第一个移动应用--BV1gK5vzTEXV-

So you might not believe it， but this is the actual mobile application that we're gonna build with reactact native in this one single tutorial it works both on a simulator and on your iOS and Android devices in this application everything works in real time for example when someone likes a post every user can see the update immediately and what you have just witnessed was a clip from the end of the tutorial where we test out our entire application。

 everything that you know about react can be used to build this mobile application things to react native and in this video I'll assume you have no experience with mobile development and react native so basically I'll take you from scratch and I'll teach you 99% of the things that you would need to build a realword mobile application and specifically using react native and Expo so let me give you a complete walkthrough of the end result and then we'll talk about。



![](img/3c902dbcec98786b9e863ce7af553dc4_1.png)

The textt and what you'll learn from this video So this is a social media application that is called spotlight and it has seven different screens which are authentication home bookmarks post creationre notifications our own profile and the profiles of other users everything starts with the authentication screen we have Google authentication implemented that works flawlessly once we are logged in we will be navigated to the home screen where we have stories and posts we can like posts add a comment and add a bookmark we can see all of our past bookmarks on the screen and if we are the owner of the posts we are able to delete them in the create screen we can select an image from our device add a caption and share it with everyone there will be three types of notifications which are like follow and comment we will be able to see the post details as well as the comment。



![](img/3c902dbcec98786b9e863ce7af553dc4_3.png)

In the profile screen we can see our stats and posts and we can edit our own profile with this really cool animated model that slides in from the bottom of the screen and we can visit other user profiles where we can follow and unfollow them and in the homepage we will have refresh functionality as well as a logoup button that will navigate us back to the authentication So this is the entire application that we're gonna build today and as you can tell there is a lot to cover in this one tutorial so you will learn how to use every fundamental component that you should know in react native such as view text image link scroll view flatlist and the rest is on the screen on top of all these you will learn about special files and folders like app tabs and layout and you will learn some concepts and terms that you should know in mobile development such as Sp screen Sa area view tab and stack navigators。

Building this application we are gonna talk about the performance and we will see how to improve it as well。

 we are gonna learn how to use our own phones like the one that we have in the logo。

 we will even change the default app icon and I'm going provide some additional resources that you should keep in mind while building your next mobile applications with react native the most important question is do you really need a MacBook to be able to follow along with this video absolutely not any laptop that is connected to the internet should be fine and this is all things to expo which is a framework and a platform that is built on top of react native We are gonna talk more about it later in the video but basically it allows us to scan a QR code and test out the application on our physical device when it comes to the prerequisites if you know the basics of reactact you should be able to follow along from start to end without any issues and our text tag will be。



![](img/3c902dbcec98786b9e863ce7af553dc4_5.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_6.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_7.png)

React native with Expo convex for our entire backend and clerk for authentication along the way。

 you will learn some really interesting concepts to talk about in your interviews so overall this is the kind of tutorial that I wish I had when I first started with react native and I say this from the bottom of my heart now I can talk about this tutorial for the next 20 minutes but I think I'll just leave it here and see you inside just before we get into the video if you'd like to support my work I have a Umi course with over 100 hours of content for the cheapest price that you can ever get it's only one time payment for lifetime access you can find the discount link in the description and the source code of this project and future projects will be there you can watch this entire tutorial in Udmi as well without any ads thanks for watching and let's get into it So before we start writing any code I have prepared some。



![](img/3c902dbcec98786b9e863ce7af553dc4_9.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_10.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_11.png)

Notes that we can take a look at。 and once we are done with it。

 we'll go ahead and actually start coding。 You can get these notes from the link in the description。

 It'll be completely free at the moment it is private。 but while you're watching this video。

 it's going to be public。So let's start with the question， what is react native in the first place？

So it is a framework that allows you to build mobile applications using reactact。

 you can either use a JavaScriptscript or Typecr and in this video will be using Typecr。

 so all in all it is a framework that allows you to build mobile applications still using React。

And there is a really common keyword or a term called cross platform development。

Which means writing code ones that can run on multiple platforms and this is exactly what react native allows us to do。

 so it is a crosspl framework because we can write one codeb in JavaScript and we can deploy it to both iOS and Android。

Now this is really convenient and pretty cool when you compare it to back in the old days。

 so just think about it for a second back in the old days。

 if you wanted to build a mobile application you actually had to build it twice one for iOS。

 one for App store right and one for PlaySt which is for Android and you had to learn two different programming languages right for iOS you had to learn Swift and for Android。

 you had to learn Kotland and before Swift has been introduced you had to use objectiveject C which was a lot more harder than Swift。

And for the Colin， you had to learn Java。 and like there are still。

Some drawbacks like for Apple development you had to learn you had to have a MacBook which is pretty expensive to get and for the Android you had to learn Android SDK and its frameworks so it was really a complicated process and if you were a company founder that means you need to hire two different teams right one would be building the iOS application and the other one would be building the exact same application but for Android so it was really a messy process but thanks to react native we can just write one codebase right and then we can deploy it to both iOS and Android so I hope this gives you a little bit more insights into react native。

But a react native by itself is not enough and this is a screenshot that I took from the documentation。

 so if you visit reactnative。v and get started with it。

 you're going to see that they tell you we believe that the best way to experience react native is through a framework and their recommendation is Expo。

 this is what we'll be using in this video as well。

 so it is like a toolbox with all the necessary APIs that lets you to build production ready applications。

Okay， so now that we know react native is not enough， we need to use a framework like Expo。

 this is going to be our go to framework when using react native， but please don't get confused。

 react native and Expo are not the same thing， so like Expo is built on top of react native。

When you are building an application with Expo at the end of the day you're still writing reactact native。

 but it just has a lot more optimizations on top of it and you are getting a lot of other tools that you would need and like it's pretty convenient so you can think of it like react in Next Js in web development。

 when you are building an application with NextHs， you are still actually writing react code。

 but on top of it you have some features like server actions， API routes。

 things like that right server components so on and so forth so it is the exact same situation that we have right here。

And now let's take a look at some comparisons that we have between react and react native so I have prepared this list to prove you that react native is not actually different than react as the name suggests it is still react but it just has a more concepts and syntax differences on top of it so let's go through this list pretty quickly the point of this thing is just to get you you know just to give you some idea so in react web if you wanted to build a component you would use things like a dev H1 p tagag so on and so forth if you wanted to give some styles you would use a class name field right and in react native it is not actually that different instead of using ad you would use view and for any text you can imagine like H1 H6 like p tagag H3 span anything you would use text so you would wrap your entire text。

In a text component， which is coming from react native。Okay， I hope that makes sense。

 we don't really have class name in react native instead we would use S and this is something that we're going to get next。

So styling in react web， you would give a class name and then you would。

Let's say you would prepare these classes in your CSS files and you would give the styling like we have a card and profile image classes and these are the styles that it has。

And then when it comes to the react native， we are actually getting a component called style sheet from react native and here we create our styles。

 so we have Car and with these styles and then the profile image and under this style we say styles。

 card， so that means this view will get all these styling that you see here。So it is like CSS in JS。

 right？And we're going to see all these later in the video as well and when it comes to event handling in react web development。

 we have on click on mouse over， so on and so forth， and it's almost the same thing in react native。

 but instead of on click we have on press because as you can imagine it is a mobile phone So the name。

Like name makes sense， right on press on one press on double tab。

Things like that right and instead of a button component。

 we have things like touchable opacity or pressable。

 these are the components that we're going to see later in the video。

Okay let's just speed up a little bit， we have lists in react web development like we do items。

m for each item we would return something so it is really similar what we have here instead we have a component called flat list and here we say this is the data that well like to map through and for each item render this function so we basically get the item and for every single item we would like to return this part it might look complicated but it's actually pretty simple that we're gonna see in the incoming sections then we have forms so instead of using an input element we can use things like text input and instead of on submit we can use on press on the button。

Okay， I hope this gives you a bit more confidence in your react native journey， right。

 it is not really that different than react。Okay， so with this in mind， I have an empty folder。

 let me just go ahead and open this up。In my desktop。

 okay there we go I actually have it I have created an empty folder on my desktop。

 I have called this as Slight app， you can call this anything。

 just open it up in VS code then we would like to open up our terminal and start an expo application So this is the command that you would type NPX create Expo app at latest and I would like to initialize this under the current folder so I'll go ahead and just put dot at the end。

And let me show you the actual documentation that I got this from。So if you visit export。

v created argumentation， this is the Quick Start command that you can get。Okay。

 let's go ahead and run us。This might ask you a question， just press Y and then press enter。

So like in your very first time， it might ask you that。Since this is my like not first time。

 I didn't get that question。Now let's wait for this to complete and in the next section we're going to talk about this codeb。



![](img/3c902dbcec98786b9e863ce7af553dc4_13.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_14.png)

Okay so installation has just been completed in my terminal I can see it says your project is ready and you would like to start it so I'll just clear up my terminal and before we start this application I would like to mention that we have a bunch of different files like hooks components Cons etc we are gonna actually delete all of them and we'll start from scratch because I can imagine this might look really really complicated for a beginner but as I said we will actually reset this project in a second but first I need to mention if you want to follow along with this video Currently you have two different options so you would either install the exppogo application in your actual physical phone so you can visit app store if you are using iPhone or if you have an Android device you can visit Google Play store and just get the exppogo application and then by using this。

We can test out our application。Or you can use a simulator if you are on Windows。

 you would get Android Studio and if you are on Mac。

 you would get Xcode Now since I am teaching you guys I have to show this simulator on the screen so I can just test this out show you the end result in real time I using a simulator but if you ask me this is a lot more harder to get into like why it is just because it'll take longer to install any of these simulators will be more than 10 gigabits but if you install Expogo on your phone。

 it'll take less than one minute and you can just see the end result in your actual phone and let's see how we can start our application in our phone。

So I'll just visit VS code and I'll say MPX Expo and just run this command。Okay。

 so if you are using your physical phone， you need to scan this Q code in your actual terminal and you need to connect to the same wfi like。

Your computer and your phone should be connected to the same Wifi okay and then since I am since I'm going to be running this in the iOS simulator。

 I'll just press I if you are on the Windows you can press a and you should have the Android simulator up and running。

So I can realize like I know we are going really slowly。

 but I just need to make sure that everyone is in the same page， so I'll just press I。

Hopefully this will go ahead， start the expo application on this simulator。And here we go。

 this is the boilerplate application that we got from the export team， so this is what they give us。

 this is the code base and this is the output and let me just put them side by side just like this。

Okay， now here it says go into the app tabs index at TsX。

 so app tabs index at TSX if you update any of these parts。

 so let's say welcome one to3 if I save it。It should restart in real time if it doesn't。

 you can go here in your terminal press R， which means reload and it should reload with the latest version。

 and you can even run this in your browser， so I'll just press W which sends for web browser and this is the actual application right you can build it for the web but in our case you are not really interested in this。



![](img/3c902dbcec98786b9e863ce7af553dc4_16.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_17.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_18.png)

Okay， but just keep that in mind it is actually possible。Okay。

So I hope we get the point now we are going to reset this entire project。

 but I just want to talk about a concept called tabab Navigator。As the name suggests。

 you can get a navigation based off of these tabs， so here we are in the Explorer screen and we are in the home screen and this is possible thanks to this tabs folder which is built into Expo so these are the things that we're going to talk about more later in the video but I just wanted to mention it since we have it already。

Now I'll open up my terminal and kill this with command C。Let's clear this up。

And we would like to reset this project， so they have prepared a reset project script for us。

 we can basically say NPpm run reset dash project and run this。So here it says。

 do you want to move existing files into app example instead of creatinging them。

 so let's just say yes。And run this。And to let me make this screen a little bit larger。Okay。

 so as you can tell， everything that we had previously has been moved into this app example folder and since we don't really want to have any boiler plate code。

 we are going to start from scratch， we can basically go ahead and delete this entire folder we don't really need it and we'll just start with an empty app folder other than this we have the configurations as well as some assets like phones and images。

Okay。So that's kind to bid for the reset project next we can get started with the basics。

Alright so this is where we left now we're going start with the basics of react native and I'll try to go really slowly for the next one hour until we understand everything then we can just really spit up the process if you ever feel we're going slowly you can spit up the video from the settings like from the video settings okay now I' would like to start this application I'll open up my terminal and I'll say let's clear this up if you are on Windows you can just say CLs or clear and if you are on Mac you can say command K which would clear this up。

Okay， now let's say MPX expo。We can run our new application。This is what we had previously。

 so I'll just press R， this should reload it。And there we go。 now I'll visit app index TSX。

 which is our home screen， So it says edit this， let's just edit it， I'll just add one to3。

 let's say there we go we can see the change in real time。Now let's talk about the basic component。

 right basic components， so here we have a text。If you' would like to put a text outside of a text component。

 you are going to get errors， so here it says any text you have。

 it should go under like inside a text component。So we can just say hello， there we go。

 this is coming from react native。And here we can give some styles， as you can tell。

 let me just like delete this。Okay， so style will take an object with any of the fields that you can think of that is coming from CSS。

 so here we say Fl1， justify content and align item center so that it can center it in the middle of the screen。

 but now if you can imagine we might have a bunch of different CSS styles and this will get out of hand so there is another solution。

Instead of having all these， let's say I'll call this as styles。But。Okay。

 styles that container and where is this styles coming from。

 So basically we can say con styles and import style sheet。Style sheet。That create。

Now this style sheet should be coming from react native。Just like that， and we can say create。

This will take an object。 and here we can add the container class。So just like previously。

 we can add those styles， so we had flex1。Allign items of center。And justify content of center。Okay。

 now we can see this is a lot more readable， we can just say styles like container here we can have a text。

 so let's say。啊睇到。You can call this anything， by the way， so this can be even hello。

 but it should make sense。 I'll just say color should be red。Let's say， styleyle。Sles that title。

 Now this will become red。 You can say font size will be， I don't know， let's say 50。Okay。

 so it'll just update in real time。 Now with the beauty of this。

 let's say you have 200 lines of CSS code。 you can basically create a folder， let's say styles。

And let's say we're going to have styles for the authentication page we can just say oath dot Sts。js。

 Now this part is not an extension， This is just the convention that I'd like to use so you can even have this as oath dotjs。

 it is a regular JavaScript file。And this is also a regular JavaScript file， but as I said。

 this is the commission that I would like to use。So I will go ahead and create this file。

 let me cut this， paste this in， and I would like to export this constant。

 let's import the style sheet， save this file， now we can get these styles from that file。

Let's delete this。 I'll say import。Styleles from。Syleles， s。Okay， maybe we should go one up。

Styleles then we have o styles， so it is still working。

 but as you can tell our code base is a lot more cleaner and organized and actually we're going have a bunch of different styles file like bunch of files like these later in the video。

Okay， so we have talked about the text and we could have things like touchable opacity。嗯嗯。Okay。

 just like this。I am a really slow typer， but let's just see。Let's import this。

 we don't really have table， actually， I'll delete that， we have Table capacityacity on press。

 let's just say alert。Tuched。Let's see， you。Touched and here we can add a text in between。

Let's say press me okay， if you press that here we can see we just got an alert and in the same way we have pressable component。

It is also coming from react native and here we have on press， on hover on blur。

 and you can always just go ahead into these components， press control space。

 you can really get all the props that they have。So in the same way， we can copy it。Pasted。

They press me。Presciible。Okay。So it is working in the same way。

 but obviously they have some differences。We're going to be talking about them later in the video。

 but just know that tangibleable opacity gives you this opacity feedback out of the box。

 so can you see it like I'll just delete this。Once I click to it。

 like for a second we have this AD feedback and this is why you might want to use it most of the time and it's actually a simpler component than pressible。

Okay， then we can have like images， let's say we're going to get an image component that could be either coming from react native or expo。

For now let's use the one that is coming from react native and here we could have a source and here if the image is going to be coming from your local files。

 let's say we're going to get this icon dot PNG。Then you need to require it since it is a local image。

 right， Let me kill the left hand side。 I'll say require。And give the exact path。

So I think this is not the correct path， so we should go one up under the assets， under the images。

Do we have logo dot PN G。 Okay， now we don't actually have the logo do PN G。

 but we have icon dot PN G。 And we can get this。 We can add some styles on top of it。Like， with。

Let's say 200 and height as well。Okay， for some reason， it did not refresh it， I'll just say R。Okay。

No， it didn't。Okay， so I have just found a solution。

 I think instead of width and height we should have this style with the width and height。

 now it is working as expected。And if the image is coming from a remote network。

 let's say we're going to get an image from onsplash。So let's grab this image address。

 copypy image address。 Let's go back to V S code here。 in this case， you would like to actually use。

A field called UI and once you paste it。It should work。Let's see why this did not work。

 Maybe we should add some styles。Say width is gonna be again，200。Okay。

 now it is working if you are getting an image from a remote network like onsplash or I don't know any place。

 it should have this UI field， but if it is a local image， you should require it from the。

Like from the relative path。Okay， so I hope that makes sense。

So these are the basic components that we have just explored。

 but on top of these there is a file called underscore layoutot do Tsx this is an actual special file that we should keep in mind we can create multiple layout files in different places so currently this gives us the stack navigator which is something that we'll talk about in a second and here the index at tsx file is also a convention So for your homep pages in different routes you would call it you would call it as index So instead of calling this home do tsx which is say index Tsx and if you had a different routes the entry files would be index Now I know this might sound complicated but we're gonna to see a couple of different examples and anything that goes into this app folderer will become a screen so in our application we're going have。

Bun of different screens like profile screen， notification screen， create post screen， home screen。

 so on and so forth。 and you are going to put all of them into this folder。

Now we have talked about the stack navigator like how does that work。

 let's go ahead and create a couple of different files I will have a profile that TsX and I am using an extension let me show this。

It is called yes 7。React react native snippets。 If you get this。

 you should be able to do it as shortcut R and F。It will give you a functional react native component。

 So let's say this is。Profiled screen。And we can overcase this one。

Then let's have another screen called。Notifications。Thoughd。GSX or TSX actually， we're using Tscript。

Once again， I'll say RNF and let's just say notifications。Screen。

I'll save those Now from the homepage， I will link this， so I'll say a link。

 this is another component here I just get that from Expo router and I'll say visit notifications。

Screen。And let's say H graph will take us to slash notifications， and as you can tell。

 it is a type save out of the box。Let's say from the homepage， we can visit the notification screen。

 I'll click that。Okay， it says no rot point， I think we should restart this with our。

And I'll try to collect it。 there we go Now as you can tell。

 new screens are coming from the right hand side right this is what stackg navigator allows us to have。

 And if you go back now notice how this screen will go from left to right。Okay。

 so new screens will be coming from right and if you want to go back， they will be popped right。

 and this is what sex navigator allows us to have。Then if we wanted to， we can make this。Like。

So not self close tag， I was going to say。 And here we can add different。Screns。

 plus say stack dot screen for the homeage， which we call this as index。

 We can actually hide the header。 So here， if you save it， our header is gone， right， and you can。

Like bring this back。 Let's just say， bring the header。

We can change this name so we can say title will be home because this is our actual homepage。

 or we can call this as feed if this is a social media application and we can visit the notifications page instead of having this as lowercase we can actually change it as well so here we'll say。

Go into the notifications screen and make the title to be notifications。

So here we just uppercase the N， let's save， there we go。And now there is one issue here。

Let's say here I'll go ahead and just say heatather shown will be false。

And you're going to see that content overflows with this status bar that we have at the top and if you wanted to take this into the view always。

 we can just go ahead wrap it with something called save area provider So I'll go here I'll just say save area provider component。

And wrap everything with it， then we would like to have Sa area view component。Let's say。

 import this as well。Grab everything with it。 And now， if we give this some sling。

 let's say not class name， but let's say style。We're going to say flex will be one so that it will take the entire screen and here we go now it is inside the view。

 it is not overflowing with the status bar， so this is something that you should also keep in mind like you can change the background so on and so forth。

This is an absolutely important component that you should keep in mind。

 and we'll be using this actually later in the video。

So now what what should we be doing is to show you this image in our application。

 we're going to have a bunch of different screens right and we're going to have the tab navigator so we'll have home screen bookmarks create notifications as well as the profile screen and now let's try to create this tab with the related screens。

I will go into my B code。

![](img/3c902dbcec98786b9e863ce7af553dc4_20.png)

And if you remember， we had a special folder called tabs。 So I'll go ahead。

 open this up the brackets and just put tabs name in between。Okay。

 this is a special file that Expo will take a look to be able to implement the tabs agator。

Here I'll put a special file once again， which is going to be our layout dot Tsx file。

 then we can put our tabs so we're going to have the profile。I'll just drag and drop it。

 we'll have the notifications。So we are going to have， let's say， what do we have， let's take a look。

 so we are going to have create and bookmarks as well as the home screen。



![](img/3c902dbcec98786b9e863ce7af553dc4_22.png)

So let's try to do it slowly。 We'll have。Create。Dot TsX。

 and we can say R and F to get this boiler plate code。And here we'll also have。Bookmarks， let's say。

Okay， now let's save all of these， I think we can also take the homepage into it。

Which is going to be called as index， right？Let's say， save this。

Now we don't really have an index in the root level。

 so we can go ahead and just add an index file here as well， I'll say index dot TsX。

Let's say R and F， this could be our starter point and all this file will be doing is to redirect the user to the feed。

 which is this file。 So I know this might look complicated。

 but I promise this will make sense just in a second。 let's say from here we will take。

Our users to tabs， Okay， this will take us to the entry point。

So once again this will make sense just in a second now let's try to actually put these colors as well as these icons into our tab navigator so for this we're going to visit VS code under the layout let's say R andF here we can just call this as tab layout。



![](img/3c902dbcec98786b9e863ce7af553dc4_24.png)

You can call this anything， but I think this makes sense and let's shrink the left hand side instead of having a view。

 we are going to get the tabs component from export router and we are going to give every single tab screen So just like in this stackg navigator will say tabs do screen and you are going to put our options So the first thing we need for every single screen is the name and first we'll have the index point which is going be the homepage right this is the starter page that we' have。

 then we are going to have five more tabs let's try to put those I will duplicate it one，2，3。

4 and5 let's say we're going have bookmarks。

![](img/3c902dbcec98786b9e863ce7af553dc4_26.png)

You are going to have create。Or you can have notifications。And I think were can have a profile。

Maybe that was。Like one， two， three， four， Okay， that should be enough。

We have five screens for some reason I put6， but there we go。

 let's save and try to see this in action。 Do we have anything， I'll just press R。



![](img/3c902dbcec98786b9e863ce7af553dc4_28.png)

There we go， we got five different tabs， but now they don't really have an icon。

 and also I don't really want to see this name at the bottom。 we only want to see the icons。For this。

 we can change our options。Here under the tabs， let me just say screen options。

Which is going to take an object。 So here I just say tap bar。Show a label。And all these say poll。

If you save。It should get rid of those names and let's try to change the icon for every single tab screen。

 So for the homepage we'll say options。We're just going to take an object where we'll just say tab bar icon。

 and this is going to take a callback function。 So just like this， instead of returning a text。

 we would like to return an icon。 This is going to be a self closed attack just like that。

 Let's say we are going to get ion。Iコs。Let's say I own icons for some reason this does not autocomplete for me。

 Let me try to get it from Expo vector icons， So Expo gives you different icons out of the box and for the name of the icon well get the home let's save。

Here we can see it has just been updated， but it is super tiny。 We can go ahead， change the size。

 as well as the color。So we'll just take the size as it is， the default size。

 as well as the default color。So let me just zoom out so that you can see the entire line and there we go。

 it is a little bit larger and it got this blue color if you delete this。

 it will be black so it doesn't really get the actual theme。By default， this is blue。

 but we are going to change the colors。Okay， so in the same way。

 we are going to add a couple of different icons， so here let me just give you the name of these icons so you can just pause the video and maybe try to add it by your own。

So for the bookmarks， our icon name is bookmarks for the C， it is add circle。

 then for the notifications， it is heart and for profile， it is person circle。Okay。

 so once you have done this， let's watch my solution where I'll basically copy and paste。

Let's not waste the time， it's the exact same thing then for the create。

Let me get this and let's actually save there we go， it has just been updated and you know。

 as it is focused， the color will change。Okay， for the C， we would like to get this。

 but now here for the color I used something called primary color。

Which is going to be this green color， so let's go ahead and create this colors under a folder called constants。

And I will have this theme do TS file， which you can grab it from the source code。

 let me try to provide this to you it's around 10 lines of code。

 we have a primary color secondary background， so on and so forth， I have prepared these already。

So once you get that， we can import these colors。And use the primary color for this icon。 Okay。

 there we go。 Then what do we want to do？Now let's get the notifications as well。Okay， paste it。

And then，4D profile。So since this is the exact same thing， I don't really want to type this out。

 we don't really need to waste five minutes on these。

 basically we are just returning a callback with this ion icons right okay everything seems correct to me。

But why this is blue and this is green。 Let's go ahead and change the general color on each icon。

whichch is going to be under the screen options on the actual tabs component in the parent component right Now first off。

 I don't really want to see the tabs， so I'll go ahead and add this heatather shown to be false let's say if the tabs has just gone Here we see still tabs。

 but it is coming from the stack navigator so we can go ahead and actually say。Whats the style。

Basically， I'll just get this part。But the style is something that we have done previously。

 will you say heatather shown to be false。Okay， why did not work， I think we can just delete those。嗯。

Wait。Let's just make it to be look like this Okay， so my bad instead of style it should be screen options because we are in the parent component so time to time I can also make mistakes but let's just ignore the fact I'll just save there we go that tab is also gone right？

Now we'll go ahead here and we would like to add some other styles so we would like to change the color right for this we can get the primary color on the tab bar active tint color So if you save if it is active。

 we're going to get this primary color and we can change the inactive color as well， just like that。

Let's save， there we go， it just changed albeit bit， if you can see。

Then we can add like tap bar style。Now you might be asking hey。

 how do I learn all these props well basically as you need them as you build more projects you're going to see and understand all of them more and more so this is what I'm doing as well before I record these videos I just go ahead and experience with most of the things and the most common things that are in the documentation and these are one of those things that I have built already。

So just please don't get overwhelmed， you might be asking， hey， there are millions of things。

 how do I learn every single one of them？So technically， and honestly。

 you don't really need to learn 99% of them only the things that you actually need。 And in our case。

 Tbar style is one of them。 so I will grab this from my notes and paste it instead of typing this out I can explain every single line。

 So here this is the T bar style that we are updating。 let me just save。 Okay。

 we have just change the background color which is make it to be black。 we。

Make the top bar like border top width to be0 position will be absolute elevation of0 and you might be asking what the heck is elevation。

 you can read it， It is basically something specific to Android and I have test out elevation 0 looks a lot better。

 That's why I just， you know ignore that。 Then height is 40。 you can make it to be 80 like double it。

 You can see the change， but I think 40 is pretty cool to or width and we give some padding of bottom of8。

 Okay， these are the styles that we have just added。

Now we are going to make the rest of our application to be in the black background color。

 but we'll just get there step by step。Now what I want to do just basically。

Kill all these and take a step， like take a moment。

 try to understand what the heck is happening in our application。

So everything starts from the app folder from the layout dot TsX this is the first file that is run Okay。

 so here we wrap our entire application with a save area provider and save area view components so our so that our content is always in the save area it is not overflowowing with the status bar and in the index page we are basically taking the user immediately to our tabs folder and specifically into the homepage right this is our。

Homeage let to say， this is the feed screen in tabs。

Okay so whenever you re your application by default you're in this page and from here since we set it up our tabs。

 we can go into the bookmarks right， it will open up this file and render it。

 then we can go into the C notifications and profile screen so I hope this makes sense。

 we are going to fix the styling， we are going to make it actually look a lot better but this is the general idea of our application。

So we have tabs， which send for tabs Navigator and it goes under the tabs folder。

 this is a special folder that Expo gives you， then from here you can change the general styles on each tab and specifically you can do like change the options for the icons。

 so and so forth。So this is what we have done so far。Now。

 just before we move on with the next section， let's go ahead delete these imports and change the background color of our entire application。

 which is going to be under the layout here I'll just say background color。Will be black。

And it should update it and here in react native， the other color formats are also supported。

 so you can say like black， or you can say Hex code right FFF。

 you should save it and it should work like let's do CC。Like it should work。

 you get the point and also our GPBA works I think also HSL works， but in our case I'll just be。

I'll be using this simple black color and you can keep it shorter if you really wanted to。

 you will go with 000， it's the same thing。There we go we have the colors as well。

 and later in the video we'll just see how to change the background color of each screen so with that I'll see you in the next section。

Alright， so this is where we left Now it is time to implement authentication and connect our application to a database and for these we'll be using Cl and convex you can find the link in the description so let's go ahead and visit Cl to implement the authentication first Now I am in the homepage of the clerk if you haven't heard of it。

 it's the most comprehensive user management platform and in this project will be using it to handle the entire authentication flow while making our application completely secure and some production grade applications and companies are actually using it So it is pretty cool and it is really cheap to get started with it it's free right so up to 10000 users you can use it for completely free and probably you will never hit this amount of users So let's go ahead and get started with it I already have an account So just go ahead and visit。



![](img/3c902dbcec98786b9e863ce7af553dc4_30.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_31.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_32.png)

My dashboard， let me just try to quickly log in。And there we go。

 Now we would like to create an application。 let's say create an app， I will call this as spotlight。

 This is the name that I would like to use。 You can call this anything。

 I will disable any other providers other than Google If you really want to。

 you can just opt them in， right。Like， you can。Have all these others providers。 But in my case。

 I'll just be using Google because that's the only thing that we would need。 Let's say。

 create the application。And we have a bunch of different SDKs and guides In our case。

 we'll like to use it with Expo， so I'll select this and let's go through these steps one by one first we'll like to get Cl Expo right I'll open up my terminal。



![](img/3c902dbcec98786b9e863ce7af553dc4_34.png)

Celdes。

![](img/3c902dbcec98786b9e863ce7af553dc4_36.png)

Paste this in。Then the next step is to get the types to make the Tyscript happy。



![](img/3c902dbcec98786b9e863ce7af553dc4_38.png)

Get the type definitions。So once this is done， we can paste that in。Okay。

 so this is what happens if you live in Turkey with a shitty internet connection， but there we go。

 I'll go ahead and paste this in。

![](img/3c902dbcec98786b9e863ce7af553dc4_40.png)

Then we would like to set our environment variables， I'll copy this here they say use a dotV file。



![](img/3c902dbcec98786b9e863ce7af553dc4_42.png)

Now later in the video we'll be using convex and they actually use that enV the logo file。

 which is the same thing， but let's go ahead and create this one， I will paste this in。

 which is the Cl publishable key。

![](img/3c902dbcec98786b9e863ce7af553dc4_44.png)

This is something Ch will use。Just in a couple of seconds。

 so we need to visit the layout and wrap our application with this Cl provider。

Now I'll copy this part and actually all these visit my layout file。



![](img/3c902dbcec98786b9e863ce7af553dc4_46.png)

It should be in the root。Now I can feel this might look a bit。Overwhelming。

But let's just see the reason that I say it's overwhelming is because we have really a limited space。

 font size is too large， but there we go， we got the publishable key。

 which is coming from the environment variables and we can wrap our entire application with this part。



![](img/3c902dbcec98786b9e863ce7af553dc4_48.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_49.png)

Go here。 I'll go ahead， P。My application。And let's get this one。



![](img/3c902dbcec98786b9e863ce7af553dc4_51.png)

Closes this off。 There we go。 We need to import these。 They are going to be coming from clerk。So。

 I'll copy that， and。

![](img/3c902dbcec98786b9e863ce7af553dc4_53.png)

Okay， now let's say this should be happy with us， but we have some more stuff to do。



![](img/3c902dbcec98786b9e863ce7af553dc4_55.png)

Now Cl stores the active users session token in memory by default， and in Expo applications。

 the recommended way to store sensitive data， such as tokens is by using Expo secure store package。

 which is going to encrypt the data before restoring it。

 so we are going to go ahead and install this to make our application a lot more safe。



![](img/3c902dbcec98786b9e863ce7af553dc4_57.png)

Let's paste。Oops， so what have I done， Let's just paste it。 I think I have just done a mistake。

 Let me just。Copy this once again。

![](img/3c902dbcec98786b9e863ce7af553dc4_59.png)

Clear up the terminal and paste this in。Next， we would like to create a cache thatTS file in our root directory。

Let's copy this。

![](img/3c902dbcec98786b9e863ce7af553dc4_61.png)

So these are just some steps that we are doing that we are never going to be thinking about it later。

This will make our application completely secure and authentication will work flawlessly。

 so we have 30 lines of code， which is something that Cl needs to be able to get the token as well as save the token to handle the authentication so you don't really need to understand everything that is going on here there is a lot of magic that is happening behind scenes。



![](img/3c902dbcec98786b9e863ce7af553dc4_63.png)

Okay， then now that we have got this token， we're going to go ahead add this token cache into our clerk provider。



![](img/3c902dbcec98786b9e863ce7af553dc4_65.png)

So I'll copy this part。Save this file， go into layouty， and here you would like to。Oops。

 what have I done， let's say token cache and we're going to get the token cache from this cache pile that we had and I think our application should be ready to go here they have a bunch of different steps that we'll be doing in a couple of minutes。



![](img/3c902dbcec98786b9e863ce7af553dc4_67.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_68.png)

Okay， so with this now in our entire application， we have clerk initialized and we can use the authentication。

 so let's see。We would like to build the authentication page so you can get these designs。

I think I forgot to add the authentication screen but let me show you this pretty quickly so I have just added right here。

 this is the authentication screen， let's take a look at it， we have an icon。

 we have the title a P tag maybe a description an image as well as our authentication button so let's go ahead and design this then we are going to make this work with the clerk。

I'll open up my UPSS code。Here I would like to create an authentication page。

 so it's not going to be a part of the tabs because as you can tell。

 we don't really have the navigation for this page。

Or for this screen I should say we are not in the web development， so we don't really have pages。

 but instead we have screens and let's start with the authentication。

 I will create this folder and here we can put a log the TSX file and here we would like to basically have our styles first then we will implement the functionality。

Now here this is not a CSS course， that's why I would like to skip this styles part here we have a oath styles dot Js file and let's actually make this to be a Tpescript file I'll just say。

Bothath styles。 yes and I will provide this file to you so you can grab this from the Giub repo and let me show you the entire page。

If you want to type this out， so we are getting the colors。

 we are getting style sheet as well as dimensions， where we will just check the width and height of the screen here we have container brand section basically this is some CSS stling just to make our application look clean and nice。

Okay， so I don't really think we should be spending 10 minutes to write all these classes。

 that's why I'll just provide them to you。Okay， this is super simple styling once again。

With this in mind let's go ahead and actually try to build the login page， I'll just get R and F。

 let's try to save this file and actually try to build the content。

So here I'll shrink the left hand side， we are going to have a view with some styling。

 let's say style will be styles that container and these styles will be coming from O Sts file。

Then we will have the brand section， so go ahead， say brand section。And。

Let's just say we will have a view。Let me please get this and I don't really want anyone to get mad at me just because I copy and paste but this is really really basic stuff that we have seen a couple of sections ago we are having a view with a style an icon and some text so there is nothing logic here that's why I would like to copy and paste and walk you through it so typing this would take three minutes explaining would take 30 seconds。

Okay， I hope this makes sense Now we got the brand section。

 let's save and try to see what we're going to get。 Currently we are in the feed screen。

What I want to do， just go into the actual index。File。

 and for now I'll just take my users to the authentication， so let's say oath。Maybe to or人。Okay。

 for some reason， we cannot get。The type safety。Maybe we should start our application。

I'll just say MPX expo。Press or。And。Make it look like this。😔，Okay， we have O login。

 I forgot to wrap this with Princes。Now I'll just reload this once again， it should work there we go。

 this is what we have in the authentication page specifically in the login page we just added the brand section now we would like to have an illustration where we'd like to get this image so I've got this from a website called Story set。



![](img/3c902dbcec98786b9e863ce7af553dc4_70.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_71.png)

Let me show this storyet dot com。 It should be。

![](img/3c902dbcec98786b9e863ce7af553dc4_73.png)

And I think I got it from the bro styles。I search for something like social。

And let me actually provide you the actual link So I have just grabbed a link， let me paste it。

 It is storyet。com slashillusration slash onlineline wishes slash bro It's funny name。

 but there we go This is the image that you can go ahead and download it then put it into your assets or you can simply grab it from the Gi revo So under the images I would like to get this image。



![](img/3c902dbcec98786b9e863ce7af553dc4_75.png)

From the source code。So I'll take the outhBG2 this is what I have called it and just like if you want to use different images。

 I have prepared two of them as well， so o with BG3 and one， I would like to use this one。

 but you can use any of the others that we have。Alright。

 so we would like to get the illustration now it is your challenge to go ahead and display the image on the screen。

So we have seen this previously， since it is a local image。

 we need to require it in the image source， so here Ill is say illustration。And paste it。

We have an image let's import it from react native and under the source we are going to get this image since this is a local image。

 we need to requirequi it， right， let's save， there we go。

 this is what we got you can use cover or contain since basic CSsS， I'll go with the cover。

And after the illustration， we can put the login section basically where we have the button， right？

I would like to once again copy this and paste it。And please don't get mad。

 this is super basic stuff that we have seen so far like W， touchable opacity， style， on press。

 like this is something that we haven't seen but name makes sense like on press we don't have this function let's leave it as an empty function for now。

Would you say console log。Okay， let's say this is what we got with the sling。

Now we should be able to make this work currently if you click to it， we just see a console log。

 but we are going make it work with Cl and specifically with the Google authentication now when we click to this button instead of doing this dummy operation let's actually call this function handle Google sign in which is something that will create above so let's say cons handle Google sign in。

 this is going to be an asyncarrow function and here we would like to do something which is first we need to get something from use SSO from Cl so use single sign on and here we would like to get start SSO flow and here I would like to get the router just like and react but this is gonna be coming from let's say Expo router this will allow us to do navigation manually。

Here I would like to have a try catch block here in the try we would like to say a wait start SSO flow and our strategy will be o Google you can see there are a bunch of different options but in our case we're going with Google and this will give us a couple of different things which we can these structure like we can get the create session ID as well as set active。

So all these are coming from the clerk documentation。 Please feel free to check this out。

 let's say set active。 if we got this and if create session I existed。

 we would like to say set active with the session created session I This will basically。

Authentate the current user。 And once we are authenticated。

 we can just replace the current screen with the homepage， which is gonna be tabs， right， Okay。

 just like that in the catch， we can just put a console log。And we should be good to go。Let's say。

 this is gonna be error。Okay， I'll save and let's click to this。

Here we go it says Expo wants to use gogle。com， let's just say continue。

 we should be able to see our accounts， so these are the things like these are accounts that I have added previously and the language is Turkish at the moment。

Let's just make it to be English so that everyone is happy。Okay。

 so let's just try to log in with this one。 let's say continue。Okay， since we are。

 since we are just authenticated， it takes us to the。A feed page， right。

 we just go into the home page。

![](img/3c902dbcec98786b9e863ce7af553dc4_77.png)

Or home screen， I should say， if you visit your dashboard。

 you should be able to see that you have a user that is just logged in。

 which means everything is working correctly。

![](img/3c902dbcec98786b9e863ce7af553dc4_79.png)

Okay， but now if we restart our application， what is going to happen？

It will still take us to the authentication page it is because in our root layout let me close everything in our root layout we don't really have any check for the authentication right we always take the user to the login page or login screen but we should fix it right in our root layout before our application started we should check if user is authenticated or not depending on that we should take the user either to the login page or to the related page right so for this I would like to go ahead create a component so that I can put the logic。

Specifically into that file， sos see components。The name that I'll come up with will be initial layout dot TsX。

 you can call this anything， but I think this makes sense， so let's say R and F。

Wwhich will be a functional component and here we don't really have anything related to react native because we are not going to return JSx right let's use a delete this。

 this will be a component where we handle the authentication and navigation let me zoom in once again Okay so first I would like to get some stuff from use oath from Cl so why can we get from here。

 let's say we would like to check if。Cllek is loaded， right， you can read the description。

 a bulloleion that indicates whether clerk has completed initialization。

 initially it is false and it'll become true once Cl loaded and we can check if user is signed in or not。

Then we can get the segments。Let's say， use segments。And you're going to see what that means。

Basically， it will give you the segments of the current screen， so if you're in the home screen。

 if you're in the login screen， you know if you're in the notifications。So on and so forth。

We're going to see this in a second and let's say。Okay， we'll get a router。

I'll say use router coming from Exp router because as you can tell we'll be doing some navigations and here I would like to have a use effect coming from Re。

 even though this is react native， we can still use Re。As you can tell。

 we have talked about it previously， it is really really similar to react on top of react。

 you just have a couple of different concepts right and now in this use effect we would like to check for some stuff so first of all I'll say if。

Clek is not loaded。Just return， don't do anything。 and here we can add is loaded。

We'll say is signed in。And we can add the segmentss。 So if any of these changes， right。

If any of these changes， this use effect should run once again， and now I'll get a variable。

 I'll say if you are in the oath。Page。And this is how we can check for it。

 would you say if segments of the first item is equal to oath。

 if this is the case that means you are in the oath page and since we don't really have pages。

 let's say in oath screen。Let's say if user is not signed in and if user is not in the oath screen。

 which means they should be navigated to the homepage or to the login page。

 my bet will say Roger replace， take them to the login page and in the same way if they are trying to cheat。

So， let's say else if。Oops， let's say else if user is signed in and if they are still trying to visit the login page。

 we are going to just take them to the home page right and at the end we'll say if。It is not loaded。

 we can just return。Now or we can return a load component。And here。

 if everything is done successfully， we can just return。Be sack。

Let's get this and we'll just say screen options header shown to be false。Okay。

 so if user is authenticated and if they visit let's say home screen or if they visit notification screen。

 we are never going to hit any of these if checks， we will just take them to the related screen and now we'll go ahead into this layout instead of having this stack we will have the initial layout so previously we had stack as it is。

 but now we have put it here on top of it， we have added the authentication logic that will do the navigation。

So I hope this makes sense。Let's get the initial layouthou。

Save it and now here we can see since we are logged in， it takes us to the homep page。

 I'll go ahead and refresh。Like we are by default in the in the home screen。

 even though our index file says take the user to log again， right？Since initial layout runs。

We are in the actual home screen Okay so let's quickly close everything and reiterate what we have done so far then we'll just move on with the next section So we have set it up clerk we just need to get some environment variables we need to set up this cachet Ts file which is something that we don't really need to understand completely this is something that clerk needs to be able to handle the authentication securely and then we have built a login page with a really cool design and we have added this function called handle Google sign in where we just use the clerk functions and once you are authenticated we take the user to the homep page and in the initial check we have a component called initial layout that will do the authentication navigation right if user is not signed in and if they are not in the oath screen they should be navigated to。

The oath screen in the else case， they should be in the tabs page and if none of these are correct then we are gonna hit this return statement where we'll show the related page okay and we have wrapped our entire application with these clerk providers and we have the initial layout check in like in the root layout right Okay so I hope this makes sense this might look a little bit complicated。

 but if you think about it if you go step by step about this code base I think it should make sense。

So I would say pause the video and take a look at the code base， try to see what we have done so far。

 it should take around five minutes and then in the next section we're going to go ahead and integrate a database to our current application。

Alright， so this is where we left， we have integrated Cl for the authentication and now it is time to have a database and for this we'll be using convex。

 you can find the link in the description， they have a free plan that we can use just like Cl。



![](img/3c902dbcec98786b9e863ce7af553dc4_81.png)

So let's go ahead andvis that。Before we try to log in and create an application just know that conVx can be used as your entire backend and actually in this project we'll be using it as our database which works in real time out of the box and we'll be using their file storage to be able to store our files such as our post images right and there are a couple of different concepts like queries。

 mutations， actions so on and so forth well get into them right so I would like to just go ahead and log in。



![](img/3c902dbcec98786b9e863ce7af553dc4_83.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_84.png)

If you don't have any account， go ahead and create one。

 you don't really need to pay anything once again， you can create a project form here。

 but what we would like to do actually create it from the terminal So I'll open up my terminal let's kill this with command or control C and clear this up we would like to say NPpm install。

Oops， let's say NPpm install convex。And by the way， you can take a look at the documentation as well。

 let's say documentation。convex。 devv。They have a bunch of different SDK in our case we would like to have react native with expo。

 so we already have an expo application， we would like to just install convex and run this command let's see what this will do in the terminal。

NowNow that we have this ready， let's go ahead， paste this in。

If you are using this command for the very first time。

 it will ask you to log in to your ConVx account， but since I am already logged in。

 it askeds me to create a new project or choose an existing one。

 I would like to create a new project so I'll just select this press enter now。We can give it a name。

 so I'll just say Spotlight app， let's just how to accept that。

And we would like to deploy this on a cloud， I mean cloud environment， so I'll just select this one。

 it will go ahead and create a project for us。Now it says it is ready， let's take a look at it。

There we go in real time it works we got the Spotlight application。

And here we don't really have like any tables， but we would like to create a couple of different tables。

 right， such as one for users， posts， notifications， likes， so on and so forth。Okay。

But first we need to handle the authentication as well。

 so what do I mean you might say okay we already handled that right， we got the clerk， it is working。

 so that's correct， but we also need to connect that authentication service with our database because at the end of the day if you think about it。

 Cl and convex our two different services when someone signs up with Cl。

 we need to let our database know about that user so that we can store it in our database。

So let's try to see in the documentation， we are going to take a look at the。Authentation。

 specifically with clerk。Okay， so this tells you to go ahead sign up to a clerk。

 this is something that we already done， we have created an application and now it says you should create a JWT template。

 so let's go here under the configure and make sure you selected the correct application。



![](img/3c902dbcec98786b9e863ce7af553dc4_86.png)

So configure JWT templates， create a new one that is matching with convex。Okay。

 just copy this issuer URL， save this， and let's take a look at the next step。



![](img/3c902dbcec98786b9e863ce7af553dc4_88.png)

They tell us to create an O do conflictfig that T has filed， and by the way。

 when we run this command。

![](img/3c902dbcec98786b9e863ce7af553dc4_90.png)

I don't know if you have realized it， but we got a convex folder。

 which is the place that we're going to put everything related to our database。

Which is convex database， right， So let's go ahead and first handle the authentication under this o do config dot yess file。

 So I will paste what I have copied。For a second， we'll be using it and copy this entire thing。

Paste it below and we would like to change this part with what we have right here。What's cut it。😔。

And paste it。 Okay， this should be good to go。 This is something that we had to do around eight lines of code。

 Let's close this file。 Let's see the next step。

![](img/3c902dbcec98786b9e863ce7af553dc4_92.png)

Okay， they tell you that you should be running this now to be able to deploy your changes。

 but we already have this open right， now it just says convex functions are ready。

So keep this in mind from here and out until the end of this tutorial。

 you would like to have two different terminals open one would be running this NPX convex step。

 so every single time we should have this。NPX convex tab running because when we add a function that is related to our database。

 it will deploy our changes to convex and then we are going to run our application。With NP P X expo。

 right， I'll just run this in a second。 But first， let's see the other steps。

 So here this is the guide for。Ck react， but in our case we are using Expo。

 so we don't really need to install this， I believe， let's try to see how we can make this work。

Like they can like you can see in the main TsX， they wrap the entire application with Cl providerder as well as convex Proder with Cl。

 so let's try to do this， but instead of app we would like to wrap our layout right our entire application。

So I know this might sound complicated， but let's just try to see it。I would like to wrap。

Or I would like to create a folder called Pro。To keep our code base clean。

 and I will say clerk and convex Pro， the Tsx。So basically， instead of having this clerk。Logic here。

 I would like to take this and put it into into its own file， so let's try to build this file。

So let's try to build this file。 I promise it'll make 100% sense。

 So I'll just say R and F to get this code， let's delete this imports。

 We can delete this return statement instead of。A view will like to get the clerk provider。

It is going to be coming from Cleric Expo， and this is the exact same thing。 What we have done here。

 we would like to get the token。As well as the publishable key， let's try to import these。Basically。

 I'll just cut this from here。Get it。And then let's get the token cache。Get the clerk provider。 Okay。

 now inside of this， instead of just having the clerk loaded。

 we would like to have the convex provider as well。 So say convex provider with clerk。

I think it should be。Provider with clerk。Just like this and we will be importing this。From here。Okay。

Now this gives us an error because if you take a look at the documentation。

This takes a client as well as a use oath。 So let's try to add those here or say use oath。



![](img/3c902dbcec98786b9e863ce7af553dc4_94.png)

We we will get the use of from Cl Expo， then we would like to add a client。

 Let's try to create it above。I will copy this， so this is coming from documentation。

Convex react client should be coming from。Convex react okay just like this， let's try to import it。

 there we go and we are using a public convex URL， this is coming from the that EMV dot local When we run this command in our terminal we got these environment variables。

Okay， just keep that in mind， I forgot to show you this。

 but these are the things that we have in the that the NV file。Okay。

Then we'll go ahead and add this Con client。Right here， then we can just say once clerk is loaded。

We can wrap our children with it， and this children will be coming。Here， as a prop。

We can say children will be type of react node。So what we have done so far is basically we took this entire part。

Put it into its own。While into its own component and on top of it， we have integrated convex with it。

 right， so we can basically go ahead and delete this part completely。We can delete the token cache。

 these imports， and we can wrap our application with the clerk and convex provider that we have just created。

Now in our entire application， we can have the clerk and convex working together。

And we have take this logic， put it into its own file so that our code base is a lot more readable and。

It is like organized。Okay， so with this in mind， let's try to delete this stack and save this file。



![](img/3c902dbcec98786b9e863ce7af553dc4_96.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_97.png)

Alright so we are making a really good progress so far。

 we have integrated authentication as well as a database Now you might feel like we are going a bit slowly。

 that's correct， but we are actually building a real word application right so we just need to take care of every single step slowly so that we all understand everything that we do now we have database as well as authentication system。

 it is time to maybe just go ahead and define our tables so I have said we're gonna have tables for users posts。

 comments， so on and so forth right and since it is related to our database we're going to go into the convex folder and we will define our schema so let's say schema do yes this is a special file that will make our codebase to be Tafe so if you don't know what that means itll basically give us auto completions。

That we don't really have any errors in our code， So it'll just be typeafe as the name suggests。

All at so let's just try to see how we can define our tables， how we can define our schema。

 I'll say export default and let me shrink the left hand side。

 we' are going to say define schema which is a function， let's say let me just delete this。

This is a function coming from convex， I don't know why it did not import it by default。

 but it should be coming from convex serverver this will take an object and here we can define our tables。

The first table that I'd like to have will be users。 So you say users define table。

Say define table just like this it'll be coming from the same import from conVx server。

 this is a function that we're going to call and we're going to put an object with the fields that wed like to have so each user will have a username and this is gonna be type of string but this is how we can do it we'll just say V dot string and we need to get this V from conVx values which is our validator。

Okay， then each user will have a full name， so let's say V does string is well。

 So if this is something like ajan。This will be the full name version of it。Like this。

Then we would like to have email for every single user oops， let's say V string。

 every single user will have a bio， but this could be optional， right， so I might not have any。

BioSo I can just say be that optional and it will be type of string。

Then each user will have an image， this could be optional。

 but since users are logging in with Google， they will have an image anyways。

 so I'll just remove the optional field and let's say each user will have some followers which is going to be say V number will just store this as a value in the same way we will have number of followings。

And in the same way we will have the number of posts then finally I would like to get a field called Cl ID which will be type of spring Now why do we store Cl ID in the user's table So if you think about it Cl and Convex are two different services right we have talked about this。

When we authenticate with Cl， when we sign up with Cl， we will save the same user to our database。

 so let's say we got the user that is just signed up with clerk will like to save it to our database and we would like to keep a reference to this user so well just add a Cl ID。

 what it corresponds and the clerk service right and。This is the field， how we can do it。

When user signs up， we will add the clerk value of this user and by default。

 users will have a field called underscore ID， this will be given by convex。

 so if you have used Mongodb previously it would do the same thing so here convex does the same thing and it gives you a creation time field as well by default。

 which is the created a。Okay。Now we would like to add some indexes which would help us for the querying later in the video so we can just get a user by their clerk ID right。

 so I can just say add an index， you can call this anything。

 I'll call this as a by Cl ID and the fields that we would like to query with will be Cl ID。

So basically， later in the video， we'll say， hey， give us a user， so let's say an example。

 let's say get user by。Clork I D。Okay， let's just get this。Let's say we're going to call a function。

 and we're going to put the clerk ID， let's say this  one23， and it will give us the user。

With this clerk I， I hope that makes sense， basically index is used to have some querying。

 it'll just make it faster。And then we can add our other tables so I would like to just grab and paste them one by one and I would like to walk you through it line by line so we have the post table just like what we have here we will define a table each post will have a user ID this is the owner of the post then each post will have an image URL because this is an application like Instagram we have to have an image and we would like to store a storage ID now this will be needed when you want to delete a post and the type of this will be storage ID this is something that will get later in the video and here the user ID if you have realized this type of like user ID if you delete this part you can see it should be typeafe Currently it isn't。

I don't know maybe in this schema we don't really get it。

 but in other files we will actually get that then each post will have a caption but it'll be optional so you don't really need to add a caption and we're going to store the number of flags as well as comments then we're going to get like we are going add an index we will just say hey give us a post by user and we're going to pass the user ID it'll give us the post that match with that user ready so if this index stuff doesn't make sense once we use them I think it'll be clear。

Okay then we' would like to store the comments right， I'll just put the comments table。

 let's define it， each comment will have an author which will be the user ready and each comment will be made on a post right so it will be related with a post we just put those types those fields and then we add the comment content itself and again we just add a query。

Then we'll like to store the number of likes， right？Or like I should say。

 we are going to have a likes table， and I'll just put it above the comments。

Let's put a comma here okay we'll have a table called likes， whenever we like a post。

 we are going to create a like document which will have a user ID and post ID Use ID is the one liked right。

 so it is the author and the post ID means which post that we have liked。

Then we can add some indexes now please let me just grab those。

We should be able to query a like with the pulse ID and。So I should say。

 and then we should be able to get with the user and post data。 So once again。

 if this doesn't make sense， I think it should be really， really clear when we。

When we reach to the end of the tutorial， because we'll be using these indexes and it should be really。

 really clear。Then let's get the follows table in the same way we would like to have a couple of different indexes。

 Let me go ahead and put it below。So we are defining another table where we have a follower ID and following ID。

 so let's say we have two different users John and Jane。Now if John。Let's say John follows Jane。

 That means John is following and。Sorry， John is the follower right it follows the Jane and Jane is the following When John follows the chain。

 we will create a follow document， we will say follower ID。

 we will put the John's ID and following ID would be Jane's ID Now I'm just explaining it really slowly it might be your very first time building a social media application。

 so I feel like I had to explain it。Then we add a couple of different indexes that we'll be using later in the video。

Okay， then we would like to keep track of the notifications。

 so when you like a post or when you comment on a post or when you follow someone。

 we would like to send a notification， so let's create this table I will say notifications define a table with these fields so each notification will have a receiver as well as a sender and we will store them as IDs。

Now notifications will have three different types either like comment or follow。

 so you could simply go ahead and just say be that string， this is also acceptable。

 but just to make our code a bit more clean， we can just force this right。

 we'll say it'll be union type。And it will be one of them， so be that literal。

 it could be either like。Comment or follow then the like it will have two different fields。

 one post ID and one comment ID。 Now these are optional。

 it is because if it is a follow notification， it is not related to any post so it's not going have any post ID and it will not have a comment ID as well。

 but if it is a like or if it is a comment notification， it will have these。Fields， right？

And here once again we add an index， so we have one last table， let me save to get this formatting。

 and by the way， whenever you save， it will take a look at this file and try to deploy your functions to your convex dashboard。

Okay， so the very last table that we'll have will be bookmarks， let me just paste it。

 whenever we bookmark a post， we will create a bookmark document with these fields。Okay。

 so I can definitely feel this might feel a little bit overwhelming。

 but basically these are the tables that we'll have in this tutorial in this project。

 and we'll be using these indexes。O。Let's save。And take a look at our dashboard。



![](img/3c902dbcec98786b9e863ce7af553dc4_99.png)

If you。Like if you say generate schema， I don't know why we didn't get that。

 but let's refresh this page。

![](img/3c902dbcec98786b9e863ce7af553dc4_101.png)

Okay， so I think I have visited the production。嗯。I should be visiting the development right let's take a look at this instance。

 if you take a look at the data， you should be able to see all the fields like all the tables that we have and if you say show schema。

Like this is crazy， the code that we have just written in our local machine is now accessible on the web in the Conx dashboard。

So these are this is the code that we have just written。And in the same way。

 we should be able to see our functions。Right here， but currently we don't really have any functions。

 which is something that we'll build next。So I have just said we are going build some functions and specifically convex functions Now you might be asking what is a convex function well basically any operation that we need that is related to our backend for our database we are going build a function to give you some examples let's say if we want to get some posts right if we want to do a get request we are going to be writing a function called query and it will you know give us some response so here itll return us the posts and in the same way we have a different type of function called mutation where we can use this for create update and delete operations and here are some examples if you want to create a post we are going build a mutation if we want to update a comment we're going build a mutation and in the same way if we want to delete a post we're going to build a mutation for it so the first mutation that I would like to build。

Is to create a user right let's say create user This is gonna be a mutation that will write in our convex backend and you might be asking why this is the case So let's just take a look at it on a diagram so currently this is the state of our application which is signed up with Cl right we have the user under our Cl dashboard but we don't really have a user in our database right if you take a look at it。

 we don't really have this user so we need to take that user and create it in our database as well and how can we make this happen Well there is a concept called web hooks which is something really。

 really important for you to understand this is not specific to react native or this is not specific to this application only this is a general concept every web developer should know so let's just see what they are in the first place they are automated messages that are sent when something happens。



![](img/3c902dbcec98786b9e863ce7af553dc4_103.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_104.png)

And in our case that something is when a user created， so I will say， hey convex。

 when a user signed up， just send us an event to our database。

 we're going to take that user and save it to our database right so there is an event that clerk has called user created and you are going to listen for this event and this will send only once for every single user because they can only sign up once and like later they can just only login so I hope that makes sense it will send us an event that is called user created and with this event they will also send the user information such as their full name email profile image。



![](img/3c902dbcec98786b9e863ce7af553dc4_106.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_107.png)

Username so on and so forth and we are going to take this user and save it to our database and let's try to create that function called createre user so I'll just visit VS code。

 let's kill everything under the convex I will create a file called users that yes and everything that is related to user table。

 we are going to put it here on this file。And let me just show you the documentation as well。

 so I'll just say convex functions。Let's go here， take a look at it。

 just in case if you wanted to check this out after completing this tutorial。

 so just remember that everything is actually coming from the documentation。

So here we can see there are three types of functions that I have mentioned。

 one of them are queries then mutations and also there are actions and you would use actions when you are talking with thirdpart services such as Stripe。

 open AI so on and so forth Now let's just try to build our very first mutation so this is the like syntax that they would give you let's just copy it。

 I will paste it into VS code but we're going to obviously change it。

Well let's actually delete everything that we have currently。Just。I don't know why I copied it。

 but let's go ahead try to build it from scratch so we have a function you can call this anything in my case I'll say create user This is gonna be a mutation which is a function that we call and it takes an argument so here we can take some arcs let's just say if you wanted to create a user user should have a couple of different fields one of them is username and if you want to see all the fields that we have these are the things that we should take as an argument right。

So let me just get them pretty quickly we're gonna to get the full name for the user because I think this is what we have in the schema then we are going to have an image we're going to have a bio so these are type of strings this is also type of string but there is one thing this is optional right when user signs up theyll not have a bio so we're going to add the email as well and finally the Cl id Now this is not really happy with us because we need to add a handler function that will do thelog so let's say async this is gonna to take the context as the first argument and then we're going take the arcs。

Now you might say what is this context is all about so by using this context you can interact with your database as well as check the authentication and to this arcs you are able to access to these arcs basically so let's go ahead and just say a await so basically we are trying to create a user in database so we'll say a await context。

 Db。 insert。Let's just find it and we would like to insert something into the user's table and here we can see it is typeySa right if you press control space。

 you can see all the tables that we have we would like to go under the user's table and we're going to add all these fields that we have such as user name。

 full name， let me just accept everything。So these are the arguments that we have above right。

 and on top of these we would like to add the default fields， such as the number of followers。

 following and posts when users sign up by default， they will be0。

OkayNow just before we create the user we need to check if it has already existed， right。

 because there might be some mistakes and this function might be called to for a user。

 so we're going to check if a user existed already or not。And let's do it， let you say。

Well actually before we assign it， I'll just say wait context that DB。

 we would like to query something under the user' table and we are going to query it with an index。

 so I'll just go here I'll say dot with index and we have created an index called bycle ID and these are the other indexes that Cl gives you so if you take a look at the schema this is the index that we have added under the user's table so we're going say with index called by Cl ID and here we are going to pass a callback function。

Where we will take the query， so we'll say query do equal to Cl IDd if it is equal to this argument。

 and this is going to give us a result where we can fetch it with first or unique。

So it's the same thing。 I'll go with first。And we will assign this to a variable called existing user。

Just like this。And I will say if。Existing user， right if we have a user just return and don't do anything。

 but if user is not existed， we're going to go ahead and create the user in the database so I hope this makes sense。

Now we are able to see how to create an index as well as consume it。

We basically get a user with the Cl ID， and this clerk ID is coming from the arguments。

Okay so we have created this function， but how can we call it right。

 we just talked about it on a diagram when someone signs up with clerk。

Clark needs to send us this webbook event， so we just need to set this up and you can take a look at it from the documentation。

 but let me just walk you through it。

![](img/3c902dbcec98786b9e863ce7af553dc4_109.png)

We'll go under the dashboard， under the configurefi。We just need to find the web hook。

So where is that， I think。So for some reason I cannot see it， let's search for it， we hooks。

 okay there we go under the developers。We would like to add a webbook and specifically an endpoint。

 So let's say。To be able to add this end point， we just need to get our convex URL。



![](img/3c902dbcec98786b9e863ce7af553dc4_111.png)

Under D dot and V。So I will go ahead copy this entire thing called ConVx URL and just go here paste it Now if you are adding an endpoint for web hook instead of saying cloud this should be site and you might say how do you know this well basically once again from the documentation let's say HtP actions conVx。

 there we go。

![](img/3c902dbcec98786b9e863ce7af553dc4_113.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_114.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_115.png)

They tell you that you should use site at the end。

![](img/3c902dbcec98786b9e863ce7af553dc4_117.png)

Okay and then there should be an endpoint that I'd like to listen， I'll just call this as Cl webpo。

 you can call this anything literally like hello but it shouldn't like it should make sense right so I'll just say Cl webpo in the event that I would like to listen to here we can see we have all bunch of like all kinds of events but I would like to listen for user doc created。

Okay， I'll just go ahead at this。And we just got a signing secret。

 so this is really important we should copy this and add this as an environment variable。Now。

 instead of adding it into the enV file， we will go ahead and add it into our convex dashboard。

 so under these settings。

![](img/3c902dbcec98786b9e863ce7af553dc4_119.png)

Under the environment variables， we're going to say clerk the book secret and add this value in your case it will be different。

 please use your own because I will delete mine before I publish this video。

Let's go ahead and save it。Okay， so now that we have set this up。

 let's go ahead write some code to make this work， and I need to mention something。

When clerk send us an event， we are going to take the user and save it to the database。

 but now think about it， everyone can send you this kind of an event right。

 we could have a malicious user like it'll just send you this event millions of times and in that case you just need to make sure that this event is actually coming from Cl so with this in mind let's try to write our code。

So I will create a file called HttP do T， and we are going to build a logic in this file。

 So I would like to get in like get a package。Let me just say NPpm install S V IX。

 which is used to verify webpos。 Okay， so let's wait for this to be installed。 There we go。

 We just got that。And I don't have the X application running， but I'll just run this in a second。

Let's try to build this file first Now first I'll get a couple of different imports from KVx and we're going to get this web hook from SVIX package。

 so let's create a router I say con。H TTP。H TP router， and you are going to call this。 Now。

 I promise this code will make sense once we complete this file just for a couple of minutes。

 bear with me。 So we'll say H TP dot route。You are going to create a route and this will take an object where we'll say path will be equal to what we have just created。

 which was slash clerk， slash webpo， So if you have created this something， you should put that name。



![](img/3c902dbcec98786b9e863ce7af553dc4_121.png)

In my case， this is what I have done， right， clerk webbook。



![](img/3c902dbcec98786b9e863ce7af553dc4_123.png)

Let's go back and then the method type， it'll be post as well as the handler function。

So this is the logic that we're going to put。And I'll just put it in line if you want to。

 you can create a function outside， but it is not really important。This is not how it'll look like。

 let's say it will be an HtP action where we willll take a callback function just like this。

 I believe， and instead of calling this wreck， I'll just call it as request。

Okay now let's go ahead and create our function logic。

 So first things first we just need to check for the environment variable if it existed or not。

 let's say con web hook secret let me just copy this and pasteed because I'm really slow typer and I don't really want to waste too much time so we go under the process that emv and search for Cl web hook secret and you just need to make sure that this is matching with what you have typed here right it should be exactly the same otherwise it will be undefined and here will just say if this web web hook secret is undefined we just throw an error and then we just need to check for the headers So as I've said。

 we just need to make sure that this web hook is coming from Cl so let's go ahead and first check the headers so in this request that headers there will be sviX ID signature as well as the timestamp and if any of these values are undefined。

Then we are going to throw an error just like this or the response will be 400 and we willll just say like no S viax headers font。

 but if we have the headers， we can go ahead do something else we're going to get the payload from the request and we're going to get the body out of it just like this and then we' would like to create a web hook。

 so you say con web hook we're going to call this class that we have just above。

And we're going to put the webpo secret in it。 then let's just say let event。

 this could be type of any for now let's just leave it as it is and we'll be using this event。

 Now I'll have a try and catch block here I'll just say verify the webpo。

And this is how we can verify it。 Let me please go ahead and get this So we say。

A web hook that verified here is our body and here are the headers if is if this doesn't throw any errors。

 which means it is verified successfully but if it throw some errors itll hit the catch block where we'll get the error and throw a response so so far what we have done is to check for the environment variable check for the headers and verify the webbook okay so this is what we have done if everything went well so far we can go ahead and actually save user to the database and I would like to get the event type from this EVT that we have just created above and here we can see I was going to say this should be typeafe we can make it just in a second let's say event that type。

And we'll just check for it so I'll say if so I have just accidentally pause the video let's move on I was going to say if event type is equal to user doc created。

 we are going to run this block where we can go ahead grab all these fields that we have coming from clerk so we'll basically destructure it from event data we are getting the ID now here we have email addresses but we're going to take the primary one so here is how we can do it we'll just say con email because in a clerk account user might have bunch of different email addresses we're going get the primary one and then we can get the full name so they have the first name and last name we can combine them together right and then we can basically run a mutation oops let me just go back we'll have a try catch block in the try I'll say await context that run mutation and。

We'll just say API this is something that we have imported previously。

 This is coming from the generated folder from convex and this is a folder that you don't really need to think about。

 This is something that convex created for us already that will allows us to interact with our database I hope that makes sense we got the API and from here willll say API do users here we can see this type save and we can say create user so we're gonna call this mutation with some arguments such as the email that we have above we can put it either like this or we can just shorten it this is what I'll be doing we will just add the full name which is the name that we have created above and we're gonna put the image which is gonna be the image URL coming from Cl Now we can get the Cl ID as well as the username。

So let's say username and how can we create the username for this So this is what I'll be doing let's imagine the email of the user is equal to Janhanddo@gmail。

com I will go ahead and get this as the username and let's do it with the split method I'll say email do split。

With the add symbol and grab the first value， right， it will be this part。

I hope that makes sense and in the catch we can console log an error just like that and throw a response with status code of 500。

 but if everything went well right， if we don't really have any errors so far we can return a response where we can say webbook processed successfully and here is the status code。

Okay， so I hope now this function or this file is making a little bit of sense。So what we have done。

 we got some imports created an HttP router that we are listening on this path with this post method and here is the function logic that we're gonna run。

 we will take the context as well as the request first we just need to make sure that this event is coming from Cl and we have a bunch of different really cool checks so that our code looks clean and everything would work properly so we check for the headers check for the environment variable we verify the web hook just like this and for this we have use a package called SVX because this is something what clerk uses as well so that's why we have to use it this is the web hook infrastructure and then we have verified the web hook successfully we check for that event that we have mentioned previously extract the user data and save it to our database Now let's go ahead delete the user from Cl。



![](img/3c902dbcec98786b9e863ce7af553dc4_125.png)

port。And we'll try to sign up from scratch， let's say delete the user and maybe before we delete that user。

 let's try to sign out。

![](img/3c902dbcec98786b9e863ce7af553dc4_127.png)

I'll say MPX exporto。And I will open up my simulator， let's say R， maybe I should press I first。Okay。

 it's just been。Like created， let's say R， okay， why is this not working？Okay。

 so I just close that application， press I， now it is bundling。

You should be able to see our application and let me actually show you how we can log out。

 I will go into the home screen， which was index under the tabs。Here， instead of this link。

 let's just say we are going have a。I don't know， let's just say touchable opacity。

Let's give it some styles， let's say。We don't really have this button ball。Let's put it in line。

 I'll just say color。Do we have color， no we don't。Alright， so here I'll just put a text。Okay。

 just wait a second， just look messy， but we'll make it work。 let's say sign out。

 I will take this styles。Put it。 And here I' just say， color will be。Okay， what am I doing。

 It should be another object。 Let's say color should be white。 Let's say， okay。

 we have this sign out button。 and when we click it， we actually want to get something from clerk。

 So I think it should be use oath。 Let me double check this。Can we have like sign out Yep we have。

 So here when we click this， So let's say on press， I would like to call the sign out function。

 Now Typescript is not really happy with us。 It wants you to put it like this。

 So let's go ahead and do it。Okay， let's say if I collected this。

 we are signed out and our layout runs once again， initial layout。

And it checks that you are not authenticated， it takes you to the login page because we always say whenever the is signed in field changes。

 you should run this use effect and that's why we are taken to the oath page Okay。

 this is the function that we'll be using later in the video。

 but let's just have it for now in the home page。

![](img/3c902dbcec98786b9e863ce7af553dc4_129.png)

Okay， now let's go ahead to delete this user。Now when we try to sign up with Cl。

 we should have the user both here and then in our database， let's go into the data。

 you don't have any users but let's make it work。

![](img/3c902dbcec98786b9e863ce7af553dc4_131.png)

I'll try to sign up with my Google account。So we just signed up， hopefully it should be here as well。



![](img/3c902dbcec98786b9e863ce7af553dc4_133.png)

Let's take a look at the dashboard Did we got the user。Okay， we have it。

But for some reason we didn't get that here， let's see why this is the case。

Now this is real world programming， we could have some problems and errors but we should be able to debug it pretty quickly and I will not cut this part I want you to see the debugging process so I just went into my webbooks I need to check why it failed。



![](img/3c902dbcec98786b9e863ce7af553dc4_135.png)

Do we have any console logs first， Let's take a look at it。Here， we don't。Here， it says。

B request hidden error while pushing must have it okay， so as you can tell。

 we should have a default export of a router， which I forgot to do in HttP do TS file so we should say export default this HtTP。

So I will go ahead at the very bottom of my file。 I'll say export default。 let's save。

Now we shouldn't really have any errors。

![](img/3c902dbcec98786b9e863ce7af553dc4_137.png)

Okay， I'll go ahead， try to delete this user once again， and I'll try to sign up from scratch。

The reason that I am deleting this because。This event is only called when user signs up， right？

Let's go ahead， Saint art。

![](img/3c902dbcec98786b9e863ce7af553dc4_139.png)

I'll try to sign up and once again， just know that we don't really have the user in the database。



![](img/3c902dbcec98786b9e863ce7af553dc4_141.png)

I'll try to sign up with this account。Let's refresh。



![](img/3c902dbcec98786b9e863ce7af553dc4_143.png)

We have user in Cl and in convex as well， and it is working in real time I I didn't need to refresh it。

 Okay， so we got the bio which is unsai， but we have Cl ID email these fields。

 everything that we have just put， right？And by default you get this underscore ID field coming from Convex as well as the creation time Okay awesome that means our database now is in sync with the clerk right you have just learned something really really important called web hooks and this is something that you can use in your other projects you can talk about it in an interview you can just say I have built a project where I use web hooks to make sure my authentication service is in sync with my database so and so forth so this is one of those use cases and later in the video we're gonna see how we can check for the authentication in our convex functions but let me just quickly try to mention it So here we can go into this under this context object so you can say wait。

Like context do oath here we can see we can get user identity and this will check if user is authenticated or not so here it says a promise that resolves to user I if the conveyx client was configured with a valid ID token and this is related to authentication right so it will get the details about the currently authenticated user and we'll be using this later in the video so with that that's gonna to bit for this section where we have learned about webbooks and just for your reference I'll go ahead visit this file and here I'll just add a comment what we are doing in this file we just need to make sure that the webbook event is coming from Cl If so we will listen for the user created event and we will save the user to the database okay。

Now we are gonna move on with the post creation in the create page so instead of starting with the homepage we would like to first create some posts right and then we are going to build the homepage where we can fetch those posts and display that So here what do we need to do So first things first we need to create a conx function that will take the post details and save it to the database once we click to this button and we also need to store the images right and for file uploads thankfully we have a section so if you visit the documentation you should be able to see we have image uploads and you can take a look at the documentation how it is done but I will try to walk you through it like with with our approach and react native and Expo This is mostly for web but as you can tell it can be used with react native as well。



![](img/3c902dbcec98786b9e863ce7af553dc4_145.png)

So we're going to go ahead visit VS code and before we try to build anything。

 I would like to provide you some styles that we are going to have in the Create page。

 so under this Sts folder， create this file called create dot Sts dot TS。And I will go ahead。

 copy everything from my source code and paste it like this。 It is around 100 lines of code。

Let's take a look at it。 Once again we got the width some imports such as dimensions as well as these style sheet and we built like really really basic stuff that is related to CSS。

 We give padding supporters making stuff centered so on and so forth so this is not a CSsS course once again that's why I'll skip this and we can use these styles Now just in case if you want to type this out。

 let me show you the entire file。So you can pause the video if you really wanted to。

And type this out。But this is not something I'll be doing。Okay。

 then let's create our convex function， and then we'll go ahead build the Ui。 First。

 we just need to have it。 since this is related to posts。

 I will create it in a file called posts dot yes。 Now let's try to。B our build our file。

 I'll just go ahead and zoom in。Let's get the simulator on the right hand side and try to build it So first I'll create a mutation as you can tell because we would like to create a post and whenever you need stuff that is related to creation like update or delete you would like to create a mutation you can call this anything once again I will create it as create post which is going be a mutation。

 let's import it， open up our object and give our arguments If you want to create a post you just need to add a caption this could be optional so let's say Vt string let's import the V and this could be optional so lets say V dot optional。

And then we are going to take another field called St ID。

And this will be needed when you want to delete a post， once we try to delete it。

 you will actually see this， this would be important。For now we don't really need to understand it。

 but let's go ahead create the handler function as well。

 is going to be an async function that will take the context so that we can interact with our database and we can get the arguments。

Okay， so as I said we would like to upload some files and for this I will provide you a function that is around three lines of code。

 so it is called as a generate upload URL， it is a mutation。

 so this is exactly coming from the documentation let me show you this。Okay。

 so this is the exact same function just on top of it。

 I have added a check where we check for the authentication， so we say context。 o get user identity。

I have assigned this to a variable called identity， if it is undefined or if it is false value。

 would you say you're unauthorized， but else we are going to create an upload URL so that we can upload our image into。

Okay， so let's go into the handler， let's check for the authentication here and get the current user。

 sos say con。Current user。And before we do so， I think we just need to get the identity。

 so let me try to get this part。And you are going to make this code look a lot better later in the video。

 we're going to build a reusable function to check for the authentication。

 but for now I' would like to keep it simple and just give you the longer version okay so we'll just get the identity and if it is not defined we're going to throw an error but else we can get a user so'll say current user and we'll say a weight do。

Like context， dot D B， dot query。The user's table with an index。So let's just put that and go below。

Theith index。By color I， we're gonna take the callback function just like this。 Let me wrap it。

And we'll say query， but equal to the clerk ID field to the identity that subject。

So this identity subject will give you the clerk I and。Look at this as this has not anyps。

Because we just need to say the get the first value。Okay。

 and we can add another check if current user is not defined， we can say user not found。

So I hope this is not any confusing at the moment， we will make this look a lot better later in the video。

 but for now this is what we can do to get the user。Let me put it like this， okay。

So so far we have done nothing related to creation like creating a post。

 now we can go ahead and actually try to do it。 I'll say create post。Let's say， a rate context。

Dot D B。 And if we want to add something， we'll be using the insert method。

 and we'll like to insert it under the posts table and we can add our fields so we're gonna put the user ready so that we know who's the owner of the post。

 Then we can add the image URL。 Let's go ahead， paste this。

 But we don't really have the image URL at the moment。 How can we get it。 Well。

 we'll basically just say。Here， as a constant image URL。A it。Context。

Thatt storage and we'll say get URL。 we're going to put this ag dot storage storage I。

 This will give us an image URL。We can just say if immate is not existed， we cant throw in error。

And then we can say the storage I。Which is coming from the arguments。

 we're going to put the caption and each post will have zero likes and zero comments when they first created。

So with this now our code is happy with us if we don't add this check。

 I think it'll be unhappy with you because Typescript thinks this could be undefined or null。

 that's why we will add this check just to make it happy。So once we have created the post。

 we would like to increment。The number of posts of the user， right。

 So I'll just go ahead and put this comment increment E。Increment user supposed to buy one。

So how can we do this， we can just say context that Db instead of saying insert since we want to update something。

 we'll use patchch and the user that we'd like to update will be current user and here is the field。

 we'll just say posts。What's say current user dot posts plus one。Okay。

So this is what we have just done and at the end of this function we can return the post ID。

 which would be coming from here， let's say con post ID。

 this is what you get as the response and we can return it。Okay， so this is our function。

 let me just zoom out。What we have done so far is just to check for authentication and you know if you don't add this part I think this code will not be happy with you because TypeScrri cannot really know if this user is null oops TypeScr don't really know if this is null in the database or if you actually have it that's why we add these Eve checks and we generated an image URL and create the post。

Then we just increment the users's post count by one。So this is the function that we would need。

 we will be using this， we are going to call this from the front end。

Wwhichch will be in the create page Now let's go into the create page and actually try to build the UI。

 So under the app， under the tabs， we have this create TsX file。 Let me just zoom in。

And shrink this left hand side。 So we would like to build this。

Function where we just called the create screen。Okay so instead of typing everything out。

 I'll just walk you through it like line by line I promise I will explain every single thing that we have here so instead of having this tutorial be 10 hours by doing this we can just have it like we can dec the size by twice right you can just double down that so we are gonna get the user from clerk we're gonna get the router because once we create a post we would like to navigate the user to the homepage and then each post could have a caption like each post could have an image when we select the image it will be in this state by default it is not so let's go ahead import the use state as well and I would like to keep a loading state so that I can show a loading spinner and this will be true once we say share okay then we would like to get the current user but。

More on this in a second， we would like to pick an image from our media library。

 So currently we have some photos in this machine right in the simulator and how can we select these。

So basically， we will be using a package for this， let's go ahead open up our terminal。

And kill our Expo app， I will say MPX Expo install。And we'll just say Expo dash image。Dash。Picker。

I don't really know if you can see it completely， but this is how that will look like and any youre like anytime you're installing something from Expo you would be using this part。

 but if you are installing it a regular package you would say NPpm install and then the package name so just keep this in mind this part is really important if you are getting something from the Expo ecosystem。

So with this in mind， let's go ahead， run this。Okay， why do I have it twice in the terminal。

 asked Ros now。By using this package， we should be able to select an image from our media library。

Now that we have it， let's say NPX expo。And I'll press R to reload this application。There we go。

 This is what we have at the moment Now for this UI， I would like to get an if check。

 so I will say if there is no selected image， we would like to show this kind of a UI right a container that says tabab to select an image so let's go ahead and make this work I will add this if check before the return。



![](img/3c902dbcec98786b9e863ce7af553dc4_147.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_148.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_149.png)

Now I know there is a lot of different things， let's go ahead and import everything。

 so we're going to get these styles from create file， we're going to get touchable opacity。

 ion icons， let's get the colors， I'll walk you through this code and when we press to this touchable opacity we're going to call a function called pig image for now I'll delete it let's save。

And go into the create page。 Okay there we go。 This is what we got。

 So we have a view with container style and we have the header section where we have an arrowback icon and then we have this text that says new post and then like we are just adding this so that this is centered if you delete it This is how that look So this is some dummy view then we have the entire touchable opacity so it doesn't really matter if you press here or if you press here it will always be pressed and then we would like to call a function called pick image So how can we make this work I' will basically provide you this。

Above and once again， I'll walk you thread So we're gonna get this image picker from the package that we have just installed So I'll go above。

 I'll say import everything as image picker from this package This is something that we have just installed and when we press here we are gonna to be calling this function which will go ahead launch the image library and the media types that we accept will be images However you can get the live photos as well as the videos I'll go with images in this project you will allow for the editing and aspect ratio will be one to one you can change this and quality we will just decmented al to compress our images and if it is not canceled we will set our state with it So let's save and here I'll actually console log the selected image。

They select image and open up the terminal。Let's go ahead。Pss here。

 there we go our media library is selected。 if I say cancel， nothing will happen。

 but if we try to select an image， let's say choose。Now we can see this is the file that is selected。

 right？And we will be using this exact URL to be able to save this to our convex file storage。Okay。

 so now that we know how to make the create page work， since we have a selected image。

 this if doesn't really run， instead we see this UI。Here it says create。

 this is exactly what we have。 Now let's go ahead and build this Ui。

 which is going to look like this。

![](img/3c902dbcec98786b9e863ce7af553dc4_151.png)

So when we like when we select the image， we're going to see this UI where we see this header component and then we will preview the image where we can also change it if we really wanted to。

 then we'll have this write a caption section but there is a problem with this and to be able to solve it we have a component。

 but first I'd like to show you the video， what is the problem。So this is like let me show you。

 when we try to write a comment， here we can see the keyboard overflows the input， right。

 we cannot really see it。Like I'll press here there we go we cannot see it we have the same kind of problem here and to be able to fix it thankfully we have a component instead of view we're gonna have keyboard avoiding view coming from react native so open this up and close it then we are going add some props to make it work properly and in like we can check for the platform let's go ahead import the platform we will say behavior will change depending on if user is on iOS or Android。



![](img/3c902dbcec98786b9e863ce7af553dc4_153.png)

On i， it will work with the padding and in Android， it'll work with the height。

 Then we can give some styles just like this， which is the container and the vertical offset。

 and again it'll just change depending on the platform Now if you ask me how do you know all these values。

 Well basically I have just test them out before recording this video and then inside this we're gonna have our entire Ui So here I'll have a view。

Let's turn this off。And it just has this content container as the style。 Let's build the header。 Now。

 I will put my header。That will go here。Were is going to be a touchable capacityacity。

 I would like to grab this。Paste it and walk you through it。Let me put it right here。

So we have a touchable opacity on press were going to reset our state and it'll be disabled if we are in the loading state。

 then we have an icon which is close outline and once again it'll be like color will change depending on the state then we have a text so basically we are building this part。



![](img/3c902dbcec98786b9e863ce7af553dc4_155.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_156.png)

I hope it makes sense。 Then Om press， we are going to call this function。

 which is something that well built in a second。 and to have a loading state。

 we are going to bebu activity indicator， which is coming from react native。

 So let's say there we go。 This is the UI that we have if you say like。Go back。

 It will actually take you back if you select an image。Once again， you should be able to see this UI。

Now， if it is true， we are going to have this activity indicator。So I hope this makes sense so far。

Below the header component， we're going to build something else， which will be a scroll view。

 So let me go ahead， get this component， close this off and import it。From react native。

 And we can add some stling。Now why this is a scroll view I will show you just in a second once we built this entire UI。

So let's say it all de bounces will be false。 keyboard should per tabs will be handled。

 Then we'll like to have a Uu。With some styling， and for this view， I'll go here。

 let's just say you would like to have a view component。This will take styles。Let's say， styles。

Or style， I should say， and this will be albe dynamic if you want to add dynamic styles。

 you can use an array。Just like this， we're going to say get these styles content and if we are in the sharing state。

 if we are in the alling state， we are going to add this。Style as well。

 which will make the U I look like disabled。 Then we would like to add an image section。

 So let me please go ahead and。Imported。Or edit， there we go， we'll get the image from react native。

Okay， so instead of getting it from react native， I think I'll get it from Expo image。 So say import。

Image component。From Expo image。So do we have that component or do we have that package。

 I think we should install it。 So I will open up my terminal once again， kill this， clear this up。

 I'll say MPx Expo install。Expo dash image。Now， why are we using Expo image component is because this package gives you an image component。

That makes images really optimized， so it is like the image component that we have next Js。

 so basically it is for performance reasons， So we'll go ahead get the Expo image and we have added this part where we show the selected image these are the sliding that we have and then we have this change button on press we' are going to call the same function once again So let's save open up our terminal and start the application。

I'll press R， or maybe I should press I。Okay， it should restart it。Let's try to select an image。Okay。

 here we can see images been displayed， we can change it。And it just works as expected。

 and since we have this editing tool， we can basically edit this。Okay。

 so below to this image section， we will like to add the input section。

 so I would like to once again get the code and walk you through it。So right here。

 I'll put a comment， let say image。Section。And here we'll have the input section。Let's paste it。

 we're going to get a text input component。The rest is almost the same thing。

 so there is no there is no reason to type this out all again from scratch。

 we are showing the user profile image and we can basically write a caption。

 So here why did we used a component called scroll view it's because like here I think we cannot see it。

 but if we had like multiple。Lines， let me try to add those。

We can scroll through it in our phone and we can even add like offset， I believe。It's offset。

Let's say content offset will be， I don't know，50。Does it have to be string， Okay。

 so it says point pro。So I don't really know how to use this because I haven't used it， to be honest。

Here we should give x and Y， I believe。Okay， x， let's say0 will be， but y。Let's say，100。

So as you can tell， we have some offsets and like I just literally learned it with you today。

And how did I learned it like when you hover over this， I just saw this x and y and when I had 50。

So here on the error， I I just saw this x and y， and that's why how I realized there is this x and y fields。

 So I'll just go ahead and just say y will be 100。Okay。

 so just because of this scroll view component， we are able to make it work like this。Let's go here。

 I think I also need to X field， I'll make it to be 0。

we can basically add more stuff and scroll through it。Here it doesn't really work as expected。

 but in your phone you can imagine with your finger。

 you can basically scroll it and see the entire view。Okay。

So this is what we have built for the return statement now when we say share nothing happens right let's just press that literally nothing happens because we don't really have a function for that and let's try to build it now so this is a quick pause that will take around one minute I'd like to mention something and I am recording this from the feature because we have some potential issues so the first things first if you want to see the keyboard when typing this out in the simulator you need to press command shift K and all of a sudden you will see the keyboard but now we still have this problem where keyboard is overflowing with the content so we thought we have fixed the issue by using this component but it didn't really fix it completely so I found a solution instead of using2 any will go with 100 and let's save and let's try to see this in action there we go we have 100 pixels of offset and we can see this in action that is working in。

Android we don't really need to add any offset because by default。

 the keyboard will be avoided so you just need to keep this in mind for i specifically。

 Okay so that was something that I wanted to mention just keep this in mind and let's move on with the video So we need to find this button called share which is going be under this touchable opacity let's see where that is it is this one and we're gonna add this on press handle share function and let's go ahead at the very top try to add this function So first things first we need to get the generate upload URL function。

 which is something that we have created here as a mutation and in convex you can just say use mutation if you want to consume it you can say API that whatever the file that is So under the posts we have this mutation and I would like to call this as。

upload URL。 And in the same way， we can get the create post function。 So let's say create post。

 which is a mutation。 That's why we say mutation later in the video we'll learn things about queries。

 So we'll say use query。 But for now， it is a mutation。 And under the posts。

 we will call this as create post。 This is what we had。 And then in the handle share function。

If is something that we need to build， let's say cost。Handle， share。

Wwhichch will be an acing function and let me walk you through it now first things first will just say if there is no selected image。

 then just return out of this function， don't do anything。

But else we can open up our trica trica statement and just say we are in the loading state。

 So'll just say set is sharing to be true。 Then we are going to get an upload URL by calling this mutation right and then we need to get an upload result by uploading our file and to be able to make this work I will get a package So let's let's kill this。

Clear this up。 I'll say MP X， oops。Let me make it full screen MPX Expo。

 so here is the entire package name I just paused the video and take a look at my notes because I was not able to remember that。

 but there we go it is called as Expo file system Let's go ahead and install it。

By using this package， we will be able to upload our images really。Like Per way and clean。

Let's start our application。Press R so that it would reload it and here in this function。

 we would like to get an upload result。I will go here below， paste this and walk you through it。

 we need to get the file system。As an import， just like what we have done here。

So say import everything as file system from this package。 and by using this， we can upload。

Upload a URL right or upload an image to this URL that we have What are we going to upload is this selected image Our method is post。

 This is the upload type we basically have this binary content and the meme type is image JP then we can go ahead just check for the status。

We'll say if。If status is not equal to 200， which means something failed。

 but else we can get the storage ID from this upload result and then we can call our mutation so it'll be a wait。

 create post。And we are going to add our fields， which we have the storage ID。

 as well as the caption。And if everything has done successfully。

 we can take the user and push it to the homepage， so let's say slash tabs。And in the catch。

 we can basically just say console log。Eir sharing the post。You can handle this in a better way。

 but this is how I will leave it and finally we'll say set is sharing will be false。

Either we succeed or we fail。In either case the alling stage should be false okay let's save and test this out now hopefully you didn't get really confused with this package。

 this is how we can easily upload images， easily upload files by using Expo and this is one of those packages that Expo gives you out of the box。

Okay， so let's go ahead and select an image。I'll say， choose this one。 Let's say， first post。Oops。

 say first post and share it， we have the avoiding state for a second。Once it is doneuccessfully。

We are taken to the homepage。 Let's double check under the posts。 we should have that。

And here by the way， I don't know why we got the exact same user twice。

 looks like we have a bug that we're going to fix， but here we can see this user has one more one post right under the posts。

 we can see this is the post and we can go into the files。We can see this file。

If you hover over this， I think this is going to give you the preview。



![](img/3c902dbcec98786b9e863ce7af553dc4_158.png)

So I think it was giving me the preview， but right now it doesn't。



![](img/3c902dbcec98786b9e863ce7af553dc4_160.png)

But you can take a look at it， we have just installed it。

Okay so this is what we have stored in our convex storage so this is how we can create posts。

 let me pretty quickly walk you through it what we have done and how it works from start till the end so first when we visit this page we hit this if check where we say if there is not a selected image then please show this UI and when we click to this。

We basically call a function called pick image， and it is going to。Launch our image library。

 it will allow us to select images and we have some props to add our own customization and if an image selected successfully we are going to set our state with it so I will go ahead and select it now that we have a selected image we are not going to hit this if check but instead we are going to hit this return statement which is going to show us this kind of AUI and when we click to this button we are calling this handle sharere function and here we are calling two different mutations that we have。

And we have created these in this file， one is to generate an upload URL we just got this from the documentation and added our authentication check。

And then we have our own create post function where once again we check for the authentication。

 we get an image URL， then we create the posts in our database with these fields and then we increment the user's post count by one right this is what we have done and let's save this file。

Then here in this function we are basically consuming those mutations and on top of everything we have used a package called file system。

 this is coming from Expo this allows us to upload images pretty easily and it is really easy to use and if everything has done successfully we take the user to the home screen so I hope everything that we have done in this section makes sense you can post the video and just analyze the codebase for five to 10 minutes and once you're ready we can move on with the next section and I have just realized we have an error that is related to users so I don't know why we got this user created twice I think this will never happen again when you are developing we got this issue but let's go ahead delete all the users and I'll delete all the posts that we have。



![](img/3c902dbcec98786b9e863ce7af553dc4_162.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_163.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_164.png)

And let's try to sign up all over again just to make sure that this is not happening if it is happening。

 which is we have to debug this， so I'll go here into my simulator。



![](img/3c902dbcec98786b9e863ce7af553dc4_166.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_167.png)

We need to sign up from this account and let's try to sign up。



![](img/3c902dbcec98786b9e863ce7af553dc4_169.png)

So we just signed up， let's see。We got the user here。



![](img/3c902dbcec98786b9e863ce7af553dc4_171.png)

Lets refresh， we should have it in the clerk dashboard as well。 There we go。 I would like to。



![](img/3c902dbcec98786b9e863ce7af553dc4_173.png)

Like log out and log in once again。And in this case， it shouldn't really create this user。Okay。

 so we didn't really get this and we don't need to refresh it because convex by default is working in real time。

And let's try to create a post， so I'm just doing this for the debugging purposes。

Just to make sure that the same user is not being created twice。Okay， so we got the post。

But this did not create it once again。 It just updated the post count。

 So I don't really know why we got the same user previously twice， but now it is working as expected。

 Okay， so with that， that's kind a bit for the section。Now let's move on with the home screen。

 which is going to be our feed， so we would like to build this header section below to the stories and then we would like to fetch the posts that we have in the database so let's go ahead and start with our query that we'll build with the convex and then once we build the UI were going to go ahead and fetch the posts。

So first I'll go under the convex， we have this posts filed， and we would like to build a query。

 let's say export con， get feed。Poss。Now this is going to be a query because we would like to fetch some data you would be using mutations to update some data or create and delete。

 but queries will be used to get some data Now in the same way we can add arguments but we don't really need to add we would like to basically fetch all the posts so for that reason I'll just put a handler function let's say this is going be an ascing function where we'll put the context as the first argument。

Once again， we can get the arguments， but we don't really need it for this function。

So we'll go ahead and try to build the logic so in the same way。

 so here we have tried to get the current user so what we can do is copy this and paste it here this will check if user is authenticated and it'll get the current user now instead of doing all this again and again we can go ahead take this and make it a reusable function so I will cut this entire thing。

 visit my user's file that I have。As part of my convex functions and I'll create that helper function。

 So here this is not going to be a mutation or query。

 This is basically an async function that I would like to call as get。Authentated user。

And let's try to paste this in。Okay， so we just put the entire logic where we return the current user if there is no errors。

 but the only thing that we are missing is the context which we can get as an argument but what is gonna be the type of it so it could be either a query context or it could be a mutation context right so let me just grab this。

teachian context。Okay， and we are importing them from generated server。

 so let's try to save it like once again， what we are doing here is the exact same thing。

 what we have here。So I will delete everything that we have because I will call my function。

Called get。Authenticated user。 and I will await this， and I will add my contact into it。

 Then what this gonna give me。Will be the current。User。Okay。

 so here this is a context going from the mutation， and now we will take the exact same thing。

But this time this context is coming as like from the query。

 that's why we said type could be either query context or mutation context。

 so I hope this makes sense like I am trying to go really slowly just to make sure that we are getting familiar with the convex once we understand these we can just split up with these functions。

Okay， so now that we got the current user， we would like to get all posts。

 so they say get all posts and here we can say con。Posts will be equal to a context。Dot D B。

We would like to query our posts table。 And if we don't really have any queries。

 we don't really need to， you know， just。Add things like with index， so on and so forth。

 We would like to get everything。 and I would like to order this in the descending order。

And let's just say， collect everything。Okay， so now that we have all the posts。

 let's add the let's add a check。 I'll say if posts thatt length is equal to 0。

We'll say returnturn and MTRA。And then we can finally go ahead just say return posts If you think this is the entire function that we need。

 you are wrong。 let me tell you why if you hover over the posts。

 you can see we have bunch of different fields and the most important thing is the image URL as well as the caption but there are some stuff that we are missing if you just take a look at this posts。

 you don't really understand if we like it already or not and depending on that like we need it because depending on that field we are going to show this as field and if we bookmark it already we will make this to be filled as well right we will just have this as a different color so let's go ahead and try to actually built that part So instead of returning the posts immediately I'll say return posts with。



![](img/3c902dbcec98786b9e863ce7af553dc4_175.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_176.png)

Some info， right， And let's try to build it。I will go ahead to seeEn hands。Posts with user data。

And interaction。Sas。Okay， let's say constant。Posts with info and you would like to do this in aprom。

 all。Because we are going to run an array， so here I'll just go inside and I will sayPo that map。

 you would like to get each single post。And I will wrap this with an ascing function。Just like this。

 let's say async post and call this arrow function。

Now what do we really want to do we would like to get the post author first because if you take a look at the post you only have the user ID。

 you don't really have the author image or author username right we need to get this data so that we can display it on the UI so we are going to go ahead use this user ID and from that we are going to get the post author。

 so let me just type this out we'll say post author。



![](img/3c902dbcec98786b9e863ce7af553dc4_178.png)

You would like say await context。 Db。 get and we are going to say post。

 user ID so this is going to give us the post author and then we would like to check if we already like the post or not。

 so say await context that DB you would like to query something from the likes array here I'll go ahead and just say with index and if you remember we have an index for this by user and post。

We' are going to get a query。And basically， I will say if query that equal to。Here is the user ID。

 which is the current user ID。Let me give space。And then we'll say equal to。

 I think this should be inside。And we're going to add basically the other field， let's say。

 post lady。Like this。It's equal to this post ID。Okay， and out of this thing。

 we would like to get the first result。 So' just say get the first one。

 which're just going to give us。A like document。 So let's say con like。Okay， if this is existed。

 that means we already liked it， but save， this has been formatted。

 so in the same way I would like to check if we bookmarked a post or not。

So this is the exact same thing， but we are going under the bookmarks table。

And then we would like to actually return an object。 So below to it， I'll say return。

We would like to get every single thing about the post， but on top of it we will like to enhance it。

 so we would like to add the author info， so to say author objects where we will add the author ID。

Post author do underscore already， then we'll take to add the username。

Which is going to be post author that username。Oh， get it。And finally。

 we'll like to show the image of the author。So post author not。Image。Okay。

 then the very last two fields that we need to add， if we already a it or not， let's say is light。

And is bookmark。Now like is an object right， we would like to convert this into a booleion and we can add two bank operators。

 so this is a basic JavaScript trick that you can keep in mind and with this that's going of it for the entire file。

Right， let me just make this to the entire screen。And zoom out so that you can see the entire function。

So we got the current user， we got all the posts and if it is empty。

 we're going to return an empty array and then we would like to enhance the posts so that we can actually extract the author information as well as if we already like the post and if we already bookmark it depending on that because we will update the UI。

And this is how we basically did it， we used our indexes that we have created previously。And yeah。

 so exactly that's what we have done。 We are returning the posts with info out of this function。

 And now it is time to go ahead and。But the UI， then called that query。So I will visit the feed。

Let's say this is the file that me make this look like that。

We will go under the app tab where we have this index and I'll delete everything that we have here。

 which is the only sign up button， we are going to still keep this sign out at the very top。

 we are going to keep this view with this style now on top of it we would like to add the header section which is going to be this part we have the logo as well as the logo out button。

So let's see how we can make this work， I will basically copy and paste it。

 it's around five lines of code and for the styles we need to add a file let me go ahead and provide this to you。

 so I will just say feed dot styles dot TS。I will grab this from the Gi Bripo and if you want to type this out。

 I can show you the entire file。This isn't the longest one that we have。

So you can pause the video and take a look at it。But I think we don't really need it。

So we here you can have the entire file。😔，Okay， I'll just save。

 Now let's go ahead and import the styles， which are gonna be coming from。Not oath styles。

 but let's say feed styles。O。Then we'll import the icons as well as the colors。

Let's save and take a look at the output。 Okay， this is exactly what we got。

 I'll just open up my terminal and reload this。So here we can see the text is a little bit different and for this we are using the header title with a J Brains mono mediumum。

 we didn't really install this font。If you take a look at the assets， let me show this。

So we don't really have this font installed， this is something that we'll do later in the video if in your case you cannot see it highlighted like this。

 just ignore that we are going to install it in a couple of minutes。Okay。So with this。

 now let's keep moving。Let's keep building after the header。

 we' would like to build the stories section。 and in our application。

 the stories section will not really work， but I just want to still implement it with the hard coded data so that you can see how to implement that kind of a。

Component， right。So I will go under the components， I will create this thing， let's say story that。

TSX and under the constants， I will provide you mock data that TS file。

 So I will go ahead and get that file。So， we have around。50 lines of code for stories。

 and each object has an ID username avatar， which is coming from onsplash and has story bullolean。

 so it's either false and true。This is a couple of different stories that we have around eight of them。

 now let's save and for the story component。Let's try to build it。

 this is a basic function where we get the styles from feed dot styles。

 we got a couple of different components from react native and then we have the story type which is Typescript specific and we just have UI no logic at all just some styles with an image and a text so I'll save this and let's go ahead try to build the remaining part so after this view I would like to add a scroll view。

Let's say scroll view component。 and I'll explain why are we using this in the first place。

 So I'll just say the shows。Let me actually copy it。So it shows vertical scroll indicator。

 we don't really want to see it， so I'll just say false。

 then we would like to add the stories section。I will go ahead， save this and let's go inside。

I'll say， stories。Let's paste this in， we are going to get the stories from the Mac data file and let's get every single story。

 right？Now let's save。 there we go。 This is what we have。 and here we can see again。

 we just say do not show the scroll indicator if you say true。So it did not refreshed。

 I'll just say reload。Okay， so I don't know if you can see it， but it is not visible actually。Okay。

 so like normally there should be this scroll indicator at the bottom and。

Here we are trying to hide it Now I've used it in my phone when I was testing out it is actually shown。

 but here I don't know why this doesn't show when it's true， but in your physical phone。

 this will actually be visible and I think because the parent has false is it the reason。No。

 but this is the article。Okay so just keep that in mind if you make it true in the physical point。

 you will be able to see a scroll indicator at the bottom and if you make it false。

 it'll not be visible and I will leave it as false specifically so that the bottom scroll bar is never shown in the horizontal direction This is what modern social media applications does so below to these stories and below to this scroll view but still inside the parent I would like to like show my posts so we would like to say posts do map for every single post show a post component so we would like to create post component and we also need to fetch the posts fetching posts is easy because we already created our query so I can say con posts will be equal to use query。

And we'll say API thought posts and get fee posts。And we can add a loading state as well。

 So I'll just say if。Posts is equal to undefined and if a query is equal to undefined in convex。

 that means it is in the loading state okay， just keep that in mind if it is undefined it will be in the loading state and if it is null that means there is no value。

So let's say return in this case， I would like to return a loader component that we are going to create in a second and let's say if。

Posts。That length is equal to 0。 In this case， we will take to return a placeholder or just say no posts found。

And this is a component that we will be using only in this file。

 That's why I'll just scroll at the very bottom and create that component。

 So basically this is a view with a text with a text that says no posts yet and now we will take to build the loader component we are gonna be using this in multiple places so I will put it into the components folder so let just say loader do Tsx and let me give you the styling it is a really simple component we have a view where we just show a large activity indicator Okay I'll save let's go back try to import this and then we would like to。

Create the post component。So for a second， I will delete this and I'll just say if this part is true。

 let's see what we're going to see。Okay， this is going to be DI in the loading sake。

 this is what we'll see。 and let's say if this part is true。

 if you don't really have any posts in the database， who are going to see this text。

And you can always change this and make it a lot better， but I'll just leave it as it is。

Now let's add this post component into the UI。 and you would like to create a file for this。

 That's going to be under the components。 So this say post that T X。And let's say R and F。

Where we would like to build a post component。And this is gonna be taking the post as the argument or as a pro I should say right so we'll just get the post And here we would like to make the typeyscript happy for now I'll just say we're gonna get a post it's gonna be type of any but in a couple of minutes we will put the actual type and just to now forget it I'll add a to do so I'll just say add the actual type later in the video and the very first thing I would like to do is just get the feed styles So I'll go ahead and import it then let's build the UI and we're gonna build the functionalities So here under the return statement I'll just delete this text and here I would like to add a style with styles dot post and first let's build the post header I'll just add a comment just in case if you want to copy and paste it from the source code so we're gonna have a view component let's say this will have the style as。

Styleles that post header。 and this is also type save because it is able to see that file and read the content。

 Then inside this view， we would like to first put a link。 So let' just say a link。

And you might be asking why？

![](img/3c902dbcec98786b9e863ce7af553dc4_180.png)

Just imagine。When we click to this section it should take us to the profile of this user right so that's why we're going to go ahead and add a link。

 let's say import the link from Expo router and for the HR for now let's just put slash user and slash1 to3 later in the video where actually make it work。



![](img/3c902dbcec98786b9e863ce7af553dc4_182.png)

Now this is not really happy with us， but let's just say for now we are going to take the user to the。

 I don't know， let's say notifications tab and to make this work it should be looking like this to work properly and then under this link I will have a touchable opacity where we will show the image。

So let me import this well have the image and you can import it from either Expo image or react native In this case we'll use Expo image so that we can actually cache it and make it work performly so we have the source which is post author image style contentfi transition and then the cache policy and then we're going to show the post author username so let's say this and I will open up my simulator let's go ahead import the post。

And save， hopefully we should be able to see our very first post。

 we don't have the contact content yet， but we can see whos the author。And then below to this view。

 we would like to put something else。I think still inside the view， but below to the link。

 So I will say show a delete button， but we only want to show this if we are the owner of the post。

 So again， I will add a to do。 let's say fix it later。Okay， I'll just leave it like this for now。

 let's just say we will have three dots。Wwhichch will be a touchable opacity， ion icons。

 ellipses horizontal， and you are going to have this white color if we are the owner of the post。

 we will see a delete button and let me show you this as well。How it'll look like？So。

 we are going have。A touchable opacity with this trash outline。

 so I will delete that and bring this back。 Here we go， this is how that look。

And I can comment out this， we will be making this to be dynamic in a couple of minutes and then outside of this view。

 we would like to put the actual image， the post image， so I will go ahead and get the image。

So it is the exact same thing， that's why I am not typing this out。

 we basically get the post image URL and we cache this and here we go。

 this is the post that we have shared in the previous section。Then below to it。

 we would like to put the post actions。So here I would like to have my。Post actions。

Which is gonna to be the buttons where we can like， or we can add a comment， we can bookmark。

 so on and so forth。 So I would like to provide this section， which is around 10 lines of code。

 Let me save and I'll walk you through So we have a view。

 This is the parent view where we give the post actions Then we have the left hand side which are these two buttons。

Okay， so we just show a hard hard outline and then chat bubble outline if I can correctly。

 then we have the bookmark outline that is on the right panel。

So after this view we would like like after this view， we would like to put the post info。

Okay so we will go ahead and just check the number of likes and comments。

 so once again I'd like to just paste it which is around 10 lines of code and I'd like to walk you through it so we can already see some data so here we say be the first one to like this post and we'll just say if there is a caption then display it with the author info then we just say view all two comments later in the video we'll make this to be actual number of comments and then we just say two hours ago but now there is an issue if you can see。

Like we just need to scroll even more to be able to see everything so here it is overflowing with the tab bar and to make this work we can scroll scroll to the top and actually it'll be in the index TsX file we'll go into this scroll view where we have this parent scroll view I will add this content container style and from the bottom we'll just give 60 padding Now if we scroll to the very end we can still have 60 pixels of like padding so we can have this area before this just notice how。

We cannot really see everything clearly right it overflows。

 so this is another thing that you can keep in mind while using scroll view component and now let's go ahead into the post TsX。

 make these functionalities work where we can like comment and add a bookmark。

So we are going to start with thelike function， but before let's just handle this to do where we would like to add the actual type instead of just saying any。

 so I will delete this line and let's go ahead make this to be let's say post props which is going to be a type that we' would like to create so here we are accepting a post let's go ahead and get that now this post is extended right we just know that from the get feed posts we are returning an object。

Getting all the fields that a post has， such as， you know everything that you see on the screen。

 and on top of it， we have the author author。Author information and then we have two different boan values so we would like to add these so that our post prop is typeafe And instead of typing this out since we already know this。

 I will paste this and walk you through it so each post will have an ID which is type of post ID and you can get this ID from。

AConvex generated data model。 You can also say this is going to be type of string。

 But if you want to be really clear what you are doing with， you should say。

This should be actual type of post ID right， and then on top of these Eolean values。

 we would like to have the author field just like that。Okay， so with this in mind。

 everything should be working as expected。 Now we can just say post。And you can see it is typeyafe。

 you can go under the author and you can get all these fields。Now I think this is complaining。

Here we go so it says it could be undefined and to be able to fix this I will go here and let me sharing the left hand side。

 so when you are getting the post author it says this could be nu。

 but we really know that if we have a post we know that we have an author as well so I'll just wrap this with brackets and I'll just add a question mark or exclamation mark at the end just to say this will never be not we will always have a post author。

Okay， let's save now we don't really have any errors。Okay。

 I hope that makes sense we have just handled our to do。And we can build our like function。

 so I will save this file and since liking a post is related to posts。

 I will go under the convex folder and visit the posts file and we are going to add a function called let's say toggle like。

I am calling this as tole like it's because this will both handle liking and un liking so let's say this is going to be toggle like which will be a mutation and we would like to get the arcs and here we'll just pass the post ID so let me know which post that we are trying to like so to say it's going to be type of V ID。

With posts， there we go。 And we'll just say we're gonna have a handler function。

 which will be an async arrow function。 and we're going to get the context， as well as the arcs。

Okay so now let's try to build the function logic so first things first we are going to get the currently authenticated user and since we have this function already we can just call it then we would like to check if we already like this post or not so I'll just say cost existing and we are going to go into the likes table and we are going to search for it if we get a result that means we already like this and then we would like to get the post itself。

So here we just get the like， we just check if we already liked it or not。

 and now it is time to get the actual post so we'll just say context Db dot get and pass the post8 let's just add an if check if post does not exist we'll say post not found and now depending on this existing existing state。

 we will just say either we would like to remove the like or in the else case we would like to add a like。

Okay， so if it is existing， it means we already like it where we'll like to now delete our like。

 so I'll just say a await context Db dot delete， so basically go ahead delete this like from the likes from the likes table and then what do we want to do just go ahead decrement the number of likes on this post Okay so we just say patch this post and this is the field that we'll like to update。

So that's going to bid for the if check and I think we can also return false。

 This indicates now the like state is false right， so it means it is unlike and then in the else case。

 you would like to basically add a like。As you can tell。

 we're going to add a like into the likes table with this user id and with this specific post and then we'll like to increment the likes count by one Now there is one more thing that we would like to do if it is not my post I would like to send a notification right so I'll just say if it is not my post let's create a notification and how can we check this。

Let me just provide the code。Let's save to get this formatting so we basically say if current user ID is not equal to the post user ID right if this is not my post。

 go ahead under the notification table and create a notification and here are the fields type will be like there we go and finally。

Still inside the L statement， notice how we return false in the F in the if。

 now here we'll take the return true。Let's see true。 This will indicate。This is now liked。Okay。

 so that's the entire function， believe it or not。It looks like too much。

 but actually it is super simple， right？Just take a look at this if you really wanted to pause the video。

 then we should be good to go now let's go into this post TsX file and actually try to call this mutation that we have just created so I would like to have a state first so I' just say con this is going to check if we already like the post or not so is light and set is light。

This is going to be equal to u state。Let me type this correctly。 Here we go。

 And we' will just say post dot is liked。 and we can now create a function。

 I'll just say con handle like When we click to this icon。 we would like to call this function。

 So let's say async。Arrow function that we're going to build the logic in a second。

 and we can also keep track of the like count。 So here I'll just say。Likes count。

 it will be a state post likes that is coming。 As you can tell from the props。 There we go。 Now。

 let's visit and find this touchable opacity where we have heart outline icon。

 but we would like to make this to be dynamic， So I will cut this for a second。

 I'll say if it is a light， we would like to show a heart icon， but if it is not liked。

 then we would like to show this heart outline。 Let's save。

I'll just make this to be true so that we can see the field state。 There we go。

 and then we would like to change the color as well。 So I would like to go below。

And instead of having the white color， we'll just say if it is liked it should be primary color。

 which is green and otherwise it' be white， then on press。

 let's just save to get this formatting on this touchable opacity on press should call the handle like function。

So let's go ahead and try to build it。So first things first。

 I will just say give me a try catch block and then I'll say wait toggle like and this is the mutation that we would like to consume。

 so let's say use mutation。Under the API， under the posts， there we go， get the toggle lake。

What say is the toggle like。Now we can call this， and as you can tell， this is expecting some props。

 right， toggle like Hp。Okay， we are just going to send the post ID。

 let's say post ID will be equal to post dot underscore ID。Then after this。

 we would like to update the state， right， on you say set is liked。

And now is this going to be true or is this going to be false， I don't really know right。

 we should get a response from this function and this is actually what we have done。

In the if and L statements， we just return the current state either true or false。

 so here I'll just say con and assign it to a variable called new is liked and we'll just set is liked with it then we can go ahead update the likes count just like this in the catch you can handle it properly or in a different way。

 I'll just leave it as a console log。So let's save and hopefully this should work out and also I would like to use this likes count。

In the actual UI， so I will go ahead and find the post info section here instead of having this text。

 I will cut it for a second and I will say if life count is greater than0。

 then we would like to see the actual actual count otherwise we'll just see the previous text Now let's save and I would like to reload this application。

By pressing R in the terminal。Okay， so I'll go ahead like this， there we go， we have one like。

And let's double check this。Here we can see our post got a like and if we visit the likes table。

 we can see we just got a document， we can go ahead and try to unlike it， this should be deleted。

In real time， here we go and this post now has0 x， so that means everything is working properly and since we just liked our own post。

 we shouldn't really have any notifications。Here we go。

 And now let's test out the notification feature as well。 I will go ahead and。Like， log out。

Because I will try to sign up with a different account。

 so currently we just have only one user in the database， which is this one。

 let's sign up with this and I will like the other accounts post。All right。

 so it looks like we got an error for some reason， let's try to reload our application。

Is this something that we just got in development or okay so we are going to see if that error occurs anytime soon。

 otherwise we can just move on at the moment we can take a look at the notifications。

 we don't really have any documents。So I am logged in as a different account and I will try to like the pulse of this user。

 which should create a notification， so I will like it。Like in real time we got de notification。

 it is type of like， this is the receiver， this is the sender。

 and we can see this post now has one like， and we got that user in the database as well。Okay。

 so it seems like everything is working Now if we try to unlike it。

 obviously we don't really want to delete the notification。

 so I will unlike it and this is not being deleted which is what we would like to have and now you might be asking okay so if this is not my post why on earth do I see this delete button so this is just an icon this is how we coded it it is hardcoded we are going to fix it obviously but just know that currently if you click it nothing happens so this is a todo that we left for the incoming sections and next we can add the comment functionality？

So before we start writing the comment functionality。

 I'd like to take a quick break and just talk about the performance issues that we currently have。

 and then I'll give you some resources that you should keep in mind while working with reactact Native。

So first things first， let's see the problems that we have and how we can optimize them。

So it's going to be under the home screen， which is what we have。

 and it's under the app tabs index that TSX file。Alright， so it is going be related to posts。

 So for now let's go ahead and just cut this。 We are going to ignore this for a second and we are going to fix that as well。

 I'll just put it right here and comment this out。 So as if it does not exist and we are going to add it as I said just in a second。

 So what is the problem here that we have。Now in a real word social media application。

 probably you will have hundreds and thousands of posts and what Sc view does here at the moment when you map through it it actually tries to render all of them at once and this is a problem because your application might crash because there is not enough memory so what we should use instead called a component called flatlist so this is something that I have mentioned if you remember at the beginning of the tutorial and this is the time to use it so what this does is to actually only render what is visible on the screen so just imagine we have 100 posts but currently we can only see one we cannot see the others so it will only render the one that you see and as you scroll it will render the remaining part so currently we just have only one post but imagine if in the database we had 100 posts。

That would be the case。 So scroll wheel tries to render everything at once。

 and flatlist instead does only render what you see on the screen。

So I'll just bring this back maybe the story section。And you are going to try to fix it。

So let's save， so we are going to optimize the poll section， but now four stories。

 if you think in your social media application you will have。

 let's say at most 20 stories in that case using scroll view is I think completely fine because like if you render every story that you have at once your application will not crash right but you could still use flatlist for this case as well so what like once again what scroll view does is to render everything that you have at once。

 even though if they are not visible on the screen， but on the other。On the other hand。

 what flatlist does only render you what is visible on the screen and as you you know as you see the other elements it goes ahead and render them and it this doesn't really cause any delay or anything but it just improves the performance so before we try to implement it I'd like to give this as a note。

 I'll go into the route。And I'll create a node that MD file so that you can have this as a reference at the end of this tutorial。

Let me just copy it and paste it from my notes。Shrink the left hand side， paste this in。

So these are the notes that I have prepared with the help of AI just to make it look really clean and crisp。

 but I just double checked everything that you see on the screen is completely correct。

 so let's just go over it。You should use flatlist when performance is critical because Fllist only renders items currently visible on the screen。

 and it save memory and improve your performance。And when you have long lists of data。

 so basically what we have in the post section right when we are rendering potentially large sets of data。

 so this could be your feeds， search results， message lists。

 so on and so forth now we can read the rest， but basically you would like to use scroll view when all content fits in memory。

 so when you are displaying a small fixed amount of content and so on and so forth。

I hope this helps and we're going to add more notes as we go through this section。Alright。

 so now that we know the theory， but how the hell do we implement that right。

 so we're going to go ahead what I'd like to do just ignore the stories completely for now once again I'll just cut that and put it right here as a comment so that it doesn't really bother us。

So for now let's just think about depos since we are not going to be using scroll view。

 we can basically go ahead and delete this completely and instead use a component called Fllist。

So let's say flat list imported from react native， and this is going to be a self closed component and let's see how we can use it。

Instead of doing like post do map or St do map， we will say。

This is the data that you would like to map through。 And for each post， what do we want to do。

 We would like to render an item。 So this is going to be taking a callback where we will take the item。

 So here you can see if you。Press control space。 You can see index item and separators。

 We would like to get the item。 and for every single item， we would like to return a post component。

 and here we'll go ahead and add the post。Like this。

 because this post component wants you to add a post prop。

But now we didn't really add the key right for this， there is a special prop called key X director。

 and we would like to add a unique field， such as the ID。 and then we would like to add this。

Previous probe that we have called show， I think it should be vertical。 Yes。

 so since this is related to posts， we don't really want to show that vertical scroll indicator。

 So I'll just say falses for this。 Then I also want to add this content container style where we give some headings from the bottom。

Okay， so I would like to just save it and let's see what we're going to get。 Okay， there we go。

 what we have， let's just double check。 I'll read about my application。

So we can just see our posts just like previously， but now it is a lot more optimized and performant。

But now we don't really have these stories right for this we can go ahead and add another prop。

 so I'll just say a list header component and for this we would like to return return a component called let's just say storiesies section you can call this anything but this is the name that I'll be going with Now let's try to cut this part and delete this comment I will go ahead and create this component so this will be an arrow function where we can immediately return what we have just cut it。

Okay， so I think this is going to be。Like this， so we can just still go like this。

 but I want to make it a bit more begin friendly， so we'll just say return this part。

And let's paste and remove the comments。Okay， so basically we have a functional component where we return a scroll view with stories。

 and we say this is going to be in the horizontal direction。

 do not show the indicator and this is the ss。Okay， so everything should be working as expected。

 just like previously， but now everything is a lot more optimized and performant because we are using flatlist。

If you really wanted to， you can still use flatlist for this one as well。

 but since we only have eight stories， I think this is completely fine to use Scview so that was the first thing that I wanted to mention now let's go ahead and talk about something else so I think at the beginning of the video I've talked about the pressable component versus touchable aacity and so far we have only used touchable aacity and it has a reason so I would like to just save this file and go into the notess and try to add some notes so that you can have it on your source code as well。

Let me copy everything。And I'll just tell you the difference by reading this file。

So before I read anything just know that pressible is used in more complex situations when you need more complex interactions and touchable aacity used for more simply like for simple fade effects and this is what we have used so far we don't really have any advanced interactions so we we mostly used touchable aacity but you can take a look at the entire thing once again I just doublecheck everything that you see on the screen as completely correct but basically you would like to use pressable for complex interaction states and both of them are used for button purposes and pressible is a bit more newer like in the old code basis you are gonna see touchable aacity more and more and it has a simpler API as well so I think and I hope this makes sense as well there is one more thing that I like to talk about which。

As the image component that is coming from react native。 And in this file， I think we are using。

The one that is coming from react native and there is another image component which is coming from Expo。

 So what are the differences about those I think I have already mentioned that。

 but I'll just give you some notes。Which explain it a lot better。And once again。

 basically you would use Expo image when you need some like a more performance and for caching。

 and in our case since we have high quality images。

 this is a social media application we always want to have some caching so that images loads immediately and we are using Expo images most of the time and you should use react native image when you need basic image display with minimal configuration and when you are trying to keep your apps bundle size smaller。

 here are some more some edge cases that you can take a look。

 but this is the general idea that you should keep in mind。So with all these nodes in mind。

 we would like to talk about something else， which is about fonts。

 so currently probably this is not what you see。Since I am running the demo application as well。

 this gets the font size and font family from the cache， so in your case。

 let me just pretty quickly show you if we go here if I delete this。

So probably you're seeing the font size just like this， but in my case。

 this is coming from the cache。And let's try to actually install it。

 So when I first started with this application， I didn't really have this。At all。

Now I would like to go and show you this assets folder where we have some fonts。

 this is the default font coming with Expo installation。

 but we would like to add our own custom font。

![](img/3c902dbcec98786b9e863ce7af553dc4_184.png)

So first， I'd like to give you the URL。Let me copy it。 It's going to be coming from jetbrains。

So jetbrains。com/ LP/ mono。

![](img/3c902dbcec98786b9e863ce7af553dc4_186.png)

Once you get into this website， you can download the font。

 which is going to give you a zip and from there you would like to find a file so I have already installed it I'll just show you which one it is。

 let me try to copy and paste it。Into the fonts folder。Okay。

 so it's really simple you will go ahead and unzip that folder and grab this file。

 which is jetbrains mono mediumium。 Ttf。 Now we just get this。

 but this doesn't mean we installed it into our application， we need to load it。

For this we go into our layout， So let me go back into the underscore layout。

 which is our rule layout。 and here we would like to load the font。And before we load it。

 I would like to talk about a concept or something called splash screen and you might be asking what the hell is that。

 So when you are trying to log into your application right So when you open this up for a split second you see the icon right that could be in Facebook。

 Instagram to either in any application you name it for a split second you see this kind of a screen and this is what we call splash screen。

 the loading screen basically So for this I would like to write some code that will handle the splash screen so we're going to say。

Until our phones loaded， just show the sp screen and。You know， like once our phone loadeded。

 show the actual application content。So I hope I have explained it in a clean way。

 let's try to see how we can make that work so we'll just first say supply screen was imported from Expo router。

 we'll just say prevent auto hideide async and then we'll like to load our fonts which we can do it with use fonts hook and click think this is going to be coming from Expo。

They import。P oops， let's say， use plants。Which is going be coming from Expo fonts， Expo font。 Okay。

 then this is the font path that we' would like to load。 So first， the name is called as jet brains。

Moonno dash， medium。And this is the path that we would like to import it。 So we'll just say require。

 go under the assets， under the fonts， and this is the exact same file that we have just installed it。

 which is going to give us a variable， so's say con。We're going to destructure this phones loaded。

So this is a bullion that we' would like to check， lets say if。Once loaded。

 then you should go ahead and actually say splash。do hide async so once our phone loadeded。

 we would like to hide the supply screen so that we can actually see the actual application content and we don't really want to add it like this。

 but instead I will go ahead and wrap this with a use callback so that it is memorized in cached。

Let's go ahead import the use callback from React。This is on layout root view and we are going to pass it into our Sa area view component。

 So let's say on layout， we would like to call this function and if you are wondering what does that mean。

 what this does， Basically it is invoked on mount and layout changes with Okay so let's go ahead and save。

Now you should be able to see the exact same font that I have if you cannot see， go ahead。

 maybe kill your application or press R， it should reload it。And we are able to see our font。

 Now4 as split second。 I'll just press R like we can see the supply screen， right， This is the icon。

 oops， let's just press once again。 This is the icon that Expo gives you。

You can see it from the assets， images， and it is this splash icon dot PG。

 Now you can use this completely like definitely， but I have prepared something for you if you want to get it。

 I will go ahead and delete this one。Let me just say， delete this。

And I will provide the one that I have prepared so I have just drag the en it。

 It is again called splash dash icon。 This is the actual icon that I have prepared and if you toggle the status bar visibility you can see this is the recommended size 10 to 24 square you would like to get this size for the splash icon and if you ask like how did I make this open it is command shift P and I'll just toggle this so that it doesn't take any space。

So let's open up the terminal， I'll press R。Hopefully we should be able to see the splash icon。

 but looks like we can't， so I will go ahead just say command C。

Kill the application and restart this。Okay， so for some reason this does not work。

 Maybe it is in the cache。 It should be cleared。 Let's see how we can fix this。 Now。

 what I'll be doing is to kill my terminal and clear this up measuring the left hand side。

 I would like to start my application from scratch but clearing the cache。

 So you say MPx Exp start dash C。Hopefully， this will clear the cache， as you can tell。They are。Okay。

 still we can get this icon， I don't know why previously it has worked for me。

But at the moment it doesn't， maybe I should kill the application， restarted again。

Okay so it does not work let's go ahead and try to find another solution so since it is not working as expected let's take a look at the documentation so this is something expected they basically tell us do not use expogo to test your sp screen you should get a preview built or production build to test this out otherwise you might get this kind of conflicts that we just got so we can assume that it is going to work in the production。

And then here are some notes about a splash screen icon， this is the recommended size。

 this is what I have mentioned a couple of minutes ago。

 and then it should be a PNG file without a like with a transparent background and if you want to configure your you know colors images you should visit the app adjacent file where you have all kinds of configurations about your application so you can change the Android icon you can change the icon for all devices and then for the splash screen。

Now in our case， we would like to actually change these icons as well。

Wwhich is the icon Png as well as adaptive icon do PG So you might be asking what are these So this is the main icon for our application and adaptive icon is also like the same icon but it is used for newer Android devices So older Android devices will use this one and i devices would also use this one but newer Android devices are going to be using this adaptive icon So what I have done is to actually prepare these icons as well。

 which is going to be the same thing with this one So I would like to just copy this paste it once again and I'd like to delete the icon PG and I'll delete this adaptive icon do Png as well So I'll just copy this paste this once again let's say this will be icon Png。

And adaptive。Iconda PNG。Hopefully this should be our new icons。 Now we cannot really see it。

 I believe。Let me just open up my terminal and rerun this。First， we should press I。 Okay。

 so I think this supply screen ver for。Like， let me just double check。 Okay。

 our supply screen now started to work。 And if we take a look at the expo。

Can you just go back if you press command M。No， that was not correct thing， let me bring this back。😔。

Is it command D， Okay， we can go home。Can we refresh this。Okay。

 let's clear this out and restart once again。I I am looking to if it is going to work with the newer icon。

So press command D。Kuan。Okay， why it does not work。Commentee， let's go home。 Okay。

 here we can see our icon also changed， and it is working as expected。 Let me give you some notes。

 and hopefully， we are going to。En this section。Under the notes， I'll get the。Notes about the icons。

Okay， so here you have it。IconpG versus adaptive iconconpng So this is the standard app icon that appears on most devices。

 It is the primary icon for your application and this is the recommended image size it is the same thing for adaptive icon and adaptive icon has been introduced in Android 8 this is specific to Android devices and if you don't provide these icons your app will still work but it'll use exposed default icons for a professional application you definitely want to include these icons with your custom icons right okay there we go。

 the very last note that I'd like to include or some resources So if you want to find hundreds of other thirdpart libraries you can visit react native do directory So let me show you this pretty quickly。

So here you have a bunch of different packages that you can take a look。

 explore so on and so forth and if you want to handle some gestures which are a great way to provide an intuitive user experience in an application so there is a package for this as well you can learn more about these under the documentation and so you can add like different gestures like pan tab rotation so on and so forth and there is one more package that Id like to mention which is react native reanimated where you can create smooth animations so let's go ahead and take a look at the documentation。

 this is really really common like commonly used if we just search for NPpm install react native reanimated like weekly downloads over 1 million which is insane。



![](img/3c902dbcec98786b9e863ce7af553dc4_188.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_189.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_190.png)

And you would like to definitely keep this in mind while building applications So these are the some resources that I'd like to mention before we end this section so with that I'll see you in the next one Now let's go ahead and implement comment functionality Currently everything is hard codeed and at the end of the day we would like to have this kind of a model when we click to this comment icon where we can see the previous comments and we can add our own comment right so let's see how we can make that work。

First things first， I would like to add my convex functions so that we can really。

Consume those functions in a couple of minutes。 You can put it into the post Ts file。

 but I would like to actually put it into the comments star Ts file。 It doesn't really matter。

 but this is the convention that I would like to use。Or not a commission， but it' just my preference。

 So let's create a function to add a comment。 You can pause the video and try to do it by yourself and then watch my solution。

Let's say this is gonna be a mutation， right， We'd like to add some data。

 And if you want to add a comment。We need to get some arguments。 Let's say the content。

 which is the comment itself， which will be type of string。

 Let's say Vita string and we should import the V。From convex values。

 then we'll like to get the post ID so that we know on which post that we are adding a comment。

 then we' would like to have the handler function。Which is going to be taking the context as well as the request。

 I mean， arguments， not request。Let's go ahead， open up our function and try to build it。

 So I would like to get the current user with our。Function。

 let's say await get authenticated user and pass the context as the argument。

 So we would like to get the post。 let's say await context that Db do get。

 and we're going to put the post ID， which is going return the post itself。Let's add an if check。

 we'll just say if post not found， let's throw an error and by the way you can also return a conx error。

 I think I haven't mentioned this， but this is also available。

 then we'll like to create the comment itself so we'll just say go into the comment table and try to insert a data which is this one。

 this is the comment author， this is the post and this is the content then this is gonna to give us the comment ID How do I know well when you hover over this it will tell you that the return statement it returns you the ID of the new document。

Okay so I'll just assign this to the comment ID we would like to increment the comment count by one。

 so I will go ahead edit it with a comment since we are updating webu page。

 this is the post that we would like to update and this is the field that we would like to update right post comments plus one then we would like to create a notification if this is not my post so I'll go ahead add my ifche I'll say if post user ID is not equal to my ID I would like to insert a notification which is type of comment and here is the related data and at the end of the day we could return this comment ID from this function。

So this is the entire mutation that we have。 The other one that we would like to add into this file is to get comments。

 which is going be a query。 So I'll go ahead to say export con get comments， which will be a query。

Let's get this query from our imports and we' would like to get the like pass some arguments so that we know on which post we are going to get the arguments and this will be post I。

 which is type of。Posts and we will just say our handler function。Let's grab the context， oops。

 context and arguments。And try to build the logic。 So we'll say con comments。

Let's say await rate that context。Wait why this is not happy。 Okay， it should be like this。

Context that T the query。The comments table with an index。 So let you say dot with index。

 And if you remember， we have a index called by post。 So we'll just add our callback function。

 Let's say query dot equal to this is the field， and we would like to collect all the posts。I mean。

 all the comments。There we go。 This is going to give us all the comments。 Now。

 there is one more thing we would like to do。 So if you think we should just say return comments。

 let me tell you， my friend， you are wrong because in the comments we have no info about the user。

 The only thing we have is the user ready， but in the comment section we would like to show the。



![](img/3c902dbcec98786b9e863ce7af553dc4_192.png)

User image as well as the user full name right and we need to just go ahead fetch those info right and let me provide this to you this is something that we have done previously right we just said posts with info now we'll just say comments with info so we got all the comments and we're going go ahead map through each comment and for each comment we would like to get the user which is going to have the full name as well as the image field。



![](img/3c902dbcec98786b9e863ce7af553dc4_194.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_195.png)

This is going to be our query that we'll be using in a couple of minutes Now let's go into the post at TsX I would like to create a couple of different states plus string everything just like likes count。

 I will duplicate this and we' are going to have something called comments。Count。And let's say set。

Think we should say。Comments count and this will be post comments just like that。

 and then I would like to have one more state just to check if the comments model will be visible or not So I'll just say show comments and by default this is gonna be false if this is true we would like to show a model I'll just like I'll just scroll to the very bottom of the file just before this view I will add a component called comment let's say comments model and this is a component that we're gonna to create just in a second let's say this will take the post ID。

Let's say， post dot I。Is this going to be visible or not。

 We will depend on the state called show comments。 And when we close this。When we close this model。

 this state should be false。 so here is the function that we pass。 and finally。

 once the comment has been added， we would like to increment the number of comments。

 So here it says set comments count， let's see。It should be S。 okay， I had a typo。

 Now this should be happy with us， but we don't really have the component。 That's why it crashes。

 Let's go under the components。And create this the Ts x。Let's say R and F。Save it。

And try to import it in this file。Okay， let's go ahead and try to build this common model component。

 So first， I'd like to add my props as my type， right， So to say type comments model。

Just going to be a type。 So here I would like to just copy and paste all these four values。

 So we're going to have a post I， which is going to be type of。Posts I， right。

 then we'll get the visible on close and on comment added functions。

 Then let's go ahead to say this is the object that will like to this。 Now this should be type save。

Let's get all of them。 So this is Typescript specific。

 and we would like to have a state to keep track of the comment itself。 So when we are typing in。

 we would like to have the state so that we can update it and initially it'll be empty as you can tell。

 then let's try to get our query， So let's just say con comments。

 we'll just say use query coming from convex， we'll just say API。Butt comments。

 that get comments and this is taking an argument which is which is going to be the post ID。

 Then we'll like to have our mutation。 So I'll basically duplicate this and I'll say add comment。

This is going to be a huge mutation call。Just like that， API comments and let's say， add comment。

This takes the I think this is not the place that we should add， so for the mutations。

 if you remember when we call it we would pass those right。

 so this is the place to actually pass these arguments not here。Okay， with this in mind。

 I'll just have a one more function。 Let's say handle add comment。

Let's say this is going to be an async empty function for now we are going to build the logic just in a second。

 Now let's try to build the actual UI。 So when we collected this it should open up the model right。

 but we don't really have a model in the first place。

 Let's go ahead and try to build it and for a model there's a component。Exactly called as model。

 which is coming from react native and whatever you put inside of the model becomes a model。

So let's just try to see how this would work。 We will say this will be visible depending on this visible state。

 right， this probe that we are getting， and then we would like to have a couple of different things。

 let's say animation type will be slide so it'll just slide from the bottom and let's say this will be transparent。

Say it will be not false， but true。 Then we would like to have on request close。

 We would like to add our own close function， right， And then let's try to build the actual。

Component So first things first， I would like to have my keyboard awaiting view。

 This is something that we have mentioned previously。 Basically。

 when we want to open up the keyboard， we want this input still be visible。



![](img/3c902dbcec98786b9e863ce7af553dc4_197.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_198.png)

So that's why we are using this component。And I will get some props like the behavior。

 as well as the style， let's say platform do O and styles。I think this styles will be coming from。

 Let me just double check。 It should be from the feed styles。

 Then we would like to have the model header。Let's save to get this formatting。

 we'll go into the keyboard avoiding view， paste this in， save this。

 and let's try to import our components， so touchable aacity， which will have this close icon。

 let's get the colors。And in the comments title。 So basically， you have just built this part。



![](img/3c902dbcec98786b9e863ce7af553dc4_200.png)

Alice try to build the remaining part。

![](img/3c902dbcec98786b9e863ce7af553dc4_202.png)

So after this view， we will just say if comments are equal to undefined。

 which means we are in the alling state here we will like to return something else。

 we will like to return something else。 and in this case， we will like to have a loader component。

We're just going to have this。Activity indicator， which is size of large。

 And then here we would like to actually return our comments。 and as you might guess。

 we would like to use a component like flatlist。Okay。So if youll remember we have this data field。

 where we'll just say map through the comments and render item， so each comment。

 go ahead and create or render a comment component。We don't have this。

 but we are going to build it and let's add the item。As the comment field。

So you can call this anything right， but it should make sense so that you know what you're sending and this is the item that we got then we'll like to add the key extractor so I'll just put it right here and then I'll just give some styles。

Into the container。Okay， now let's try to build the comment component。

 which is something that Id like to create under my components folder。So let's say comment that TsX。

And this has no logic at all other than styling and Ui。

 So I'll just paste it around 30 lines of code and let's take a look at it。

 So this is using date fnS package。 Let's go ahead and install it。

 So let's say MPm install date dash FnS。So we'll be using this to be able to format our dates and let's say MPX Expo。

And rerun our application。Okay， so basically this has a view and image with some styles。

 this will take the comment author and then we have。You know the full name of the author。

 the comment content as well as the comment time and this will go ahead and format the distance so that it will say something like two hours ago。

 one hours ago， so there isn't anything called one hours ago it should be one hour ago but you get the point Okay let's go ahead and try to import the comment。

Component。Now， I don't know why this is not really happy with us。

 and I think it is because I haven't imported it。 So here we should be getting it from our comment pile。

Now let's save okay， and let's try to keep building it where we just have only one more view。

 I'll just say view as at the styles， which is going to be comment input。

 Then inside we are going to put a text input So again this is a component I think we are using this for the very first time。

 or I don't know if we have used it previously。Yeah。

 I think we used it in the caption section right here when we try to add a caption。

 but basically we got a style， a placeholder and then the text color of the placeholder value on change and this could be multiline then。

Like after this， we'll just have a post button， which is going to be a touchable capacityac。

When we collect it， we' are going to call this method that we just have above and then it'll be disabled if we don't really have a new comment content and we just have some additional styles。

Okay， now when we collect it， nothing happens because we never call the function when we collected this icon。

 let's find it。 Which one is that we should be under the actions。So right here。

 when we click to this chat bubble outline， let's say on press， it should make this state to be true。

 let's save and fingers crossed。 Hopefully it should work。 There we go。 We can see our model， right。

 It is it just sizes down。Or like it just animated from the bottom of the screen。

It works without any issues， so let's go ahead and add something okay。But if we try to post it。

 nothing will happen once again we don't have the function logic yet。

 so let's try to build it and I'll just try to walk you through it。

 So first things first we'll just say if you don't have a comment content， just return out of this。

 but else we'll like to have a try catch。In the try。

 I'll just say call my mutation which is add comment and these are the fields that we'll like to add or the arguments。

 so the comment content as well as the post ID once this is done。

 we can just say set new comment to be reset it and then we can just call the on comment added function then in the catch。

Let's just put a console log。Like this。Let's save and try to send our very first comment。

 I'll just say， hey， nice post。

![](img/3c902dbcec98786b9e863ce7af553dc4_204.png)

Let's post it。 Okay， so there we go。 we just got that。 let's open up our database。

 This post has a new comment。

![](img/3c902dbcec98786b9e863ce7af553dc4_206.png)

Under the comments， we should be able to see the document。

 but we shouldn't get a notification because I just commented on my own post。



![](img/3c902dbcec98786b9e863ce7af553dc4_208.png)

So this is the account that I am currently logged in behind the scenes I just logged out from the other account。

 but this is the account that I am logged in， so just keep this in mind this is my actual post and now let's see if I just try to open up my keyboard with command shift K。

Okay， so I just wanted to show you that this is actually avoiding the keyboard view， right？

So we are able to see the content， it is not overflowing if you were to use a regular view。With arch。

This behavior， let's see what would happen。It overflows right， you are typing your comment。

 let's just say hey， but you are not able to see what you have just written。So with this in mind。

 let's save。And add one more comment。We let you say post， here we go， and our date is formatted。

 by the way， if you can see。Is there anything that we are missing？

I don't really think so Well actually we have so here we just say we all two comments。

 but this is a hard coded value right we should fix this actually。

 so we need to get the number of comments and here thankfully we have a state where we just say comments count and when we add a new comment we are actually updating it so it will always work properly we can go ahead delete this and make it work。

Dynaically， so let me just grab this， paste it。So instead of just two， we have added this part。

 let's save。Let's try to add one more comment， to say one more。Okay， it's been added。

Here we can see we all three comments and when we click to this， it should also open up the model。

 let's try to add it here as you say on this touchable capacityacity， on click or on press。

 it should open up the model。Okay。And the other thing that we are missing is this two hours ago。

 which should be dynamic， not hard quoted， so let's say format distance to now。

 get this from dataFS and this is the time that we would like to format So if you save this is actually one day ago when we post this it was yesterday and just make sure this is coming from date dash fS。

And then I would like to scroll to the bottom where we show the。Comments count。

 instead of showing this always， what I'd like to do is just wrap it with an if check。

 So because imagine if we don't really have any。Comments， it'll just say we all zero comments。

 which doesn't make any sense。 So I'll just go ahead and say if。Comments count is greater than0。

 only then show this part。Let's go ahead and wrap it。Okay。

 so with this in mind that's going a bit for the common functionality， everything works as expected。

 we are able to even send the notifications and let's actually make sure that it is also working。

 I'll just log out from this account log in as the other account。And I'll just try to add a comment。

 Okay， like it doesn't click， I think I just， I just need to press command shift K to get rid of that。

Effect。Okay， now I can click to it， let's open up our database。

Take a look at the notifications and add a comment。 So this is not my post。

 I should be able to get a notification。 let's say， oops， what the heck is happening。Let's say。

 you know a1 to 3， it doesn't really matter， let's post， here we go。

 we can see we just got a comment type notification。And here is the receiver。 Here is the sender。

 It works without any issues。Okay， so in the next section。

 we are going to add the add bookmark functionality。So for the bookmarks。

 let's go ahead and create a file under the convex， I'll just say bookmarks。

 Ts and we would like to add our mutation as well as the query。

 So let's start with the mutation This is going to be called as a toggle bookmark because with this single mutation we should be able to both bookmark and unbookmark so I'll go ahead paste this because this is something that we have done multiple times and I'll just walk you through it let me import everything。

Okay， so this is a mutation where we take an object we'll have some arguments so that we know which post that we are trying to bookmark and then were going to get the currently authenticated user and we would like to just check if this is already bookmarked or not。

 we're going to query it right with an index and then if it is already existed we are going to remove the bookmark but else we are going to insert it and here we will return false or true to indicate the newest state。

So this is the mutation。 Now let's go ahead and try to get the bookmarks。

 which is going to be a query。 I'll just paste it and walk your through。Okay。

 so we got the currently authenticated user and we get all the bookmarks of this user。

 but if you take a look at it under the bookmarks， we don't really have any information about the post other than post ID and this is not enough because let me show you the image。

Under the bookmarks page。We would like to see the post image， right， and for that reason。

 we are going to do the same trick that we have done previously we are going to get the。

Resources with the information， So we'll just say promise at all map thread for each bookmark。

 get the post and return this out of this query。I hope that makes sense these are the things that we have done multiple times。

 so I just didn't want to type this out along by line Instead I have just explained everything。

Now with this in mind， let's go into the post component。

And create a function called handle bookmark just like above for the like function。

When we click to this icon， we are going to be calling this function and let's get our mutation what you say toggle bookmark。

Use mutation under the bookmarks if you wanted to， you can put it under the posts。

 but I'll just go ahead and add it under the bookmarks。So now here in this function。

 I'll just call my mutation， let's say a wait toggle bookmark and we're going to put the pulse ID and this is going return the newest state and I will call this as new is a bookmark and then we're going to set our state with it。

 which is going to be set is a bookmark， but seems like we don't really have it。

 I will duplicate this。 let's say is a bookmarked。And set is bookmark。Just like that。

 this is going to be a post that is a bookmark。Okay。

 hopefully we should be able to say set is bookmarked with this。

 but now when do we call this function？Well when we collected this icon called bookmark outline。

 so here I'll just say on press call this function and we don't really want to see this always。

 we would like to check if it is already bookmarked or not if so we're going to see the bookmark icon else we're going to see this one。

Okay， let's save， take a look at the database， let's just put them side by side。

 we don't have any bookmarks at the moment if I click to it。Here we go。 It has been added。

 The icon has changed， and I can。Like on book market。Okay。

 looks like everything is working without any issues and next we are going to add post deletion。

 so if you want to delete a post， we should visit the convex folder and try to add a mutation and I will add it into this file called Post dos。

So I just say export con delete post， which is going to be a mutation。

 we would like to take some arguments， which is going to be the post ID so that we know which post that we are trying to delete and then in the handler function。

 we would like to delete it。So first， we're going to get the currently authenticated user。

 and then we'll like to check。I mean we would like to fetch the post that we are trying to delete if it does not exist。

 then we can throw an error so I'll just save to get this formatting and then before we try to do anything I would like to just verify ownership so I'll just check if the current user is the owner of the post if not we are going to throw an error so I'll just say post do author is not equal to the current user then return an error。

 but else we would like to delete the post but immediately deleting the post so instead of immediately deleting it。

 we would like to do something else。And let me tell you what that is。

 so we would like to delete all the associated likes in this post。

Right so there might be 200 likes which are documents that we are storing。

 so we would like to go ahead and delete every single one of them。

 then we would like to delete all the comments as well as the bookmarks So I'll just go ahead add these。

So this is what I have just added as well as the likes。

 then we'll like to do the same thing for the bookmarks。

Okay so this is what I have just pasted this is really like almost the same thing that's why I don't really think that we should be explaining this and once we have done all these we would like to delete the image from our storage so I'll go ahead add this line and then finally we would like to delete the post itself from the table right so we have a bunch of different information about this post we would like to delete it and here I'll go ahead paste this line and I think I have mentioned this previously that we need this storage ID fields on the post and I said we are gonna need it when you want to delete the post and here is that exact moment here we just say context storage deletes something and here is the thing that you would like to delete then we'll just delete the post itself and finally we can decrement the user's post count to by one。

Which is going to be the current user。 And here will just say math dot max。

 And if you are wondering why this is the case， Basically。

 this always make sure that the number of posts at minimum could be 0。

 So imagine for some reason this part。Eals to， let's say， minus2。

 This is going to get the maximum value out of these， which is going to be 0。

 So the posts will always be 0 at minimum。I hope that makes sense。So with this。

 everything should be good to go I'll just add one more comment here called delete the post。

 Now this function could be definitely written in a better way。

 This is the simplest way that we can do and it doesn't really look that bad You can obviously optimize it but here is what we have We are just checking for the ownership deleting all the likes。

 comments and bookmarks that are associated with this post then we are deleting the file from the storage。

 deleting the post from the table and finally updatinging the user' post count。

Now that we have everything ready， we can go ahead and actually。

Call this when we click to this button and just before we make this work。

 we are going to need one more query that is related to users。

 so let's just type this out and then I'll explain what this does so let's say export Con get user by Cl ID。

which is going to be a query and our argument， as you can tell will be the clerk ID。

 so let's say ags pass this clerk ID， which is going to be type of string。

 let's import the query and we'll just say have a handler function。

Which will take the context as well as the arcs。So we are going to pass the clerk ID of a user。

 and it'll give us the。User that is stored in the database So let me explain this might sound complicated。

 but its actually pretty simple， So we have two different users right。

 we would like to let's say get this user we are going to pass the clerk I of that user and it will give us everything about this user such as this complete document and let's try to see how we can make it。

So I'll just say con user he'll say I wait context。 Db。 get or query I think。

 because we are going to query the user's table and we would like to query this with an index。

 which is called as by clerk ID， this is something that we have created in the schema file right。

 this is exactly what we have done and we would like to get the unique value you can also say first。

Let's use unique this time。Then were gonna return this user。Okay， now you might be asking。

 why do we need this function， how can we use this？So let's just see。

 we're going to go into the post component。And there is a hook that is coming from Expo or clerk。

 I should say， let's say use user。And we's say con。 Now this gives you a user state。

 Let's console like this。 the user is here。And put the user。Open up the terminal。

 so here we can see this is the user object。I know this looks really weird， but user is here。

 There is a lot of different fields。 We would like to get the ID in that user so that we can call our query to get the。

Convex equivalent of it。So let's try to see I'll save。And then just try to call my query。

 So'll say use query。And I'll say。You would like to get the API that users that get user by clerk ID and this wants us to pass an argument which will be the Cl ID and this will be user。

 ID。So we don't really need this one。 Now， here we can see the user could be null， right。

 What we would like to do， we'll just say。Let's delete this for a second， or I think。Here。

 let you say if we have a user， then pass this， but else just skip this call until we got the user Now we don't really have any errors。

It is working correctly。And this is going to be equal to let's say cost， you can call this anything。

 I'll call this as convex user。Or specifically， we can just say current user。

So this and this is the exact same user， but this is the user that is stored in clerk and this is the user that is stored in database。

 and this has different fields than this one right such as number of followers following so on and so forth Cl doesn't really store those for us。

I hope this makes sense this is the best way that I can explain then we would like to use this field and check if we are the author of the post if not we will not be able to delete it but if we are the owner we can delete that so here if you realize we have a to do where we would like to fix it now。

Allright， so let's go ahead and delete that and unment this。

This is the three dots icon that look like this， but we'll like to show one of these at a time so here I'll just add a comment。

我 say。Or actually， actually， I'll get it from my comments。If I am the owner of the post。

 show the delete button and I would like to grab this and I'll just walk go through it。So。

 we will say current user。Was that a question mark？Alright。

 so we you say if post author is equal to me right if it is me if it is my post。

 then I would like to show this trash outline icon。

 but else I will show this three dots and currently as you can tell it already worked this is the this is a different account now I'll try to log in with this account let's go back or I should。

Well god。And I will log in as the post owner。We should be able to see the trash outline there we go。

 it just updated and we should be able to delete that。So here I'll just say on click or on press。

 we're going to call a function called handlele the leads。Let's say， yeah， handle delete。

 I was going to say handle delete post， but this should be good to go。And let's create our function。

 lets say， handle the leads。And here in this function， we're going to call our mutation。

Was scrap that。I'll see。Delete post。It is going to be coming from the posts file。

And we should be able to call it in this hassing function。Now we could have to try catch。

 I'll just accept what AI gives me。 We are going to call our mutation with the argument。

 let's save and I'll just press this。It's been deleted here we go， and it says no posts yet。

 let's take a look at the database。Z posts in this user should have zero posts。

It's been updated and that means everything is working as expected now we don't really have any posts just to have something on the application。

 let's go ahead and create some， I'll just say choose。And let's say ABC， or I'll just， you know。

 just add anything。This should be posted， let's add one more。Okay， so one challenge for you。

 when we add a post， we take the user to the homepage。

 but we don't really clear the state so you can do this， let's go ahead maybe I can do it as well。

Once we share this before we take it to here， we can just say it set and let AI to complete it。Okay。

 I can add these。This is how we can make that work。 Now let's just test this out once again。

 I will add an image， let's say choose。Let's say， hey， this is。Wangyi。Weekend trip。

Let's say this was。 and let's share。Now， if we go back， our state should be updated and here we go。

 we can like add a comment book market。Let's you say。Nice。Okay， everything works as expected。

And next， we can move on with the bookmarks page。 Well。

 just one more thing before we move on to the next section。

 I just realized I didn't show you the file storage。

 So what happens if we try to delete a post We didn't really make sure that if it has been deleted from the storage。

 I'll go ahead and delete this one Now it is gone from here as well， So you can just。

Make sure that it is working without any issues， so now it is actual time to go ahead and build the bookmarks page so to be able to build the bookmarks page first we just need to visit that file。

And let's try to make this to be capitalized so that we are consistent in our codeb。

 and then we need to call a query， which is the one that we have already built under the convex folder and this is our query。

Wwhichch we call this as get bookmark posts， so this is going to give us all the bookmarks of the current user and we would like to take it and consume it in this file so since we since we already learned how to use a query。

 I'll just paste this in so we would call the use query， get the API and get the related query。

And if this is in the undefined state， that means you are in the loading state。

 so this is how that work in convex and let's get this load component that we have built previously and then we can also get a not found state so we'll just say if the length is equal to0。

 we' would like to show this simple component that I'll just provide。

So this is a simple function here we have some styles。

 and it just basically says no posts yet or no bookmarks yet。Now， let's save and。Take a look at it。

 I think we have a bookmark， yep， that's why we see this return statement if I unbookmark it。

So I don't know why this did not update it。 let me just reload our application。Let's go here。

 alright， no bookmarked post yet， let's add this。Now we can see our bookmarks and let's try to build this now。

Well， I just want to speed up the process a bit。 So that's why I'll just delete。This， completely。

And give you some。You know， code。 So I'll just say we。

Which we have the style and this is coming from Fita styles and this is using the container class and then we would like to have the header at the top so this paste is save and this is what we're going to see and then below it we would like to render the posts and for this I'll be using a scroll view so I think youll just have less bookmarks so it could be a good option to use scroll view but if you wanted to we could use flatlist as well。

So here I'll just get my code from my notes instead of typing this out。I can walk your through。

 So this is a scroll view component with these styles， and for。

The content will just say bookmark post star map。Get every single post。 And you can just say。For now。

 let's just say we're going to have a real component。And if you try to say， you know， post the。

 I don't know， like caption， you're going to see that this will complain。For a second。

 if you don't add this question mark。 Now it， it's because it thinks that this could be null。

 And just to get rid of this error， you can either add a question mark or maybe a bit better option would be。

To make this a function and add a if check。 So here I'll basically say if there is no post。

 just return null， but post is not equal to null。 Then we can just return a view with the image。

 Let's get this。Import the image from Expo image because you are trying to cache it and this cache policy has a bunch of different options this is the one that makes sense in this use case。

 but you can take a look at the other options。Here we can see we have like four in total。Okay。

 let's save here we go。 This is the post that we have。 Let's try to unbook market。 It's been updated。

 Let's try to add it once again。You know， it just works without any issues。Okay。

 so that's going to be for this screen as well。 Next we can move on with the notifications。



![](img/3c902dbcec98786b9e863ce7af553dc4_210.png)

Which looks like this at the moment。

![](img/3c902dbcec98786b9e863ce7af553dc4_212.png)

Alright so to start with notification screen， let's go ahead and find the actual file which is gonna be this。

 but before we try to build the UI， let's try to build the query that is gonna give us all the notifications that we have for our account and for this we would like to create a convex function which is gonna be a query you can put it in any of these files but I believe it would be better if we go ahead and create a file called notifications do yes let's shrink a left hand side and say export con let's say get notifications that's gonna be a query you can pause the video and try to do it if you really wanted to but like let me just go ahead and build it so since we would like to get every single notification for the current user we don't really need to pass any arcs So we'll just say handler where we'll just take the context and we would like to build the logic。



![](img/3c902dbcec98786b9e863ce7af553dc4_214.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_215.png)

So first things first， as always， we would like to get the authenticated user and then we'll just get the notifications so let's say con notifications and let's await this call。

 context D query where we would like to go under the notifications table and let's try to query it query it with a index so I'll just say with index and for this we'll just say by receiver and we'll just say if we are the receiver give us all the notifications and this is how we can do the current user ID if it is matching with the receiver ID we should just go ahead and collect all the notifications and I would like to sort this before so'll just say order should be in the descending order so we would see the latest one at the top and the oldest one at the bottom。



![](img/3c902dbcec98786b9e863ce7af553dc4_217.png)

Here we can see it says two days ago， and this is like eight hours ago， it is sorted in this order。



![](img/3c902dbcec98786b9e863ce7af553dc4_219.png)

Okay， now if you think。We say like return notifications， this function is done。

You would be wrong right， because if you think about it once again under the notifications。

 we don't really have any information about the post。

 the only thing we have is the post lady in the same way we don't really have any information about the sender other than their IDs。

 but we would like to get more info about them。

![](img/3c902dbcec98786b9e863ce7af553dc4_221.png)

And let me show you what I mean， so this is the notification sender right。

 we'll like to get their profile image as well as their username。

 and in the same way we'll like to get information about the post。Okay， so I hope that makes sense。

 This is something that we have done actually in the past。

 where we where we would just say notifications with info。



![](img/3c902dbcec98786b9e863ce7af553dc4_223.png)

Right， we have done this in our other queries。So in the same manner， I'll go ahead and create this。

Variable， then we're going to say pros dot all。 and we'll just say。

Notifications map for each notification。 We would like to run this callback function， right。

 and we'll just say con。 Let's first get the sender of the notification。

 And this is how we can do it。 This is gonna give us the sender。

 And then I'll just say let post will be equal to null。And let's duplicate this。This will be comment。

Now you might be asking， why are we doing this， I think we'll just see this in a second。

 Let's say if our notification has a post lady， That means this is related to a post and we are going go ahead fetch that post will' say post will be a await context D dot get this specific post and let's say if notification is。

The type is equal to comment。 And if it has。A comment ID。

 we would like to go ahead and get the comment itself so that we can display it right here， right？

Okay， so I hope that makes sense。 Now if you don't really add this part。

 Typescript will be unhappy with you。 So that's why we are adding it。 And then after this if check。

 we can go ahead and return an object。 So we'll just say get everything about the notification but on top of it we'll like to add the sender information So we'll just say let's give the ID well like to give the user name as well as the image So here it says sender could be null but we just know that if there is a notification we will always have a sender right so I can go ahead wrap this with。

Brackets， and you say exclamation point， this will never be known。Okay， finally。

 we would like to say。Like return the post as well as the comment for the comment。

 I you say get the content。Okay， just like that， this should be good to go and at the end of the day we will return the notifications with info。

Okay， let me just make this entire screen zoom out so that you can see it clearly。

So this is our entire query。And I hope this makes sense。

 like we cannot just return the notifications as it is。

 we would like to get it with the info so that we can grab the post。

 comment and the sender information。Okay， I hope that makes sense， let's zoom in。I will shrink this。

Okay， now this is the query that we have just built。

 now let's go into the notifications under the tabs and try to build the UI。Before we get into it。

 let's say we would like to use a query。Just like this。

 we would like to go under the notifications file and get our notifications。

 This is the query and while we are in the loading state， we can show a loader and once again。

This is how it works in convex if a query value is equal to undefined that means youre in the loading state and let's say if we don't have any notifications。

 you would like to return this component which is something that I will provide it's about five lines of code just like this。

Let's get these styles， but this like these styles are going to be coming a。Okay。

 they're going to be coming from a file that we'd like to create。 So you say notifications。

That styles。Not yes， and you can grab this from the source code。

 And if you don't have the source code， you can just。You know， take a screenshot。And type this out。

 I'll just show you the entire file。O。So these are just some styling， let's get these styles。

It the ion icons， as well as the colors。Okay， so currently I think we have some notifications。

 that's why we cannot see this UI， let me just press R so that it is being reloaded。

And let's go into the notifications page okay， so it looks like we've got some notifications。

 but let's just say if this is the true case， this is what we're going to see and please feel free to update this UI。

 this is not looking that good but it's just good enough for a placeholder。Okay， let's save。

S the terminal， shrink this one， I would like to go ahead and just update this return statement。

 so I will have my view， let's say style will be styles that container just like as always。

 then we would like to have our header component。So I'll just say styles that header and here this is our title where we say notifications。

 then we would like to have a flat list， you can also use a scroll view component。

 but for in my case I'll be using a flat list。

![](img/3c902dbcec98786b9e863ce7af553dc4_225.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_226.png)

Okay。Say flat list， imported， self code and the data that we'd like to map through will be notifications for every single item we would like to render this function。

 let's say。We' are going to get the item。We are going to create a component called notification。Item。

And we are going to pass the notification。As the prop， which will be the item。

Then let me just grab the key extractor。So this is the key when we use in reactact。In react native。

 it is equal to a key extractor。I don't want to show the vertical。Scroll indicator。

 so I'll just say false and finally， let's give some styles。Now， if you save。

 obviously it will crash， so let's go ahead and create this component。So notification item。

 this is gonna take。A prop。 let's say it will be the notification。 Just like what we have here。

 For now， let's just say type will be any later in the video。 we can fix it。

 And let's say we would like to return this statement。 And this will be only U I specific。

 So I'll just have a view。Okay， let's go ahead and add some styles。

So the first style that we' would like to have will be notification item。

 Then we are going to have a。Another component called view and this time I'll again get the styling just like this。

 so I don't really want to type this out just to save a little bit of time there is no logic at all and let me tell you what we're going do。



![](img/3c902dbcec98786b9e863ce7af553dc4_228.png)

So here I would like to wrap this component with a link so that when we click it。

 this would take us to the profile of this user and。



![](img/3c902dbcec98786b9e863ce7af553dc4_230.png)

Let's try to build it。 I would like to copy this link。

 I think it is around 10 lines of code and I will walk you through it so we have a link that is coming from Expo。

Currently， we don't have the user profile， so I'll just take them to the notifications later in the video。

 we are going to fix it。 So I'll just say to do fix later and we will have touchable capacityac。

 We're gonna have an image from Expo image and。We're going to pass the source style content fit。

 and then we are going to have this view。And like this is the kind of like。

It looks a little bit complicated， but it's basically if in else statements a couple of times。

 so we say if notification type is equal to like， then show a hard icon。

 but in the else' case check if the notification type is equal to follow if so show this icon but else go ahead and show this one so depending on that we are going to see either this one。



![](img/3c902dbcec98786b9e863ce7af553dc4_232.png)

Or this And this one。

![](img/3c902dbcec98786b9e863ce7af553dc4_234.png)

So this is what we have just done， let save。Go into this page。 Here we go。

 We have two different notifications， one is like the other one， a comment。Okay。After this view。

 we would like to and actually after this link， we would like to add one more view。

So I'll just say review and turn this off。😔，And this is going to be actually notification info class。

So I would like to go ahead and get one more link。So please feel free to type this out or grab it from the source code if you don't really want to again we are going to fix this for now let's say it'll take us to the notifications because we don't really have the users page so let's say to do fix later and let's say this is going to give us the username。



![](img/3c902dbcec98786b9e863ce7af553dc4_236.png)

Then after this link， we would like to have this text。

 so it'll say either they have commented or they like your post。

Or like started following you and we are going to put these dynamically once again。

 depending on the notification type。

![](img/3c902dbcec98786b9e863ce7af553dc4_238.png)

So I would like to go out below this link。Have a text component。Just like this。

 and I will give a style called action。And then we're going to do this conditional rendering。

So here I'll just say if notification type is equal to follow， show this one， if it is equal to like。

 show this one else， show the comment itself。Let's save and take a look at it。

So this one has commented as undefined， looks like we got something wrong。We're going to fix it okay。

 so this shouldn't really say undefined， but it seems like the address is working and after this text I would like to put one more text just to show like when this has been posted and it willll just say get this function from data FS。

And this will take the creation time。Now it is working， it says about five hours ago or one day ago。

And after this step， I mean， after this view and after this view， just。Before the very last one。

 we would like to show the image and we only want to show this if it is related to a post。

 so let me just do controlt Z。

![](img/3c902dbcec98786b9e863ce7af553dc4_240.png)

So this notification is related to a post， so we just show that in the same way。We show the post。

 but this has nothing to do with a post and we don't really show anything。

 So for that reason we need to do conditional check。



![](img/3c902dbcec98786b9e863ce7af553dc4_242.png)

So I will just say after this view， if notification。Has a post I D。

Or if it is like if notification that post is true。

 then we would like to go ahead render this part and let me grab this， which is an image component。

Okay， so notification that post image URL will be the source otherwise。

We are not going to show anything， but seems like this crashed。 Let's go ahead and rerun this。Okay。

 so for some reason， we cannot get the image， let me console log this。What is wrong with this。

 say console log。The notification。Okay， so we got the notification， we have ID field creation time。

Okay， so post is null for some reason。So why is this the case。

 maybe it is because we have posted something and we have deleted that， but when we delete the post。

 we didn't delete the notifications， so I think this is what happened。

 let me just double check if we go into the post file。When we try to delete a post。

We have deleted the likes， comments， bookmarks， but we forgot to delete the notifications， right？

Okay so I have just realized this I can leave this essay a to do for you。

 let's say to do delete associated notifications and you can pause the video try to do it and then watch my solution Alright so I have just paused the video and implement it let me show you my solution so first I have visited the schema Ts file and edit an index called bypost and just make sure you edit this index to the notifications table so once you have added this part。

We're going to come back to here and we will just fetch all the notifications by this post just like what we have done above right。

 then we're going to just do a for loop to delete every single notification。

 and now then now that this is not a to we can delete this and we can just move on with the video but since these are the previous notifications。

 we can delete them， this will work from the next like future post deletions。

 but we can manually can go into the database。

![](img/3c902dbcec98786b9e863ce7af553dc4_244.png)

And try to just delete all the notifications。

![](img/3c902dbcec98786b9e863ce7af553dc4_246.png)

Okay， let's say delete all of them and we are going to test everything from scratch。



![](img/3c902dbcec98786b9e863ce7af553dc4_248.png)

So here， I would like to just create one more post。Let's say。Some nice pick。Okay。

 so from this account， we have two different posts。 Let's go ahead， log out。

And log in with the other account， then we will try to create some notifications。

So we are just doing this for the testing purposes to see if everything is working。Okay。

 so I'm just logged in with a different account， I will like this post and I will add a comment。

 let's say。Dude， this is sick。Okay， we have added this， let's like this one as well。

And add one more comment。我 say我。😔，Like this。Now let's try to go back to the other account。

Now let me just try to log out。And we are going to check the notifications。So here we go。

 we got one like from this user on this post， we got a comment， it says dude， this is sick。

 the same thing for this comment， so it seems like everything is working。

 we cannot really see the follow notification at the moment because we don't really have that functionality implemented。



![](img/3c902dbcec98786b9e863ce7af553dc4_250.png)

But once we done this， we are going to test this out again。



![](img/3c902dbcec98786b9e863ce7af553dc4_252.png)

Okay， so for this section， just keep that in mind， we have added this index to the notification table。

 we went ahead and added this part so that if we delete a post。

 all the notifications that are related to that post will be deleted。

And then we have basically implemented this entire file。Now what I've like to do。

 instead of putting this into this file， I will just actually cut it。And put it under my components。

 and instead of calling this as notification item， I'll just say notification。Dot T S X， let's say。

 just paste this in。And we need to get all the imports。

 So here's what I generally do instead of importing them one by one。

 I just go ahead import everything and then I press command shift P and and I say organize imports。

 So what that does it just gets rid of all the imports that we are not using。

 So there we go this is just a。Cool trick that you can keep in mind。 And let's just say， export。

 default this function。Alright， let's save， go back and try to import this。

 and I would like to call this as notification instead of notification item。Save this file。

 Go back and。Get this one。 Okay， now this file looks a lot more cleaner。 if you really want to。

 you can take this and put it into its own component and its own file。

 But I think this is like five lines of code。 I think that's completely fine。 And once again。

 I'll just say command shift P organize the imports。Here we go。

I don't know why we get an error for a split second。But seems like everything is working is expected。

Now at this point， if you really want to add the notification type you can pause the video and try to do it that would be a great challenge because we have done this multiple times and you can just test out your knowledge if you cannot do it feel free to ask it in the comments and we can answer that so I will delete this console log let's save it and just before we enter this section I would like to。

Fix something else。 and why are we getting this here it says require no module futures。Okay。

 so actually， this is existed， but。You may also want to run NPM install。

 so I'll just go ahead say MPM install once again。And run our application。And reload it with R。

We'll say this。 reload this once again。We should be good to go。 Okay。

 so I was going to say there is one more thing that I would like to fix。

 I think it is in the post comment， I mean， post component。Let's find it。posts at T x。

So at the very bottom， no， it's not here。 So there was a component that I would like to。Take。

 let me just see。 I think it is under the home page。 Okay， so instead of having this right here。

 I would like to take this and put it into its own component。I mean into its own file。

 so let's just say stories that Tsx。Grab this completely。Paste this in。

 and I'll just say export cost。 And maybe let's just do export default。Lets just be consistent。

 Let's get this scroll view， get these styles。 I think it is feed。

 Let's get the stories and the story component。Now we'll go ahead and try to import it。

Let's say you can do the same thing for this one， but I'll just leave it as it is。Okay。

 so with that that's going to bid for this section as well， let's clear the imports。

 let's say command shift P， organize imports and let's save it。

So I'll see you in the next section now it is time to build the profile screen which is going to look like this so we will have the user information at the top with the sets。

 then we will be able to edit our profile when we click to this button this model will show up and we should be able to save the changes we are going to display the posts and then when we click to a post it will open up in a model just like this so with everything that you have learned so far you can build all these functionalities by yourself just keep that in mind and now just for the sake of tutorial let me go ahead and show you every single step So first things first before we try to build the UI Once again we would like to add our functions so I will go under the posts and we would like to add a query。



![](img/3c902dbcec98786b9e863ce7af553dc4_254.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_255.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_256.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_257.png)

Let's shrink this mutation， and at this point， I will just go ahead， paste this in。

Let me just drink the left hand side so this is a query where we would like to get posts by a user and this user ID will be optional because if we are looking our own profile。

 we don't really need to pass a user ID right we would like to get our own posts so here we'll just say if user ID existed then go ahead find that profile but if it is not existed then this user will be the currently authenticated user and just add an if check in case user not found then we're going to go ahead get the posts for this current user and then we'll return the posts out of this query now if you are asking why is this optional。



![](img/3c902dbcec98786b9e863ce7af553dc4_259.png)

Once again， because in our profile。In our profile page we don't really need to add a user ID。

 but if we are looking to other user profiles such as this one。

 then we need to add a user ID so that we can get that profile， I hope that makes sense。



![](img/3c902dbcec98786b9e863ce7af553dc4_261.png)

Let's go back。 This is the function。 let's save the other function that we' would like to add will be related to users。

 so let's open this up and this will be a mutation。 Once again。

 I would like to copy and paste because at this point we know everything about convex the only thing we need to do is just。

Type this out pretty quickly。 So we are going to get two different arguments。

 I don't know why I tried to delete them， but here we go。

We are going to get the full name to be able to update it as well as the bio。

 then we'll have a handler function， which will get the current user and it we try to update these fields。

Okay， so that was the mutation that we would need。Now we can go into the app。

Tabs and find the profile page or the profile screen， I should say。 Now let's try to build it。



![](img/3c902dbcec98786b9e863ce7af553dc4_263.png)

So in this page we are going to have this icon or this touchable capacityacity to be able to log out So for that reason I will go ahead and get the use oath from Expo clerk and then we would like to have a state this is going to check if the edit model is visible or not by default this is going to be false and then we would like to get the current user。

By this query that we have created already and we have used this in the past So we'll just say this is the clerk ID and instead of doing it like this。

 I think we can just say if user ID existed， go ahead run this query， but else you can skip that。

Okay。So this is what we have for the current user and then for the edited profile info。

 so just think about it， when we click to this button。

 we are going to see the model and by the default like by default we would like to get the full name and the current bio and then we can either write something on top of it or we can just change it completely。



![](img/3c902dbcec98786b9e863ce7af553dc4_265.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_266.png)

So for this， we would like to have a state， let me grab this。I'll just paste it right here。

 which is the edited profile and set edit edited profile okay the full name and bio by default these are the fields that we have and then we are going to need one more state so when we click to this post this will be the selected post so that we can show it inside the model。



![](img/3c902dbcec98786b9e863ce7af553dc4_268.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_269.png)

Right so I will have my state， let's say con selected post and set selected post Now if you don't really add this type。

 this is completely fine， but we would like to let TypeSscript know that this will be type of post and this is how we can do it convex gives you this doc or document and you just say which type this is so you can either say it's going to be coming from user table but in our case this is going to be a post or by default itll be not so here we go it is not by default。

Then we would like to get the posts by user and since this is our own profile。

 we don't really need to add any arguments， so I just leave this as empty Then we would like to call our mutation as well。

 so let's go ahead and grab this Use mutation under the users we have this update profile mutation。

And then， we are going have last。Two functions that they cost， handle， edit profile。

This is going be anarrow function， let's say。Let's leave it as it is for now。

 and I will duplicate this and let's say handle。Let's just say， save。Profile。Hence。

 this will be an async function。Just like that and you know what my apologies we don't really need this function。

 the only function we need is this handle save profile and we are going to call this once we click to this button。



![](img/3c902dbcec98786b9e863ce7af553dc4_271.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_272.png)

Okay， so with this now I think we can build the UI So first I'll just say if we don't have the current user or if we are in the loading state。

 go ahead show a loader component， but else we can return our actual view。

 so this will be a really long return statement， but let's try to build it step by step。

We are going to say styles do container。 And I think these styles will be coming。

From a different file that we need to create， let's say profile that。Styles， but yes。Once again。

 I will grab this from Gitargripo， paste this in， this is one of the longest ones。

Let me show this entire file。Okay， so this is what we have。Marius scrolled really slowly。Okay。

 so that's what we have。 I'll just save。 you can grab this from the Gi repo and let's get the styles from the profile Sts file and let me see the entire view。

Inside this view we would like to have the header， which will have the username as well as the logo button。

 as you can tell， so here I would like to just grab this， it is around1 lines of code。

 let's get the touchable opacity。The ion icons， as well as the colors。

Let's save this is what we got our username as well as the blog button once we collected it。

 it just signs us out， right？Then after this， we would like to put a scroll view。

And then this is going to take the show vertical scroll indicator to be false。

 We don't really want to show this at all in our application。

 and then we would like to have one view that will be the container for profile info。

Let's close this off。 And inside， we would like to have avatar。And stats。

So select number of followers following， so on and so forth。

So here let me just save to get this formatting。And then paste this in， close this off。

We have avatar and stats class， and on top of it， we will have one more view。

That will have the image。This is coming from Expo image and we are going to put the current user image。

 so once I save this is the output that we got。So outside of this view we would like to put the stats container。

 so let me go ahead and grab this again it is around 10 lines of code。

 so we have two different texts， so let me just save and see the output， there we go。

 this is what we have just added。Then on top of this view， we would like to put the full name。

 as well as the user bio。 and we only want to show the bio if it is existed。 So we just have。

A conditional styling here。Okay， seems like we are missing something。 Maybe this should be。Oops。

 outside of here。Let's see。Okay， now this is actually working。

 so just double check that you are under three different views and then you add the text。Right here。

Okay， then we'll like to add the action buttons。So I will go ahead paste them here。On press。

 let's just delete that， save。So this is what we have， this doesn't do anything。

 this is just for decoration， you can add the actual functionality。

 but I'll just skip that and let's say when we click to this when we click to this edit profile。

Button。We would like to just change our state。 So you say on press。Make this state to be true。

 and depending on this state， we would like to show our model。So for now。

 let's save and let me show you the entire thing like this。And then after this touchable opacity。

 after these two views， I will say if the number of posts is equal to0。

 I would like to show this component， which is around 10 lines of code once again。

Let's just say function， no posts found， this is the content we just say no posts yet。Okay。

 then after this like below to it， we would like to show the actual posts and for this we are going to be using flatlist and let me turn this off。

 the data that we' would like to map through will be posts let's say number of columns This is something that we have used for the first time in flatlist。

 but here we go then let's say scroll enabled。Let's say this will be false。

 they shouldn't be able to scroll and for the render item， we can show a post component。

 but in this case I'll just put it in line and I'll just show the image itself Okay。

 just a simple image and when we click it， this will set the selected post so that we can let me show this。



![](img/3c902dbcec98786b9e863ce7af553dc4_274.png)

Oops。😔，So that when we click to a post， we should be able to show a model。



![](img/3c902dbcec98786b9e863ce7af553dc4_276.png)

Okay。So this is what we have the flat list we're going to save and go back here。

 by the way we got the Ui， we can collect it， nothing happens， we can collect it as， nothing happens。

 but let's make it work below to this scroll view we're going to have two different models。

 so one for the edit profile model and then the other one let's say。Selected image model。

 Let's start with the simplest one， which is this model。 I would like to give you the code。

 It's around 2 lines of code。Here let me walk you through it so we're going to get the model from react native we will say animation type will be fade。

 transparent of true and when we close it it should set the selected post to beal and here it will be visible depending on the state now since this is an object we would like to convert this into a Boolean so we just put double bank operators once again super simple JavaScript trick that you should know。

Then we have a view with some styling if there is a selected post， we are going to see this part。

 so I think we don't really need to add this check。

 but if we don't edit this is not really happy with us， so that's why we have that。

Let's save and test this out。 Here we go。 if I click this， this one is selected if we click to this。

Okay， you get the point， it works and when you click to the close button。

It says the states to be not。

![](img/3c902dbcec98786b9e863ce7af553dc4_278.png)

So with this now we can add the actual model， the one and only edit profile model。

 which will slide down from the bottom of the screen， right it'll be animated。



![](img/3c902dbcec98786b9e863ce7af553dc4_280.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_281.png)

So I think this will be around 50 lines of code， I can copy it and paste it。

 then walk you through it slowly。So I am just trying to do everything to not type this out I hope nobody gets annoyed by this because like I am more on the explaining part of the tutorials rather than typing everything out I think it just doesn't make sense at this point we are I think4 to5 hours in and you should be able to understand everything that we just copy and paste so let me import everything and we will take a look at the code。

Okay， so we have just imported from。Like this entire model once again we have our animation type。

 divisiblepoion， transparent and close function， then we have Toable without feedback。

 we don't really want to get any feedback so this is one of those components that you can use and then on press will just say dismiss the keyboard。

So let's save， see the output， and then I'll explain the rest。So if we collect to this。

 our state becomes a true and you are able to see the model， which is this view。

 then here we say once again。Like use the keyboard avoiding view。

 make sure that behavior is working correctly depending on the platform。

 and then we have this edit profile header， which is this part， then we have the name。

 we have a text input。And once you type something in， it will update the state。

Here we go and it will only update the full name， then we have the exact same thing for the biography right and at the moment we don't have any value。

 so it is an all。We are going to fix it or we are going to add something I was going to say。

 and then once we click to the saveve changes button， we are calling this function。

 so let's go ahead and create that then we will try to actually update our profile。

So here I'll just scroll to the very top。And here basically we would like to call our mutation。

 so I'll just say update profile and we are going to add the edited profile state。

 which has the full name as well as the bio then once we edit like once we save this update the profile we would like to make this state to be false so that this model would close。

Okay， that was a lot of different things。 Now let's actually test this out。

 I'll click here and I'll just add one，2，3 at the end of my name and then I'll just say hey everyone。



![](img/3c902dbcec98786b9e863ce7af553dc4_283.png)

Let's save the changes。 Here we go。 lookss like it has been updated。

 We can just double check by taking a look to our database。 This is the W and。



![](img/3c902dbcec98786b9e863ce7af553dc4_285.png)

This is the new full name。Here we can see。And let's try to build it with the like let's try to test this with the actual keyboard。

So I'll go ahead， press command shift K。As we can tell， the。Vi is。Lake。

Keyword keyboard is in the view， All right。And there isn't really any issues on this side as well。

Okay， I'll just say。Maybe I can just disable the keyboard Its kind of annoying because while it is open。

 you cannot really type type out with your actual keyboard。

 So what you say S weE and we can delete this one to3 and there is like correction if we can see。

 I believe we can turn this off as well。I don't really remember the exact prop， but。

If you go into this text input for the bio。Let's say completion。 Do we have anything like that。Like。

 autocompte。And let's see what this does， specific how to completes hence for the system。

So I think it should be auto to complete and we can just say this will be off。 I this the case， Okay。

 we have of like a bunch of different things that I don't even know that was existed。But yet。

 basically， this is how we can explore different things。

 So let's just say it will be S weE just like that。 save and here we go。

Now that our profile page also works， the only thing that we left is the user profile。

 So when we click to other user profiles， we are going to see this page。



![](img/3c902dbcec98786b9e863ce7af553dc4_287.png)

As you can tell， we will be able to follow them and unfollow them。

 so this is what we're going to build next。So in this page we are going to need a couple of different functions and specifically we are going to need two different queries and one mutation and let's see what they are。

 so let's start with the queries the very first query that were going to need is to fetch the user profile and then the other one is to check if we are following this user or not depending on that we will either show this follow button or unfollow button and then the mutation。

You will be， as you can tell， like follow or unfollow functionality。Okay。

 so we're going to just toggle the follow state， so before we start building the UI。

 let's go ahead and create our convex functions， then we'll just jump into the UI。



![](img/3c902dbcec98786b9e863ce7af553dc4_289.png)

Okay， so I'll go under the posts。

![](img/3c902dbcec98786b9e863ce7af553dc4_291.png)

And I don't know if you have realized， so maybe you had a question， you said。

 why don't we have a query to fetchD postss， but we don't really need to build it because we have already done that right。

 get posts by user and we're going pass the user ID and we'll just collect every single post that this user has。

Okay， so let me just make this entire screen so that we can see it clearly and I'll just get my very first query。

 which is to get user profile。What's a query。At this point you should be able to do this in seconds。

 but I'll just type this out， let's say we're going to pass an ID which will be the user ready and then we' would like to go ahead and get the user。

Let's just add an if check where we say if there is not user， throw an error。

 but else go ahead and return that。Okay so that was the very first query。

 the other one is to check if we are following this user or not。

 so I'll just paste this and then we'll go through it， it's around 10 lines of code。Okay。

 so it this called is following and we're going to pass the idea of the user so that we know if we are following this user or not。

 we'll get the authenticated user and then we'll just check for a document under the follow table and we'll say hey。

 if we are the follower and if this is the following。

That means we are already following this account， right。

 because we are the follower of that user then。Like we'll get the first result。

 this will be an object or an null， and if you want to convert this into a boion。

 we would use our JavaScript trick so we're going to put double bang operator So if you follow。

 I mean if you hover over this。You can see we are returning a booleion。Okay。

 so that was the very last query， but we we need one more mutation Okay so let's just try to type this out。

 this will be a bit longer， but I think it is nothing complicated so let's say export cant toggle follow just like this this is going be a mutation and once again we' will get an argument so that we know which user that we are trying to follow or unfollow。

Then let's get the handler function。Just like this。

 we are going to get the currently authenticated user and then just like what we have done above。

 I'll just copy this。If you really want to， you can make this a reusable function， but I'll just say。

 you know copy and paste and I will call this as existing。 So if this is already existed。

 that means you are following this user and you would like to unfollow it so we'll say if existing do it is else do this here we would like to unfollow。

Right， and then here we would like to follow。Okay you。

Now if we want to unfollow that means we would like to delete a document。

And specifically we would like to delete the follow document and then we would like to decrement the number of following let me showho this we are going to decrement the number of following of this user or I should say okay let me just tell you from scratch if we want to unfollow this user we would like to decrement the number of followers of this user and we would like to decrement the following count of our own account right so I hope that makes sense let's go ahead and try to do it。



![](img/3c902dbcec98786b9e863ce7af553dc4_293.png)

Since this will be reusable， I'll just create a function called updatedate。Follow counts。

And we are going to pass the context。Current user。Id and following ID。

 which is coming from arguments。And then well just say true or false so in this case this will be false here itll be true I know this doesn't make any sense。

 but we will create it any second and it should be clear and then if we are following that means we would like to create a document so let's say context Db insert into the following table and this is the document that we' like to insert so we're going to put the follow ID and then the following ID。

Okay， once we have done this， we would like to do the same thing。

Because we would like to increment the number of these values and the you know。

 the same arguments will be added， but this will be true。

 which means like if we are following or on following， okay。

So hopefully here we should be good to go and you know， we are missing something else。

 which is to create a notification， right？And here I'll go ahead， copy and paste。

This is something that we have done multiple times at this point。

 we'll just insert under the notifications， a type of follow document， a follow notification right。

 and here is the receiver and sender is the current user。Now let's build this function。

So I think I can provide this to you， once again it's around 10 lines of code。Okay。

 so first we get the mutation context。 So since this is coming from a mutation， right？

This is the context that we are passing， let's say type of this is mutation context。

 and then we got the follower ID and following ID， which are the type of Use ID。

 and then is follow bullolean。So this code is pretty easy to understand。

 we get both of these documents， then like if you don't add this part， TpeScrri will be al mad。

 that's why we are adding it。And then we just say， go ahead and update these values。

Following the number of following either will be incremented or decremented and same for the followers。

And how can we check for the increment or decrement， itll be depending on this boolean。

Which we have here， So either false or true。So all in all， this function。

Allows you to follow or unfollow， right， as the name suggests。

 So I think you can pause the video if you didn't really understand it。

Even though there isn't anything complex， but I can feel this might look a little bit weird if you are kind of like a beginner。

So once you have once you are done with it， we can go ahead and try to build our UI for the user page and just before we built the UI。

 I'd like to show you this image。So I don't know if you have realized it。

 but this is not part of the navigation， right？And let's take a look at it。 Okay， all these pages。

 all these screens are part of the navigation， but here this is not the case。

 so we would like to go ahead and put it。Outside of the tabs folder， because anything。

 anything that you put here。Under this folder will be a tab， right， if I can correctly。

 Then let's go ahead， create this。Screen I will call this as user and this could be dynamic right you could have millions of different users so that means there could be millions of different screens Since this will be a dynamic screen we're going to put these square brackets。

 This is how we will make it work。 We'll just say ID dot TsX you can call this anything like username but we'll be fetching the user profiles depending on their IDs That's why I'll just call it as ID。

Then we would like to have a layout file。I'll say layout that TsX， this will be a really simple file。

Let me just take this out， let's say R and F。So we can just call this as user layout。

And instead of view and text， we would like to basically return the stack。

Let's get it from the export router and then I'll just say screen options。

 we don't really want to show the headers。Okay。Now， let's save。And we'll like to build this page now。

 I'll just say R N F， let's say， user profile。Page， or I think we should call it as screen。

Give all its space and safe Now we' would like to build the actual content。

Let's just make them to look correctly。Okay。So here I'll just go inside and we would like to call some queries。

 So first， let's try to get the profile of the user。

Now this is not the page that we are trying to build。 This is our own profile。

 the page that we are trying to build。Will be the profile of others right， So when we collected this。

 we should be taken into this page。So let's say profile， and I'll just shrink the left hand side。

 give all the space， let's say use query。Get it from the convex and I'll just say。

Get the API that users， and get user。Profile， I was going to say。

 but why don't we have this function。Cant user。Profile。So I don't know why。

 but I have just put this into the posts。I think this doesn't really make any sense。

 This is not related to posts。 So I'll go ahead， cut it from here and actually' I'll cut all of these。

 right， They all are related to。Users， so I'll just cut everything， save this file。

 go into the convex folder。And under the users file。 So Ill just paste this in。Let's get the I。Okay的。

Now everything should be happy with us。😔，We just have all these queries and mutations and one helper function。

Okay now let's say sharing the left inside， this should be happy with us now。

 let's say get user profile。 Now this wants you to put an argument right。

 which is the ID and how do we get this ID。From the file name。

 So this will be coming from a hook that's say con。Use local search prints。

And we can destructure thevalue， which is going to be ID。 So if you call this file as hello。

 you would say grab me that right， but in our case it is called as ID， so this is how we get that。

And here this says， like let's just added I as I。 but now this says this is type of string or an array of strings。

 but we are expecting a type of user id right， So let's make the typescript happy and you say this will be。

Id of users just like that。 Now， this is happy with us。 Now， the other query that you'd like to do。

 let's just duplicate that。 It will be posts。Well say API get user profile。In the same way。

 this wants us to put an ID， so here we go。And finally， well like to get our mutation。

 So let's say con is following。I think this is also the query， not mutation。 Let's say is following。

 I'll just how to accept this。 Here we go。 This is。Working correctly。 Then we can get our mutation。

 which is called as toggle follow。What they use mutation。Okay。This is the mutation that we have。

We are going to have a function called handle back for now let's just leave it as an empty arrow function we will implement this later in the video。

And let's handle the loader case。 I'll just say， let me grab the entire thing。

 Its just a simple if check。 So if profile is undefined and if you remember in conveys。

 if something is equal to undefined， that means you are in the alling state。

 So basically we check any of these are。In the alerting state。

 we're going to show a loader component。Which is something that we have created already。

 Then we can go and jump into the return statement。Let's delete this part completely and。

Here is going be our container。 Now， this is related to user profile。

 and I believe the styles will be coming from the profile styles。

 Then we would like to add the header。Section， which is going to be this part。

 So we have an icon and then the user。Like username， right？I would like to grab this， put it。

 which is around five lines of code， I'll save to get the formatting。Let's get this component icons。

 and then the colors。All we do is to。Just show the user profile name， right， I mean， user name。

 So let's go ahead and try to see this page。 How can we make this work。

Let's go under the notifications page。Under the tabs。 So when we click to a link。So。

Under the notification。So we were just taking this user to de notification page， but we have a to do。

 now let's just fix it now。When we collect it， we'll just say take them to the user page and here is the entire。

Entire URL， So let's save， I'll just click to this。It says this page does not fund。

 but this is not correct， let's go ahead press or when you add a new page I think you should reload your application。

Let's test this once again， I'll click to this。Okay。

 so here it says the value does not match validator。Let's take a look at it。So we got the ID。

 I'd like to just console log it。What do we get， But the idea is here。

So I just found a solution it was a silly mistake by AI in Convex we don't really have ID。

 but instead we have underscore ID right， so ID just returns undefined。

 we should fix it now let's save and test this out if you click to this profile it should take us to there and here is what we can see。

Okay， now I hope that makes sense。Let's go ahead sharing this left hand， delete that。

And build the rest of the UI。Now， what are we going to have is this remaining part。

 and I will just put them under a scroll view。

![](img/3c902dbcec98786b9e863ce7af553dc4_295.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_296.png)

So let's go back。Put them side by side and import a scroll view。They close this off。

And we don't really want to show this scroll indicator。 Then I'll have a view at the very top。

 let's save to get this formatting。 Then this view will have a style。

 let's say styles that I think it should be profile info。

 Then inside we're going have one more view with the style to be。Styles， dot avatar。And stats。

 Then I'll just grab you the content。So this is the avatar， let's get the image from Expo image。

 save there we go， next to it， we would like to put the stats。

 so just below the image still inside this view。I'll just say， it stats。

And then I'll provide you the code。W is around once again， 1 lines of code。Okay， so here we go。

 number of posts， followers and following。Then after this view， I mean after this view。

 and then after this one， we would like to go ahead build this full name text。This is what we got。

 and if user has a bio， you would like to put that。And looks like this user doesn't have it。

 so it is not updating the UI， then we would like to have this button and for this I'll be using pressible just to have at least one of them in our code base。

 you can still use pledgeable aacity， but this is what I'll be going with。



![](img/3c902dbcec98786b9e863ce7af553dc4_298.png)

![](img/3c902dbcec98786b9e863ce7af553dc4_299.png)

So pressible as import that。 And depending on the following state。

 we are going to show a different style and on press， we're going to call the。

Call the mutation and past the following ID if you don't add this part。

 Typecr will be unhappy with you， so this is what we added。Depending on the state。

 the button text will change。And let's save and test this out。Here we go。

 I can follow that in real time this has been updated and I can unfollow that user。

After the pressible and after this view， but still inside the scroll view。

 we would like to create the post grid， so here I'll just have a view with the styling。

To be the cells that post the grid。And inside， I， like， I just need to check the number of posts。

 I'll say posts dot length。Wait， why don't we get this。Posts。Okay， so for some reason， posts is。

Not an array。 Why is this the case。Okay， this should be get user posts。But we don't really have it。

 Maybe it should be under the posts。Get。Posts by user。And this wants you to add。A use ready。

So if you have realized these mistakes a couple of minutes ago， you might be mad at me。

 but I have just realized。Okay， now we can just say posts and we can get the length。

 Now it's an array。 and if it is equal to0， we would like to do something。Like this。

 And in the else case， well like to show something else。

 and here I'll just put a placeholder that says no posts yet。

And then here we'll like to just show a plotlist。Let me grab this。

So this is what we have done multiple times。Where we'd like to map through the posts number of columns scroll is not enabled。

 and for each item we'd like to render a touchable capacityac let's save。Okay。

 currently this user doesn't really have any posts， that's why this is what we see。

Now I don't really know why this has not been centered， let's go ahead and fix it。

Let's maybe say flexs will be1。Okay。So probably you already have it in the source code。

 but I have just added that。Now it's being centered。Okay， so everything is working at the moment。

 we can follow this user， we can unfollow them。It just works without any issues and just one thing that we are missing is this function like called handle back。

 When we collected this， nothing happens and we have attached it to this icon。

 So let's go ahead and build this function。 So basically we'll be using the router。

I would like to import it let say use router coming from here and what you say con router。Okay。

So inside， I'll just say if。Like let's say if Ro can go back， yep。

 this is something that is available。 if this is the case， we should be able to go back。

And in the else case， you could just say rot the replace。Slash tabs。

 So we're just going go into the home page。 I'll just click to this。 Here we go。

 We can go back to the notifications page。Then I think there is one more thing that we are missing is that when we click to here。

 nothing happens， so let's go ahead and fix that。I will go into the post component。

This is where that is。And here， here we go。Like if you remember back in the video I just said we're gonna to fix this part and let's fix it now this is going to be dynamic value so if post is mine that means the author is me when I click to this it should take me to my own profile tab but if post is posted by someone else it should take us to the user page that we have just created right so here is how we can do it I'll basically paste this in we're going to get the current user。

Let's just put a question mark。So we'll say if the post author is me。

 then take me to the profile tab， but else take me to that user page。Let's save， I'll click to this。

Nothing happens， I think we should say as child right。

 because there is a touchable opacity and we would like to take the link inside of it So this is how we can do it。

 let's save and I'll click to this it should take me to my own profile。

Okay this is how that work if that was a different profile。

 trust me it would take us to that user screen that we have just built so with that that's going to bid for the user page。

 there isn't really anything complex that we have implemented it was a pretty basic QI where we just handle a mutation and we have added a couple of different queries。

Okay so in the next section we're going do some fixes and optimizations Now let's do some optimizations the very first one is related to Android devices so this is an Android device that I actually test it out and I've just realized when you take a look at the navigation bar it is in the white theme so it should be dark I think this doesn't really look nice it would be better if the background is dark and these things are white red these buttons so how can we make this work well thankfully there is something called Expo navigation bar and willll go under the layout。

Try to get that package， so I'll just kill my application。Clear this up。

 And I'll just say NPx Expo install。What's say exporto dash navigation。Dashbar。

So this will go ahead and install it。While it installs。And here we go， we got that。

 So let's start our application， freeload it。Okay， it says no apps connected， I'll just press I。

And thenreloadge， okay。Let's kill the terminal。We're going to go ahead and use it so what I'd like to do use a use effect and just try to change the background color as soon as our application starts so first I will get my import。

Just like this， I'll say import everything as navigation bar from this package then。Below to this。

 I'll just say use effect。And let initialize it。Okay， so when our application starts。

 we would like to check if platform that operating system is equal to Android。 if this is the case。

 we' would like to go ahead run this block。And I would like to just basically copy and paste。

 so navigation bar set background color with this black color and then the style will be a light so that these buttons are light。

And the background will be black。Okay， so once you have done this。

 we can basically save and I'll just add a comment。

Just so that you can have it in the source code Now one Android devices。

 this problem should be fixed and I have tested out。

 it is actually working Now it is in the dark background color。

So that was the very first thing that I wanted to mention the other one is let me take a look at my notes okay so we would like to make the number of flags to work in real time so what do I mean by this now what do I mean by this what does that mean to make this work in real time so let me pretty quickly open up my camera and just show you in real time。

I'll go ahead and try to scan this Q code， let's open up the terminal。Just like that。Okay。

So let's wait a second， this should open up the actual application。

 and I'll just log in with my account。Alright， so I am just logged in。 Here we go。Dude。

 I just got an even email notification， but here we go。

 this is the exact same post that you can see on the screen， right， this is what I have。

 this is what we got here。So I will go ahead and unlike this post currently it is liked。

Here you can see and if I unlike that， this screen should get updated immediately but notice how I will unlike it。

 it doesn't get updated here right， and actually we can make this work in real time because we are using Ks so let's go ahead and try to fix the code and then we'll just test it out once again。

Alright， so I will kill this field。 We're going to go under the post component。Oops。

 let's shoot their left hand。So we have this state called likes count。

 but we don't really need to keep it in a state， we'll just use it as post likes。

 so I'll just delete this state and here we have an error instead of likes count we'll just sayPo dot likes。

Okay， and then we have one more error， let's go here under the handle like we don't really need this function because convex will fix it immediately。

Now in the same way， I will go ahead and fix the commentss count because at the moment if I try to add a comment from my phone。

 this will not update it for this user right if we delete this part。And make the comments to be。

Post that comments， that。Okay， I think that should be it post dot comments because it's already number and we can save。

Here we should be able to get rid of this and go into the Commons model。Plete this type。Ptus probe。

And delete this call。So what we have just done is to get rid of that state so that we don't really。

So we don't really need them right， we'll just make it work in real time。 Okay。

 so I'll just open up the terminal and as well as my camera just to show you this。

So what these price are that will reload the application。Okay， just take a look at the screen。

 we have zero likes， and here it also has zero likes， I'll just go ahead like it。

And here you can see in real time on the screen for this account。

 it is updated and if I like it here on my phone， it should be two likes。Okay。

 I don't know if you can see it， but now it is two legss here as well， I will unlike that。Okay。

 I can not click it。Okay， now it is just one like， let's go ahead and add a comment。So I' to say。

 hey， but first， let's see there is only one comment。Hey there。😔，And post it。Okay。

 it just works in real time。 So I just really wanted to show you the entire process and。Okay。

 so that was just one optimization that I wanted to add。

 I think it is better to see the numbers increment in real time。Okay。

 so that's going to bid for this optimization， I think there is one more thing now this one that I'll show you is not like an optimization。

 but it is something that I genuinely want to talk about。So I will go under the home page。 Okay。

 so app tap feed。Here what do we want to do。 So when we just try to refresh this right in Instagram。

 this is how that work， but here nothing happens。 but thankfully there is a component for this where we can just make it work right So here first things first。

 I'll just get a state to check the refreshing。State， so just say by default。

 this is going to be false and let's import the U state， and then on refresh。

 we'll do something let's say con on refresh。For now， let's have an empty function。Just like that。

 And then we can add it into the flat list。 I'll just say。Was it on refresh。

So here we would like to actually render a component。

And I think it is not on refresh my bad it should be a refresh control The component that we'll like to show will be refresh control coming from React native then we can add couple of different props so here I'll just say refreshing well depending on this state and on refresh what are we going to be doing is to call our function and then the tinth color if we really wanted to we can customize it and there are a bunch of different things that you can take a look after completing this tutorial。

So let's save and we can try to refresh this， here we can see we can actually get that。Viu。

But nothing happens at the moment。What we can do on the on refresh method。

 we can actually try to run this query once again， right so that we would get the latest posts。

So here I'll go ahead for now， I'll say set refreshing will be equal to true when we run this function。

 and then I'll just say after two seconds。You would like to just say set refreshing to be false。

 So currently this does nothing， right， The only thing we just update the state is if something is happening behind the scenes。

 So after two seconds。Basically nothing happens， so if you really want to。

 you can call this query once again and since we are using convex。

 if you really want to refch a query， you can use this package called10 stack query。But in our case。

 I just wanted to mention this and I will not be implementing that if you really want to。

 you can have this as a really great to do。Okay， so this is how we can implement on refresh functionalities。

 Let's take a look at our code base if we have any twos left。Basically， we fixed it。

We can delete that。And then the other one， I think it's in the same page。Okay， we forgot to fix it。

 so let's go ahead and do that。This is。When we click to the username。

This should take us to the user profile。 So just like what we had above。

I will copy this entire thing。And then， paste it。Okay， so now if you click the username。

 it should take you to that profile。Just like here。Okay。

 so with that that's going to bid for the section as well， so I have just said by。

 but there is one more thing that I would like to mention。

 which is that let me open up the camera first。So here I just got an Android device and this was the previous device now this is working completely fine。

 this is also working completely fine， but there is just one thing that I'd like to mention。

 which is this status bar， so let's go ahead and try to make this work with a dark background。So。

 here。Even if there wasn't a problem on this Android device。

 this is the component that I'd like to mention， so I just forgot that until now we didn't really need it。

 but here we go we'll just be using it so we're going get this status bar import from expo status bar and I'll just put it right below to the Sa area provider okay so we' just say status bar we can give it a style like light dark and there is also invert。

I believe yep， we have even auto here let's go with the light， since our background is always black。

 this should be a light so that text is white。But if you go with dark。

 notice how this will be invisible right， and this doesn't really make sense。

 we'll go with the light option and let me open up the camera to show you this。

So here we can see now it is black， it is looking a bit better if we go with dark。Oops， let mees。

Like delete this and just say dark。It's like that。😔，Like the text completely disappears。

 but in our case， we would like to have this as light。Okay so now that this is working。

 I think we can move on with the next section so now that we have an entire application built。

 this is completely ready to be deployed but how do we deploy this so unfortunately it is not as easy as deploying a web project so we can really go into Veral or render do co and just drag and drop it This is not how that works there are some good news and bad news the good news are that you can deploy it right you can publish it to Google Playstore or app store the bad news are it just a little bit more involved right so you would need to have a developer account to put your you know application information and then from there you would publish it and I don't know like how long it'll take but I think it is a couple of days or maybe weeks I don't really know I have never deploy any application to app stores。

But I'll just provide you some notes that you can keep in mind so that you just really know the steps Okay so I'll just go ahead and paste this in and let me walk you through it So building and publishing your application you can build your app for production with Expo application services and I have some links that I'll just provide in a second and if you want to submit it to Google Playstore or app store you will need a developer account and then it would take a couple of days or weeks as I have just mentioned and then if it is accepted I think it'll just go live immediately and I guess like I believe there is also be version。

And then the actual version。 So if it is not accepted completely， the be version will be live。

 I might be wrong。 just let me know this is something that I have seen。

 haven't really experienced it fully。But it's really nice to know these right then here are two different links that you can take a look from the expo documentation。



![](img/3c902dbcec98786b9e863ce7af553dc4_301.png)

You can build your project for app stores and you can submit it to app stores right。

 and there is even a video explanation， so there is really no excuses to not deploy it。

If you really want to， you can like you should definitely take a look at these documentations and just make that work。



![](img/3c902dbcec98786b9e863ce7af553dc4_303.png)

And then。What the hell must it does。Then like there are a couple of different steps that I take note。

 and I'd like to walk you。 So first things first， you need to visit Expo。 and sign up。

 So I have just said you can use the EAs to build your applications。 and since this is。



![](img/3c902dbcec98786b9e863ce7af553dc4_305.png)

Since this is the service of Expo， you should visit their website and sign up。Which is free。

 I believe， let's take a look at the pricing。Here we go they have a free plan and 30 mobile application builds per month。

That's pretty cool， right？And then like there is even submit to App Store。Open。



![](img/3c902dbcec98786b9e863ce7af553dc4_307.png)

Okay so you just went ahead and signed up， then here is what you would do in your terminal。

 install the EAS CI globally， then you would log in with this command so these are everything that you would do in your terminal right。

 so you would run this one first， then this one and then you would say EAS in it and this will ask you to create a project and you can just say yes。

Okay， let me just fix that then if you want to build it for Android。

 you should say EAS build platform Android， and this will give you an APK file。

 which is the file format that is used by Android operating system to install and distribute。

Applications right in the same way you would do it for iOS and then it would give you IPA file。

 so this is for iOS and this is for Android。And then you would take those files and submit it to Playstore or App Store。

So once again， there is no excuses to not do these if you really want to。

 and then your actual challenge is to publish this application and if it went live successfully you could let us know and you know I can just do a shout out then we can give you some stars and that would be a really cool project for your resume。

So with that， if you were able to follow along up until now。

 I don't have anything to say other than congratulations， it is 3 a。

m in the morning and I am going to bed straight。

![](img/3c902dbcec98786b9e863ce7af553dc4_309.png)