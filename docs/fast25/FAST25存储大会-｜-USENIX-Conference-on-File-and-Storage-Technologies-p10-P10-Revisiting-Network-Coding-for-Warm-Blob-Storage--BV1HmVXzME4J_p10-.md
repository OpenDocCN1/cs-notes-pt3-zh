# FAST25存储大会-｜-USENIX-Conference-on-File-and-Storage-Technologies-p10-P10-Revisiting-Network-Coding-for-Warm-Blob-Storage--BV1HmVXzME4J_p10-

。

![](img/5825206f58655827bb983f273d767b9a_1.png)

Hello， everyone。 good afternoon。 I'm Ping Chen。 it's my pleasure to give this presentation on behalf of thiss authors。

 So this paper is from Hhou University of science and technology in China。

 This work is supervised by Professor Yu Chonghu and Professor Dan Feng。 Okay， as we know。

 Bb storage。 Yes， is widely deployed to store a huge amounts of abstracted data such as photos and documents。

 Okay， practical bb storage system keep data in different performance storage to make the performance trade of。

😊，You， for example， in Facebook， the new data are first stored in the hot storage to guarantee high access performance。

 When data become cold， the， the Facebook moves the those data to the warm storage。Okay。

 we find two interesting things。 We find that warm data dominate storage comprising over 80% at Facebook。

 And the second one is， additionally， most bs are small。 in Facebook。

 almost all photos and 60% of videos are under  one me。😊，So in storage system。

 eraing coding coding provides reliability against failures and is widely deployed。

 It cause key data blocks into N called blocks to form a stripe January。

 any key of the un codeed block in the stripe can recover the data。

 These figures illustrate a single block repair where recovering a lost block requires rering two blocks leading to high repairs cost。

So the some techniques to propose to to solve this problem。

 the regenerating technology is proposed to solve the high cost problem。 Yeah。

 we know it is repair friendly this techniques splits a large block into smaller sub blocks reducing data transfer size。

 So the number of sub blocks is called the subization level。

 Okay M R is one of the efficient approaches to generating course。

 It can minimize story redundancy and are classified into two types。

 The the first one is non system M R and systematic MR。

 So the former stores only party blocks while the later includes both data and priority blocks。

 So systematic M are more popular as they enable direct access to original data with high rate。😊。

formmise。So systematic M SR offers good original data access performance。 Well， it performs。

 it performs poorly in repair operations due to accessing multiple sub sub blocks。

 causing lots of non continuous Is。 So this figure shows the single block repair process。

 So we can see that a block。😊，It's divided into many sub blockslocks。

 and repairing a lost block requires the travel of multiple sub blockslocks in each node。

So we we confirm this finding through experimentation。

 So this figure shows a repair performance of different N and key for various various blob size。

 So we can see that the repair performance drops dramatically as the bb size decreases， which。

 which demonstrates that the repair performance is limited for small blobs。😊。

So to address limitation one， existing approaches use a continuous layout to merge small blocks into equalized large blocks improve to improve the access and I O efficiency。

 However， it still causes read amplification due to unnecessary data retrieval。

 This figure shows thatgrade degraded read performance reduce significantly as the merge size increases。

 Also， the read performance drops dramatically as as the block size decreases。😊。

So these twos motivate us to do something。Luckily， we find the non systematic MR code perform better for reading small data。

 It has fewer sub blocks resulting in fewer Is than systematic MR code in for example， in figure A。

 we can see that repairing a lost block only requires the retval of three sub blockslock。

 Well you know， in figure in figure B， the systematic MR。

 The clay called in figure B needs to retrieve 6 sub blockss。 So， obviously。

 the the the technique in in figure A is better。So in this paper， we design N b。

 which combines key idea from both systematic and non systematicy MR codes。 for small data。

 we adopt the non systematicmatic M approach while for large data。

 we retain the system approach to address some key challenges， We further propose three solutions。

 Okay， first， although non systematicmatic S MR offers a better repair performance。

 they cause thepl amplification when accessing original data。

 as reading one block requiring decoding key blocks from keynot。 for example， as showing figure a。

 we if you want to read any better of original data， you have tocode two blocks in the in the stripe。

 So while the original data can be directly read read in the figure B。

 So because it store it stores original data block。 So therefore。

 all main goal is to reduce the read amplification for non system system。mr。

So we find that blob blob exhibit good access locality。

 So there are two kinds of access locality in bb data。 the in locality and inter b locality。

 So the former means that small blo is commonly accessed together。 such as the photos。

 So if any from such a b is read。 the rest of it should be prefeched。

 So the inter b locality means that there are multiple some b that are often accessed together。

 such as user I， some some users may be accessed together。😊。

So the data locality motivates us to accelerate read performance by encoding data in your group。 So。

 for example， considering two data block D1 and D2 that has access locality。

 So we can see that in figure A without considering the locality。

 Read D1 and D2 need to decode four blocks。 Well in figure B， consider considering the locality。

 Read D1， D2 only needs to de two blocks。 And when D1 is read D2 has a good chance to be read immediately。

😊，So this is the workflow。 We designed the split merge in code scheme for improving intra b locality and the merge split in code scheme for improving the locality。

 So the design details are provided in in the paper。 So secondly。

 the nonssmatic MR code effectively repair small blobs， but handling large blobs remain challenging。

 So observing that clay code performs well on large bbs。

 So we a hybrid encoding architecture the nonssmatic MR codes for small blobs and clay know systematic MR for large blobs。

 So it's a question how to determine the threshold between small and the large b。

 So we select the data site at which disk time dominate as the red circle in the figure So the left one is we did the large b。

😊，And the right， the right domain is small blobs。Okay。

 we also find that exist in systematic MR code only support scenarios where up to two blocks are broken。

 So therefore， we design the sub sub block in rotation this technology to support more failure cases。

 So more details and proof are shown in the paper So we implement our N in Linux specifically we locality manager module to manage with access locality So we we implement the coding and distribution model based on and the repair based on the R So all experiments on Aliba Alibaba show that compared with M comparable read through for the repair performance reduce a single block repair time by up to 45 percent and the full node repair time by up to38 percent which。

Demontrate that the efficiency of our method。 So for further experiments on N blog are presented in the paper。

 Okay， this is a conclusion。 So we， we have open source the code for researchers convenience。

 So any any any technical question， please contact the author's email。 Okay， thank you。😊。



![](img/5825206f58655827bb983f273d767b9a_3.png)

![](img/5825206f58655827bb983f273d767b9a_4.png)