# 宾夕法尼亚州立大学【中英⚡数据库管理系统｜CMPSC431 Fall 2015, Database Management Systems】 p24 P25 NoSQL导论：MongoDB - 第2部分 -BV1N76CBwEXb_p24-

Good morning， everyone。So the。The demo one will be held in this week and I'm sure all of you have filled out the schedule。

With the T and。We up closeed it。The final schedule in project， and then when you go back to find it。

 there will be a demo number one schedule。And I can show you quickly right here。

So right here we have every team's time to meet up with the TA。

And is there any team who will be demonstrating on the CSE machine or you can demonstrate it from your laptop？

All from the laptop。Okay， so then no one has to。In the computer。Okay。

 but if you do have to email her and I think she will announce which。

Oice to meet up with and basically it's just 15 minute demonstration I'll repeat this again before the class finish but the expectation will be a needed interface that is able to communicate with your database and you have to populate some sorts of data into a data okay so whatever you want to do on your interface either just just displaying the data in table on the interface or if you want to do searching or if you want to do I can do the function of registering user already okay I just need look at the connections establish that all。

And in terms of interface， I think all of you guys know we are expecting like a web page。

 but if you want to do any GI or even you want Gui on the phone。

 like I don't know like an app or anything that's all right， Okay， so that's that for。ですけど。

And regarding to homework4。Still writing it， hopefully I can have it out。😊。

Today or tomorrow so we will be using those SQL and I found a data set from Yelp so we can play around with the YelL data which I think is really fun so that would be for homework for if I end up posting it really late I will move to deadline。

So， that's that。Let's get to this lecture for。So we are going to continue the Monggo Dibi lesson from last time and we will finish it today。

And on Wednesday， we will move on to chapter6。All right。

 so review from last time last time we spent quite a amount of time talking about what is knownB and what's the concept behind it and how do we map it to speak all right So we learned about Mongo Db in the database can have multiple collections in the collections we have documents and document has filled and one of the most interesting thing about Monggo Db is that for document each document in the same collection does not have to have the same privilege。

 And that's one of the very strong。Strong feature of no sequel in small D B in particular。

And last time we。P around with some of the queries and if you remember in MonggoDP。

 they call their own semantics like Cru， CRRUDC stands for Create R stands for read U stands for update and deep stands for delete。

 and last time even though we only spent like half of the lecture like really putting our hands on and trying out to command。

 we actually already learned really helpful。So longerma be is really easy to learn。

And last time we were trying out on the terminal， when you work on the homework or anything you can still work on the online terminal。

 but today I'll just do it on my own terminal， I just think the font is nice big and nice to see。

 it's the same thing。And before we move on， just want to。

Remind you again so this slide will be based on the little Mongol Db book。

 so it's by Carl Carl when you are reviewing for Monol Db。

 I think this would be a really good material for you to reach。If you and I have the references last。

All right。So， let's get into。Before we get started， if you are trying out on your laptop。

 just remember we have the script for。Creating the data。

If you're not working on that but that's fine， we can just write it on the slides。So。

I have to script。From that time， it extra 2 full。So basically， we just need to。

Insert the unicorn data again。Since last time we were working on the arm。On terminal。

 so it's gone now。And if you remember。Let's say we don't have any collection called unicorns right now。

 starting from the beginning， okay， like last time。

 do you remember how we can create a collection called unicorns？



![](img/f914ddc5876808955acd34ad139da803_1.png)

응，就你 거。

![](img/f914ddc5876808955acd34ad139da803_3.png)

That's it。 so then you switch toユicコンテす。

![](img/f914ddc5876808955acd34ad139da803_5.png)

So if you are not familiar with the example of this time。

 we're going to talk about lots of unicorns so don't feel weird about it。

 that's what Carl came up with and I think it's really functional。All right。

 so now I'm just going to paste this script I had earlier， and now we have all the email。Okay。

 nothing fancy so far just doing the same thing with O。

So if you look at slide three where we have the CoVI4。

 which we were supposed to work on last time in Miana time。

 so in Que4 we want to find the female unicors that either love apples or way less than 500 pounds。

So what do you think we will do？If you remember last time we were talking about whenever you want to get some document with certain criteria。

 we will be using the function find。Because let's start from that。So for the find function。

 we can directly just specifyify the criteria。😔，And if you remember in MongoDb。

 just like a lot of No equalQL language， whether we want to specify some criteria。

 it has a format of key value， key column them value。

 if you have multiple key value terms specify implicitly you're specifying， they should all be true。

 so it's an an statement。But this time we want。They are either love apples or way less than 500 pounds。

But the common thing is they're all females。So you can think of it as the first criteria being gender is email。

And。Either law f or way less than fact。So what we can go about it。

So just remember whenever we put fuel in Longgo TV， you start with a cur braces。Right。

So let say the gender is female， this one， this part is easy。That's the first criteria we want。

And the second one is the one we last time didn't talk about， so implicitly。

 if we just put all of the terms together， it's going to be an an state。

And if you remember in Monggo Db， it will use a lot of operators starting with a dollar sign right Last time we have dollar sign in dollar sign greater than dollar sign with G T。

 So actually in Monggo Db， we have dollar sign or。Okay， so this is。Pretty cool part。

Is the chairriff covering？The lastO。So if we start with a dollar sign or， you can specify。

Multiple terms in a list。Like this， okay so we can open a list。😔。

And then we just list the terms so as long as one of the terms in the list is righted。

But then the whole thing is true。So what you can do is。This unicorn loves Apple， okay。

 that's the first term。And。This unicorn weight。It's less than 500， if you recall in Monggo DB。

 saying any comparison， less than greater than it's also again done in dollar sign， so we do this。

Less than 500。Okay。哎。So that's all we want to put in the ore list so then we can close the ore list。

😔，And then we close the whole terms。All of the terms for the find。Then we close the fight。

Rather intuitive， but if you read through it again， it's basically saying。

OrWe want to find the unicorns。 It's either gender F。 we want to find the unicorns。

 That is gender F N here。And in the end， saying， what do we want？

The unicorn either loves apple or weight。Less than 50。So you can see how nested Mongo D B can get。

Give you a little bit of time before I hit enter。Yeah。

 so you have the or after gender act's like the married。Yeah。

 if we just concatenate all of the terms with directly comma， it means end。Mmm。Allright。That's that。

 so these are the unicorns that we move want。Okay， so if you go back to check it， yep。

 this is female and the loves have。私のタこ。I'll either love Apple or weight less than 500。

And you can check for these as well。Okay， so that's we're pretty。

So up until now we have learned about create， read and deletes， and this is one of the read。

Which is like the just queryming in SQL。So right now we have one。Left。

One out four that we haven't learned yet， which is update。Okay。So let's talk about updatingmongo Le。

For example， today if we want to update one of the unicorn's weight into 590。Let's take a look。

 so in the collection we have。One of the unicorns。Whose name I think is。换到。NoodlesWith six os。Yeah。

 yesterday I was I couldn't find it， and I type seven old anyway。

So there's one of the unicorns with named noodles with six os。Did you take a look at this unicorn。嗯。

The weight is。and we want to increase it a little bit。Before we move on， right now。

 I feel like you must already feel like why is there always so many fields listing。

 it's really confusing， so is it possible that we just select the columns or the fields we want。

So that would be the projection in MongoDP， which is the projection we learned in relation to algebra bracketque。

 just selecting the fields we want。So to do it in MonggoDb。So we can repeat again。In the find。

Function right here。We can actually specify a second argument listing the fields we want。

And this is the interesting part。So in Mongo Db， it allows you to stheify the field you want either by including it or excluding it。

For example， right here， okay， we start second sets of arguments。In the second sets of pe race。

For example， today， because we are only caring about updating Role's weight so we can just show the name and the weight of rles。

 so you can say I just want the name and put column one， it means included。OkayAnd I want the weight。

On one include。Okay， so if you take a look at the result， this is what you will see。

 It gives you the name and the weight。 However， we were not expecting the automatic I generated by Mongol Db。

 So what we can do。It's following， including name， including weight。 We can do。Excluding。I D， okay。

 so this is a very interesting feature of Mongo D B。

 You can say I want to exclude I D by specifying into 0。So when we press it again， now we only get。

The name and delete。Yeah。イ。Can we work。就す。Multiple things。I don't really get what ist mean you say。

嘅系师布嗯哼。Oh no， no， no。 so yeah， Mongo D bes all like this。

 they are all en curly braces because the idea will be more like a set of fields because every document has different fields。

 so it doesn't try to put it all in。Okay。Al right， but so now you're wondering， okay。

 we have including and excluding， but won't it be weird if we just mix them match？

They include and exclude logically， it doesn't make sense。 Sa， okay， include name， include weight。

 exclude date of birth， and you exclude the， the food they love to eat。

 So Mon the D actually doesn't allow you to do that。可这样子。You do say。

You would say you can not currently。Mix inclusion， including and excluding。 Okay。

 so the only thing that you can mix mix with， including will be an automatic I D because it count by default。

Another way you can do it。Is saying。So did I say。I don't want a date of birth。

And I don't want to know what food it loves to eat。Okay， then it will give you the rest of。Okay。

 so that's a really handy feature of Mon。All right。

 let's go back to our initial task where we want to update。Rudles weight， from 575 to 590。

So if you take a look right here， okay， right now， its weight is 555。So intuitively， you might think。

All right。We want to just do。Update， okay。Update the unicorn。 so we find the unicorn first。

With the name。不都。じ。Okay， we find the link first。And then for the second argument， you just say， okay。

 change the way。フイナ一。Seems pretty。Intuitive， right？But actually if you hit An。

 even though nothing won't happens。Okay， if we again try to。The noles this time。It's gone。

You'll be a why because it seems correct， right， we just find the name and then we update the weight。

But in Mongodibi， what this actually does is it finds the document matching this。

And just totally replace it with a document with only weight 5，90。 Okay， So far。

 it's kind of bizarre， but。Let's take a look， okay？

We can say we want to find where the document having weighed 590。And you see。

 we do have a document of unicorn in here who has only the weight information。Okay。

So you want to be careful when you're updating ongo ZB。documentに何万個っとい。Now let's fix this。

 but let's get。The information of。Rodles back。So what we can do， Okay， we will do again。

 Let's start with the updates。其他。Update。And this time， we just want to directly edit。This one okay。

 this document。So what we can do is， again， let's say， okay， I want a find document with Wen 90。

Again the correct way。Of， updating it。It's actually giving it a set。Okay， so this is the。

Not so intuitive part。 Okay， you want to say， what do I want to update it。

 I don't want to directly replace the whole thing。 And instead， I want to set field by field。

So how do we do it？In the set operator， you can just basically list the fields that you want to set the documents to have。

So here again， we go back to saying you don't have to write all these down。

 just get the idea of that's all， right so we try to recover。Noodles， okay， the name of it。

Let's just make it up。 Maybe we remember it loved Apple。And。Remember memberss gender。没有。Okay。

 that's that。So now you can go back。F。Do do， because it doesn't have。It's there again， okay。

 because we just updated it back by doing the set。So by doing this set right here。Okay。

 we can target a specific document and set the fields we want the field to clean。

So what would you do now with the weight？那ぜ。All right。So today， let's say we want to directly。

Change the weight back。Without replacing the whole document， what we can do。To say。Update。

The unicorn。With this name。And then you say， I just want to directly set。有位。To be something， okay。

 sorry， for example， let's say you lose his weight again。Then we can just do that， Okay。

 so that's the correct way of updating to be careful that you don't want to replace the whole thing。

Al right。A little bit more on updates， actually we have a few more operators on updates。

 if you take a look at slide8， I put two operators。

 the first one is INC which stands for increment and the second one is push。

We can practice how these are， so increment very intuitively we know doing increment just on a certain field you either increment okay by the amount you specify so if you specify negative and it's decreasing。

So for push。Push will be an idea of， for example， in a field you already have an existing value。

 if you do push， it makes it into a list and app pending another value。

Because if you recall in No SQL， the values for a field being atomic is not necessary。

So you can just directly transfer transform it into a list。

 so let's take a look at slide nine where we have period five。

Sa today we have a unicorn whose name is Pilate and we want to decrease the number of vampires of its flight too。

I was finding again yesterday what it means by the vampire， apparently unicorns kill vampires。

 so that's the number of vampires unicorns kill control so I thought that unicorns owns vampire。

 but it's not that way anyway， so some of the unicorns in this data the said has like number of vampires and for the unicorn whose name is pilot we want to decrease it by two。

So what we can do， again， this is updating that we can say。In the universe course。

 we want to do update， right？In the Uniicorn we want to update has name pilot。

So so far you will already notice we are searching the unicorns by name， okay。

 so this is because in the data set they don't have overlap name。

So we want to find a Uniicorn whose name is Pit and we want to do update。

 which is decreasing the vampire number by two， but in Mongodivi we only use increased INC。

So increased by negative two is decreasing by2， okay？So here， same thing earlier。

 we do set operator to set the value， but now we want to do increment， so we just do this。

We first find the unicorn we want， and then in the second argument of update。

 we say we want to do increment。So what field do we want to do increment on？

You want to do on the vampire still。And what's the value we want to increment by。

 we want to increment by negative two。打谢进福仔。I forgot to check how many impact it had before。

 but remember it's supposed to decreased。Okay。So that's for changing the value directly。All right。

 and let's try I'll push。So for query number six， we want to add。Sugar to the list of food。

 Uniicorn Aaraa loves to eat。 We can try to find。What are likes to eat first by doing fine？

And the name of the unicorn is all。And let's say we are only interested in the name。

And the food it love seeing。And we don't want I just to review quickly again of how to do the list of fields you want。

One stands for including zero stands for ink。So you can see right here we have Aura。

 it loves carrot and grape， and we want to add sugar into it。So this is another example of update。

So what we can do， okay again， we do update。And first fine。The unicorn， the name is Aurora， right？

And here's the interesting part。How do we do to push a value into an existing list？

So we just need to do push。And where do we want to push into。

 we want to push into the field called love。And the values we want to push into。也就かな。H。

That's it really simple。 Okay， so here's the operator of pushing and you just push a new value into the existing value。

 Okay， if the original one is not a list， it will transform it into a list and then just make them into a list of two elements。

So if you try again， we want to find oururra in the gloves it likes to eat。

 then this time we get sugar。In the list， okay， so that's it。Any questions so far？For the updates。

Pretty sium。Okay。Let's see a few more things。I we don't have that much to talk about today。

 it's going to be quite short。嗯。So MongoDB， it provides you with a little bit of tweaked version of update。

 so it's called Upert， you can see on slide 12 I skip to slide 11 because I already talked about it。

So on slide 12 for the up。And it's basically。That it will insert a document if it is not found。Okay。

 so it's update plus insert。However。You have to enable a bowling in update to do that so for example。

 if you're updating a document that actually doesn't exist， if you just put up iss true。

 then you'll just create a new document。For example。That's right。For example。In our collection。

We want to see whether we have any unicorn whose name is Walllaas or anything like that。

And we can't find any。哎。So if today you are saying we already don't have all a lot to begin with。

 but today if you're saying I want to increment the number of pis of this uniformicor by one。

 and you simply do。Like this。Okay， and we do increment。We go to find that， there's still no unics。

Right， because。What we do here。We're directly saying we want to update the number of vampires on the unicqorn that doesn't exist。

Right。If you want to do two things in one that first created， if you don't find it。

And then incremented by one， what you can do。All you can do is to specify one more argument。

Right here， just saying， up is true。Okay to is update and insert， you're just saying for this action。

 I want the officer to be true。So unlike last time， even though we couldn't find Wala。This time。

 we will create one for you。Okay， and then increment the vampires。So if you do the up again。

 this time because that unicorn already exists in the collection。

 so it won't create a new one to replace it instead。If we do it again。

It will directly incrementitive at times， okay， so they just allow more flexibility。

 taking care of the documents that does not exist。So that's for offset。And let's take a look。

 so for now what we have seen so far， we are searching the Uniicors all by the NAs because I said in the data set。

 it just by default it doesn't have any unicorns with the same name right so every time we do an update it just directly on a single document。

Well， what if today we say we want to do an update on more than one？😔，More than one year ago。

For example， you would take a look at 37。So。Yeah， I think Carl is pretty。Funny。

 so he wants to give all of the unicorn back。So if you want to give a unicorns vaccine。

 it's saying we set the one more field call vaccinated。Into the documents。

 so what we want to do today is setting vaccinated to all of the unicorns in our collection。

So you can say originally you might think we can do it like this。

 okay we want to do update on which unicorns on all of the unicorns。

 so for the first argument we want to set we just don't say anything， okay。

 we just do empty curly braces because then all of the unicorn meet the criteria。

And the second thing you might want to do would be say， okay， we want to set。嗯。I feel vaccinated。

To bulling trip。But if you directly do this， actually you would just do the first unicorn according to the index。

So you do try。We would directly do this only。Okay， then you find the unicorns。

That have been vaccinated it。You would see there's only one of them。

remember what we want to do is update all of the unicorns instead of just one。Okay。

So instead of directly doing here。Well we should do。Is to specify one more argument。

 so it's just basically saying for multiple。Yes。大谢。So we want you to say multiple truth。

So Mongo D by default， you will only update one。Unless you say multiple truth。

 then all of the documents that fit the criteria。Print the criteria， which is no criteria。

Will be updated。Okay。That's that。So we have four more queries left。

 I'll just quickly go through them and then we're done today。I think last time。

It was Austin asked about sorting。I think maybe so you asked about what can we do for sorting。

 so in Mongol DP we can do sorting， okay we can say we want to do increasingly or decreasing。

So what you can do。For example， today we want to sort the unicorns based on their weight。

Then you can do we find first， okay， we just find all of the Unis。And we do sorting。So in Mogul Db。

 the sorting criteria will be like this， you say。I want to store by weight decreasing， okay。

 I want the heavierest first。These just do sort and then put the criteria like that。Like。

What do you want to s by。To validate whether this is true。

Let's also put in the fields we want to make it clearer， Okay， so in find， remember we can specify。

Two arguments。And the second arguments will be。The fields you want。

 So here let's say we only want the name。The weight。And we don't like the automatic defense。

So this is what we can do。We want to first find all of the unicorns。Right。

 and we only want those fields。And we sort the unicorns based on the weight decreasing。

 so we will get the heaviest unicorn on the top。Okay， so this is the result you can see。Okay。

 so the reason it's put to the last it's Walla because we didn't give it a weight。 Okay。

 so right there you can see that's。Unicorns are sold to increases。So that's what fair we eat。

She's right。And for the second argument in find where we specify name， weight and I D。

 that's optional。 okay， just to make this clearer。So in MongoTb。

 you can actually also sort by two fields， we can say we want to sort by this first。And then this。

 okay so what we can do is basically just add more arguments。In the sort function。

So we can say we want to first store by the name， maybe increasingly。Right here。IfWe add one more。

In the sorting list， okay， we can say first order the unicorns based on the name increasingly then sorted based on the weight decreasing。

 and this won't really show in our result it only comes in handy when you have maybe two of unicorns with the same name you want to break the tie。

指对速で做。系。So you can see now they are being sorted alphabetically。ButJust remember。

 you can specify more than one criteria that to sold。これ。

Then let's think about whether every time we want all of the information。

 maybe we just want the top two， maybe we just want second and three okay， so I Mongo DB。

 one is the interesting feature you can do is to say maybe I want to limit just the top few in SQL as well I want to limit maybe the top five。

So if you want to limit the top five。Let's say。We first sort unicorns by weight decreasingly。

 and maybe we just want the heaviest pipe。Then what we can do is just to do this， dot limit。

 and then just say the number of documents。So it will catch it from the top。

So if we press youll see this time， we only get the five heaviest unicorns。In our data set。Okay。

So one of the function that goes hands in hands with this is not only can we say we want just like how many we want。

 we can only also say how many do we want to skip。For example。If today， I want to say， I just want。

The second is the。Heappaviest。So we should get these two。Then what we can do。Did say， okay。

 we only want two unicorns。And if you don't only do limit， it's supposed to give you this。

 the top two。 So if you say and I want to skip one， then the two will move down here。

So you can do this by saying I want to sketch。Okay， so instead of giving you。The heaviest， too。

It would move down and give you the second heaviest and third heaviest。系い。やぱ見て。

And just remember in Mongo Db， the order of limit and skip doesn't matter。 Okay。

 if you skip first and then do limit， it's the same。So this is what you can do for a query。1。

To get the second and third he you。Any question for that？And then we come to the last one。

Early for today。All right。So the last thing we want to talk about today will be to do some counting。

So as you can imagine， we also have average maximum all those things。

 but we just quickly work on how count is like in Mongol TV。It's really simple。

 you just have to do this。Let's say we want to know how many unicorns we actually insert into the database。

 we haven't even checked yet because we always just copy and paste the whole script。

So you did just say count。It's almost the same idea in Cor， just count。Then你要跳。Okay。Then you can say。

 what if I only want to count certain criteria of Unis？For example。

 I want to see the unicorns who have。More than 50 vampires。Okay， so what you can do。

And you can just specify whatever criteria you want。In here。

Then we will know only five out of 12 of over 15 them。

So this is actually completely semantically equivalent。To this。We can say we want to find such。

Unicorns first。Okay we find it first。Then we do come。Okay， we are the exact same。So just remember。

 we have different ways。Of doing counting。Any question for this？All right。So。Before you go。

 just remind you a few more things。So as you will know， demo1 is this week。

 and I showed you the schedule earlier， you can go on Angel to see it which put it under the project folder。

Okay， and so make sure you。Contact the TA and know where you should meet。

 she should send out in email。Tell you guys where you need have。And。

So the expectation will be import data into the database and have a really simple interface to interact with your database Okay。

 you don't have to make you fancy we're not asking it for a really cr interface。And homework portion。

 I will post as soon if I post it a bit late， Ill move the deadline bit。

 so it will be on in NoSQL just on the things we have learned in the last today and last time。Okay。

 and midterm is。Thanks， next week。Yes， next， yeah， next next week。 And I'm still thinking about the。

Uncoing exactly。 Maybe I'll do it。Thank thanks a lot。Just right after you're written them， don'。

Anyway， I'll let you guys， so that's for that， I see you guys。Wednesday。

