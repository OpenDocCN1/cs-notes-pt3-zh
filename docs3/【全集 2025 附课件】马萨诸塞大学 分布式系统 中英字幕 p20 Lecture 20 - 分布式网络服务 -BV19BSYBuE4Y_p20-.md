# 【全集 2025 附课件】马萨诸塞大学 分布式系统 中英字幕 p20 Lecture 20 - 分布式网络服务 -BV19BSYBuE4Y_p20-

Okay， it's a couple minutes early， but I'm just going to start and make a few announcements so。

As I had already posted on Piazza， we are supposed to have a class this Friday because Friday follows a Monday schedule but Ive cancelled that class because I am actually not here this Friday okay so for those of you who didn't know now you know。

There is no class on Friday， but there will be a makeup class on Tuesday。

 which is an out of cycle class but because I'll miss the Friday lecture I need to make up for it that class will be held in this room on Tuesday at。

😊，From 230 to 345 I'll send another email or a Piazza post with an email notification so that those of you who can come please do I know some of you might have another class at that time if that's the case somewhat unfortunate but this was the only time the room was available so I couldn't find a different time for the room so that's one thing the other announcement is about some of the things that we've been giving out as I mentioned lab3 came out a few days ago lab3 requires you to deploy your code that you develop on Amazon's cloud okay to facilitate that we have created accounts for you on something called AWS Academy which gives you free credits to run your code on AWS and for you to understand how to do that we gave out a lablet earlier today which is the cloud Lalet。



![](img/699358d61cf6aa9f62d53ad318ea3562_1.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_2.png)

That lablet really walks you through how to use AWS Academy to access Amazon's cloud how to start machines on the cloud and you can just use free credits to do that the only thing I'll say is once you are done with your shut down all the machines otherwise they keep incurring cost and eventually you will run out of all the free credits then you will not be able to use them for the lab so just don't forget to turn things off once youre done because they will keep incurring cost otherwise that's the only thing I really wanted to mention but if you have any questions about accessing AWS tell us and we can try to help this is kind of the last lab where you are deploying your code on the on the cloud and trying to make it a cloud application right？



![](img/699358d61cf6aa9f62d53ad318ea3562_4.png)

Okay so that's a good segue to the topic that we are going to cover today so we are done with the core topics that involve everything from clock synchronization to transactions to consensus so now we are going to switch gears and come back to practical applications of all of those concepts that we've been talking about for the last maybe seven eight classes or so we'll start with the web today and then we'll look at other topics like file systems and middleware in the next several classes so today's class and maybe next class is going to focus on the World web I'll talk today about web applications。

 web services and so on and next time we'll talk about web caching and and content distribution and how that actually ties into some of what we have been talking about in terms of caching and cash consistency and replicate。



![](img/699358d61cf6aa9f62d53ad318ea3562_6.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_7.png)

But let's start simple we'll start with web applications this is a picture that by now all of you should be familiar with we spoke about this in the second or the third lecture is a typical client for application using the web where the client machine is the browser the server machine is a web server and in today's class we are really going to dig deeper into how these server applications are buried how they can be scaled up and so on okay so thats the thing you want to keep in mind。



![](img/699358d61cf6aa9f62d53ad318ea3562_9.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_10.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_11.png)

So let's talk about the server component okay so so this is a pictorial view of the Apache web server okay Apache is an open source Apache web server or the HtTP server an open source project is the most popular web server that's actually used on the internet today typically if you go to a website any website is highly likely it's actually running Apache and there are other web servers as well but this is the most common one okay this is what I would call the functional or component view of Apache okay。



![](img/699358d61cf6aa9f62d53ad318ea3562_13.png)

Early on when we were talking about building server application I showed you a different picture which involved a threaded application where you had requests coming in they came to a dispatcher thread dispatcher thread send them to a thread pool that was basically the threaded view of the application because this is a multithreadread and a multiprocess server but this is the functional view assume assuming a request comes in and the request has been handed off to a thread how does the thread process that request so this is the path it's going to take it's pipeline processing so essentially the request are coming into an Apache core they are going to be handed off to some thread and then the thread is going to process the request in some number of stages and so in the Apache architecture these stages are called hooks each hook is going to actually cause the request to be processed by one or more modules modules are component that perform specific。



![](img/699358d61cf6aa9f62d53ad318ea3562_15.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_16.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_17.png)

Types of processing so for example， if you have SSL which is secure socket layer the request contents become in encrypted so you might have to decrypt that request in order to process it and then you can have all kinds of server side processing for example if you have things like jascript and so on those are modules that can plug in that Apache can call for specific types of processing so your request will go through many stages and then it will essentially complete and exit the system all of this is essentially a single process as far as apache is concerned so this is not a multi tier types scenario but these are all stages inside Apache so it's a modular architecture it's essentially you can have different modules that plug in you can configure Apache in different ways depending on what you want。

Apache to do， and then that's how it is going to process each test。Right。so。

Keep this picture in mind we come back to it in different context but this is essentially a functional view of the Apache web server now let's talk about a couple of different things and we'll come back to web applications the other concept in addition to the web server that I wanted to mention is the proxy server we briefly encounter proxy server in lecture3 where I said you can go from a client server architecture to a client proxy and a server architecture and a proxy is the intermediary that's sitting in between a client and some sort of a server proxies can perform all kinds of server in this example proxy the proxy here which is a web proxy performing what is called protocol translation so our web server or not a web server server here is a FTP server it allows you to do file downloads it only talks FTP now if you want to expose this file downloads through an。



![](img/699358d61cf6aa9f62d53ad318ea3562_19.png)

HtTP interface you can put a web proxy in front of it requests are going to come from clients as aTP request to download files the web proxy is going to translate them okay this is where its doing protocol translation from hTP to an equal and fTP request get back the response send back an hTP response that' is just one example of a proxy proxies are useful in variety of different context。

So another example could be this server。Not an FTP server。

 it is a media server it is just a server that is capable of streaming videos over the internet and this device here or a browser here maybe are running on a small phone。

Okay， so let's say the video content that is on the video server was。Encoded for a large screen。Yeah。

 so it maybe it is for a laptop screen or even a television。

 but now you want to watch that content on a small screen so what the proxy can do is it can bring the content。

And do what it's called。rancoing where it converts the content from one format to another it can make it tailored for a smaller screen。

 it can reduce the resolution to all kinds of translation and then send it to the browser so this is an example where it' is changing the content proxies can do protocol translation they can do content transformation they can do other things like caching as we will see lots of different use case so well get back to proxies maybe next class today we are mostly going to focus on the server and think about web applications and so on but but keep this in mind that in the web world proxies are used extensively for all kinds of different use cases。



![](img/699358d61cf6aa9f62d53ad318ea3562_21.png)

that clear。Okay so let's get back to web application so we seen this before this is a standard picture of a multiter web application where the server actually has multiple component the first tier here this is our Apache server it's only talking HtP typically you would take the application logic and put it into a different component which is in this case shown on a different machine altogether and then you can put the data itself on yet another component that's your data tier so typically you have a web tier you have a application tier it's called CG here but that's a really old way of writing web applications these days you write them in Python or any modern language are things like node Js jascript and so on so you write our application here that's it in the middle tier the backend tier is a database that's our three tier architecture and we are going to now build on that and try to do variety of things。

With that basic architecture。

![](img/699358d61cf6aa9f62d53ad318ea3562_23.png)

Okay， all right， so with that recap let's now talk about web cluster。

 so let's say you want to take an application。webb application and scale it up to lots of users so how are we going to do this we are going to make a cluster of servers so this is where we will replicate that web application onto multiple machines。

so you will have a front end machine where request will come in。

 a front end machine will send the request to one of those replicas， the replicas will process it。

 send back the response to the front end and the response will go back to the user。Okay， very' clear。

Okay， so now what if this each of those web servers are multi tiered？Applications。

 we have applications。What are we going to replicate what are we not going to replicate so think about what I showed you here right so so rather than a simple web server your application actually has three tiers right so here I only shown your replica as a single box but it could be each of them could be a three tier application。



![](img/699358d61cf6aa9f62d53ad318ea3562_25.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_26.png)

Right， so that brings up。Several interesting problems first is lets say。

So let's say you have a database。So you have put a database here。

 each of these things has a database and maybe it has a second ti sitting in front of it。

This just takes whatever I showed you on the previous slide and has actually replaced each of these replicas with a three tier application with a database at the back that's one way to do it but now if you do this you have multiple copies of that database okay you will have to implement some consistency protocol to ensure that your database is consistent if one of these replicas makes a change to the database let's say it's a shopping website the database has some product catalogs and it has order information and so on so if you make a change in one you are to then replicate it to all of the others so in in database world trying to do this replication can be expensive because consistency is something that database people care about a lot because we talked about asset properties and so on and if you remember。



![](img/699358d61cf6aa9f62d53ad318ea3562_28.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_29.png)

Besides， these are all expensive to implement at some level， especially in your application。就是他是说。



![](img/699358d61cf6aa9f62d53ad318ea3562_31.png)

Another approach is。Let's just get rid of this。😔，So。

 another approach is you can still have a multi tier application。

 but you don't replicate the data here so what you can do is you can put an application ti。



![](img/699358d61cf6aa9f62d53ad318ea3562_33.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_34.png)

I don't know why this is not。

![](img/699358d61cf6aa9f62d53ad318ea3562_36.png)

You can put this application here and then there is a single database here that they all talked。



![](img/699358d61cf6aa9f62d53ad318ea3562_38.png)

so there is a single database here at the top and then there the HtTP server is replicated。

 the code is replicated but the data is not replicated so there' is only single big database thats serving as your back and here so in this case youve gotten read of the need to maintain consistency across database replicas your code is still replicated so you are still getting some scalability because now you can process multiple requests in parallel across replicas but the database。



![](img/699358d61cf6aa9f62d53ad318ea3562_40.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_41.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_42.png)

There is no replication of the database okay this has simplified the way you have to deal with consistency of data okay but with one caveat which is if your application is very intensive it is IO intensive the database here will become a bottle line。

Because you have only one of those you have replicated the other tiers but to reduce the problems of trying to maintain consistency you said you will only have one database okay so that's a pretty common approach that' is used for writing your web application where you don't deal with a lot of the database issues you just keep one big database you put it on a big machine and then but everything else is replicated this reduces the need to maintain consistency which is something that you will see in lab3 because you are going to replicate some of your tiers in your application and try to maintain consistency okay this gets around us but you can still have backend as your bottom。

Is that clear so there is one way to build a web cluster， but now lets dig a little bit more into。



![](img/699358d61cf6aa9f62d53ad318ea3562_44.png)

How the application itself， the end application or the browser interacts with all this component。



![](img/699358d61cf6aa9f62d53ad318ea3562_46.png)

那个嗯。So here is an example where you have the client component shown on the left and there are all these other components that are shown that are essentially part of the server。

 this is not even a multi tiered component is just showing a single frontend which is the switch here with multiple web servers but you will see that there's a lot of things that have to happen to make this seamless from an applications perspective in particular this is going to show you a slightly different way of processing request than what I showed you on the previous slide and it'll go back and compare them So in this case what will happen is this is your browser the client is going to send a request to the front end which is called a switch here so the switch or the front end will have URL and IP address that's what is advertised to the external world so your browser is going to connect to the switch the switch is going to then have to send it to one of the replica there are two shown here the switch actually sends it here to the。



![](img/699358d61cf6aa9f62d53ad318ea3562_48.png)

One at the bottom as you will see the request comes here。

 this web server actually talks to a dispatcher and say there is a new request which replica should process it in this case the dispatcher actually says send it to the other server。

so you will see now that request has been forwarded to that web server。

 that web server will then process that request and you will see the responses directly going from this web server back to the client。

In this example， if you look at the previous example。😊。



![](img/699358d61cf6aa9f62d53ad318ea3562_50.png)

You will see that requests are coming to the front end the front end is sending them to one of the replicas。

 the replicas sends the response to the front end and then the front end sends the response。



![](img/699358d61cf6aa9f62d53ad318ea3562_52.png)

Okay， so。So there' is one scenario where all the requests and responses are coming from the front end there's another scenario which is shown on this slide where the response directly goes back from the web server to the client okay so the question is why would we do this as opposed to the simpler approach where all the interactions or the browser are actually going through a single point which is the frontend node of the application。



![](img/699358d61cf6aa9f62d53ad318ea3562_54.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_55.png)

Is the question clear or what what we are talking about？Yes。

Okay so one point at being made is if the session is persistent you can go through the switch if it is non-persistent or stateless you can go to go directly back from the server to the client okay that is indeed true but here is another thing that you can think about right so so let's say this think about this client it is a web browser。

Web browser sent an STTP request to this node， this IP address。

And then the response came from some other machine that you didn't even contact。嗯。

So now should the web browser take this response because you signed a request to some website。

 some other server sent you a response， Why would you even want to take that response because you don't know where this response came from so if you implement something like this there are some certainties you to deal first question is why bother why it should this web server send a response to the switch and switch should send it back that's the first question you should ask this is what is shown here everything is flowing through this node a frontend node the reason you don't want to do this necessarily is the frontend node can become a bottleneck because every all the traffic is flowing incoming traffic is going through here and the outgoing traffic is also going through that node So that note could potentially be a bottleneck。



![](img/699358d61cf6aa9f62d53ad318ea3562_57.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_58.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_59.png)

对。Because its all of this this is a very large website think about lots of these replicas this node can easily become a bottleneck so the less work it has to do the less the less there are the chances it will become a bottlene so if you at least take the responses out of the front node and send them back directly maybe theres less work for the switch to that's one reason why in this case the response went directly from the web server or to the client。

so that's now having said that you we should say but here is a different machine that is sending that request back to the client is that a good thing from a browser's perspective the first thing is that browser will not actually accept a response that came from a machine that it did not contact right because that' is not our browser's at design you make a request are expecting to get a response back on that same from that same machine so so this。

😊。

![](img/699358d61cf6aa9f62d53ad318ea3562_61.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_62.png)

If you dont do some extra work will not even work from a browsers perspective so what this web server will do is when it sends back a response。

 it will actually in the TCP packet it will replace its IP address with the IP address of the switch。

So that when the response is received at the client。

 the client will think the response came from the switch。😊。

Because if you think about how does the browser know where the response came from all the packets are coming with the source address which is the address or the sender okay so when a packet comes you will see what the sender is and then you know where it came from the sender is the same machine that you contacted you will not actually know at a browser that the response came from the website。

Wwhich is different than the switch because the switch is at the the web server is masquerading the IP address or the switch for this to work。

 otherwise the browser will reject the response it will not even accept。😊，Yes， question。

To have the switch set up。Yeah。Yeah， the question is。

 can you set up a persistent connection that will avoid all of this right that's a push so we can。



![](img/699358d61cf6aa9f62d53ad318ea3562_64.png)

Indeed do that in fact I want to mention three different ways by which you can implement what I've been talking about one is called STTP redirect the second is called TCP slicing the third is called TCP handoff these are three different approaches that allow you to essentially have the switch send the request off to some other node and the response will come directly from that okay so the first thing you could do is STTP request comes to the switch okay the switch can ask the dispatcher who is the server to server if that's the server or you do what is called an STTP redirect which means you forward that hTP request to another node and then that node sends back an STTP response when you do an STTP redirect the client is told that the request has actually been redirected to a different that's the simplest way you can achieve this which is and the STDps is official way of forwarding request to another node is called a redirect so you just forward that。



![](img/699358d61cf6aa9f62d53ad318ea3562_66.png)

So and the client will then expect the response to come back from some other node that's one way to do it second way to do it is called TCP handoff this redirection is this is also a form of redirection。

 but it's a way to do it at the TCP layer not at the STTP layer which is what was happening here you will see that it says handoff TCP connection when you do a TCP redirect the machine that has received it when it sends back a response needs to actually pretend like it's the original machine that did the redirect otherwise the client will get confused it set up a socket connection to machine A responses to anything you send on the socket is coming from machine B that does not work So you want when you do TCP redirect you are essentially going to have to do what is called。



![](img/699358d61cf6aa9f62d53ad318ea3562_68.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_69.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_70.png)

masquerading of IP addresses so that the response it looks like they're coming from the right machine that's the second approach and let me now talk about a third approach this is called tCP splicing what tCP splicing means is essentially you have an intermediary which is the switch for us the client sets up a tCP connection with the switch the switch sets up a tCP connection with a backend server and these two connection are spliced everything that's coming on the tCP connection is then simply copied onto the second connection so you are just copying things back and forth so that two TCP connection is' like you're pasting them together so it looks like data is directly flowing from the sender to the server that was actually serving the request so in this case for example your you will have a tCP connection from here to the switch the switch would have to then set up another tCP connection to that web server everything that comes。



![](img/699358d61cf6aa9f62d53ad318ea3562_72.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_73.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_74.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_75.png)

So the switch is then basically simply copied on that TCP connection not processed simply copy it which is like your forwarding data it goes to the web server and the responses are copied by so this is essentially two TCP connection that does just relaying things back and forth so it looks like you have a direct connection from the client to the server。

so these are all ways by which you can essentially implement these frontend switches or load balancing that allow you to essentially have lots of servers behind the switch and you will now see that in some cases the servers are hidden remember this trans replication transparency that I talked about maybe there was even a midterm question on it right so if you do things like。

What is shown here where the you only talk to the front end and front end signs all the data gets the response come this is replication transparent the browser does not know there are multiple machines only sees the front end but if you do any of these other techniques which is redirect splicing or handoff the response is actually coming back from another machine in some case the presence of that machine is hidden because the replica pretends to be the switch pretends to have the IP address the switch and does not reveal it in cases like htP redirect it becomes visible so it these things have different tradeoffs and different overhead to how you go about implementing this cluster of servers。

lots of these are networking details which I don't really expect all of you to understand at a full detail。

 but you should at least understand the basics of what I'm talking about。Yeahep。

Any questions on this？So there are a few other things I want to mention because theres a question about persistent connections。

 which is what I did want to get to， so the switch itself can essentially schedule the request either at a request level or at a session level。

😊，So if you schedule。Your data at a request level what happens is every time a new request comes in a new HDP request comes in。

 the switch can then potentially pick another replica to serve it because if you do least loaded request comes in you pick the least loaded server that request is sent off to that server and then you get a responsible this works well if you have stateless application because any replica can serve any request but if your application is state full you can no longer do this because let's say you are in an e-commerce application you put something into a shopping cart the shopping car of your application is state that is basically you are for your session that state of your session that's what you want to potentially buy so you put something in a shopping cart that the shopping cart is actually maintained at one of the servers specifically it will be maintained at one of the replicas that handle the request where you said put this in my shopping car the next request goes to。

other replica that replica will not have that state of the shopping car because it is stored in memory on some other machine so in this case you want to essentially do session level scheduling where all requests of a session okay maybe the session itself is persistent but regardless of whether it is persistent or not all requests of that session are always sent to the same replica。

So that any state that you kept is now consistent you will not actually miss it the only other way to do it is that you are to put the state on disk okay and if the request goes to another server you are to first load that state back from the disk or the session state is now reconstructed on a new server and then you serve the request but that is going to add over it because now you are essentially keeping state on disk so that is going to add IO latency to your request。

If you want to keep the state in memory， you have to use session level。

 load balancing and session level scheduling for stateless applications and request level is good enough。



![](img/699358d61cf6aa9f62d53ad318ea3562_77.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_78.png)

So lots of details that you have to think about when you build your web application is it stateless is it stateful okay and if it is stateful and how are you going to do the load balancing are you going to keep the state in memory will you keep it on disk and so on。

That year。Any questions here？Okay。

![](img/699358d61cf6aa9f62d53ad318ea3562_80.png)

All right， so the next thing I want to mention when we talk about these clusters is this notion of elastic scaling。

 this is something that you will see large applications implement。

 they are not typically implemented in small application but let me motivate what elastic scaling even means。

So let's say your web application， let's say it's a shopping application。

And you would say you replicated it on four machines。

You assume that there will be some load coming in and you put it on you have four machines serving all your load for normal days maybe four machines are fine okay then maybe you decide that you are going to have a sale for your store maybe it is a black Friday sale maybe you are going to have a memorial day sale you have some sale and you expect that because you are giving good deals to your customers more customers are going to visit your website on that day okay to shop。

Now if there is a lot of interest in the kinds of products you are offering or the prices you are offering a lot of customers are going to visit that site and maybe four machines are not enough all four machines get overloaded and then the site does not respond to users so site is effectively overloaded because the volume of requests that is coming in it cannot be served by the static number of replicas you are deploy。

and then your site stops functioning this often happens you probably have encountered some website that is overloaded and not responding to it essentially the number of requests that are coming in as over the number of servers that are present。

😊，So then you can ask， what can you do in this case？Beside us overload and what do we do。

You can increase the number of servers right so if we say the four servers okay that is the replication factor is four four servers can't handle the load okay lets add more servers。

😊，So you can add more servers and then maybe those larger number of servers will serve your load。

But the question is who is going to add these servers and when is that going to happen Maybe the site administrator is smart enough to realize okay there is a sale coming up or normal four servers is not enough so before the sales start they put maybe four more servers so they double the capacity and then when the sale aid all is good so maybe you are good good that way okay so if you this change of capacity can be done by human administrator where they take proactive measures to decide what the capacity is but maybe they don't know how popular the sale maybe they say let's double the capacity but maybe the sale is so popular you actually need it three times the capacity so then your site might still be overload so it's not often possible to predict what the load will be for events that are popular or maybe it's a news website it is often happens on a news website big news story breaks okay many new sites。

😊。

![](img/699358d61cf6aa9f62d53ad318ea3562_82.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_83.png)

Justク。The bigger the news story， the worse the traffic and they'll just crash sometimes news website gets 10 x 50x traffics 50 times more than normal that's a very large number so they don't they cant anticipate news stories when they break you cannot anticipate typically so they can be unexpected things that happen so you cannot do what you could potentially do if it's a shopping website you could provision this capacity so that brings us back to this notion of elastic scaling which says why should administrator do is why can't we build that functionality into the system the system can monitor the load on the servers and the load is rising and it exceeds the threshold then add more servers because if you don't then the load might rise further and the servers might get saturated so you could simply monitor the incoming load and see the utilization of servers the servers let's say every time the load。

😊。

![](img/699358d61cf6aa9f62d53ad318ea3562_85.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_86.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_87.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_88.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_89.png)

The server goes about 80%。 You said that is too close for comfort。

 maybe now the server will saturate let's add replicas and then if the load goes below low threshold。

 maybe all the servers are sitting at 10% you might have too many replicas let me reduce it not different from dynamic thread pools and the load by top you added more threads to server your incoming request here are actually adding hardware capacity you're adding servers saying I need more server capacity or less server capacity this is called elastic scaling you dynamically vary the capacity of the web application based on the workload so well add more servers that you will make sure the code is deployed on the server you will tell the switch that there one more server or end more server so the switch can then start sending new requests all of that has to happen but it can be automated Okay all large websites actually automated。



![](img/699358d61cf6aa9f62d53ad318ea3562_91.png)

So that is the concept of elastic scaling they actually come in two flavors one is called horizontal scaling the other is called vertical scaling in horizontal scaling you vary the number of replicas you add more servers or you reduce the number of servers so what you are varying okay is the number of servers。

In vertical scaling you change the size of the server so instead of saying I have a two core machine I add a eight core machine so it still has more capacity you didn't add more servers you put a bigger server to replace a lower capacity server that' is called vertical scaling just changing the capacity vertically which means you are adding more capacity or less capacity to the same number of servers in horizontal scaling you change the number of servers with time as the workload okay these are two ways you can do elastic scaling。

Yeah and then there are other ways you can also do this one is called proactive。

 the other is called reactive proactive says you can actually look at the workload。

 maybe you can predict the workload in the future you can use some technique which is forecasting or machine learning techniques that say given this trend what's the next hour going to look like and then you provision the capacity now so that you can actually address the workload increase in the next hour that's called proactive。

Reactiveor says monitor the workload now and the workload rises above some value the threshold add capacity now you are reacting to changes you didnt do it ahead of time you are doing things on the fly as the workload change so you can have both of these techniques as well so you can do horizontal vertical each of these could be proactive yet。

All large websites that you will see will have elastic scaling built in。😊。



![](img/699358d61cf6aa9f62d53ad318ea3562_93.png)

Because they dont want a case where there is a sudden increase in traffic and the just buckles because that's lost if its a shopping website thats lost revenue okay you are turning away customers who could have bought more products you could have made more money right so you don't want your revenue to be lost because you designed your website poorlyly with less capacity than it。

😊，So they will all implement this technique in fact if you actually go and look at cloud documentation anytime youre deploying a web application with cloud platforms actually give you this capability for free you can actually turn on elastic scaling for a web application and then the cloud platform will do this for you so you wont even have to write extra code you can just say this is a web application I'm deploying add elastic scaling and they will have a load balancer and they will actually provision your server for you so you can even not have to do this。

Yourself as a web developer， you can have the cloud platform do it for you。Any questions here， this？

可闭。这个是。电第关。Thank you。我 road。呃。跟你关咯。2。他的他。Okay， what she is。

Are the servers that you are adding to this application are the idL servers that you are just adding？

嗯。But did you borrow them from other customer so it is the farmer if you are a cloud platform let's say Amazon。

 Azure is Microsoft's cloud as Google Cloud they are all very large data center you should probably know this from the data center lecture so these are very large data centers they are provision for some very high capacity so typical utilization of a data center will be somewhere between 20 to 50% which means up to half the machines will be idL because you can have customers come in forget this the cloud service model is customer comes in says I want 10 machines and maybe in order of minutes you give them 10 machines right so when you have this type of environment you better have extra capacity because you might have lots of customers showing up asking for machines so they are over provision so there are always there's a idL server sitting in the cloud and this。



![](img/699358d61cf6aa9f62d53ad318ea3562_95.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_96.png)

cal is simply asking for the servers on the fly and heading them to the you're not going to another customers。

 I am taking a server away nobody is going to like that if you say I'm going to take your server。

 give it to some other customers so that does not work for most part inside enterprise that might be okay so if you are essentially a single enterprise you can take capacity from lower priority applications and give them to higher priority application if you remember when we are talking about cluster scheduling and I mentioned bo。

 which was Google's cluster scheduler， I did mention there that when the interactive load goes up you can take machines from batch batch workloads which are that same training and give them to interact when Google's case if YouTube workload goes up they can borrow capacity from the batch applications and put it towards YouTube so that your users are going to get better customers so but that's a different case that's a single enterprise。

So very large one if you are talking about traditional cloud。

 you will get idle capacity machines and put it for this elastic scale。Any other questions here？Yes。

やぱ的什。Okay， question is， vertical scaling， can we do that when the server is running？

There are many ways to actually do vertical scaling I say gave the simplest case where I said you have a twoco machine and I can put that application on a four core machine now it so happens that you actually may not have to switch servers at all because the way the cloud allocates machines is you have physical server and you are constructing VMs on that physical servers and simply allocateocating VMs so there maybe idle core sitting on that Vm that are unalocd or sorry on the physical machine so rather than moving the application what you could simply do is you can take the unused course on that physical machine and just give it to the Vm so the Vm suddenly has more core or it just looks like it's running on a bigger machine so you can do these kinds of things if you I don't know if the lablet on the Vms ask you to change the number of core on the fly probably didn't but one of the things virtual machine technology allows you to do is you can actually add and remove core。

W Williams。so you can give it more capacity while it' is running you don't have to shut it down so you don't actually need to physically move it onto a bigger machine you could do that too that you can just do live migration which we also studied right so you could live migrate the machine and then it just lands up on a bigger server or you could essentially allocate more core to the VM if there are idle capacity on that server so many different ways to do vertical scale。



![](img/699358d61cf6aa9f62d53ad318ea3562_98.png)

I clear are any other questions here？Okay， so I will talk briefly about microservices。

Wwhich I mentioned before as well you used a simple microservice architecture in your lab right so you probably know now what this means so rather than having a single server for the application tier in a multiter application you break that tier into smaller pieces so each of them is called a microservice so your app tier of your multiter application now has many components okay each component is its own small service。

 they all work together to build a bigger web application that's the idea of a microservices architecture so many web applications may have ends or hundreds or some of them have thousands of microservices deploying that are deployed to implement a bigger application so it can be quite complicated you build one with three I think in the lab so that's a very simple one but most of these will actually a lot more of these microservices that are working together and the idea is you。



![](img/699358d61cf6aa9f62d53ad318ea3562_100.png)

If you build small microservices it gives you modular architecture because each microservice is designed for a very specific task okay thats the task it performs it has a welldefined interface that allows other microservices to interact with it each of them can be deployed independently they can be upgraded independently each of them can be scaled independently you can apply elastic scaling to now microservices you don't have to scale the entire code of the application if one component was bottleneck。



![](img/699358d61cf6aa9f62d53ad318ea3562_102.png)

In the previous case if you had a simple three tier application your vertical scaling applies to the entire application tier but maybe only one part of the application is bottleneck if you are a microservices architecture your code has not split into containers each of them is a different component you can scale each one independently if only two microservices are overload it you can just elastically scale those microservices and leave the rest so it allows you much more fine grain ability to do both clustering and scaling。

So these are some advantages of a microservice architecture。

I'm going to show you a picture that explains how you scale microservices and in some sense also web applications so there are three axises here the X axis。



![](img/699358d61cf6aa9f62d53ad318ea3562_104.png)

Call horizontal duplication， but it's really scaling by cloning which means replication you create multiple replicas which is the web cluster that I showed you so this is basically scaling code y axis is what is called functional decomposition so this is do you take the application you split it into components and you scale it So when you build something using a microservice architecture this is what we did we took a bigger application which is what you are written in your lab one and you split it into pieces so you functionally decompose it into pieces now each of those can be scaled independently so that is essentially functional decomposition that's the y axis x axis just says that you just replicate and then the z axis is what is called data partitioning which says rather than having all your data in the single data one way to scale it up is not to replicate the database but partition the database so what does this mean。

So， let's say you have some number of users okay you could say users one through 00 are assigned to this database all of their database here users 101 to 200 are assigned to this other copy of a database which is running on a separate machine okay so all of their requests go there a third one goes somewhere else and so so that is essentially data partition。

So you can partition data， you can partition code and you can replicate code and data so these are three different ways of scaling your application。

Is that clear what I just said so one way you want to think about data partitioning is let's say using an example that you are all familiar with this let's say web email right so you have Google Ma or you may have these web mail services you can think about a number of users that this service has to support okay on the order of tens or hundreds of millions。

😊，So you' are not going to have one machine serve all of them the way that's going to be provisioned is certain users are mapped to certain replicas so when you log in you are assigned to some group of servers and somebody else logs in based on their name or user ID they may map to some other group of machines and so so you are essentially participating your user internally and mapping them to different machines so that you can scale the system it's not like any Google server that can serve any user your data is kept your mail data in this case is kept on certain number of machines so so internally split you on redirect you will not see this because you are only interacting in the front end but in the back end that's what is actually。

so this is better than replication because if you replicated all the data you are to deal with consistency the partitioning gets away from replication it allows you to scale by you know splitting the data and putting them on different machines and then redirecting requests to different machine。

That is a different way to scale then you replicate all the data。

 keep it consistent and any request can go to any machine。Two different approaches。That clear。Yes。

Yes。Okay， good question question is how is data parting going to deal with server question right？

If you have only one copy of the data you will and if the machine crashes you can't deal with it it's gone so you will need to keep at least one backup copy somewhere in the system or maybe more than one you're doing paxos and so on you have more than one copy but there has to be at least another copy somewhere but it's not full partitioning you can essentially have a backup copy that'sre sitting there and youre just sending all the rights to that copy and when the primary fails the backup takes so that's one approach the other approach of course a machine can go down but maybe you're taking tape backups or something and you'll take you some downtime you'll restore it and then you'll bring it back but that involves downtime and potential data so when you do data partitioning as always with data crashes are hard to deal with。

Because there are only two ways you actually replicate it but light degree of replication right there are two copies of everything but you still have to keep them consistent as opposed to end copies which increases the cost that's one approach the other approaches that you will essentially keep it on tertiary storage on top tape back up and then bring it back online right so these are ways that you have to deal with。

Thank you， any other questions here？Okay， so。

![](img/699358d61cf6aa9f62d53ad318ea3562_106.png)

Let's talk about HTP now the protocol and we look at how STTP works and what are some nuances we got to deal with when we deal with web application The first thing is STDB is a protocol where a request response protocol you make an STTP request and you will get a response and let me show you that there are four or five types of HTP request that you can make the simplest request is a get request you probably dealt with this when you build restful services and so a get request basically asks for a document document comes back a put request is the opposite of get you can send a document a post is also way to send data but typically a post is used when you are filling a web4 where you are sending some information that the user has filled you're sending that to the server as opposed to a full document that you're sending a port allows you to take a file and actually upload it to a server a post just allows you to send some arbitrary。



![](img/699358d61cf6aa9f62d53ad318ea3562_108.png)

Stings of information to a server theyre both sending information from the browser to the server but theyre slightly different from one another delete allows you to delete a document okay typically you will not see any STTB server supporting delete because yout you shouldn't tell the server go delete some files that belong to someone else but where this is actually use this if you are using a browser front end to actually access let's say cloud storage。

Maybe it is Google drive right so if you can your files you can use STtP delete to delete some document from it for example。

But in typical web applications， you will not see delete being supported。

 You will see mostly get and post being supported and head is a special call that returns the header of the document。

 not the document itself， but just a but these are standard STTP method the most common one is a get request this is the web browser will send get a document and get but you to remember that there are other types of STTP request as well that are used in some specific cases but assuming you send a get request the response that is going to come back to you can be of many types you might get an hml file as a response that's a text document you may get an image as a response if you are sending an hTP request to get an image that's embedded in a document you may get a image back you could get an audio file back if you click on an audio data that's embedded in a web page what streaming to use an audio file you can have a video file。



![](img/699358d61cf6aa9f62d53ad318ea3562_110.png)

As well you can essentially download document like PDF and you can click on a PDF link where a PDF and you can have multipart where is actually concatenating different types of information and sending it back in a single request so when a response comes back from the server it has to first indicate in the response what type of information is being sent is it text document and is it a text Xm is it image Jpeg or is it video impact and then you actually send the data and the reason you do this is the browser needs to know how to interpret what is coming back just get some bytes you don't know what it is so you have to actually include the type of information that' is coming back as part of your STTP response。



![](img/699358d61cf6aa9f62d53ad318ea3562_112.png)

So we willll send a request typically when the response comes back it will have a type associated with it and the data or the payload is the actual information that is included that actually has that requested contact。

😊，So that's our standard STTP request response， but now let's look at the protocol itself and try to understand it a little more so STTp has gone through many iteration it started with version1 it was maybe almost 30 years ago then it went to version 1。

1 and it stayed there for a long time and then recently you version 2 of STtp came out theres a version 3 that's been designeds in the past few years there's been a rapid iteration but for a long time the typical STtP versions are either one or 1。

1 well let's try to understand those first theres still widely used and Ill talk about what STtP2 does and what benefits it offers over one so htP1 is also called non-persistent STtP is the simplest way to do STtP which is every time browser wants to set up an STtP connection to the server it will set up a new connection。



![](img/699358d61cf6aa9f62d53ad318ea3562_114.png)

It will send a single STTP request， you will get a response you will shut the connection down you want the browser wants to then send additional requests to the same server。

 it will set up additional connection each is a separate connection each STTP connection will have one request and one response。

That shown in this picture where there's a browser is setting up a connection to a web server thats a shopping site you'll see that there are three connections here so maybe it went and got some information then it puts something into a shopping card then it did something else each is a request that connection that you set up will set up a TCP connection then you send STTP request you get a response close the connection this nonpersistent STTP now as you can imagine every time you set up an STTP connection you have to pay the overhead of setting up a TCP connection and you remember that three TCP handshake that incur some overhead。

So STDP designer said this is expensive if a browser makes multiple connections to the same server。

 why close the connection after the first responses come back lets keep it open so that the browser can send multiple requests on the same connection。



![](img/699358d61cf6aa9f62d53ad318ea3562_116.png)

嗯。😊，So that was the addition they made to STTP and that version of STTP was called 1。

1 so it's also called persistent STTP some of you may have used it in your lab。

So here you set up one connection to the server okay you can send one request get back a response。

 the connection stays open if the browser wants to send another request it can use the same connection is already open just send the STTP request get back a response so you have saved the overhead of setting up a new TCP connection。

And you can do this multiple times you can send multiple requests， get multiple responses。😊。

This is persistent STD now the problem with persistent STtp is that all of these。😊。

The question and response have to be sequential。Okay， so you have to send a request。

 get a response until the response comes， you cannot sign the next request。



![](img/699358d61cf6aa9f62d53ad318ea3562_118.png)

Okay。So this can be a problem because let's say you have a web page and the web page has six images in it。

so you will first make an STDP request guess the STl web page then the browser will look at the web page and say there are six embedded images you have to download them from the server lets say all the content is on the same server。

Now， in this case， you are to fetch them one at a time。😊。

Because you have to get the response before you send the next request so you will get the first image and the second image and the third image by the time you are done the six images some time has passed the user is sitting there waiting for their page to load。

😊，Okay because you are not seeing the images load and is just taking some time now if you are done。

Non-persistent connections you could have after you got the first page set up six connections in parallel ask for all the six images in parallel download them in parallel and then the content gets to you faster assuming you have enough bandwidth a bandwidth is not the problem you can essentially parallelize your connections and load your content in parallel。

Is that here what I said？So， if you set up multiple connections。

 whether they are persistent or not ortho coal， if you set up multiple connection you can load content from the server in parallel if you have a single connection especially in STTP 1。

1 you are going to be doing sequential。😊，A request， you send a request。

 get a respond only then can you send a next request。So for this reason。😊， persistentent STTP。

Its not very useful when you are actually talking to content rich websites because often to load the webage the browser has to make many connections to the server and if you load do use a single persistent connection then you are sequentializing all of your content loading and is going to take a long time your browser would rather prefer to set up multiple connections load things in parallel。

OkaySo so the whole purpose of then creating this persistent connection is lost because anyway to speed up performance now you would rather have multiple connections but the reason we had this is we said we didn't want too very connections so the browsers basically do not use this feature as much okay especially when they are loading a single pay they would rather have multiple connections。

Is that clear what I said but if you are going to make connections apart in time maybe you click on a link you go read that web page after you are done you hit next and then you can still use that connection because that connection sitting there id you can do that but if you are loading a single page where it has n embedded items this is not the best way to do it from a performance standpoint。

So what can we do？Any thoughts on how we can improve this？Okay， so you have a persistent connection。

 you want to somehow make use of it yes。If maybe there's some way to maintain the persistent allow case into。

当时。Okay so you can have persistent connection， you can have asynchronous responses， yes。

 thats a good way to do it you know something great。

Treading okay so explain what you mean by threading here， exactly。大概。不知道会放下。On the same connection。

Okay so you are talking more parallelization than reading but yes so what both of you said is actually the case so lets say your persistent connection the problem with HDDP 1。

1 is it is making everything sequential okay you could say why should that be。

Why can't I assign multiple requests to the server on the same connections and get multiple responses？



![](img/699358d61cf6aa9f62d53ad318ea3562_120.png)

The only problem if you do that is since you are multiple outstanding requests you could have multiple outstanding requests when a response comes back you need to know which response which request is this responsible maybe you send three requests for3 JPG files。

😊，1 Jpeg file has come over the network Okay now you need to know which other requests should give it the give this content so long as you can solve that problem you can use a single connection and essentially have parallel our。

Not parallel but concurrent requests go on that connection and concurrent replies come back so though that is essentially what STTP2 point or did after many years the designers of HtP said this persistent connection not really getting the benefits because browsers prefer to set up multiple connections to speed things up Why not let why not use pipeline pipelinelining means we get rid of sequential connections you can just send as many requests as you want okay the browser server will send responses the responses can also be interleave meaning you can send get one part of image one another part of image2 another part of image one and so on so they don't even the responses don't even have to come sequentially you can actually have take the response chop it up into smaller packets and interleave the packet they all get reconstructed at the other rate so this is going to give you the benefit of。



![](img/699358d61cf6aa9f62d53ad318ea3562_122.png)

Essentially trying to use parallelism， okay that's number one。So， the second thing STDP 2。

0 does is it actually takes the headers which are all text based and makes them binary。

which means that you can send the information in fewer bits so rather than signing ASI headers saying this is text or this is image you can send binary headers you can still do text but you can do binary the third thing you can do is you can compress。

It uses on the flight compression。So that the size of the request response is smaller so rather than sending a long text document why not compress it on the fly send it because it's shorter so you save network over and and decompress it at the other so it uses compression but the most important part is it allows you to multiplex multiple concurrent connection or the same persistent TCP connection and this is done through this notion called streams so you have multiple streams of request and responses that are interleaved on the same TCP connection so you each request and the response is a stream so you can have multiple streams that are sharing the same TCP connection there is no blocking because there is no sequential axis you can essentially do parallel。



![](img/699358d61cf6aa9f62d53ad318ea3562_124.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_125.png)

So that is your STtp 2。 or that try to get over some of the overheads of 1。1 now it says。



![](img/699358d61cf6aa9f62d53ad318ea3562_127.png)

Getting more common still STtp 1。1 is the more common case， but STtp 2。0 is being pushed heavily by。



![](img/699358d61cf6aa9f62d53ad318ea3562_129.png)

Companies that use lots of web services so Google and others actually came up with this and have been pushing STtP2 a lot and STtP3 or later versions actually do away with the need for having TCP as the underlying protocol you can run STtP or other types of protocol as one called quick which is a UDP protocol so you don't have the threeway handshake you can do other things with it so you can essentially run STTP or other types of protocol that's something that they're trying as well so browsers like Chrome are actually at the front of supporting these types of technology So if you use Chrome and you access any Google services very likely it's using STTP2 or a later version but if you are talking other servers maybe you are defaulting to 1。

1 if it doesn't provided support for 2。2。Is that clear any questions here？はい、よこしです。喂。我现在拿。本跑。他的。

Okay question is is quick for a worldwide web or its a smaller area we will get to quick in our latest class when I get to maybe streaming so let me give you a little bit of histories since you asked that question so quick was a protocol that was designed for streaming。



![](img/699358d61cf6aa9f62d53ad318ea3562_131.png)

So essentially YouTube and other services that were doing a lot of video streaming wanted more efficient ways of streaming and TCP has built in retransmission which sometimes is not useful so they essentially came up with their own protocol that ran over UDP which was called quick then so that was the origin of it then they said this is a good protocol maybe we can run other things on it and they are using it for other protocols as well not just streaming but it is designed to run over the internet if that was your main question it not designed for something smaller like a data center and so on because data centers can run their own variants or TCP that will not work on internet this is designed to run over the internet but both the server and the client need to support。



![](img/699358d61cf6aa9f62d53ad318ea3562_133.png)

By default， TCP and UDP are still the most common protocols。

 but there are new ones like quick that are emerging at lots of services support。Okay。

 but I' will get back to that in a later class。

![](img/699358d61cf6aa9f62d53ad318ea3562_135.png)

So I'm going to talk quickly about web services and then we will end it here so web services are a way you can design your web application okay where the client and the server part of the application are just two application components that are interacting with one another okay the typical web world a client as a browser okay there is a user that is using the browser and the other end is a server that's an program but think of a scenario where the client is one application the server is another application and they are just interacting with one another okay maybe using an RPC type interaction so if you build application that way and using web like technique you get web services。

The web services essentially doesn't mean it is just a service。

 it means something specific which is this is a web application that is built in a certain way where you are client and a server that are talking to one another using web technology and the way they interact is actually RPC like communication。

And we'll talk about that in just a moment box but you will see that here there's a client there's a stub okay and there's a communication subsystem。

 there's a server， that's a stub that looks really like an RpC system。

 only difference here is the protocol that using to talk to one another is called So that's a web services protocol So stands for simple object access protocol and I'll show you an example on the next slide so you're not using TCP to send data back and forth you're using higher level techniques called soap when we get to restful web services in two slides you'll see this protocol is htP not soap so you're layering RpCs or httP that is what restful web services but let's start with web services first so here is an example of a soap request don't need to understand all of this all it' showing you is it's an XMl request。

😊。

![](img/699358d61cf6aa9f62d53ad318ea3562_137.png)

The entire request is essentially XL text that is send it has all kinds of headers and it has information。

 this entire request， the only thing you really need to know are these two lines where it is sending an alert it's sending a message saying pick up somebody at 2 pm it sending an alert to a user so this request this is like think of it as an RPC request is going to the web application so this is the argument that that's the function you're calling is an alert function this is a string you're passing to it so the other end will essentially send an alert to some other user and send that message to that user that's what is actually going on here but that's not really relevant from our higherleve discussion higher discussion is web services use XL。



![](img/699358d61cf6aa9f62d53ad318ea3562_139.png)

And you will see that there is a lot of baggage you are to have to deal with just to send one request with a string which's all this extra information as to go so there's another way to say web services or a heavyweight protocol there's a lot of extra information that goes back and forth to make all of this work here's another example so let me talk about restful web services and then I'll show you another example so because web services had a good idea which was let's use web technologies to allow applications to interact with one another but they were heavyweight they never really took off so many years later some web designer said why not change that soap protocol with HtTP the basic idea is good we want components to talk to one another。



![](img/699358d61cf6aa9f62d53ad318ea3562_141.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_142.png)

StTDP is a widely used protocol， so let's use STDP for applications to communicate with one another。

And then lets send RPC like request over STTP that gets you to restful web services so it was a much lighter weight protocol for achieving essentially the same thing again I already have explained this long time back rest stands for representational state transfer is just a way to think about how do I exchange information between two application components using STTP as my protocol as opposed to standard RRPC which runs over TCP right so use RA Java RMI you may have used socket communication you may have used GRPC they all run overTCP。

😊。

![](img/699358d61cf6aa9f62d53ad318ea3562_144.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_145.png)

When you write restful web services effectively you are implementing RPpC like functionality。

 but it runs or STTP is was easier to understand and envision right so you will use it。😊。

Get requests to make requests if you want to make updates， send updates。

 you can use post and requests， you can also support delete。

 but many of them don't so you can use our standard STtP request types to implement RpC communication So that's really what web services do and here is an example So this example is a service is sending you stock information So you are going to basically say get stock price and here the company name is IBM so that's your URL So essentially the argument is embedded in the So this is the call you're making there's the argument there and then you're sending some extra header information you send that off to this other application component。

 It processes that sends back a reply and here is your reply so you will get an STTP response the response here is a small Xml it could be JO doesn't have to be Xml but so you're getting back IBM stock price as some value。

Okay so you are using STDP to communicate back and forth now we have RP PCC running or STDP so everything is implemented as web services this is how things are and you did this in your lab as you probably remember that is what your lab asked you to do you are using。

Rest interfaces to talk between the application clients and the front end or even the front end and the back end component。

 so those are essentially have one way to think about deals you are making RPC calls between application components they were all layered on top of Ht。

Here is the corresponding soap call if you had implemented the same stock ticker application you would send this long Xml request okay and you would get another long Xm reply and then that would run over soap soap itself can be layered over many other protocol so so there is a lot of extra overhead performance tend to be much slower STTp is much easier highly optimized for。

For communication or the internet and so on so it actually gets the job done much more efficient。

so I'm going to show you one more slide and then we willll end here this slide is comparing So and htTP okay so this column is what So does that other column second column is what restful interver services do so you will see。



![](img/699358d61cf6aa9f62d53ad318ea3562_147.png)

That S is designed to be language agnostic which means you can write So applications in many languages。

 platform agnostic， which means it will run on many operating system and it transport agnostic。

 which means it doesn't even read to run on TCPIP it is designed to run on UDP and other protocol。

Because restful web services run on STTP， you cannot be transport diagnostic your transport is set it STTP。

 STT B or TB， you cannot change that， but your services can be written in any language。



![](img/699358d61cf6aa9f62d53ad318ea3562_149.png)

So is language agnostic and they can run on any O as they can run on Windows they not so you still look at platform agnostic so so you are getting most of the benefits that gave up transport flexibility this is designed to have arbitrary distributed application where your M components that all interact in arbitrary ways so you can write arbitrary distributed applications here。

 this is client server。

![](img/699358d61cf6aa9f62d53ad318ea3562_151.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_152.png)

![](img/699358d61cf6aa9f62d53ad318ea3562_153.png)

Two components interacting with one another。 you make a call。 you get a response。

 So I think then you've got you can that component can make other calls and so on this point of point。

 this uses all kinds of standards。 There is a web service definition language there's a web services compiler just as you have RC G and all these Java Rmi compiler so you similar techniques here here there are no tools right you can write web application in whatever tools you want and no standard but there are many tools I shouldn't say there are no tools there are no standard tools you can use your own tools write your web application there is error handling here is extensible heavyweight this so long as you know how to write web application is much simpler right to the HttP transport layer much more efficient So those are the pros and cons it's really。

Not very much use of soap anymore is good to know that they existed or practically every web service that is using this type of concepts uses restful interfaces。

Okay， any questions here we'll stop here next time we'll talk about web caching and think about how can we use caching and proxy servers in interesting ways。



![](img/699358d61cf6aa9f62d53ad318ea3562_155.png)