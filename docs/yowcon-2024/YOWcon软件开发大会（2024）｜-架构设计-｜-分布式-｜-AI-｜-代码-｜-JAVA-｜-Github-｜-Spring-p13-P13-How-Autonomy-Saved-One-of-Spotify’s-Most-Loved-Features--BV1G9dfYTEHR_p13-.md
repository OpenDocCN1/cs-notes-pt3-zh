# YOWcon软件开发大会（2024）｜-架构设计-｜-分布式-｜-AI-｜-代码-｜-JAVA-｜-Github-｜-Spring-p13-P13-How-Autonomy-Saved-One-of-Spotify’s-Most-Loved-Features--BV1G9dfYTEHR_p13-

![](img/8f20598b72faea2635f1e315ce0476c5_0.png)

Let's start with a self of usal。So yeah， it's great to be back in Australia， it's a bit warm。

 especially for someone who grew up close to the Arctic Circle in north of Sweden。

 but you know I manage。So my topic today is how autonomy saved one of Spotify's most loved features from being killed with the alternative title of or how we accidentally fixed Mondays。

 and I'm going to come back to what that actually means。But as we just heard。

 I'm a consultant at Better Product work， a company that I started just one week ago。

 so it's pretty new， but we believe it's a group of people where experience of product model type Spotify type corporations or companies and we believe that the conventional way of building products is kind of broken and we work with visionary leaders to challenge convention and find a new and better ways to do product development。

But I was also said Spotify from around 10 teams to 200 teams。

So that's a little bit what I will talk about today。So but first， how many of you？

Is there anyone who don't know what Spotify is， Raise your hand。Cant see anyone Great penetration。

 Wow， So it's music streaming service。 How many of you know what Discover Week is。Most or many。

 I'd say， not everyone。Okay， so don't worry I'm gonna tell all of you。

 So you probably know what a playlist is， though， kind of the the the mix tape of my youth， you。

 you can put together a lot of different music into a list and give it a name。So here we have。

 for instance， let's see if we can get this to work， you can see the pointer up。

Summer rotation by youa Kimsonian， that's a list that I've created or here's funk outta here by Spotify a playlist that I've chosen to follow。

 but then all of a sudden one day for the first time something pops up in the area for user generated content。

Called Discover Weekly made for Ewa Kimson。 this is unheard of。 just popped up。 I didn't follow it。

 I didn't create it。 and we'll come back to why that's important。 But once I click Discover Weekly。

 I get 30 songs。That I've never listened to before， at least not on Spotify app。

The Spotify doesn't know if you listen to it。Anywhere else， not yet this least， who knows？

And there's a high chance that I like， if not all， but then most of these or。

 or at least can find a few new favorites。So that was quite a feat。Now。

 you know a little bit what what it is。 Let's， let's go back in time a little bit。

 Do you remember how you used to do to find music before Spotify came。Maybe something like this。

This is amoeba records in California。And I could spend an hour easily， you know。

 browsing through Z Ds and try to find new music。 You maybe listen to some of them。

 My music nerd friends at Spotify could probably spend a day or more in a store like this。

My mom on the other hand， if we were to visit let's say， Los Angeles。

 she might look into the store and say， yeah， you know what。

 I'm going to hit the clothing store across the street。She loves music。

 but she's not that interested in music if you know the difference。

And I'm going to get back to why it's important what my mom thinks。

 it actually has value to the story。But then Spotify came along and did this search。So， any of you。

Used a napster back in the day or I mean， no of Napster， maybe okay， Kazza， D。 C， Directect Connect。

 Yeah Pirate Bay， There are many ways of illegally downloading music。

 but still a lot of people were doing it because it was free。

So I was among them in my college or university years you would go to parties and oh do you have napster and you would search for music if you were lucky。

 you would actually find what you were looking for。

 if you were even more lucky it wouldn't take forever to download and if you were even luckier it was actually the right thing once you downloaded it and you could play it so the big feet and of Spotify。

 almost all the music existed and it started playing instantaneously。And I thought it was so cool。

 I was just put thing after thing into it， and it just started playing。

 it had even the more obscure things that I liked。But showing it to my mom。She's like， what is this。

 What do I do， Well， search for something that you like。 What do you like。The beetles。

 oh they're not at the service complicated， but yeah it's fixed now， by the way。TheRolling Stones。

 she searched for that and it starts to play。Great， everyone's happy。

 so back at the Spotify headquartersquarter， our founder， one of the founders and the CEO。

 is still the CEO actually。😊，Yay， we've nailed search and pay， that's awesome。

 but there' is a problem。If you don't know what you want to listen to or a product is useless。 Okay。

 that's a little bit exaggerated， maybe， but it's hard。So we know that we。

 we play a big role in our users lives。 when it comes to lean in use cases。 That's what we call them。

 People who are happy to access all the music in the world through a search bar， early adopters。

 technology， evangelist and so on。😊，But lots of more people want a little more guidance。

 and we're still not performing as well as we could in the lean back mainstream use cases as we started referring to them as。

And we need to understand why and try to solve this。

 This was the strategic intent that the leadership set to the organization。

So we've made some attempts to reach this audience that was less of an effort compared to search and creating playlist and so on radio。

 So in the early days you could feed a decade and a genre into it， So 70s， jazz or 80s rock。

 something like that。And then later you could see it with a song or a playlist and so on。

 and we didn't see any really great uptake or uplift in the engagement from these type of users。

Personally， I believe that it's because people who listen to radio， well， they listen to radio。

 they don't listen to PowerPoin。So then we tried influenced by Pinterest as you may see and Netflix style recommendations like so you listen to of mice and men that maybe try motionless invite and again。

 the music nerds at the company loved this。 It's like wow， there's a connection between these two。

 I didn't know that might be good and you could scroll forever and ever and ever it never stopped again。

 music nerds loved it。My mom， well she wasn't super happy getting up Sunday morning。

 spending 30 minutes scrolling through Pinterest style recommendations and then find something to listen to。

 she just wants to tune in。Oh know， dropout， no that's another thing。ESo， at this time。

Some music industry pundits or talking heads were suggesting that you know mainstream users。

 they aren't that interested in discovering new music， they're content with listening to same old。

 same old， so there's no use building these algorithms or recommendations for them。

So there was actually this sentiment was also prevalent at Sify。

 but there were a group of engineers or a couple of them who wouldn't believe this。

 They kept thinking about this problem and they said there must be a better way。

And they presented this idea to the product manager。And he said， well， yeah， it seems reasonable。

 So that's not good。 Let's let's bring in a product designer to challenge it。

 play the role of the Ba Cup because most of our ideas。

How intuitive and obviously were turned out to be wrong。So let's kill it as fast as we can。

So the designer said， you know， why do we need this feature， It's so bloated already。

 mainstream leanback users need a really simple app。

 we couldnt we shouldn't add more things so that that risk is complicating it。

 We must keep it simple。And I don't know if you remember。 but at this time。

 Apple Music was fairly new， and they had a collaboration with YouTube and put YouTube's new album。

In every user's library。Anyone remember this okay？And what was the reaction？Well。

 they thought they were bringing a gift and to many people they were。

 but a lot of people were really， really upset。Insly upset in my view， but they really hated it。

 and people took to Twitter saying things like， it's as if you know。

 I'm coming downstairs to have breakfast and there's bone or sitting in his underwear eating my sand。

 which is。 and you know this is a violation。 and the problem was that it wasn't easy for some reason to remove the song or the album。

 So they had to put out an emergency removal tool and yeah all of that。

So there was a sound argument to be made that we shouldn't put things in the user's library。

So that was a strong opinion against this thing。But so what it really was the discover Pinterest style that I showed earlier that was an algorithmic recommendation that we tried to use。

 and the two engineers had this idea that there's a feature at the end of the year called G in review。

 Now it's called Ra。 and maybe some of you seen it is actually released or this year's version came a few days ago where you can see all your your' listening in over from the year was our top five artists。

 top five songs and so on。And people share this。 and they。

 they figured that let's use this discover algorithm on all the music listening history for this year and call create a playlist from that called play it Forward。

 That was fun。 So they did that and didn't think much of it。😊，But then in March。

 they looked at the data and they saw that this is still being used by millions of users。

 So this is really high engagement。There's something to this， so that's how the idea was born。

And it was basically data from 75 million users， how they listened to this music。

 there was a proven user interface， a playlist super intuitive， loved by every user。

 an algorithm that could put songs into microchs to say that this song is probably similar to that song in that song which makes it easier to recommend songs。

Then it's used collaborative filtering。You know what collaborative filtering is？Maybe not all。

So let's say is someone here using Disc cover Weekly。Okay， you're using it。

 So let's say that you've created a playlist。 You spent a lot of time into your your favorite playlist or your。

 your current songs。 And maybe it's 20 songs。 let's say。

And you're thinking that you're this unique snowflake only I in the world have these 20 songs。

 but yeah， of course， no， we can find lots of users who have roughly the same songs。

 if not exact the same songs。 And what if all of these users。

 let's say that 80% of them have three songs in common that youve never listened to on Spotify。

 There's a chance you might like them。 So that's basically how it works。

 and then it's a little bit more complicated than unfortunately， that's a separate session。So。

 they have this idea。Great， so now what can we do it？What would it be like in your company？

Because in the most companies that I worked with， except Spotify。

Engineers won't even be thinking they won't be awake at night。

 challenging what the the no wals in the company say about the situation。

They wouldn't challenge that， they wouldn't come up with these ideas。

If they came up with another designer said this is a really shitty idea。

It will be very hard for them to make it happen。But not to Sify。Because in traditional organizations。

So many people that when I talk to to leaders or executives， they really believe in Welsh， of course。

 people on the floor， people in the teams， they should make a lot of the decisions。

 they are the experts。 this sounds super reasonable。 we shouldn't do it。

 They don't want to micromanage。 they only want to set goals and directions and guidelines and so on。

 but they're also responsible for that。 We're doing the right thing。 So how do we do that。

So traditionally， or you could say bureaucratic or plan driven organizations。

 people were suggesting that， but maybe if we only focus on the big things， projects， initiatives。

Okay， but how do we decide which project we should run and how we should prioritize them Well we build a business case or we do a return of investment cost benefit analysis okay so what will it cost and what will the return of value be？

Yeah， then we have to decide a lot of things we need to know who's going to be involved and so on and so forth。

 and suddenly you have locked down a lot of the decisions in early analysis that you said that you would ideally leave to the teams。

So we get these detailed budgets， toll gates becomes the only way of seeing RV moving towards the goal。

And in middle management， you know yeah， the only thing you can do。

 you're not responsible for that whether we're making the right thing or not。

 So you're focusing on resource allocation， delivery and plan， budget， time scope。

 And when we grow the companies， we have departments to make it easier to。

Recruit and have professional development and so on。 all makes sense。 very good ideas。

 but unfortunately， we also build silos between departments。

 which makes collaboration between departments hard。

And we don't really have any feedback between the front lines and the top because projects take a long time and not until we've actually delivered them。

 then we'll know。And if we use the assumption that if we ask users。

 internal users or or if we ask experts what we should build and we build roughly that。 Okay。

 often not exactly and often not on time。 but still， you know， then we're done， we did a good job。

 right。And often， because we are late and there is so much to do。

 we are too busy to check if we were even doing the right thing。

So Spotify shows another path that we call autonomous quas。And the CTO， who。

 who stood for many of these ideas。I that the most important feature of the organization is the autonomous squad。

 All other features in the organizations in the organization are designed to support this mini Start applied squad。

So that's the extent to， to which we we， we took the metaphor。 It should be a mini startup。

When I came out of Spotify， I started going around in the world。

 and people were also talking about autonomous team and autonomy outside of Spotify and great。

And but then when I started scratching the surface。

 it turned out that what most people meant with autonomous teams was independent that they could release independently。

Not that he could also decide what ideas to pursue。

 what with how to solve the problems that we were given。

So I started talking a lot about autonomous squads and so on。

Then this guy came along and had been talking about similar thing。As well。

 Morty Kagan of Silicon Valley Product Group， and he wrote a whole book called Empowered。

 and he chose the term Empowered Product team to describe this， used autonomous squad as an example。

So I guess yeah， he's， he's more famous than me。 So。

 so I started talking also about empowered product teams， but it's basically the same thing。

 The most important thing is to empower teams by assigning them problems to solve。

 then give the teams the space to solve them。And since then。

 Marty and I have collaborated and even wrote an article on the product model。

 how the Spotify model is really a product model， and it's all about the empowerpowered product team if you want to check that out。

But it's basically synonymous。So why do we need this。Well。

 there are four risks in product development。 One is that we're building things that aren't valuable or desirable。

 Customers won't buy it or they won't use it。Or that we're not building things that are viable for the business that it conforms with compliance and our business model and so on。

 that it's not usable， that users can't find it or don't understand how they use it。

 or that it's not feasible， but we can't。 It's too expensive or too complicated or it doesn't work with the technology we have。

But the thing is that all of these four interact all the time and the solution space and the problem space are moving concurrently and inform each other all the time。

So， for instance， as the discover weekly example showed。It was existing technology。

 already the existing systems， very little new development， really。

 It was because it was the engineers。 They were working with the enabling technology every day。

 They were in a unique position to understand what is now possible。If you know the Henry Ford thing。

 my customers would if I would have asked my customers， they would have said faster horses。

So they don't know what to ask for。 The engineers。 That's where a lot of the innovation comes from。

 So they need to be involved in actually suggesting what things to do or what things to try。

So new idea， great。 We can decide ourselves。 But how do we define success。

 How do we know if this is something worth actually pursuing。😊。

So we focus on outcomes and business results， not output。

 just to make sure everyone is on the same page。So we can see the world that we're living in now。

 we see needs that go unmet or pains for the users or friction or bad results for the company。

 which gives us a lot of ideas on， yeah we could fix this， but this could be improved。

 this could be better。And this leads to products and features and enhancements。 unfortunately。

 sometimes also do requirements and specifications。

 and it's easy to fall in love with your product and solutions。

 Some people even fall in love with requirements。Believe it or not。

And we lose focus on are we actually doing the right thing， or are we changing the world？Or。

 is this leading to different behavior that we want to see more of。Or less so。So the activities。

 epics， features， stories， whatever you want to call it。

 that's how we believe that we are going to reach our goals。And they are just hypotheses or bes。

 and they have to change if the numbers aren't improving。And worse。

 we are really bad at knowing what bets are the right ones。 They have a very low success rate。

As you can see from Ron Kohave， who used to run experimentation and testing at Amazon and Microsoft。

He says that the vast majority of new ideas fail in experiments。

 and even experts often misjudge which ones will pay off。So at Google and Bing。

 only about 10% to 20% of experiments generate positive results。

 So if you're not better than Microsoft or Google。Maybe 80 to 90% of what you're doing。

 you shouldn't even do。Okay， that's customer facing， you know， and user things。 Well。

 if you look at Microsoft as a whole， it's still one third that prove effective。

 And this is there are lots of numbers from the industry on that shows around one third of what we do is typically going be something that works well。

 One third of neutral results。 But what's what's even worse。 one third of negative results。

 It's actually going to hurt us or our customers or both。 and we shouldn't even be doing it。

And if you look at internal projects。Most of our solutions are useless。

 so this is a Stan group Ks report that they've been doing several times the last 25 years。

Or different numbers。 some， some would suggest that even more than 60% of features that we build for internal internal products are are never used or hardly ever。

And 30% infrequently or 50% here in this one from 2016。So we need to move away from opinions to data。

 So instead of saying， we're working on X， because Sam said it's important。

 we're done when Sam is O with it or when the specification is fulfilled， no。

We're working on X because we think it's going to give impact Y。

 which matters to spotify because of Z。 It's Z here， right。We're done when the metrics have moved。

Or in Google's word。Let data drive decisions， not the hippo， the highest paid person's opinion。

So instead of this at Spotify， we used something that we call aligned autonomy。

Meaning that we have cross functional squads， small and long lived， self organizing。

 focused on goals and outcomes， actual business results and using feedback loops to actually understand。

 are we getting closer to that。And collaboration between squads interacting directly。

 understanding when to collaborate and not what depends do we have managingishing them between themselves。

Rather than travering a manager hierarchies。And management focuses on vision， goals。

 strategic context， servant leadership， removing obstacles from squads， and so on。

And we have transparent information flowing both ways。

So what we learn on the ground actually informs the strategy。

 and then we set the strategy based on these data and insights that then informs what should the teams be focusing on。

 but it's not deciding exactly what but rather what problems to solve。For instance。

 we learned that we were running experiments， collecting data。

 doing user research in the teams that h， we need to figure out this Lean Bau case。

And then leadership understood the importance and they turned it back and say， yes。

 let's focus on this for this quarter， half year， year， whatever。Horizon you plan for。

So just this is a little bit of context because this means that the organization shifts from gatekeeping to facilitating context。

 So gatekeeping context would be that。Product managers， managers。

 designers who have access to product context， user customer context。

 What is the market doing competitors， What do the user say， They translate that into work items。

 backlog items stories， activities， which means that the teams don't have any direct contact and。

 and no empathy and no engagement with their actual user。So instead we want to facilitate context。

 how can we make this， all this context more easily digestible。

 more easily available for the teams so that we can actually involve them in deciding given this information。

 given what we hear and see what do you think we should doing， What's the best solution here。

 What's the best way forward。So just an example to understand what I mean。So this is at Spotify。

 for instance， all developers would have access to metrics。

 dashboarding have track and full of any metric they care about at Spotify。

 but it's a chance that they they don't have the bandwidth to do all of it。

 They might not have the expertise and so on。 So great as a product manager and designer can work together with analytics and figure it out and you know。

 pull out the signals from the noise。 What's the most important thing here。

So we see a decrease by blah， blah blah blah， blah and the， the。

 the number of registrations is dropping。 You'll have to get more people to play without hurting recommendations。

 blah， blah， blah。 So it's this describing a problem to solve。 It's not saying， build this feature。

 And now we're inviting the team。 Okay， how can we solve this。And saying with。

 with use research where， okay， the team could probably watch it on on live or or participate in it or or watch the recording of it afterwards。

 but。It's also great that someone can tease out the more important details and present them to the team。

So。The Discover weekly team。They were obviously not called Discover Weekly before Discover Weekly。

 they were called the Lambada team actually。So they wanted to they knew that it's all about engaging Leback users。

 that's the strategic direction now and we know what the metrics are reach depth retention。

 how can we get more people to use Disc Week or our features for Leback mainstream users。

 how can we get them to stay longer and how can we get them to come back more often。

So they could decide that， yeah， this is something that's in line with our mission。

 So they would just go off a bunch of them。 the two engineers， the product manager and designer。

 iterate a little bit on the solution。Yeah， throw some things away。 And after a couple of weeks。

 they had a cool enough app that they would fish food it。 as Google calls it。

 That means the team is using it。 Oh， cool。 awesome。 Just one thing， though。

 So they started using it and continuously improving and tweaking it。😊，Okay， now what。 No。

 we have an even better prototype。Let's test it on our colleagues。 Dog fooding。

 as it' sometimes called。So they didn't even， you know， announce it。

 They just snuck it out into people's playlist。 And people started， what's this。

 They turned to slackla and said， do you know what team is making this， What is this。

And they just was giggling in silence and looking at the metrics and seeing how it went viral internally。

Until it was time to okay， let's come out of the shadows and they wrote an email actually asking people to try it out and they used the playlist description in a novel way。

 adding a link to a Google form， explicitly asking for people people's feedback and what they thought about it。

So the rest of qua started using it and loved it and gave feedback。What's this。 Wow， awesome。

 release it。 It's as if my secret music twin put it together。 Everything in it is good。

 And we've got great survey results。😊，So it was a done deal。 Awesome， Now what。

 Maybe were fooling ourselves again。 We should try it with real users。

 So the CO has said the team should be able to ship anything to 5% of its users。 No questions asked。

 no permission needed。 Just ship it。😊，No， it's only music。

So this was possible because we intentionally invested a lot。

 both in culture and the way of working to support these kind of ideas。 So the CEO， again。

 used to say， we aim to make mistakes faster than anyone else。

You often kept referring to this phrase。Which might seem strange or stupid taking our context。

 but of course it's in order to learn more than others。So both working on the cultural aspect of it。

 celebrating failure。 team started having failure role。 say this is this is what I did。

 That was a mistake。 And this is what I learned from it。 We even published blog posts about it。

 The C TO had blog post about celebrating failure， if not X percent of what you're doing is failing。

 You're probably not pushing and innovating enough。But also in the way we work。

 so decoupling the architecture so that you can safely make mistakes and be wrong。

 if you work for five years on a big project and it's totally wrong， that's going to be very bad。

But if you only do try and minor changes and that not doesn't work， that's going to be okay。

So if Albaart blows up， you can still listen to music。If notifications blow up。

 you don't get spammed， but you can still listen to music。

And grab your rollout so that if something breaks， we can quickly roll it back again。So we're modest。

 let's do 1。5%， with still a million users。So will they like it。Let's find out。So watching the data。

We got 1200 survey responses， very， very positive user metrics really， really positive。

 and the whole U2 thing was only mentioned by a couple of people in the survey。

 and they were still using discoveryover Week。 So that turned out to be an exaggerated concern。

So we also did what's called social sentiment analysis or monitoring， watching Twitter。

So it's scary how well Spotify Discover weekly playlist snow me。

 Like former lover who lived through an near death experience with me Well。 At this point。

 Spotify Discover weekly knows me so well that if it proposed， I'd say yes。😊。

Discover Week on Spotify eliminates the needs from a musically knowledgeable boyfriend。 Now。

 it can be single forever economical win。 So， yeah， pretty good positive sentiment on on Twitter。😊。

So now we also could experiment much more because we had much more user data and do AB testing。

So early on， we said， what should the cover out look like， Well， discover。 It should be， you know。

 of course， an astronaut on the moon。 That's a very discovery， so。Don to figure out， actually。

What's the best way to get people to interact with personalized content， Well。

 that they know that it is personalized。 If they get that it's made for you。

 they will going are going to will want to interact with it。 So let's do a picture of them。

 but with cool colors。 Because we had a Facebook integration。

 We could take their profile picture overlay it with colors and the logo。 And wouldn't that be cool。

No， said the engineers， the senior engineers and the architects。

 It's not cool because we have to build an an entire content delivery network。

 It's going to be expensive。 It's computationally expensive to get the profile pictures from 75 million users。

 What if they update it， were so many reasons again， that in a regular company。

 if you would have needed permission。Or budget and so on。 It would been no。

But they could easily try it。 and they saw a 10% lift in weekly average usage。

 which is huge in in this context。 So they knew that it it's worth it。We tried。

 what's the right length，4 hours，3 hours，2 hours，4 hours， said the music nerds。Probably not。

 but we tested it and the two hours was more reasonable。

And this is where it's really great to combine a quantitative and qualitative analysis because the quant to looking at the numbers and yeah。

 people prefer two hours， they that's we can tell， but we don't understand why necessarily。

 So then interviewing and talking to users。 But it turns out that two hours is 30 songs。

 If you would publish a playlist every week saying these hundred songs you will love。

 It's like have I even loved hundred songs ever in my life。😊，And30 songs。 That was， oh。

 that little cute boy girl that's coming to you with a mix tape that they made hundred0 songs。

 a stalk here with a bunch of C Ds like， I've made these for you。 It's like， no。

How often should it be updated every day， No， every week is is， is enough。 you， you know。

 you want to keep people curious if it's every day， it's like， yeah。

 I don can't even be bothered ass a new one every next day。And then if we get it a little bit wrong。

 should it， should we err on the side on too unfamiliar or too familiar。 Well。

 let's make it too unfamiliar because it's it's discovery， right， you don't want， oh。

 you listen to when I'm 64 by the Beatles。 you should check out the day in life because they're on the same album。

 You probably did listen to both of them of Spotify。So the funny thing here， though。

 is that there was a bug that made two songs that you've listened to recently appear in your Discovery weekly playlist。

But instead of fixing the bug， we looked at the data and it turned out that the bug performed better than the actual feature。

And in qualitative analysis， we figured out that， okay。

 when they saw that there were these two songs， they were like， yeah， this this I I like。

 So maybe I like the other stuff as well。 So it increased their trust in the algorithm。Yeah。

 and then with some content mishaps still to this day， people complain about it。But， you know。

 I think it's a lot of guilty pleasure listening that informs the algorithm that they don't want to acknowledge。

So the winningan formula， we had two hours of personalized music recommendations。

Refreshed every Monday morning， delivered in a standard Sify playlist， no new user experience needed。

 a playlist image based on the Facebook account， all songs replaced each week which was also a killer feature because you know you get the Fmo thing or what if I don't check in this week then I don't know I would never know what I missed and you were actually actively had to copy it to other or liked the songs that you liked or it would be gone forever。

So no front end development needed，100% data informed。We have a winner， awesome。

But there's one problem。It didn't scale。So it was 75 millions shared playlist from a single user that changes every week on the same day。

And the playlist system wasn't built to handle that。Which the team had been told over and over again。

 you can't do it。 It won't support it。 we're thinking about rebuilding the playlist system yet again。

 it's been on our backlog for a year or two， so you should wait。HBeen on your backlog a year or two。

I guess we shouldn't wait was the team's reaction。And they didn't。 So， but now we had uneployed。

 and people were sad on Twitter。 just like that， My Spotify Discover weekly playlist was taken from me。

 I'm in mourn。 I hope it returns soon。😔，But now we had what's sometimes called a high integrity business case。

 We knew that this was a hit。With a very high probability， we tested it on a million users。

 so we had a high priority now to sort out the tech issues。

So it involved several teams and several months of work to really make it proper。

But we knew that it was worth it。So we gradually roll it out again， we tweaked the marketing message。

 we used the own user's own language in the launch， so adding translation and all the fancy stuff。

 but it turned out we showed through the data that discovered weekly in English actually performed better。

Because it was seen more as a brand or a feature in its own when it was in English rather than in the user's own language。

And we used the Twitter bus in ad campaigns like on the New York subway like this。

Tweak the packaging a little bit， released it。Discover Weekly reaches 1 billion tracks streamed in 10 weeks。

 Our biggest most successful launch ever。😊，And on Twitter， Monday mornings。

 I take a bath and listen to Discover Week。Got really excited。

 and I started crying a little because I realized tomorrow is Monday and Spotify is making me a new discovery weekly。

😊，It's actually so sad。 I'm excited I get for a new Disc vehicle on Spotify every Monday。

 Hence the claim that we accidentally fixed Mondays。 Now。

 Monday is something to look forward to instead of dreading。Yeah， this is fun to Tom Conrad。

 I don't know if you know who is it， Who is， but he's the co creator of Pandora。

 Spotify his biggest competitor， bigger than Spotify at that time in the US。 Okay。

 everyone is right to discover weekly is absolutely perfect。😊，A little bit better than？

So we believe that the ingredients of successful innovation is that you put people and problems into a fail friendly environment with cross functional teams where it's okay to throw things away and fail as long as you learn。

 And you do that by having enough slack and clear success metrics so that and a feedback in infrastructure so you can do user testing and get a feedback loop。

 Then all new stuff will come out in the end sooner or later。And I had shown this。

 done this talk at some internal courses and so on。 And then Daniel did one of his rare interviews。

 the CEO again。With fast company， you've had some pretty successful consumer rollouts。

 like to discover weekly personal personalized playlist。😊。

I would have killed that if it was just me 100%。 Like， why would you have killed it。Well。

 I never really saw the beauty of it。 I questioned them2， three times。

 Are you sure you really want to do this， Why are we spending all this time and energy for a while。

 They given didn't give the team any more headcount， any more funding in terms of headcount。

 But they kept working on it anyway。 All of a sudden， they shipped it。

 I remember reading about it in the press。 I thought， oh， this is going to be a disaster。

And then obviously， it turned out to be something really successful。

 It's one of the most loved product features that we have。

 There are lots of things in this company that I didn't think were good ideas that turned into some of the best things。

 And then it goes on to list these other things。 I think this really shows the power of empower product teams。

😊，It didn't doesn't mean It didn't mean anything that the the hippo， the highest。

 really highest paid person's opinion in the company， The CEO and founder， He didn't like the idea。

 He didn't want to give it funding。 He thought it was gonna be a disaster。But still。

 because the team could use a low cost experiment experimentation way of proving their idea every step of the way。

 that's what ultimately mattered。So it's a hierarchy of competence and customer focused rather than a hierarchy of authority。

So innovation can't be forced， just enabled and encouraged and supported。

 And managers can't make it happen， but they can create an environment to support it and stop it from being killed。

Thank you。

![](img/8f20598b72faea2635f1e315ce0476c5_2.png)