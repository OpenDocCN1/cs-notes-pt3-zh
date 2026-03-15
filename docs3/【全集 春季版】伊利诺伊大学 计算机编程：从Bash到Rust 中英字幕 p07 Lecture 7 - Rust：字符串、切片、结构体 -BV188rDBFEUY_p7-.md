# 【全集 春季版】伊利诺伊大学 计算机编程：从Bash到Rust 中英字幕 p07 Lecture 7 - Rust：字符串、切片、结构体 -BV188rDBFEUY_p7-

Okay。We'， come back to CS 196， they were doing。Russ lectures 3。

 so let's go over the objectives for today。Firstly， we want to do slice types and string slices。

 So this is building off of ownership and memory accessing， which Sammy talked about on Tuesday。

 We're gonna talk about strs， which is a very useful type of data types that you can create yourself。

 And then we're doing a bighoot review with a lot of questions from everything we've covered so far。

 And that's also gonna to be worth 1% of extra credit for people who are in top five。

 So say stay focused。 A lot of questions are be gonna be from today。 so。😊，Let's start off with。

What a slice is。 So slices allow us to reference contiguous sequence elements in a collection instead of just getting the whole collection。

 So let's talk about it over here。😊，If we have from last week's lecture， hello like this。

 this is a whole collection in memory。😊，Or in the heap。 But let's say we don't want Ho。

 We just want the last three letters。That's called a slice， like this。

So let's talk about how we can get this and why this is useful。So firstly， slices are references。

 So that means they do not have ownership over what you're getting。 And a way we can use slices。

 let's say we have like a long string， like a very long message。

 and we want to get just the first word， or let's say want to find the first occurrence of a specific word in the word right after it。

 So that's where we can use slices。So a string slice is a reference to a part of a string。

 So they look like regular references， except for。The very end。

So notice that you have the square brackets with two numbers of dots。

 It's kind of a weird looking format。 but this part makes it very， very useful。

So a string is essentially an array of characters。 So an array is a list。 So we've seen list before。

 pretty basic stuff。 Is there any questions about arrays before I move on。Right。

 just regular sequence of characters。 So let's say we have an array or a list of characters called reverse me like this。

And now， we have。All the indexes。 So if it's an array， we have an index is 0 to the last length。

 So index 0 has R。 indexdex 1 is E， et cetera， et cetera。

So0 to 7 means we want the characters between the zeroth index up to。

 but not including the seventh index。 So in this case， we're going to get0 up until So R up until E。

 So the first word reverse。 We don't get the very last index。 That's exclusive。

So let's like see this in practice， because I think it's the best way to actually work with this。

So I already prepared this beforehand so we can just。



![](img/88cd40dc273c9b3c120243d4187bdf7c_1.png)

Get this up。So we have here a string slice。 So we're declaring a variable called reverse me。

And it's just the string reverse me， reverse with the space， me。And we declare word  one。

 which is the string slice of reverse me。With this。

 with these parameters and War two with this parameters。

 So does anyone have a take a guess at what the print will do。



![](img/88cd40dc273c9b3c120243d4187bdf7c_3.png)

Noep， okay， we can just run it done。

![](img/88cd40dc273c9b3c120243d4187bdf7c_5.png)

Me reverse。 Alright， so let's talk about what happened here。So firstly， we got the first word。

 which was reverse。 So we went from 0 to 1。 So if we count from here， we have 0，1，2，3，4，5，6。

 and 7 is the last one。 we ignore it。😊，Soly we start from 8。 So 8 starts here，9，10。So，8。9。

 and then 10 is the last one we ignore it。 And we just printed them， but in reverse order。

Simple stuff。 Any questions about this。

![](img/88cd40dc273c9b3c120243d4187bdf7c_7.png)

O。So internally， what a string slice is is essentially itss data shock that stores the starting position student and the length of the slice。

 which is the ending index minus the starting index， so。😊。

The word 2 variable contains a pointer to the9 by in reverse reverse me。 and it's a length of 10-8。

 which is 2。 So the reason it's 9， not 8 is because we started 0。So let me explain that graphically。

 since it's easier。 So let's say in memory in the heap， we have this reverse me over here。

 So we can see it goes from 0 to 9， and it has each bite is stored in a different area in the heap。

Reverse me over there is the string， and word2 is the slice。

Notice that they have something called a pointer。 A pointer is a variable that just points to a section of memory。

 Similarlyly， how you seen integers。 like if you have an in that holds a number。

 string holds a string。 A pointer is a very specific type of variable that holds a memory location。

 So lets us know where to look in memory。😊，So reverse me。

 the actual string points to the start of the string。 That makes sense。 We want the full string。

 and that this holds the pointer， the length of the string in the capacity。

 So we'll talk about capacity later when we talk about vectors and such。

 All you have know is that it has a length of 9。 And now we have word2， which was me。

 And this pointer starts at the eighth index or the ninth byte from the start。😊。

And has a length of 2 because 10-8 is 2。Does that make sense how this works graphically。Yep， great。

So using the notation to dot dot， we can do a few clever things。

 And let's say we want to slice a string S。 So we have the string S and let's slice it up in a bunch of weird ways。

So let's say want to go from 0 to the fifth index。 We can just do S dot dot， and then the index。

 If we don't say anything to the start， Rus knows we want 0 automatically。

 And this is a quick way of doing that。Similarly， if we want to go from any random index to the end。

 instead of finding out the length of the string， calculating that， storing in a variable。

 all that mumbo jumbo， we can just do some index dot dot， and then don't put anything after that。

 Close the bracket That way， Ru is we want to go from some index the very end of the string。Also。

 because we have this dot dot notation， we could also just do dot dot and get the whole string。

 So let's say we wanted to get a reference of the whole string。 We could just do a slice type。

 but have it be dot dot。So a few other key points is the string slice has a specific type。

 and that's Ampersand pointer because it's a reference， and it's like a string。

So this is when you w to， in a function， for instance。

 have a return type that is a string slice or you want to have a parameter that a s， a string slice。

And string literals are also string slices。 So if you declare a string like this。

 So let's say a random string called literal and make it literal。

 So this is not a string with like varying size。 This is actually a string light。

 It's a reference to a location in memory。 And it's also why it's immutable。

 It's because a string slice is by default an immutable reference as are all of the references。😊。

That's how other slices， though， because slicing is very useful， not just for strings。

 We can actually slice in other collections， like arrays。😊，So， for example， here。

 we have an array called summary array， which has a bunch of random numbers in there that have no meaning。

And then we have let slice， which is。A slice of this array。 And we're going from one to 3。

 So that means we get the first and second index。 So slice now reference to 9，6。Does that make sense。

All right。Now let's talk aboutstructs。 So Strs is a custom data type that allows you to group a set of values that make a meaningful group。

So this is different from a collection。 A collection is often just like a list or a tuple array。

 It could be anything， whereas a struct will be a single variable that holds a bunch of values that are meaningful。

 So， for instance， let's say we want to store U IU students instructs。😊。

So the students struck with store the name， the U I N， are they 1，96 student and their GP。

 and these different values are all different。 They aren't the same type， clearly。

 but they're all related to one thing， and they're all meaningful to one group。So let's say how。

 let's first declare astruct。 So how do we declare a struct。

 We declare astruct by using the keyword struct followed by the name of the struct and then two curly brackets。

And then we do what's as the key value pair。 the key being the name of the variable。

 and then the type of that variable。And we store that in a comma separated list。

So this is our U IU studentstruct。 We have， obviously the keywordstruct， the name U IU student。

 And this is something I learned today。 But if you don't capitalize your struck name the way I've done it here。

 the compiler actually gives you an error saying， are you sure you want to do it like this is another way to do it。

 So something I learned。😊，And then all the value in a key value pair。 So the name is a string。

 The U I N is a number。 The integer is a boolean， and the GP is a float， because it's a decimal。Now。

 let's declare the stroke in our code。 So how do we do this， So let's say we want to， in our code。

 declare a new student。 So we use the let keyword as we do with any other variable。

We call it by the Str names， the USC student。 And then similarly to how he declared the， defined the。

 Sorry， we can declare it in a very similar manner。So our student is called UN Nightly 6， 196。

I thought it was really funny。 I don't know I No one was laughing。

The UIM are then 186 in their GPA because their new student that comes in is four。Oh。

 so one thing to note here is that let's say you have name U I N in this order。

 You don't have to follow that here。 name could be at the bottom。 G A， second， etc cetera。

 etc cetera。Okay， accessing value。 So we can access values tostruct using dot notation。

 So similarly with the tuple， if you want to get the second value， you do dot 1。For a struct。

 we just do the struct and then the value name。 So we have like name， U I N， whatever， whatever。

 We can get the name by doing student one dot name。 And the output， as we can see。

AndThe student is called U nightly sticks。Okay， we also access values andstructs。

 So if were gonna make a variable mutable， we can edit the values using dot notation。 So as we know。

 all variables in rust are immable。 You cannot change them once you set them。

 But if we make a mutable student。 So a student mute over there。

 we can change their G or any other value that they have， because this is now a mutable variable。😊。

And we can start our output here because the immutable students D pay went from 4 to 3。3。

 They didn't do2 well in 125 or something。Okay， very important。

 So the entire struct must either be mutable or immutable。

 Individual values inside thestruct cannot be individually mutable。

 So if we look back at thestruct over here。Or we' look at this over here。

Notice that we can just say the name is mutable。 or G is mutable， although that would make sense。

 The whole thing either has to be mutable or none of it can be mutable。

 And that's just for safety when you're writing code。



![](img/88cd40dc273c9b3c120243d4187bdf7c_9.png)

Especially concurrent code。And I's talk about using a function to create astruct， so。

If we want to have astruct data type is just going to be the data type that we declared earlier。

 So if we want to make astruct， declare something， we can do new student with all the parameters that we want and return thestruct data type。

 and we assign all the values inside。And the reason we only have two parameters is that because we can hard code values when we create this。

 We don't have to always be passing a variable because let's say we have a new student They're automatically gonna have a G 4。

0， or they're automatically not gonna to mean 196。 So we don't have to manually assign every value。

 We can automatically do that by predefining some values。All right， so let's demo this。

What's an actual code。

![](img/88cd40dc273c9b3c120243d4187bdf7c_11.png)

But I made another folder over here， called Strs。

![](img/88cd40dc273c9b3c120243d4187bdf7c_13.png)

So over here， we can see we have our struct， as we saw in the lecture slides。

 It's called your A C student。 and has these four values。Give me a second。

 I have a bunch of other stuff in here。Okay。So let's say we have this function here。That we declared。

 obviously， what this is gonna do is once we pass the parameters over here。

 it's going assign that to our new student and then return that student over here。

So it creates a new， a newstruct， assigns that to the student variable here。

 And then we can do stuff over here so we can print out the student's name， U I N， are they in C。

 S 1，96， and then their GPA。So， let's run that。

![](img/88cd40dc273c9b3c120243d4187bdf7c_15.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_16.png)

Oh， my bad。

![](img/88cd40dc273c9b3c120243d4187bdf7c_18.png)

嗯。😔。

![](img/88cd40dc273c9b3c120243d4187bdf7c_20.png)

Ope my body uncommented my comment。

![](img/88cd40dc273c9b3c120243d4187bdf7c_22.png)

Let's clear this。 Run that again。Having see that we have a new student who has this UI N， They the91。

96 and their GP coming in is 4。0。 They're a new student。



![](img/88cd40dc273c9b3c120243d4187bdf7c_24.png)

B wait， doesn't this seem kind of like a waste of time， because if we notice。For， if we notice the。

 the variable name that we're passing into the function of the parameter name and the parameter U I N is going be the name and U I N of this the the structure that we're creating。

 This is kind of redundant code。 and makes no sense。But we get this done and obvious。

 And so it does rust。 So instead of doing that， there's a smarter way called field in his shorthand。

So in it is just short forizer initialization。And when the parameters in the field names have the same name。

 you can just have that。 and you don't have to automatically have a key value pair。

 You can just put name UI N。 and Rus knows automatically that because the field names。

 the parameter is are the same to assign those values to each other。But sometimes。

 let's say we want to make a new struct that uses most of the values in olderstruct with a few updates。

 And for this， we're going to usestruct updates syntax。So let's say we have this direct over here。

 So we have a new student whose name is student1。 Their U I N is that number。 They are non 1，96。

 and the GP is 4。And we want to use， we want to make a new student called student 2 with these values。

 So this is what we want。 And we could use the dot notation to copy the values from student1。

 But this is unnecessary code。 and it can get messy with bigger strokes。

So there's a better way to do this。 We can use what to instruct update syntax。So notice here。

 the updated values we manually assign to what we want。

 So we know that we want a different name and a different U I N。 So that we manually assign here。

However， for the other values that are going to be repeated， we just do dot dot。

 and then the other instance of the struct， which is student1。And this， let。

 let's Rus know that we want the other fields in Rus to be what student1 was。

 So it was going to change everything except from nameming U I N to student one's values。

Any questions about thestruct update syntax。Okay， we're gonna demo it real quick。Just to go over。

What this is， because it can be a little weird。

![](img/88cd40dc273c9b3c120243d4187bdf7c_26.png)

Okay。So we've declared our student one here with what we saw in lecture。

 And this is what we could do。 We could just say student 2 is whatever these things are。

 And we can copy student one's values by using the dot notation over here。😊，That makes sense。

 And now， when I run this。Did I do something again， I keep on commenting my comments。



![](img/88cd40dc273c9b3c120243d4187bdf7c_28.png)

All right。Clear。嗯。And we see the new student has these values。



![](img/88cd40dc273c9b3c120243d4187bdf7c_30.png)

From the print statement。But this is a lot of unnecessary code。

 And if we have a bigger stock with a lot more values， let's say we want the students year。

 their major and all this other stuff。 It'll be a lot of unnecessary code。So instead。

 what we can do is。Use。The the update syntax。By manually assigning the name of U I in here。

 we can take student one's other values and automatically assign that to student 2。



![](img/88cd40dc273c9b3c120243d4187bdf7c_32.png)

So now when I print run this again， we get the exact same output。 The results the same。

 but you have less code to write， and it's cleaner for anyone else looking at your code。



![](img/88cd40dc273c9b3c120243d4187bdf7c_34.png)

And I want to talk about tuplestructs。 So tuplestructs are similar to。A tuple。

 But we the difference is if we want to have a tuple of a specific type that we want to repeatedly use over and over again。

So。😊，The main difference between a struct and a tuplestruct is the fields don't have names。

 only types。 And this is useful when you want to give a tuple structure a name。



![](img/88cd40dc273c9b3c120243d4187bdf7c_36.png)

So forver here， let's say we want to repeatedly use test scores or lecture reviews like so。

If we have the test scores。As a regular tuple， we don't know what it is。

 We're gonna re recycle it again and again。 We don't know it's data type。 It's just another tuple。

 similar with like lecture reviews。So few key points about this is。

Notice we only define the types of thestruct holes。

 We don't give it a name like we do with a regularstruct。

 This is just a random unsine 32 B integer or sine 32 B integer， sorry。

We use brown brackets or parentheses like we do with a regular tuple。



![](img/88cd40dc273c9b3c120243d4187bdf7c_38.png)

And although these two tus look the same， they're both their own individual type。

 So this is important because if you have a function and the parameter wants test scores。

 you can pass a lecture review to it because they are different types。

 So even though they look exactly the same and they have similar functionality。

 they are different types just because the way we declare them。

But apart from these restrictions mentioned， you can， they can be used like a regular old tuple。

 You can use dot notation to access the values。 You can assign them to variables， etctera， et cetera。

Okay， so。Now， we're just gonna go through a pretty big ofooot with everything we've covered so far。



![](img/88cd40dc273c9b3c120243d4187bdf7c_40.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_41.png)

第。

![](img/88cd40dc273c9b3c120243d4187bdf7c_43.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_44.png)

🎼哎， here a koo code。🎼Please share that ID when you log in， for your Hoot。🎼，🎼，🎼。🎼，🎼，うん。🎼哎。🎼The。🎼。🎼The。

🎼。🎼，🎼Okay， who is not in the cahoop yet， Raise your hand。🎼O。🎼The。🎼拜拜。🎼。🎼Whos not the caooot？🎼。🎼，🎼。

All right， is everyone in the cahoot？🎼All right， then'm got start。



![](img/88cd40dc273c9b3c120243d4187bdf7c_46.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_47.png)

🎼，These variables of that are blankk by default。Alright， great。 Most of you guys got that right。

 So variables in rust are immutable by default。 You cannot change them once you've assigned them。

 And that's done for concurrency and to make your code very safe。😊。



![](img/88cd40dc273c9b3c120243d4187bdf7c_49.png)

Right， leaderboard。 Remember top5 gets a whole 1% extra credit。



![](img/88cd40dc273c9b3c120243d4187bdf7c_51.png)

🎼嗯。🎼，All right， great。

![](img/88cd40dc273c9b3c120243d4187bdf7c_53.png)

I can get that code back。Okay， so if we use the mute keyword， that makes our our variable mutable。

 That means we can change it。 So now we can assign it to a new value。 And when we print it。

 we'll just print 6。😊。

![](img/88cd40dc273c9b3c120243d4187bdf7c_55.png)

🎼う。🎼Yeah。🎼やっただったらった。🎼い。🎼对。🎼，Okay。So scalar data types are like integers， strings。Floats and bos。

 Those are the four scalar types we have。 They only hold a single value。

 Compound data types are the arrays in tus that can hold multiple， like a list。

Any questions about this so far？ Any of the previous questions to stop me if there are。



![](img/88cd40dc273c9b3c120243d4187bdf7c_57.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_58.png)

🎼粉气粉。Okay， great。 Yep， arrays can only hold one data type when you're working with them。

 So if you put an integer and a flow together， your array will crash， It's not going to work。



![](img/88cd40dc273c9b3c120243d4187bdf7c_60.png)

This leaderboard。

![](img/88cd40dc273c9b3c120243d4187bdf7c_62.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_63.png)

嗯。たたたた。🎼，🎼，🎼The。Allright， so this one is from the second lecture of rust。

 The stack and hold variables that we know the length of。 So obviously， this is false。



![](img/88cd40dc273c9b3c120243d4187bdf7c_65.png)

嗯。Awesome， yeah。 So if the stack can hold things that we know the size of， the heap is the opposite。

 it holds source data of an unknown size or the size that might change。嗯。🎼，Allright， great。

 pretty self explanatory。 I don't know why we'd ever want to reduce performance。

 Programers always want to make code faster， especially with rust。 So yeahep， good job， guys。😊。



![](img/88cd40dc273c9b3c120243d4187bdf7c_67.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_68.png)

🎼The。🎼。🎼，Okay， so false， a value in Ru can only have a single owner。 If you have multiple。

 So once you hand over ownership to another variable。

 the original variable loses ownership of that value。



![](img/88cd40dc273c9b3c120243d4187bdf7c_70.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_71.png)

Rus is a single paradigm program language。🎼あ。Alright， so rust is a multipar programming language。

 That means you aren't restricted to a single kind of programming paradigm。

 So programming paradigm as a refresher is like objectoriented programming or functional programming。

 you guys are probably used to object orient because you're all working in Java probably。 So yeah。

 Ru allows you to code however and not however way you want。

 but you're not restricted to a single style。

![](img/88cd40dc273c9b3c120243d4187bdf7c_73.png)

Updating the leaderboard。

![](img/88cd40dc273c9b3c120243d4187bdf7c_75.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_76.png)

🎼お。All right， pretty easy。 you want to declare astruct So if you want to define a struct。

 use the keywordstruct， if you want to declare a struct， you use let。



![](img/88cd40dc273c9b3c120243d4187bdf7c_78.png)

So that's a little bit tricky。 defining is like when you do over here。This is defining astruct。

Declaring instructor when you use in your code like this with the let keyword。



![](img/88cd40dc273c9b3c120243d4187bdf7c_80.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_81.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_82.png)

손。🎼，🎼，Okay， this one is so hard。Functions will take ownership of the variables that are passed into it unless stated otherwise。

 So if you give it pass a string into a function， this whatever variable。

 that the function allocates the string now owns that string。 So unless you specify otherwise。

 the function will take over ownership over that。

![](img/88cd40dc273c9b3c120243d4187bdf7c_84.png)

Variable that you pass into it。

![](img/88cd40dc273c9b3c120243d4187bdf7c_86.png)

🎼，🎼It is us today。Yeah， slices are references。 So if you have a string， you take a slice of it。

 youre on copying and making a new thing。 You're just pointing back to what you had originally。



![](img/88cd40dc273c9b3c120243d4187bdf7c_88.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_89.png)

Up in the leaderboard。

![](img/88cd40dc273c9b3c120243d4187bdf7c_91.png)

🎼，🎼，🎼い。🎼Yeah。🎼这。Alright。 yeah。 So astruct， we use the dot notation to access the variable。

 So the blue answer is correct。 use dot and the variable name。



![](img/88cd40dc273c9b3c120243d4187bdf7c_93.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_94.png)

嗯。🎼，🎼だった。🎼，Okay， so when you declare a stroke， you can either make the whole thing mutable or you can make the whole thing immutable。

 You can just say the name is mutable， but the rest is immutable。

 The whole thing has to be either one or nothing。Any questions about that or any of the previous questions？

Allright， we'll move on then。

![](img/88cd40dc273c9b3c120243d4187bdf7c_96.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_97.png)

。🎼Yeah。🎼，Cavin see the code okay？🎼Yeah， no。🎼Thats yes。🎼。🎼さ。🎼。Okay。



![](img/88cd40dc273c9b3c120243d4187bdf7c_99.png)

So I'll walk through this。 So we declared a string。

 which is a bunch of random letters or ABC D up to K。 We want to get a reference from 3 to 7。

 So if we count from here 0，1 to 3， that starts it。 Oh my God， A D。😊，E， FG， and H is the seventh。

 but we do not include the last thing。 So we just have D， E， FG。



![](img/88cd40dc273c9b3c120243d4187bdf7c_101.png)

Probut first has been holding that for a long time。 So good job。



![](img/88cd40dc273c9b3c120243d4187bdf7c_103.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_104.png)

🎼，🎼The。🎼そ。🎼The。All right。は。😊，Well， you're all correct。 These are all correct examples of rust。

 as you remember from the first lecture。

![](img/88cd40dc273c9b3c120243d4187bdf7c_106.png)

I was hoping more people pick blue， but that's okay。



![](img/88cd40dc273c9b3c120243d4187bdf7c_108.png)

All right， last question。String slice internally hold a pointer length， but not capacity。🎼，🎼看点。The。

All right， this is true。 So a string slice， I go back quick， real quick。



![](img/88cd40dc273c9b3c120243d4187bdf7c_110.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_111.png)

Okay， so a string slice only holds the pointer and the length。

 whereas the actual string as a hole will have the pointer length and the capacity。😊。

Any questions about that？Yeah二。So the capacity is the amount that it can hold。

 So let's say we had like an array， for instance， and we one of the last few like item or a two。

 Sorry， one of the last couple items to be empty。 The capacity is bigger than the size at the moment。

We just want enough space later on to add characters to it。

And we'll talk more about that when we talk about vectors。

 which can resize the arrays that can resize and。Are very smart。 Alright。

 let's look at the leaderboard。

![](img/88cd40dc273c9b3c120243d4187bdf7c_113.png)

![](img/88cd40dc273c9b3c120243d4187bdf7c_114.png)

🎼On the top five will'll be getting 1% your credit。



![](img/88cd40dc273c9b3c120243d4187bdf7c_116.png)

All right， so good job to all you guys that was a pretty long quiz of。

En up keeping up with all of it。

![](img/88cd40dc273c9b3c120243d4187bdf7c_118.png)

Okay， so that's everything from us。 If you have any questions。

 you come here and ask us give me announcements today。Alright， no announcements either。

 If you have any question you can talk to us Next slide， we're taking a break from new rust contact。

 We learn how to debug and code better and rust， and then we'll get back into more rust stuff。

 So enjoy your weekend。😊。

![](img/88cd40dc273c9b3c120243d4187bdf7c_120.png)