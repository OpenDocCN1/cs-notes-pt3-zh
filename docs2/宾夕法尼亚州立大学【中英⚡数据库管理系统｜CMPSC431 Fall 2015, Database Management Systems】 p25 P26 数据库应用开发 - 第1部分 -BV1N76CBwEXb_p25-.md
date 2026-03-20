# 宾夕法尼亚州立大学【中英⚡数据库管理系统｜CMPSC431 Fall 2015, Database Management Systems】 p25 P26 数据库应用开发 - 第1部分 -BV1N76CBwEXb_p25-

Good morning， guys。How's the project going？Are you guys ready for your demo number one？Okay。

 let's good。All right， so today we are actually going to talk about something kind of related to De。

😊，And I didn't put this before your first demo because I want you to figure out what technology you want to use。

 but in this chapter which is chapter 6 we are actually gonna talk about just specifically JDVC and when C worked which I just assumed you know I make the project in C so we will still talk about this chapter I was debating whether to talk about it before because now I feel like this textbook is relatively old and nanotechnology or a lot of packages you guys are using now is really different from this however。

 I think a lot of big picture ideas still are the same so we can still take a look at this and you can see what you have to take care of when you're working on。

So in Cha 6， Cha6， we call the database application development， we will talk about how we connect。

 basically what we' are doing on1， connect the front end。With developing an application。So yeah。

 we will go back from No SQL back to SQL again， okay No SQL。

 that was all the three lectures that was all。😊，So for this chapter。

These are the things we will look at， and the first part will be SQL in application code。

So I'm sure you guys are all really familiar with SQL right now。

 so we are just basically showing you what it looks like when we put it in an application。

 so so far we are only doing SQL in terminals。But I'm sure you guys already started to interact it with your front end。

So in this chapter we'll talk about it and there are different ways that we can put SQL in action with our application。

 so one part will be called embedded SQL， which we directly put。The SQL in the host language。

 which we will talk about later， so it allows us to access data using state static SQL questions。

That would be for em part。And we'll also talk about we spend some time on the concept of cursors。

 which actually we're mentioneding No SQL， but we did't mention it in SQL。

 so far we haven't learned about cursor in SQL， but this will come in handy when we develop applications。

Then we will talk about dynamic equal， so dynamic SQL。

 basically means we can create the queries at the run time。

 which I'm sure you guys will be using a lot because your application， your project will not just be。

 okay I designed these queries and all the values already fixed there So I have come up with all the scenarios It must be。

You need to take the user input or it depends on the timet at the current time。Okay。

 so that's for the dynamic equalL plot。And then we will also talk about JDBC。

 which I think last time when we were doing the project phase one presentation。

 something teams mention well be using JDBC， so we will talk about what's the architecture of GDPDPC and what actually works。

 what it is。Then later on， we'll get aQL J and store procedures。

 but that's kind of later caught in this。So let's get started in SQL in application code so today everything' is kind of laid back okay we are not going to solve any problem。

 everything's just kind of I'll talk through and you guys think about why it makes sense why it's designed that way Okay so this chapter is a lot more relax compared to the audience one okay。

 no more coding in this one。So。SQL in application code SQL comments can be called from within a host language program such as C++ Java or Python。

 so that's what you will be using to design your overall system。

 the language you use other than SQL or if you want to them use SQL。So back then in the textbook。

 they only talk about C and Java。Yeah， I think had out。

And I've seen a lot of you have already using Python to do your project。

So SQL statements can refer to host variables， which means that we can have variables in our host language program that we actually want the SQ later to take it to use okay so this includes special variables used to return status so later on we will see whenever we have some errors from SQL we can also catch it。

And they must include the statement to connect to the right database。

 so sure you guys already know that in your program when you design for demo one。

 you will need to somehow establish the connection between your application and the database okay。

So there are two main approaches that we can put our SQL with our application together。

 so the first will be embedSQL in the host language。

 okay so this will be the approach we when you commonly say it's embeded SQL。So。I think you guys。

 I'm not sure which one you guys use， but for embedded seafood。

 it's basically saying need directly half to Coke。That exactly looks like what we do in SQL。

 when we learn about SQL and chapterify， you exactly put it into。What is your whole language program？

Okay，Then another approach will actually be creating special application program interface。

 so which is the API we talk about all the time。So instead of directly putting the SQL code embedded into our host languagegu program。

 we use API。If one knows what API is。Yeah。Okay。So。What is。All right， so。

When you think about coding in SQL and then having your application actually coded in other language。

 a lot of times one of the biggest problems that will occur is they actually be handling different data types while SQL returns is not guarantee the language you use would definitely catch it right Sometimes they have different understanding of data types So we call this the impetus mismatch。

And one of the scenarios you can think of is a lot of times the sQL returns multi sets of records。

We send multi setss because a lot of times in the commercial MySQL actually allows duplicate。

 but that's what the multis mean is removing multi that means no duplicate sets so quite often they will return the multis of records and in your host language that will not be supported a lot of times they cannot understand directly sending in table so this is actually where cursor comes handy。

 so SQL supports cursor。To handle the mismatch between secret and programming language。

Because the biggest difference between equalQ is all of the answer it returns。Is table and rows。

Don' answers。So sometimes you might want to cursor to help your host language to iterate through what rows you're talking about。

Okay， so we will get into a bit more in what cur it means later。

So let's discuss the two approaches separately okay the two approaches are the embedded SQL。

 which we directly put in the SQL code in our host language program and the second approach will be creating API so let's start from embedded SQL。

So embedded sQL。Really intuitively we will just put SQL in the whole neighborhood program so what happens when we do that is actually like this。

 so our preprocessor will convert the SQL statements into special API code okay so you don't really need to look into any APIs。

 you just directly put the SQL code embeddedbed it into your program doesn't matter how you do it in C it will show you how it looks like later and if you do it in Python as things sometimes you can just directly send it in as a string which write into query and sending the SQL command as a string。

Then a regular compiler is used to compile the code。 So throughout this chapter。

 whenever we talk about example， even though it is a quite old practice。

 but the example will be illustrated in the scene， but I think the big picture still share the common thing。

So you can take a look at here， a couple of things that we might want to do when we do inbedsQL。

 maybe in C the example here in C will be maybe we want to connect to a database so you will say execute SQL connect or you want to declare variables then you will need to give it a section where you put variables so you will start by saying execute SQL between declare section and then execute SQL and declare section or you might have some statements which are like the queries we do a lot of times then in chapter5 okay so that will be put here。

So， let's take a look at。An example。For example， right now。

 if we want to declare some variables first。Then in the see program， you can do this。

You just start by saying， okay， here are the variables I want to declare。

 and I just put them in and following the normal way that you would declare variables。

 nothing fantasy。later on， I will show you how the whole thing will look like。か可。C program。

So the bottom two are just something。Hard to say something special about using C and communicating with SQL。

 but actually all of the other programs will have this as well。

 it's just basically taking care of errors。So normally the way SQL can communicate with the host language will be maybe sending back a value。

 like that's like a state okay or an error error， so you can understand what it means by looking at the documents just different different host language will have different kinds of。

Variables taken care of。So remember earlier we were talking about the mismatch between SQL and C。

 so a lot of times SQL returned the answer as tables。

 then actually C or other language might not be able to directly take in the input as table so that's why we will need cursor。

So what cursor means is that we can declare cursor on a relation which is a relation to tables。

Or a query state that generates relation。 So then the recursor takes care of iterating through the answer。

 So a cursor allows us to retrieve the row in the table by positioning acursor to a particular row and reading its content。

 Okay， so you might have a query that says a specify some criteria that leads you a cursor to a certain row of。

The table， then the cursor would be the one blinking there。

 and then see or other whole language knows which data youre actually talking。

So what happens whenever we use a cursor is actually that we will first open a cursor。

 which I'll show you later and repeatedly fetch the topple， okay。

 so you have a lot of rows you actually need to use。

 then repeatedly fetch it and move the cursor untilples all the topples you want have been reached。

Okay， so this is just a very simple idea of why we will want to use the persona。

I'm pretty sure in other host language you guys use are also using cur。Have you guys looked into it？

Like when you split。Who has done to like you can put a query？And then get。Result back。

So what did you guys do？可。PHP did it involve anycosa or just directly diss at all？

Just we out the data and the we program。I converted to James。And a PhV renders the Jason。All right。

 that's another approach then。 so let's take a look at what we were do forcoive。So cursor。

 the cursor can move to particular rows by specifying additional parameters for the fetch comment。

 which we will show later as well， so in C， okay still imagining if we are interacting with C between C and CQL so using fetch you can actually fetch the values that's returned from SQL and then store it into the variables in your program which I think you guys will do a lot as well。

So the query is access through a cursor and can control the order of top loads returned by using order back。

Also， I think some of the teamses are already displaying the result in tables。

 So maybe you will have the function of。Soing the tables in some sense， right。

 given the criteria saying I want to sort this by the product price。 I want to sort this by。

How many days left for it clip。So we can also use order button。嗯。

So here are just a couple of things that order bikeke clause。

We know that the variable you want to order by must be included in the select as well。Intuitive。

And also。Yeah， nothing fantasy here。Yeah， you can order the answer in the post language。

So here will be one of the example for ordering。Wwhich we are all really familiar with so let's say we want to get let's say in our database。

 we again to store the sailors both in reserve back to what we are familiar with and let's say today we want to get the names of sellers who have reserved a retina。

In in alphabetic order。 So inside here。It's all what we learned before， right。

 for the Sequ statements。And putting that execute SQL declare S in cursor for。

 it's actually showing we embed this whole thing in our host language program。

 So right here we actually declare this whole chunk to say what this return would be put in a cursor okay so that's how we use the cursor and then we order it by to S name。

And just a really little note note that because we didn't select maybe say SID。

 then we should not order it by SD because it's not returning the coast So when doing the order by just make sure you have it。

You order by the thing that you have selected。So。A little bit more on closer。So here I ask。

 we usually need cursor for select and do not need it for insert the link update。Yeah。

 just select you're going to do it like a lot of times with the same data， but the insert cognitive。

你个月。没有。嗯。So for the cursor， it's also serving for the host language to know what data it gets back。

So yeah， so William， what were you going to say， I was just select' giving you data back for。Yeah。

 exactly， so that's the end so because they do not return tus back to the program。Okay。

But there will be other things。Some special case will we actually need that because for others。

For other actions。 But in general， we only need it for select。

Because select is the one returning topics。So here will be an example。

Of the embedding sequenceequency。Let's talk about what actually happens here。

 so you can also map it into your own post language that you use。For example， at the very top。

 you see we declare a variable， which is SQL state， which is the one we said earlier。

 it will be able to be the one storing whatever state the SQL part returns。Okay。

 then here we start by。Sa here。We start by saying we want to execute SQL begin declare section。

 so for these three lines， here's the part we were declaring the barrier。AndCan like be said earlier。

So in this chapter， I won't ask you to remember the comments because everyone has their different ways of using their own post language as long as you know the big picture。

在な。So here we start by declaring this section， declare a section。

 and then we put the variables we we'll later want to use， and we've finished declaring。

And then later。Right here， we actually give a C min rating。

Which we just randomize whatever number there is and then right here。Which we will use later。

And then right here we start a whole chunk。Right here that's for the cursor and what happens in the cursor is here we do select from where as we are really familiar with right in SQL。

AndYou can see here we have we want to select the seller name and age from the seller table where the seller rating is greater than the theing rating。

 and here you can see we have a column you C that's because we are specifying this variable comes from the whole language program So if you just execute it alone。

 then it will actually not work in SQL Okay so this is just specifying this comes from there。系。

And in this program， what it's actually doing is just to keep fetching information so you can see from here。

We keep fetching that information， and put them。Again。

 there we have column put them into the C S name and C H that we declare earlier。Alright。

 and using the fetch， because then this will match， map。To here in the A format map。Okay。

 we just keep fetching in and then simply print it out。 Okay so this is what the program is doing。

 They simply print out the name and edge。 we fetch and each row。Okay。When will we stop， So here。

Different。Stay code means different things。 So if you have state code right here。

It just basically means we have more we have more road to fetch。

 okay so we do as long as the sQL state is still like that and then we stop when the sQL state changes means we don't have any rows left anymore。

so that's what the whole cursor here。Is doing。Okay， so here I said this。Yeah。

 that's for storing the values returned。Sequel。To the host language and then。The whole thing。

 just a whole check of。We use the cursor to go through all the qualified topicss。

So nothing fancy about this program， but then you can see how it's actually working when we have SQL and your host's language program communicate。

Starting out， by decing whatever variables we will need， and then we start this chunk。

And we embed the SQL command in there and you can refer to the variables you actually declare in the host program interact with your SQL part。

 and you can also fetch back the values returned by the SQL part。So for this kind of approach。

 when you can directly see your SQL commands in the program， then we call it the Invent SQL。

So remember earlier we were talking about like right here， even until here for the C min rating。

 it's generated right here， so it's not really dynamic。

 but a lot of times in our application we will actually need whatever criteria or values that we will be using have to be dynamic because maybe it will be a user input。

or maybe it'll be the current。So that's what we call a dynamic sQL。So for dynamicyna SQL。

 what we are basically saying is that SQL query strings are not always known on compile time。

 this allows construction of SQL stain to be on。So what do we mean by that？Here will be an example。

So。Let's say we want to do dynamic sequel and use scenario。You started out saying。

We store some sQL strings into the variables， okay？And right here we will prepare it。

 and then from the SQL screen。And then execute it when you're ready。 Okay。

 so you can actually store different kind of sQL strings， and they will change it。Okay。

 you store it as string just。Just character array， and then they might change。

 You will be able to modify them throughout the program based on different condition。

 different needs that you want。And you first prepare it， but you don't execute it。

 So you only execute it whenever you feel like it fits what you want at the moment。Okay。

 so this this can be dynamic。 you don't have to directly embed it first。 You can prepare it。

So the string can change it out based on your need。

So as you can see because we first store the SQL in a string first。

 so the SQL command is actually prepared at run time right。

 you only run it you can only know what it is when you're running it so this sometimes will incur some runtime overhead let's say your design is very complicated。

 your criteria set for the SQL string is really complicated and that may cause some round time overhead。

就 so far。What we have learned about is the first approach。Of interacting， let's say。

 the front and back。Okay， so that's the embedded sQL。But。Actually。

 there are some drawbacks for embedded SQL， so that's why we need the second。

So here we see there's a problem withSQL， so even though the source code can be compiled and work with different database management system。

 the final executecutsable usually only work with one。

All we mean by that is maybe your program you wanted to be able to interact with multiple database management of system。

So if you write it that way， when you embed it。It can only work with one， for example。

 maybe your program you wanted not only be able to work to communicate with a MySQL database。

 but also an article or Microsoft different kinds， even though they're all SQL。

 but maybe you want them to interact with different types。

 different versions so if we do it in the embedded way as you saw we have just hardcoded what we want to do in the host program so if you change it up to different kind of database in a database management system that we will not be able to use it so for embedding SQL。

 this kind of approach we call it very database dependent。

Because our queries write what we write in for the queries。Are all depending on what database we use。

So we can say even though this is sort of independent at the source code level。

We just embed the SQL comment。 we don't care what outside the language is using。

 right If we're embedding， then doesn't matter we embed in Java doesn't matter we embed in C or embeddedbed in Python。

 What's embedded in there looks the same。 So it's independent on the source code level。

 But once it's compiled， it's not independent at the level execution level。So。

An alternative for embedding would be this。Rather than modifying。In compilepir。

 we can introduce one more layer of abstraction between application and database management system。

So we will spend some time talking about this today。

The first thing we can do will be to add drivers with database calls。So the drivers。

The one taking care of communicating with the driver would be the API。

Okay so that's the application program interface what we' were talking about。

So when using this approach， we have more standardizing interface。

Okay so because there's one more packaging in between for you。

 so you have more standardized way of communicating and whatever the other side it is interacting with。

 you don't have to care。So that's what the API is for。

 so we can pass the SQL strings from language present result sets in a language friendly。So。

 here are two。More famous example， so one will be ODPC， which stands for open Data connectivity。

And another one， which I think you guys are using， which is the JDE。Which teams are using JTs？能。Okay。

 I just remember in the in the project， you guys Oh you changed it up。😊，그 할。

So why was the reason originally we intendedtimated our entire backend in Java。

 so we couldn't get the server working rather than just。In based stuff and job just was。I see。

If have your knee today， okay。😊，Anyways， still a lot of people use JDVC so okay。

 so these are just the two examples， okay， for the alternative of embedded。😊。

SequSo because the API will already take care of。Communicating between what you write and what the database is。

 Okay， so we say this API approach is database independent。Just come care too。

Directly embedded this SQL language。All right。For this approach。

 let's take a look at how it actually works。Yeah， I covered out very much so an application。

Interactiveactible with the data test source。Okay， so the API stands between the application and the data source okay。

 so the first thing we want to do is to select the data source Okay I want to quickly talk about what data source actually means。

So when you first see data source， it seems more like where data is from like a data set。

But actually here the data source stands data source stands for what database you are using that's it okay because like we said earlier。

 you might be able to have your application run at different kinds of databases okay so just do not confuse between the two ways so here when we say to select a data source to say which database。

You want the application to interact。So after you're sure about what data source you want to use。

 then。A driver， corresponding driver， will be dynamically local。那都是。

So this is the part that's helping you out， because。呃。

You can just write your program in one way in different kinds of drivers will take care of。

Translating what you write to suit different kind of database so you don't have to care。

Then after the driver is selected， a connection will be established with the data source。

So this is what I want you guys to do this time， right。

 to have the connection established as long as you can have the front end interact with the back。

Then really easy， your SQL statement that the right would be translated and executed。Then eventually。

 we just return the query result。So just a couple of notes right here。

 keep in mind that there is no limit on the number of open。Ideally， so you can open as many。

Number of connections you want， and this will also mean an application can have several open connections to different data sources。

So remember last time when we were talking this will be a bit away from SQL but last time we were talking about NoSQL and I think I remember someone was asking whether we can actually mix different kind of databases so then I said all you remember in Twitter when we talk about Twitter they actually both use NoSQL and SQL okay so they combine it together that's because your application can have multiple connections。

With different kind of database， which is kind of intuitive as well， right， you open a program。

 you can open different port to connect with different databases。So by having this。

 this allows you to have the ability of mixing different databases， different data sources。

 in some sense， for your advocate。So。Later in this chapter。

 what we will be focusing on will be JDBC okay so we'll just use JDBC as an example for you to understand how this API approach works。

 so JDB is not the only one and now there are so much more than that。

 but we can just understand it from JDBC starting from JDBC so we will talk about what's the architecture okay。

And then you can map this in some more modern。They actually have the same concept that they are just dealing with different kind of databases or different kind of front end。

Technology。So the JDBC architecture actually has four partss。

The first part we say just the application。So when we talk about the JDBC for whole thing。

 okay your actual location is in there as well。So for the application part。

It takes care of establishing connections to the data source， which is。

It takes of initiating and terminating the connections。Okay。

 which is really simple in your application you definitely have one part saying here is where I want to connect to the database。

And it was set transaction boundaries and it will also taking care of submitting the SQL statements。

 so whatever you do in the front end， you will have a way of converting it into the SQL statement you want right maybe you want to select the users or you want to just select all of the products or select product with certain categories and these will be the SQL command you want to send in and all the components will take care of all the other work。

And application also have to receive the results。And they displayed it。

So the second part will be driver manager。 remember later on we will talk about driver driver is one of the biggest part for an API approach。

So for driver manager。It is the one loading the JDBC drug。

 so we have different kinds of drivers that we will want to use depends on your data sources。

 so driverver manage the one helping you out to pick the drug so you don't have to care about it。

So it doesn't matter what the driver is， the way you communicate with EI it's the same。

 okay we make the same cost， but JDBC picks different drivers for you， so that saves a lot of effort。

And driver managers will also pass and log the JDPC function code to the correct。

So because we have driver manager， of course， we're going to have drivers。

So we will get into a bit more really quickly about the drivers。

What the drivers are actually doing is to establish the connections to the data sources and it will transmit requests and returned results and error codes error codes are the one we saw earlier in the example。

 what state it is in。So that's what the drivers would do so imagine in different kinds of databases earlier if we don't have API。

 maybe every different database have every different kinds of error code for the same error but now driver it will convert it for you so your program you can just look up in one uniform document seeing okay when it's maybe400 it's one meaning or some other code is one meaning。

So you don't have to worry about what database。A talking about。

And then we translate the results in error codes from a data source native form into JDVC stand。

Then the very last component the JBC also included to be the data source。

So the whole JPBC wraps up the whole thing。So the data source just。

Think of it as the database that we use。So it processes commands from the driver。

And return to results。So we kept talking about drive the driver。

So we can actually take a look into what drivers are。Okay。

 what driver is supposed and then what different types of drivers？

So here I think it looks weird again。Yeah， right， depending。On the relative location。Off。

Data source in application。That's how we have different kinds of drivers。So we will talk about these。

 There are four drivers right here。Which our first one is bridges。

And the second one is direct translation to native API via non Java driver。

 the third one will be network bridges and the fourth one will be direct translation to the native API via Java driver。

So later on in your slides you will see on the right top right corner I have a little database icon okay so what I want you to do is to draw the rest okay I'll show you what the rest looks like to show。

The concept of the drive。So let's talk about one by one。The first one is the bridge。

 so you can see right here， it's a bit small， but you can see。

The bridge right here we're starting out with the app。Okay， which is what you have？Okay， and the app。

Sits on top of the JDBC。And here's just an example， it doesn't have to be ODBC。

 but JDBC sits on ODBC。And then we connect to the database。So what is actually happening here？

So for the first type of drivers where we call them the bridges。

 so they translate the JDBC called into function calls of another API that is not native to the database management system。

So what we are saying right here is that's an example we have imagine。

The driver is a driver between JDBC and ODBC， so you actually write your application in the way that you are thinking about this is going to be for the JDBC for the Java Act and then。

The driver take care of translating from one API to another the API。Okay。

So then because maybe your database is actually for OTBC。So that's what this kind of rich type is do。

So the advantage right here is that it's easy to piggyback to the application onto an existing installation。

So for example， today you already have some other types that you want to use。

 but you don't want to install it so then you can just use this bridge type。

 you don't install another， let's say you don't want to install O PCC。Okay， then。

The driver can take care。But as you can imagine， this doesn't sound that small right you're just from one API to another API API still sits on top of something else right API still wraps up other more bottom part functions。

 so the disadvantages here will be like increase the numbers of layers between data source and and that would affect the。

So for example， you can imagine today。Let me see。For example。

 we want to get data from Twitter and have any one of you tried。Crawling data from Twitter。

So Twitter Day provides an API， okay， also an application programming interface that you can actually write a program and then specify。

 say， from this moment on， I want to collect all of the tweets that is being tweeted right now。

 including what stream。The Twitter is sneaky， they will only give you  one percent of it。

 but if you do that。So there are researchers， this is off the topic。

 but there are researchers trying to see whether there is any way if they use enough computers to hack it and then they can get like so many of the1% and get it all and apparently it's not possible。

 I don't know what to does behind it， but they just don't let people do。

To collect all of the data at that moment okay but anyway。

 so Twitter API is a very powerful tool because it's impossible for yourself。

 almost impossible you can still break it， but it's almost impossible for you to collect all of the tweets happening at this moment right like we are talking there are so many tweets in Twitter right now so Twitter they apply they offer this API for you to use。

So you can imagine today maybe you think okay， Twitter A is kind of hard to learn。

 so you found on GitHub someone else is writing。Another API on top of Twitter API saying this will be more intuitive。

Okay so then you write a program， connect to the third party API。

 which connects to the Twitter idea and Twitter then connects to their database management system。

Imagine that's not the smartest way。 Okay， so this is kind of the what the bridge is doing。

But maybe it's a lazy way because you just don't want to think。

 maybe quick implementation but slow performance。Okay， that's type one。The second type。

We call direct translation to the native API via nonga。So here you can see。

 that's what we have right here。Also starting from the application we have again。

 in our application again， sits on top of JDBC， which is the same thing throughout the all four types because we're talking about different types of drivers。

Oject。Then。R BCC sits on top of and databases API。So what do you mean by this but for this type？

This type of drivers， it actually translates JDBC function all directly into method implicationss of the APII of one specific data source。

 so you can imagine sometimes the database itself will provide you with some APIs。

 even though it's not， maybe not written in Java。If your application is running job。

So the advantage of it is that most of the time。If the database is going to implement an API。

They will implement the way thats the most optimize。

And they might be able to use C or C++ in the mixture of Java just speed it up， okay。

But the disadvantage of it。It will be that database driver that implements the APII needs to be installed on each computer that runs them。

So for example， if today your application actually has。Ha to run on multiple computers。

 then they will all need to install this。Sometimes that becomes an overhead。

So that's why this will lead to the third approach if we don't want to install all of the computers with the database API。

Then we can actually use network。So you can see right here。Imagine this。As all of the computers。停该屎。

I'm just doing my own thing here。 you guys come see， but imagine the left side， Okay。

 the application in JDDC is on each computer。Okay，Then we actually have a connect right there。

 you can see in the middle part we have the middleware。 that's the JDBC with the ODC。

 You can imagine it as a stove。so we have the local part is connect to the server。

So how this approach is doing is that the driver talks over the network to a middleware server that translates the JDBC request into database management system specific method invocation。

 so instead of having the driver sitting on each computer。

 you just have this sitting in the car okay in the。

So the right on the client side then is not database management assistance。

So it doesn't really care about what the database is。And because the whole thing。

 the more important part now is being taken care by the server。

 so whatever you need to put on the clients， okay the each the computer side it's a lot smaller。

And the reason， again， the reason we can have it so small is because。

For the little driver we have on the clients， they only needs to implement functions for sending SQL to the in terms of understanding the SQL command and having theques returned back from the database that'll be taken care of。

いのか。OkayFinally， the very last approach we have。It's just a bit different from the second approach。

 it's the direct translation to the native API via Java drive。

 so earlier it was a non Java one here the Java。How the driver actually communicates with the database management system is through the Java Socket。

So you can see right there we have the application sitting on top of JBBC。And the JDBC talks。

Through Java Sockets with the database。In earlier you saw， I know you guys couldn't really color it。

 but earlier in the second one， we have the DB API。Orange。

 but here it's blue because that means they are actually written in the same language。

So driver on the client side is written in Java in。That means they are database management systems。

So the driver in this type translates JDVC calls into the native API of the database system。

So that was all of the types for the drivers。So then when you are working on your project。

 you can think about what happens in your technology。

How you can map it to what you are using for them。So we have three minutes left。Yeah。

 so for the teams that haven't demonstrated the demos， I think it will be taking place today。

tomorrow okay so just make sure I think you guys will meet Yan J at 337 and I might be there。

 I might not be there so I come in enough， but she would definitely be there。

And for office hour today， Ill have to move it to two to three okay。

 if you are planning to come later， I have to move it to two to three and I'll send on an email later as well。

So that's it for today， Okay， I's see you guys on Friday。嗯。

