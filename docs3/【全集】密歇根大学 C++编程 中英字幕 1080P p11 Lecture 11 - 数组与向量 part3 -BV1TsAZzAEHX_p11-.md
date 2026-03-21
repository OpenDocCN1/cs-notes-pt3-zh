# 【全集】密歇根大学 C++编程 中英字幕 1080P p11 Lecture 11 - 数组与向量 part3 -BV1TsAZzAEHX_p11-

![](img/e1e0a6021328e1f91c111c57045d41aa_0.png)

Oh， happy Wednesday。 Oh， I didn't even log in all the way。I'm trying to get there。

 So to pull up canvas。 Sorry， thought I was ready。诶。

Think we should be in pretty good shape to finish up raising vectors to day。

We got through almost all of it last week， we're leaving a couple things for this week here and we'll do a little more practice we call it visualual Studio。

对。

![](img/e1e0a6021328e1f91c111c57045d41aa_2.png)

So we've got weak taners and vectors thats we'll start with that one。

 I just's keep adding to it here。

![](img/e1e0a6021328e1f91c111c57045d41aa_4.png)

Yeah。All right。So we looked at having like these parallel vectors so we could store information and then the indexes would match and think is where we left off here so other fun things we can do with vectors here I you can do the same thing with a arrays but if you're passing them in the functions you just have to also pass the size and that gets a little bit obnoxious here so something you might be able to do is say hey I want to get an integer value of the max value given a vector of type end here call numbers。

So if you give me a vector of numbers， a list of numbers here。

 I'm going to tell you what the largest value is。So to do that。

 you need to look at every number so if someone just reads off a list of numbers to you。

 what are you doing in your head to figure out which is the biggest number？So if I say 7，2， 29，5， 30。

24，9， well， what happened in your head？To figure out what the biggest number was。嗯，对。喂那个必。

Yeah you're going to write to code， you're just skipping your head or do you think in code in your head？

Yeah， so we， we， we compare them when we know which one is the largest And every number we look at。

 we say， is it the new largest。 starting with the first one， so our largest value。

Is probably the one at zero until we know otherwise。Right。

 and then we're going to loop all the way to the end here， so we're in index。

Is one right you don't need to start at zero， you could if you want to save some typing do the the regular loop here and to say。

 you know for value into value in numbers， that's fine too you've done one extra comparison。

 which no one actually cares， but most people start at one because it's。You know。

 nanoseconds faster to skip one comparison， that's why， say， hey。

 if my largest is less than the value。Right， so if the value is bigger than the largest right you can write it either way。

 I guess right if the value is larger。sL than the largest， we now have a new largest。

Lrgest is equal to the value over were done in return to largest。look at every number。

 if we find a bigger one that's not the biggest。It works the same way for minimum we just flip it we're looking if it if we find the one that's smaller right so max is pretty easy for getting numbers out how about a average。

😊，Given a vector of integers。Numbers， right？We just add them all up divide by the length right。

 so we have a in total starts at zero and for valued value。

And numbers we'll just add to it the total。Plus equals the value， we're done。

 we can return the total divided by numbers do size。

Now we want to be a little bit careful here because that is an integer and size is also an integer。

Are we going to get the number we're expecting out here if we take an integer divided by an integer。

 so we want to make sure one of these is a double here。

 so probably total should be a double that we actually get a double result。Right。

Because if one of our two opera ends is a double， then we'll get a double result here。

 so just want to be a little bit careful that when you're adding integers， it is an integer total。

 but you want to make sure you get the double result。So average is pretty good。

 min max those are pretty good to follow here。What if we wanted to sort a list this one gets a little bit trickier。

 you get into sort， I think there's a whole chapter on it later and there're searching and sorting algorithms。

 we're just going to steal the easy one here because it's a fun example to look at with vectors and we're going to do the really naive。

 slow， lazy approach because it's the easiest one to code。



![](img/e1e0a6021328e1f91c111c57045d41aa_6.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_7.png)

Right and that's okay， it's not not the end of the world here there's much better ways and you' we'll spend lots of time looking at those eventually for now if we wanted to sort one here。

That's just avoid function。 I don't need to return anything because I'm going to be changing the vector you give me。

RightI'll modify it in place here， so I don't need to return any values here。

 we'll call this sort of vector event。Called numbers。🤧So excuse me。Yeah。

The two basic ones that the book gets into here， you have a selection sort and an insertion sort。

We're just going to do the selection sort and that's easiest to turn now well again what we can come into those later。

 I don't think we cover any of that in this one here I think we stop at pointers。



![](img/e1e0a6021328e1f91c111c57045d41aa_9.png)

We stop with pointers， so it's available to you。Um。At the end of the semester。

 you want to make sure you save all the chapters， you can print them to PDFs because。

When we teach 200， we use Zybo again。But we don't have like the Zab stuff and at least when I teach it I don't give points for going through the chapters。

 it's just like a reference material at that point because you've already done it all for 150 and that way you don't have to buy it again。

But we use the same content and we finish the rest of the book here and then usually there's some supplemental stuff were like hey go go look at this textbook because there's a couple in the library if you want more information。

 at least when I teach it and I think that's what everyone does because that's what they tell us we're supposed to do。

But academia is kind of weird and you can do whatever the hell you want sometimes and I don't understand this place。

 but that's okay so make sure you save all the chapters to PDF you'll get to all this other stuff eventually here next semester we spend a lot more time on inheritance and pointers and recursion templates and containers and searching and sorting those are some of the major topics we get to next semester so save your chapters put them to PDF you can always open them up later with not then you don't have to pay for the book again right Okay so a quick way to sort so the naive way is we can just go find either the biggest number or the smallest number and put it either at the front or the end。



![](img/e1e0a6021328e1f91c111c57045d41aa_11.png)

you want to take all the biggest numbers first， you have to take all the smallest numbers first？

It really doesn't matter， we can go either order it biggest first， okay。

 so we're going to do is we're going to find the biggest number and then we're going to put it at the end。

And then we're going to look at。Everything except for that number and find the next biggest number and put it at the end minus1。

And then we're going to find the next biggest number out of the rest of the numbers。

 but at the end minus2 and minus we're going to work our way back building out this sorted portion of our array here by finding the biggest one and putting it there so we have to go get the biggest number we can't use this function we sort of can for the first one but it's not useful after that because I'd want to ignore the last little bit that I've already sorted here is the small problem that we have so what we generally do is we do this in two loops here so we have our first loop here so we're going to say for in index is now we want to start at the end。

Here， so I want the size-1。 Remember if I have five numbers， my size is 5， but I have indexes 0，1，2。

3， and 4。Right， so I want my last index。 So my index is going to be my numbers dot size-1 here。

 And I'm going to go as long as index is greater than。One here。Or greater than zero。

 sorry greater than zero is if I've sorted the fifth spot and the fourth spot and the third spot and the second spot。

By putting the biggest number here， the next biggest number， the next biggest number。

 the next biggest number， I don't have to do anything with index zero。

It it's already sorted right so I can stop when I get to zero。

 I don't need to do anything with zero so I'll stop when I'm greater than zero so nothing happens that last time and we're going to do is we're going to take index minus minus I'm going to go go down one every time so we're going to get four and then three and then two and then one and then we're going stop。

Right。So that's our outer loop here， so this will be where we want to put the number here so this is the index to replace here although we'll do that so index to replace。

Index to replace right's the that's the one we're going to put the biggest number in。

Or we can even name it like that。 Let's， let's do that。 So this will be the index to。But biggest。

The index to put the biggest。食。Hopefully clear。 and， we can name it whatever we want。 It's our code。

 right。 Then we need to do is go find the biggest number。

RightSo we're going to loop through finding all the values starting at zero going up to and including this index here。

To find the biggest。Right， so we need to find the biggest number then so we have an int。

Biggest value I will just say biggest rate is going to be my numbers do add zero until and otherwise it's the first one right and then let's go loop through so now I want to use indexes here I don't want to use looping everywhere because eventually I'm not going to look at all the numbers I'm going look at all the numbers minus1 all the numbers minus2 all the numbers minus3 all the numbers minus4 right we're going to restrict how many we're looking at each time here so this will be for in index to compare。

Starts at zero， my index to compare is less than my index。foot the biggest lesson or equal to。

As I can go compare up to that number here。And then my index to compare。Plus， plus。

 so this one increases。It's a little long here sorry but again i'm zoomed in this would fit on your screen without having to scroll left and right so we're going to say okay if my numbers at my index to compare。

Is greater than the biggest。Now what I actually need to be tracking though is not just the biggest number I need to know what index it's at because I need to hold on to that number because when I've looked at all five numbers what I'm going to do is just swap the two places so if the biggest number was at index1 and I need to put it at index4 I'm going to take what was index1 and put it where index four was and just swap the two numbers so we need to store the index here not just the biggest value here so I'm going to rename this one here。

 this is the index of biggest。And that just starts at zero right it's assumed to be the zero with index here。

 so if the numbers at the index to compare is bigger than the numbers at the index of the biggest。

 bless you now we have a new index that we're tracking because I know the value at that index was bigger。

So we're going to say， okay， my index of biggest is equal to the index to compare。

So if we draw this out here， sometimes those even is draw out。



![](img/e1e0a6021328e1f91c111c57045d41aa_13.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_14.png)

I like drawing with word， because I can't。So if we have， so shout out five， oh my good。

ness five numbers for in here。What number should we try？Six， six。7，7。F， who's going to do it。

 come on， somebody， my teenagers would be proud。No no right it's dying soon now that all the old people are onto it right it's not fun anymore it's like hey。

 even Stephen Colbert does this oh goodness， please don't all right what else age eight give me someone smaller。

2。4our， okay。So our first loop says， okay， we're going to start here with index number four right so we have indexes0 one。

2，3， and 4。 So we're starting with index 4 because that's where we're going to put the biggest number。

 Then we're going to start back at the beginning and start comparing here。

 So this is our next to compare， so。I'm going need to eventually swap the biggest number into index4 so we say okay。

 what's the biggest number well must's start at index0。

 the biggest number is at index0 it's6 and then we say okay is the biggest number now at index0 or index one。

The biggest number is now at index one right so our biggest index is one I say， okay。

 is the biggest number at index1 or index2？That's it index 2 right is the biggest number at index 2 or index 3 still index 2 didn't change is the biggest number at index2 or index 4。

 still in index 2 didn't change Now we swap， so we're going to take what was at index2 to put it at what it was index 4 so we could swap the eight and the4。

And then now my index to swap。Here， my biggest indexes。

Is now index three so we're done with four so this portion is sorted here that's my sorted portion and now we start back in the beginning okay index zero is the biggest is index0 bigger index one bigger index one is bigger is index one bigger index two bigger index one index one or index three index one and then we're going to swap the seven and the two okay swap the seven and the two。

Now， the next one we have to swap into is that index two。Okay， what's the biggest index， zero sure。

 one， no， two， no， okay， let's swap， so we swap the six and the four。

Now the next one we're looking at here is index one。Okay。

 now I'm going to try and find the biggest number to go to index one， is it index zero index？What？

It's in ex zero， so it' swap the values there， so we swap the four and the two。Two and4。

 and now sorted。Okay， so index to put the biggest， right？😊。

Eventually we'll find the biggest value here， and then we have to go swap those two numbers。

 so I have the int。Temp will say is my numbers at the index to put the biggest。

indexd of the biggest shirt that's fine either one could be the temp one and then we need to go change the value so I've stored what was there now I can change it to my numbers at the index to put the biggest。

 so grab the biggest number here。Just a head hold onto it and then replace it with what was where we're going to put it。

Then I can move my numbers with the biggest。And put T number there。I me what was called biggest？

put the biggest number there， so that's the swapping bar Okay。

 and then we go back and we decrease this one I want Okay。

 now we're going to put the next biggest number here。And we do it again。

 go find the biggest number and then we find go to the next slot find the biggest number go to the next slot so the problem with this is it's incredibly slow because if you've got 100 numbers we had to do 100 comparisons and the 99 comparisons and the 98 comparisons and the 97 comparisons and 96 comparisons and 95 comparisons right and you've gotten far enough in calculus you know the shortcut for how long it's going to take how many operations it is total n times n minus1。

😊，Right。Yeah， yeah， obviously， we learned that one from calculus。Yes thank you。

So n times n minus one right if you do something。not factorial because you're not multiplying it's just plus right。

 so 100 plus 99 plus 98 plus 97 plus 96 plus 95 plus 94 plus 93。Right， that's our shortcut。Okay。

So it's incredibly slow， but relatively easy to understand， right， find the biggest one。

 what are the we at。Find the next biggest is one what do they at minus one so it's a quick easy sort here so we'll call this on our selection sort now problem with this one is。

If the ray or the vector is already sorted， we still have to do that many comparisons because it still has to look at all of them be like。

 oh okay， you are the biggest numberr and if it is， it swaps with itself。

 if the biggest number was at the last index， it swaps with itself， nothing really happens。

But it has to do all of the comparisons anyway， right？Excuse me， the other kind of sort。

 which is a lot of fun here is a insertion sort so we're going to。

Slowly move the numbers into sorted order， we're going to insert them into the position in the sorted portion of the list rather than selecting the biggest and moving it。

It's not all that much different， but it's a little bit different here。

 so we're going to call this one our insertion sort。Given a vector Let willll call the numbers。He。

 you know what， instead of commenting that， I'm just going to call it selection sort。

Look at that and then I don't need a comment telling you that's a selection sort。

I that's so much nicer。谢谢。Okay。Comments are stupid。In my opinion。

 right when you get to the next class and someone tells you have to put comments and just smile and nod。

Don't tell them Eric thinks they're stupid， but that doesn't go well for me。

It doesn't go well for you either。So the insertion sort， excuse me the idea here。

 let's let me slide numbers again here， let's do a different list here of numbers and we'll work through the insertion sort。

So give me five numbers。是。嗯，对。Right，3。😊， five。1。Heat。s one， six。Sorry I heard six first Okay。

 so the insertion sort says we're going to make the sorted portion larger by inserting numbers into these sorted portion and what we can do is we can say okay。

 I know。The first number is sorted。Now all by itself。

 this is now the sorted portion of the list here， so all I need to do is grab the next number and put it in the correct location in the sorted portion and to do that all we need to do is start swapping so if it's smaller than the number before it。

 we just swap their places。So it's five smaller than three。

No we're done so now my sorted portion is here right I have two numbers sorted okay and then we go to the next one now we need to insert this value into the sorted portion and all we do is we start swapping it backwards until it's no longer less than the number before it or it reaches the end right so is one less than five Yes okay。

 so we swap one in five。You say， okay， here's the one， here's the five is one less than three， yes。

 okay， so we swap one and three。One and three， if we got to the end， we're done。

 So now my sorted portion is three numbers long。I I go to the next value is eight less than five。No。

 okay， so we're done now it's sorted is six less than eight， Yes， okay， so we swap。So we said， okay。

 let's move the six， move the eight。Is6 less than5。 No， okay， it's done。

 Now my sorted portion is the entire list。 we reach the end。 So with this one。

 if the list is already sorted， it's much faster because all it has to do is say， okay。

 do you need to swap No， do you need to swap， do you need So the fastest it can run is you know。

 if I've got 100 values is 100 comparisons。 How often do you get a sorted list that you have to sort not very often So。

It doesn't matter that much here， but in general， this is a better performing sort than the selection sort。

In general， if it is reverse sorted， then it takes just as long as the selection sort because every number has to compare itself all the way back in the list here right so the one has to compare itself all the way back to the first visit this direction right if one's at the end it has to come all the way back to the start and the two has to come all the way back to the start and three has to come all the way back to the start。

It's slow if it's reverse sorted， but in general this one's a little bit better here。

 so we're going to start with the index to sort here， so we're going to say for int index to sort。

Okay。Starts at one， right because we know zero is already sorted here。

 And we're going to do that as long as the index to sort is less than my numbers dot size。 right。

 We to do go all the way to the end here。 type my index to sort plus plus。Okay， excuse me。

If it's less than or while it's less than the value before it， we want to keep on going。

we can use loops here and usually the loop is easier because you could use the indexes here。

 so we're going to start at the index we're sorting here and we're going to go down to zero actually we don't even need to get to zero right we just need to get to one。

Because if I swap with index0， I'm done。 There's nothing left to do that。 So I'm going to say for。

this is the index to swap。Starts at the indexed to。Indexed to sort。So starting at the index。

 we're going to sort。We're going to start decreasing here if we need to swap here。

 to go and allow our index to swap。Is greater than zero or take our index to swap minus minus。好的。

And we only needed to do this。If the value is less than。

RightThen we need just swap otherwise we can stop this loop here。

 so that's why the while is's sometimes a little easier。Yeah。So we're going to say if my。

Numbers at the index。That we're swapping if that is less than the numbers at the index to swap。

Minus1。Because we're always looking at the number before it， the index before it here。

 So starting at one。Right， iss it less than 0。If it is， let me go ahead and swap here。

So we do this temp thing here， so an image temp is my numbers apps my index to swap。

And then take this one， assign at that value。No， sorry to take this one， sign of that value。

And then we'll take the。Number here and assign it depth。so it swaps up right。

 grab the value where we are swapping， place it with the thing before it。

 take the thing before it we' replace it with that temp value， right？Now， if it's not。

my else case here， we just want to break my loop。Top before loop。

Right because I didn't have to do any swaploppping I don't need to do any more comparison。

 so again I think brakes are ugly a while loop we could use instead of using brakes。

 but this is this is okay toom as sure should work for us here and that's all that does。

 so we just work our way back to the front here as we're increasing the number that we're sorting the index。

So start in index one， sort it if it's less than index zero swap right then look at index two。

 if it's less than index one swap， if not you keep on going index three is it less and is it less is it less is it less so it should swap them back as we go here。

So if we get our vector events。And numbersumb to sorts。

And we can use this little syntax here with our curly races to say， hey。

 what were our numbers here we had four and seven and six and nine and two or something I forget what they were here。

 that's all right。and I wanted to print those out here， see out my numbers to sort。

And then we sort them here， so let's use our selection sort given our numbers to sort。Oh， I can't。

 that's right。 You can't just output a vector to save for。And value in my numbers to sorts。

Dot I have like a print， let's write a function here for a print vector。After' on one line。

Given the vector event。Ners， there we go， so for value。In numbers， see out the value and a space。

 and then eventually we can add our end line here。that'll put them all in one line for us right。

There we go， I'll print out whenever to sort。We'll sort them。And then we'll print out our vectors to。

Again， here。Mction one works for us。

![](img/e1e0a6021328e1f91c111c57045d41aa_16.png)

Let's try it we haven't actually run the code yet， we wrote a bunch of code。

 we didn't run anything yet， that's kind of boring。



![](img/e1e0a6021328e1f91c111c57045d41aa_18.png)

哦。Didn't sort anything。They tried our selection sort。Put it in the sort。Let's take a look and see。

 so go to our selection sort。Add a break point and run it the debug quote， see what it's doing here。

All right， so we got our numbers。Right，4， seven，6，9，2。And it does some stuff。

 It does some comparisons。Does a swap， okay， now the next one finds the biggest number。对。

Finds the biggest number， swaps。Oh oh， I went too far shoot I got too excited， sorry。Too many clicks。

 let's put it down like here because we want to just watch the swapwas。Con continue。

 so here's our numbers here， so we have the nine in the right spot。Now the seven is the right spot。

 out the twos in the right spot。啊哦。Didn't finish right， what happened here？Right， four， seven， six。

 two， two。Oh， we already swapped， that's right， okay， so to continue now the nine of the two swapped。

Do we swap， we put the wrong one there， didn't we？嗯。Let me change here， we had4，7，6，9，2。

Now there's an extra two， Oh， I'm sorry。I should put it here before we do the swap， there we go。Okay。

 so now the seven is here， four two six， seven， the next one here we've swapped six didn't swap。

 nothing changed， right？

![](img/e1e0a6021328e1f91c111c57045d41aa_20.png)

And then the four and the two should have changed， but nothing changed。



![](img/e1e0a6021328e1f91c111c57045d41aa_22.png)

Oh， we didn't pass the reference to the vector。we just passed a copy of the vector。

 so we need to say， hey， this is a reference here， not a copy， sorry， my mistake。Yeah。

That was a big issue。

![](img/e1e0a6021328e1f91c111c57045d41aa_24.png)

Now when we run it， we get oursorted list as I passed it the reference and then pass it a copy。



![](img/e1e0a6021328e1f91c111c57045d41aa_26.png)

So the selection sort works if we do it right， lets try with the insertion sort。Aserion sorts。



![](img/e1e0a6021328e1f91c111c57045d41aa_28.png)

24， six seven9， it worked。

![](img/e1e0a6021328e1f91c111c57045d41aa_30.png)

All right， so we're able to sort our vector here。Using the selection sort， the insertion sort。

Getting indexes， swapping values here， having some fun with them。



![](img/e1e0a6021328e1f91c111c57045d41aa_32.png)

All right， the next little bit here， So this was a whole bit to。

To the swapping swapping new variables here right another fun thing we can do is you can make an array of arrays or a vector of vectors these are my favorite here so a vector of vectors again I prefer you can use the array of arrays that one works to here。



![](img/e1e0a6021328e1f91c111c57045d41aa_34.png)

we're going to make， let's make a board here so we can have a vector。Of type vector， of type cha。

 So it's a vector of vectors of characters， So we'd like to think of these as rows and columns。

That makes life easiest they're not actually in rows and columns because it's here's a vector of characters。

 here's another vector of characters， here's another vector of characters。

 here's another vector of characters， but if we stack them and say here's the vector and then here's a vector and here's vector。

 we have rows and columns and it makes sense the way we visualize it here so call this our board then it's going to equal an array array of arrays or a vector of vectors here so I'm just going to put some spaces in here。

I want going to do some characters。So there's the first vector right and then the next vector。

 why is the spacing here so bad， and I'll take this one down there we go。Let's do this one here。Yeah。

Right， and then one more。That one here， and then the whole thing ends there。

Those didn't line up nice at all， goodness， there we go。

So the first item at index zero of the outer vector is another vector with three spaces。

so to get at one of those positions， I'm going to say the board at zero gives me row0 do at。

0ero gives me column zero the first item there right00 right， this one is 01， this one is 02。

 this is10，1，1，1，2，2，0，2，122。rowow two column two， again， they're not actually columns。

 so it's easier to visualize this way here， so we're going to start start a board here。

And if we wanted to play T ta toe。We play Tiact toe， right。

 we can play as long as the game's not over。That's sort of how you play tech to， right so while。Not。

Game over， given the board。Well， let's keep on playing here。

Right and we probably have a horse person turn of this， right， so turn recurren player。

Char for current player。X usually starts right， so if X be the current player and while the game isn't over。

 let's。Make a move right so let's mark Mark forward and we'll tell Mark board who the current player is and we're going to pass the board and we're going to make all these functions pass values here right using globals is a little bit messy here so we're to pass all of our stuff here we'll mark the board。

Right after we mark the board。It goes to the next player。Great。

 so then now most people would say if the current player is X。Then the current player becomes oh。

Otherwise， the current player acts。If you copy paste from ChatGBT here。

 your code will look like this， say cur player equals x。If my current player is equal to。Oh。

 otherwise。These little turnernary expressions， remember I mentioned these， these are ugly suckers。

 ChatBT loves these。When students give me this kind of code？I know they didn't write it。

 Im just going to be honest I hate writing these things， these irritate me like crazy as they suck。

And no one understands， what do I put first， like why is it backwards， this sort of garbage。

 so if the players O becomes X， otherwise it becomes X。No， that's wrong， isn't it， it should be oh。

 isn't it see， I screwed it up。If the current player is O， it moves to x。

 if the current player is not O， it should move to O there we go， these are confusing。

 why do you put them in the backwards here anyway we change player。And we keep on going。

Maybe we want to print the board at some point too， right， print board。

Given the board and then we mark the board and we change the player if the game's not over。

 keep going， keep going， keep going。we're doing our functional decomposition。

 throw it out at your Thanksgiving party， it'll be a good time。

 everyone look at you like you're crazy。To smile， you're nerd。 you own it。All right。

 so to print a board， right， so avoid print board。对。Given a vector。Of vector of char。Lord。

I want to print。The first row， and then a new line， the next row， a new line the next row right。

 but I want to add in the cool little dashes to make it look liketic tae right we're playing T ta toe sorry I think I mentioned that right。

Now， we could do this really smartly here。They don't really need to do a bunch of loops here。

 it's not all that helpful to do a bunch of loops here。

 so I'm not going to bother so we're going to say I want to see out。My Lord。At zero at zero， right。

 here's the first one。And then I want to add a pipe character to make the little straight lines here。

 right， and I want to add01。Another pipe character。And I want to add zero two。😊。

And then when I add an deadlineline， go down line。Then I want to output a bunch of dashes here。

I think it's five， right， one， two， three， four， five right the character above， the dash。

 the character above， the dash， the character above。Right。😊，And I want to do this again for row one。

And the new life。And fine， right， so now it's row1。Row 1。Row1。And I want to do this line again here。

对。Right， and then I want to do。This one， now I want row two。Again。

 I'm sure we could come up with a loop to do it here， but I don't want this after the third row here。

 so like your loop gets a little bit funny and this isn't too bad here I only feel a little bit bad about it Well that should print board。

Great。All right， now we can print a board。How about game over so that's a boolean value right we're telling you true or false the game's over sorry。

诶。人哋咩我先要。Its is equal to doing。그도 이데。如果你不理备。嗯嗯。There is a conditionary。So you do the assignment。

 then the condition， and then the else， if I remember， right？有。I think equals x then it becomes O。

Otherwise， X， okay。Wow， I didn't give me an error then all right， cool， see I hate these things your。

It's the turnernary expression， so it's the single line F else assignment。

So it lets you say I'm doing N else， so here's if this one else， this one。They're ugly。

I hate them and I don't remember how to use them apparently。

I usually have to go look up and that's why I hate them anytime that makes me like stop and think。

 I don't like it， I don't like to think。All right， so I'm game over then。

Ge over now given a vector vector aboard。There are two different ways the game can be over。

 right You can have a winner or you can be tied the cats game I don't know why it's a cat's game my cats on the how to play Ti tato。

ButS we call it catth game。 So if either one of those is true， then the game's over。

 so we're going to return。Is tied。Given the board？Or。Has winner。Given the board。

Functional decomposition， right， it's hard to know to do both。 so let's break it apart， right？Oh。

 we can do that， so it is tied given a vector vector aboard。Now， we know it's tied if。

There is no space。And there's not a winner。But really。

 we don't particularly care if there's a winner， we just care if there's not a space。

So what we're going to do is we're going to loop through and see if we find a space we're not tied。😊。

Right that's our easy way， so we're going to say for this is a vector of char。

 we're going to call the row in the board。And then for char， I don't know， bot in the row。

Right because the board is a vector of vectors of character so I can loop through every row of the board and then every row is just a bunch characters right like column maybe call it column。

 I guess sure， if the column is equal to a space， that can turn false。

we are not tied because I found a space， there's room to play if I've looped through all the columns and all the rows and it didn't return false and it must be tied and return true。

Yeah。嗯。Again， we don't care if there's a winner here or not， this doesn't check for winner。

We're just being lazy here because our we are just saying game over。

 we're going to assume when we print the board， you can tell if there's a winner or a loser。

We don't need to say someone volunteer or game game over it got tied。

 we're assuming people can figure that out here， right， then it has winter。As winner given the board。

 sorry a vector vector of char for the board here。Now this one， you can either win by row。

 you can win by column or you win by diagonal right so let's break it apart so let's return has winner by row given the board or has winner。

I call them。Given the board or as winner by Diagonal bye。Paagonal， given the board。

 if any one of those are true， someone won。Right we're just breaking into apart。

 so let's do the head winner by row first， that's this one here。As winner。I row。For that to be true。

 every character in the row must be the same and not a space so we're going say hey。

 for a vector of char row in the board。She。If my。Row at zero does not equal the space。

Not a space and my row at zero is equal to the row at one。It matches right and my row at zero。

His mat matches the row at2。If that happens， right， then I can return true。I found a winning row。

 right， It's not a space。 The first match is the second， the first match is the third。

They all match I've found a winner if I checked every room and I didn't return true， must be false。

That's winner by row。Has winner by column。Is a but different， right by column。No。

I need to loop for every column and check every row here， so it's a little bit different。

 so we're going to say for int， this is my column index， starts at zero my column index。

It's less than three right or board dot size or I mean we know it's three。

 so I feel there'll be board dot size here。Column index plus+。W。

We're going to check column zero and we're going to check column one。

 we're going to check column two。So if my bo dot at， now。

 I'm always checking row zero at the column index， right？So it's always row zero。

 buts the column index is going to move from column zero。

 column1 and column two right if that one does not equal a space right and。This one。Equals。Row 1。

 same column， right， row zero then matches row1 at the same column。Right， and。是。

Row zero matches row two at the same column。If all of that was true， I can return true。

If I didn't return true， I checked all three columns， I can return pulse。

Theyn't try to win my column right， so column is the thing that's moving here， column zero， row 1。

01 and two。Column 1， rows，0，1 and 2， column 2， rows，0，1， and 2。哎。😊，Now by my diagonal here。

 now if you wanted to be crazy。We could do both diagonals like hey。

 have a diagonal up and a diagonal down function， I think that's a little bit overkill right I think at that point we've gone a little too far here。

 but totally up to you right you get to write the code。But I'm just going to do a single one here。

So both diagonals cross through the middle， right， which is row one， column one。That's one one。

If that is a space， were done。So we're going to say hey。

 if my board at one do at one does not equal a space。Right。

That's the first starting edition here and。Now I'm going to check both diagonals at the same time。

Ca why not we can say this one or this one。 All right， the logic' is a little bit crazy here。

 but that's okay。 So we're going to do another set of parentheses here。

 So then my board dot at0 dot at 0。I's equal to the board at 11。And。The board of  zero0。Matches 2。

 too。Right， so zero01，1， two two if those ones match， we're good here。So that's one possibility here。

 right？But I want that one or。Another possibility going in the other direction。

 so this is a little messy here。Your parentheses are pretty pretty important as we go here。

 so let's let's just do that on one line here it'll be a little bit long but' make this look a little bit nicer I think so we'll say that one。

Or。Right。Then my board got at。Row zero， column two。 still row zero， but I want this one over here。

 does it match this one， does it match this one。Does that one match the board at11？

 it goes through the center。And my board。 ask 02。Pa 2， that will match the board。

At now column row2 column zero。That's the other case here。Center is not a space and。

00 matches 11 matches 22， or centers not a space and 02 matches 11 and 02 matches20。

Right row two column zero， any of those ones are true then。We can return to true。

 let's see they return。Return true。Oh， my off by one still， see you。

See this is why it's too long here， where is that magic one？Yet one more parenthey。

 I guess that looks too like too many but sure turn true。I guess we have it in， I don't know。 No。

 sure otherwise。And really， if you're saying if something returns true else return false。

 you just return it。I mean we don't need to do any of that。

 we can just say return this sucker is it's already true or false。Right？Is just true or false。

 like thisagonal or this aagonal？So that's not really a one liner， but kind of a one liner here。

 it's a two， three liner。It's a little bit ugly， that's okay。Not at the end of the world。

And look they sort of match up here now right， so this one and this one or this one。

That was the goal with that one。Right right？Cool， and we need to markboard。Right， so。Mark Borden。

 probably Vne， right， Lne， Mark B。Given a vector vector of cha。

 now this one is important here that we pass by reference。Does I need to change the board， right。

 these ones to print and to see if the game's over。

It doesn't really matter if I have the copy or not now it's going to be faster if we pass a reference because I don't have to make a copy of memory。

 it's probably better to pass all these by reference。

 but not necessary here but this one for sure we have to pass by reference so I can go and change the board so we don't run the issue we did when we were sorting so to market where we just printed it so we'll ask them right so see how enter。

A row and column。Mark。I't remember we say what players turn it is。

 this was Markboard given the current player Charr。Current player。So we will say current player。

Turned。And line enter a row column mark。Sure， why not？

And then I can see in on row and you can actually see an on column as well。

 and you can do both at once if we're only doing numeric values it should be fine if you need an in for row and an in for column。

Right， we can grab them both at once。Now we want to make sure they're valid numbers right，0。

1 or2 and that the spot isn't already marked right。

 So I'm going to say while my row is less than 0 or row is greater than2 right or。

Column is less than zero， or column is greater than2。Or I board at row at column。

Does not equal a space。Yeah。If that's true， that's invalid， ask again， let me move these up here。喂。

We'll say， invalid。And valid lot。Right just almost bad you could print it again。

 you could do whatever you want to hear that's probably fine so eventually you'll get something that's。

Between zero and two， right zero， one and two are good。

For both of those and now it's nice here because when we're oring remember this we'll do the short circuiting if this one is true it never looks at the last one right it just says。

 oh there's something true and you're oring together run the loop right the whole condition becomes true so if I have a row that's negative or row that's greater than two it's not going to try and get an invalid index and crash and when you try and get an index out of a vector crashes on you。

Says you get that invalid index and pukes， it never tries to get one because I'm oing them all together。

 the whole thing was true and it will just tell me it's invalid immediately right so I don't have to do that as a separate check。

 which is nice。Assum all that works， then take my board at the row。At the column。Column。

And I'll assign it in the current player。头则。Once I get a good entry， mark it。

And we can keep on going， right， current player changes。These games not over。 Keep on going。

 So I guess at the end， we should probably print the board one more time here。Right。

 should we try it。

![](img/e1e0a6021328e1f91c111c57045d41aa_36.png)

We'll see if it works， that's our first run here Are a bunch of code。All right， here's our board。

 X's turn。 I'll let you guys go first and if you can beat me atict toe。

 you get immediate A in the class。Regardless， if you can beat me， really？Sure。

 if you can be me a Ti ta to， have it， right。So what row and what column？What row index is that。

 zero， zero？All right， so I'm going to go to the center， right， one one。Oh。

 I'm cheating apparently I went， oh， because the stupid enter key， all right， hang on。

 feeling the sands is so obnoxious。

![](img/e1e0a6021328e1f91c111c57045d41aa_38.png)

It know。I think we just see in one more time hanging on like a string for garbage or something。

Garbage， sing on garbage。

![](img/e1e0a6021328e1f91c111c57045d41aa_40.png)

I think that does it here。 Let's try that because it keeps the enter key around or something like that。

 R he went 0，0。 I did 1，1。Nope， still did it。

![](img/e1e0a6021328e1f91c111c57045d41aa_42.png)

All right， all right， we got a bug here， hang on， it's this entry thing is the worst part。All right。

 so zero， zero。X was good， oh。Didn't it debug。And never。Can I get to that line？1 one。

Why did it not stop at that line？Oh， I never got to the the Oh， okay， yep， sorry。

 you got to grab the garbage here and here。Justin kicks every time we grab this one here， Oh。

 wonder if we just into garbage as well， let's try that。That's like the enter key all right。

 this hopefully will work， let's try that。

![](img/e1e0a6021328e1f91c111c57045d41aa_44.png)

0，0。No。And once I go spy， how what does it hey？

![](img/e1e0a6021328e1f91c111c57045d41aa_46.png)

没有。He。Inputs， it worked the first time， but not the next time， right。Yeah。

We're not getting any other CN right， that's the only CN。你。Rowan column。Why is it not working。

 All right， hang on， let's try it continue。0，0。All right， now we're back， so we did zero， zero。

Now once more entry， we should actually do it here。

 that's where we should break there we go excuse me one one。



![](img/e1e0a6021328e1f91c111c57045d41aa_48.png)

![](img/e1e0a6021328e1f91c111c57045d41aa_49.png)

Aecta here， row 1， column1。No。Mark the board。 Our player moves， game is not over， print the board。

 mark the board， step into。Current players turn。Get row and column now row is nothing。

 columns nothing。

![](img/e1e0a6021328e1f91c111c57045d41aa_51.png)

Oh。Do we do the marking wrong？

![](img/e1e0a6021328e1f91c111c57045d41aa_53.png)

So I think I copy pasted that。 That's a copy pastment error。

it wasn't a bug with the input it's a copy paste error crap， all right。

 so row one column one row one。Column2 all of these， I did it wrong on all of them， you guys。

 you guys， column2， column2， column2。

![](img/e1e0a6021328e1f91c111c57045d41aa_55.png)

Look my bad。Let me take out my breakpoint， so it'll actually run。



![](img/e1e0a6021328e1f91c111c57045d41aa_57.png)

See， okay。

![](img/e1e0a6021328e1f91c111c57045d41aa_59.png)

0ero， zero， one， one。

![](img/e1e0a6021328e1f91c111c57045d41aa_61.png)

Oms turn。Did do my。Comparison wrong， if the current player is， oh， it goes to otherwise it's oh。

 I did， I was going to take too many turns， So why hate turnary expressions no。喂。

If it actually goes to， oh， why to stay it oh。我睇嘅。对个。That was X currently。



![](img/e1e0a6021328e1f91c111c57045d41aa_63.png)

High， on site sea equal extraordinaryern。是。Something's not working with my turnern expression。Equals。

This question mark that。Firmplay equals。

![](img/e1e0a6021328e1f91c111c57045d41aa_65.png)

Okay， so equals。Then we give it curve player equals O。Mr。 Mark X。Otherwise， oh。



![](img/e1e0a6021328e1f91c111c57045d41aa_67.png)

This is still super ugly。 That's awful looking。No， yeah， just this one， right？Equals。

He is the condition。C is the value if that's true， okay。



![](img/e1e0a6021328e1f91c111c57045d41aa_69.png)

These are awful looking。I'll try that。

![](img/e1e0a6021328e1f91c111c57045d41aa_71.png)

0 zero， one， one X turn， all right， let's try it， let's try it right。Fottom right。

 what a row and what index next two two， all right， so I'm got to go。Force you to go somewhere else。

 right stop one of these positions， so I'm going to go01。

And then you're going to have to block me you go to。2，1。

 and then I have to stop you so I go to zero and then you have to stop me。So you go one。

 two one zero two oh yeah zero two， okay， I almost one there all right。

 and then I'd stop you so I'm going one two and then you have to stop me。喂佢个个。1，1，0，10。

one get one zero game over， we tied。You'll try again I'm sorry。Let's try it， yeah。

 let's see if our code works， right it should tell you it's invalid。So zero zero one one。

 you try one1 invalid spot got some checking， no cheating。

 I'm going to learn lot to cheat you try you can beat me this time。咁人 b me。We're going to go。1，0。

1 zero。Allright， well， I gotta stop you so I go20 and then you go zero two， all right。

 I gotta stop you so I go zero1， you got stop me， you go21， right。

 and then it doesn't matter where I go， I'm gonna make the pattern because I like the upside on y shapes。

 I'm gonna go20 No no， sorry2，2。And you go one two。That's my favorite ending。

 when's like an upside down lie kind of V don lie。My wife thinks when I let I play my kids I should let them win occasionally。

 I tell life isn't fair， kids have never beaten me at Ti tak toe。Oh， they think it's not fun anymore。

It was never fun Ti tako was never fun it is spoil， it's never fun， it's impossible。

And it's when we win。If someone， you just can't win， though， it's a terrible game， you know。

 connect four。Is fun because the person who goes first can always win。

It solved if you know what you're doing， you will always win as the first player。

I don't know how it works so I don't have the memory to memorize all the right moves so I don't know how that works so I'll play connect floor and sure but chess chess is much more interesting that's a good game you can find me on chess。

 co if you want Eric Chessky the only one out there in the world I'm not very good I'm not terrible but I'm not very good my brother beats me all the time he was actually rateed which was fun。

What are you rate as unofficially on chestes。 co I'm like 11 or 1200。So。So。

It's fun chessess is much more interesting and then writing chess engines is really fun too the team at chess。

com was really cool like they do videos on some of their tech stuff like they do for their chess engines it's really fun I feel like that sort of stuff。

And the new。Deep learning sort of train yourself here is really fun now when they put together the challenge though was really unfair because they had the former best chess engine in the world play against the deep learn deep Min every they call it here or Al zero or something and they're like look it wins or the current one lost all the time to the new version but the handicapped it because the chess engine is written to use an opening book it's like the first 15 moves everybody knows you always here's the best move you don't need to calculate anything and they're like for this test you don't get to use that orre like that's how it was written if you don't let it use that it's gonna suck and they're like oh look the new deep Min is so much better。

Okay， sure that's not an apples to apple comparison， but okay。

 so that sort of stuff is fun if you like chess， but a little bit trickier to write the rules is not just like。



![](img/e1e0a6021328e1f91c111c57045d41aa_73.png)

Print the board， marked the board。I mean， it is， but marking the board or moving a piece on the board is got a bunch of different options there right。

 So all right， how do you feel about arrays and vectors again。

 I've used vectors for everything because I just like them so much better and array will do the exact same thing。

 but it is fixed in size fortict toe。We know it's a three by three right there's no you don't have any advantage of using a vector here。

 I just prefer vector， so I always use this crazy at notation instead of the square bases。

 you can still use square bases with vectors if you like right but you don't get at with a arrays the at notation that's all and a array can't tell you their size like vectors can。

And so I like vectors Okay， that's just my personal preference here。

 I think they're easier and I'll use them all the time Okay but would be the exact same thing with a arrays we just change some of our syntax around。



![](img/e1e0a6021328e1f91c111c57045d41aa_75.png)

All，' feeling pretty good。All right， we're still working on the project， right。

 how's that going for you？Project 3。Okay， right， the parallel array is going to help。Right。

 we have multiple things stored at the same index in different arrays。Right。

 that'll make life easy for you right if you know how you want to read the file you write the file to match if you know how you want to write the file。

 you read the file to match you pick whichever format you prefer go for it right pick one and both have to do it。

😊，But should go relatively well， so come next week， we'll get into objects and classes。

 solve Project three， and we'll talk about the final project that we're working on here。

Now we don't have to work in pairs for the final project here it's not one of our objectives if you'd like to work as a partner I'm open to it I think it's a better experience turns out working with someone else actually makes more work for you because like you have to coordinate so you do the exact same project whether or not you do it solo over with a partner but the collaboration takes a little bit more time energy and effort sometimes both people will submit the same repository excuse me so I'd recommend you use Git you don't have to some email files back and forth。

Sure it can work， but whatever's up to you git has some weirdness here if you both modify the same vial at the same time so cause a little bit of headache sometimes sorry my sugars high。

And so we'll get into object classes， getting into the pointers， thanks for break in the review week。

 we got to come back and pick up this last topic here using UMA activity diagrams as' just some supplemental stuff here。

 all the other things hopefully right this use case and activity diagrams we'll get to during the review week。

Recursive procedures will get to don't have the chapter around recursion。

Yes we'll probably do that in the review week as well that's pretty quick we're just writing some real basic ones for that C++ is still modern people still use it all the time here can you edit compile and execute programs using an integrated programming environment such as MS visualual Studio feel like we've gotten there so in terms our objectives we're getting there here。

But we'll get to these UM this is drawing pictures to show what we want to do sounds kind of silly but it's really worth a lot of time when we design solutions it makes it easier to write the code so UM is a popular tool for that yeah we're doing pretty well so don't forget about the Zybooks that'll be do Monday right and then we'll move on to the next chapters and go from there。

Awesome next Wednesday the day， right let's see what it says。呃。Yeah， the2 for the hour week yep。



![](img/e1e0a6021328e1f91c111c57045d41aa_77.png)

Awesome， all right， thanks folks， I'll see you Monday。



![](img/e1e0a6021328e1f91c111c57045d41aa_79.png)