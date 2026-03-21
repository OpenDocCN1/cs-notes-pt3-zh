# 约翰霍普金斯大学《入侵检测｜Intrusion Detection》中英字幕 - P19：18_Snort快速入门（补充资源）.zh_en - GPT中英字幕课程资源 - BV1sGu1z5E2J

是。

![](img/1594245c822936da05a7782aeeb8f11f_1.png)

I want to take you guys through a quick tutorial that I think will help you a lot with the module4 assignment。

 so in this assignment we're going to be working with Snort inside of the security Onion VM so you can see here that I have the security Onion VM running。



![](img/1594245c822936da05a7782aeeb8f11f_3.png)

![](img/1594245c822936da05a7782aeeb8f11f_4.png)

![](img/1594245c822936da05a7782aeeb8f11f_5.png)

And the first thing you're going to want to do is download the file。

 there's a link to it in the PDF file that gives you the assignment so you can come into your virtual machine。

 you can either actually open up the chromromium browser and just go right to it and download it that way。

 or you can actually just do a W get command。

![](img/1594245c822936da05a7782aeeb8f11f_7.png)

![](img/1594245c822936da05a7782aeeb8f11f_8.png)

And the W get will allow you to pull that file down from the command line so you can just do W gett and then the URL to the file。



![](img/1594245c822936da05a7782aeeb8f11f_10.png)

![](img/1594245c822936da05a7782aeeb8f11f_11.png)

So once you have it， you should have it in your downloads folder， you're just going to do a G。



![](img/1594245c822936da05a7782aeeb8f11f_13.png)

Un zipip。And then you're going to give it the the name of the zip file that ends in dotgz and what you'll end up with is。



![](img/1594245c822936da05a7782aeeb8f11f_15.png)

The actual PCAP file， which is called insidesidet TCP dump。



![](img/1594245c822936da05a7782aeeb8f11f_17.png)

Okay， so once you have the file locally， you're going to run snort and you're going to ingest this file directly and do some packet processing on that file。



![](img/1594245c822936da05a7782aeeb8f11f_19.png)

![](img/1594245c822936da05a7782aeeb8f11f_20.png)

So before you do that， though， I think the assignment mentions that you have to figure out some of the command line switches you need to provide SNorRT in order to help it operate correctly。



![](img/1594245c822936da05a7782aeeb8f11f_22.png)

![](img/1594245c822936da05a7782aeeb8f11f_23.png)

So what you're going to want to do is you're going to want to edit your sNort configuration file。



![](img/1594245c822936da05a7782aeeb8f11f_25.png)

Okay， and the way we do this。S of them。

![](img/1594245c822936da05a7782aeeb8f11f_27.png)

The snort config file is at Etsy。NSM， and then it should have the name of your network adapter here。



![](img/1594245c822936da05a7782aeeb8f11f_29.png)

So that's the JUSP19。Okay， and then snort。com。

![](img/1594245c822936da05a7782aeeb8f11f_31.png)

Okay， so this is your snort configuration file here。All right。

 I'm just going to press the page down key。Until we get to。I believe it's step。5。

Let me just search for D。Okay， so it's right here right on online 170。Let's see this is 1 177 here。

What you're going to want to do is you're going to want to change the。The config D line right here。

 it should probably say PF ring， I think for most of you。

 so you're going to want to change that to PAP。And then optionally， you can comment out these lines。



![](img/1594245c822936da05a7782aeeb8f11f_33.png)

Just by putting a。Pound sign in front of them， so you may want to comment those out。

That's the only change you're going to need to make to your config。Okay and once you've done that。

 we are ready to run Snort。

![](img/1594245c822936da05a7782aeeb8f11f_35.png)

So the way we do this。If we look at the man page for snorrk。



![](img/1594245c822936da05a7782aeeb8f11f_37.png)

Okay， we see a couple things of note， you see that the dash C requires a rules file。

 so this is how we're going to tell sNort to look at the configuration file that we just edited。Okay。

 the other thing you'll notice here is the dash small R。Okay。

 this is how you ingest the TCP dump files of a PC file directly。

 which is why we made that change to our rules file。

 so we're going to need the dash C option and we're going to need the dash R option to run snort。

And then another thing that is nice to do is we're also going to give it a dash V。

Which is verbose mode。And you'll see why in a second why we're going to do that。

 but it will just give you some visual feedback， some confirmation that indeed the packets are being processed by SNort。



![](img/1594245c822936da05a7782aeeb8f11f_39.png)

![](img/1594245c822936da05a7782aeeb8f11f_40.png)

Okay， so we'll do it right here we'll do pseudoto snort。



![](img/1594245c822936da05a7782aeeb8f11f_42.png)

Dash sheet。And we're going to give it the location of that configuration file。That we just edit it。

This snort。com。

![](img/1594245c822936da05a7782aeeb8f11f_44.png)

And dash R is going to be the PCAP file that we want to ingest。



![](img/1594245c822936da05a7782aeeb8f11f_46.png)

And then we're going to do dash V so that we get output to the screen。



![](img/1594245c822936da05a7782aeeb8f11f_48.png)

I't go ahead and run it。And you'll see that it's initializing the rules file。

 it's taking the rules from that file that we just edited。



![](img/1594245c822936da05a7782aeeb8f11f_50.png)

And loading them into the snorre configuration。

![](img/1594245c822936da05a7782aeeb8f11f_52.png)

Okay， so we'll give it a second here。It's still initializing。



![](img/1594245c822936da05a7782aeeb8f11f_54.png)

And after some period of time， after the initialization completes you'll see packets start to stream through。

 so it might take about a minute or so for the system to fully initialize。



![](img/1594245c822936da05a7782aeeb8f11f_56.png)

![](img/1594245c822936da05a7782aeeb8f11f_57.png)

Okay， but you can clearly see that the packets are being ingested and processed by snort right here。



![](img/1594245c822936da05a7782aeeb8f11f_59.png)

![](img/1594245c822936da05a7782aeeb8f11f_60.png)

Okay， I stopped the execution a little bit early just for demonstration purposes here。

 but when the files has been completely processed， you're going to get an output a bunch of statistics at the end of the run。



![](img/1594245c822936da05a7782aeeb8f11f_62.png)

![](img/1594245c822936da05a7782aeeb8f11f_63.png)

![](img/1594245c822936da05a7782aeeb8f11f_64.png)

And the assignment is actually asking you to。To tell us how many alerts were found in the PAP file that SNort just examined。

 so if we scroll up here under the action stats section， you'll see that there's an entry for alerts。



![](img/1594245c822936da05a7782aeeb8f11f_66.png)

![](img/1594245c822936da05a7782aeeb8f11f_67.png)

![](img/1594245c822936da05a7782aeeb8f11f_68.png)

And again， this isn't the actual answer I stopped it a little bit early。

 but it is in the hundreds I think is the answer you should get so if you get something that's much smaller or much larger you may want to run it a second time。

 but it should be in the hundreds so I hope that was helpful Do you guys have any questions please feel free to shoot me note or an email I should be around most of the day to try to help out thanks。



![](img/1594245c822936da05a7782aeeb8f11f_70.png)

![](img/1594245c822936da05a7782aeeb8f11f_71.png)

![](img/1594245c822936da05a7782aeeb8f11f_72.png)

![](img/1594245c822936da05a7782aeeb8f11f_73.png)