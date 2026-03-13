# 【EDUCBA】使用Swift开发一款滑动匹配iOS应用  Develop a Swipe-Match iOS App Using Swift p02 01_02_01_卡片视图设计 -BV1WNFozjEHe_p2-

![](img/62e280e317210264b004e62c80692128_0.png)

So， a。Let's remove this warning。Faiil to instantensiate the default view controller。

You I mean storyboard D。Entry point is not set， so we can set the entry point。



![](img/62e280e317210264b004e62c80692128_2.png)

You can see oh yeah there is no entry point。 that's why we are able to see on black screen while running。

 so you can add entry point from here， select this one。



![](img/62e280e317210264b004e62c80692128_4.png)

Select main story board。😔。

![](img/62e280e317210264b004e62c80692128_6.png)

Is the initial view controller， you can see the arrow。

 this arrow if you place anywhere so that will act as an entry point。



![](img/62e280e317210264b004e62c80692128_8.png)

![](img/62e280e317210264b004e62c80692128_9.png)

![](img/62e280e317210264b004e62c80692128_10.png)

Okay， you can see white screen， why white because。

![](img/62e280e317210264b004e62c80692128_12.png)

![](img/62e280e317210264b004e62c80692128_13.png)

This。呃。Tap bar item 1 and 2， both are white。 you can see if you switch between the two。



![](img/62e280e317210264b004e62c80692128_15.png)

So the typess are changed。

![](img/62e280e317210264b004e62c80692128_17.png)

Now， white it is showing a tint colour as blue。😔，Let's change this select。😔，Okayay。



![](img/62e280e317210264b004e62c80692128_19.png)

Image， didnt。

![](img/62e280e317210264b004e62c80692128_21.png)

Okay。Now you can see image tint tint color as pink。So， let's run and see。😔，Okay。

 you can see the pink color。So this is about tab bar， now let's add the functionality。



![](img/62e280e317210264b004e62c80692128_23.png)

![](img/62e280e317210264b004e62c80692128_24.png)

So， we'll be having。😔，View controller， view controller。😔。



![](img/62e280e317210264b004e62c80692128_26.png)

This view controller will be associated with。Item 1。So， in order to。

Connect both thing will what we will do is we will go to Arent factor and connect the class view controller and hit the enter。

 so which means this particular class and this particular view controller is connected。

Whatever you write code in that class it will be accessible。For U I o U。

So what we will be doing is well be creating different。Profils， they will be say5 to 6 profiles。

And we will be having the user photo。The name and profession and one info button user can swipe that profiles left or right。

After swiping it， suppose I have got5 to 10 profiles after swiping all the profiles at last I won't be able to see any profile。

 so we will display some message。And at the top will display a date and time when we have seen that particular user。

So this U， we are going to design it。

![](img/62e280e317210264b004e62c80692128_28.png)

So well be having one card container view。 So for that crack click new file。



![](img/62e280e317210264b004e62c80692128_30.png)

Saif file， click on next。Sy people。😔，Gard。Container view。Ticcon create。

This creates card container view， so this swipeable card container view will be one container。

U we will have different cpable cards。So let's create a class。Clas。Soy people。G。Container review。

Which will inhert from UI view。😔，Okay， you have you is not available。Because we have not imported。

You a it。Now this error should disappear。So well be having one method override。😔，Okay。

Aake from nib function override function awake from nib， simply call a super dot。Aake from Nb。

 so for cars， we need a delegate， such as when the user is tapping。

 when the user begins swiping and end swiping， so we need to create those delegates。

Wells let's create it。New file。Sit file。Syable。😔，Vi delegate。😔，And click on create。Classs。Swipeable。

😔，View。Deleiate。Import。Foundition。And of type class。Okay。Function。Dt。Function。Did。Begin swipe。

Function。Did end swipe。Okay。😔，Class cons cannot appear protocol O。 So thislu protocol。

We are creating a delegate， so creating a delegate would be。Protocol。Okay， protocol protocol name。

 this we are ining from class， and these are the protocols tip tab。

Did it begin swipe and didnt swipe。So this signature will change as an when we progress。

So this is why people view delegate。Will come over here。 This will inherit over here。

 So I probably we delegate。Okay， we need to conform to this。Simply cut it。Create in an extension。

For better code， s people。Card container view。Cooler。It is gone。Swipeable card container。 O。

 it should be for better convention， swiable card。😔，View container。 So this name is better。

Let's rename it over here as well。😔，Now we require one more delegate， which will be selecting a card。

So， that will be。New file， search file， click next。😔，It will be swipeable。😔，Gard。View delegate。😔，So。

 that will be。Protocol。Soyable。😔。

![](img/62e280e317210264b004e62c80692128_32.png)

Card view。😔，Delayd。Clas。Fengction。Did select。So。😔，This will be modified。

 the signature of this function will be modified， as and when we progress， did select card。

 So this is regarding card。Card selection。 We also needed data source。

 data source like number of card。Card for it index。 And when there is no card。

 So this kind of data source is also required。 So we will add one view。New file。Swift。Swipeable。😔。

Carview data source。

![](img/62e280e317210264b004e62c80692128_34.png)

Click on Cre。Protocol。Swipeable。😔，Card view data source。So， this will be。Container。

Will be providing data source to the soable view container。

Such as all total number of cards and which card is selected and what will be seen when there is no card。

Function。Number of cars。😔，hich should be integer。So， these returns。The total number of cars。

Now what does cards mean cards is nothing but a profile say a profile with a user picture。

 name user photo， name， profession and information， so this is nothing but a card。

 so number of cards will return total number of cards that will be visible that will be available not visible visible will be only the first one when we swipe next card will be visible against swipe Next card will be visible so this will show total number of cards present。

Next will be function。Card。Add index。Okay。😔，Card for。😔，Item at。Index。Index。Andt。😔，So。

 return type you will determine。Say it will be swipeable。😔，Card view。Card， which is not yet present。

Yeah。Okay， it is not present， so you will create this class。

Initially we are we have kept with Norton type， so this function， this particular data source。

 this will return a card for a selected index。And discard width and height will change as per the index。

Function view for empty card。😔，Ui view。😔，Okay。So use of undeclared type UI view， Okay。

 we need UI kit。😔，Okay， so this particular data source view for empty card will display an empty view when there is no cards present。

 that is when user has swiped out all the cards that were present in this app。

So these are the three data sources。We'll use the data source。



![](img/62e280e317210264b004e62c80692128_36.png)

Now， let's create a class which will be of type a syable card view card。



![](img/62e280e317210264b004e62c80692128_38.png)

So， just right。New file。Sft file， click on next and type it spe。Card view card hand click on create。



![](img/62e280e317210264b004e62c80692128_40.png)

So in this， let's create a class。

![](img/62e280e317210264b004e62c80692128_42.png)

Class。嗯。Sy pe。Card， few card。😔，We will add super class later。We will add one required initialr。

So you can see the definition this particular initializer must be implemented but by every subclass。

That is whatever class you create。From this class should always implement this initializer。Coldder。

A decoder。N sr。こ。Super dot ionity。O， super member cannot be reference in root class。Let's use UI Ki。

😔，Okay。And then we need another nicheizer。This should be colder。😔，Let's add one imagela， as well。

Initializer。We will have frame。😔，Cgect。Super dot I。Frim。Frame。This， we are going to override it。

Now we are getting error like initializer does not require overide designally sir okay， first。

 we need to have some super class over here。

![](img/62e280e317210264b004e62c80692128_44.png)

So we will be creating our super class。 so for that thing， let's comment this out。😔。

In order to a thee。Errder， compile diameter。Let's create a unni file for this particular。Class。

Sorightly， new file。Empty。Click on next。Tbe as syable。Card view card。😔，Dot X， I， B。Click on C。



![](img/62e280e317210264b004e62c80692128_46.png)

From this object library， drag and drop Ui view。Now this is this we are going to create a card。

 So for that thing， change the dimension of this。

![](img/62e280e317210264b004e62c80692128_48.png)

So go to attribute inspector。This one。Change size to free form。And change this one， too。33，5。

To4 it dimension。And make sure that authorizing is enable。So this one， this one。

This is so you can see oh it will expand and collapse as for the screen size。

If I remove this and this， you can see。When it is expanded， it will be like this。Now。

 let's bind this Nb file with the shift file。So go to identity inspector in this enter the file name。

Syable。Card view card。Copy hand paste。😔，Okay。Let's change this background color。These two。Customom。



![](img/62e280e317210264b004e62c80692128_50.png)

So this class and N file is created。 Now， we will create the classes that are required that is。

We should create spepable card view。So let's create that class rightly。New file。



![](img/62e280e317210264b004e62c80692128_52.png)

Suit file， click on next。Syable view。And click ont create。Classs。Soy people。Poview， which will。😔。

Which will subclass from UI view。😔，Use of undeclared type U view。 Okay。

 we can when to do this with U Y kit。😔，And this will have。Required initializer。Super dot。I I。Yeah。嗯。

哎。😮，Overrightide initial slicer。Yeah。Frame Cgect。Super dot I I。Frame as frame。 This one。

 we are going to override it。From U view。So now in this class， this in this class。

 this particular block of code doesn't throw an error because this has been inherited from U I view and U I view has got。

This particular method and this frame method， hence， it is not throwing any o。



![](img/62e280e317210264b004e62c80692128_54.png)

what is the difference between required initial slicer and overhead initial slicer？

A required initializer indicates that this particular initializer to be mandatory used by a class that inherds spable view。

Whereas over initial means。This will override the initializing the frame of superview。

We will require an instance of。Deeleiate。And with the delegate that we created is swipeable。

 view delegate。Make it as optional。Now we will be creating different variables。That are required for。

Gestures and animation and those things we are creating。😔，First， we will deal with。D recognizer。



![](img/62e280e317210264b004e62c80692128_56.png)