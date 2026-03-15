# 【全集 春季版】伊利诺伊大学 计算机编程：从Bash到Rust 中英字幕 p09 Lecture 9 - API 调用、请求、JSON -BV188rDBFEUY_p9-

Good evening， everyone。 Welcome back to C S 1，96。 So I'm gonna quickly go over our objectives before I start。

 So today we're going go over APIs。 That's the main focus of today。 So what are APIs。

 Why do we use APIs， How do we use APIs。 And then to fully understand APIs。

 we're also gonna talk about H request。 And Json and touch on X M L。

 And these are a bunch of acronyms that make no sense right now， Don't worry about it。

 We're gonna cover everything today。😊，So what are APIs。

 So API stands for applicationp programming interface。

And I'm gonna to use this example from this video。 You can watch this later。 It explains it very。

 very well。 And I thought its a great example。 So imagine you're at a restaurant less C， S 1，96。😊。

So you are over here。 You have a menu full of requests， Those your food orders。

And in the kitchen is what's gonna handle your request and you get food out of it。

Things pretty obvious。 But there is something missing here Theres a key vital component missing from sending your order to the kitchen and getting what you want。

And that's the waiter。So like in any other restaurant， you're going to look through the menu。

 find what you want， make that request to the waiter。The waiter will take your request。

 Pass it off to the kitchen。 The kitchen will do whatever they need to do， make your food。

Get the food back to the waiter。And get that back to you。 And yeah， we're happy。 We got our meal。

 Everything went smooth， and was pretty easy to do。😊，Similarly， when we have a system like this。

 So you over there， the client and there's a server。 And like this。

 although it looks like they're very close by， the distance between the client and the server doesn't matter because we use APIs。

 so。Our server could be on the other side of the country， could be on the other side of the world。

 It doesn't matter because the use of APIs reduces the complexity and makes sure that regardless of where we are。

 we can make this work every single time。So let's go back to our example。 So we have a request here。

 That's the green ball。 We send our request to the server。 The server processes our request。

 gets us the response that we want， the data that we want， anything that we need from the server。

 and we'll pass that back to the client。 And now we have our response。But again。

 how did this response get moved around， Who's handling it， You know。

 how are we getting exactly what we need， It's pretty difficult to handle。

 extendend millions of bits over and get that back。

 But the waiter here is our API using the application programming interface。

 we can reduce the complexity of having to send data over and we can outsource a lot of our work because the API makes this so easy。

So let's give a real world example of this。 Like， where have you seen APIs in your day to day。

So everyone waved Sammy， Sammy。嗯。So we have Uber is a really great example。

 So this is a screenshot directly from my Uber app。 So I scped it off。

 I don't you guys know my address， but notice the bottom right corner。😊，It says Google there。

 So last I checked， which was a couple hours ago， Google does not own Uber yet。Actually， Albet。

 Google's parent company owns 5。8% of Uber。 So the more you know， But no， Uber does not own Google。

 There's no affiliation there。 But what Google is using is it's using Google Maps API。

And you're probably wondering， why would Uber， a company that is worth over a billion dollars。

 need to use code from somewhere else。 Well， here's why。

Google has arguably the best map software in the world。You get。

 there's around 32 satellites around the world， which Google pays for。 or sorry， like rents out。

 I guess not sure have satellite to work。 But 32 satellites that Google pays to give you updated information and give you live data。

 You can get directions。 Uber driver uses the directions using the shortest route using map and traffic data with constantly updated maps。

 And secondly， it's very easy to use。 once you have the API。

 There's no need to update the maps or to handle any of the complexity of running GPS software。

So even a huge company like Uber will outsource their work to APIs。But why do we want to use APIs。

 Why do we care， We're learning to program。 We don't need outsource this。 Well。

 it's because of one very important fact。 And that is。Good programmers are lazy。

 And what I mean by that is that you're not gonna sit there and just copy code of Github for every assignment you have to do。

 Defly don't do that。 What I mean is that good programmers are efficient。

 You're not gonna waste time writing the same code over and over again。

 You're not gonna manually input data by yourself。 You're going handle that using a script， etca。

 etc cetera。Here's la comic。 That was pretty funny。Anyway。

 being a bad programmer might not stop throwbo apocalypse。

 but it will save you a lot of time and make you more efficient overall。

And I'm not the only person who thinks that。Larry Wall。

 the author of the Prol programming languagegu， says the most of you are familiar with the three virtues of a programmer。

The with the virtual programmer， there are three， of course， laziness， impatience and hubris。

And again， these sound like bad things， but all of these three virtues are will make you more efficient and more likely to get your outcome faster。

So let's look at the advantages of using API。 So firstly， automation。

 APIs last automate task out having to do the automation ourselves。

 It's very nice be to outsource work When code for that already exists。

 There's no need for us to reinvent the wheel over and over again。😊，Secondly， efficiency。

 API allows developers to access powerful tools and create new features and publish them very。

 very quickly。 So normally， if you want to add a search bar or something。

 C a search engine on its own is very difficult to ask Google and then have implement that empty your app is also very difficult。

 So by doing using APIs， we can be more efficient with our time。😊，Finally， adaptability。

 API sent companies and developers a lot of time and money。

 because changes published and made very quickly。 So take， for instance。

 a client suddenly wants to add a new feature and they say it has to be done two days。

 If you have to write something from scratch and implement it and test it。

 itll take a very long time。 So it's nice knowing that you call an API。

 you have working code It's a black box that gives you exactly what you need and you don't have to test and waste more time。

😊，And again， it comes back to this idea that good programmers are lazy。 We're not。

 There's no point trying to reinvent the wheel every time we want to do something。嗯。

I slide this moving。Okay。Again， don't，'t need to reinvent the wheel。

 Youd have to use APIs to make your life a easier。 And also for your projects。

 This is the key thing I wanted to hammer on。 You guys are totally welcome to use APIs for your projects because a lot of the things that you might need are too complex to make in the semester or already exist is' need to waste your time writing it again。

😊，So a quick break from API to talk about HM L requests， so。Firstly， what is H TDP。

 The H T H TDP stands for Hypertext Trans protocol。

 And this is a protocol that's designed for communication between clients and servers。

So let's look at what HB request looks like。 So you don't need to understand a bulk of this。

 I just wanted to give you guys a picture of what it looks like。 So at the top。

 you have the request line。 And that's specifically what you're doing。

 You notice we have a keyword there， get。Fed by the URL U and then the HP version。Underneath that。

 we have the request headers。 There is information about the request。 General self。

 We can ignore that completely for our purposes。 Then there's a blank line which separates the header and body。

 And then we have the request message body。So this is what you， the client。

 are sending out to the server。And then you'll get back at H TP response message。

 So this is what it looks like again。 Again， a lot of this， you don't need to remember。

 But at the top we have the status line， response headers。Very important thing that we do want。

 though， is the response message body， because that contains the data of the information that we're trying to get back。

So let's talk about four main H H GP methods。 So there's more than this。

 But these are the four that I want to talk about just because they're。Easy to explain。

 and gives you a good introduction to them。So。Firstly， we have。The get method。

 So you use get to request data from a specified source。 So that's the main thing all does。

 Get gets you what you want。 Pret self explanatory。 The query is in the URL of the get request。

 So youll do get URL， and then some kind of query string。

And so an example that I'm probably gonna to use later today is the Google custom search API。

 So what， the way this works is that you'll use get past the URL and then the parameters and then the parameters。

 you'll have things like identify， how to identify yourself， the search query， etctera， etc cetera。😊。

So get a request should never be used when dealing with sensitive information。

 And a reason for this is because。This data can be cached in your browser history and in the Web server logs。

 So if it can be cache， it means it's just stored later so anybody can come back and try to use malicious code to take it out of your server or your browser。

 sorry。And get requests are only used to request data。 You cannot modify data using the get request。

That makes sense。 Any questions so far about anything。O。

And now we're going to talk about the post method。 So use post to send data to server to create or update records。

So again， get to get stuff post to update things on the server side。

So data sent to survey a post is stored in the body of the H T TP request。

 So that's different to the Ga request， which in the URL。 This is in the in the body。

 which is just underneath the header。And post is a little safer than get because you can't cache a post request。

 Therefore， anything that you do with post will not be stored and saved most of the time。Now put。

 I use put to request data for the specified。 sorry， that's a typo Use put to change data on。

On the server side。 So why do we have put and post then。Well， put requests are indpotent。

 So what does that mean， This means that calling the same put request multiple times will always have the same result。

Whereas if you called posts multiple times， you could have repeated values。

 So let's say you had a for loop and you just kept doing put over and over and over again to say。

 you know， that guy's name is Sammy。 You can do that over and over again， right， If you use put。

 you only see that one time。 That's exactly what you want， even though it's a bug in the code。

 If you use post， you'll have a huge list of a bunch of people all call Sammy with no new information。

 So put is for indeppotent requests。Finally， we have the head method。

 So this is almost the same as the get method， except without a response body。

 So that doesn't make sense。 I thought get was just for getting things， getting to us， right。

 That's probably what you guys are thinking。 Well， head is good when we wanted to just see what we're getting before we have download the whole file。

 So， for example， if you're about to download a huge Json file。

 instead of wasting time actually downloading this huge thing。

 you can use head to check first and then download it once you know exactly what it is or reject that download。

😊，But how do APIs actually send us the data that we want？ Well。

 there's two very popular formats for moving data around。Firstly， we have Json。

 which is jascript object notation and X M L extensible markup language。

 So we're gonna focus on Json just because it's very popular now。

 So Json is the standard for serializing data object in human re format。

 Json can be read very easily by humans and computers because the way it's formatted。

 And you'll see that when we get onto it。😊，It's popular as a common format for browser server data exchange。

 It's used by different languages systems beyond just javascript。 So don't worry。

 if you don't know any jascript， you can use this in many， many different languages。

The documents you have are a nested structure， and the basic idea is that it's made up of key value pairs。

Xl， the other hand， is an older data format that's still very powerful and still widely used。

But one that we're not gonna focus on is because a lot of the API that you will see will not be using X M L。

Again， the documents have a nested structure， and the base structure is that you have nodes。

 You have a big node like this with sub nodes in between inside it sorry。

So let's look at the Json structure。 So the Json is made up of arrays and objects。So what's an array。

 Well， array we've seen this in like multiple languages is just a list。

 a comma separated list surrounded by square brackets。And object， on the other hand。

 is surrounded by curly brackets and contains a comma separated list of objects。

Of sorry key value pairs。And a key value pair is in the format of key slash field name in speech marks。

 So you have to have your key field name in speech marks and then a value。

 So let's see this like in practice。Or first， let's go over data types。 My bad。

 So there you can have different kinds of types in Json。 So here's the main ones。 You have integers。

 floating points。 Those are your numbers， you know， whole numbers， decimals。

 You can have a string which must be surrounded by double quotes。You can have boolean。

 So that's the keyword true or false。 And notice here that the T and F are a lowercase。

 That's important because if you don't do it， you might have errors。You can have nested arrays。

 nested objects， and then the null value。 So those last two， second， last two， sorry are pretty。

 pretty powerful because that means you can have a huge Json object with multiple Json chunks inside it and multiple arrays inside it because you have this nested structure。

 And that allows you to send a lot of data very quickly。

 And it's very easy for computers and humans to read。So let's look at this U IU student Json。

 And this is correct。 Json。 It about validated everything。 So as you can see。

 it's pretty easy to read。 We can see that at the top， we have the name， which is John Doe。

 the U I N， which is an integer， which is string stringing up。😊，A bunch of numbers。Their email。

 which is again， a string。 I'm gonna skip classes for now and then go to the bottom。

 which is the foreign language completed， which is true。 That's the boolean。

But now let's take a look at the classes， because that can me look confusing。

So notice that there's a square bracket just outside classes。 So classes is an array。 Great。

 So we know what class classes holds a list of something， a comma separate list of something。😊。

But what's inside classes， In classes are objects。 Notice the curly brackets。

 So the class is an array holding a bunch of objects， which are the classes。

 So we can see that inside the object all of a name and the grade， etca， etc cea。

 And this shows that how powerful Json can be because you can have nest structures like this to store a lot of data into one document。

 about one person。😊，So you have the object as a whole。The this something is whole。

 And you see it's surrounded by curly brackets。These are the key value pairs。

All different colors are different key value pairs。We have our array as a whole。All。

 so the yellow indicates where the array starts to ends， and we have the colored objects inside。Now。

 how do we tie all of this together。我。Firstly， we want to read the API documentation to get access requirements。

 So what does that mean， Well， different APIs are very different in how we use them。

 But most of them involve getting a URL and API key。 So let's talk what API keys are next。So often。

 APIs will ask you to uniquely identify yourself so that they know who you are。

 This is so that if you paid for the service， you get exactly what you're gonna what you paid for。

 or if you're an anonymous user， you're not gonna abuse their systems and dedo them or crash their system。

So youll probably need to get an API key。Thirdly， you want to generate a URL from the API documentation。

 So similar to the get request， we want to have a URL that we can send request to。

 So you can find this in the documentation。Next is optional， but highly advisable。Optional。

 the highly advisable is you want to test your request。

 either in your browser or using a tool like postman。 So we're gonna use postband later on。

And you test using Hl request and check the app， which is often in Json。

 That's how we tie everything together。 And finally， you want to integrate this into your program。

 And this is， although it's just one step is actually a really。

 really big step because you have to first test everything and then try and put that thing that you've made into your app without breaking everything else。

😊，So now let's go into a demo using API calls。Alright， so let's first look at this website over here。

 So this is a website called Recrs。 It just gives you a bunch of dumb like API。

 These don't actually do anything very important， but you can use it to test your own API calls。

So let's go over here to this thing called single user。So we can see it's a get request。

And let's say we wanted to see what the URL was。 We can click over here。

And if we were to make the get request， this is where we're going to get。

 We're gonna to get this Json string。So let's do this in postman。

 because let's say we weren't able to open this link like this。

 We wanted to see more information about it。 So I'm gonna copy this link。

 And this is postman over here。嗯。I can open a new request here。Let's just call it。Example， get。

I'm going to create this。And now I can paste the URL here and we see that we can change the kind of request that we want to make。

 We're gonna to stick with get for now。 And when we send it。We get the Json data。 And as we can see。

 it's automatically pretty printed。 So we can see。Very clearly what this person Json holds。

Any questions about this。O。And's gonna， but this like isn't very useful。 Like。

 this does not give us a lot of information。 So let's do something that's more applicable。

 So I'm going to talk about Google custom search。 So Google's custom search is a feature that lets you make your own search engine that you could either use to search the entire web or just a couple websites。

 So if I go to geeks for geeks， for instance。

![](img/9e64b7e099393787c2dae2684094a60d_1.png)

![](img/9e64b7e099393787c2dae2684094a60d_2.png)

This search bar here at the top is a Google custom search bar。It's designed。

 It's built off of Google's own search engine， but only searches Es for Geek's web pages。

So over here， we have the searches。 It's pretty basic。 We can make searches like， let's say。AI。

We get a bunch of results here。Or computer science。We get a bunch of results here。

 But how can we use this in our own programs， Well， to do that。

 Google has its own URL that we have to URL path。 we have to follow。 So if I go to Google。



![](img/9e64b7e099393787c2dae2684094a60d_4.png)

![](img/9e64b7e099393787c2dae2684094a60d_5.png)

Custom search API over here。We see that they specify a format for us。

 So I'm going look through documentation。And we see， this is how they want us to pass。This story API。

 I want to get a URL like this and put the parameters at the end。 So because it's a get request。

And we can see that the way they want to do it is we have the URL。 We give our API key over here。

We put our search engine key over here and finally， our query at the very end。

So I've already done a query over here in Postman that we can take a look at。

 So notice that I I blurred out my API and my search engine keyeks。 I don't want to get hacked。

 And then I the query that I did was CS S 196。 So let's look at the JSO output。

Let's makes a little bigger first。First I copy this into the S code。



![](img/9e64b7e099393787c2dae2684094a60d_7.png)

Let's take a look at this， JO。哦。Stop。Okay， so if we look at the Jsson。

 we get a huge amount of data here。 So firstly， let's make this a little simpler for us。

Using V S coding other I D， you can simplify your Json queries into the main chunks。

 And this is again， showing Json's nested feature。 We see we have the URL here。

 And you have the kind。 So the kind is a custom search。 now we have the URL in the URL。

 We get exactly the query that we made。😊，Pretty basic stuff。In the queries。

 we see that we made this search here。 We get a total number of results。

And then other information regarding the query that we just made。

Now we can look at the actual information here。Search time， formatted search。And then finally， items。

 So items work really takes a lot of space。 This is all the results that Google found for us。

 And mean see the top result here is this link here。😊。



![](img/9e64b7e099393787c2dae2684094a60d_9.png)

So let's paste this。 Let's get this link。 We paste it into Google。



![](img/9e64b7e099393787c2dae2684094a60d_11.png)

It's the 196 website。So that's pretty self explanatory the Google custom search engine lets you make queries on the fly using Google's own software。

 So any questions about the custom search API。Or anything regarding the API so far。O。



![](img/9e64b7e099393787c2dae2684094a60d_13.png)

Then we can get right into the Kahoot。 so let's do the Kahoot。



![](img/9e64b7e099393787c2dae2684094a60d_15.png)

🎼。🎼，🎼。🎼The。🎼爱。🎼。🎼。🎼，🎼，🎼The。🎼，🎼The。🎼。🎼てん。🎼，🎼拜は。🎼，🎼Is everyone the。🎼我经。



![](img/9e64b7e099393787c2dae2684094a60d_17.png)

哎。🎼。

![](img/9e64b7e099393787c2dae2684094a60d_19.png)

🎼嗯。🎼，Okay。I don't know who got this wrong， but API stands for application and programming interface。



![](img/9e64b7e099393787c2dae2684094a60d_21.png)

We said at the start。

![](img/9e64b7e099393787c2dae2684094a60d_23.png)

![](img/9e64b7e099393787c2dae2684094a60d_24.png)

🎼うん。🎼，Okay， great。 So everyone got it right。 So there's two answers here。 So firstly。

 let's say why other two are wrong。 So maze game is solving a maze using AI locally。 Again。

 if you're not making a request to something external， it's not an API call。

 similar with Instagram applying filters to a photo， I've tried this。

 you can do this offline with no Wifi。 So again， no API call。

 So a flight website checking the offsite server to see what flights are available。😊。

I think Kahod cut off my last couple characters。So when you have。

 when you go into the flight website， you look for any flights。

You have to make an API call to all the different like flight companies to see which flights they have given a date and time。

 Similarlyly， with sharing link to Facebook on an external website。

 Facebook doesn't hand out its source code to every single company that wants to use like a share button。

 It just uses an API call to protects itself。 while allowing that giving external website the functionality to share content to Facebook。



![](img/9e64b7e099393787c2dae2684094a60d_26.png)

That's the leaderboard。

![](img/9e64b7e099393787c2dae2684094a60d_28.png)

![](img/9e64b7e099393787c2dae2684094a60d_29.png)

🎼嗯。😀，Who got this wrong， speak to me afterwards。Yes， and you can definitely use APIs in your 1。

96 projects。 It's totally okay。 Obviously， do not just take。

A whole project from Github and give that to us because we will find out。

 But you're totally allowed to use APIs and other libraries。🎼嗯。🎼，🎼。Yeah。Okay。So this one is all hard。

 The request for， the query string for a G request is passing in the URL。

 So if I go back over here for a sec。If we look at this directly。In the diagram here。

 you see the G request is directly in the request line or or directly in the URL。

 And we also saw that with Google custom search。

![](img/9e64b7e099393787c2dae2684094a60d_31.png)

![](img/9e64b7e099393787c2dae2684094a60d_32.png)

![](img/9e64b7e099393787c2dae2684094a60d_33.png)

🎼。🎼，🎼，Okay， so Gar requests。I think one person messing with me。 I don'm not sure who this is。

 use G requests to get data。

![](img/9e64b7e099393787c2dae2684094a60d_35.png)

It's like in the name， you get data。 you're not changing anything。



![](img/9e64b7e099393787c2dae2684094a60d_37.png)

。It' not saying， okay。🎼。🎼，🎼这。Alright， so post is safer than get。 So both of them aren't ideal。

 Neither of them are perfect。 and you should definitely， if you're sending passwords and stuff。

 should never just use post， but get queries can be cached in both the browser and the server web logs。

 whereas post cannot。 So it's slightly safer， buts still not that safe。



![](img/9e64b7e099393787c2dae2684094a60d_39.png)

![](img/9e64b7e099393787c2dae2684094a60d_40.png)

That round really changed its leaderboard。

![](img/9e64b7e099393787c2dae2684094a60d_42.png)

🎼咚。🎼，🎼The。🎼，All right，Most you guys are right。 So ineppotent means like with the put method。

 it just means I gave way the next question。 It just means that if you try to do the same command over and over again。

 like inserting Sammy into a database over and over again， it won't happen。

 It'll just have one result， and it will not keep app more and more copies unlike the post method。



![](img/9e64b7e099393787c2dae2684094a60d_44.png)

![](img/9e64b7e099393787c2dae2684094a60d_45.png)

![](img/9e64b7e099393787c2dae2684094a60d_46.png)

🎼，🎼はいオケーオッケーオッケーた。😊，🎼哎。Okay， so it's 6 seven， eight，9 that order。🎼あさ。🎼，🎼啊，fiix3个。Oh。

I'm really sorry about that。We could probably， I don't know。

 We could probably leave this one for like extra credit or something。



![](img/9e64b7e099393787c2dae2684094a60d_48.png)

So full disclosure， the next two are also Json questions。

 and I hope they're formatted a little better。

![](img/9e64b7e099393787c2dae2684094a60d_50.png)

![](img/9e64b7e099393787c2dae2684094a60d_51.png)

🎼，🎼，🎼How many塔 they gone。🎼。

![](img/9e64b7e099393787c2dae2684094a60d_53.png)

Okay， that one is pretty tricky。 let's take a look at the image。So if we look at the toppings here。

 it's an array。 So we have the square bracket here， square bracket here。

But the array is not like in Ru。 We can have multiple different data types。

 So you notice here we have this pizza object as one of the toppings。

And then peppers is another topicping。

![](img/9e64b7e099393787c2dae2684094a60d_55.png)

So two toppings was the answer。And I again， gave the answer to the next one。



![](img/9e64b7e099393787c2dae2684094a60d_57.png)

嗯。The。🎼But。🎼The。Okay， let's look at the image again。 I did just say this。 but， yes， one of the。

 one of the toppings is a whole extra pizza。 So if we look over here。



![](img/9e64b7e099393787c2dae2684094a60d_59.png)

And the topics actually， we have another object is one of the toppings。

 And this is a pizza object because it has a size crust cheese level toppings。

And then also peppers on top of the pizza。

![](img/9e64b7e099393787c2dae2684094a60d_61.png)

So yes， this person did order a whole extra pizza as a topping。



![](img/9e64b7e099393787c2dae2684094a60d_63.png)

How sorry I skip the leaderboard。

![](img/9e64b7e099393787c2dae2684094a60d_65.png)

🎼。🎼道我你少机没多。🎼裙子。🎼Yeah。🎼，Allright， great。 So yeah， XL and JSON use a nested structure。

 and that's why we have really crazy things， like putting objects inside objects。

 inside objects and having as pizza's toppings。😊。

![](img/9e64b7e099393787c2dae2684094a60d_67.png)

![](img/9e64b7e099393787c2dae2684094a60d_68.png)

![](img/9e64b7e099393787c2dae2684094a60d_69.png)

嗯。拜拜。🎼，All right， so the job， guys， you do not put speech marks。

 You have to put speech marks around a key field in JSson。 So if you have like name for instance。

 and then my name， you have to put speech marks on the name and also the name put the string。

All right， let's take a look at the results。

![](img/9e64b7e099393787c2dae2684094a60d_71.png)

Okay， all right， so congratulations， top three and run up。🎼啊。🎼3。



![](img/9e64b7e099393787c2dae2684094a60d_73.png)

Alright， so the key things I wanted to hit on today were the APIs are a really powerful tool that you can reuse。

😊，So you can reuse code if' going to reinvent the wheel every time。 Also。

 you can use in any language。 you in Python， Ru， Java。 It is very expansive。 And secondly， finally。

 sorry， you can use these in your projects。 We're not gonna say you're cheating or anything。

 If you use an API。 APIs are using industry as well。 So please， you're more than welcome to。



![](img/9e64b7e099393787c2dae2684094a60d_75.png)