# C++-DSA课程-｜-数据结构-｜-leetcode-｜-Apna-College-｜--Complete-C++-Dsa-Course-p86-P88_L.86_二叉树的直径--BV18oUGBkEmV_p86-

![](img/5ac8b1327510523855dc7a4c23040007_0.png)

Hi， everyone and welcome to the complete series。 And today we're going to solve the problem for diameter of a binary tree Ak is s scanner available。

 Also there is a link for accompanied company by sheet in the description box to start we are given this binary tree diameter co find out。

 and this is also problem number 543 on what exactly do we mean by a diameter diameter is basically the length of the longest path between any two nodes of the binary tree andjo nodes。

 These are always the leaves of the tree。 just for example is binary tree sub longest path that is this path and is path key length calculate cur in terms of edges branches and nodes edges in terms of edges is lengthgi that is1。

2，3 So the answer or the diameter is going to be equal to3 for this particular tree generally though leaves be。

😊，Mamari path explore cur binary tree to a pathas exist k length3 k equal second pathipas exists kaiki length1 and2 k equal and a core path exists kai thisky length3 k equal to Yabiari diameter key same lengthhar。

 which is equal to 3 the ane binary3 key and the diameter co calculate kem by calculating the length of the longest path between two leaves or between any two nodes Obium3 key diameter keyem。

 There are two cases you exist kam。😊，Ytohamari3 Kjo diameter He Vohamari triki rootke through Ja。

 for example， is casesme Johamni diameter deki Vohamari is rootke through Jahi What trikijo root He。

 Vohamari is longest path can included the I klava a call caseme exist Katate just made diameter rootke through Nejahi。

 for example， Agris the Rike ku tree。 consider cur。 just may we have these notes。And right side。

 may Hamipas Kafisri notes them or Yahaahammni diameter go calculate Kanegi gousk to a to Hamipas ye path exists kai。

 Johamari rootke throughjata just may the length is 1，2，3，4，5。

 and 6 to a path he lengthhyipas 6 k equal second path y exists。

 Kaai Jobi rootke throughjata Gikyente 1，2，3，4 and 5。😊，And the third path here exists kja 12，3，4，5。

6 and 7 k equal。 So obviously， the diameter of the tree is going to be equal to 7 per longest root longest path right And similarly longest path for any node of for example。

 that is theri root root what is the exact length of。😊，for example。

 is is diameter longest and right long and height of the binary calculate which was the longest path on the and which was on the right but the right root diameter calculate diameter is basically plus right equal this is the value for and right in terms of edges right equal2 is equal to3 which is the diameter of the the length or the answer。

😊，Is always equal to left height plus right long is long plus right equal。

34 and equal second case diameterja right right diameter right diameter is diameter will be the right diameter and。

😊，lyra answer left diameter B recursively her a single node of the binary tree in the values who calculate kringi or inco comparering node toto left height plus right diameter at the longest value sub value subino saybi sub value head。

 That is going to be the final diameter of the binary。😊，For example。

 agarham is rootka example to yahaper subseli calculate Kte v value Joari rootke throughjari root k throughja value value have left height plus right height。

 which is equal to 3 second valueri left diameter to left me cukipath existing Kta to left diameter is going to be equal to 0。

 and third value is right diameter right can diametere diameter which is equal to 2 up 30 and2 misses subse valueri3ka head。

 This is the diameter of the binary3， and this is the answer same chi Aham Ya curri is particular node K to Yaha subseli valuek throughjari I K throughja value value have 1 plus 5kala has 6 second value H Jo left diameter ogi left diameterripa has 0 equal cuki co longest path existingra right diameter is side Agi Mula length of this path。

 which is going to be equal to 7 to 7ripa right diameter the largest value is going to be equal to。😊。

is binary right diameter value sub diameter longest right right or in values who calculate and we will try to find out the largest value in the diameter function logic functions calculate if we have a function called diameter。

😊，Johamme Hamari code can the diameter return kta for any root node。

 to Apenni diameter calculate knesehamka kcete Ane right subriche and up left subriche diameter calculate k cukihamra recuralpha havewakiari function co diameter calculate k tohamri sub function cos co B diameter calculate k to subse V are going to calculate the left diameter diskum same function co call kcta by passing root left node。

 and we can also calculate the right diameter diskleum same function co call kta by passing root k。😊。

Right node diameter diameter current diameter calculate root calculate and right calculate function assuming calculate function root calculate calculate which is root plus right calculate。

😊，Which is root key。Right height andpa valuejagi for current diameter current diameter is basically this value root final diameter of that is going to be the maximum of these three values Jobi maximum of these three values maximum of left diameter right diameter and current diameterse as the diameter from this function base base case root is equal to null diameterbi root value becomes equal to null case directly return as the final answer for the diameter。

 So this is the overall logic disk basis per diameter of the So let us convert the pseudocode into actual code an will analyze the complexity function is function。

😊，P hammna base case likeect kbi we root key value analhead。

 those case may we are going to return 0 Neto subse Pa hum up knee left diameter co calculate curgi by calling this function diameter of binary tree just scanander hum root call left pass Kinggi。

 similarly hamm me right diameter calculate Kgi。😊，By calling the same function jske underham rootka right past Kringgi and Oskeba。

 we are going to calculate the current diameter。Jmahammni left height and right height go aing。

 So let's assume make height function already exist Kaai just K under hum root Ka left pass K plus height function K under he hum root Ka right Pa Kane。

 And we are going to return the maximum of current diameter。😊，Left diameter and right diameter。

 to Tinogi Jobi maximum value Hoie。 That will be our final answer。 justkohams functions a return Car。

 Now， let us also write this height function from China to public function even as。

 Let's call it in teacherger height Just scan there Hamippa3 node root anvalier of height of the3 I may already calculate Kanehi Kabibi root P valuenal Hoja。

 Those case may height Hojagi0 k equal。 Nato sub Pahammmi left height calculate Ka。

 which is going to be height of root car。😊，Right。Okeba， we are going to calculate the right height。

 which is going to be height of root car。Left and right。

And Yahai I returned calling a maximum of left height。And right height plus1。

 So this is how we write our height function。 justy overall time complexity of the Ubi fan。

 depending upon the number of nodes in the binary tree。

 And this is the diameter function for the binary tree。igbar let us run our code。😊。

And submit it to code hamra successfully submit O， but this is not the most optimized version of the code。

 Ma yaha a gram time complexity key to Hamraju diameter of the binary Chi single nodeja andhajaar single node k in the values co calculate kskaab head diameter function key overall。

 your time complexity Ho， that will be big of n in cuki single node k diameter right diameter to recurs calculate。

 but is current diameter co calculate K height function co to height function key time complexity single node co a height function key overall time complexity up may big of nkala Yaha diameter function single node k big of n time complexity extra to the overall time complexity of the diameter function is big of n square to yaha even though recur function use。

😊，overall time complexity that is n square Q separate functions go use but is time complexity diameter linear calculate are going to use a parallel approach basically diameter diameter node。

😊，ari diameter simply simply a global answer variable create and is node diameter diameter diameter diameter right right right diameter diameter diameter basically what we are going to do which is global answerverse is diameter which passes through this node diameter plus right height。

 which is going to be equal to 3。😊，To answer value compare next answer equal Similarlyly。

 I diameter calculate value0 equal is0 value value value values compare。😊，Similarly1 plus1。

 which is height plus right height to equal which is the length of is is answer similarly and and current got the value of the diameter of function diameter height right and。

😊，height function k under single nodegi height calculate K knee diameter we calculate。

 which basically meansari pass a height function Had exist km root pass kthe y in t height return k sub height functionri knee left height calculate k by calling height function for root left。

😊，And similarly， Hamari lay up me right height， calculate katai by calling this height function for root car。

 right anduske bath maximum of left height and right height plus1co return K theyai as the final height y function Hamaripa already exist Ka is can the I base case A Kabbi B Uhamari root nu K equal hip。

😊，Those case may we are going to return a value equal to 0。

I function single calculate current diameter。 we calculate current diameter diameter that is equal to height plus right height or is function height or right simply is value height plus right height current diameter calculate or andbi maximum value that will become our answer So y single change function same height function answer diameter calculate or diameter this is the height function Jo。

😊，I see height function K Ba hum a variable declare kecam， which is called answer。

 just going initialize curing is0 kat and Yahaber hum answer Kleki maximum value calculate kseche by comparing answer with left height。

😊，Plus right height is your left height and right height head。

 This is basically the current diameter of node root node calculate for each single node in the binary tree when we are calculating the height node k pass maximum value of current diametergi which is basically the final diameter of the binary tree answer variable canja and is answer variable diameter function as the final answer diameter function callshi in fact simply function root and height co calculatene j function completeja answer diameter is answer variableja and is answer overall time complexity constant function time complexity height function which is same which is big of n linear time complex。

😊，S is out of a binary cheeky diameterco calculate kapam。 Let us now run this code。And submit it。

 So this is how we have successfully solved the problem of calculating the diameter for a binary tree Gcomnet solve k with big of n time complexity。

 So make major optimization at Gni khead to reduce the time complexity from big of n square to big of。

 So if you have successfully completed today's lecture。 Then you can market in is down the comments。

 It case At me can also share a progress with me on Twitter just cu Kkuniche description box scan mi Zga Askulate9 Miltonex lecture can that then keep learning and keep exploring。

😊。

![](img/5ac8b1327510523855dc7a4c23040007_2.png)