# 【Infosec】用于攻击性安全的ChatGPT ｜ ChatGPT for Offensive Security p08 02_01_03_social-media-and-open-source-intelligence [BV1jPrHBsEv1_p8]

![](img/4383bb123c61b42066853553f6fc8f2c_0.png)

Social media and open source intelligence。In this script。

 we're going to pull some social media posts or simulate pulling some social media posts and then going to interact with the GiHub API。

To pull API data for a target and then analyze this data。

All right so starting off just going to set some variables for this script and then here is a simulated social media post。

 so in real world you would replace this with an API call pull Facebook， Twitter。

 LinkedIn posts however and then populate this array in this instance of just hard coded as a social media post。

Next up going to generate a LinkedIn script that can query the LinkedIn API。

Then going to perform some social media analysis and then pull the GiHub data from the API and then process that data。

 so let's run this script。嗯。Thanks， the first thing we're going do is analyze this this fake social media post。

Also， the first thing going to generate that LinkedIn script。And then。

 and then analyse the social media post。By analyzingnalysing the social media posts。

 here are some points that might indicate potential security lapses。 Have a look at this function。

 Ana social media posts that are analyzingly and extracting any security lapses or information about the target infrastructure。

 can imagine as you've got a whole bunch of social media posts。

 you might be able to get some really good， actionable insights here。

Let's have a look at this LinkedIn posts that LinkedIn Air script has created。

 as I've asked Cha ET to generate a LinkedIn script to intris with the LinkedIn API。

 so it's generated a nice little script here and money to do some imports here to run the script。



![](img/4383bb123c61b42066853553f6fc8f2c_2.png)

They I can。Hela said could be useful。Okay， next thing， we've queried the。

Pointless AI Github Github repositories。 and then putting that data into。A variable。

 So Github analysis calling。Disfunction， get good up data。Okay。

 which is making a request to the Github API for this talkcker。Okay， next up with that data。

 I'm going to processor sending it to this function。

Which is going to assess the company activity based on its public repositories。

After pulling all this information about the repositories， and then。

Looking at what information I can get from there， so data analysis。

Based on the company's public repositories， is is an assessment of company activity and areas of focus。

 ethical hacking and cyber security is analys those repositories and has given you action of insight based on these that you can then use in your further reconnaissance efforts。

Okay so the main way that I've used Ch EPT in this script is by generating a LinkedIn script that can call the API。

 which which come in useful if you want to script this。

 analyzing social media posts if you pull these posts from an API。

 you can then analyse that instead of having to go through all yourself to summarizemar in a report。

 and then doing the same thing with the GitHub data， analyzing that。S。

So let's have a quick look at this get Git update data function I just want to show you the benefits of using H GPT。

And say。嗯。I am。From this data， I'm extracting， I'm extracting the information right。

 so I can I can just print it in response to Jason and so here I go all the data。

The high degree of data integrity， but it's difficult to interpret and' basically just getting like a giant JSON object it's very difficult to interpret。

Here I'm using a JO query where I'm looping through the response using Chat UBT for each repository we get back from GitHub in this J returnturn J containing the Vpo HTML URL and description key values。

 some generating JO and processing it using Chat UBT。In this next function。

 I'm returning the results， but I'm returning it as text。

 so instead of I'm analyzing the adjacent and then I'm returning it as plain text。

And now here we've got our native， So using built in。

Built in function I am processing the data just using just looping through that JN and then printing out the results this has a high degree of data integrity but it's very rigid it for a specific use case only。

So we can combine these and use's a hybrid approach。Instead of。

This where I'm asking chat ET to loop through it I am using code P and code to loop through it。

 but then within the loop I'm calling chat EptT so I'm going through each object in in the array and I'm calling and then I'm passing it to a JOsonN query which makes a chat EBT request So for each each repository return JSO containing the HTML URL description So this has the best of both wordsds It's got high data integrity but it's also very dynamic。

But this also can mean that theyre the worst of both worlds。

 so compromise of availability versus integrity。And finally。

 I've shown it using JQ so you can use JQ to process that data again again it's Richard。

