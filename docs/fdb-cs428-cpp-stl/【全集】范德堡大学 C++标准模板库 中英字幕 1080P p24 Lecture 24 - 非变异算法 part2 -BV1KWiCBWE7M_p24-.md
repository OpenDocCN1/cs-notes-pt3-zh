# 【全集】范德堡大学 C++标准模板库 中英字幕 1080P p24 Lecture 24 - 非变异算法 part2 -BV1KWiCBWE7M_p24-

Hello and welcome to the next session in my webinar series on C++ Standard Tt Library by example。

Today we're going to wrap up our coverage of non mutating algorithms。

 focusing on algorithms that search within a range。😡。

So let's go ahead and take a look at the code we'll be inspecting， and then we'll jump right into it。

So I'll start by sharing my screen。And you can see that we're going to be focusing today on my C+ plus STl S 1010。

7 folder， and we'll see there are four projects under here。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_1.png)

10。7 a through 10。7 B。 so let's go ahead and take a look at the actual。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_3.png)

Soce code。There's a number of algorithms in STL that will search for elements in an integer range and these algorithms include search。

 which looks for the first range， looks for in a first range for the occurrence of a second range。

 possibly using a binary predicate or a value， search n that looks in a range for the occurrence of n items that are equal to a value。

 again， possibly using a binary predicate。😡，Something called adjacent find。

 which could either go under the find or the search algorithms。

 I'm putting it here because it basically acts as kind of a lobotomized search end and it looks in a first range for a pair of values that are adjacent to each other that have the same equal value or compare equal with a binary predicate。

😡，Then of course there's binary search that searches in assorted range to find an item and it'll do that in linear time and then there's also another algorithm that's called lower bound。

 which is similar to binary search except that it returns an iterator to the item that's found whereas binary search just returns true or false it's not really all that useful quite frankly so lower bound is a more useful method if you're trying to find the item with binary search and do something with it once you found it。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_5.png)

Okay， so let's take a look at the first example， this example is going to demonstrate how to use the STL search algorithm。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_7.png)

And we're going to give it a couple of strings for input。

 one string is going to be the famous phrase now is the time for all good people to come to the aid of their party。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_9.png)

And the other phrase is a famous lyric from a song by yes that says I've seen all good people turn their heads each day。

 so satisfied I'm on my way and then we're going to be searching for the sub sequence all good people。

 which of course miraculously appears in both of these quotes。😡。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_11.png)

So we're going to go ahead and start searching using search for sequence or search for Subence。

 which is that helper method I defined， and we're going to use that to search the vector and then we're going to go ahead and use search for subs to search the list of strings so we have a vector of strings and a list of strings and you'll see then in both cases we're going to be searching in we're going to use the subsence to be an array of strings so we're showing how you can write generic code that can be used with vectors lists and also arrays So let's go down here and take a look at search for subsequence and you can see search for subsence takes a pair of input iterators input iterator one and input iterator2 and then it takes the ranges within the first input iterator and the second input iterator to search for。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_13.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_14.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_15.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_16.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_17.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_18.png)

We write out the name of the function using a little convenience macro that's provided for us。

 and then we go ahead and we use the search algorithm。😡，And if we find a match。

 if it turns out that the subsequent sequence in first two through last two is found in the original range。

 first one through last one， then we'll get an iterator and we'll go ahead and say where that match occurred。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_20.png)

Otherwise， it didn't occur。😡，So let's go ahead and run the code and see what it does。😡。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_22.png)

And you can see here that when we looked this up we found the sub sequenceequence。

 all good people appears in the first vector starting at index five。

 which is indeed where it starts out all good people shows up there starting at index five because we're we're counting from zero of course。

 and then in the second list。😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_24.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_25.png)

It turns out that all good people shows up starting at index location two where you see all good people starting here so this did indeed work and it shows you how you can search for sub sequenceequences and here i'm using a list of strings or a vector of strings but you could use other types as well Okay so that's the search algorithm。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_27.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_28.png)

Now let's go ahead and take a look at。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_30.png)

A similarly named algorithm called search end。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_32.png)

And here we're going to have。The same basic input we're going to have our now is the time for all good people phrase as a vector of strings Ne I've seen all good people phrase as a list of strings and once again we're going to have an array that's going to look for all good people and what we're going to do here just to kind of make this really interesting is we're going to call a helper method we wrote。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_34.png)

Which is named search N for value。And what we're going to do here is we're going to be looking for。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_36.png)

Anywhere in these ranges， either the list or the vector。

 where we'll find two consecutive occurrences where words start with the letter T。😡。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_38.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_39.png)

In the case for the。The vector version L1， which is。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_41.png)

This guy up here L1。 and then in the case of L2， we're going to look for any place where we see two consecutive words that start with the letters S or the letter S two words that start with S So this is kind of funky and kind of cool So let's see how we're actually going to do this I'll show you the search and for value helper method in a second But first I'm going to show you that we're going to be passing in a binary predicate and you can see here the binary predicate takes a con string ref S and a con string ref V where V and S are the values that we're looking for and they need to be adjacent and we're checking to see if the first letter of S equals the letter V where V is actually the value that's passed in here and so it's going to go through and it's going try to find two adjacent elements that have that condition that predicate met and down here we're going do the same thing except this time we're going to pass in the letter S。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_43.png)

And we're going to check to see if there's two adjacent values。

 because then here's two the size of two that have the letter S as their first character。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_45.png)

This is the actual search and for value generic。😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_47.png)

Algothm that I wrote to do this you can see here that we have a forward iterator a size which is a value type T or sorry type name T and then a binary predicate and so down here we're going to have the range from beginning to end we're going to have how many things we want to be consecutive that's what size is we're going to have the value that we're looking for and then we're going have the binary predicate so let's take a look at what our code looks like what we're going to do here is we're going to start at the beginning and while we haven't reached the end we're going to call search n looking for initially the beginning to the end。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_49.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_50.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_51.png)

Trying to find matches of in this case two elements that have the value in this case。

 the string T or the string s， and we want to just compare the first characters to see whether they're equal。

😡，And what we'll get back will be an iterator and if the iterator doesn't equal the end in other words we actually got a match。

 then what we're going to do is we're going to print out the value that matched and where it matched and then we're going to set temp which is this value that's used to restart the search skipping over what we've looked at so far we're going to increment temp by。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_53.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_54.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_55.png)

Itter plus plus so we're going to increment the it by one and then start the search again now this will keep going either until we've reached the end or we keep finding things and if we have reached this point where we don't get a match and 1 equals first that means we didn't find anything so we print out the the value of the output saying consecutive values were not present。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_57.png)

Okay， so let's go ahead and run this program and you'll see what we'll get it's kind of cool and kind of fun。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_59.png)

So here you're going to see that we found。😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_61.png)

Two values of T at position two in our initial。😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_63.png)

String our vector of strings so here it is the and time contain T's and they're adjacent to each other so they have the value of two and then you can also see that we found again T appearing later so two and the also appear and that appears at position 10 so we got the match as we expect there。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_65.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_66.png)

And then down here， in the other。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_68.png)

Lyric from the song we find that S appears in two consecutive elements where the S is the first character with so and satisfied So those were examples of where we got the matches so this is demonstrating how search n works and you can see you can either do full comparisons or you can pick and choose the elements of the the values you're searching on as I do here Okay now let's go ahead and take a look at yet another example and this one's kind of fun this is basically kind of a variant of what we just looked at except rather than using search n we're going to use another STL algorithm called adjacent find and as I mentioned before you can either look at this is one of the find family of algorithms like find find if find if not and so on or you can look at it as kind of a search and what it does as we'll see in a second is it's kind of stripped down search end。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_70.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_71.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_72.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_73.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_74.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_75.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_76.png)

Where it looks for two adjacent elements that compare equal， but unlike searchN。

 you can't give it more than two， you can only look for two that are adjacent that same that have the same matching value。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_78.png)

So again we'll give the same input now as the time and I've seen all good people we'll search for all good people again。

 except this time we're going to use adjacent find for pre。

 which is this helper method I wrote to use adjacent find and in this case we simply give it the container that we want to search for we're not dealing with iterators here just to mix it up a bit so we give it the container so this will work for lists or strings or sorry lists or decks or vectors and so on。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_80.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_81.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_82.png)

And then we also give it a binary predicate， which is just like the one we looked at in our search and version of this where we're just going to look for the characters that have the same letter that happen to be adjacent to each other and then we do the same thing except this time we pass in the list as opposed to the vector so let's go ahead and look at adjacent find for pre and you can see in this case it's a template function that's parameterized by the type of the container so it'll take any sequential container as well as the binary predicate。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_84.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_85.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_86.png)

So down here we have code very much like we did for search end but it's just a little different because we're not using search end。

 we're using adjacent find so we start at the beginning of the container and we keep going till we reach the end of the container and what we do is we do adjacent find starting initially at the very beginning and we look through the entire container。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_88.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_89.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_90.png)

Using the predicate， which will determine if two adjacent elements have the same value because they're。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_92.png)

Their predicate will return that they have the same value and they'll have the same value if they have the first letter。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_94.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_95.png)

And again， much like we did for search in， if we don't run off the end of the container。

 we'll print out that we found two values at iter star iter sub zero。

 So we're going to index and print out just that character are found at the position that's designated by the distance from the beginning of the。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_97.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_98.png)

Container to the iterator where it ended up getting the match。

 And that'll that distance method is basically Stl's way of doing pointer arithmetic for things that may not actually be pointers。

 but maybe iterators instead。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_100.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_101.png)

And again， if we don't get a match， we'll print out， we didn't find the values。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_103.png)

So let's go ahead and run this code and see what we get as a result。😡。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_105.png)

We got some interesting results here， we find that we're going to find two values of T at position two and that's the same thing that we found before。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_107.png)

The time。And then we also find two values of T at position 10。 and that's2 the。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_109.png)

And then down here in list。😡，Of strings L2， we find that there's also two adjacent values。

 You can see that T turns up in position5 with turn there， and we find s in so satisfied。

 So this is it could be like an alliteration finder， I guess。

 but basically what this is doing is finding matches that are adjacent to each other。 And once again。

 we're showing the power of STl to be able to write generic code be able to plug in predicates that do very interesting and somewhat nonconventional things by just indexing into the appropriate pieces of the search keys we're looking for to get a very。

 very fine grain match。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_111.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_112.png)

We're now going to return our attention to the last of our non-mutating algorithms that we'll be covering and this will cover binary search and it will also cover lower bound。

 which we're going to wrap up in a little helper method called binary Find to compare and contrast it with binary search。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_114.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_115.png)

So let's take a look at the example as before we're going to have the quote now is the time for all good people。

 except this time we're going to put it in a string array as opposed to a vector we had a vector string before now it's an array of string and then we're gonna to have another string which is going to be the words we're going to search for in our quote which are going to be the words to find all good people and the first thing we're going to do here is we're going to sort the string array and we do this by using some convenience methods that are provided by STL that will let STL wrap a built-in array so that you can get the beginning and then the end and those can be used as an iterator range and that just handles all the Galbldy go under the hood to figure out how far off the last element is from the first element so once we sort though that range then string a array will be sorted it'll be in sorted order。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_117.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_118.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_119.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_120.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_121.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_122.png)

The next thing we're going to do is we're going to use the binary search algorithm to start searching through the other string。

 the string of search words to find all good people and as you can see here if we find a hit by using binary search then we're going to go ahead and print out that we found the word otherwise we're going to print out we did not find the word now the tricky part about binary search is it's a boolean it just returns a boolean and it doesn't give us the location where the element was actually found and that quite frankly is rather annoying so as a result we're going to show another example here using my little helper method called binary find and that's going to use the lower bound method that's part of STL in order to go ahead and do essentially a binary search that returns A。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_124.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_125.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_126.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_127.png)

Returns an iterator to the item if it was found。So down here we're going to make ourselves a vector of string。

 which will just be a copy of the range of the integer A。

 and then we're going to go ahead and print out the contents of that vector and of course the contents will be sorted because we sorted that array earlier and when we print this out it's going to tell us the index location of every one of the elements and that'll make it easy to tell when we do the binary fine whether it worked or not。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_129.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_130.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_131.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_132.png)

So the next thing we do is we have another rangebased for loop。

 where we go through the list of words we're searching for。 And for each word。

 we go ahead and do a binary find on it。 We'll look at the binary find code in a second。

 Just imagine for a moment。 It does binary search， but it returns an iterator if it gets a hit。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_134.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_135.png)

And in this case， just for fun， we're going to give it a constant iterator at the beginning and the a constant iterator for the end。

 And then the word we're going to go search for。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_137.png)

So if we get a match if we don't have the iterator we find be the end iterator。

 then we're going to go ahead and say we found the word at index and then we're going to say what the index is and we can get the index by using the distance algorithm which figures out how far away the iterator is from the beginning of that vector so that'll just tell us the index and we can match that up against the printout we have here otherwise we don't get a hit。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_139.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_140.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_141.png)

So let's go ahead and take a quick look at binary find that's defined up here you can see it goes ahead and is going to be。

😡，By default it's going to use the compare algorithm and it's going to make compare algorithm be less and so it'll compare them in lexical order with for less。

 so assumes it assumes the range is sorted in ascending order。😡。

The lower bound algorithm gets called here and it'll go ahead and search for the value using the comparison function。

 which in this case is less， and if we get back something that is not equal to last，😡。

Then we go ahead and we check to see whether or not the value research for equals the one we found and if it doesn't compare less than we say that we got to hit otherwise we say sorry we didn't get it。

 we didn't actually find what we're looking for so thats just a little extra sanity check to guard against some weird cases where you get matches that aren't really matches。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_143.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_144.png)

So let's go ahead and run the code， you can see here。😡。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_146.png)

We get the output and it basically says we searched for two here by the way。

 is what we're searching for， we're searching for。😡。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_148.png)

To find all good people in this quote it won't find find it'll find two it'll find all it'll find good it'll find people so those all get matched。

 but unfortunately the binary search algorithm doesn't tell us where where they were found so we then go ahead and print out the contents of the sorted vector that we made and now we search using the binary find convenience method one that's down here and in this case it won't so won't find find of course but it'll find all the other words we're searching for and it'll tell us where they were found so for example two is found at index 14 as you can see down here and all is found at index1 and good is found at index4 and people is found at index9 and so on and so forth so just kind of showing you that this actually works。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_150.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_151.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_152.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_153.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_154.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_155.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_156.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_157.png)

So this illustrates the。Algothms that we wanted to talk about over the past couple days that focus on non mutating behavior。

 in other words they don't actually change the contents of the containers that they're searching over。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_159.png)

Or looking for maxes or mins over or finding or other things that we've talked about so what we're going to do next is we're going to start discussing various mutating algorithms but before that we may actually take a little diversion and show a fun case study that exercises some interesting STL features and also shows off again the adjacent find algorithm so I think we'll probably talk about that tomorrow and that one's fun it's basically a calendar scheduling or meeting scheduling conflict detector tool and I think you'll enjoy it it's a good example of how powerful STL is and how you can use it for all kinds of interesting use cases。

😡。

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_161.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_162.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_163.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_164.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_165.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_166.png)

![](img/8744adf2f3fcbed1db7dde3c46f26bf3_167.png)

Well， thanks very much again for joining and please feel free to like and subscribe and I look forward to talking to you again soon。



![](img/8744adf2f3fcbed1db7dde3c46f26bf3_169.png)