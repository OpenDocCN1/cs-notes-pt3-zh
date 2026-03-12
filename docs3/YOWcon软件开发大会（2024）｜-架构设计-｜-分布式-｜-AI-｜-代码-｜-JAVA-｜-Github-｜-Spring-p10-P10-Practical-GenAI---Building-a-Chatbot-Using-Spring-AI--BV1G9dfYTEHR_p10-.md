# YOWcon软件开发大会（2024）｜-架构设计-｜-分布式-｜-AI-｜-代码-｜-JAVA-｜-Github-｜-Spring-p10-P10-Practical-GenAI---Building-a-Chatbot-Using-Spring-AI--BV1G9dfYTEHR_p10-

![](img/71d6ce2d83903e99fbe9737a68e40218_0.png)

So。What I'm aiming to convey today。Is that as enterprise developers。

 and given that most of you have used spring， I'm assuming you are mostly enterprise developers。

 enterprise developers have a really important role in making Gen AI usable。

G O I is a very real thing。 It's not going to go away。

 but it is something that is extremely difficult to use in business applications。So， you know。

 the importance is uncontestable， but you read a vast number of blog posts。That are very。

 very far removed from reality。 So what I want to talk about is how， hopefully。

 all of us in this room can use the skills we have to get closer to reality。

 So I want to show some of the core concepts of building or Gen AI applications or Gen AI。

 enabling existing applications。 I want to show that you can do this in the JVM。

 and that the JVM is competitive with Python for building Gen AI apps。 And also。

 I want to show you both some of what I consider to be best practices。😊，And also。

 some of the challenges。But before we get there， let's， let's think about spring。

 Spring has been around for a very long time。 I have the beach ball of death。 This is not good。 Okay。

 spring has been around for a very long time。 It， in fact。

 dates back to the beginning of this century。 So yet it's still around and it's still thriving。

Let's think about why that is。And I think there's really three fundamental reasons。 One is。

That the spring team is awesome。 And certainly， you know。

 one of the things that I am most proud of in my career is that I assembled the genesis of that team。

 which has continued to be involved in spring and lead spring for decades。

 The spring community is awesome。 And that obviously， you know。

 overlaps with the spring team because the spring team is part of the spring community and comes out of the spring community。

😊，But thirdly， spring is built on some very solid。Core concepts。

 and those core concepts have stood up incredibly well over two decades。

So if any of you have been involved in the spring community since the beginning。

 you'll probably remember something that we used to talk about called the spring Triangle。

That was the three key ideas that have always been called a spring。They are dependency injection。😡。

As portable service abstractions。And aspect oriented programming。

 dependency injection is obviously how spring components get to know about each other and get to know about infrastructure。

Portable service。😡，Abstractions are how spring apps can work with underlying resources and capabilities。

 For example， one of the first killer things that spring did was enable you to write an application that could provide transactions either in。

 say， a Tomca environment or a webpher web logic distributed transaction。😊，Environment。

AO P enables you to combine those two things。 So， for example， if you're using spring。

 you've probably used or seen the transaction interceptor。😊。

Where you have at transactional annotations on your methods， that is enabled with spring O O P。

 which intercepts calls to those methods and applies transaction management。

 So it turns out that these three core concepts have been a gift that is kept giving for decades。

 And it turns out that， as hopefully， I'll be able to convince you。

 they are extremely powerful and suited to dealing with the challenges of building Gen AI applications。

😊，If you've。Thought about Gen AI or worked with it。

 There's a pretty high probability that you've used Python。Certainly。

 there is undoubtedly a Python affinity in machine learning。

And it has reached the point where I truly believe that every developer needs to know Python。

 I think it is the one language that every developer is going to need to know。 So if you don't。

 if you're not already fluent in Python， I would strongly encourage you to get fluent because I really think that's important。

 And get by getting fluent， I also mean getting fluent in current Python。

 Python has improved a whole lot in the last few years。 If you look at， say 3，12。

 It has kind of like a type system。 Ty hints are really quite good。

 It's certainly way better than Python 2 incomparably better than Python 2。

 And it's even significantly better than early Python 3。 So I would say just side piece of advice。

You should know Python。 You should be able to read it。 However。

 that is absolutely not the same thing is saying that you should be building applications in Python rather than Java or dotnet or whatever else you're using。

I think it's important to be able to read Python and write Python because there is a lot of work in machine learning in Gen AI that's done in Python。

 And if you want to keep up with all the experiments that people are doing。

 it's really important to be fluent。 But I really believe that if you're building enterprise applications and that need Gen AI。

 you're better to stick with the stack that you're presently using and the Gen AI capabilities that are now growing on that stack。

 So in this presentation， I'm going to do live coding using spring AI。

 and you'll be able to see that Java or Cotland or whatever language you use on the JVM is really quite competitive。

 now in Gen AI。 Okay now we get to the exciting point where this demo is cursed。😊。

I have given this talk or a variant of this talk twice before。

 each time has been accompanied by disasters and clearly the like internet not working one talk that I gave in San Francisco three wireless mics ran out of battery while I was trying to talk this time our challenge is the beach ball of death So yep。

 In is really dead。Okay， so yep， it's just intelligent。 Okay， let us try for squt。Yep。

 its intelligent。Okay， interesting。Well， if I can get intelligentj up， we will get to look at， okay。

HThis is what it was doing this morning when I couldn't work out why Intel J was not。

It just started and minimized itself。I tried reboring this morning， didn't fix this problem。

 Unfortunately， I don't remember what did fix it。It， I had this exact problem this morning。

 what if I。Has anyone seen this where。W， okay， that's fascinating， okay。So we have Inj up。

 So what I have started by doing is creating a new spring boot app。

 and I did that by going to start do spring do AO。 So with the spring initializer you can see on the right the packages that I took open AI o Lama。

 which are from spring AI the Neo4j vector database， spring data Neo4 J in the spring boot actuator。

 So by the way， the project that I have is on my Github So Johnson R is my Github I and this repo is currently pinned is spring AI demo So very important to know that if InJ crashes completely you can still actually get to see the code。

 So I will endeavor to show you some of the code now So what I'm going to do is build a simple chat bot and demonstrate how we go about。

😊，This in Chava。 So the first thing that we need to do is have fundamental kind of table stake setup。

 So there are two core concepts that spring AI has in accessing Gen AI models。

 One is called a chat model which is essentially an LLM like one of the open AI LLMs like G 4。

 The other is an embedding model。 embedding models are used for vector similarity search。

 and they are a very important part of the whole setup。

 So you can get your chat model set up using spring AI is simply by importing a starter。

 So if you import a spring boot data for open AI， you will automatically get a chat model。

 In this case， one of the things that I want to show is that you can use more than one chat model in the same application。

 So I'm explicitly configuring it。 So I am。😊，explicitlyicitly configuring it using a spring at configuration class。

 and you can see here I've got two chat model beams。I've given them separate names。

 but you can see that I've used the at primary annotation on one of them So I just inject the chat model anywhere。

 I get the default chat model， So the default chat model is the default open AI chat model。

 which I think is G 40 currently in spring AI， but I've also set up a local chat model。

 which is an O Lama chat model， has anybody used O Lama OLAMA。

O Laama is a very cool open source project that enables you to work with open source models potentially locally。

 So there's been really a lot of evolution in the world of LLMs in the last year。 say 18 months ago。

 even 12 months ago。 open source models were not that you could run on your local machine with not a whole lot of use for most things。

 Now they are definitely quite usable for certain things。

 And thats that's kind of a game changer because remember if you look at the that the resources consumed by models like G 4。

 They are so inconceivably massive that your you know。

 your laptop can't not only could it not possibly do training or phone tuning。

 It can't remotely do inference。 And it also means， of course。

 that these big models have a very high environmental。😊，Fprint， they use a lot of electricity。

 and they use a lot of water。 So， you know， one of the things that I would say in terms of best practice。

Is use the smallest chat model that you can use for any purpose。 That gives you two benefits。

 One is it means that the planet might last a little bit longer。But secondly。

 it means that you have more ability to explain what's happening。Let's suppose that， in theory。

 big models were able to eventually do anything we wanted to do。

That would still be pretty scary for a business application。 You know。

 why was a particular response generated。😰，I don't know there's， you know，1。

2 trillion parameters in the model。 Clearly， some combination of them said this is a response we should have。

 That's really not adequate。 So if you can think of your applications in terms of potentially breaking them up into smaller。

Interactions， you have a greater ability to explain。 So， you know， unfortunately。

 to the best of our knowledge at this point， L L Ms are probably always going to be black boxes。

 neural networks have always been black boxes。 but there's a difference between an application that's wholly reliant on a giant black box and an application that uses a number of much smaller black boxes and potentially makes decisions between the invocations。

So。Remember the spring triangle， which parts of the spring triangle are relevant to using multiple LLMs。

 Well， there's clearly two。 One is the portable service abstractions。 So when we inject these things。

 the chat model interface will be the same。 So we will get a high degree of portability between these different things。

 That is something the framework provides for us。 Another thing， of course。

 that is relevant is dependency injection。 we're going to be able to inject our chat models。😊，Here。

 of course， I should say that getting portability between LLMs and embedding models is not unique to spring。

 Obviously， this is something that Python frameworks like Lngcha and Lama indexdex have done for some time。

 There's also Lng chain for J。 But the point I would make is that naturally。

 you would expect spring AI to do it。 And it now does it very， very well。

 So portable service abstractions。 We've got that。Now we have set up our configuration。

 we can inject chat models。 So here is our application。

 It's just a very straightforward springbo application。

 The most interesting thing is the chat service。😊，Chat service uses something called a conversation session which is a session scope component。

 not particularly relevant to GenAI， but just an example of how know if you're building this app。

 you can kind of app， you can use all the things that are given for you in the spring framework like transparent management of conversation sessions。

😡，This is the most interesting thing。 So here we have simply injected our chat model。

 Which chat model do we get when we inject the chat model by default。 We get the primary one。

 I've also injected an oama chat model In the next milestone of spring AI。

 there's some really nice stuff that is going to be available around injecting multiple chat models。

 but in this case， I'm differentiating them by the type。

 I could also differentiate by using an app qualifier annotation。😊，So once I've got a chat model。

 I can build a number of chat clients。So the way to think about this in spring AI concepts is。

You have your provider， like Oama or。Open AI。 And you have one or more。 very often。

 one chat model that talks to a particular model from that provider。

And that takes care of the low level transport， right， the core connectivity。 However。

 when you use that chat model in a particular application context。

 you may want to use a different system prompt， for example。

 you may want to have different observability， different。 you know。

 interactions in the use of that model。 So that is where the chat client sits as a higher level concept。

 So you can typically have one chat model and a number of chat clients。

 So chat clients typically use。A system prompt。 in this case。

 the system prompt comes from system prompt dot M D。 and what this。

Does is set up the basis of every interaction。 So the messages that will be exchanged in a conversation typically start with a system prompt and then are in exchange of user messages and assistant messages。

 and assistant messages is a response from a chatbo。

 and the system prompt is kind of sets up the whole conversation。 So in this case。

 the system prompt says that the chatbot's a helpful assistant working for classical music emporium。

 And it helps users discover classical music and learn about composers。 Okay。

 let's run this and see what it does。 So we will start it up。😊，And oh dear， the zombie one see demo。

 the zombie one is still using that port from the previous。Oh god， how do I kill。Oh。嗯。嗯。

I've got to cure whatevers on Po 80， you know what？There is a easy command for this。

 but we're just going to totally avoid that。 And we're going to do this。

 So our demomo is now in port 8081。 No， oh， there's another one on 81，81， seriously。

So I said this demo is cursed。Yeah。8083 can not be in use。Okay。

 I have absolutely no idea what is going on here。 I have never put anything in my life on port 80，87。

 So if this is not going start up。啊。Okay。There is nothing on  I87。Oh， there is something in 8087。

 Okay， okay，8094， this is， no， thats gonna be fun。😊，We got to find something somewhere。

1994 sounds like a good part。How can this be。Not every single port。I am utterly baffled。 Okay。

 we're going work backwards。 We're going to find right 300， which is normally used by node。

 I am not running any node projects。 So let's be sneaky。 Let's get in here。😊，Okay。Okay。

 let's see if it's any better if I run it this way。I have absolutely no idea how to。It's， yeah。

 it is。 But what started it。は。I think this has to be intelligent。 Okay。

 I'm going to quit intelligent， and it will presumably kill those。あ。嗯。Yes， thank you。

 That is the one that I can never remember。 Okay， so， okay， so now we're gonna go back to， well。

 let's go back to。80，80。80，80， okay， actuated health endpoint is not up。 Nothing's up。 Okay。

 let's try。 Come on。 It has to be intelligent， doing something evil。呃。Now， 8080 is there。

 but Intelligge has died。Okay， I'm gonna use， okay，80，81。 Okay， I'm going to use 80。81。

 and I'm not going to use Intel。 I'm going to use the Springbird run。Okay， so。I have absolutely。

 I'm sorry。 I have absolutely no idea what's happening。 I think it has to be intelligent。

 but exactly what it's doing。 I don't know。 So how can。So 8082。 Okay， so well， well， we。

 we're just gonna go through all ports in turn and hope we can actually show you something。

 So we're going to， if this comes up， well， there'll be something on 8082 as we burn each port。

 Something's on 8082。 So let's have a look at it。😊，Okay， so who are you。

 So this is going to go to the chat model in the sky。

 And you can see that it has used the system prompt。 So it's a helpful assistant？

 So now let's ask it， Do， do you have， does your business have physical stores。

So what happens when L L M doesn't know the answer。So there are two things that can happen。Yes。

 it can I either say it doesn't know the answer or it can just make it up。 In this case。

 it kind of made it up。 I mean， it's quite possible。 that could be right。

 but it it is clearly not something we can depend upon in our applications。

 So the system prompt did succeed in that it helped us， you know。

 direct the user towards interactions around classical music。

 but it didn't succeed in grounding the response in anything sensible。

 So if we wanted to answer questions， we need to change our chat service。

And we need to essentially provide what is called retrieval augmented generation。

 Retrieval augmented generation is a core technique for avoiding hallucinations。

So what this means is that we， when we are asked a question。

 we look up the materials that might be relevant to answering that question。😡，How do we do that？

So clearly， we've got to have a database that is storing potentially relevant materials。

 And secondly， we have to have a strategy for querying that database。

 The normal data store that we use is a vector database。

 And the way this works is we've taken a lot of content， for example， text content。

 we have embedded that content ten。 So we've done vector indexing。

 So each chunk of content in the database as a vector associated with it。

 And when a question is asked or we need to find something relevant to a conversation。

 We go to that database and say， what do you think is the most similar content that is relevant to answering this question。

😊，So the way in which I've enabled this involves two things。

 The first thing is that we put a question answer advisor in。

 this is something that comes from spring AI and spring AI gives us a simple out of the box implementation of retrieval augmented generation。

 So what this does is actually behind the scenes。 It's going to edit our prompt to include this。

So the user message will be。Extended by adding this。

 So what this question answer advisor will do is go to the vector store。

 say what is most similar to what the user asked。Put it in here。

 And then the model may be able to answer the question。 Obviously。

 we need a vet needed a vector store as well。 If you recall in the。The way we set this up。

 we use the spring AI Neve store starter。 So again， we come back to portable service abstractions。

 Spring AI supports pretty much all the popular vector stores。

 There are two fundamental schools of thought on vector stores。

 One is that you use a dedicated vector store like P cone。

Another is that you use the vector capabilities that are being added to pretty much every database。

 So in this case， because I'm using neo for J for other things。

 I'm using neo for J's vector capabilities， which are quite good。 If you are， for example。

 using Postgres， P G vector is really， really， very good。 So， for example。

 if you're using a spring JPA application using Postgres。😊，You really。

 your first instinct should be to use PG vector and add vector capabilities to Postgress。😡。

So we're going to restart this。 And this is truly exciting because I have absolutely no idea what's going to happen。

 So we have， well， actually， I'm pretty sure it's going to fail。 Okay， so were only use port 80，82。

 Let's go to 8083。 mind you it shows you how easy it is to configure spring applications。

 So we restart this go to 80，83。 And hopefully it's the right 83，8083。 We're going to。

 we have in some setup code， which you can find in the repo。

 you can see that I have index some existing documentation。 So this tells us about the stores。

 So yeah， we， we put in a little bit of data that hopefully will make this work。

 Do you have physical stores。😊，So very different response。

 We have been able to ground the response in solid fact in this case。

So that's one of the fundamental techniques of you know， making L L Ms useful in production。

 And as you can see， it was very easy to set up basic rag using spring AI。

 If we go back to the chat service， you can see the way I configure this。 So we've got default。

Advises。Which include the message chat memory advisor， which is where we store all the messages。

 And that， as you would expect in spring， is pluggable， portable service abstractions。

 And we have the question， answer advisor。 Any， remember the term advisor。 It's an AO P term。

 isn't it。 So this is， you know， essentially an application of AO P concepts to chat。

 So the advises are essentially a pipeline of interceptors that。

Are involved in generating chat responses。Okay， let's have a look at what else we could do with advises。

 Remember what is AO P good for， AO is good for addressing crosscutting concerns。

 AO is also good for having like really， really offput terminology。

 like join point and crosscutting concerns。 But essentially。

 what AO enables us to do is to apply consistent behavior across multiple things。 So， for example。

 transaction management。 What kind of consistent behavior might we like to apply across multiple chat interactions。

😊，Well， one pretty obvious one is a toxicity guard， right。

 If we want to guard against prompt injection， guard against， you know， toxic interactions。

 that's a very obvious example。 And it means that you potentially have the ability to build components that are reusable across multiple applications。

 Okay， now let us build a， or I'll show you a。😊，Out of the advise that is not out of the box。

 which is one that I have authored myself。 So let's have a look here at the topic guard。

 So I hasten to point out that this is not something that is production grade。

 It's just an illustration。 And what I'm going to do is guard against unpleasant。

Or irrelevant topics。 So in order to do that， we need to classify the topic that the user seems to be talking about。

How are we going to do that。 We're going to use another L LM。 We could， of course。

 use a much smaller model for a classification model。 But in this case， we're using the local LLM。

 So here， when we create this， we're giving it a chat model in the constructor。

 and we're going to classify the topics。😊，Very simple Cotland data class， as you can see。

m using Cotland， rather than Java。 I do find Cotland， an extremely pleasant language to work in。

 And it works brilliantly with spring。 But， you know。

 you could write this in Java and it work exactly the same way。 So we're going to classify the topic。

 And the topics that we have as sport， religion， politics or other。 And I think， as you can guess。

 we probably don't want to talk about politics or religion。So to do the actual classification。

We will use a different chat client remember I said that chat clients are kind of essentially lighter weight than chat models。

 we can have multiple chat clients。In this case， we're going to use a quite different prompt。

 which is topic guide， which looks like this。 There's a couple of things that are different about this prompt to the other one。

 One is that I happen to use a convention of X， M， L like convention to delimit the content。

It's usually a good idea to try to be very clear about what things are like， you know。

 being assessed versus what is kind of system prompt doesn't need to be X M L style。 But， you know。

 this concept of delimiting something that should be assessed by the models important。

And also notice here that we've got curly brackets。 So this is actually a template。

 It's not going to be a literal string。 We're going to replace that dynamically with the value that we have at runtime。

 So in this case， we're using the default out of the box prompt template syntax。

 which spring AI provides， which is compatible with Python F strings。😊。

This makes sense because Python is obviously， as I mentioned。

 a very popular language in the world of Gen AI。 The next milestone of spring AI is going to probably have additional prompt templates。

 like possibly ginger and moache。 So additional templating technologies。

 So here we've also set a parameter to say that the user content is going to be passed to that。

 But we've done something quite different here。 Remember that this interaction is not about generating a response to the user。

 This interaction is about returning a JVM object。 This interaction is about returning this object。😊。

Turns out that particularly when you're building business applications。

 a lot of the interactions that you have with LLMs are not just generating free text。

 They're generating structured output。Again， this is the kind of thing you would expect a framework to help you with。

 And in fact， spring AI does。 So see， when we make the call here， previously。

 we asked for just the response and we got text back here。

 we're asking for an entity and specifying the type of that entity。

That causes spring AI to do some magic under the covers。

 What it does is it introspects the topic classification class and adds some text to the model interaction saying。

 when you return， please use JSON。😡，To return this structure。

 So it generates a Json schema and passes it up to the model。

 The models have all been trained these days on returning structured data in Json。 So， yeah。

 it's highly probable that even a local model， like the small one that I'm using here is going to do that correctly。

 But notice we didn't have to write any low levell code for marshallling that Json response。

 The model that I'm going to use here is an o Lama model running on my machine。 It's much smaller。

 So these are the local models I've got。 So this model is。Gmma 22B。

And this is now up and running on my。 my machine told me something about Brisbane。This is running。

On my machine。 And it's not terrible。 So as you can see。

 there are certain things that this could be good for。 Like， for example， translation tasks。

 summarization tasks， potentially this kind of classification task。

 It would not be capable of doing the rag enabledable chatbo task that I have tried it And the results were really quite bad。

 Okay， so now we've got this up here， I'm trying to remember which port we're up to now。

 So why don't we go to， let's go to， we haven't burnt 8084 yet， have we。

 let's burn port 8084 and see what we get。This is the first talk I've ever had to do this。 This is。

 this is fascinating， so。😊，Hopefully， the topic guard will be in place。 so if we run it。

 despite it lying to me， it's still up。Do you like to busy。It'll probably tell me it's an AI。

 but it loves classical music。 I don't have personal preferences。 Okay， fair enough。

 Do you like Donald Trump。I'm sorry， but I can only help you with classical music。

 Notice that response was really fast as well。 Let's look at how that happened。

 That came from the topic guard advisor where we use this is banned topic method。

 So in the advise request。 We firstly asked if the topic was banned we did this using a ret template。

 because the local model is a little bit more flaky。 But guess what， we're still saving the planet。

 If the local model doesn't work 100% of the time and we have to reinvoke it。

 It's still better than using all that water firm open AI。 And if the topic is banned。

 we kind of short circuitr the response to say， I'm sorry I can only help you with classical music。

 So there's one other thing that I wanted to show which I think I'm just going to show the code in the two minutes I have remaining rather than run it。

 But we've seen one core technique for。Roounding L LM responses and avoiding hallucinations。

 That is rag Retrieval augmented generation。 There is another really important technique。

 And that's called function calling。 So at modern models have been trained to be able to know when they should call functions。

 So the way this works is you pass up to the model string saying， by the way。

 you might find these functions useful。 And so， for example。

 if the user wants to update their mailing address， call this function。 And by the way。

 here are the arguments。 So the way in which this looks in spring A I is rather consistent。

 So let's go to the chat service and put some function calling magic in there。 So we。😊。

Would simply do this。So， we would add。Default functions in this case。

 the functions have been injected。 Remember that in spring。

 you can inject a list as well as a simple type。 So this is going to say anything that implements spring function callback in my context。

 injected here and make it available。 So let's look at where they come from。

 They're in a file called functions And we're using the builder pattern to build function callbacks。

 notice that this enables us to implement functions with full access to the resources managed by the spring container。

 So in this case， I've injected the Ne4j template and these functions are actually interacting with Neo4j。

 So in this case， it's actually doing a database query and returning the response。 So， you know。

 another benefit of using spring AI is that。😊，You can really leverage everything you already have in your spring applications。

So look， I'm sorry， I really did want to illustrate the function calling。

 but I'll leave you with a few of what I think are best practices and a few challenges。

 best practices。Hes Cutlin。Spring today is really economical。 It is very concise。

 You don't really have to do a lot of configuration， a lot of duplication。

 When you see spring apps using Kotland， you realize that whatever duplication is in most spring applications today comes from Java。

 not spring。Secondly， externalize your prompts rather than burying them in strings。

 It really drives me crazy when I see people burying prompts in Python F strings or Java strings。嗯。

Thirdly， consider the use of multiple models because you should be able to use the most appropriate model for your scenario。

 Okay， well， if you want to see the full code， including the function calling。

 remember Johnsonsonar on Github and it' pinned as spring AI demo。😊。

