# 【EDUCBA】应用Chef实现云基础设施项目自动化 ｜ Apply Chef to Automate Cloud Infrastructure Project p09 02_01_02_创建食谱 -BV134F1zaEdz_p9-

Now， let's see how we can implement the use of cookbooks。

 So cookbook is like basic building block of your chef。 Every recipe should reside in cookbook。

 So you should be aware of the cook structure。 Well。

 I'm going to create one directory called cookbooks。 So I will just create cookbooks here。

The director is created。 Let's check。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_1.png)

So we have cookbooks directory here。 Well your cookbook directoryies where you keep majority of your cookbooks if you are going to run your cookbook in local mode So whenever you have some local mode changes So all your cookbooks and recipes should reside under your cookbooks directory under cookbooks director you can just make lot of other cookbook as well So now I'm ready to generate a cookbook inside cookbooks and which can create from scratch So the simplest way to get started is to use the chef generators So now we'll see what is Se generators well your chef command comes with your chef development kit So whenever you type chef right。

This is a Se command and when we have installed Che client right。

 so it comes with your Che development kit， so in run if we just mention Che I and I and help。

 you'll get to know how we can bring all our changes inside cookbooks。To just generate a cookbook。

 So just mention help。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_3.png)

And you will see the options here。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_5.png)

This is a very powerful tool。 Now， it tells you what type of help it can do like。

Excuse things generate。 So here I am using cookbook to generate a cookbook。

 So I'll be using this generate keyword。 So you generate keyword and from your command prompt。

 which will allow us to generate cookbooks or cookbook components to understand how to use this command I can just run like。

Chf。Genrate， just put hyphen have and help。 So it will tell you。

What all things you can use by using generate commands if you put this youll get to see all those options here。

 So we'll let print out all the applicable generators。

 but right now we are interested in generating a cookbook It's here。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_7.png)

![](img/f487f8aa054dd468cd2d5e52df38c3cc_8.png)

And later on， we can generate other things like other components。 Now， let's check Seph。Generate。

And what we have to generate， we have to generate a cookbook。So cookbook we have generated now。

 if you don't have any idea what to type next， just put help。

It will shows us what all help you can get with a key called cookbook。 So I am just passing this。

 Well， it will tell you how to generate a cookbook which is simply to provide a name here。

 if you see here， Che generates cookbook with name options。

 you just put the name here and so in order to generate a cookbook。

 just mention Che generate cookbook followed by the name and when Will are mentioning the name it will be followed by the path of the cookbook。

 So we will run the generate command。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_10.png)

![](img/f487f8aa054dd468cd2d5e52df38c3cc_11.png)

And it will also tell where to generate the cookbook。

And we will create this cookwood inside the directory。 what we have just created now。

 that is cookbooks， which will be， will name it as chef workstation。 So what I will write。

 I will write chef。Generate what to generate cookbook。And where to generate。

 we can just sew inside this cookbook directly， we just put the name of our cookbook。

 and I call this self Se workstation。And by running this command。

 well see the info here and let me edit this。 it should be cookbook here。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_13.png)

![](img/f487f8aa054dd468cd2d5e52df38c3cc_14.png)

No。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_16.png)

A guys have our cookbook has been generated。 So in the information you will see Git branches here and by default。

 gi is used to track all changes what you're making in your cookbook so you can just check this thing it should somewhere it should be in like。

Get is there。 So if you mention here。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_18.png)

Committing cookbooks files to Git so get is the default version control here for whatever changes you are making it will go to git So your cookbook it is ready。

 So now you'll be probably wondering how you would execute a recipe which resides inside a cookbook because previously we just execute a recipe just not inside a cookbook and while running the recipe we whenever error warning exception like you don't have a cookbook directory So now what I will do I will just move out the files。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_20.png)

And I will place this file inside this cookbook。 So let me do Alice。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_22.png)

This is my cookbook。So what I have to do， I have to move this file。

Dot first recipe dot R file into our cookbooks directory。 So for that。I'll be using moveve command。

 move。Where to inside this。And the name of a cookbook is your Che workstation just here and where it should move。

 it should move to your recipe directory。Two recipes。Now， youre。 Now you're good to enter。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_24.png)

So。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_26.png)

If you see Ls minus here LD， you won't find that。Recipe it should be inside yourbooks。

 just CD cookbooks。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_28.png)

Do Alice。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_30.png)

And you have to go to Che walktation because this is the direct structure we have created。

And this C workstation has been generated by the generate command。

 So if you do L Pen C you'll see a lot of directory structure here。

 So these data we were created once we use Che generator that is came from your Che development kit。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_32.png)

And if you go to recipes， youll find recipes here。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_34.png)

Dois and our recipes here。 and it is there is another recipe also that is defaulted RV。

 which well talk later about it。 So just go back here。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_36.png)

And it's time for us to run our recipes， So what is general method you can just like we did earlier。

 you can just mention shdo。

![](img/f487f8aa054dd468cd2d5e52df38c3cc_38.png)

Chef hyphen client。Ihon， iPhone， local mode。And then you have to provide the location that has cookbooks。

😔，And this location， surf orchestrat。Then you have to put the recipes file。

And where recipes inside recipe you have to put the name of the file what you have just so so if you want to run this。

 then you will probably be thinking that this will run。

 but this command will not run because now we are we have inserted this recipe in a cookbook so your C client and theres other recipes as well that is defaulted RV。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_40.png)

So you are probably your self command， it will be confused which one to use and this is not a default way of mentioning and executinguding a Se command。

 So if by actually I can't execute this individual recipe file because the recipe can call on other recipes。

If by default I want to run my defaulted RB file whenever it a a safe workstation cookbook。

 so what I will do I have to mention this my first speed RV inside this defaulted RB file。



![](img/f487f8aa054dd468cd2d5e52df38c3cc_42.png)