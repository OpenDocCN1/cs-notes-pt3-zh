# 悉尼大学【中英⚡计算模型｜COMP2022 Models of Computation】 p08 P9 Ambiguous Grammar -BV1vTe6zzENb_p8-

In this lecture we will be studying about ambiguous grammar。

 So what do we mean by ambiguous grammar A grammar is said to be ambiguous if there exist two or more derivation tree for a string omega that means two or more left derivation trees。

 Okay so in the last lecture we have studied about derivation trees and we saw how we can draw derivation trees for the strings of a certain grammar。

 So let's say that we have a grammar given and there is a string omega that can be generated from this grammar and if this string omega can be derived from two or more left derivation trees。

 then that grammar is said to be ambiguous。 So when we mean two or more derivation trees。

 we should keep in mind that they should be both left derivation trees。

 It's not that you form one using a left derivation tree and under using a right derivation tree and that is ambiguous。

 No that is not the case it is only when it can be formed using two or more left。



![](img/0ec9e52c969ccb3695da447bb55b2746_1.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_2.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_3.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_4.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_5.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_6.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_7.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_8.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_9.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_10.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_11.png)

Drivation trees， then it is said to be an ambiguous grammar。 Okay。

 so now let's take a simple example to understand this in a better way。

 So here we have an example we have a grammar G which is given like this it has S as a nonteral symbol or the variable and it has terminal symbols a plus B plus and this multiplication sign and we have P as a production rule and s is the start symbol and the production rule is given like this S gives。



![](img/0ec9e52c969ccb3695da447bb55b2746_13.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_14.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_15.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_16.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_17.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_18.png)

S plus S and S can also give S into S， and it can also give a and it can also give B。

 Now we want to generate the string A plus a into B。 This is a string we want to generate。

 And let's see in how many ways we can generate this string。 Okay。

 so let us start with the start symbol， which is S。 And I will say that S gives S plus S。

 I will start from this production。 S gives S plus S。 Okay， now I need to get a plus a into B。

 Now this a is what I need to get。 And I am forming the left derivation tree for this。

 So this is a left derivation tree。 So we have to start from the left more symbol， which is S。

 So here this s， I will replace it with a because we have a production which says S gives a。

 So this S will be replaced by an A。 and the other S， let me just write it down as it is。



![](img/0ec9e52c969ccb3695da447bb55b2746_20.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_21.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_22.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_23.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_24.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_25.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_26.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_27.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_28.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_29.png)

And now I got this a plus S。 And now this a let me write it down as it is plus。

 and I have an another s over here。 and I need a into B。 Now further that。

 let me further expand this S using the production rule， which says that S gives S into S。

 So this s will be expanded as S。

![](img/0ec9e52c969ccb3695da447bb55b2746_31.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_32.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_33.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_34.png)

Into。S， and no。I will replace this as by a because we saw that s gives a and I need a in my string。

 so this a had write aacities and this s I will replace it with a and in 2。



![](img/0ec9e52c969ccb3695da447bb55b2746_36.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_37.png)

As as it is， and now this final s I will replace it with B now I can do that because the production rule says s can give B。

 so this a will be as it is this a will be as it is into this S will be replaced by B okay so now I am getting the string a plus a into B which is a string I want it to generate okay so this is one way I can generate this string now let's see another way in which we can generate I will again start with the start symbol and now I will start with the production which says s gives S into S this one。



![](img/0ec9e52c969ccb3695da447bb55b2746_39.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_40.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_41.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_42.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_43.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_44.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_45.png)

S。Into s。 okay， so this is again， a left derivation。 So we should start with the leftmost symbol。

 So here， this s over here， I will replace it with S plus s S gives s plus s。

 So this S I will replace it with s。

![](img/0ec9e52c969ccb3695da447bb55b2746_47.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_48.png)

Plus， S and this into as， I write it down as it is。



![](img/0ec9e52c969ccb3695da447bb55b2746_50.png)

Okay， so this is what we are getting。

![](img/0ec9e52c969ccb3695da447bb55b2746_52.png)

Now， now why am I doing this This is because I want to get this string and we see that there is a plus symbol in between and we were having into2 so if I do this I can get the symbol plus now I am having s plus S into s。

 now this S over here I will replace it with a because S can give a so a。



![](img/0ec9e52c969ccb3695da447bb55b2746_54.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_55.png)

Plus， then this S into as recognize me just write them as they are。 and now。



![](img/0ec9e52c969ccb3695da447bb55b2746_57.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_58.png)

This is over here。 Let me replace it with a again。A plus a。



![](img/0ec9e52c969ccb3695da447bb55b2746_60.png)

Into S。And then this final s， I will replace it with B because yes can give B。 So a plus a。Into B。

 so now I am getting by string a plus a into B， which is the string I wanted to generate。

 So we see that this string a plus a into B， we generated using two derivation trees first I chose the production rule S plus S and I could get the string and even when I chose the string S into s I could get this string and we have seen that in both the cases we use the left derivation tree。

 So using the left derivation tree we were able to derive this string in two ways。



![](img/0ec9e52c969ccb3695da447bb55b2746_62.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_63.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_64.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_65.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_66.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_67.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_68.png)

Thus， we can say that this grammar is ambiguous al right。

 so this is the example of an ambiguous grammar and I hope it was clear to you so thank you for watching and see you in the next one。



![](img/0ec9e52c969ccb3695da447bb55b2746_70.png)

![](img/0ec9e52c969ccb3695da447bb55b2746_71.png)